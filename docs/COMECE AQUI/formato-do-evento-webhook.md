---
title: Formato do Evento Webhook
deprecated: false
hidden: true
metadata:
  robots: index
---
Todo evento enviado ao endpoint do cliente segue esta estrutura:

```json
{
	"id": "evt_019c9fa546617331837c688f972450f6",
  "eventType": "consent.created",
  "created": 1772204934,
  "dateTime": "2026-02-27T15:08:54.545Z",
  "tenantId": "data-tutor",
  "apiVersion": "2025-02-01",
  "data": {
    "userId": "2b6737aa-53ec-4bf3-b93c-e0794463330c",
    "consentId": "urn:itau:1d7c356d-5569-4ca8-845a-50d85536c5a7",
    "authorisationServerId": "68308291-ec0d-4398-83ce-68b6b1087e49",
    "organisationId": "9c721898-9ce0-50f1-bf85-05075557850b"
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