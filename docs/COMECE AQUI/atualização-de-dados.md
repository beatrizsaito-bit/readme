---
title: Atualização de dados
deprecated: false
hidden: false
metadata:
  robots: index
---
A consulta de dados no Open Finance pode ser limitada mensalmente de acordo com o dados que será consultado. Quando o limite operacional é atingido, a consulta de dados retorna 423 e não permite a atualização do dado.

Considerando essas regras do Open Finance, o Data Link possui um motor de atualização para possibilitar a atualização dos dados ao longo de todo o mês. A tabela abaixo indica a frequência de atualização:

<br />

| Endpoint de recurso                                                       | Periodicidade | Execuções/dia | Execuções/mês |
| ------------------------------------------------------------------------- | ------------- | ------------- | ------------- |
| **Consentimentos**                                                        |               |               |               |
| `consents/{consentId}`                                                    | 1x por dia    | 1             | 30            |
| **Accounts**                                                              |               |               |               |
| `accounts`                                                                | semanal       | 0,14 em média | 4,3 aprox.    |
| `accounts/{accountId}/balances`                                           | a cada 2h     | 12            | 360           |
| `accounts/{accountId}/transactions-current`                               | a cada 3h     | 8             | 240           |
| **Cartão de Crédito**                                                     |               |               |               |
| `credit-cards-accounts`                                                   | semanal       | 0,14 em média | 4,3 aprox.    |
| `credit-cards-accounts/{creditCardAccountId}/limits`                      | a cada 3h     | 8             | 240           |
| `credit-cards-accounts/{creditCardAccountId}/transactions-current`        | a cada 3h     | 8             | 240           |
| `credit-cards-accounts/{creditCardAccountId}/bills`                       | 1x por dia    | 1             | 30            |
| `credit-cards-accounts/{creditCardAccountId}/bills/{billId}/transactions` | 1x por dia    | 1             | 30            |
| **Investimentos**                                                         |               |               |               |
| `bank-fixed-incomes/investments`                                          | 1x por dia    | 1             | 30            |
| `credit-fixed-incomes/investments`                                        | 1x por dia    | 1             | 30            |
| `funds/investments`                                                       | 1x por dia    | 1             | 30            |
| `variable-incomes/investments`                                            | 1x por dia    | 1             | 30            |
| `treasure-titles/investments`                                             | 1x por dia    | 1             | 30            |
| `{investmentType}/investments/{investmentId}/balances`                    | 1x por dia    | 1             | 30            |
| `{investmentType}/investments/{investmentId}/transactions-current`        | 1x por dia    | 1             | 30            |
| `variable-incomes/broker-notes/{brokerNoteId}`                            | 1x por dia    | 1             | 30            |
| **Câmbio**                                                                |               |               |               |
| `exchanges/operations`                                                    | semanal       | 0,14 em média | 4,3 aprox.    |
| `exchanges/operations/{operationId}`                                      | 1x por dia    | 1             | 30            |
| `exchanges/operations/{operationId}/events`                               | 1x por dia    | 1             | 30            |
