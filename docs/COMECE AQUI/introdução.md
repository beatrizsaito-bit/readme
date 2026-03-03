---
title: 'O que é o Data Link? '
deprecated: false
hidden: false
metadata:
  robots: index
---
O Data Link é a plataforma da Lina que conecta mais de 50 instituições financeiras no Open Finance, possibilitando a integração de dados diretamente da conta bancária do cliente, seja ele uma pessoa física ou jurídica. Tudo isso com base no consentimento do cliente, em linha com os mais elevados padrões de segurança e privacidade, e em total conformidade com as normas do BCB e com a LGPD.

Através do Data Link, o seu cliente realiza o consentimento de seus dados financeiros e esses dados podem ser utilizados para diferentes análises como hiperpersonalização de ofertas, análise de crédito, consolidação de carteira, entre outros.

<br />

O Data Link possui 3 camadas de dados disponíveis

* Agregação de Dados: Dados disponíveis no Open Finance são armazenados e disponibilizados através de APIs próprias
* Índices Financeiros: Cálculos financeiros, categorização de gastos e a consolidação de informações podem ser consultadas e implementadas a motores de decisão
* Inteligência de Dados: Modelos de machine learning para predição e prescrição contextual, como a inferência de renda e personalização de oferta

<br />

# Fluxo e consentimento de dados

![](https://files.readme.io/e8a19070f891846991837ea998c4d265aaaf182c5c642964f8ba8dfdb480828a-image.png)

<br />

1. Jornada de consentimento: O usuário realiza o consentimento dos dados. Ele escolhe quais dados deseja compartilhar e de qual instituição financeira.
2. Enquanto o consentimento estiver autorizado, o Data Link atualiza os dados financeiros consentidos e disponibiliza para a consulta via APIs próprias da Lina

<Callout icon="📘" theme="info">
  O acesso é restrito aos dados explicitamente autorizados pelo seu usuário final, seguindo a regulamentação do Open Finance
</Callout>

<br />

## Consentimento no Open Finance

No Open Finance, o usuário não precisa autorizar um compartilhamento único de todos os dados, há uma granularidade nos níveis de permissão. Por exemplo, é possível compartilhar os dados de **conta** e não compartilhar os dados de **investimentos**.

<br />

### **Validade do consentimento**

A validade do consentimento pode ser modificada pelo usuário, sendo que há a opção de o consentimento ficar disponível por tempo _indeterminado, ou seja, não ocorrerá a revogação automática do consentimento.

<br />

### **Revogação**

**Solicitada pelo usuário:** A revogação de um consentimento realizado pode ser solicitada a qualquer momento pelo usuário e tem efeito imediato, assim a partir desse momento novos dados não serão atualizados.

**Automática pelo prazo de validade:** Caso o consentimento tenha um tempo de expiração determinado, ao atingir essa data, o consentimento é revogado e novos dados param de ser atualizados.

<br />
