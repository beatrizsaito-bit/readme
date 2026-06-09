---
api:
  file: datalink_openapi_inline.yaml
  operationId: get_new-endpoint
hidden: true
link:
  new_tab: false
metadata:
  robots: index
---
<br />

```json
{
  "openapi": "3.0.3",
  "info": { "title": "DataLink API", "version": "1.0.0" },
  "servers": [
    { "url": "https://itp-dados.linaopenx.com.br", "description": "Produção" },
    { "url": "https://itp-dados.hml.linaopenx.com.br", "description": "Homologação" }
  ],
  "security": [{ "bearerAuth": [] }],
  "paths": {
    "/api/v1/consents": {
      "post": {
        "tags": ["Consentimento"],
        "summary": "Criar consentimento",
        "description": "Inicia o fluxo de criação de um consentimento Open Finance para um usuário final (pessoa física ou jurídica). Retorna uma URL de redirecionamento para que o usuário autorize o acesso aos dados na instituição financeira selecionada.\n",
        "operationId": "createConsent",
        "requestBody": {
          "required": true,
          "content": {
            "application/json": {
              "schema": {
                "type": "object",
                "required": ["organisationId", "authorisationServerId", "consent"],
                "properties": {
                  "organisationId": {
                    "type": "string",
                    "description": "Identificador único da organização (instituição financeira). Obtido no endpoint de Instituições Participantes.",
                    "example": "74e929d9-33b6-4d85-8ba7-c146c867a817"
                  },
                  "authorisationServerId": {
                    "type": "string",
                    "description": "Identificador do servidor de autorização da instituição. Obtido no campo `AuthorisationServerId` dentro de `AuthorisationServers` no endpoint de Instituições Participantes.",
                    "example": "c8f0bf49-4744-4933-8960-7add6e590841"
                  },
                  "consent": {
                    "type": "object",
                    "required": ["loggedUser", "permissions"],
                    "description": "Dados do usuário e permissões solicitadas.",
                    "properties": {
                      "loggedUser": {
                        "type": "object",
                        "description": "Identificação do usuário. Informe `cpf` para Pessoa Física ou `cnpj` para Pessoa Jurídica.",
                        "properties": {
                          "cpf": {
                            "type": "string",
                            "description": "CPF do usuário (apenas dígitos, 11 caracteres). Obrigatório para PF.",
                            "example": "12345678909"
                          },
                          "cnpj": {
                            "type": "string",
                            "description": "CNPJ da empresa (apenas dígitos, 14 caracteres). Obrigatório para PJ.",
                            "example": "11222333000181"
                          }
                        }
                      },
                      "permissions": {
                        "type": "array",
                        "description": "Lista de permissões solicitadas. Deve incluir `RESOURCES_READ` e ao menos uma permissão de dados. Algumas permissões possuem dependências (ex.: `ACCOUNTS_BALANCES_READ` requer `ACCOUNTS_READ`).",
                        "minItems": 1,
                        "items": {
                          "type": "string",
                          "enum": [
                            "RESOURCES_READ",
                            "CUSTOMERS_PERSONAL_IDENTIFICATIONS_READ",
                            "CUSTOMERS_PERSONAL_ADITTIONALINFO_READ",
                            "CUSTOMERS_BUSINESS_IDENTIFICATIONS_READ",
                            "CUSTOMERS_BUSINESS_ADITTIONALINFO_READ",
                            "ACCOUNTS_READ",
                            "ACCOUNTS_BALANCES_READ",
                            "ACCOUNTS_OVERDRAFT_LIMITS_READ",
                            "ACCOUNTS_TRANSACTIONS_READ",
                            "CREDIT_CARDS_ACCOUNTS_READ",
                            "CREDIT_CARDS_ACCOUNTS_LIMITS_READ",
                            "CREDIT_CARDS_ACCOUNTS_TRANSACTIONS_READ",
                            "CREDIT_CARDS_ACCOUNTS_BILLS_READ",
                            "CREDIT_CARDS_ACCOUNTS_BILLS_TRANSACTIONS_READ",
                            "LOANS_READ",
                            "LOANS_WARRANTIES_READ",
                            "LOANS_SCHEDULED_INSTALMENTS_READ",
                            "LOANS_PAYMENTS_READ",
                            "FINANCINGS_READ",
                            "FINANCINGS_WARRANTIES_READ",
                            "FINANCINGS_SCHEDULED_INSTALMENTS_READ",
                            "FINANCINGS_PAYMENTS_READ",
                            "UNARRANGED_ACCOUNTS_OVERDRAFT_READ",
                            "UNARRANGED_ACCOUNTS_OVERDRAFT_WARRANTIES_READ",
                            "UNARRANGED_ACCOUNTS_OVERDRAFT_SCHEDULED_INSTALMENTS_READ",
                            "UNARRANGED_ACCOUNTS_OVERDRAFT_PAYMENTS_READ",
                            "INVOICE_FINANCINGS_READ",
                            "INVOICE_FINANCINGS_WARRANTIES_READ",
                            "INVOICE_FINANCINGS_SCHEDULED_INSTALMENTS_READ",
                            "INVOICE_FINANCINGS_PAYMENTS_READ",
                            "BANK_FIXED_INCOMES_READ",
                            "CREDIT_FIXED_INCOMES_READ",
                            "FUNDS_READ",
                            "VARIABLE_INCOMES_READ",
                            "TREASURE_TITLES_READ"
                          ]
                        }
                      }
                    }
                  }
                }
              },
              "examples": {
                "pessoa_fisica": {
                  "summary": "Pessoa Física (PF)",
                  "value": {
                    "organisationId": "74e929d9-33b6-4d85-8ba7-c146c867a817",
                    "authorisationServerId": "c8f0bf49-4744-4933-8960-7add6e590841",
                    "consent": {
                      "loggedUser": { "cpf": "12345678909" },
                      "permissions": [
                        "RESOURCES_READ",
                        "CUSTOMERS_PERSONAL_IDENTIFICATIONS_READ",
                        "CUSTOMERS_PERSONAL_ADITTIONALINFO_READ",
                        "ACCOUNTS_READ",
                        "ACCOUNTS_BALANCES_READ",
                        "ACCOUNTS_OVERDRAFT_LIMITS_READ",
                        "ACCOUNTS_TRANSACTIONS_READ",
                        "CREDIT_CARDS_ACCOUNTS_READ",
                        "CREDIT_CARDS_ACCOUNTS_LIMITS_READ",
                        "CREDIT_CARDS_ACCOUNTS_TRANSACTIONS_READ",
                        "CREDIT_CARDS_ACCOUNTS_BILLS_READ",
                        "CREDIT_CARDS_ACCOUNTS_BILLS_TRANSACTIONS_READ",
                        "LOANS_READ",
                        "LOANS_WARRANTIES_READ",
                        "LOANS_SCHEDULED_INSTALMENTS_READ",
                        "LOANS_PAYMENTS_READ",
                        "BANK_FIXED_INCOMES_READ",
                        "FUNDS_READ",
                        "VARIABLE_INCOMES_READ",
                        "TREASURE_TITLES_READ"
                      ]
                    }
                  }
                },
                "pessoa_juridica": {
                  "summary": "Pessoa Jurídica (PJ)",
                  "value": {
                    "organisationId": "74e929d9-33b6-4d85-8ba7-c146c867a817",
                    "authorisationServerId": "c8f0bf49-4744-4933-8960-7add6e590841",
                    "consent": {
                      "loggedUser": { "cnpj": "11222333000181" },
                      "permissions": [
                        "RESOURCES_READ",
                        "CUSTOMERS_BUSINESS_IDENTIFICATIONS_READ",
                        "CUSTOMERS_BUSINESS_ADITTIONALINFO_READ",
                        "ACCOUNTS_READ",
                        "ACCOUNTS_BALANCES_READ",
                        "ACCOUNTS_TRANSACTIONS_READ"
                      ]
                    }
                  }
                }
              }
            }
          }
        },
        "responses": {
          "200": {
            "description": "Consentimento criado com sucesso.",
            "content": {
              "application/json": {
                "schema": {
                  "type": "object",
                  "properties": {
                    "consentId": {
                      "type": "string",
                      "description": "Identificador único do consentimento no formato URN. Utilize este ID em todas as consultas subsequentes de dados do usuário.",
                      "example": "urn:banco:6a10b48f-0479-4214-83d5-5ffb6a1f16aa"
                    },
                    "redirectUrl": {
                      "type": "string",
                      "description": "URL de autorização na instituição financeira. Use para redirecionar o usuário ao banco. Válida apenas enquanto o status é `AWAITING_AUTHORISATION`.",
                      "example": "https://auth.bancobmg.com.br/of-auth/realms/bmg/protocol/openid-connect/auth?client_id=datalink&..."
                    },
                    "redirectUserUrl": {
                      "type": "string",
                      "description": "URL intermediária da Lina que resolve o redirecionamento para a instituição financeira.",
                      "example": "https://itp-dados.linaopenx.com.br/api/v1/consents/redirect/urn:banco:6a10b48f?tenant=lina"
                    }
                  }
                },
                "examples": {
                  "OK": {
                    "summary": "OK",
                    "value": {
                      "redirectUrl": "https://auth.banco.com.br/authorize?request_uri=urn%3Aietf%3Aparams%3Aoauth%3Arequest_uri%3AD2AKVKARaSdsGQ5KF_8Q8&client_id=25548518981519&state=FCfO8Ncq",
                      "redirectUserUrl": "https://itp-dados.linaopenx.com.br/api/v1/consents/redirect/urn:banco:6a10b48f-0479-4214-83d5-5ffb6a1f16aa?tenant=lina",
                      "consentId": "urn:banco:6a10b48f-0479-4214-83d5-5ffb6a1f16aa"
                    }
                  }
                }
              }
            }
          },
          "400": { "description": "Requisição inválida. Verifique os campos obrigatórios e o formato dos dados." },
          "401": { "description": "Não autorizado. Token ausente ou inválido." },
          "422": { "description": "Entidade não processável. A instituição ou servidor de autorização informado não foi encontrado." }
        }
      }
    }
  },
  "components": {
    "securitySchemes": {
      "bearerAuth": { "type": "http", "scheme": "bearer", "bearerFormat": "JWT" }
    }
  }
}
```
