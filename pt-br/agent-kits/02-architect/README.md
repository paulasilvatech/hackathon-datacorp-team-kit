---
title: "@architect — Estágio 2: Spec Moderna"
description: "Guia didático do agente de especificação moderna: EARS, bounded contexts, C4, ADRs e plano técnico com Spec-Kit"
author: "Paula Silva, Americas Software GBB, Microsoft"
date: "2026-05-18"
version: "2.0.0"
status: "approved"
tags: ["agent", "architect", "specification", "ears", "adr", "stage-2", "pt-br"]
---

<!-- markdownlint-disable MD013 MD025 MD026 MD028 MD029 MD034 MD040 MD051 MD060 -->

# @architect — Estágio 2: Spec Moderna

> Use este agente quando o time já tem descobertas do legado e precisa transformá-las em especificação moderna. Ele ajuda a decidir limites, escrever EARS, registrar ADRs e preparar o terreno para implementação.

## Objetivo da etapa

Transformar o discovery report em uma spec implementável: requisitos rastreáveis, bounded contexts, diagramas C4, ADRs e plano técnico alinhado ao GitHub Spec-Kit.

## Quando usar

- **Horário:** 14:45–16:00.
- **Protagonista:** Software Architect.
- **Suporte forte:** Requirements Engineer, Enterprise Architect, Product Owner e Technical Lead.
- **Pré-requisito:** Handoff #1 com evidências do legado e `source_legacy:` disponíveis.

## Passo a passo com o agente

1. Selecione o agente `@architect` no Copilot Chat.
2. Cole o prompt de abertura abaixo.
3. Liste as regras e mistérios vindos do Estágio 1.
4. Use `/speckit.specify` e `/speckit.clarify` para formalizar requisitos.
5. Use `/speckit.plan` para gerar plano técnico, dados e contratos.
6. Registre decisões importantes em ADRs.
7. Faça o Handoff #2 para os Pares 3 e 4.

```text
Estou iniciando o Estágio 2 — Spec Moderna.
Temos discovery report, catálogo de regras, glossário, DDMs e mapa de dependências.
Ajude a transformar isso em requisitos EARS com source_legacy, bounded contexts,
C4, ADRs e plano técnico para Java 21 + Spring Boot + PostgreSQL + Next.js.
```

## O que perguntar

| Situação | Prompt útil |
| --- | --- |
| Regra de negócio bruta | "Converta esta regra em EARS com REQ-ID, acceptance e source_legacy." |
| Limite de módulo incerto | "Compare 2 ou 3 bounded contexts possíveis e mostre prós/contras." |
| Decisão arquitetural | "Gere um ADR com contexto, opções, decisão, consequências e riscos." |
| Plano técnico | "Prepare `/speckit.plan` considerando modular monolith, JPA e PostgreSQL." |

## Definition of Done

- [ ] Pelo menos 12 requisitos EARS com REQ-IDs.
- [ ] 100% dos requisitos com `source_legacy:` ou `[GREENFIELD]` justificado.
- [ ] C4 L1/L2/L3 ou equivalente Mermaid para orientar implementação.
- [ ] ADRs principais: modular monolith, persistência e autenticação.
- [ ] `spec.md`, `plan.md` e `tasks.md` preparados ou em progresso no fluxo Spec-Kit.
- [ ] Escopo assinado pelo Product Owner no Handoff #2 (~16:00).

## Anti-padrões

| Não faça | Faça |
| --- | --- |
| Escrever requisito sem evidência | Exija `source_legacy:` ou justificativa greenfield |
| Criar arquitetura bonita demais para o tempo | Prefira decisões simples, testáveis e implementáveis |
| Misturar ADR com opinião solta | Registre opções, decisão e consequências |
| Entregar spec sem acceptance | Todo requisito precisa ser testável |

## Navegação

| Anterior | Início | Próximo |
| --- | --- | --- |
| [@archaeologist](../01-archaeologist/README.md) | [Kit PT-BR](../../README.md) | [@builder](../03-builder/README.md) |

— Paula
