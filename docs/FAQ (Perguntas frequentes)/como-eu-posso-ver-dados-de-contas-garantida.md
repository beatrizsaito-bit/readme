---
title: Como eu posso ver dados de conta garantida?
deprecated: false
hidden: false
metadata:
  robots: index
---
Conta garantida é uma modalidade de **contrato de crédito** e a circular nº 2957 do Banco Central. Em algumas instituições financeiras esse produto pode ser apresentado em uma interface como de **conta corrente**, entretanto como o tipo de produto financeiro é diferente esses dados ficam disponíveis na **[API de Empréstimos](https://lina-itp.readme.io/reference/get_api-v1-users-user-id-credit-contracts-credit-type-contract-id-payments)**.

Para consultar os dados de conta garantida, utilize a referência o endpoint:

```json endpoint
/api/v1/users/{user_id}/credit-contracts/loans/{contract_id}
```

A conta será indicada no retorno do **productSubType** como **CONTA_GARANTIDA**:

```json
{
	"contractId": "dadd421d-184e-4689-a085-409d1bca4193",
  "authorisationServerId": "c8f0bf49-4744-4933-8960-7add6e590841",
	"brandName": "XPTO",
	"companyCnpj": "13832718000196",
	"ipocCode": "01181521040211011740907325668478542336597",
  "organisationId": "74e929d9-33b6-4d85-8ba7-c146c867a817",
	"productSubType": "CONTA_GARANTIDA",
	"productType": "EMPRESTIMOS",
  "updatedAt": "2025-09-23T15:19:28.718Z",
} 

```

<br />