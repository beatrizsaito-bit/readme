---
title: Realizando um consentimento
deprecated: false
hidden: false
icon: fab fa-confluence
metadata:
  robots: index
---
<br />

# Passo 1 - Liste as instituições disponíveis



<Callout icon="📘" theme="info">
  A Postman Collection disponível para download possui numeração para orientar as chamadas de Fluxo de consentimento.
</Callout>

Realize a consulta no endpoint de listagem de insituições participantes do Open Finance.  

Cada instituição possuem um **OrganisationId**  e do **AuthorisationServerId**, identifique e copie os valores da instituição que será solicitado o consentimento.

# Passo 2- Solicitação de consentimento

Para caso de consentimento de pessoa física será necessário o CPF do usuário. Para casos de pessoa jurídica é necessário o CPF de um dos sócios e o CNPJ da pessoa jurídica.

Você precisará enviar o `organisation_id`, `authorisation_server_id` e `user_cpf` preenchidos, além das permissões que deseja consultar.

<Callout icon="❗️">
  A permissão **RESOURCES_READ** deve ser preenchida em toda requisição
</Callout>

Abaixo está a lista com as permissões necessários para cada agrupamento de dados

<Table align={["left","left"]}>
  <thead>
    <tr>
      <th>
        Função
      </th>

      <th>
        Permissão necessãria
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

A partir desta definição, basta realizar a chamada POST para o endpoint listado. Em casos de sucesso, a resposta conterá uma redirectUrlque deve ser utilizada para o redirecionamento do usuário final, por exemplo:

```Text Redirect
{
  "redirectUrl": "https://auth.mockbank.poc.raidiam.io/auth?request_uri=urn%3Aietf%3Aparams%3Aoauth%3Arequest_uri%3AD2AKVKARaSdsGQ5KF_8Q8&client_id=yXYqweXJXhxqMebXy7j_e&state=WD2D99Nhn3nse80JoBP87n0E1IA8utKYxpxxDONIba2UPpTNGKLDod38gWlhhLexDgu9Y8xmuWzAJGhpibmDaNNG4bg3HzDYTIo3"
}
```

<br />

<Callout icon="📘" theme="info">
  **URL de redirecionamento**

  A URL de redirecionamento recebida nesta chamada é uma URL do banco destino (transmissor) e deve ser acessada somente uma vez por consentimento. Esta URL não poderá ser reutilizada e chamadas subsequentes apresentarão erro. Neste caso, reinicie o fluxo desde o passo 3 deste guia.
</Callout>

<br />
