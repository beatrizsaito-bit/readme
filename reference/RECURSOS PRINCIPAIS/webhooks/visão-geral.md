---
title: Visão Geral
excerpt: >-
  Webhooks permitem que sua aplicação receba notificações em tempo real sobre
  eventos   na plataforma Lina, como atualizações de saldo, novas transações e
  mudanças no ciclo   de vida de consentimentos
deprecated: false
hidden: false
metadata:
  robots: index
---
<br />

## Como funciona

1. Um evento ocorre na plataforma (ex: saldo atualizado)
2. O evento é enfileirado para entrega confiável
3. Nosso serviço assina o payload com **HMAC-SHA256** e faz um `POST HTTPS` para seu endpoint
4. Seu endpoint valida a assinatura e processa o evento

## Requisitos do endpoint

| Requisito         | Detalhe                                         |
| ----------------- | ----------------------------------------------- |
| Protocolo         | **HTTPS obrigatório** (HTTP é rejeitado)        |
| Método            | Deve aceitar **POST**                           |
| Timeout           | Responder em até **10 segundos**                |
| Status de sucesso | Retornar **2xx** para confirmar recebimento     |
| Idempotência      | Usar o header `X-Lina-Event-Id` para deduplicar |

## Características

* **Entrega garantida** — até 7 tentativas com backoff exponencial (~34h de janela)
* **Assinatura criptográfica** — HMAC-SHA256 em cada request
* **Rotação de secrets** — troca sem downtime (grace period de 24h)
* **Circuit breaker** — endpoints com falhas consecutivas são desabilitados automaticamente
* **Retenção de 30 dias** — eventos disponíveis para consulta via API

***

<br />

# Tipos de Eventos

## Eventos disponíveis

| Evento                             | Descrição                                   |
| ---------------------------------- | ------------------------------------------- |
| `consent.created`                  | Consentimento criado                        |
| `consent.confirmed`                | Consentimento confirmado pelo usuário       |
| `consent.rejected`                 | Consentimento rejeitado pelo usuário        |
| `consent.revoked`                  | Consentimento revogado                      |
| `account.balance.updated`          | Saldo de conta atualizado                   |
| `account.transactions.updated`     | Novas transações de conta disponíveis       |
| `credit-card.transactions.updated` | Novas transações de cartão disponíveis      |
| `user.data.insert.start`           | Início da sincronização de dados do usuário |
| `user.data.insert.finish`          | Sincronização de dados concluída            |

## Estrutura do payload

Todos os eventos seguem a mesma estrutura:

```json
{
  "id": "evt_01abc2def3456789",
  "eventType": "account.balance.updated",
  "created": 1710409800,
  "dateTime": "2026-03-14T10:30:00.000Z",
  "tenantId": "seu-tenant-id",
  "apiVersion": "2025-02-01",
  "data": {
    "object": {
      // dados atuais do recurso
    },
    "previousAttributes": {
      // valores anteriores (quando aplicável)
    }
  }
}

Headers enviados

Cada webhook inclui os seguintes headers:

┌───────────────────┬───────────────────────────┬────────────────────────────────────────┐
│      Header       │          Exemplo          │               Descrição                │
├───────────────────┼───────────────────────────┼────────────────────────────────────────┤
│ Content-Type      │ application/json          │ Formato do payload                     │
├───────────────────┼───────────────────────────┼────────────────────────────────────────┤
│ User-Agent        │ Lina-Webhooks/1.0         │ Identificação do serviço               │
├───────────────────┼───────────────────────────┼────────────────────────────────────────┤
│ X-Lina-Signature  │ t=1710409800,v1=abc123... │ Assinatura HMAC-SHA256                 │
├───────────────────┼───────────────────────────┼────────────────────────────────────────┤
│ X-Lina-Event-Id   │ evt_01abc2def3456789      │ ID único do evento (para idempotência) │
├───────────────────┼───────────────────────────┼────────────────────────────────────────┤
│ X-Lina-Event-Type │ account.balance.updated   │ Tipo do evento                         │
└───────────────────┴───────────────────────────┴────────────────────────────────────────┘
```

