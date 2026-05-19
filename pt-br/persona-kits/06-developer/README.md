# Developer — Kit Copilot

<!-- markdownlint-disable MD013 MD022 MD031 MD032 MD060 -->

> Implementação, TDD, correção de bugs e ciclo entender → reproduzir → corrigir → verificar.

Leia primeiro: [PERSONA.md](PERSONA.md).

## Fase do SDLC
Implementation, Evolution

## Conteúdo do kit

| Arquivo | Tipo | Propósito |
|------|------|---------|
| `PERSONA.md` | Persona | Responsabilidades, handoffs, prompts e rubrica do Developer |
| `.github/agents/implementer.agent.md` | Agent | Implementação, TDD e correção de bugs |
| `.github/prompts/implement.prompt.md` | Prompt | `/implement` |
| `.github/prompts/fix-bug.prompt.md` | Prompt | `/fix-bug` |
| `.github/prompts/tdd.prompt.md` | Prompt | `/tdd` |
| `.github/prompts/refactor.prompt.md` | Prompt | `/refactor` |

## Instalação
```bash
cp -r .github/* /path/to/your-repo/.github/
[ -f hooks.json ] && cp hooks.json /path/to/your-repo/
[ -f mcp.json ] && cp mcp.json /path/to/your-repo/.vscode/
```

## Boas práticas
- Escreva teste antes quando o design estiver claro; escreva junto quando estiver explorando. Sempre commit com testes.
- Um PR deve contar uma história: um assunto, pequeno o bastante para revisar em cerca de 20 minutos.
- Refatore em commit separado da mudança de comportamento.
- Comentários explicam o porquê; código explica o quê.

## Referências
- [Clean Code - Robert C. Martin](https://www.oreilly.com/library/view/clean-code-a/9780136083238/)
- [Refactoring - Martin Fowler](https://refactoring.com/)
- [Test-Driven Development - Kent Beck](https://www.oreilly.com/library/view/test-driven-development/0321146530/)
- [GitHub Copilot Best Practices](https://docs.github.com/en/copilot)

---

## Navegação

| Anterior | Início |
|--------|------|
| [Persona Kits](../README.md) | [Kit PT-BR](../../README.md) |
