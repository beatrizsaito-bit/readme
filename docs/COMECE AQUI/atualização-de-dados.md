---
title: Atualização de dados
deprecated: false
hidden: false
metadata:
  robots: index
---
O Open Finance limita a quantidade de vezes que dados podem ser consultados. Quando o limite operacional é atingido, a consulta de dados retorna 423 e não permite a atualização do dado.

Considerando essas regras do Open Finance, o Data Link otimizou para permitir a consulta e atualização máxima de dados, a frequência de atualização pode ser consultada na tabela abaixo:

| Produto              | Dados                                                                                                             | Frequência                   |
| :------------------- | :---------------------------------------------------------------------------------------------------------------- | :--------------------------- |
| Consentimento        | Informações de consentimento, motivos de rejeição, status                                                         | 1 vez ao dia                 |
| Dados Cadastrais     | Dados cadastrais, relacionamento, qualificação                                                                    | Ao realizar um consentimento |
| Contas               | Dados de contas e detalhes (número da conta, listagem, tipo de conta)                                             | 1 vez por semana             |
| Contas               | Limites e saldos                                                                                                  | A cada 1h42min               |
| Contas               | Transações                                                                                                        | A cada 3h                    |
| Cartões              | Dados de cartões e detalhes (dígitos finais do cartão, listagem, tipo de cartão)                                  | 1 vez por semana             |
| Cartões              | Limites e transações                                                                                              | A cada 1h42min               |
| Investimentos        | Dados de investimentos e detalhes (listagem, tipo de investimento)                                                | 1 vez por semana             |
| Investimentos        | Movimentações e posições                                                                                          | A cada 6h                    |
| Contratos de crédito | Dados de contratos de crédito (empréstimos, investimento, antecipação de recebíveis, adiantamento a depositantes) | 1 vez por semana             |

<br />
