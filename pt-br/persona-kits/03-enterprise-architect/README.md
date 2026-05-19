# Enterprise Architect — Kit Copilot

<!-- markdownlint-disable MD013 MD022 MD031 MD032 MD060 -->

> `CONSTITUTION.md`, ADRs, revisões arquiteturais e governança de segurança.

Leia primeiro: [PERSONA.md](PERSONA.md).

## Fase do SDLC
Arquitetura, Desenho, Segurança

## Conteúdo do kit

| Arquivo | Tipo | Propósito |
|------|------|---------|
| `PERSONA.md` | Persona | Responsabilidades, passagems, prompts e rubrica do Enterprise Architect |
| `.github/agents/enterprise-architect.agent.md` | Agent | Arquitetura e segurança |
| `.github/prompts/create-constitution.prompt.md` | Prompt | `/create-constitution` |
| `.github/prompts/create-adr.prompt.md` | Prompt | `/create-adr` |
| `.github/prompts/architecture-review.prompt.md` | Prompt | `/architecture-review` |
| `.github/instructions/security.instructions.md` | Instructions | Convenções de segurança |
| `.github/instructions/infrastructure.instructions.md` | Instructions | Convenções de IaC |
| `hooks.json` | Hooks | Bloqueios de edição para `CONSTITUTION.md` |

## Instalação
```bash
cp -r .github/* /path/to/your-repo/.github/
[ -f hooks.json ] && cp hooks.json /path/to/your-repo/
[ -f mcp.json ] && cp mcp.json /path/to/your-repo/.vscode/
```

## Boas práticas
- Use C4 L1/L2 para visão executiva e L3/L4 para implementação.
- Toda decisão arquitetural precisa de ADR com contexto, decisão e consequências.
- Prefira arquitetura previsível e operável em produção.
- Use os pilares do Azure Well-Architected como gates de revisão, não como checklist tardio.

## Referências
- [C4 Model - Simon Brown](https://c4model.com/)
- [Microsoft Azure Well-Architected Framework](https://learn.microsoft.com/azure/well-architected/)
- [ADR - Arquitetura Decision Records](https://adr.github.io/)
- [Azure Arquitetura Center](https://learn.microsoft.com/azure/architecture/)

---

## Navegação

| Anterior | Início |
|--------|------|
| [Persona Kits](../README.md) | [Kit PT-BR](../../README.md) |
