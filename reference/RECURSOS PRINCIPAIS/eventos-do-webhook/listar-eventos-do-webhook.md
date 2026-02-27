---
title: Listar eventos do webhook
excerpt: >-
  Retorna o histórico de eventos do tenant autenticado. Eventos ficam
  disponíveis por 30 dias.
api:
  file: Data Distributor las.json
  operationId: get_api-v1-webhook-events
deprecated: false
hidden: false
link:
  new_tab: false
metadata:
  robots: index
---
<br />

**Tipos de evento disponíveis para o filtro `type`:**

* `account.balance.updated`
* `account.transactions.updated`
* `consent.created`
* `consent.confirmed`
* `consent.rejected`
* `consent.revoked`
* `user.data.insert.start`
* `user.data.insert.finish`

***

**Status dos eventos:**

| Status              | Descrição                                                     |
| ------------------- | ------------------------------------------------------------- |
| `pending`           | Aguardando entrega ou em fila de retry                        |
| `delivered`         | Entregue com sucesso (2xx recebido)                           |
| `failed`            | Todas as 7 tentativas de entrega falharam                     |
| `endpoint_disabled` | Webhook não configurado ou desabilitado no momento da criação |

<br />
