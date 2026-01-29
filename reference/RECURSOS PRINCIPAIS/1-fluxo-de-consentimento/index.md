---
title: Consentimentos
hidden: false
---
# Estrutura do Objeto

<Accordion title="consentId">
**Descrição**  
Identificador único do consentimento no formato

**Mandatoriedade**  
Obrigatório

**Tipo de dado JSON**  
`string`
</Accordion>

<Accordion title="creationDateTime">
**Descrição**  
Data e hora de criação do recurso UTC.

**Mandatoriedade**  
Obrigatório

**Tipo de dado JSON**  
`string`
</Accordion>

<Accordion title="status">
**Descrição**  
Estado atual do consentimento cadastrado

- AUTHORISED  
- AWAITING_AUTHORISATION  
- REJECTED  

**Mandatoriedade**  
Obrigatório

**Tipo de dado JSON**  
`string`
</Accordion>

<Accordion title="statusUpdateDateTime">
**Descrição**  
Data e hora da última atualização do consentimento em UTC.

**Mandatoriedade**  
Obrigatório

**Tipo de dado JSON**  
`string`
</Accordion>

<Accordion title="permissions">
**Descrição**  
Lista de permissões concedidas para acesso às APIs do Open Finance Brasil.

**Mandatoriedade**  
Obrigatório

**Tipo de dado JSON**  
`array`
</Accordion>

<Accordion title="expirationDateTime">
**Descrição**  
Data e hora de expiração do consentimento em apenas quando houver validade determinada.

**Mandatoriedade**  
Condicional

**Tipo de dado JSON**  
`string`
</Accordion>

<Accordion title="rejection">
**Descrição**  
Objeto retornado quando o consentimento for rejeitado.

**Mandatoriedade**  
Opcional

**Tipo de dado JSON**  
`object`
</Accordion>

<Accordion title="additionalInformation">
**Descrição**  
Informações adicionais fornecidas pela instituição transmissora.

**Mandatoriedade**  
Opcional

**Tipo de dado JSON**  
`string`
</Accordion>

<Accordion title="journey">
**Descrição**  
Informações adicionais relacionadas à Jornada Otimizada.

**Mandatoriedade**  
Opcional

**Tipo de dado JSON**  
`object`
</Accordion>

<Accordion title="isLinked">
**Descrição**  
Indica se o consentimento foi iniciado via Jornada Otimizada.

**Mandatoriedade**  
Opcional

**Tipo de dado JSON**  
`boolean`
</Accordion>

<Accordion title="linkId">
**Descrição**  
Identificador do consentimento de pagamento ou vínculo relacionado.

**Mandatoriedade**  
Opcional

**Tipo de dado JSON**  
`string`
</Accordion>




