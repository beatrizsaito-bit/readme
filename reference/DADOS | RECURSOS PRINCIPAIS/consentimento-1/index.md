---
title: Consentimento
hidden: false
---
<br />

# Permissões

<Callout icon="❗️" theme="error">
  A permissão **RESOURCES_READ** deve ser preenchida em toda requisição
</Callout>

Abaixo está a lista com as permissões necessários para cada agrupamento de dados

<Table align={["left","left"]}>
  <thead>
    <tr>
      <th>

      </th>

      <th>
        PERMISSÕES NECESSÁRIAS
      </th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <td>
        Dados cadastrais e de qualificação de usuário PF
      </td>

      <td>
        * `CUSTOMERS_PERSONAL_IDENTIFICATIONS_READ`
        * `CUSTOMERS_PERSONAL_ADITTIONALINFO_READ`
      </td>
    </tr>

    <tr>
      <td>
        Dados cadastrais e de qualificação de usuário PJ
      </td>

      <td>
        * `CUSTOMERS_BUSINESS_IDENTIFICATIONS_READ`
        * `CUSTOMERS_BUSINESS_ADITTIONALINFO_READ`
      </td>
    </tr>

    <tr>
      <td>
        Dados de conta bancária
      </td>

      <td>
        * `ACCOUNTS_READ`
        * `ACCOUNTS_BALANCES_READ`
        * `ACCOUNTS_OVERDRAFT_LIMITS_READ`
        * `ACCOUNTS_TRANSACTIONS_READ`
      </td>
    </tr>

    <tr>
      <td>
        Dados de cartão de crédito
      </td>

      <td>
        * `CREDIT_CARDS_ACCOUNTS_READ`
        * `CREDIT_CARDS_ACCOUNTS_LIMITS_READ`
        * `CREDIT_CARDS_ACCOUNTS_TRANSACTIONS_READ`
      </td>
    </tr>

    <tr>
      <td>
        Dados de fatura de cartão de crédito
      </td>

      <td>
        * `CREDIT_CARDS_ACCOUNTS_BILLS_READ`
        * `CREDIT_CARDS_ACCOUNTS_BILLS_TRANSACTIONS_READ`
      </td>
    </tr>

    <tr>
      <td>
        Dados de empréstimo
      </td>

      <td>
        * `LOANS_READ`
        * `LOANS_WARRANTIES_READ`
        * `LOANS_SCHEDULED_INSTALMENTS_READ`
        * `LOANS_PAYMENTS_READ`
      </td>
    </tr>

    <tr>
      <td>
        Dados de financiamento
      </td>

      <td>
        * `FINANCINGS_READ`
        * `FINANCINGS_WARRANTIES_READ`
        * `FINANCINGS_SCHEDULED_INSTALMENTS_READ`
        * `FINANCINGS_PAYMENTS_READ`
      </td>
    </tr>

    <tr>
      <td>
        Dados de adiantamento a depositantes
      </td>

      <td>
        * `UNARRANGED_ACCOUNTS_OVERDRAFT_READ`
        * `UNARRANGED_ACCOUNTS_OVERDRAFT_WARRANTIES_READ`
        * `UNARRANGED_ACCOUNTS_OVERDRAFT_SCHEDULED_INSTALMENTS_READ`
        * `UNARRANGED_ACCOUNTS_OVERDRAFT_PAYMENTS_READ`
      </td>
    </tr>

    <tr>
      <td>
        Dados de direitos creditórios
      </td>

      <td>
        * `INVOICE_FINANCINGS_READ`
        * `INVOICE_FINANCINGS_WARRANTIES_READ`
        * `INVOICE_FINANCINGS_SCHEDULED_INSTALMENTS_READ`
        * `INVOICE_FINANCINGS_PAYMENTS_READ`
      </td>
    </tr>

    <tr>
      <td>
        Dados de renda fixa bancária
      </td>

      <td>
        * `BANK_FIXED_INCOMES_READ`
      </td>
    </tr>

    <tr>
      <td>
        Dados de renda fixa de crédito
      </td>

      <td>
        * `CREDIT_FIXED_INCOMES_READ`
      </td>
    </tr>

    <tr>
      <td>
        Dados de fundos
      </td>

      <td>
        * `FUNDS_READ`
      </td>
    </tr>

    <tr>
      <td>
        Dados de renda variável
      </td>

      <td>
        * `VARIABLE_INCOMES_READ`
      </td>
    </tr>

    <tr>
      <td>
        Dados de títulos do tesouro
      </td>

      <td>
        * `TREASURE_TITLES_READ`
      </td>
    </tr>
  </tbody>
</Table>

# Estados do consentimento

<br />

| ESTADO                 | DESCRIÇÃO                                                                                                                                                                                                                                                                                                                                                        |
| :--------------------- | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| AWAITING AUTHORISATION | Estado inicial quando um consentimento é criado. Neste estado, o consentimento representa apenas uma intenção de compartilhamento, indicando quem é o cliente que irá realizar o compartilhamento, quais permissões estão sendo solicitadas e a sua data de validade. O usuário tem 60 minutos para concluir a aprovação.                                        |
| AUTHORISED             | Estado que indica que o consentimento foi aprovado pelo cliente e que é possível realizar o consumo de dados. Neste estado os recursos ao qual o consentimento dá acesso já foram selecionados. Apesar do consentimento estar aprovado, ainda poderão existir recursos cujo acesso dependa de uma aprovação de múltipla alçada (alguns casos de pessoa jurídica) |
| REJECTED               | Estado que indica que o consentimento foi revogado, que pode ocorrer por diferentes motivos,  como expiração do tempo máximo para autorização e aprovação do consentimento, vencimento da data de validade do consentimento após a sua aprovação ou ainda uma revogação explicita solicitada pelo cliente.                                                       |

<br />

![](https://files.readme.io/b5b95799ad6e575d242d243f2779880f2e3f46b908e58de18d58899a07cf6895-image.png)

<br />
