---
title: Rotacionar secret do webhook
excerpt: >-
  .Gera um novo secret para o webhook. O secret anterior permanece válido por 24
  horas para que o cliente possa migrar sem downtime.
api:
  file: Data Distributor las.json
  operationId: post_new-endpoint
deprecated: false
hidden: false
link:
  new_tab: false
metadata:
  robots: index
next:
  description: >-
    ⚠️ Guarde o novo secret imediatamente. Ele não será exibido novamente.


    Durante o período de 24h, o header X-Lina-Signature terá dois valores v1 —
    aceite o evento se qualquer um for válido.
---