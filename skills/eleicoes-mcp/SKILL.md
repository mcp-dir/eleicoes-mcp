---
name: eleicoes-mcp
description: Skill da REST API do Eleições 2026: Dados Públicos do TSE na MCP.AI: 9 endpoints em /api/eleicoes. Boletins de urna, logs e divulgação oficial do TSE das eleições 2026 (1º e 2º turno), com hash e link de origem, para você consultar e conferir com o ChatGPT ou o Claude. Cobre o 1º e o 2º turno; sem turno indicado, o padrão é o 2º. Cada número vem com o arquivo do TSE, o link oficial e o SHA-256, sem opinião. Dado bruto do TSE organizado para consulta. Não constitui laudo nem análise oficial. Serviço independente, não é do TSE. Grátis. Autentique com workspace API key (sk_live) gerada em app.mcp.ai/settings/api-keys. Use quando o usuário pedir algo coberto pelos endpoints.
---

# Eleições 2026: Dados Públicos do TSE — REST API skill

Você tem acesso à **Eleições 2026: Dados Públicos do TSE** REST API na MCP.AI.

> Boletins de urna, logs e divulgação oficial do TSE das eleições 2026 (1º e 2º turno), com hash e link de origem, para você consultar e conferir com o ChatGPT ou o Claude. Cobre o 1º e o 2º turno; sem turno indicado, o padrão é o 2º. Cada número vem com o arquivo do TSE, o link oficial e o SHA-256, sem opinião. Dado bruto do TSE organizado para consulta. Não constitui laudo nem análise oficial. Serviço independente, não é do TSE. Grátis.

## Base URL

```
https://api.mcp.ai/api/eleicoes
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
curl -X POST https://api.mcp.ai/api/eleicoes/cobertura \
  -H "Authorization: Bearer sk_live_..." \
  -H "Content-Type: application/json" \
  -d '{}'
```

## Reportar problemas

Se um endpoint retornar erro, vazio ou dado inesperado, reporte (não desista calado): **POST /api/eleicoes/report** com `{ "message": "...", "context"?: "...", "conversation"?: [...] }`. Isso notifica o time da MCP.AI.

## Endpoints (9)

#### `eleicoes_cobertura`

Quanto do acervo existe: seções com boletim de urna (BU) e com log de urna por UF, sobre o total de seções do TSE, e a hora da última sincronização. _(POST /api/eleicoes/cobertura)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `ano` | integer | Não | Ano da eleição. Padrão: 2026 (o único no acervo por enquanto). |
| `turno` | number | Não | Opcional: 1 ou 2. Sem ele, mostra os dois turnos. |

#### `eleicoes_como_ler`

Glossário curto e neutro: boletim de urna, log de urna, código de carga, por que algumas seções fecham depois das 17h, prorrogação, fuso, biometria agregada, versões do arquivo e SHA-256. _(POST /api/eleicoes/como/ler)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `ano` | integer | Não | Ano da eleição. Padrão: 2026 (o único no acervo por enquanto). |

#### `eleicoes_comparar_turnos`

1º e 2º turno lado a lado, só números: do Brasil, de uma UF ou de um município (totais oficiais) ou de uma seção (boletim de urna), com a subtração 2º − 1º em cada campo e a conferência de que as vari _(POST /api/eleicoes/comparar/turnos)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `ano` | integer | Não | Ano da eleição. Padrão: 2026 (o único no acervo por enquanto). |
| `uf` | string | Sim | 'BR' para o país inteiro ou a sigla da UF (ex.: 'BA'). |
| `municipio` | string | Não | Opcional. Sem ele, compara a UF (ou o BR) inteira. |
| `zona` | string|number | Não | Opcional, junto com secao. |
| `secao` | string|number | Não | Opcional, junto com zona. |
| `cargo` | string | Não | Padrão: presidente. Governador só em AC, AM, DF, ES, RN e TO no 2º turno. (presidente, governador) |

#### `eleicoes_conferir_bu_impresso`

Devolve o boletim de urna oficial de uma seção, campo a campo, para comparar com um BU impresso. _(POST /api/eleicoes/conferir/bu/impresso)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `ano` | integer | Não | Ano da eleição. Padrão: 2026 (o único no acervo por enquanto). |
| `codigo_carga` | string | Não | Código de carga impresso no BU (só os dígitos importam). |
| `turno` | number | Não | Padrão: 2º turno (25/10/2026); use 1 para o 1º turno (04/10/2026). A resposta sempre diz o turno. |
| `uf` | string | Não | Sigla da UF (ex.: 'BA', 'PR'). 'ZZ' = exterior. |
| `municipio` | string | Não | Nome do município (ex.: 'Maringá') ou código TSE de 5 dígitos. |
| `zona` | string|number | Não | Número da zona eleitoral (ex.: 66). |
| `secao` | string|number | Não | Número da seção eleitoral (ex.: 45). |
| `itens` | object[] | Não | Opcional: vários boletins numa chamada (até 100). Um item por entrada, na mesma ordem. |

#### `eleicoes_consultar_secao`

