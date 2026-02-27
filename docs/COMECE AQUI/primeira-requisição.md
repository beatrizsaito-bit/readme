---
title: Primeira requisição
deprecated: false
hidden: false
metadata:
  robots: index
---
<br />

# Passo 1 - Carregando Collection e Environment para a primeira chamada

Clique no botão "importar" no canto esquerdo superior da aplicação Postman e importe ambos os arquivos (Collection e Environment) para a aplicação.

![](https://files.readme.io/3ad062e2ec0d019c90b21a118ee8860d9b11fba86aa17f98007cff3adc577aa6-image.png)

Clique no canto direito da aplicação e selecione o Environment enviado e previamente carregado na aplicação:

![](https://files.readme.io/b74b85c7254bdf774034f9b0c90f84fdd7bf980fe3085881c17e8fc66a876a56-image.png)

Com o Environment carregado e a Postman Collection à esquerda, podemos realizar a primeira chamada para validar o funcionamento das credenciais enviadas:

![](https://files.readme.io/433ba4174da2b43719023b93da38b85d7d732fac87d2b08774f871b1b2a6da7c-image.png)

Ao acessar a collection, clique na aba Authorization ou Autorização, role ao final da página e clique no botão laranja. Caso tenha sucesso na chamada, a tela a seguir será exibida. Ao final, clique em Use Token ou Utilizar Token para confirmar e autenticar todas as chamadas subsequentes que serão realizadas a seguir

![](https://files.readme.io/89cc72838cba29587e8e0412352bda599a744be845182e47f966e93cea54fa57-image.png)

<Callout icon="📘" theme="info">
  Postman Collection - Autenticação

  Todas as chamadas da postman collection serão autenticadas com o token obtido através dos passos acima. Não é necessário realizar a autenticação para cada uma das chamadas, já que o refresh também é realizado por essa funcionalidade.
</Callout>

<br />

<br />

# Passo 2 - Liste as instituições disponíveis

<Callout icon="📘" theme="info">
  A Postman Collection disponível para download possui numeração para orientar as chamadas de Fluxo de consentimento.
</Callout>

Realize a consulta no endpoint de listagem de insituições participantes do Open Finance.

Cada instituição possuem um **OrganisationId**  e do **AuthorisationServerId**, identifique e copie os valores da instituição que será solicitado o consentimento.

# Passo 3- Solicitação de consentimento

Para caso de consentimento de pessoa física será necessário o CPF do usuário. Para casos de pessoa jurídica é necessário o CPF de um dos sócios e o CNPJ da pessoa jurídica.

Você precisará enviar o `organisation_id`, `authorisation_server_id` e `user_cpf` preenchidos, além das permissões que deseja consultar.

<Callout icon="📘" theme="info">
  **Observação**

  Para ambiente de homologação, utilize os valores de `organisation_id` , `authorisation_server_id` e CPF mockados do  **Mock Bank**
</Callout>

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

A partir desta definição, basta realizar a chamada POST para o endpoint listado. Em casos de sucesso, a resposta conterá uma redirectUrl que deve ser utilizada para o redirecionamento do usuário final, por exemplo:

```Text Redirect
{
  "redirectUrl": "https://auth.mockbank.poc.raidiam.io/auth?request_uri=urn%3Aietf%3Aparams%3Aoauth%3Arequest_uri%3AD2AKVKARaSdsGQ5KF_8Q8&client_id=yXYqweXJXhxqMebXy7j_e&state=WD2D99Nhn3nse80JoBP87n0E1IA8utKYxpxxDONIba2UPpTNGKLDod38gWlhhLexDgu9Y8xmuWzAJGhpibmDaNNG4bg3HzDYTIo3"
}
```

<Callout icon="📘" theme="info">
  **URL de redirecionamento**

  A URL de redirecionamento recebida nesta chamada é uma URL do banco destino (transmissor) e deve ser acessada somente uma vez por consentimento. Esta URL não poderá ser reutilizada e chamadas subsequentes apresentarão erro. Neste caso, reinicie o fluxo desde o passo 3 deste guia.
</Callout>

# Passo 4 - Login e acesso à Instituição financeira

<Callout icon="📘" theme="info">
  **Acesso à instituição financeira**

  O acesso à instituição financeira deve ser realizada pelo usuário final - que por sua vez deve realizar o início da sessão no domínio da instituição financeira (seja por celular ou web). Vale lembrar que o ambiente é da instituição financeira e não temos controle sobre a jornada do usuário neste acesso.
</Callout>

Após o redirecionamento, o usuário deverá realizar login na sua instituição financeira e finalizar a autorização do consentimento. Após a autorização ele será redirecionado para a URL parametrizada.

# Passo 5 - Redirecionamento final do usuário

<Callout icon="📘" theme="info">
  **Redirecionamento Lina OpenX**

  Para clientes que ainda estão em fases de testes, o redirecionamento sempre ocorrerá para a página:
  Redirect Demo Page . Para testar futuras integrações, basta inserir a URL de redirecionamento no campo de redirecionamento. Para clientes em produção a URL configurada no cadastro sempre será utilizada para casos de erro ou sucesso.
</Callout>

# Passo 6 - Coletando userId e consultando dados

<Callout icon="⚠️" theme="warn">
  **Importância do campo userId**

  Utilizamos o id do usuário como chave de identificação dos usuários na nossa base. Não realizamos consultas por informações pessoais como nomes e CPFs. Mesmo que um usuário realize inúmeros consentimentos (em diferentes instituições), sempre retornaremos o mesmo id de usuário - portanto, não existe a necessidade de armazenar diferentes IDs por transação.
</Callout>

Através da consulta da rota /api/v1/users/ é possível verificar o userId de todos os usuários com consentimento em sua base.
