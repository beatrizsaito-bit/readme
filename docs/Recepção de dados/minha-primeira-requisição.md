---
title: Minha primeira requisição
excerpt: Passo-a-passo para a sua primeira requisição no sistema Lina
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
## Passo 1 - Artefatos Lina Distribuidor de dados

Entre em contato com [service.desk@linainfratech.com.br](mailto:service.desk@linainfratech.com.br) e solicite credenciais e artefatos para realização de testes na nossa Plataforma. Serão compartilhados:

- **Postman Collection** - possui todos os endpoints listados na nossa [documentação de APIs](https://lina-itp.readme.io/reference/get_api-v1-organisations) ;
- **Postman Environment** - contém todas as variáveis de ambiente necessárias para a realização das chamadas. _Importante:_ neste artefato, estão contidas as credenciais de cliente;
- **Swagger OAS 3.0** - também será compartilhada a última versão das definições de API do nosso Produto, que será sempre a versão corrente da nossa [documentação](https://lina-itp.readme.io/reference/get_api-v1-organisations)

## Passo 2 - Carregando Collection e Environment para a primeira chamada

 Clique no botão "importar" no canto esquerdo superior da aplicação Postman e importe ambos os arquivos (Collection e Environment) para a aplicação.

![](https://files.readme.io/8f3cdeec1ce872c2643917ca48640dca5b3ff758c5b3faf8587ca6b664626eea-image.png)

Clique no canto direito da aplicação e selecione o Environment enviado e previamente carregado na aplicação:

![](https://files.readme.io/eac46815a933ada307edec09817a9bda704a58da6715da6caad0703738564408-image.png)

Com o Environment carregado e a Postman Collection  à esquerda, podemos realizar a primeira chamada para validar o funcionamento das credenciais enviadas:

![](https://files.readme.io/ba492f1c114a9c8ec8da897506f9f8bac08e3b24d722c28cda8a714df93eb3dd-image.png)

Ao acessar a collection, clique na aba _Authorization_ ou _Autorização_, role ao final da página e clique no botão laranja. Caso tenha sucesso na chamada, a tela a seguir será exibida. Ao final, clique em _Use Token_ ou _Utilizar Token_ para confirmar e autenticar todas as chamadas subsequentes que serão realizadas a seguir.

![](https://files.readme.io/3e9e76c61dc014d18004addf1a9e314a3fb2eaea15ce5a170f7a425a50930ea4-image.png)

> 📘 Postman Collection - Autenticação
> 
> Todas as chamadas da postman collection serão autenticadas com o token obtido através dos passos acima. Não é necessário realizar a autenticação para cada uma das chamadas, já que o _refresh_ também é realizado por essa funcionalidade.

## Passo 3 - Listando as instituições disponíveis

A Postman Collection enviada possui numeração para orientar as chamadas de **Fluxo de consentimento** (mais sobre [consentimento](https://lina-itp.readme.io/docs/consentimento-do-usu%C3%A1rio) )

![](https://files.readme.io/bb72c9c4bb0e9ef9a7e05feb25c80deab9783d3a8cf6edc28a9dcb048e1703b7-image.png)

Após selecionar a instituição que deseja realizar o consentimento, copie o valor do campo `OrganisationId` na variável `organisation_id` e `AuthorisationServerId` na variável `authorisation_server_id` no canto direito superior no _environment_. Também é necessária o preenchimento da variável `user_cpf` com o CPF do usuário que realizará o aceite do consentimento. (para mais informações de como alterar as variáveis, acesse: <https://learning.postman.com/docs/sending-requests/variables/environment-variables/>.

## Passo 4 - Solicitação de consentimento

Com `organisation_id`, `authorisation_server_id` e `user_cpf` preenchidos, analise o `body` da requisição no campo `permissions` e siga as orientações dos comentários para adicionar, ou remover permissões que serão solicitadas para o usuário final. Algumas observações:

- `RESOURCES_READ`- campo obrigatório e deve ser preenchido em toda requisição
- Para usuários PF, necessário incluir: `CUSTOMERS_PERSONAL_IDENTIFICATIONS_READ` e `CUSTOMERS_PERSONAL_ADITTIONALINFO_READ` para acesso à dados cadastrais e de qualificação
- Para usuários PJ, necessário incluir: `CUSTOMERS_BUSINESS_IDENTIFICATIONS_READ` e `CUSTOMERS_BUSINESS_ADITTIONALINFO_READ` para acesso à dados cadastrais e de qualificação
- Dados de conta bancária: `ACCOUNTS_BALANCES_READ`, `ACCOUNTS_OVERDRAFT_LIMITS_READ`, `ACCOUNTS_READ`, `ACCOUNTS_TRANSACTIONS_READ`
- Dados de cartão de crédito: `CREDIT_CARDS_ACCOUNTS_READ`, `CREDIT_CARDS_ACCOUNTS_LIMITS_READ`, `CREDIT_CARDS_ACCOUNTS_TRANSACTIONS_READ`, `CREDIT_CARDS_ACCOUNTS_BILLS_READ`, `CREDIT_CARDS_ACCOUNTS_BILLS_TRANSACTIONS_READ`
- Dados de empréstimo: `LOANS_READ`, `LOANS_WARRANTIES_READ`, `LOANS_SCHEDULED_INSTALMENTS_READ`, `LOANS_PAYMENTS_READ`
- Dados de financiamento: `FINANCINGS_READ`, `FINANCINGS_WARRANTIES_READ`, `FINANCINGS_SCHEDULED_INSTALMENTS_READ`, `FINANCINGS_PAYMENTS_READ`
- Dados de adiantamento a depositantes: `UNARRANGED_ACCOUNTS_OVERDRAFT_READ`, `UNARRANGED_ACCOUNTS_OVERDRAFT_WARRANTIES_READ`, `UNARRANGED_ACCOUNTS_OVERDRAFT_SCHEDULED_INSTALMENTS_READ`, `UNARRANGED_ACCOUNTS_OVERDRAFT_PAYMENTS_READ`
- Dados de direitos creditórios: `INVOICE_FINANCINGS_READ`, `INVOICE_FINANCINGS_WARRANTIES_READ`, `INVOICE_FINANCINGS_SCHEDULED_INSTALMENTS_READ`, `INVOICE_FINANCINGS_PAYMENTS_READ`
- Dados de renda fixa bancária: `BANK_FIXED_INCOMES_READ`
- Dados de renda fixa de crédito: `CREDIT_FIXED_INCOMES_READ`
- Dados de fundos: `FUNDS_READ`
- Dados de renda variável: `VARIABLE_INCOMES_READ`
- Dados de títulos do tesouro: `TREASURE_TITLES_READ`

A partir desta definição, basta realizar a chamada `POST` para o endpoint listado. Em casos de sucesso, a resposta conterá uma `redirectUrl`que deve ser utilizada para o redirecionamento do usuário final, por exemplo:

```json json
{
    "redirectUrl": "https://auth.mockbank.poc.raidiam.io/auth?request_uri=urn%3Aietf%3Aparams%3Aoauth%3Arequest_uri%3AD2AKVKARaSdsGQ5KF_8Q8&client_id=yXYqweXJXhxqMebXy7j_e&state=WD2D99Nhn3nse80JoBP87n0E1IA8utKYxpxxDONIba2UPpTNGKLDod38gWlhhLexDgu9Y8xmuWzAJGhpibmDaNNG4bg3HzDYTIo3"
}
```

> 🚧 URL de redirecionamento
> 
> A URL de redirecionamento recebida nesta chamada é uma URL do banco destino (transmissor) e deve ser acessada somente uma vez por consentimento. Esta URL não poderá ser reutilizada e chamadas subsequentes apresentarão erro. Neste caso, reinicie o fluxo desde o passo 3 deste guia.

## Passo 5 - Login e acesso à Instituição financeira

> 📘 Acesso à instituição financeira
> 
> O acesso à instituição financeira deve ser realizada pelo usuário final - que por sua vez deve realizar o início da sessão no domínio da instituição financeira (seja por celular ou web). Vale lembrar que o ambiente é da instituição financeira e não temos controle sobre a jornada do usuário neste acesso.

Após o redirecionamento do usuário, basta realizar o login na plataforma digital da instituição, escolher os recursos a serem compartilhados (e.x. quais contas, cartões, investimentos, etc. que serão compartilhados) e confirmar o consentimento. Com o aceite de consentimento, o usuário será redirecionado para uma URL de domínio da Lina, ou URL destino que foi parametrizada pelo time Lina OpenX.

## Passo 6 - Redirecionamento final do usuário

> 📘 Redirecionamento Lina OpenX
> 
> Para clientes que ainda estão em fases de testes, o redirecionamento sempre ocorrerá para a página: <https://redirect-demo-opal.vercel.app/>. Para testar futuras integrações, basta inserir a URL de redirecionamento no campo de redirecionamento. Para clientes em produção a URL configurada no cadastro sempre será utilizada para casos de erro ou sucesso.

Ao aceitar o consentimento e ser informado do redirecionamento à Lina OpenX (i.e. receptora de dados), o usuário será redirecionado para a tela a seguir. Para dar sequencia à Jornada de Consentimento, basta copiar o `payload` no botão abaixo:

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/12d196f60033a28dd7b79198899fdafff72722f99642b075f0458ad271eba9c7-2024.09.17_validate_callback.png",
        "",
        ""
      ],
      "align": "center"
    }
  ]
}
[/block]


O conteúdo deve ser colado no corpo da requisição **1.3 - Validar Callback**, da Collection enviada. Ao colar a requisição - basta realizar a chamada e aguardar o retorno.

![](https://files.readme.io/42fa7b58cbc0b5bd585a9a8200ac12eac0c1e3bf15afdd6572f904001c874f2c-image.png)

## Passo 7 - Coletando `userId` e consultando dados

Ao executar o passo 6 - a resposta da chamada **1.3 - Validar Callback** irá retornar o campo `userId` no corpo da resposta. Este ID pode ser utilizado em todas chamadas subsequentes na pasta 2 e 3.

> 🚧 Importância do campo `userId`
> 
> Utilizamos o id do usuário como chave de identificação dos usuários na nossa base. Não realizamos consultas por informações pessoais como nomes e CPFs. Mesmo que um usuário realize inúmeros consentimentos (em diferentes instituições), sempre retornaremos o mesmo id de usuário - portanto, não existe a necessidade de armazenar diferentes IDs por transação.

A automatização da nossa Postman Collection já atrela o último ID de usuário obtido no passo 1.3 para a variável `user_id` do environment - portanto, cada chamada realizada no passo 1.3 da collection, a variável será sobescrita. A partir de agora, basta escolher o recurso que gostaria de consultar!

![](https://files.readme.io/989b31831326731def33342bc6c7e950b2ebc47f70564ae9fb7e227b7b2885be-image.png)