<br />

<br />

# Verificando Assinaturas

Cada webhook enviado pela Lina inclui uma assinatura HMAC-SHA256 no header
`X-Lina-Signature`. **Você deve validar essa assinatura** para garantir que
o request é legítimo e não foi alterado.

## Formato da assinatura

X-Lina-Signature: t=1710409800,v1=5257a869e7ecebeda32affa62cdca3fa51cad7e77a0e56ff536d0ce8e108d8bd

* `t` — timestamp Unix (segundos) de quando o webhook foi enviado
* `v1` — assinatura HMAC-SHA256 em hexadecimal

> Durante rotação de secret, o header pode conter duas assinaturas:
> `t=...,v1=<assinatura_novo_secret>,v1=<assinatura_antigo_secret>`

## Como verificar

### Passo a passo

1. Extraia o timestamp (`t`) e as assinaturas (`v1`) do header
2. Construa o signed payload: `{timestamp}.{corpo_do_request}`
3. Compute o HMAC-SHA256 usando seu webhook secret
4. Compare sua assinatura com as `v1` recebidas (timing-safe)
5. (Recomendado) Rejeite se o timestamp for muito antigo (ex: > 5 minutos)

<br />

```javascript
const crypto = require('crypto');

  function verifyWebhookSignature(payload, signatureHeader, secret) {
      // 1. Parse do header
      const parts = signatureHeader.split(',');
      const timestamp = parts[0].replace('t=', '');
      const signatures = parts.slice(1).map(p => p.replace('v1=', ''));

      // 2. Proteção anti-replay (opcional, recomendado)
      const age = Math.floor(Date.now() / 1000) - parseInt(timestamp);
      if (age > 300) { // 5 minutos
          throw new Error('Timestamp muito antigo');
      }

      // 3. Construir signed payload
      const signedPayload = `${timestamp}.${payload}`;

      // 4. Computar HMAC-SHA256
      const expected = crypto
          .createHmac('sha256', secret)
          .update(signedPayload)
          .digest('hex');

      // 5. Verificar (timing-safe) contra qualquer v1
      return signatures.some(sig =>
          crypto.timingSafeEqual(
              Buffer.from(sig, 'hex'),
              Buffer.from(expected, 'hex')
          )
      );
  }

  // Uso no Express
  app.post('/webhook', express.raw({ type: 'application/json' }), (req, res) => {
      const signature = req.headers['x-lina-signature'];
      const payload = req.body.toString();

      if (!verifyWebhookSignature(payload, signature, process.env.WEBHOOK_SECRET)) {
          return res.status(401).send('Assinatura inválida');
      }

      const event = JSON.parse(payload);
      console.log(`Evento recebido: ${event.eventType}`);

      // Processar evento...

      res.status(200).json({ received: true });
  });
```
```python
import hmac
  import hashlib
  import time

  def verify_webhook_signature(payload: str, signature_header: str, secret: str) -> bool:
      parts = signature_header.split(',')
      timestamp = parts[0].replace('t=', '')
      signatures = [p.replace('v1=', '') for p in parts[1:]]

      # Proteção anti-replay
      age = int(time.time()) - int(timestamp)
      if age > 300:
          raise ValueError('Timestamp muito antigo')

      # Computar HMAC-SHA256
      signed_payload = f"{timestamp}.{payload}"
      expected = hmac.new(
          secret.encode(),
          signed_payload.encode(),
          hashlib.sha256
      ).hexdigest()

      return any(hmac.compare_digest(sig, expected) for sig in signatures)

  Java

  import javax.crypto.Mac;
  import javax.crypto.spec.SecretKeySpec;
  import java.security.MessageDigest;

  public class WebhookVerifier {

      public static boolean verify(String payload, String signatureHeader, String secret)
              throws Exception {
          String[] parts = signatureHeader.split(",");
          String timestamp = parts[0].replace("t=", "");
          String signature = parts[1].replace("v1=", "");

          // Anti-replay
          long age = System.currentTimeMillis() / 1000 - Long.parseLong(timestamp);
          if (age > 300) throw new SecurityException("Timestamp muito antigo");

          // HMAC-SHA256
          String signedPayload = timestamp + "." + payload;
          Mac mac = Mac.getInstance("HmacSHA256");
          mac.init(new SecretKeySpec(secret.getBytes(), "HmacSHA256"));
          byte[] hash = mac.doFinal(signedPayload.getBytes());
          String expected = bytesToHex(hash);

          return MessageDigest.isEqual(
              expected.getBytes(),
              signature.getBytes()
          );
      }

      private static String bytesToHex(byte[] bytes) {
          StringBuilder sb = new StringBuilder();
          for (byte b : bytes) sb.append(String.format("%02x", b));
          return sb.toString();
      }
  }
```
```java
import javax.crypto.Mac;
  import javax.crypto.spec.SecretKeySpec;
  import java.security.MessageDigest;

  public class WebhookVerifier {

      public static boolean verify(String payload, String signatureHeader, String secret)
              throws Exception {
          String[] parts = signatureHeader.split(",");
          String timestamp = parts[0].replace("t=", "");
          String signature = parts[1].replace("v1=", "");

          // Anti-replay
          long age = System.currentTimeMillis() / 1000 - Long.parseLong(timestamp);
          if (age > 300) throw new SecurityException("Timestamp muito antigo");

          // HMAC-SHA256
          String signedPayload = timestamp + "." + payload;
          Mac mac = Mac.getInstance("HmacSHA256");
          mac.init(new SecretKeySpec(secret.getBytes(), "HmacSHA256"));
          byte[] hash = mac.doFinal(signedPayload.getBytes());
          String expected = bytesToHex(hash);

          return MessageDigest.isEqual(
              expected.getBytes(),
              signature.getBytes()
          );
      }

      private static String bytesToHex(byte[] bytes) {
          StringBuilder sb = new StringBuilder();
          for (byte b : bytes) sb.append(String.format("%02x", b));
          return sb.toString();
      }
  }

```

