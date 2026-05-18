---
title: "Estágio 3 — Implementação"
description: "Etapa de implementação: construir o protótipo do SIFAP 2.0 — backend Java 21, frontend Next.js 15, banco PostgreSQL 16 — usando GitHub Copilot Agent mode."
locale: "pt-br"
canonical_path: "06-kit-repositorio-times/03-implementacao/README.md"
author: "Paula Silva, Americas Software GBB, Microsoft"
date: "2026-05-18"
version: "2.0.0"
status: "approved"
tags: ["estagio-3", "implementacao", "codigo", "prototipo", "workshop", "pt-br"]
---

# Estágio 3 — Implementação

> Construa o protótipo do SIFAP 2.0 — backend Java 21 + Spring Boot 3, frontend Next.js 15, PostgreSQL 16 — usando o modo Agent do GitHub Copilot.

## Onde isso encaixa no SDLC

```mermaid
flowchart LR
 classDef done fill:#7FBA00,stroke:#5C8700,color:#fff
 classDef current fill:#F25022,stroke:#B33816,color:#fff,font-weight:bold
 classDef next fill:#FFF7E0,stroke:#FFB900,color:#0A0A0A

 SP[Specification ✓<br/>EARS + ADRs + C4]:::done
 IM[Implementation<br/>VOCÊ ESTÁ AQUI]:::current
 EV[Evolution<br/>Estágio 4]:::next

 SP --> IM --> EV
```

## Quem trabalha aqui

```mermaid
flowchart TB
 classDef lead fill:#7FBA00,stroke:#5C8700,color:#fff,font-weight:bold
 classDef qual fill:#00A4EF,stroke:#0078D4,color:#fff,font-weight:bold
 classDef support fill:#FFF7E0,stroke:#FFB900,color:#0A0A0A

 P3[Par 3 · Implementação<br/>TL + Dev<br/>LIDERA — código + reviews]:::lead
 P4[Par 4 · Qualidade<br/>DBA + QA<br/>LIDERA — schema + testes]:::qual
 P5[Par 5 · Operações<br/>scaffold do pipeline CI]:::support
 P1[Par 1 · Visão<br/>de plantão para clarificar requisitos]:::support
 P2[Par 2 · Arquitetura<br/>review de PRs que tocam contratos]:::support
```

## Conteúdo

| Arquivo | Propósito |
|---------|-----------|
| [`GUIDE.md`](GUIDE.md) | Guia passo a passo deste estágio |

## Navegação

| Anterior | Início | Próximo |
|----------|--------|---------|
| [Estágio 2 — Spec Moderna](../02-spec-moderna/README.md) | [Kit PT-BR](../README.md) | [Estágio 4 — Evolution](../04-evolucao/README.md) |

— Paula
