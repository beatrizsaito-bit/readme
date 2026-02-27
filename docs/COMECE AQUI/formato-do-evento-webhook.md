---
title: Formato do Evento Webhook
deprecated: false
hidden: false
metadata:
  robots: index
---
Todo evento enviado ao endpoint do cliente segue esta estrutura:

```json
{
  "id": "evt_019c9f741f617007ba5ad5ef22f6b47b",
  "eventType": "account.balance.updated",
  "created": 1772201713,
  "tenantId": "go-assets",
  "apiVersion": "2025-02-01",
  "data": {
    "userId": "2b6737aa-53ec-4bf3-b93c-e0794463330c",
    "object": { ... },
    "previousAttributes": { ... }
  }
}
```

<br />

Detalhes:

| Campo                     | Descrição                                               |
| ------------------------- | ------------------------------------------------------- |
| `id`                      | ID único do evento. Use para idempotência.              |
| `eventType`               | Tipo do evento                                          |
| `created`                 | Unix timestamp (segundos). Use para ordenação.          |
| `tenantId`                | Identificador do tenant                                 |
| `apiVersion`              | Versão da API                                           |
| `data.userId`             | ID do usuário relacionado ao evento                     |
| `data.object`             | Estado atual do recurso                                 |
| `data.previousAttributes` | Campos que mudaram — estado anterior (quando aplicável) |

**Header de assinatura enviado em todo evento:**

```
X-Lina-Signature: t=1772201713,v1=5257a869e7ecebeda32afda62cdca3fa51cad7e77a0e56ff536d0ce8e108d8bd
```

Verificação: `HMAC-SHA256({t}.{raw_body})` usando o secret do webhook. Rejeitar se `|now - t| > 300` segundos.
