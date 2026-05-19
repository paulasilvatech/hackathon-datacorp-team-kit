---
title: "Funcionalidade de Exemplo — Placeholder"
description: "Exemplo didático de pasta Spec-Kit: o que criar, em que ordem e como saber que a feature está pronta para implementação"
author: "Spec-Kit"
date: "2026-05-18"
version: "1.0.0"
status: "placeholder"
tags: ["spec-kit", "sdd", "example", "pt-br"]
---

<!-- markdownlint-disable MD013 MD025 MD026 MD028 MD029 MD034 MD040 MD051 MD060 -->

# 001 — Funcionalidade de Exemplo

> Esta pasta é um modelo. Renomeie quando o time escolher uma funcionalidade real no Estágio 2.

## Para que serve

Ela mostra a estrutura mínima esperada para uma feature guiada pelo GitHub Spec-Kit. O objetivo não é preencher tudo manualmente; é entender o que cada comando `/speckit.*` deve produzir.

## Exemplo de renomeação

```bash
mv specs/001-example-feature specs/001-geracao-ciclo-pagamento
```

Use nomes curtos, sem acento e orientados a comportamento.

| Nome bom | Nome fraco |
| --- | --- |
| `001-geracao-ciclo-pagamento` | `001-backend` |
| `002-validacao-beneficiario` | `002-sifap` |
| `003-relatorio-auditoria` | `003-coisas` |

## Artefatos obrigatórios

| Artefato | Quem ajuda | O que deve conter |
| --- | --- | --- |
| `.specify/memory/constitution.md` | Todo time | Princípios e regras inegociáveis |
| `spec.md` | PO + RE | User stories, EARS, acceptance criteria e `source_legacy:` |
| `plan.md` | Arquitetura + TL | Plano técnico, módulos, riscos e contratos |
| `research.md` | Arquitetura + Dev | Decisões investigadas e trade-offs |
| `data-model.md` | DBA + SA | Entidades, relações e regras de dados |
| `contracts/` | SA + Dev | OpenAPI, eventos ou contratos externos |
| `quickstart.md` | QA + DevOps | Como validar manualmente a feature |
| `tasks.md` | TL + QA + Dev | Tarefas pequenas, ordenadas e testáveis |

## Passo a passo recomendado

1. Escolha uma regra real encontrada no Estágio 1.
2. Abra o Copilot no modo Ask ou Plan.
3. Rode `/speckit.specify` com contexto e `source_legacy:`.
4. Rode `/speckit.clarify` até não restarem perguntas críticas.
5. Rode `/speckit.plan` para transformar requisito em arquitetura.
6. Rode `/speckit.tasks` para quebrar trabalho por ordem de execução.
7. Rode `/speckit.analyze` para achar lacunas.
8. Só então use `/speckit.implement` ou Agent Mode.

## Prompt mínimo de exemplo

```text
/speckit.specify
Feature: geração de ciclo de pagamento mensal.
Regra legado: criar pagamentos apenas para beneficiários ativos.
source_legacy: legacy/natural-programs/BATCHPGT.NSN#L120-L168
Acceptance: 10 ativos + 2 suspensos geram 10 pagamentos.
```

## Definition of Done

- [ ] `spec.md` tem REQ-IDs e EARS.
- [ ] Todo requisito legado tem `source_legacy:`.
- [ ] `plan.md` cita stack e decisões arquiteturais.
- [ ] `tasks.md` começa por testes quando houver regra de negócio.
- [ ] `quickstart.md` permite que QA valide o fluxo principal.

## Referência

- [Cheat sheet do Spec-Kit](../../cheat-sheets/spec-kit-workflow.md)
- [Spec-Kit oficial](https://github.com/github/spec-kit)

— Paula
