---
title: Consentimentos
deprecated: false
hidden: false
metadata:
  robots: index
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

A partir desta definição, basta realizar a chamada POST para o endpoint listado. Em casos de sucesso, a resposta conterá uma redirectUrlque deve ser utilizada para o redirecionamento do usuário final, por exemplo:

```Text Redirect
{
  "redirectUrl": "https://auth.mockbank.poc.raidiam.io/auth?request_uri=urn%3Aietf%3Aparams%3Aoauth%3Arequest_uri%3AD2AKVKARaSdsGQ5KF_8Q8&client_id=yXYqweXJXhxqMebXy7j_e&state=WD2D99Nhn3nse80JoBP87n0E1IA8utKYxpxxDONIba2UPpTNGKLDod38gWlhhLexDgu9Y8xmuWzAJGhpibmDaNNG4bg3HzDYTIo3"
}
```

<Callout icon="📘" theme="info">
  **URL de redirecionamento**

  A URL de redirecionamento recebida nesta chamada é uma URL do banco destino (transmissor) e deve ser acessada somente uma vez por consentimento. Esta URL não poderá ser reutilizada e chamadas subsequentes apresentarão erro. Neste caso, reinicie o fluxo desde o passo 3 deste guia.
</Callout>

# Passo 3 - Login e acesso à Instituição financeira

<Callout icon="📘" theme="info">
  **Acesso à instituição financeira**

  O acesso à instituição financeira deve ser realizada pelo usuário final - que por sua vez deve realizar o início da sessão no domínio da instituição financeira (seja por celular ou web). Vale lembrar que o ambiente é da instituição financeira e não temos controle sobre a jornada do usuário neste acesso.
</Callout>

Após o redirecionamento, o usuário deverá realizar login na sua instituição financeira e finalizar a autorização do consentimento. Após a autorização ele será redirecionado para a URL parametrizada.

# Passo 4 - Redirecionamento final do usuário

<Callout icon="📘" theme="info">
  **Redirecionamento Lina OpenX**

  Para clientes que ainda estão em fases de testes, o redirecionamento sempre ocorrerá para a página:
  Redirect Demo Page . Para testar futuras integrações, basta inserir a URL de redirecionamento no campo de redirecionamento. Para clientes em produção a URL configurada no cadastro sempre será utilizada para casos de erro ou sucesso.
</Callout>

# Passo 5 - Coletando userId e consultando dados

<Callout icon="⚠️" theme="warn">
  **Importância do campo userId**

  Utilizamos o id do usuário como chave de identificação dos usuários na nossa base. Não realizamos consultas por informações pessoais como nomes e CPFs. Mesmo que um usuário realize inúmeros consentimentos (em diferentes instituições), sempre retornaremos o mesmo id de usuário - portanto, não existe a necessidade de armazenar diferentes IDs por transação.
</Callout>

Através da consulta da rota /api/v1/users/ é possível verificar o userId de todos os usuários com consentimento em sua base.

<br />
