---
title: "Ficha da Persona - Enterprise Architect"
description: "O que o Enterprise Architect faz dentro do time de 10 durante o Dia 2 do Hackathon SERPRO 2026."
author: "Paula Silva, Americas Software GBB, Microsoft"
date: "2026-04-18"
version: "1.0.0"
persona_id: "03"
tags: ["persona", "enterprise-architect", "hackathon", "SERPRO"]
---

# Persona - Enterprise Architect

## Quem é essa pessoa

É quem enxerga o sistema dentro do ecossistema. No SIFAP, isso significa: SIAFI, Banco do Brasil, INCRA, MDA, e outras entranhas governamentais. O EA sabe onde os contratos estão, quais são frágeis e quais podem ser tocados sem acionar toda a cadeia.

## Missão no hackathon

Garantir que o SIFAP 2.0 não quebre o mundo em volta dele. Desenhar o mapa de dependências. Validar que a arquitetura alvo respeita os contratos externos (síncrono com SIAFI, assíncrono com BB) e que a estratégia de coexistência com o legado é viável.

## Seu papel no framework Agentic Legacy Modernization

Este hackathon aplica o framework **Agentic Legacy Modernization** - uma abordagem de modernizacao de sistemas legado usando agentes de IA especializados em cada fase. O pipeline completo esta descrito no `01-blueprint/HACKATHON-BLUEPRINT.md`. Sua persona mapeia para o pipeline assim:

- **Agentes relevantes**: Discovery Agent (E1), Deployment Agent (E4)
- **Fase do framework**: Assessment → Coexistence and Traffic Migration
- **Seu papel no pipeline**: Mapeia dependencias externas e define estrategia de coexistencia (Strangler Fig)

## Onde você aparece por estágio

| Estágio | Você faz isto | Entregável que depende de você |
|---|---|---|
| 1. Arqueologia | Constrói o mapa de dependências e integrações (C4 nível 1 - sistema em contexto). Identifica contratos externos. | Diagrama C4 Nível 1 + inventário de integrações |
| 2. Spec Greenfield | Define as decisões de topologia (onde o sistema mora no cloud, quem é cliente de quem, que APIs são síncronas e por quê). | ADRs de topologia e integração (1-2) |
| 3. Reconstrução | Valida que a implementação respeita os contratos desenhados. Ajuda o DevOps com Terraform em alto nível. | Validação do layout deployado |
| 4. Evolução com Agent | Avalia se as issues do Estágio 4 têm implicações arquiteturais que precisam ser revistas primeiro. | Parecer de impacto |

## Ferramentas e primitives

- **Mermaid** e **C4** para diagramas.
- **Copilot Chat** para validar decisões de topologia com prompts de pressão ("que risco esse desenho tem se o SIAFI ficar offline?").
- **Specky** na fase 3 (Context/Architecture) - produz o C4 e o ADR automaticamente a partir da spec.
- Skills de `25-personas-primitives` - prompts estruturados para análise de dependências.

## Cheat sheets que você usa

- `cheat-sheets/specky-workflow.md` - fase 3.
- `cheat-sheets/model-routing.md` - use **Opus 4.6** quando estiver fazendo análise de impacto arquitetural.

## Como se sai bem

- O C4 nível 1 está legível por qualquer pessoa não-técnica do time em 30 segundos.
- Suas ADRs nomeiam o "caminho não escolhido" e dizem por quê.
- Você ancora Modular Monolith na argumentação - não por moda, por aderência ao contexto SERPRO.
- Alinha com o Software Architect onde termina seu escopo e começa o dele.

## Como se perde

- Desenha diagrama que só você entende.
- Propõe microserviços (arquitetura é fixada - ADR explicando é legítimo; persistir é perda).
- Esquece integrações reais (SIAFI, BB) e o Estágio 3 descobre tarde.
- Duplica trabalho do Software Architect em vez de traçar fronteira clara.

## Se você acumulou duas personas

- **EA + Software Architect** é a acumulação mais comum em time pequeno. Você trata Nível 1 do C4; seu par trata Níveis 2 e 3.
- **EA + Technical Lead** também funciona se você quiser mais mão na massa.

## 3 Prompts Exemplares

1. **(Chat)** "Crie um diagrama C4 Nivel 1 em Mermaid para o SIFAP 2.0 mostrando: 3 tipos de usuario, o sistema central, e 4 sistemas externos (SIAFI, Receita Federal, Banco do Brasil, CadUnico)."
2. **(Chat)** "Se o SIAFI ficar offline por 2 horas durante o ciclo mensal de pagamentos, qual o impacto? Proponha 3 estrategias de fallback e recomende uma."
3. **(Chat)** "Compare estas 3 opcoes de integracao com o Banco do Brasil: CNAB batch, API REST sincrona, mensageria assincrona. Escreva uma ADR recomendando uma."

## Se Você Ficar Travado (Defaults de Emergência)

- **Não sabe C4?** Use Mermaid flowchart simples: boxes = sistemas, arrows = integrações. Nomeie as setas.
- **Perdeu tempo no C4 Nível 3?** Pare. Nível 1 + Nível 2 são suficientes. Times raramente precisam de L3.
- **Não sabe Mermaid?** Peça ao Copilot: "Crie diagrama C4 nível 1 em Mermaid para um sistema de pagamentos que integra com SIAFI e Banco do Brasil."
- **Discorda do Software Architect?** Escreva ADR com as duas opções e peça voto do time.

## Dependências - Quem Depende de Você

| Persona | Relação | Artefato |
|---------|---------|----------|
| Software Architect | Depende de VOCÊ | C4 L1 para ele desenhar L2/L3 |
| DevOps Engineer | Depende de VOCÊ | Topologia para Terraform |
| Developer | Depende de VOCÊ (indireta) | Contratos de integração |
| Requirements Engineer | VOCÊ depende dele | Requisitos de integração |

## Como Você É Avaliado

- **Rubrica A1 (Arqueologia):** mapa de dependências legível por não-técnico.
- **Rubrica A2 (Coerência da Spec):** ADRs nomeiam "caminho não escolhido".
- Critério: "C4 L1 entendido em 30 segundos por qualquer pessoa do time."

- Paula
