---
title: Jornada Utilizandos as APIs
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
As Apis para Iniciação foram projetados para simplificar o processo de iniciação de pagamentos,  
reduzindo significativamente o tempo e os recursos necessários para que as empresas possam oferecer  
a seus clientes uma experiência de pagamento moderna e eficiente.  
Com a nossa solução, você pode aproveitar os benefícios do Open Finance, uma das maiores inovações no setor financeiro.

Ao realizar uma chamada ao método `GET /participants/registered` serão retornadas as intituições vinculadas e habilitadas para operação de pagamento.

Selecionada a instituição, deve realizar uma chamada no método `POST /consents` para ser aberta uma solicitação de pagamento e retornado uma **"redirectUrl"**,  
onde deverá ser acessada para dar prosseguimento no consentimento e conclusão do pagamento.  
Após a finalização do processo do pagamento a página será redirecianada para o caminho informado no **"redirectUri"** do body  
informado no POST do processo de `/consents`.

> 📘 O campo `redirectUri` enviado a chamada `POST /consents` se refere à URL que o usuário será redirecionado após a conclusão do pagamento. Essa URL deve estar preparada para receber o retorno da conclusão do pagamento. A responsabilidade pela manutenção dessa URL é exclusivamente do cliente da LINA, não da LINA.

Nesse retorno também virá via query string a informação do **"paymentLinkId"** que será utilizado para realização da  
consulta via `GET /payments/requests/{paymentLinkId}`, e validar o status do request se está como CONSUMIDO e dentro da lista de pagamentos o status confirmando que ele está PAGO ou em caso de pagamentos agendado no futuro PENDENTE.

![](https://files.readme.io/5d4a5c86f832399c2f88fa7199e918768266e502ba30017a3a469a2c3cbb64d6-image.png)