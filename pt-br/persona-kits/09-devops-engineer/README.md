# DevOps Engineer — Kit Copilot

<!-- markdownlint-disable MD013 MD022 MD031 MD032 MD060 -->

> Pipelines CI/CD, IaC, observabilidade e resposta a incidentes.

Leia primeiro: [PERSONA.md](PERSONA.md).

## Fase do SDLC
Cross-cutting, Evolution, Operations

## Conteúdo do kit

| Arquivo | Tipo | Propósito |
|------|------|---------|
| `PERSONA.md` | Persona | Responsabilidades, handoffs, prompts e rubrica do DevOps Engineer |
| `.github/agents/devops-engineer.agent.md` | Agent | CI/CD, IaC, monitoramento e incidentes |
| `.github/prompts/pipeline.prompt.md` | Prompt | `/pipeline` |
| `.github/prompts/iac-module.prompt.md` | Prompt | `/iac-module` |
| `.github/prompts/incident-rca.prompt.md` | Prompt | `/incident-rca` |
| `.github/instructions/cicd.instructions.md` | Instructions | Convenções de CI/CD |
| `.github/instructions/infrastructure.instructions.md` | Instructions | Convenções de infraestrutura |

## Instalação
```bash
cp -r .github/* /path/to/your-repo/.github/
[ -f hooks.json ] && cp hooks.json /path/to/your-repo/
[ -f mcp.json ] && cp mcp.json /path/to/your-repo/.vscode/
```

## Boas práticas
- Tudo como código: infraestrutura, configuração, políticas e runbooks.
- Pipeline com mais de 10 minutos vira gargalo; paralelize ou reduza etapas.
- Secrets vivem em vault, não em `.env`, variáveis soltas de CI ou código-fonte.
- Blue/green e canary resolvem problemas diferentes; escolha pelo custo de rollback.

## Referências
- [Terraform Best Practices](https://developer.hashicorp.com/terraform/language/style)
- [GitHub Actions Hardening](https://docs.github.com/en/actions/security-for-github-actions/security-guides/security-hardening-for-github-actions)
- [Azure Verified Modules](https://azure.github.io/Azure-Verified-Modules/)
- [The DevOps Handbook - Gene Kim et al.](https://itrevolution.com/product/the-devops-handbook-second-edition/)

---

## Navegação

| Anterior | Início |
|--------|------|
| [Persona Kits](../README.md) | [Kit PT-BR](../../README.md) |