<Table align={["left","left","left","left"]}>
  <thead>
    <tr>
      <th style={{ textAlign: "left" }}>
        campo
      </th>

      <th style={{ textAlign: "left" }}>
        Descrição
      </th>

      <th style={{ textAlign: "left" }}>
        Mandatoriedade
      </th>

      <th style={{ textAlign: "left" }}>
        Tipo de Dado JSON
      </th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <td style={{ textAlign: "left" }}>
        consentId
      </td>

      <td style={{ textAlign: "left" }}>
        Identificador único do consentimento no formato
      </td>

      <td style={{ textAlign: "left" }}>
        Obrigatório
      </td>

      <td style={{ textAlign: "left" }}>
        `string`
      </td>
    </tr>

    <tr>
      <td style={{ textAlign: "left" }}>
        creationDateTime
      </td>

      <td style={{ textAlign: "left" }}>
        Data e hora de criação do recurso  UTC.
      </td>

      <td style={{ textAlign: "left" }}>
        Obrigatório
      </td>

      <td style={{ textAlign: "left" }}>
        `string`
      </td>
    </tr>

    <tr>
      <td style={{ textAlign: "left" }}>
        status
      </td>

      <td style={{ textAlign: "left" }}>
        Estado atual do consentimento cadastrado

        * AUTHORISED
        * AWAITING_AUTHORISATION
        * REJECTED
      </td>

      <td style={{ textAlign: "left" }}>
        Obrigatório
      </td>

      <td style={{ textAlign: "left" }}>
        `string`
      </td>
    </tr>

    <tr>
      <td style={{ textAlign: "left" }}>
        statusUpdateDateTime
      </td>

      <td style={{ textAlign: "left" }}>
        Data e hora da última atualização do consentimento em UTC.
      </td>

      <td style={{ textAlign: "left" }}>
        Obrigatório
      </td>

      <td style={{ textAlign: "left" }}>
        `string`
      </td>
    </tr>

    <tr>
      <td style={{ textAlign: "left" }}>
        permissions
      </td>

      <td style={{ textAlign: "left" }}>
        Lista de permissões concedidas para acesso às APIs do Open Finance Brasil.
      </td>

      <td style={{ textAlign: "left" }}>
        Obrigatório
      </td>

      <td style={{ textAlign: "left" }}>
        `array`
      </td>
    </tr>

    <tr>
      <td style={{ textAlign: "left" }}>
        expirationDateTime
      </td>

      <td style={{ textAlign: "left" }}>
        Data e hora de expiração do consentimento em apenas quando houver validade determinada.
      </td>

      <td style={{ textAlign: "left" }}>
        Condicional
      </td>

      <td style={{ textAlign: "left" }}>
        `string`
      </td>
    </tr>

    <tr>
      <td style={{ textAlign: "left" }}>
        rejection
      </td>

      <td style={{ textAlign: "left" }}>
        Objeto retornado quando o consentimento for rejeitado.
      </td>

      <td style={{ textAlign: "left" }}>
        Opcional
      </td>

      <td style={{ textAlign: "left" }}>
        `object`
      </td>
    </tr>

    <tr>
      <td style={{ textAlign: "left" }}>
        additionalInformation
      </td>

      <td style={{ textAlign: "left" }}>
        Informações adicionais fornecidas pela instituição transmissora.
      </td>

      <td style={{ textAlign: "left" }}>
        Opcional
      </td>

      <td style={{ textAlign: "left" }}>
        `string`
      </td>
    </tr>

    <tr>
      <td style={{ textAlign: "left" }}>
        journey
      </td>

      <td style={{ textAlign: "left" }}>
        Informações adicionais relacionadas à Jornada Otimizada.
      </td>

      <td style={{ textAlign: "left" }}>
        Opcional
      </td>

      <td style={{ textAlign: "left" }}>
        `object`
      </td>
    </tr>

    <tr>
      <td style={{ textAlign: "left" }}>
        isLinked
      </td>

      <td style={{ textAlign: "left" }}>
        Indica se o consentimento foi iniciado via Jornada Otimizada.
      </td>

      <td style={{ textAlign: "left" }}>
        Opcional
      </td>

      <td style={{ textAlign: "left" }}>
        `boolean`
      </td>
    </tr>

    <tr>
      <td style={{ textAlign: "left" }}>
        linkId
      </td>

      <td style={{ textAlign: "left" }}>
        Identificador do consentimento de pagamento ou vínculo relacionado.
      </td>

      <td style={{ textAlign: "left" }}>
        Opcional
      </td>

      <td style={{ textAlign: "left" }}>
        `string`
      </td>
    </tr>
  </tbody>
</Table>

## Consents`permissions`

## Consents`rejection`

<Table align={["left","left","left","left"]}>
  <thead>
    <tr>
      <th>
        campo
      </th>

      <th>
        Descrição
      </th>

      <th>
        Mandatoriedade
      </th>

      <th>
        Tipo de Dado JSON
      </th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <td>
        rejectedBy
      </td>

      <td>
        Identifica quem realizou a rejeição do consentimento.

        * USER usuário
        * ASPSP instituição transmissora
        * TPP instituição receptora
      </td>

      <td>
        Obrigatório
      </td>

      <td>
        `string`
      </td>
    </tr>

    <tr>
      <td>
        reason
      </td>

      <td>
        Detalha o motivo da rejeição do consentimento.
      </td>

      <td>
        Obrigatório
      </td>

      <td>
        `object`
      </td>
    </tr>

    <tr>
      <td>
        code
      </td>

      <td>
        Código padronizado que representa a razão da rejeição.

        * CONSENT_EXPIRED – consentimento que ultrapassou o tempo limite para autorização.
        * CUSTOMER_MANUALLY_REJECTED – cliente efetuou a rejeição do consentimento manualmente através de interação nas instituições participantes.
        * CUSTOMER_MANUALLY_REVOKED – cliente efetuou a revogação após a autorização do consentimento.
        * CONSENT_MAX_DATE_REACHED – consentimento que ultrapassou o tempo limite de compartilhamento.
        * CONSENT_TECHNICAL_ISSUE – consentimento que foi rejeitado devido a um problema técnico que impossibilita seu uso pela instituição receptora, por exemplo: falha associada a troca do AuthCode pelo AccessToken, durante o processo de Hybrid Flow.
        * INTERNAL_SECURITY_REASON – consentimento que foi rejeitado devido as políticas de segurança aplicada pela instituição transmissora.
      </td>

      <td>
        Obrigatório
      </td>

      <td>
        `string`
      </td>
    </tr>
  </tbody>
</Table>
