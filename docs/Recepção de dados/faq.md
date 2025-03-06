---
title: FAQ
excerpt: ''
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
1. **Quantas vezes posso consultar os dados dos meus usuários?**\
   Não existe limite para consulta de dados na Plataforma Lina OpenX. Realizamos atualizações periódicas dos dados para garantir a precisão e relevância dos dados disponibilizados, respeitando os prazos de disponibilização de dados e limites operacionais do Open Finance Brasil.
2. **Como posso garantir que os dados dos meus usuários estão corretos?**\
   Disponibilizamos endpoints para a atualização forçada das informações dos usuários. Para isso, basta seguir as instruções dos endpoints de force sync disponíveis no swagger da API.
3. **Quando sei que os dados que estou consultando estão atualizados?**\
   A cada componente atualizado, enviamos o timestamp da última atualização para o conjunto de dados consultados campo:updatedAt.
4. **Qual é a frequência de atualização dos dados?**\
   Seguimos a seguinte tabela de frequência de atualizações:

| Produto              | Dados                                                                             | Frequência                 |
| -------------------- | --------------------------------------------------------------------------------- | -------------------------- |
| Consentimento        | Informações de consentimento, motivos de rejeição e status                        | 1 vez ao dia               |
| Dados Cadastrais     | Dados cadastrais, relacionamento e qualificação                                   | Não é atualizado na rotina |
| Contas               | Dados de contas e detalhes (número da conta, listagem e tipo de conta)            | Não é atualizado na rotina |
| Contas               | Limites e saldos                                                                  | 14 vezes ao dia            |
| Contas               | Transações                                                                        | 8 vezes ao dia             |
| Cartões              | Dados de cartões e detalhes (dígitos finais do cartão, listagem e tipo de cartão) | Não é atualizado na rotina |
| Cartões              | Limites e transações                                                              | 14 vezes ao dia            |
| Investimentos        | Dados de investimentos e detalhes (listagem e tipo de investimento)               | Não é atualizado na rotina |
| Investimentos        | Movimentações e posições                                                          | 4 vezes ao dia             |
| Contratos de crédito | Dados de contratos de crédito (garantias e detalhes do contrato)                  | Não é atualizado na rotina |
