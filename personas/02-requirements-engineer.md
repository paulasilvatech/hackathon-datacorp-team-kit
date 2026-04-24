---
title: "Ficha da Persona - Requirements Engineer"
description: "O que o Requirements Engineer faz dentro do time de 10 durante o Dia 2 do Hackathon SERPRO 2026."
author: "Paula Silva, Americas Software GBB, Microsoft"
date: "2026-04-18"
version: "1.0.0"
persona_id: "02"
tags: ["persona", "requirements-engineer", "hackathon", "SERPRO", "EARS"]
---

# Persona - Requirements Engineer

## Quem é essa pessoa

É quem pega a conversa solta e transforma em requisito testável. Ao lado do PO, é quem protege o time de escrever código para um problema mal formulado. Em um legado como o SIFAP, esse papel é crítico: as regras estão tacitamente codificadas em Natural e ninguém mais as articula.

## Missão no hackathon

Converter o que foi descoberto no Estágio 1 em requisitos formais e testáveis no Estágio 2. Garantir que os requisitos escrevem-se em EARS, que estão numerados, e que cada um tem critério de verificação.

## Seu papel no framework Agentic Legacy Modernization

Este hackathon aplica o framework **Agentic Legacy Modernization** - uma abordagem de modernizacao de sistemas legado usando agentes de IA especializados em cada fase. O pipeline completo esta descrito no `01-blueprint/HACKATHON-BLUEPRINT.md`. Sua persona mapeia para o pipeline assim:

- **Agentes relevantes**: Analysis Agent (E1-E2), Spec Engineer (E2)
- **Fase do framework**: Application Carving → Translation
- **Seu papel no pipeline**: Converte regras extraidas em requisitos formais EARS para guiar a traducao

## Onde você aparece por estágio

| Estágio | Você faz isto | Entregável que depende de você |
|---|---|---|
| 1. Arqueologia | Extrai regras candidatas dos Naturals. Classifica: regra de negócio, validação, cálculo, integração. | Catálogo de regras (tabela) |
| 2. Spec Greenfield | Converte o catálogo em requisitos EARS. Mantém rastreabilidade legado → requisito. Estrutura a spec com o PO. | Seção "Functional Requirements" em notação EARS |
| 3. Reconstrução | Responde dúvidas de requisito durante o código. Ajusta redação quando surge ambiguidade real. | Spec viva, não congelada |
| 4. Evolução com Agent | Revisa se as duas issues cobrem requisito novo ou ajuste de requisito existente. | Coerência entre issues e spec |

## Ferramentas e primitives

- **Specky** - fase 2 (Requirements) é o seu território. O plugin gera o esqueleto EARS para você refinar.
- **Copilot Chat** para validar coerência entre requisitos. Prompt típico: "analise se estes 5 requisitos são mutuamente consistentes".
- **MCP/filesystem** do repositório para navegar pelos `.NSN` do legado e correlacionar com requisitos.
- Templates de `25-personas-primitives` - skills para extração de regras e conversão para EARS.

## Cheat sheets que você usa

- `cheat-sheets/specky-workflow.md` - fase 2 com exemplos EARS.
- `cheat-sheets/model-routing.md` - para decidir quando Claude Sonnet 4.6 em vez de Opus 4.6 (requisitos pedem ambos).

## Como se sai bem

- Seus requisitos usam verbos ativos e são testáveis.
- Cada regra do legado tem rastreabilidade explícita para o requisito moderno.
- Você diz "isto é ambíguo, precisa de decisão" antes de o código ser escrito.
- Usa os cinco padrões EARS sem confundir (ubíquo, disparado por evento, por estado, comportamento indesejado, opcional).

## Como se perde

- Escreve requisitos como parágrafos ao invés de EARS.
- Duplica no texto o que já está numa ADR.
- Deixa regras do legado sem correspondência.
- Confunde requisito com design ("o sistema deve usar Redis" não é requisito).

## Se você acumulou duas personas

- **RE + Product Owner** é o par natural (PO diz "por quê"; RE diz "como verificar que foi feito").
- **RE + QA Engineer** também é forte - você escreve o requisito e quem testa é você mesmo.

## 3 Prompts Exemplares

1. **(Chat)** "Leia esta regra do SIFAP legado e converta para notacao EARS: [cole a regra]. Identifique qual dos 6 padroes EARS se aplica e explique por que."
2. **(Chat)** "Analise estes 5 requisitos EARS e encontre: (a) ambiguidades que precisam de decisao do PO, (b) dependencias entre eles, (c) requisitos que conflitam."
3. **(Edits)** "No arquivo SPECIFICATION.md, adicione requisitos EARS para o modulo de auditoria baseado nas regras BR-008 a BR-012 do catalogo. Use os padroes Evento e Comportamento Indesejado."

## Se Você Ficar Travado (Defaults de Emergência)

- **Não sabe EARS?** Abra `02-spec-moderna/GUIDE.md` seção "Notação EARS" - 3 padrões com exemplos.
- **Requisito ambíguo?** Escreva duas interpretações e pergunte ao PO qual é a certa.
- **Muitas regras, pouco tempo?** Foque nas regras de CÁLCULO e VALIDAÇÃO (são as mais críticas para pagamento).
- **Specky não funciona?** Escreva EARS manualmente no SPECIFICATION.md - o formato é texto simples.

## Dependências - Quem Depende de Você

| Persona | Relação | Artefato |
|---------|---------|----------|
| Product Owner | VOCÊ depende dele | Priorização de regras |
| Developer | Depende de VOCÊ | Requisitos claros para implementar |
| QA Engineer | Depende de VOCÊ | Requisitos testáveis com critérios de verificação |
| Software Architect | Depende de VOCÊ | Requisitos para desenhar bounded contexts |

## Como Você É Avaliado

- **Rubrica A2 (Coerência da Spec):** requisitos em EARS, numerados, rastreáveis ao legado.
- **Rubrica A1 (Arqueologia):** catálogo de regras com classificação.
- Critério: "Cada requisito tem verbo ativo e é testável."

- Paula
