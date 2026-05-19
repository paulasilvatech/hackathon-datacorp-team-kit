# Requirements Engineer — Kit Copilot

<!-- markdownlint-disable MD013 MD022 MD031 MD032 MD060 -->

> Notação EARS, detecção de drift de especificação e análise de contradições.

Leia primeiro: [PERSONA.md](PERSONA.md).

## Fase do SDLC
Requisitos, Especificação

## Conteúdo do kit

| Arquivo | Tipo | Propósito |
|------|------|---------|
| `PERSONA.md` | Persona | Responsabilidades, passagems, prompts e rubrica do Requirements Engineer |
| `.github/agents/requirements-engineer.agent.md` | Agent | Análise de requisitos |
| `.github/prompts/spec-sync.prompt.md` | Prompt | `/spec-sync` |
| `.github/prompts/contradiction-check.prompt.md` | Prompt | `/contradiction-check` |
| `.github/prompts/ears-convert.prompt.md` | Prompt | `/ears-convert` |
| `.github/instructions/requirements.instructions.md` | Instructions | Convenções de documentação de requisitos |

## Instalação
```bash
cp -r .github/* /path/to/your-repo/.github/
[ -f hooks.json ] && cp hooks.json /path/to/your-repo/
[ -f mcp.json ] && cp mcp.json /path/to/your-repo/.vscode/
```

## Boas práticas
- Use padrões EARS exclusivamente; requisitos vagos precisam ser quantificados.
- Todo `REQ-ID` deve ser único, imutável e rastreável a pelo menos um teste e uma task.
- Faça uma passada de contradição antes de aceitar novas specs.
- Remova ou quantifique termos ambíguos como “adequado”, “razoável” e “amigável”.

## Referências
- [EARS Notation - Alistair Mavin](https://alistairmavin.com/ears/)
- [IEEE 29148 - Requirements Engineering](https://www.iso.org/standard/72089.html)
- [ISO/IEC 25010 - Quality Model](https://iso25000.com/index.php/en/iso-25000-standards/iso-25010)
- [Writing Good Requirements - INCOSE](https://www.incose.org/)

---

## Navegação

| Anterior | Início |
|--------|------|
| [Persona Kits](../README.md) | [Kit PT-BR](../../README.md) |
