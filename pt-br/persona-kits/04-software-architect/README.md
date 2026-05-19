# Software Architect — Kit Copilot

<!-- markdownlint-disable MD013 MD022 MD031 MD032 MD060 -->

> `CODEMAP.md`, desenho de módulos, contratos de API e planejamento de implementação.

Leia primeiro: [PERSONA.md](PERSONA.md).

## Fase do SDLC
Design, Implementation Oversight

## Conteúdo do kit

| Arquivo | Tipo | Propósito |
|------|------|---------|
| `PERSONA.md` | Persona | Responsabilidades, handoffs, prompts e rubrica do Software Architect |
| `.github/agents/software-architect.agent.md` | Agent | Arquitetura |
| `.github/prompts/codemap.prompt.md` | Prompt | `/codemap` |
| `.github/prompts/impl-plan.prompt.md` | Prompt | `/impl-plan` |
| `.github/prompts/api-validate.prompt.md` | Prompt | `/api-validate` |
| `.github/instructions/backend.instructions.md` | Instructions | Convenções backend |
| `.github/instructions/frontend.instructions.md` | Instructions | Convenções frontend |

## Instalação
```bash
cp -r .github/* /path/to/your-repo/.github/
[ -f hooks.json ] && cp hooks.json /path/to/your-repo/
[ -f mcp.json ] && cp mcp.json /path/to/your-repo/.vscode/
```

## Boas práticas
- Prefira composição a herança, fronteiras claras a abstrações genéricas e dados claros a código esperto.
- Contratos de API são compromisso público; quebre apenas com versão e guia de migração.
- Mantenha regra de negócio fora do banco e do framework.
- Pasta `util` crescendo costuma indicar bounded context ausente.

## Referências
- [Clean Architecture - Robert C. Martin](https://blog.cleancoder.com/uncle-bob/2012/08/13/the-clean-architecture.html)
- [Domain-Driven Design - Eric Evans](https://www.domainlanguage.com/ddd/)
- [Hexagonal Architecture - Alistair Cockburn](https://alistair.cockburn.us/hexagonal-architecture/)
- [Microsoft .NET Architecture Guides](https://learn.microsoft.com/dotnet/architecture/)

---

## Navegação

| Anterior | Início |
|--------|------|
| [Persona Kits](../README.md) | [Kit PT-BR](../../README.md) |
