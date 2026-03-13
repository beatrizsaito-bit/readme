---
title: Rotacionar Secret
excerpt: >-
  Gera um novo secret. O secret anterior permanece válido por 24 horas para
  migração sem downtime. Durante esse período, o header X-Lina-Signature terá
  dois valores v1 — aceite o evento se qualquer um for válido.
api:
  file: api_documentation_openapi.yaml
  operationId: post_notification-tenant-id-webhooks-client-id-rotate-secret
hidden: false
---