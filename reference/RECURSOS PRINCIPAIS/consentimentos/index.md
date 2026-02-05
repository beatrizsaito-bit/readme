---
title: Consentimentos
deprecated: false
hidden: false
metadata:
  robots: index
---
# Permissões

<Callout icon="❗️" theme="error">
  A permissão **RESOURCES_READ** deve ser preenchida em toda requisição
</Callout>

Abaixo está a lista com as permissões necessários para cada agrupamento de dados

<Accordion title="Dados cadastrais e de qualificação de usuário PF" icon="fa-user">

- `CUSTOMERS_PERSONAL_IDENTIFICATIONS_READ`
- `CUSTOMERS_PERSONAL_ADITTIONALINFO_READ`
</Accordion>

<Accordion title="Dados cadastrais e de qualificação de usuário PJ" icon="fa-building">
**Permissões necessárias**

- `CUSTOMERS_BUSINESS_IDENTIFICATIONS_READ`
- `CUSTOMERS_BUSINESS_ADITTIONALINFO_READ`
</Accordion>

<Accordion title="Dados de conta bancária" icon="fa-university">
**Permissões necessárias**

- `ACCOUNTS_READ`
- `ACCOUNTS_BALANCES_READ`
- `ACCOUNTS_OVERDRAFT_LIMITS_READ`
- `ACCOUNTS_TRANSACTIONS_READ`
</Accordion>

<Accordion title="Dados de cartão de crédito" icon="fa-credit-card">
**Permissões necessárias**

- `CREDIT_CARDS_ACCOUNTS_READ`
- `CREDIT_CARDS_ACCOUNTS_LIMITS_READ`
- `CREDIT_CARDS_ACCOUNTS_TRANSACTIONS_READ`
</Accordion>

<Accordion title="Dados de fatura de cartão de crédito" icon="fa-file-invoice-dollar">
**Permissões necessárias**

- `CREDIT_CARDS_ACCOUNTS_BILLS_READ`
- `CREDIT_CARDS_ACCOUNTS_BILLS_TRANSACTIONS_READ`
</Accordion>

<Accordion title="Dados de empréstimo" icon="fa-hand-holding-usd">
**Permissões necessárias**

- `LOANS_READ`
- `LOANS_WARRANTIES_READ`
- `LOANS_SCHEDULED_INSTALMENTS_READ`
- `LOANS_PAYMENTS_READ`
</Accordion>

<Accordion title="Dados de financiamento" icon="fa-coins">
**Permissões necessárias**

- `FINANCINGS_READ`
- `FINANCINGS_WARRANTIES_READ`
- `FINANCINGS_SCHEDULED_INSTALMENTS_READ`
- `FINANCINGS_PAYMENTS_READ`
</Accordion>

<Accordion title="Dados de adiantamento a depositantes" icon="fa-money-bill-wave">
**Permissões necessárias**

- `UNARRANGED_ACCOUNTS_OVERDRAFT_READ`
- `UNARRANGED_ACCOUNTS_OVERDRAFT_WARRANTIES_READ`
- `UNARRANGED_ACCOUNTS_OVERDRAFT_SCHEDULED_INSTALMENTS_READ`
- `UNARRANGED_ACCOUNTS_OVERDRAFT_PAYMENTS_READ`
</Accordion>

<Accordion title="Dados de direitos creditórios" icon="fa-file-contract">
**Permissões necessárias**

- `INVOICE_FINANCINGS_READ`
- `INVOICE_FINANCINGS_WARRANTIES_READ`
- `INVOICE_FINANCINGS_SCHEDULED_INSTALMENTS_READ`
- `INVOICE_FINANCINGS_PAYMENTS_READ`
</Accordion>

<Accordion title="Dados de renda fixa bancária" icon="fa-piggy-bank">
**Permissões necessárias**

- `BANK_FIXED_INCOMES_READ`
</Accordion>

<Accordion title="Dados de renda fixa de crédito" icon="fa-chart-line">
**Permissões necessárias**

- `CREDIT_FIXED_INCOMES_READ`
</Accordion>

<Accordion title="Dados de fundos" icon="fa-layer-group">
**Permissões necessárias**

- `FUNDS_READ`
</Accordion>

<Accordion title="Dados de renda variável" icon="fa-chart-area">
**Permissões necessárias**

- `VARIABLE_INCOMES_READ`
</Accordion>

<Accordion title="Dados de títulos do tesouro" icon="fa-landmark">
**Permissões necessárias**

- `TREASURE_TITLES_READ`
</Accordion>


<br />

