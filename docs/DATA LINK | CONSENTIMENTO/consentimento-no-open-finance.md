---
title: 'Consentimento de dados '
deprecated: false
hidden: false
metadata:
  robots: index
---
O consentimento no Open Finance é a autorização que o seu cliente deve conceder para que ocorra o envio de dados entre a instituição financeira e o Data Link. O seu cliente pode ser **pessoa física** ou **pessoa jurídica**, em ambos os casos é possível realizar o consentimento de dados.

Dentro do Open Finance é possível obter consentimento dos seguintes dados: **cadastrais**, **contas**,  **cartões de crédito**, **contratos de crédito**, **investimentos** e **câmbio**.

<Cards>
  <Card title="Dados cadastrais" href="https://lina-itp.readme.io/reference/getpersonaldata">
    Informações do dono da conta (PF/PJ), relacionamento com banco e qualificação
  </Card>

  <Card title="Contas" href="https://api.datalink.com.br/v1/api/v1/users/{user_id}/accounts">
    Listagem de contas, saldos e transações
  </Card>

  <Card title="Cartões" href="https://lina-itp.readme.io/reference/listcreditcards">
    Informações do cartão (bandeira, produto, etc), limites, faturas e transações
  </Card>

  <Card title="Contratos de crédito" href="https://lina-itp.readme.io/reference/listcreditcontracts">
    Empréstimos, financeimentos, antecipáveis e pagamentos dos contratos
  </Card>
</Cards>

## Revogação e validade do consentimento

O consentimento por ser **revogado a qualquer momento pelo usuário**ou pode ser que tenha sido revogado pela **expiração do prazo de validade**.

A expiração automática do consentimento é definida em sua criação no campo **validade do consentimento**, caso esse campo esteja como indeterminado não haverá revogação automática.

<br />

<br />
