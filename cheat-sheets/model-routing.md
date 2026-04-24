---
title: "Cheat Sheet - Roteamento de Modelos Claude no Copilot"
description: "Uma página. Quando usar Claude Haiku 4.5, Sonnet 4.6 ou Opus 4.6 dentro do GitHub Copilot. Regras simples, casos típicos."
author: "Paula Silva"
date: "2026-04-18"
version: "1.0.0"
tags: ["cheat-sheet", "copilot", "claude", "model-routing", "hackathon", "SERPRO"]
---

# Roteamento de Modelos Claude - Cheat Sheet

## Regra-mãe

> Modelo maior = mais capaz e mais lento. Use o menor que resolve o seu caso. Economize Opus para decisão, não para produção em lote.

## Os três modelos

| Modelo | Quando usar | Custo relativo | Velocidade |
|---|---|---|---|
| **Haiku 4.5** | Tarefa mecânica, transformação simples, pequeno contexto | Baixo | Rápido |
| **Sonnet 4.6** | Padrão do dia a dia. Código, testes, refactor, explicação | Médio | Médio |
| **Opus 4.6** | Decisão arquitetural, análise de impacto, discussão de trade-off | Alto | Lento |

## Casos típicos por persona

### Product Owner / Requirements Engineer
- Escrever história de usuário → **Sonnet**.
- Refinar EARS já escritas → **Haiku**.
- Discutir se um requisito deveria ser v1 ou v2 → **Opus** (uma vez, decidir, seguir).

### Architects (Enterprise + Software)
- Desenhar C4 com Mermaid → **Sonnet**.
- Decidir entre dois padrões (hexagonal vs camadas) → **Opus**.
- Gerar variação sintática de diagrama que já existe → **Haiku**.

### Technical Lead
- Revisar PR de tamanho médio → **Sonnet**.
- Decidir padrão global do projeto (estilo de transação, p.ex.) → **Opus** no início; **Sonnet** depois para aplicar.
- Responder "esse código compila?" → **Haiku**.

### Developer
- Gerar implementação de um serviço → **Sonnet**.
- Escrever teste unitário simples → **Haiku**.
- Debater estrutura de uma classe antes de escrever → **Opus**.

### DBA
- Traduzir DDM Adabas → SQL → **Sonnet** (com Opus para o caso mais esquisito).
- Gerar DDL repetitivo → **Haiku**.
- Decidir estratégia de particionamento do `payment` → **Opus**.

### QA Engineer
- Gerar esqueleto de JUnit 5 → **Haiku**.
- Escrever teste de integração não-trivial → **Sonnet**.
- Decidir se dado cenário vale Testcontainers vs mock → **Opus**.

### DevOps Engineer
- Gerar YAML GitHub Actions padrão → **Sonnet**.
- Ajustar comandos triviais no workflow → **Haiku**.
- Decidir topologia Azure → **Opus**.

### Tech Writer
- Revisar estilo do README → **Haiku**.
- Redigir ADR → **Sonnet**.
- Decidir estrutura global da documentação → **Opus**, uma vez.

## Sinais de que você está no modelo errado

- **Está esperando 30s por resposta trivial** → suba para modelo menor.
- **Resposta veio rasa em decisão crítica** → suba para Opus.
- **Resposta está corretíssima mas você queria discussão** → suba para Opus.
- **Você está empilhando prompts para Opus gerar 400 arquivos** → desce para Sonnet ou Haiku.

## Dica de Paula

Não trate Opus como "o bom" e Haiku como "o ruim". Opus em tarefa mecânica é desperdício; Haiku em decisão é risco. O modelo certo é o mais barato que não te deixa na mão.

- Paula
