---
title: Nível 1 - Dados Brutos Agregados
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
Os dados brutos são o nível mais básico de dados disponíveis na Plataforma Lina OpenX. Neste nível, os dados são compostos pelos dados pessoais e financeiros dos clientes, agregados de acordo com cada instituição transmissora que o usuário possui relacionamento.

## Estrutura dos Dados Brutos

A estrutura dos dados brutos - assim como os endpoints de consulta - são baseados na especificação oficial do Open Finance Brasil. Neste nível, disponibilizamos interfaces programáticas e gráficas para realizar a consulta de dados financeiros e cadastrais de usuários em diversas instituições transmissoras, armazenando e clusterizando os dados de cada usuário para consulta.

## Estruturação de dados

Para o Nível de Dados Brutos, seguimos a estrutura de dados do Open Finance porém é criado um vínculo dos dados aos usuários, possibilitando uma listagem de dados (um conjunto para cada instituição transmissora) a ser consultado.

```json Exemplo Open Finance
// Chamada #1 para instituição A accounts/
{
    "data": [
       {
            "brandName": "Organização A",
            "companyCnpj": "21128159000166",
            "type": "CONTA_DEPOSITO_A_VISTA",
            "compeCode": "001",
            // demais informações...
        }
    ]
}
// Chamada #2 para instituição A accounts/:id
{
    "data": [
       {
            "number": "24550245",
            "checkDigit": "4",
            "type": "CONTA_DEPOSITO_A_VISTA",
            // demais informações...
        }
    ]
}

// Chamada #3 para instituição B /accounts
{
    "data": [
        {
            "brandName": "Organização B",
            "companyCnpj": "0123465783291",
            "type": "CONTA_DEPOSITO_A_VISTA",
            "compeCode": "001",
            // demais informações...
        }
    ]
}
```
```Text Exemplo Lina Open X
// Chamada para Lina OpenX /users/:id/accounts

{
    "data": [
         {
        "accountId": "291e5a29-49ed-401f-a583-193caa7acddd",
        "authorisationServerId": "c8f0bf49-4744-4933-8960-7add6e590841",
        "branchCode": "6272",
        // informações de conta e instituição...
        "details": {
            "compeCode": "123",
            // demais informações...
        },
        "balance": {
            // informações de saldo...
            "updateDateTime": "2024-09-09T10:53:52Z"
        },
        "overdraftLimits": {
            // informações de limite...
            "updateDateTime": "2024-09-09T10:53:52Z"
        }
    ]
}
```
