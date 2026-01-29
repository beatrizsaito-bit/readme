---
title: Referência
deprecated: false
hidden: false
icon: far fa-file-lines
metadata:
  robots: index
---
<br />

## 📄 Estrutura do Objeto 

<Table>
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
        consentId
      </td>

      <td>
        Identificador único do consentimento no formato 
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
        creationDateTime
      </td>

      <td>
        Data e hora de criação do recurso  UTC.
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
        status
      </td>

      <td>
        Estado atual do consentimento cadastrado  

        * AUTHORISED
        * AWAITING_AUTHORISATION
        * REJECTED
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
        statusUpdateDateTime
      </td>

      <td>
        Data e hora da última atualização do consentimento em UTC.
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
        permissions
      </td>

      <td>
        Lista de permissões concedidas para acesso às APIs do Open Finance Brasil. 
      </td>

      <td>
        Obrigatório
      </td>

      <td>
        `array`
      </td>
    </tr>

    <tr>
      <td>
        expirationDateTime
      </td>

      <td>
        Data e hora de expiração do consentimento em apenas quando houver validade determinada.
      </td>

      <td>
        Condicional
      </td>

      <td>
        `string`
      </td>
    </tr>

    <tr>
      <td>
        rejection
      </td>

      <td>
        Objeto retornado quando o consentimento for rejeitado.
      </td>

      <td>
        Opcional
      </td>

      <td>
        `object`
      </td>
    </tr>

    <tr>
      <td>
        additionalInformation
      </td>

      <td>
        Informações adicionais fornecidas pela instituição transmissora.
      </td>

      <td>
        Opcional
      </td>

      <td>
        `string`
      </td>
    </tr>

    <tr>
      <td>
        journey
      </td>

      <td>
        Informações adicionais relacionadas à Jornada Otimizada.
      </td>

      <td>
        Opcional
      </td>

      <td>
        `object`
      </td>
    </tr>

    <tr>
      <td>
        isLinked
      </td>

      <td>
        Indica se o consentimento foi iniciado via Jornada Otimizada.
      </td>

      <td>
        Opcional
      </td>

      <td>
        `boolean`
      </td>
    </tr>

    <tr>
      <td>
        linkId
      </td>

      <td>
        Identificador do consentimento de pagamento ou vínculo relacionado.
      </td>

      <td>
        Opcional
      </td>

      <td>
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

<br />