<Table align={["left","left"]}>
  <thead>
    <tr>
      <th>
        Função
      </th>

      <th>
        Permissões necessárias
      </th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <td>
        Dados cadastrais e de qualificação de usuário PF
      </td>

      <td>
        CUSTOMERS_PERSONAL_IDENTIFICATIONS_READ,

        CUSTOMERS_PERSONAL_ADITTIONALINFO_READ
      </td>
    </tr>

    <tr>
      <td>
        Dados cadastrais e de qualificação de usuário PJ
      </td>

      <td>
        CUSTOMERS_BUSINESS_IDENTIFICATIONS_READ,

        CUSTOMERS_BUSINESS_ADITTIONALINFO_READ
      </td>
    </tr>

    <tr>
      <td>
        Dados de conta bancária
      </td>

      <td>
        ACCOUNTS_BALANCES_READ,

        ACCOUNTS_OVERDRAFT_LIMITS_READ,

        ACCOUNTS_READ,

        ACCOUNTS_TRANSACTIONS_READ
      </td>
    </tr>

    <tr>
      <td>
        Dados de cartão de crédito
      </td>

      <td>
        CREDIT_CARDS_ACCOUNTS_READ,

        CREDIT_CARDS_ACCOUNTS_LIMITS_READ,

        CREDIT_CARDS_ACCOUNTS_TRANSACTIONS_READ,
      </td>
    </tr>

    <tr>
      <td>
        Dados de fatura de cartão de crédito
      </td>

      <td>
        CREDIT_CARDS_ACCOUNTS_BILLS_READ,

        CREDIT_CARDS_ACCOUNTS_BILLS_TRANSACTIONS_READ
      </td>
    </tr>

    <tr>
      <td>
        Dados de empréstimo
      </td>

      <td>
        LOANS_READ, LOANS_WARRANTIES_READ,

        LOANS_SCHEDULED_INSTALMENTS_READ,

        LOANS_PAYMENTS_READ
      </td>
    </tr>

    <tr>
      <td>
        Dados de financiamento
      </td>

      <td>
        FINANCINGS_READ,

        FINANCINGS_WARRANTIES_READ,

        FINANCINGS_SCHEDULED_INSTALMENTS_READ,

        FINANCINGS_PAYMENTS_READ
      </td>
    </tr>

    <tr>
      <td>
        Dados de adiantamento a depositantes
      </td>

      <td>
        UNARRANGED_ACCOUNTS_OVERDRAFT_READ,

        UNARRANGED_ACCOUNTS_OVERDRAFT_WARRANTIES_READ,

        UNARRANGED_ACCOUNTS_OVERDRAFT_SCHEDULED_INSTALMENTS_READ,

        UNARRANGED_ACCOUNTS_OVERDRAFT_PAYMENTS_READ
      </td>
    </tr>

    <tr>
      <td>
        Dados de direitos creditórios
      </td>

      <td>
        INVOICE_FINANCINGS_READ,

        INVOICE_FINANCINGS_WARRANTIES_READ,

        INVOICE_FINANCINGS_SCHEDULED_INSTALMENTS_READ,

        INVOICE_FINANCINGS_PAYMENTS_READ
      </td>
    </tr>

    <tr>
      <td>
        Dados de renda fixa bancária
      </td>

      <td>
        BANK_FIXED_INCOMES_READ
      </td>
    </tr>

    <tr>
      <td>
        Dados de renda fixa de crédito
      </td>

      <td>
        CREDIT_FIXED_INCOMES_READ
      </td>
    </tr>

    <tr>
      <td>
        Dados de fundos
      </td>

      <td>
        FUNDS_READ
      </td>
    </tr>

    <tr>
      <td>
        Dados de renda variável
      </td>

      <td>
        VARIABLE_INCOMES_READ
      </td>
    </tr>

    <tr>
      <td>
        Dados de títulos do tesouro
      </td>

      <td>
        TREASURE_TITLES_READ
      </td>
    </tr>
  </tbody>
</Table>

<br />

# Estados do consentimento

<Accordion title="AWAITING AUTHORISATION">
  Estado inicial quando um consentimento é criado. Neste estado, o consentimento representa apenas uma intenção de compartilhamento, indicando quem é o cliente que irá realizar o compartilhamento, quais permissões estão sendo solicitadas e a sua data de validade.

  Neste momento ainda não estão definidos os recursos a serem compartilhados.
</Accordion>

<Accordion title="AUTHORISED">
  Estado que indica que o consentimento foi aprovado pelo cliente e que é possível realizar o consumo de dados. Neste estado os recursos ao qual o consentimento dá acesso já foram selecionados. Apesar do consentimento estar aprovado, ainda poderão existir recursos cujo acesso dependa de uma aprovação de múltipla alçada (alguns casos de pessoa jurídica)
</Accordion>

<Accordion title="REJECTED">
  Estado que indica que o consentimento foi revogado, que pode ocorrer por diferentes motivos,  como expiração do tempo máximo para autorização e aprovação do consentimento, vencimento da data de validade do consentimento após a sua aprovação ou ainda uma revogação explicita solicitada pelo cliente.
</Accordion>

<Image border={false} src="https://files.readme.io/b5b95799ad6e575d242d243f2779880f2e3f46b908e58de18d58899a07cf6895-image.png" />

<br />

## Usuário responsável pela rejeição

<Accordion title="USER">
  Usuário
</Accordion>

<Accordion title="ASPSP">
  Instituição transmissora
</Accordion>

<Accordion title="TPP">
  Instituição receptora
</Accordion>
