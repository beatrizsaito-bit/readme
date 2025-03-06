---
title: Webhooks
excerpt: Avisos e callbacks para acompanhar o andamento dos eventos
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
Ao invés de realizar consultas periódicas na API para buscar informações, os webhooks enviam notificações diretamente para os endpoints que você configurar. Quando um evento é disparado (como, por exemplo, a criação de um novo consentimento),  a aplicação **Data Link** faz uma solicitação **HTTP POST** ao endpoint configurado, contendo os dados relevantes no corpo da requisição em formato JSON. Para mais informações de como webhook funcionam, acesse [aqui](https://webhook.net/) 

<br />

## Configurações

Para configurar, basta acessar o [Painel de Administração (Console)](https://console.linaopenx.com.br) e acessar o menu à esquerda em *"Configurações"* e em seguida preencher com a URL que irá receber as chamadas da aplicação

![](https://files.readme.io/d4170e8f3a2e67365d6320a631097b2b351ddd7afb5fb0d6367e4f1622d482fc-image.png)

<br />

## Modelo de dados

Um exemplo do modelo de dados utilizados para os eventos de webhook:

```json
{  
  "eventType": "...",
  "data": {  
    // chaves e valores de acordo com o evento
  },  
  "dateTime": "..."  
}
```

### Tipo do evento (`eventType`)

Os seguintes eventos são enviados através do webhook registrado:

| Tipo do evento (eventType) | Dados                                                                   | Descrição                                                                                                                                                                                                                                    |
| :------------------------- | :---------------------------------------------------------------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| consent.created            | `userId, consentId, authorisationServerId, organisationId`              | Enviado a partir da criação de consentimento em uma instituição por um usuário                                                                                                                                                               |
| consent.confirmed          | `userId, consentId, authorisationServerId, organisationId`              | Enviado a partir da autorização de um consentimento por um usuário final e a confirmação do aceite com sua instituição transmissora (instituição domicílio).                                                                                 |
| consent.rejected           | `userId, consentId, authorisationServerId, organisationId`              | Enviado a partir da revogação de um consentimento. Esta revogação pode ocorrer na instituição transmissora (instituição domicílio) ou por decisão unilateral em algum canal de suporte.                                                      |
| user.data.insert.start     | `userId, consentId, authorisationServerId, organisationId`              | Enviado ao realizar a carga de dados do usuário. Ao passo que o consentimento é aceito e autorizado, a aplicação automaticamente realiza a carga de dados de todos os dados consentidos do usuário - permitindo, posteriormente sua consulta |
| user.data.insert.finish    | `userId, consentId, authorisationServerId, organisationId, timeElapsed` | Finalização da carga inicial de dados do usuário. A partir deste momento, é possível realizar a consulta das informações em sua integridade                                                                                                  |

<br />

## Segurança

> 📘 Assinatura e Secret
>
> A assinatura digital que garante a unicidade da mensagem se encontra no header `x-webhook-signature`. Já o `secret` do webhook pode ser acessado, recuperado e rotacionado no [console](https://console.hml.linaopenx.com.br/data-distributor/config)

Para fins de segurança no recebimento destes webhooks, utilizamos uma "assinatura digital" única e segura da mensagem que será enviada. Esta assinatura digital é sempre contida nos `headers` da requisição, na chave `x-webhook-signature`. 

Esta assinatura é gerada utilizando o conteúdo da mensagem (`payload`) e o segredo compartilhado (`secret do webhook` - também acessível no [console](https://console.linaopenx.com.br/data-distributor/config)) que apenas o remetente e o destinatário conhecem. Aplicando o algoritmo de hash criptográfico *HMAC-SHA256*, combinamos o payload com o `secret do webhook` em uma operação não-reversível. Este processo gera um hash, que então convertemos para formato hexadecimal para facilitar a transmissão.

Esta assinatura serve como uma espécie de "selo de autenticidade" que permite ao destinatário verificar se a mensagem é autêntica e não foi alterada durante o envio, pois apenas quem possui o mesmo segredo conseguirá gerar a mesma assinatura para o mesmo payload.

Para validar a assinatura, seguem alguns exemplos em diversas linguagens:

```javascript
const crypto = require('crypto');

function verifyWebhookSignature(payload, signature, secret) {
    const expectedSignature = crypto
        .createHmac('sha256', secret)
        .update(payload)
        .digest('hex');
    
    return crypto.timingSafeEqual(
        Buffer.from(signature),
        Buffer.from(expectedSignature)
    );
}

// Express Example
app.post('/webhook', (req, res) => {
    const signature = req.headers['x-webhook-signature'];
    const payload = JSON.stringify(req.body);
    const secret = process.env.WEBHOOK_SECRET;
    
    if (!verifyWebhookSignature(payload, signature, secret)) {
        return res.status(401).json({ error: 'Invalid signature' });
    }

    // Process webhook...
    res.json({ status: 'success' });
});
```
```python
import hmac
import hashlib
import json
from flask import Flask, request, jsonify

def verify_webhook_signature(payload: str, signature: str, secret: str) -> bool:
    expected_signature = hmac.new(
        secret.encode('utf-8'),
        payload.encode('utf-8'),
        hashlib.sha256
    ).hexdigest()
    
    return hmac.compare_digest(signature, expected_signature)

# Exemplo Flask
@app.route('/webhook', methods=['POST'])
def webhook():
    signature = request.headers.get('x-webhook-signature')
    payload = json.dumps(request.json)
    secret = os.environ.get('WEBHOOK_SECRET')
    
    if not verify_webhook_signature(payload, signature, secret):
        return jsonify({'error': 'Invalid signature'}), 401

    # ...
    return jsonify({'status': 'success'})
```
```csharp
using System.Security.Cryptography;
using System.Text;
using Microsoft.AspNetCore.Mvc;

public class WebhookVerifier
{
    public static bool VerifySignature(string payload, string signature, string secret)
    {
        using (var hmac = new HMACSHA256(Encoding.UTF8.GetBytes(secret)))
        {
            var computedHash = hmac.ComputeHash(Encoding.UTF8.GetBytes(payload));
            var computedSignature = BitConverter
                .ToString(computedHash)
                .Replace("-", "")
                .ToLower();
            
            return signature.Equals(
                computedSignature, 
                StringComparison.OrdinalIgnoreCase
            );
        }
    }
}

// ASP.NET Controller Example
[ApiController]
[Route("api/[controller]")]
public class WebhookController : ControllerBase
{
    [HttpPost]
    public IActionResult Webhook([FromBody] object body)
    {
        var signature = Request.Headers["X-Webhook-Signature"].ToString();
        var payload = JsonSerializer.Serialize(body);
        var secret = Configuration["WebhookSecret"];
        
        if (!WebhookVerifier.VerifySignature(payload, signature, secret))
        {
            return Unauthorized(new { error = "Invalid signature" });
        }

        // Process webhook...
        return Ok(new { status = "success" });
    }
}
```
```java
import javax.crypto.Mac;
import javax.crypto.spec.SecretKeySpec;
import java.nio.charset.StandardCharsets;

public class WebhookVerifier {
    public static boolean verifySignature(
        String payload, 
        String signature, 
        String secret
    ) throws Exception {
        Mac sha256Hmac = Mac.getInstance("HmacSHA256");
        SecretKeySpec secretKey = new SecretKeySpec(
            secret.getBytes(StandardCharsets.UTF_8), 
            "HmacSHA256"
        );
        
        sha256Hmac.init(secretKey);
        byte[] hash = sha256Hmac.doFinal(
            payload.getBytes(StandardCharsets.UTF_8)
        );
        String computedSignature = bytesToHex(hash);
        
        return signature.equalsIgnoreCase(computedSignature);
    }
    
    private static String bytesToHex(byte[] hash) {
        StringBuilder hexString = new StringBuilder();
        for (byte b : hash) {
            String hex = Integer.toHexString(0xff & b);
            if (hex.length() == 1) hexString.append('0');
            hexString.append(hex);
        }
        return hexString.toString();
    }
}

// Spring Boot Example
@RestController
public class WebhookController {
    @PostMapping("/webhook")
    public ResponseEntity<?> webhook(
        @RequestBody String payload,
        @RequestHeader("X-Webhook-Signature") String signature
    ) {
        try {
            String secret = environment.getProperty("webhook.secret");
            
            if (!WebhookVerifier.verifySignature(payload, signature, secret)) {
                return ResponseEntity.status(401)
                    .body(new ErrorResponse("Invalid signature"));
            }

            // Process webhook...
            return ResponseEntity.ok(new SuccessResponse("success"));
        } catch (Exception e) {
            return ResponseEntity.status(500)
                .body(new ErrorResponse("Error verifying signature"));
        }
    }
}
```
```go
package main

import (
    "crypto/hmac"
    "crypto/sha256"
    "crypto/subtle"
    "encoding/hex"
    "io"
    "net/http"
)

func verifyWebhookSignature(payload []byte, signature, secret string) bool {
    mac := hmac.New(sha256.New, []byte(secret))
    mac.Write(payload)
    expectedMAC := hex.EncodeToString(mac.Sum(nil))
    
    return subtle.ConstantTimeCompare(
        []byte(signature),
        []byte(expectedMAC),
    ) == 1
}

// HTTP Handler Example
func webhookHandler(w http.ResponseWriter, r *http.Request) {
    signature := r.Header.Get("X-Webhook-Signature")
    body, err := io.ReadAll(r.Body)
    if err != nil {
        http.Error(w, "Error reading body", http.StatusBadRequest)
        return
    }
    
    secret := os.Getenv("WEBHOOK_SECRET")
    if !verifyWebhookSignature(body, signature, secret) {
        http.Error(w, "Invalid signature", http.StatusUnauthorized)
        return
    }

    // Process webhook...
    w.WriteHeader(http.StatusOK)
    w.Write([]byte(`{"status":"success"}`))
}
```
