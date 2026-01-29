---
title: Consentimentos
hidden: false
---
# Estrutura do Objeto

<Accordion title="consentId">
  **Descrição**\
  Identificador único do consentimento no formato

  **Mandatoriedade**\
  Obrigatório

  **Tipo de dado JSON**\
  `string`
</Accordion>

<Accordion title="creationDateTime">
  **Descrição**\
  Data e hora de criação do recurso UTC.

  **Mandatoriedade**\
  Obrigatório

  **Tipo de dado JSON**\
  `string`
</Accordion>

<Accordion title="status">
  **Descrição**\
  Estado atual do consentimento cadastrado

  * AUTHORISED
  * AWAITING\_AUTHORISATION
  * REJECTED

  **Mandatoriedade**\
  Obrigatório

  **Tipo de dado JSON**\
  `string`
</Accordion>

<Accordion title="statusUpdateDateTime">
  **Descrição**\
  Data e hora da última atualização do consentimento em UTC.

  **Mandatoriedade**\
  Obrigatório

  **Tipo de dado JSON**\
  `string`
</Accordion>

<Accordion title="permissions">
  **Descrição**\
  Lista de permissões concedidas para acesso às APIs do Open Finance Brasil.

  **Mandatoriedade**\
  Obrigatório

  **Tipo de dado JSON**\
  `array`
</Accordion>

<Accordion title="expirationDateTime">
  **Descrição**\
  Data e hora de expiração do consentimento em apenas quando houver validade determinada.

  **Mandatoriedade**\
  Condicional

  **Tipo de dado JSON**\
  `string`
</Accordion>

<Accordion title="rejection">
  **Descrição**\
  Objeto retornado quando o consentimento for rejeitado.

  **Mandatoriedade**\
  Condicional

  **Tipo de dado JSON**\
  `object`

  <Accordion title="rejectedBy" icon="fa-info-circle">
    **Descrição**\
    Identifica quem realizou a rejeição do consentimento.

    * USER usuário
    * ASPSP instituição transmissora
    * TPP instituição receptora

    **Mandatoriedade**\
    Condicional

    **Tipo de dado JSON**\
    `string`
  </Accordion>

  <Accordion title="reason" icon="fa-info-circle">
    **Descrição**\
    Detalha o motivo da rejeição do consentimento

    **Mandatoriedade**\
    Condicional

    **Tipo de dado JSON**\
    `object`

    <Accordion title="code" icon="fa-info-circle">
      **Descrição**\
      Código padronizado que representa a razão da rejeição.

      * CONSENT\_EXPIRED – consentimento que ultrapassou o tempo limite para autorização.
      * CUSTOMER\_MANUALLY\_REJECTED – cliente efetuou a rejeição do consentimento manualmente através de interação nas instituições participantes.
      * CUSTOMER\_MANUALLY\_REVOKED – cliente efetuou a revogação após a autorização do consentimento.
      * CONSENT\_MAX\_DATE\_REACHED – consentimento que ultrapassou o tempo limite de compartilhamento.
      * CONSENT\_TECHNICAL\_ISSUE – consentimento que foi rejeitado devido a um problema técnico que impossibilita seu uso pela instituição receptora, por exemplo: falha associada a troca do AuthCode pelo AccessToken, durante o processo de Hybrid Flow.
      * INTERNAL\_SECURITY\_REASON – consentimento que foi rejeitado devido as políticas de segurança aplicada pela instituição transmissora.

      **Mandatoriedade**\
      Condicional

      **Tipo de dado JSON**\
      `string`
    </Accordion>
  </Accordion>
</Accordion>

<Accordion title="additionalInformation">
  **Descrição**\
  Informações adicionais fornecidas pela instituição transmissora.

  **Mandatoriedade**\
  Opcional

  **Tipo de dado JSON**\
  `string`
</Accordion>

<Accordion title="journey">
  **Descrição**\
  Informações adicionais relacionadas à Jornada Otimizada.

  **Mandatoriedade**\
  Opcional

  **Tipo de dado JSON**\
  `object`
</Accordion>

<Accordion title="isLinked">
  **Descrição**\
  Indica se o consentimento foi iniciado via Jornada Otimizada.

  **Mandatoriedade**\
  Opcional

  **Tipo de dado JSON**\
  `boolean`
</Accordion>

<Accordion title="linkId">
  **Descrição**\
  Identificador do consentimento de pagamento ou vínculo relacionado.

  **Mandatoriedade**\
  Opcional

  **Tipo de dado JSON**\
  `string`
</Accordion>

<br />

<br />
