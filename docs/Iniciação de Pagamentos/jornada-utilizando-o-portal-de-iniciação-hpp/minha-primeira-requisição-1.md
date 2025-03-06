---
title: Minha primeira requisição
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
## Passo 1 - Artefatos Lina Iniciação Pagamentos

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

![](https://files.readme.io/547fa7a0db09c15490d3f67986b4d71fde2f7de68aab66517941a176c4794d88-image.png)

Ao acessar a collection, clique na aba _Authorization_ ou _Autorização_, role ao final da página e clique no botão laranja. Caso tenha sucesso na chamada, a tela a seguir será exibida. Ao final, clique em _Use Token_ ou _Utilizar Token_ para confirmar e autenticar todas as chamadas subsequentes que serão realizadas a seguir.

![](https://files.readme.io/3e9e76c61dc014d18004addf1a9e314a3fb2eaea15ce5a170f7a425a50930ea4-image.png)

> 📘 Postman Collection - Autenticação
> 
> Todas as chamadas da postman collection serão autenticadas com o token obtido através dos passos acima. Não é necessário realizar a autenticação para cada uma das chamadas, já que o _refresh_ também é realizado por essa funcionalidade.

## Passo 3 - Iniciando uma Solicitação de Pagamento

A Postman Collection enviada possui uma pasta de "Porta HPP", deve ser realizada a chamada do método "POST" -  
"/payments - Create Payment", informando no body as informações do detalhes do pagamento. Os campos obrigatórios podem ser consultado no detalhamento da API.

> 🚧 URL de redirecionamento
> 
> A URL de redirecionamento informada nesta chamada **redirectUri **é uma URL onde o sistema irá retornar após a realização do pagamento e conterá a informação do **paymentLinkId **para consultar o Status do pagamento.

![](https://files.readme.io/d06b8355ca0c8f1a8523df0bd94cd868d4c6df0b45f0d3ad00edcf074ca61dcb-image.png)

Após a realização da chamada é retornado a URL de redirecionamento para o Portal de Iniciação, além do Id de consulta do "Payment Request".

![](https://files.readme.io/2207475fa45127370b8e2adc8d9010d70fd5b6df7a479157b0b6bdc7f319aaf0-image.png)

## Passo 4 - Copie a URL e abra no navegador

Copie a URL gerada e abra no browser do navegador, será observado os detalhes do pagamento que foi iniciado via a API.

![](https://files.readme.io/b6c656971785a359263b918f51164b1b99748d0a68a33ac283bb574460b72303-image.png)

## Passo 5 - Confirme o CPF/CNPJ e selecione a Instituição Detentora

Clique em Seguir com o mesmo CPF/CNPJ, irá para a tela da seleção da Instituição detentora de conta para realização do pagamento. Vamos utilizar a Mock Bank.

> 📘 Ambiente de Homologação
> 
> No ambiente de homologação utilizamos a Instituição detentora de contas do Mock Bank. O CPF que ela aceita para realização de testes é o "76109277673"

![](https://files.readme.io/c3e62465999f36f1ef9f93251a0e95f8c2a200c98f4233bba7039a18ac7d2270-image.png)

## Passo 6 - Confira os dados e redirecione para a Instituição Detentora

Após a seleção será exibida a tela com o detalhamento da instituição, além das informações da conta que está sendo creditada. Clique em redirecionar para ir para a confirmação do pagamento na página da detentora.

![](https://files.readme.io/ffdc9bd69a3cccf82eeb3ee2e6555d385b71ef321946f8526fc29329fbd20269-image.png)

A aplicação irá redirecionar o Portal para a Instituição Detentora.

![](https://files.readme.io/b4f471f6df3c7824dc220a949410f5c1c0ec570a39a2f1bbd6d37b41b783e3b9-image.png)

## Passo 6 - Informe os dados de acesso na Instituição Detentora.

Informe o usuário em senha de acesso.

> 📘 Ambiente de Homologação
> 
> No ambiente de homologação utilizamos a Instituição detentora de contas do Mock Bank. O usuário e senha são:  
> [ralph.bragg@gmail.com](mailto:ralph.bragg@gmail.com)  
> P@ssword01

![](https://files.readme.io/ecd8567780d208566b3179ca0e6cb6e3ad60fad6c1976348093bd241b0e012e2-image.png)

## Passo 7 - Confirme o Consentimento para a realização do pagamento

Na instituição detentora será informado todo o detalhamento do pagamento que está sendo realizado, para que seja feito o consentimento pelo usuário.

![](https://files.readme.io/1254c63c48f898d939ba6a74a0f82a87121c89fb612ff55a3f134e6ae30cc1c1-image.png)

Após a confirmação o pagamento será realizado e retornado para a URL informada no campo "redirectUri" ("<https://redirect-demo-opal.vercel.app">) do Body inicial da API. No retorno é concatenado o "paymentLinkId" que deve ser utilizado para consultar o Status do Pagamento.

![](https://files.readme.io/7fb37bea49c31b7545d7c9ba45d6c8a161c23093b846eb9a65d660152d80602f-image.png)

## Passo 8 - Consulte o Payment Request via API para verificar o Status do Pagamento.

A Postman Collection enviada possui uma pasta de "Consultas", onde deve ser realizada a chamada do método "GET" -  
"/payments/requests/:id- Get Payment Request", para verificar o status do pagamento realizado.

![](https://files.readme.io/be6dece395aafc294c3d0593e65e4ef318079337dc811060c4d0b257e655aef4-image.png)