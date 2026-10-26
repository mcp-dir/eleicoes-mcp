# Eleições 2026: Dados Públicos do TSE

### Eleições 2026: Dados Públicos do TSE para Claude, ChatGPT e agentes de IA

Boletins de urna, logs e divulgação oficial do TSE das eleições 2026 (1º e 2º turno), com hash e link de origem, para você consultar e conferir com o ChatGPT ou o Claude. Cobre o 1º e o 2º turno; sem turno indicado, o padrão é o 2º. Cada número vem com o arquivo do TSE, o link oficial e o SHA-256, sem opinião. Dado bruto do TSE organizado para consulta. Não constitui laudo nem análise oficial. Serviço independente, não é do TSE. Grátis.

- 📊 **9 ferramentas**
- 🔒 **Somente leitura**
- 💬 **Funciona com qualquer cliente MCP**: Claude Desktop, Cursor, VS Code, Cline, Continue
- 🔑 **Login via magic-link (sem senha)**

[English version](README.en.md) · [Documentação completa](docs/) · [Skill pra agentes](skills/)

---

## Instalar em 1 clique

### Claude (Web e Desktop)

A Anthropic unificou a instalação de MCPs em `claude.ai/customize/connectors`. **O mesmo link serve pra Claude Web e Claude Desktop** (basta estar logado):

