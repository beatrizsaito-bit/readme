---
title: Jornada Utilizando o Portal de Iniciação (HPP)
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
O Portal de Iniciação foi projetado para simplificar o processo de iniciação de pagamentos,\
reduzindo significativamente o tempo e os recursos necessários para que as empresas possam oferecer\
a seus clientes uma experiência de pagamento moderna e eficiente.\
Com a nossa solução, você pode aproveitar os benefícios do Open Finance, uma das maiores inovações no setor financeiro.

Ao realizar uma chamada no método `POST /payments` é aberta uma solicitação de pagamento e retornado uma **"redirectUrl"**,\
onde deverá ser acessada para dar prosseguimento no consentimento e conclusão do pagamento.\
Após a finalização do processo do pagamento a página será redireciOnada para o caminho informado no **"redirectUri"** do body\
informado no POST inicial do processo.

> 📘 O campo `redirectUri` enviado a chamada `POST /payments` se refere à URL que o usuário será redirecionado após a conclusão do pagamento. Essa URL deve estar preparada para receber o retorno da conclusão do pagamento. A responsabilidade pela manutenção dessa URL é exclusivamente do cliente da LINA, não da LINA.

Nesse retorno também virá via query string a informação do **"paymentLinkId"** que será utilizado para realização da\
consulta via `GET /payments/requests/{paymentLinkId}`, e validar o status do request se está como CONSUMIDO e dentro da lista de pagamentos o status confirmando que ele está PAGO ou em caso de pagamentos agendado no futuro PENDENTE.

![](https://files.readme.io/86db68a81dabb05294790cfc5501b16ddd89934002c539b12cae3e9131086cf8-image.png)
