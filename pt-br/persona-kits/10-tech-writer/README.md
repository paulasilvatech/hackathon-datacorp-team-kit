# Tech Writer — Kit Copilot

<!-- markdownlint-disable MD013 MD022 MD031 MD032 MD060 -->

> Documentação de API, README, `CODEMAP.md`, changelog e detecção de drift.

Leia primeiro: [PERSONA.md](PERSONA.md).

## Fase do SDLC
Cross-cutting, Documentation, Evolution

## Conteúdo do kit

| Arquivo | Tipo | Propósito |
|------|------|---------|
| `PERSONA.md` | Persona | Responsabilidades, handoffs, prompts e rubrica do Tech Writer |
| `.github/agents/tech-writer.agent.md` | Agent | Docs de API, README, `CODEMAP.md`, changelog e drift |
| `.github/prompts/generate-docs.prompt.md` | Prompt | `/generate-docs` |
| `.github/prompts/update-codemap.prompt.md` | Prompt | `/update-codemap` |
| `.github/prompts/doc-drift.prompt.md` | Prompt | `/doc-drift` |

## Instalação
```bash
cp -r .github/* /path/to/your-repo/.github/
[ -f hooks.json ] && cp hooks.json /path/to/your-repo/
[ -f mcp.json ] && cp mcp.json /path/to/your-repo/.vscode/
```

## Boas práticas
- Documentação é feature: entregue, versione e revise junto com o código.
- Escreva para quem tem 30 segundos; comece pela resposta e depois dê contexto.
- Diagramas comprimem explicações longas; use Mermaid e mantenha atualizado.
- Documentação obsoleta é pior que ausência; inclua drift check no CI.

## Referências
- [Diátaxis Framework](https://diataxis.fr/)
- [Google Developer Documentation Style Guide](https://developers.google.com/style)
- [Write the Docs](https://www.writethedocs.org/)
- [Mermaid - Diagramming as Code](https://mermaid.js.org/)

---

## Navegação

| Anterior | Início |
|--------|------|
| [Persona Kits](../README.md) | [Kit PT-BR](../../README.md) |
