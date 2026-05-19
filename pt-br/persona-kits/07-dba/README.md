# DBA — Kit Copilot

<!-- markdownlint-disable MD013 MD022 MD031 MD032 MD060 -->

> Migrações, otimização de consultas e auditoria contra SQL injection.

Leia primeiro: [PERSONA.md](PERSONA.md).

## Fase do SDLC
Implementation, Quality

## Conteúdo do kit

| Arquivo | Tipo | Propósito |
|------|------|---------|
| `PERSONA.md` | Persona | Responsabilidades, handoffs, prompts e rubrica do DBA |
| `.github/agents/dba.agent.md` | Agent | Migrações, otimização de consultas e auditoria SQL |
| `.github/prompts/migration.prompt.md` | Prompt | `/migration` |
| `.github/prompts/query-audit.prompt.md` | Prompt | `/query-audit` |
| `.github/instructions/database.instructions.md` | Instructions | Convenções de banco de dados |

## Instalação
```bash
cp -r .github/* /path/to/your-repo/.github/
[ -f hooks.json ] && cp hooks.json /path/to/your-repo/
[ -f mcp.json ] && cp mcp.json /path/to/your-repo/.vscode/
```

## Boas práticas
- Índices aceleram leitura e desaceleram escrita; meça os dois lados.
- Migrações precisam ser compatíveis por pelo menos dois deploys: expandir, depois contrair.
- Consultas N+1 são bug de performance; detecte antes de staging.
- Backup que nunca foi restaurado não é backup validado.

## Referências
- [PostgreSQL Documentation](https://www.postgresql.org/docs/)
- [Use the Index, Luke - Markus Winand](https://use-the-index-luke.com/)
- [High Performance MySQL / PostgreSQL - Schwartz et al.](https://www.oreilly.com/)
- [Azure Database for PostgreSQL Best Practices](https://learn.microsoft.com/azure/postgresql/)

---

## Navegação

| Anterior | Início |
|--------|------|
| [Persona Kits](../README.md) | [Kit PT-BR](../../README.md) |
