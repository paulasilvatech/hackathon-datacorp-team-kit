---
title: "Agent Kits — 4 Agentes de Etapa do SDLC"
description: "Camada horizontal de agentes por etapa do workshop, complementar aos 10 persona-kits usados pelas 5 pessoas do time"
author: "Paula Silva, Americas Software GBB, Microsoft"
date: "2026-05-18"
version: "2.0.0"
status: "approved"
tags: ["agents", "sdlc", "copilot", "hackathon", "pt-br"]
---

<!-- markdownlint-disable MD013 MD025 MD026 MD028 MD029 MD034 MD040 MD051 MD060 -->

# Agent Kits — 4 Agentes de Etapa do SDLC


> **Para quem é isto?** Para o time inteiro entender como os 4 agentes de estágio funcionam.
>
> **O que você terá ao final desta leitura:**
>
> 1. Diferença entre persona-kits (coluna) e agent-kits (linha)
> 2. Os 4 agentes: @archaeologist, @architect, @builder, @evolution
> 3. Quando trocar de agente durante o dia

> Se os [persona-kits](../persona-kits/) são as **colunas** do time (um kit por papel), os agent-kits são as **linhas do tempo** (um agente por etapa). Cada pessoa usa suas duas personas o dia inteiro, mas o agente de etapa muda conforme o relógio avança.

## Por que isso existe

Um workshop de modernização falha quando cada pessoa usa o Copilot de um jeito diferente. Os agent-kits resolvem isso: eles dão ao time um ritual comum para cada etapa.

| Etapa | Horário | Agente | Para que serve |
| --- | --- | --- | --- |
| 1 · Arqueologia | 11:00–12:00 + 13:30–14:00 | [@archaeologist](01-archaeologist/README.md) | Ler legado, extrair regras, mapear dependências e catalogar mistérios |
| 2 · Spec Moderna | 14:00–15:00 | [@architect](02-architect/README.md) | Transformar descobertas em EARS, bounded contexts, C4 e ADRs |
| 3 · Implementação | 15:00–16:10 | [@builder](03-builder/README.md) | Construir Java/Next.js, testes, migrations e endpoints rastreáveis |
| 4 · Evolução | 16:10–16:50 | [@evolution](04-evolution/README.md) | Delegar issues para o modo Agent, revisar PRs, CI/CD e IaC |

## Como usar, passo a passo

1. **Confirme a etapa atual** em [TEAM-FLOW.md](../TEAM-FLOW.md).
2. **Abra o README do agente da etapa** na tabela acima.
3. **Selecione o agente no Copilot Chat** usando o seletor de agentes.
4. **Cole o prompt de abertura** do README da etapa.
5. **Trabalhe nos entregáveis da Definição de Pronto.** Não pule o gate; ele existe para proteger o passagem seguinte.

## Matriz rápida persona × agente

**Protagonista** conduz a conversa com o agente. **Secundário** contribui ativamente. **Observador** acompanha e tira dúvidas quando chamado.

| Persona | @archaeologist | @architect | @builder | @evolution |
| --- | --- | --- | --- | --- |
| Product Owner | Observador | Secundário | Observador | Secundário |
| Requirements Engineer | **Protagonista** | Secundário | Observador | Observador |
| Enterprise Architect | Secundário | Secundário | Observador | Observador |
| Software Architect | Observador | **Protagonista** | Secundário | Observador |
| Technical Lead | Observador | Secundário | Secundário | **Protagonista** |
| Developer | Observador | Observador | **Protagonista** | Secundário |
| DBA | Secundário | Observador | Secundário | Observador |
| QA Engineer | Observador | Observador | Secundário | Secundário |
| DevOps Engineer | Observador | Observador | Secundário | Secundário |
| Tech Writer | Secundário | Observador | Observador | Secundário |

Para a versão detalhada, use [docs/persona-agent-matrix.md](../docs/persona-agent-matrix.md).

## Regra no-silver-platter

Os agentes sabem **como** modernizar Natural/Adabas. Eles não sabem **o que** existe no legado do seu time. Isso é proposital: o aprendizado acontece quando o time lê, debate e registra evidências.

| Pedido ruim | Resposta esperada do agente |
| --- | --- |
| "Me diga tudo que o sistema faz" | "Abra o primeiro arquivo e vamos ler juntos." |
| "Crie a arquitetura sem ler o legado" | "Ainda estamos sem evidência. Volte ao Estágio 1." |
| "Implemente sem REQ-ID" | "Falta rastreabilidade. Crie ou aponte o requisito." |

## Como saber que funcionou

- O time está usando o mesmo agente na mesma etapa.
- O protagonista sabe qual entregável precisa sair daquela conversa.
- A etapa termina com artefatos versionados, não apenas com conversa no chat.
- O passagem seguinte recebe evidências, decisões e pendências explícitas.

## Navegação

| Anterior | Início | Próximo |
| --- | --- | --- |
| [Persona Kits](../persona-kits/) | [Kit PT-BR](../README.md) | [Docs](../docs/) |

— Paula
