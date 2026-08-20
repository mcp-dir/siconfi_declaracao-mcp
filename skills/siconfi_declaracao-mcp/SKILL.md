---
name: siconfi_declaracao-mcp
description: Skill da REST API do SICONFI: Declaração Fiscal na MCP.AI: 1 endpoint em /api/siconfi_declaracao. SICONFI: Declaração Fiscal, consulta em fonte oficial. Hospedado pela plataforma, sem credenciais da plataforma, pague por consulta com crédito pré-pago. Autentique com workspace API key (sk_live) gerada em app.mcp.ai/settings/api-keys. Use quando o usuário pedir algo coberto pelos endpoints.
---

# SICONFI: Declaração Fiscal — REST API skill

Você tem acesso à **SICONFI: Declaração Fiscal** REST API na MCP.AI.

> SICONFI: Declaração Fiscal, consulta em fonte oficial. Hospedado pela plataforma, sem credenciais da plataforma, pague por consulta com crédito pré-pago.

## Base URL

```
https://api.mcp.ai/api/siconfi_declaracao
```

Todo endpoint é um **POST** na Base URL + o path abaixo. Os parâmetros vão no corpo JSON.

## Autenticação

Inclua em toda request:

```
Authorization: Bearer sk_live_...
Content-Type: application/json
```

> Gere sua chave em **https://app.mcp.ai/settings/api-keys** (workspace API key `sk_live_…`, não expira, revogável). Uma única chave serve pra todos os seus MCPs.

## Formato de resposta

```json
{ "ok": true, "tool": "<tool_id>", "result": <payload> }
```

## Exemplo cURL

```bash
curl -X POST https://api.mcp.ai/api/siconfi_declaracao/consultar \
  -H "Authorization: Bearer sk_live_..." \
  -H "Content-Type: application/json" \
  -d '{"esfera":"...","ente":"...","poder":"...","orgao":"...","exercicio":"..."}'
```

## Reportar problemas

Se um endpoint retornar erro, vazio ou dado inesperado, reporte (não desista calado): **POST /api/siconfi_declaracao/report** com `{ "message": "...", "context"?: "...", "conversation"?: [...] }`. Isso notifica o time da MCP.AI.

## Endpoints (1)

#### `siconfi_declaracao_consultar`

SICONFI: Declaração Fiscal, consulta em fonte oficial. _(POST /api/siconfi_declaracao/consultar)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `esfera` | string | Sim | Parâmetro de consulta "esfera". |
| `uf` | string | Não | Parâmetro de consulta "uf". |
| `ente` | string | Sim | Parâmetro de consulta "ente". |
| `poder` | string | Sim | Parâmetro de consulta "poder". |
| `orgao` | string | Sim | Parâmetro de consulta "orgao". |
| `exercicio` | string | Sim | Parâmetro de consulta "exercicio". |
| `titulo` | string | Não | Parâmetro de consulta "titulo". |

---

Este MCP também funciona via **conexão MCP** (Claude / Cursor) em `https://api.mcp.ai/p_siconfi_declaracao` — veja o [README](../../README.md). A skill acima é pra consumir a **REST API** direto (agente próprio / código).
