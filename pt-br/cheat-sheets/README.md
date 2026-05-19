---
title: "Cheat Sheets — Kit do Time"
description: "Cartões de referência rápida para participantes do workshop, cobrindo os modos Ask, Plan e Agent do Copilot, o pipeline Spec-Kit e roteamento de modelos."
locale: "pt-br"
canonical_path: "06-kit-repositorio-times/cheat-sheets/README.md"
author: "Paula Silva, Americas Software GBB, Microsoft"
date: "2026-05-18"
version: "2.0.0"
status: "approved"
tags: ["cheat-sheet", "copilot", "spec-kit", "model-routing", "workshop", "pt-br"]
---

<!-- markdownlint-disable MD013 MD025 MD026 MD028 MD029 MD034 MD040 MD051 MD060 -->

# Cheat Sheets

> Cartões de uma página para impressão, desenhados para ficar na mesa de cada time.

## Quando usar isso

Você abre um cheat-sheet quando precisa de **resposta rápida** sem ler um guia completo. Cada um responde uma pergunta específica:

```mermaid
flowchart LR
 classDef sheet fill:#FFF7E0,stroke:#FFB900,color:#0A0A0A

 Q1["É Ask, Plan ou Agent?"]:::sheet --> S1[copilot-3-modes.md]
 Q2["Qual comando do Spec-Kit uso?"]:::sheet --> S2[spec-kit-workflow.md]
 Q3["Qual modelo Claude usar agora?"]:::sheet --> S3[model-routing.md]
```

## Conteúdo

| Arquivo                                    | Tópico                                          | Use quando                                           |
| ------------------------------------------ | ----------------------------------------------- | ---------------------------------------------------- |
| [`copilot-3-modes.md`](copilot-3-modes.md) | GitHub Copilot: modos Ask, Plan e Agent         | Estiver na dúvida sobre qual modo do Copilot acionar |
| [`spec-kit-workflow.md`](spec-kit-workflow.md) | Fluxo Spec-Kit de relance                       | Não souber qual comando `/speckit.*` usar            |
| [`model-routing.md`](model-routing.md)     | Qual modelo de IA usar para cada tipo de tarefa | Estiver decidindo entre Haiku, Sonnet ou Opus        |

## Navegação

| Anterior                          | Início                    | Próximo                               |
| --------------------------------- | ------------------------- | ------------------------------------- |
| [Persona Kits](../persona-kits/README.md) | [Kit PT-BR](../README.md) | [Copilot 3 Modes](copilot-3-modes.md) |

— Paula
