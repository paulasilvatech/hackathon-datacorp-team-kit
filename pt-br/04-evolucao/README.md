---
title: "Estágio 4 — Evolution"
description: "Etapa de evolução: adicionar infraestrutura como código (Terraform), pipeline CI/CD (GitHub Actions) e iterar usando workflows com agentes."
locale: "pt-br"
canonical_path: "06-kit-repositorio-times/04-evolucao/README.md"
author: "Paula Silva, Americas Software GBB, Microsoft"
date: "2026-05-18"
version: "2.0.0"
status: "approved"
tags:
  ["estagio-4", "evolution", "terraform", "cicd", "agent", "workshop", "pt-br"]
---

<!-- markdownlint-disable MD013 MD025 MD026 MD028 MD029 MD034 MD040 MD051 MD060 -->

# Estágio 4 — Evolution

> Adicione infraestrutura como código (Terraform), pipeline CI/CD (GitHub Actions) e itere usando workflows com o modo Agent do GitHub Copilot.

## Onde isso encaixa no SDLC

```mermaid
flowchart LR
 classDef done fill:#7FBA00,stroke:#5C8700,color:#fff
 classDef current fill:#F25022,stroke:#B33816,color:#fff,font-weight:bold
 classDef demo fill:#00A4EF,stroke:#0078D4,color:#fff

 IM[Implementation ✓<br/>Backend + Frontend]:::done
 EV[Evolution<br/>IaC + CI/CD + Agent]:::current
 DM[Demo + Retro]:::demo

 IM --> EV --> DM
```

## Quem trabalha aqui

```mermaid
flowchart TB
 classDef ops fill:#1B1B1F,stroke:#000,color:#fff,font-weight:bold
 classDef impl fill:#7FBA00,stroke:#5C8700,color:#fff
 classDef qual fill:#00A4EF,stroke:#0078D4,color:#fff

 P5[Par 5 · Operações<br/>DevOps + TW<br/>LIDERA — Terraform + CI/CD + runbook]:::ops
 P3[Par 3 · Implementação<br/>TL + Dev<br/>CO-LIDERA — review do Agent PR]:::impl
 P4[Par 4 · Qualidade<br/>DBA + QA<br/>gate final de cobertura]:::qual
```

## Conteúdo

| Arquivo                                                    | Propósito                                        |
| ---------------------------------------------------------- | ------------------------------------------------ |
| [`GUIDE.md`](GUIDE.md)                                     | Guia passo a passo deste estágio                 |
| [`agent-experience-report.md`](agent-experience-report.md) | Template de relatório de experiência com o Agent |

## Navegação

| Anterior                                                   | Início                    | Próximo              |
| ---------------------------------------------------------- | ------------------------- | -------------------- |
| [Estágio 3 — Implementação](../03-implementacao/README.md) | [Kit PT-BR](../README.md) | Demo + Retrospectiva |

— Paula
