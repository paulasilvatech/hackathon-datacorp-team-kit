---
title: "ADR-XXX: [Título da Decisão]"
description: "Modelo de Registro de Decisão Arquitetural (ADR). Toda decisão arquitetural importante precisa de um ADR com contexto, alternativas, decisão e consequências."
locale: "pt-br"
canonical_path: "06-kit-repositorio-times/02-spec-moderna/ADR-TEMPLATE.md"
author: "Paula Silva, Americas Software GBB, Microsoft"
date: "2026-05-18"
version: "1.0.0"
status: "template"
tags: ["estagio-2", "adr", "template", "pt-br"]
---

<!-- markdownlint-disable MD013 MD025 MD026 MD028 MD029 MD034 MD040 MD051 MD060 -->

# ADR-XXX: [Título da Decisão]

**Data**: 19/05/2026
**Status**: Proposta | Aceita | Rejeitada | Substituída por ADR-YYY
**Decisores**: [Nomes dos membros do time envolvidos]

## Como usar este template

Copie este arquivo para cada decisão arquitetural que valha a pena documentar. Renomeie para `ADR-001-titulo-curto.md`, `ADR-002-...`, etc. Um ADR de 1 linha não vale o esforço — se a decisão é tão pequena que cabe num commit message, talvez não precise de ADR.

**Regra de ouro:** sempre liste o "caminho não tomado". Sem isso, vira pura descrição de implementação, não decisão.

## Contexto

> Descreva o problema ou necessidade que motivou esta decisão.
> Inclua restrições, requisitos e informações relevantes.
> Seja específico — "precisamos de um banco de dados" não é suficiente.

[Escreva aqui]

## Opções Consideradas

### Opção 1: [Nome]

- **Descrição**: [como funcionaria]
- **Vantagens**: [liste]
- **Desvantagens**: [liste]

### Opção 2: [Nome]

- **Descrição**: [como funcionaria]
- **Vantagens**: [liste]
- **Desvantagens**: [liste]

### Opção 3: [Nome] (opcional)

- **Descrição**: [como funcionaria]
- **Vantagens**: [liste]
- **Desvantagens**: [liste]

## Decisão

> Declare a decisão tomada de forma clara e direta.
> Exemplo: "Decidimos usar PostgreSQL 16 como banco de dados relacional."

**Decidimos [ação/escolha].**

## Justificativa

> Explique POR QUE esta opção foi escolhida em detrimento das outras.
> Conecte com requisitos, restrições e contexto.

[Escreva aqui]

## Consequências

### Positivas

- [Consequência positiva 1]
- [Consequência positiva 2]

### Negativas

- [Consequência negativa 1 — e como mitigar]
- [Consequência negativa 2 — e como mitigar]

### Riscos

- [Risco identificado e plano de contingência]

## Referências

- [Link ou documento relevante]
- [Requisito EARS relacionado: REQ-XXX]
- [Regra de negócio relacionada: BR-XXX]
