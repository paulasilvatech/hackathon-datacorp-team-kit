---
title: "Personas — Kit do Time"
description: "Definições de personas de IA para cada papel no workshop, usadas para configurar o comportamento dos agentes Copilot."
locale: "pt-br"
canonical_path: "06-kit-repositorio-times/personas/README.md"
author: "Paula Silva, Americas Software GBB, Microsoft"
date: "2026-05-18"
version: "2.0.0"
status: "approved"
tags: ["personas", "copilot", "papeis", "workshop", "kit", "pt-br"]
---

# Personas

> Cards de persona específicos por papel para cada membro do time. Definem expertise de domínio, responsabilidades e comportamento dos agentes Copilot para o workshop.

## Onde isso encaixa no SDLC

```mermaid
flowchart LR
 classDef discover fill:#F25022,stroke:#B33816,color:#fff
 classDef spec fill:#FFB900,stroke:#B38600,color:#0A0A0A
 classDef impl fill:#7FBA00,stroke:#5C8700,color:#fff
 classDef qual fill:#00A4EF,stroke:#0078D4,color:#fff
 classDef ops fill:#1B1B1F,stroke:#000,color:#fff

 D[Discovery<br/>PO + RE]:::discover
 SP[Specification<br/>EA + SA]:::spec
 IM[Implementation<br/>TL + Dev]:::impl
 Q[Quality<br/>DBA + QA]:::qual
 OP[Operations<br/>DevOps + TW]:::ops

 D --> SP --> IM --> Q --> OP
```

Cada par cobre 2 personas. Veja [`../TEAM-FLOW.md`](../TEAM-FLOW.md) para entender qual par lidera cada fase.

## Conteúdo

| Arquivo | Papel | Par |
|---------|-------|-----|
| [`01-product-owner.md`](01-product-owner.md) | Product Owner — prioridade de backlog e alinhamento com stakeholders | 1 · Visão |
| [`02-requirements-engineer.md`](02-requirements-engineer.md) | Requirements Engineer — notação EARS e escrita de spec | 1 · Visão |
| [`03-enterprise-architect.md`](03-enterprise-architect.md) | Enterprise Architect — decisões de design em nível de sistema | 2 · Arquitetura |
| [`04-software-architect.md`](04-software-architect.md) | Software Architect — arquitetura em nível de componente | 2 · Arquitetura |
| [`05-technical-lead.md`](05-technical-lead.md) | Technical Lead — padrões de código e coordenação de time | 3 · Implementação |
| [`06-developer.md`](06-developer.md) | Developer — implementação e testes | 3 · Implementação |
| [`07-dba.md`](07-dba.md) | DBA — design de banco e migrações | 4 · Qualidade |
| [`08-qa-engineer.md`](08-qa-engineer.md) | QA Engineer — estratégia de testes e cobertura | 4 · Qualidade |
| [`09-devops-engineer.md`](09-devops-engineer.md) | DevOps Engineer — CI/CD, IaC e deploy | 5 · Operações |
| [`10-tech-writer.md`](10-tech-writer.md) | Tech Writer — documentação e ADRs | 5 · Operações |

## Kits estendidos de persona

Para implementações completas de persona com agentes customizados, prompts e configs MCP, veja [`../../persona-kits/`](../../persona-kits/) (compartilhado, não traduzido).

## Navegação

| Anterior | Início | Próximo |
|----------|--------|---------|
| [Team Flow](../TEAM-FLOW.md) | [Kit PT-BR](../README.md) | [Product Owner](01-product-owner.md) |

— Paula
