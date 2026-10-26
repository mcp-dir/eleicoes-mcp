# Eleições 2026: Dados Públicos do TSE

### Eleições 2026: Dados Públicos do TSE for Claude, ChatGPT and AI agents

Ballot box reports, voting machine logs and official result releases from Brazil's electoral court (TSE) for the 2026 elections (1st and 2nd round), with file hash and source link, to look up and check with ChatGPT or Claude. Raw TSE data organized for lookup. Covers the 1st and 2nd round; the 2nd is the default. Every number comes with the TSE file, official link and SHA-256, with no opinion. Not an official report or analysis. Independent service, not affiliated with the TSE. Free.

- 📊 **9 tools**
- 🔒 **Read-only**
- 💬 **Works with any MCP client**: Claude Desktop, Cursor, VS Code, Cline, Continue
- 🔑 **Magic-link login (no password)**

[Versão em português](README.md) · [Full docs (PT-BR)](docs/) · [Agent skill](skills/)

---

## One-click install

### Claude (Web and Desktop)

Anthropic unified MCP installation at `claude.ai/customize/connectors`. **The same link works for Claude Web and Claude Desktop** (just be logged in):

[➕ Open in Claude and connect](https://claude.ai/new?modal=add-custom-connector#settings/customize-connectors)

**Manual** (if the deeplink does not open): [claude.ai/customize/connectors](https://claude.ai/customize/connectors?surface=cowork) → **+** → **Add custom connector** → paste **Name** `Eleições 2026: Dados Públicos do TSE` and **URL** `https://api.mcp.ai/p_eleicoes`.

### Cursor

[➕ Install Eleições 2026: Dados Públicos do TSE in Cursor](cursor://anysphere.cursor-deeplink/mcp/install?name=eleicoes&config=eyJ1cmwiOiJodHRwczovL2FwaS5tY3AuYWkvcF9lbGVpY29lcyJ9)

### VS Code (Copilot Chat)

[➕ Install Eleições 2026: Dados Públicos do TSE in VS Code](vscode:mcp/install?name=eleicoes&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fapi.mcp.ai%2Fp_eleicoes%22%7D)

### ChatGPT, Manus, OpenClaw and 40+ other clients

Works with any MCP client that speaks **MCP over HTTP**. The server URL is always:

```
https://api.mcp.ai/p_eleicoes
```

Per-client details: [INSTALL.md](INSTALL.md).

---

## Example prompts

```
Compare the 1st and 2nd round for president in Brazil: the change for each candidate, blank, null and abstention, and whether the changes add up to the change in the electorate. For each number, show the TSE file, official link and SHA-256.
In the 2nd round voting machine logs, how many votes were cast between 5:30 pm and 7 pm, by state? Say how many sections have a log available in each state.
I have a printed ballot box report with load code [CODE]. Find the section and show the votes, eligible voters, blank and null votes and closing time from the official file, so I can compare with the paper.
Show the 2nd round results release timeline for Brazil, one row per hour: % of sections counted and votes per candidate. Say from what time the data starts.
For the state [CODE], compare the 1st and 2nd round for president: votes and valid-vote share for each candidate, abstention, blank and null votes, with the difference for each field.
For the city [NAME] in [STATE], compare the 1st and 2nd round for president field by field, and check that candidates, blank and null votes add up to turnout in both rounds.
In [CITY]/[STATE], pick a section that closed after 5:30 pm and show its ballot box report: opening, closing, votes per candidate and the log summary. Compare with the 1st round of the same section.
What was each candidate's share of valid votes in Santa Catarina in the 1st and 2nd round, and how many percentage points did it change? Do the same for Brazil.
How many more voters turned out in the 2nd round than in the 1st in Brazil? Show next to it the change in votes for each candidate.
What was the abstention in the 1st and 2nd round of 2026, in number and %? If earlier elections are not available, say so and point to where to check at the TSE.
For [STATE], show the votes cast in 30-minute slots between 4 pm and 7:30 pm from the voting machine logs, with log coverage. Repeat for [OTHER STATE] side by side.
Check the SHA-256 [HASH] against the TSE files available: which file and version it belongs to, and how I can check the current file on the TSE website.
```

---

## 9 tools available

| Tool | Description |
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

Details for each tool: [docs/ferramentas.md](docs/ferramentas.md) (PT-BR)

---

## Pricing

Free.

---

## Privacy & data protection

- **Read-only**, no tool changes data at the source.
- **Sub-processors**: the LLM host you choose (Claude, ChatGPT, Cursor, your own agent). Full list in [docs/privacidade-lgpd.md](docs/privacidade-lgpd.md).
- Data returned by the tools is sent to **the LLM host you choose**, a sub-processor outside our control. We recommend plans with training opt-out.

---

## FAQ

**Is the server open source?**
The server is proprietary (hosted). This repository is the public wrapper with manifests, docs and skills, all MIT.

**Can I use it with my own agent (not Claude/Cursor)?**
Yes, any client that speaks MCP over HTTP. URL: `https://api.mcp.ai/p_eleicoes`.


---

## Support

- 📧 [eleicoes@mcp.ai](mailto:eleicoes@mcp.ai)
- 🐛 [GitHub Issues](https://github.com/mcp-dir/eleicoes-mcp/issues)
- 📄 [docs/](docs/)

---

## License

MIT — see [LICENSE](LICENSE). The MCP server at `api.mcp.ai/p_eleicoes` is proprietary (hosted); this repo (manifests, docs, skills) is MIT.
