---
title: "Estágio 2 — Spec Moderna"
description: "Etapa de especificação: escrever requisitos EARS, criar ADRs e definir a arquitetura do sistema moderno."
locale: "pt-br"
canonical_path: "06-kit-repositorio-times/02-spec-moderna/README.md"
author: "Paula Silva, Americas Software GBB, Microsoft"
date: "2026-05-18"
version: "2.0.0"
status: "approved"
tags: ["estagio-2", "especificacao", "ears", "adr", "workshop", "pt-br"]
---

<!-- markdownlint-disable MD013 MD025 MD026 MD028 MD029 MD034 MD040 MD051 MD060 -->

# Estágio 2 — Spec Moderna

> Escreva a especificação modernizada do SIFAP usando notação EARS, crie Architecture Decision Records (ADRs) e defina as fronteiras de escopo.

## Onde isso encaixa no SDLC

```mermaid
flowchart LR
 classDef done fill:#7FBA00,stroke:#5C8700,color:#fff
 classDef current fill:#F25022,stroke:#B33816,color:#fff,font-weight:bold
 classDef next fill:#FFF7E0,stroke:#FFB900,color:#0A0A0A
 classDef later fill:#F7F7F4,stroke:#C8C8C0,color:#6B6B6B

 D[Discovery<br/>Estágio 1 ✓]:::done
 SP[Specification + Design<br/>Estágio 2<br/>VOCÊ ESTÁ AQUI]:::current
 IM[Implementation<br/>Estágio 3]:::next
 EV[Evolution<br/>Estágio 4]:::later

 D --> SP --> IM --> EV
```

## Quem trabalha aqui

```mermaid
flowchart TB
 classDef lead fill:#FFB900,stroke:#B38600,color:#0A0A0A,font-weight:bold
 classDef support fill:#FFF7E0,stroke:#FFB900,color:#0A0A0A

 P2[Par 2 · Arquitetura<br/>EA + SA<br/>LIDERA<br/>C4 L2/L3 + ADRs]:::lead
 P1[Par 1 · Visão<br/>PO + RE<br/>EARS + sign-off de escopo]:::support
 P5[Par 5 · Operações<br/>DevOps + TW<br/>clareza de ADR + ADR de deploy]:::support
 P3[Par 3 · Implementação<br/>TL + Dev<br/>calibração de viabilidade]:::support
 P4[Par 4 · Qualidade<br/>DBA + QA<br/>cenários BDD + modelo de dados]:::support

 P2 --> H2{Handoff #2<br/>~16:00<br/>spec → código}
 P1 --> H2
 P5 --> H2
```

## Conteúdo

| Arquivo                                    | Propósito                                |
| ------------------------------------------ | ---------------------------------------- |
| [`GUIDE.md`](GUIDE.md)                     | Guia passo a passo deste estágio         |
| [`ADR-TEMPLATE.md`](ADR-TEMPLATE.md)       | Template de Architecture Decision Record |
| [`scope-decisions.md`](scope-decisions.md) | Template de decisões de escopo           |

## Navegação

| Anterior                                               | Início                    | Próximo                                                    |
| ------------------------------------------------------ | ------------------------- | ---------------------------------------------------------- |
| [Estágio 1 — Arqueologia](../01-arqueologia/README.md) | [Kit PT-BR](../README.md) | [Estágio 3 — Implementação](../03-implementacao/README.md) |

— Paula
