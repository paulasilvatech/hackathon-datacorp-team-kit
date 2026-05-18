---
title: "Estágio 1 — Arqueologia"
description: "Etapa de análise do código legado: explorar os programas Natural do SIFAP, extrair regras de negócio e construir o glossário do domínio."
locale: "pt-br"
canonical_path: "06-kit-repositorio-times/01-arqueologia/README.md"
author: "Paula Silva, Americas Software GBB, Microsoft"
date: "2026-05-18"
version: "2.0.0"
status: "approved"
tags: ["estagio-1", "arqueologia", "legado", "analise", "workshop", "pt-br"]
---

# Estágio 1 — Arqueologia

> **LEIA PRIMEIRO:** [`LEGACY-EXPLORATION-CHECKLIST.md`](LEGACY-EXPLORATION-CHECKLIST.md) — portão duro antes do Estágio 2.
>
> Explore o sistema SIFAP legado com Copilot Chat e Specky Research. Extraia regras de negócio, construa um glossário e mapeie dependências. Todo artefato produzido aqui alimenta o Estágio 2; especificações sem rastreabilidade ao legado são rejeitadas pelo CI.

## Onde isso encaixa no SDLC

```mermaid
flowchart LR
 classDef current fill:#F25022,stroke:#B33816,color:#fff,font-weight:bold
 classDef next fill:#FFF7E0,stroke:#FFB900,color:#0A0A0A
 classDef later fill:#F7F7F4,stroke:#C8C8C0,color:#6B6B6B

 D[Discovery<br/>Estágio 1<br/>VOCÊ ESTÁ AQUI]:::current
 SP[Specification<br/>Estágio 2]:::next
 IM[Implementation<br/>Estágio 3]:::later
 EV[Evolution<br/>Estágio 4]:::later

 D --> SP --> IM --> EV
```

## Quem trabalha aqui

Todos os 5 pares trabalham em paralelo, cada um responsável por 3 programas Natural. O **Par 1 (Visão)** lidera a síntese ao final do estágio. Veja [`GUIDE.md`](GUIDE.md) para a divisão completa.

## Conteúdo

| Arquivo | Propósito |
|---------|-----------|
| [`LEGACY-EXPLORATION-CHECKLIST.md`](LEGACY-EXPLORATION-CHECKLIST.md) | **PORTÃO DURO.** Posse de programa por par + DoD para abrir o Estágio 2 |
| [`GUIDE.md`](GUIDE.md) | Guia passo a passo deste estágio |
| [`glossary.md`](glossary.md) | Template de glossário de termos do domínio |
| [`business-rules-catalog.md`](business-rules-catalog.md) | Catálogo de regras de negócio extraídas (`Programa Fonte` obrigatório) |
| [`dependency-map.md`](dependency-map.md) | Template de mapeamento de dependências do sistema |
| [`discovery-report.md`](discovery-report.md) | Template de relatório de descobertas |
| [`mysteries-checklist.md`](mysteries-checklist.md) | Checklist de lógica escondida para os times |
| [`mysteries-found.md`](mysteries-found.md) | Template para registrar mistérios descobertos |

O código legado em si fica em [`../../legacy/`](../../legacy/) (compartilhado pelo kit).

## Navegação

| Anterior | Início | Próximo |
|----------|--------|---------|
| [Team Flow](../TEAM-FLOW.md) | [Kit PT-BR](../README.md) | [Estágio 2 — Spec Moderna](../02-spec-moderna/README.md) |

— Paula
