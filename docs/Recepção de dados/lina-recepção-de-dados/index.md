---
title: Lina Recepção de Dados
excerpt: >-
  Sua ferramenta de obtenção de dados financeiros em todas as instituições
  financeiras do Brasil
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
> 📘 A quem é destinado este produto
>
> Esta seção é dedicada para participantes indiretos do Open Finance Brasil, que buscam acesso aos dados de seus clientes (PF e PJ) em instituições financeiras brasileiras. Para os participantes diretos do Open Finance que gostaríam de utilizar licença, autorização, canais e UX próprios, disponibilizamos uma solução de recepção de dados financeiros (PF e PJ) no nível de infraestrutura que já possui todos os requisitos de segurança e funcionalidade para a operação de uma instituição receptora de dados.

## Níveis de dados e exemplos de utilização

O Produto de Dados da Lina ITP é composto por 3 níveis de dados:

<Image align="right" src="https://files.readme.io/c875e13b55261dbc34512be7b475d05cce8cd37e60364480b1856edb0bb05f8c-image.png" />

### Nível 1: Dados Brutos Agregados

Neste nível, os dados são armazenados e organizados para uma consulta agregada da vida financeira dos usuários (PJ e PF). No primeiro nível de serviço, os dados poderão ser consultados em diversas transmissoras, garantindo a visibilidade dos dados financeiros e de cadastro do usuário em diferentes domicílios bancários.

*E.x. Visualização de saldo de contas bancárias em diferentes bancos, e cálculo do saldo total consolidado.*

### Nível 2: Diagnóstico, Análise e Inferência

No segundo nível, oferecemos APIs e interfaces gráficas que exploram a sumarização dos dados coletados em diversas instituições tranmissoras, traçando médias de consumo por tempo determinado.

*E.x. Média de consumo, categorização e inferência de renda para usuários que realizaram a aprovação de consentimento na Plataforma Lina.*

### Nível 3: Predição e Prescrição

No terceiro nível, oferecemos APIs e interfaces gráficas que exploram o comportamento financeiro dos usuários (PF e PJ). Analisando o comportamento dos usuários, podemos prever padrões e seguir com prescrições financeiras para o usuário, automatizando processos como oferta de produtos/serviços financeiros e hiperpersonalização de produtos financeiros.

*E.x. Notificação via webhook para alerta de possível inadimplência, sugestão de investimento baseado no perfil do usuário, etc.*

## Integrações e interfaces

O produto de recepção de dados da Lina ITP é composto por 4 diferentes camadas/interfaces:

### APIs

APIs autenticadas disponíveis na internet para integração com as instituições transmissoras de dados Estas APIs são utilizadas para a integração entre serviços para o usuário final e a captura dos dados no ecossistema do Open Finance Brasil. Com estas APIs, é possível ter controle total sobre a Jornada de Consentimento e consumo de dados de usuários em instituições financeiras brasileiras.

### HDP (Hosted Data Page)

Página de dados hospedada na plataforma da Lina, whitelabel, que já possui incorpora todas as interações necessárias para a jornada de compartilhamento de dados. Esta página pode ser customizada para adequar a Marca do parceiro, conduzindo a Jornada de Consentimento por conta própria.

### EDP (Embedded Data Page)

Página de dados embeddada na aplicação dos nossos clientes utilizando os SDKs Lina. Os SDKs Lina promovem flexibilidade para a integração e utilização das funcionalidades de compartilhamento de dados. Desta forma, basta importar os SDKs nas aplicações dos parceiros e seguir os fluxos de integração definidos.

### Console Lina

Interface web desenvolvida e mantida pela Lina para gerenciamento dos recursos de consentimento, relatórios e análises de dados de clientes finais sem a necessidade de desenvolvimento próprio.
