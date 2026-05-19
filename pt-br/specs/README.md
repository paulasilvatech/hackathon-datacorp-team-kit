---
title: "Workspace SDD do Spec-Kit"
description: "Guia didático da pasta de especificações: uma pasta por funcionalidade, com artefatos do GitHub Spec-Kit"
author: "Requirements Engineer (time)"
date: "2026-05-18"
version: "2.0.0"
status: "approved"
tags: ["spec-kit", "sdd", "ears", "specifications", "pt-br"]
---

<!-- markdownlint-disable MD013 MD025 MD026 MD028 MD029 MD034 MD040 MD051 MD060 -->

# specs/

Esta pasta guarda os artefatos do **GitHub Spec-Kit**. Pense nela como o diário técnico de cada funcionalidade: primeiro o time explica o que quer construir, depois planeja como construir, depois quebra em tarefas e só então implementa.

## Modelo mental

Cada funcionalidade tem uma pasta própria:

```text
specs/
└── 001-geracao-ciclo-pagamento/
    ├── spec.md
    ├── plan.md
    ├── research.md
    ├── data-model.md
    ├── contracts/
    ├── quickstart.md
    └── tasks.md
```

O número (`001`) dá ordem. O nome (`geracao-ciclo-pagamento`) explica o escopo. Evite nomes genéricos como `sifap` ou `backend`.

## Passo a passo

1. **Escolha uma descoberta do Estágio 1.** Exemplo: regra de pagamento encontrada em `legacy/natural-programs/BATCHPGT.NSN`.
2. **Crie ou renomeie a pasta da funcionalidade.** Use o padrão `NNN-nome-curto`.
3. **Execute `/speckit.specify`.** A spec deve ter user stories, EARS, critérios de aceitação e `source_legacy:`.
4. **Execute `/speckit.clarify`.** Resolva dúvidas antes de discutir arquitetura.
5. **Execute `/speckit.plan`.** Gere plano técnico, riscos, dados e contratos.
6. **Execute `/speckit.tasks`.** Quebre o plano em tarefas pequenas, testáveis e rastreáveis.
7. **Execute `/speckit.analyze`.** Corrija inconsistências antes de codar.
8. **Execute `/speckit.implement`.** Só implemente depois que spec, plan e tasks estiverem coerentes.

## Fluxo Spec-Kit

| Comando | Artefato | O que conferir |
| --- | --- | --- |
| `/speckit.constitution` | `.specify/memory/constitution.md` | Regras inegociáveis do projeto |
| `/speckit.specify` | `spec.md` | REQ-IDs, EARS, acceptance e `source_legacy:` |
| `/speckit.clarify` | Perguntas resolvidas na spec | Ambiguidades fechadas |
| `/speckit.plan` | `plan.md`, `research.md`, `data-model.md`, `contracts/`, `quickstart.md` | Arquitetura, dados, riscos e contratos |
| `/speckit.tasks` | `tasks.md` | Ordem de execução, testes e dependências |
| `/speckit.analyze` | Relatório de lacunas | Inconsistências resolvidas |
| `/speckit.implement` | Código em `backend/` e `frontend/` | Implementação segue a spec |

## Convenção de branches

- Uma branch por spec: `spec/<NNN>-<feature-name>` criada a partir de `develop`.
- Branches de implementação: `impl/<NNN>-<feature-name>` criadas a partir da branch da spec.
- Commits devem mencionar REQ-IDs quando implementarem comportamento: `Implements REQ-PAY-001`.

## Funcionalidade inicial

A pasta [001-example-feature](001-example-feature/) é um marcador didático. Renomeie ou substitua quando o time escolher a primeira funcionalidade no Estágio 2.

```bash
mv specs/001-example-feature specs/001-geracao-ciclo-pagamento
```

## Definição de Pronto da pasta `specs/`

- [ ] Cada funcionalidade tem pasta `NNN-nome-curto`.
- [ ] Todo requisito legado tem `source_legacy:` apontando para `.NSN` ou `.ddm`.
- [ ] Todo requisito greenfield tem justificativa `[GREENFIELD]`.
- [ ] `tasks.md` inclui testes antes de implementação para regra de negócio.
- [ ] `quickstart.md` permite validar manualmente o comportamento principal.

## Referências

- [Cartão de referência do Spec-Kit](../cheat-sheets/spec-kit-workflow.md)
- [Spec-Kit oficial](https://github.com/github/spec-kit)
- [Spec-Driven Development](https://github.com/github/spec-kit/blob/main/spec-driven.md)

— Paula