Boletim de urna (BU) oficial de uma seção eleitoral nas eleições 2026: votos por candidato, brancos, nulos, aptos, comparecimento, abertura e encerramento (hora local e de Brasília), biometria em cont _(POST /api/eleicoes/consultar/secao)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `ano` | integer | Não | Ano da eleição. Padrão: 2026 (o único no acervo por enquanto). |
| `turno` | number | Não | Padrão: 2º turno (25/10/2026); use 1 para o 1º turno (04/10/2026). A resposta sempre diz o turno. |
| `uf` | string | Não | Sigla da UF (ex.: 'BA', 'PR'). 'ZZ' = exterior. |
| `municipio` | string | Não | Nome do município (ex.: 'Maringá') ou código TSE de 5 dígitos. |
| `zona` | string|number | Não | Número da zona eleitoral (ex.: 66). |
| `secao` | string|number | Não | Número da seção eleitoral (ex.: 45). |
| `secoes` | object[] | Não | Opcional: várias seções numa chamada (até 100). Um item por entrada, na mesma ordem; item inválido ou não encontrado vem com 'erro'. |

#### `eleicoes_timeline_divulgacao`

Linha do tempo da divulgação do 2º turno no Brasil ou numa UF: cada versão do arquivo de resultado publicada pelo TSE (ou uma linha por hora, com os votos ganhos na hora), com % de seções totalizadas, _(POST /api/eleicoes/timeline/divulgacao)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `ano` | integer | Não | Ano da eleição. Padrão: 2026 (o único no acervo por enquanto). |
| `uf` | string | Não | 'BR' (padrão) ou a sigla da UF. |
| `cargo` | string | Não | Padrão: presidente. Governador só em AC, AM, DF, ES, RN e TO no 2º turno. (presidente, governador) |
| `agrupar` | string | Não | 'versao' (padrão): cada versão publicada. 'hora': uma linha por hora com os votos ganhos na hora. (versao, hora) |
| `max_pontos` | integer | Não | Máximo de pontos devolvidos. Padrão: 60. |
| `de` | string | Não | Opcional. Só versões geradas a partir de HH:MM (Brasília). |
| `ate` | string | Não | Opcional. Só versões geradas até HH:MM (Brasília). |

#### `eleicoes_totais`

Totais oficiais por candidato (votos, % dos válidos, brancos, nulos, comparecimento, abstenções, seções totalizadas) no Brasil, numa UF ou num município, da última versão coletada do arquivo de result _(POST /api/eleicoes/totais)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `ano` | integer | Não | Ano da eleição. Padrão: 2026 (o único no acervo por enquanto). |
| `turno` | number | Não | Padrão: 2º turno (25/10/2026); use 1 para o 1º turno (04/10/2026). A resposta sempre diz o turno. |
| `nivel` | string | Não | Abrangência. Padrão: br. (br, uf, municipio) |
| `codigo` | string | Não | Para nivel uf: a sigla (ex.: 'BA'). Para municipio: 'UF/municipio' (ex.: 'PR/Maringá'). |
| `uf` | string | Não | Alternativa a 'codigo' para uf/municipio. |
| `municipio` | string | Não | Alternativa a 'codigo' para nivel municipio (com uf). |
| `cargo` | string | Não | Padrão: presidente. Governador só em AC, AM, DF, ES, RN e TO no 2º turno. (presidente, governador) |

#### `eleicoes_verificar_hash`

Diz se um SHA-256 é igual ao de um arquivo oficial do TSE no acervo e qual é o arquivo; ou, dado o nome do arquivo (ex.: o03221pr7691000660045-bu.dat, br-c0001-e006258-u.json), devolve o SHA-256 regis _(POST /api/eleicoes/verificar/hash)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `ano` | integer | Não | Ano da eleição. Padrão: 2026 (o único no acervo por enquanto). |
| `sha256` | string | Não | Hash SHA-256 em hexadecimal (64 caracteres). |
| `arquivo` | string | Não | Nome do arquivo do TSE. |
| `itens` | object[] | Não | Opcional: vários hashes/arquivos numa chamada (até 100). Um item por entrada, na mesma ordem. |

#### `eleicoes_votos_por_horario`

Votos computados por faixa de horário (Brasília) no 2º turno, contados nos logs de urna, por UF, por município ou com uf 'BR' para todas as UFs lado a lado. _(POST /api/eleicoes/votos/por/horario)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `ano` | integer | Não | Ano da eleição. Padrão: 2026 (o único no acervo por enquanto). |
| `turno` | number | Não | Padrão: 2º turno (25/10/2026); use 1 para o 1º turno (04/10/2026). A resposta sempre diz o turno. |
| `uf` | string | Sim | Sigla da UF, ou 'BR' para todas as UFs lado a lado com a cobertura de log de cada uma. |
| `municipio` | string | Não | Opcional. Sem ele, soma a UF inteira. Lista as seções do último voto mais tarde para o mais cedo. |
| `de` | string | Não | Opcional. Início do filtro, HH:MM (Brasília). |
| `ate` | string | Não | Opcional. Fim do filtro, HH:MM (Brasília), inclusivo. |
| `intervalo_minutos` | number | Não | Tamanho da faixa em minutos. Padrão: 60. |

---

Este MCP também funciona via **conexão MCP** (Claude / Cursor) em `https://api.mcp.ai/p_eleicoes` — veja o [README](../../README.md). A skill acima é pra consumir a **REST API** direto (agente próprio / código).
