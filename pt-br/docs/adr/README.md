---
title: "Índice de ADRs"
description: "Architecture Decision Records para a modernização SIFAP 2.0 desta equipe"
author: "Tech Writer (time)"
date: "2026-04-29"
version: "1.0.0"
status: "draft"
tags: ["adr", "architecture", "decisions"]
---

<!-- markdownlint-disable MD013 MD025 MD026 MD028 MD029 MD034 MD040 MD051 MD060 -->

# Architecture Decision Records (ADRs)

> Por que ADRs? Decisões tomadas sob pressão de tempo são esquecidas. O você do futuro vai
> redescobrir as mesmas opções e perder horas. ADRs são 5 minutos de escrita agora
> que economizam 50 minutos depois.

## Quando escrever um ADR

Escreva um ADR quando:

- Uma decisão for difícil de revisitar depois (>1 hora para desfazer).
- Duas ou mais pessoas da equipe chegariam a defaults diferentes.
- Uma decisão afetar mais de um bounded context ou persona.

Não escreva ADR para: nomes de variáveis, configurações de formatter, versões minor de bibliotecas.

## Índice

| ADR  | Titulo                       | Status   | Data       |
| ---- | ---------------------------- | -------- | ---------- |
| 0000 | [Template](0000-template.md) | template | 2026-04-29 |

> Adicione novos ADRs acima conforme criá-los, com status `proposed` primeiro, depois
> `accepted` após acordo da equipe.

## Como adicionar um ADR

1. Abra uma issue usando o [template de issue de ADR](../../.github/ISSUE_TEMPLATE/adr.yml)
2. Copie `0000-template.md` para `NNNN-your-title.md` (próximo número sequencial)
3. Preencha todas as seções
4. Abra um PR; exija pelo menos 1 revisão de uma architect-persona
5. Faca merge com status `accepted`
6. Atualize este índice
