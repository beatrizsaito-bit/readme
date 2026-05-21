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

| Endpoint de recurso                   | Periodicidade | Execuções/mês |
| ------------------------------------- | ------------- | ------------- |
| Consentimentos                        | 1x por dia    | 30            |
| Contas                                | semanal       | 4,3 aprox.    |
| Saldo da conta                        | a cada 2h     | 360           |
| Transações de conta                   | a cada 3h     | 240           |
| Cartões de crédito                    | semanal       | 4,3 aprox.    |
| Limite de cartões de crédito          | a cada 3h     | 240           |
| `Transações de cartões de crédito     | a cada 3h     | 240           |
| Faturas de cartões de crédito         | 1x por dia    | 30            |
| Listagem de investimentos             | 1x por dia    | 30            |
| Saldos de investimentos               | 1x por dia    | 30            |
| Transações de investimentos           | 1x por dia    | 30            |
| Notas de corretagem de renda variável | 1x por dia    | 30            |
| Listagem de câmbio                    | semanal       | 4,3 aprox.    |
| Operações de câmbio                   | 1x por dia    | 30            |
