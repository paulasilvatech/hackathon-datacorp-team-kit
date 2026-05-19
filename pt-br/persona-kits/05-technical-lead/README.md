# Technical Lead — Kit Copilot

<!-- markdownlint-disable MD013 MD022 MD031 MD032 MD060 -->

> Context engineering, roteamento de modelos, quality gates e orquestração técnica.

Leia primeiro: [PERSONA.md](PERSONA.md).

## Fase do SDLC
Todas as fases (coordenação técnica)

## Conteúdo do kit

| Arquivo | Tipo | Propósito |
|------|------|---------|
| `PERSONA.md` | Persona | Responsabilidades, passagems, prompts e rubrica do Technical Lead |
| `.github/agents/tech-lead.agent.md` | Agent | Governança técnica |
| `.github/prompts/setup-project.prompt.md` | Prompt | `/setup-project` |
| `.github/prompts/routing-table.prompt.md` | Prompt | `/routing-table` |
| `.github/prompts/audit-context.prompt.md` | Prompt | `/audit-context` |
| `hooks.json` | Hooks | Escopo, lint e testes |

## Instalação
```bash
cp -r .github/* /path/to/your-repo/.github/
[ -f hooks.json ] && cp hooks.json /path/to/your-repo/
[ -f mcp.json ] && cp mcp.json /path/to/your-repo/.vscode/
```

## Boas práticas
- Bloqueie mudanças ruins, não pessoas; revise o PR e proteja o tempo de quem revisa.
- `CODEMAP.md` é memória de trabalho do time; se está desatualizado, o time voa às cegas.
- Roteamento de modelo importa: Opus para descoberta, Sonnet para implementação, Haiku para transformações mecânicas.
- Custo por feature é métrica de engenharia; acompanhe junto com cobertura.

## Referências
- [Staff Engineer - Will Larson](https://staffeng.com/)
- [The Manager's Path - Camille Fournier](https://www.oreilly.com/library/view/the-managers-path/9781491973882/)
- [Accelerate - Forsgren, Humble, Kim](https://itrevolution.com/product/accelerate/)
- [GitHub Copilot Best Practices](https://docs.github.com/en/copilot)

---

## Navegação

| Anterior | Início |
|--------|------|
| [Persona Kits](../README.md) | [Kit PT-BR](../../README.md) |
