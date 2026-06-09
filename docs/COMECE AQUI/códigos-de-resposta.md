---
title: Códigos de resposta
deprecated: false
hidden: true
metadata:
  robots: index
---
<br />

A DataLink API utiliza códigos de status HTTP padrão para indicar o resultado de cada requisição.

| Código | Significado         | O que fazer                                                                                        |
| :----- | :------------------ | :------------------------------------------------------------------------------------------------- |
| `200`  | Sucesso             | A requisição foi processada com êxito.                                                             |
| `400`  | Requisição inválida | Verifique os campos obrigatórios e o formato dos dados enviados.                                   |
| `401`  | Não autorizado      | Token ausente, expirado ou inválido. Gere um novo token de acesso.                                 |
| `404`  | Não encontrado      | O recurso informado (usuário, consentimento, conta) não existe.                                    |
| `422`  | Não processável     | A instituição ou servidor de autorização informado não foi encontrado.                             |
| `423`  | Recurso bloqueado   | Limite operacional de consultas do Open Finance atingido. O dado será atualizado no próximo ciclo. |
| `429`  | Muitas requisições  | Limite de requisições atingido. Aguarde e tente novamente com intervalo crescente.                 |
| `500`  | Erro interno        | Erro inesperado no servidor. Se persistir, entre em contato com o suporte.                         |

# Formato de erro

As respostas de erro seguem um formato consistente:

```json
{
  "error": "NOT_FOUND",
  "message": "Consentimento não encontrado para o usuário informado.",
  "statusCode": 404
}
```

<Callout icon="📘" theme="info">
  Em caso de dúvida sobre um erro específico, informe ao suporte o `message` retornado e o horário aproximado da requisição.
</Callout>