[➕ Abrir no Claude e conectar](https://claude.ai/new?modal=add-custom-connector#settings/customize-connectors)

**Manual** (se o deeplink não abrir): [claude.ai/customize/connectors](https://claude.ai/customize/connectors?surface=cowork) → **+** → **Adicionar conector personalizado** → cole **Nome** `Eleições 2026: Dados Públicos do TSE` e **URL** `https://api.mcp.ai/p_eleicoes`.

### Cursor

[➕ Instalar Eleições 2026: Dados Públicos do TSE no Cursor](cursor://anysphere.cursor-deeplink/mcp/install?name=eleicoes&config=eyJ1cmwiOiJodHRwczovL2FwaS5tY3AuYWkvcF9lbGVpY29lcyJ9)

### VS Code (Copilot Chat)

[➕ Instalar Eleições 2026: Dados Públicos do TSE no VS Code](vscode:mcp/install?name=eleicoes&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fapi.mcp.ai%2Fp_eleicoes%22%7D)

### ChatGPT, Manus, OpenClaw e mais 40+ clientes

Funciona em qualquer cliente MCP que suporte **MCP over HTTP**. A URL do servidor é sempre:

```
https://api.mcp.ai/p_eleicoes
```

Detalhes por cliente: [INSTALL.md](INSTALL.md).

---

## Exemplos de uso

```
Compare o 1º e o 2º turno para presidente no Brasil: a variação de cada candidato, de brancos, nulos e abstenção, e se as variações somam a variação do eleitorado. Para cada número, mostre o arquivo do TSE, o link oficial e o SHA-256.
Nos logs de urna do 2º turno, quantos votos foram computados entre 17h30 e 19h, por UF? Diga quantas seções com log existem no acervo em cada UF.
Tenho um boletim de urna impresso com o código de carga [CÓDIGO]. Ache a seção e mostre votos, aptos, brancos, nulos e o horário de encerramento do arquivo oficial, para eu comparar com o papel.
Mostre a linha do tempo da divulgação do 2º turno no Brasil, uma linha por hora: % de seções totalizadas e votos de cada candidato. Diga a partir de que horário o acervo tem dados.
Para a UF [SIGLA], compare 1º e 2º turno para presidente: votos e % válidos de cada candidato, abstenção, brancos e nulos, com a diferença de cada campo.
Para o município [NOME] em [UF], compare 1º e 2º turno para presidente com a subtração de cada campo, e confira se candidatos, brancos e nulos somam o comparecimento nos dois turnos.
Em [MUNICÍPIO]/[UF], escolha uma seção que encerrou depois das 17h30 e mostre o boletim de urna dela: abertura, encerramento, votos por candidato e o resumo do log. Compare com o 1º turno da mesma seção.
Qual foi o % de votos válidos de cada candidato em Santa Catarina no 1º e no 2º turno, e quanto mudou em pontos percentuais? Faça a mesma conta para o Brasil.
Quantos eleitores a mais compareceram no 2º turno em relação ao 1º no Brasil? Mostre ao lado a variação de votos de cada candidato.
Qual foi a abstenção no 1º e no 2º turno de 2026, em número e em %? Se o acervo não tiver eleições anteriores, diga isso e indique onde conferir no TSE.
Para [UF], mostre os votos computados por faixa de 30 minutos entre 16h e 19h30, pelos logs de urna, com a cobertura de log. Repita para [OUTRA UF] e coloque lado a lado.
Verifique o SHA-256 [HASH] contra os arquivos do TSE no acervo: a qual arquivo e a qual versão ele pertence, e como confiro o arquivo atual no site do TSE.
```

---

## 9 ferramentas disponíveis

| Tool | Descrição |
|---|---|
| `eleicoes_consultar_secao` | Boletim de urna (BU) oficial de uma seção eleitoral nas eleições 2026: votos por candidato, brancos, nulos, aptos, comparecimento, abertura e encerramento (hora local e de Brasília), biometria em contagem agregada, có… |
| `eleicoes_votos_por_horario` | Votos computados por faixa de horário (Brasília) no 2º turno, contados nos logs de urna, por UF, por município ou com uf 'BR' para todas as UFs lado a lado. |
| `eleicoes_totais` | Totais oficiais por candidato (votos, % dos válidos, brancos, nulos, comparecimento, abstenções, seções totalizadas) no Brasil, numa UF ou num município, da última versão coletada do arquivo de resultado do TSE. |
| `eleicoes_comparar_turnos` | 1º e 2º turno lado a lado, só números: do Brasil, de uma UF ou de um município (totais oficiais) ou de uma seção (boletim de urna), com a subtração 2º − 1º em cada campo e a conferência de que as variações somam a var… |
| `eleicoes_timeline_divulgacao` | Linha do tempo da divulgação do 2º turno no Brasil ou numa UF: cada versão do arquivo de resultado publicada pelo TSE (ou uma linha por hora, com os votos ganhos na hora), com % de seções totalizadas, votos por candid… |
| `eleicoes_conferir_bu_impresso` | Devolve o boletim de urna oficial de uma seção, campo a campo, para comparar com um BU impresso. |
| `eleicoes_verificar_hash` | Diz se um SHA-256 é igual ao de um arquivo oficial do TSE no acervo e qual é o arquivo; ou, dado o nome do arquivo (ex.: o03221pr7691000660045-bu.dat, br-c0001-e006258-u.json), devolve o SHA-256 registrado. |
| `eleicoes_cobertura` | Quanto do acervo existe: seções com boletim de urna (BU) e com log de urna por UF, sobre o total de seções do TSE, e a hora da última sincronização. |
| `eleicoes_como_ler` | Glossário curto e neutro: boletim de urna, log de urna, código de carga, por que algumas seções fecham depois das 17h, prorrogação, fuso, biometria agregada, versões do arquivo e SHA-256. |

Detalhe de cada tool: [docs/ferramentas.md](docs/ferramentas.md)

---

## Preços

Grátis.

---

## Privacidade & LGPD

- **Somente leitura**, nenhuma ferramenta altera dados na origem.
- **Sub-processadores**: o LLM host que você escolher (Claude, ChatGPT, Cursor, agente próprio). Lista completa em [docs/privacidade-lgpd.md](docs/privacidade-lgpd.md).
- Os dados retornados pelas tools são enviados ao **LLM host que você escolher**, sub-processador fora do nosso controle. Recomendamos planos com opt-out de treinamento.

---

## Perguntas frequentes

**O servidor é open source?**
O servidor é proprietário (hosted). Este repositório é o wrapper público com manifestos, docs e skills — tudo MIT.

**Posso usar com agente próprio (não Claude/Cursor)?**
Sim — qualquer cliente que suporte MCP over HTTP. URL: `https://api.mcp.ai/p_eleicoes`.


---

## Suporte

- 📧 [eleicoes@mcp.ai](mailto:eleicoes@mcp.ai)
- 🐛 [GitHub Issues](https://github.com/mcp-dir/eleicoes-mcp/issues)
- 📄 [docs/](docs/)

---

## Licença

MIT — veja [LICENSE](LICENSE). O servidor MCP em `api.mcp.ai/p_eleicoes` é proprietário (hosted); este repositório (manifestos, docs, skills) é MIT.