<br />

<br />

# Política de Retentativas

Se seu endpoint não retornar um status **2xx** dentro de **10 segundos**, o webhook
é reagendado automaticamente com backoff exponencial.

## Tabela de tentativas

| Tentativa | Delay após falha | Tempo acumulado |
| --------- | ---------------- | --------------- |
| 1         | imediato         | —               |
| 2         | 1 minuto         | 1 min           |
| 3         | 5 minutos        | 6 min           |
| 4         | 30 minutos       | 36 min          |
| 5         | 2 horas          | ~2h 36min       |
| 6         | 8 horas          | ~10h 36min      |
| 7         | 24 horas         | ~34h 36min      |

> Cada delay tem uma variação aleatória de **±10%** (jitter) para evitar
> picos de carga simultâneos.

## Status do evento

| Status              | Descrição                               |
| ------------------- | --------------------------------------- |
| `pending`           | Aguardando entrega ou retentativa       |
| `delivered`         | Entregue com sucesso (2xx)              |
| `failed`            | Todas as 7 tentativas falharam          |
| `endpoint_disabled` | Endpoint desabilitado (circuit breaker) |

## Circuit breaker

Para proteger ambos os lados, endpoints que falham consistentemente são
desabilitados automaticamente:

* **5 eventos consecutivos** com todas as 7 tentativas esgotadas → endpoint desabilitado
* **HTTP 410 Gone** → endpoint desabilitado imediatamente
* **Entrega bem-sucedida** → contador de falhas resetado para zero

Quando um endpoint é desabilitado, novos eventos recebem status `endpoint_disabled`
e nenhuma tentativa de entrega é feita. Você pode reativar o endpoint via API.

<br />
