---
title: "Cheat Sheet - Specky SDD v3.4"
description: "Uma pagina. Pipeline SDD, 6 padroes EARS, agents e comandos do Specky v3.4."
author: "Paula Silva"
date: "2026-04-22"
version: "2.0.0"
tags: ["cheat-sheet", "specky", "SDD", "EARS", "hackathon", "DATACORP"]
---

# Specky SDD v3.4 - Cheat Sheet

> Repo: https://github.com/paulasilvatech/specky | Instalar: `npm install -g specky-sdd@latest`

## O que e

Motor de Spec-Driven Development. 13 agentes, 57 MCP tools, 16 hooks. **O pipeline e enforçado** - nao se pula fase.

## Setup rapido

```bash
specky install --ide=copilot   # VS Code + Copilot
specky install --ide=claude    # Claude Code
specky doctor                  # Valida instalacao
```

## Os 6 Padroes EARS

| # | Padrao | Template | Exemplo SIFAP |
|---|--------|----------|---------------|
| 1 | **Ubiquo** | O sistema deve [acao] | O SIFAP deve gravar auditoria em toda alteracao |
| 2 | **Evento** | Quando [X], o sistema deve [acao] | Quando ciclo e gerado, criar pagamentos para ATIVOS |
| 3 | **Estado** | Enquanto [X], o sistema deve [acao] | Enquanto PENDENTE, permitir cancelamento |
| 4 | **Opcional** | Se [escolha], o sistema deve [acao] | Se exportar, gerar CSV UTF-8 |
| 5 | **Indesejado** | O sistema nao deve [acao] | Nao permitir DELETE em auditoria |
| 6 | **Complexo** | Enquanto [X], quando [Y], se [Z], deve [acao] | Em dezembro, ATIVO, calcular 13o salario |

Validar: `sdd_validate_ears` (tool MCP) ou `@spec-engineer` (agent)

## Pipeline - 10 Fases

| # | Fase | Agent | Entrega | Persona dona | Estagio |
|---|------|-------|---------|-------------|---------|
| 0 | Init | `@sdd-init` | CONSTITUTION.md | TL | 2 |
| 1 | Discover | `@research-analyst` | RESEARCH.md | RE + EA | 2 |
| 2 | Specify | `@spec-engineer` | SPECIFICATION.md (EARS) | RE | 2 |
| 3 | Clarify | `@sdd-clarify` | CLARIFICATION-LOG.md | RE + PO | 2 |
| 4 | Design | `@design-architect` | DESIGN.md + C4 + ADRs | SA + EA | 2 |
| 5 | Tasks | `@task-planner` | TASKS.md + CHECKLIST.md | TL | 3 |
| 6 | Analyze | `@quality-reviewer` | ANALYSIS.md | QA | 3 |
| 7 | Implement | `@implementer` | Codigo | Dev | 3 |
| 8 | Verify | `@test-verifier` | Testes + coverage | QA | 3 |
| 9 | Release | `@release-engineer` | PR + deploy | DevOps | 4 |

Gates LGTM: apos Specify, Design e Tasks. Revisar antes de avancar.

## Slash Commands

| Comando | Quando usar |
|---------|-------------|
| `/specky-migration` | **PRINCIPAL** - modernizacao do SIFAP |
| `/specky-specify` | Escrever requisitos EARS |
| `/specky-design` | Gerar arquitetura + diagramas |
| `/specky-tasks` | Quebrar design em tarefas |
| `/specky-verify` | Validar testes vs spec |
| `/specky-release` | Criar PR final |

## MCP Tools mais usados

| Tool | O que faz |
|------|----------|
| `sdd_init` | Cria `.specs/NNN-feature/` |
| `sdd_write_spec` | Gera SPECIFICATION.md |
| `sdd_validate_ears` | Valida 6 padroes EARS |
| `sdd_generate_diagram` | Gera C4 em Mermaid |
| `sdd_write_design` | Gera DESIGN.md + ADRs |
| `sdd_write_tasks` | Gera TASKS.md sequenciadas |
| `sdd_check_sync` | Detecta drift spec vs codigo |

## Hooks que vao disparar

- **no-code-without-spec**: bloqueia PR sem referencia a spec
- **EARS-linter**: reclama de requisito fora dos 6 padroes
- **ADR-completeness**: exige "caminho nao escolhido"
- **traceability-check**: amarra requisito → teste

Quando um hook bloquear: **leia a mensagem**. Ajuste o artefato, nao force override.

## Fluxo do Hackathon

```
Estagio 2 (2h):
  @specky-orchestrator → Init → Discover → Specify → Clarify → Design
  
Estagio 3 (3h):
  @task-planner → Tasks → @implementer → Code → @test-verifier → Verify

Estagio 4 (1h30):
  @release-engineer → Release → PR
```

## Dicas

- Nao pule para Code sem passar por Specify + Design
- `specky doctor` deve estar todo verde antes de comecar
- Se Specky nao estiver disponivel: escreva EARS manualmente - o formato e texto simples
- Use `@specky-orchestrator` para deixar o pipeline guiar voce

- Paula
