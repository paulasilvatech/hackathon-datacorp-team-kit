# Product Owner — Kit Copilot

<!-- markdownlint-disable MD013 MD022 MD031 MD032 MD060 -->

> Escrita de especificação, refinamento de backlog e validação de aceite usando EARS e o fluxo SDD.

Leia primeiro: [PERSONA.md](PERSONA.md).

## Fase do SDLC
Descoberta → Especificação → Aceite

## Conteúdo do kit

| Arquivo | Tipo | Propósito |
|------|------|---------|
| `PERSONA.md` | Persona | Responsabilidades, passagems, prompts e rubrica do Product Owner |
| `.github/agents/product-owner.agent.md` | Agent | Assistente de Product Owner para spec, backlog e aceite |
| `.github/prompts/spec.prompt.md` | Prompt | `/spec` — escreve uma seção de `SPECIFICATION.md` a partir de user stories em EARS |
| `.github/prompts/update-spec.prompt.md` | Prompt | `/update-spec` — atualiza a spec quando uma feature muda |
| `.github/prompts/acceptance-check.prompt.md` | Prompt | `/acceptance-check` — verifica se o código atende aos critérios de aceite |
| `mcp.json` | MCP | Manifesto de servidores GitHub + Azure DevOps work items |

## Instalação
```bash
cp -r .github/* /path/to/your-repo/.github/
[ -f hooks.json ] && cp hooks.json /path/to/your-repo/
[ -f mcp.json ] && cp mcp.json /path/to/your-repo/.vscode/
```

## Boas práticas
- Escreva requisitos em EARS para que cada frase seja testável.
- Mantenha cada user story ligada a um resultado mensurável.
- Marque suposições explicitamente; suposição escondida vira bug de produção.
- Trate `CONSTITUTION.md` como fonte de verdade para itens inegociáveis.

## Referências
- [EARS Notation - Alistair Mavin](https://alistairmavin.com/ears/)
- [Spec-Driven Development (Spec-Kit)](https://github.com/github/spec-kit)
- [User Story Mapping - Jeff Patton](https://www.jpattonassociates.com/user-story-mapping/)
- [GitHub Copilot for PMs](https://docs.github.com/en/copilot)

---

## Navegação

| Anterior | Início |
|--------|------|
| [Persona Kits](../README.md) | [Kit PT-BR](../../README.md) |
