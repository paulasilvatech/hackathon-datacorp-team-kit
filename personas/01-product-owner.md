---
title: "Ficha da Persona - Product Owner"
description: "O que o Product Owner faz dentro do time de 10 durante o Dia 2 do Hackathon SERPRO 2026."
author: "Paula Silva, Americas Software GBB, Microsoft"
date: "2026-04-18"
version: "1.0.0"
persona_id: "01"
tags: ["persona", "product-owner", "hackathon", "SERPRO"]
---

# Persona - Product Owner

## Quem é essa pessoa

Dona do "porquê". É quem garante que o time não se perca fazendo código bonito para o problema errado. No contexto do SIFAP 2.0, o PO sabe que 2,3 milhões de beneficiários dependem do sistema, sabe que o ciclo mensal é sagrado, e carrega essa prioridade para dentro de cada decisão técnica.

## Missão no hackathon

Traduzir o cenário SIFAP em escopo executável nas oito horas do dia. Proteger o valor de negócio quando o time começar a querer reconstruir o legado linha por linha. Priorizar, cortar, explicar.

## Seu papel no framework Agentic Legacy Modernization

Este hackathon aplica o framework **Agentic Legacy Modernization** - uma abordagem de modernizacao de sistemas legado usando agentes de IA especializados em cada fase. O pipeline completo esta descrito no `01-blueprint/HACKATHON-BLUEPRINT.md`. Sua persona mapeia para o pipeline assim:

- **Agentes relevantes**: Discovery Agent (E1), Analysis Agent (E1-E2)
- **Fase do framework**: Assessment and Code Archaeology → Application Carving
- **Seu papel no pipeline**: Define escopo de carving e prioriza bounded contexts para migracao

## Onde você aparece por estágio

| Estágio | Você faz isto | Entregável que depende de você |
|---|---|---|
| 1. Arqueologia | Lidera a construção do glossário e captura dos "porquês" das regras. Mantém uma lista de perguntas de negócio abertas. | Glossário + "lista de mistérios" priorizada |
| 2. Spec Greenfield | Decide o que entra na v1 e o que vira backlog. Tem voto final em escopo. | Seção "Escopo e Não-Escopo" da spec |
| 3. Reconstrução | Valida que as histórias de usuário ainda refletem o negócio conforme o código sai. Desbloqueia dúvidas funcionais. | Critérios de aceitação funcionais por feature |
| 4. Evolução com Agent | Redige as duas issues que o Agent vai consumir. Valida se o PR entregue resolve a necessidade de negócio. | Duas issues bem escritas no `.github/ISSUE_TEMPLATE/` |

## Ferramentas e primitives

- **Copilot Chat** para refinar histórias de usuário e critérios de aceitação.
- **Specky** no Estágio 2: a fase de Vision e Requirements é terreno natural do PO.
- **Cowork** se precisar redigir briefings executivos ou notas de decisão.
- **Templates** do repositório `25-personas-primitives` - prompts prontos para escrita de histórias, cortes de escopo e comunicação de riscos.

## Cheat sheets que você usa

- `cheat-sheets/copilot-3-modes.md` - para saber quando é Chat (a maior parte do seu dia), quando é Edits (raro para você), quando é Agent (Estágio 4).
- `cheat-sheets/specky-workflow.md` - especialmente as fases 1 (Vision) e 2 (Requirements).

## Como se sai bem

- Diz "isto fica fora da v1" três vezes ao dia sem pestanejar.
- Conecta cada ADR a um impacto concreto no beneficiário ou no operador.
- Protege o foco do time quando alguém sugerir refatorar algo que já funciona.
- Escreve as duas issues do Estágio 4 com contexto bom o suficiente para o Agent trabalhar sozinho.

## Como se perde

- Fica preso em detalhes técnicos que não são seus.
- Deixa o time reconstruir o legado programa por programa.
- Escreve issues vagas e o Agent produz lixo.
- Não corta escopo e o Estágio 3 termina incompleto.

## Se você acumulou duas personas

- PO + **Requirements Engineer** é a combinação natural. Você escreve as regras; eu estruturo e testo.
- PO + **Tech Writer** também funciona para times com perfil mais comunicacional.

## 3 Prompts Exemplares

1. **(Chat)** "Analise o programa CALCBENF.NSN do SIFAP legado e liste as 5 regras de negocio com maior impacto no beneficiario. Para cada uma, diga se deve ser migrada, descartada ou evoluida."
2. **(Chat)** "Revise estas 3 user stories e reescreva como issues GitHub no formato que o Copilot Agent consegue consumir. Inclua contexto, requisitos funcionais como checklist, e acceptance criteria."
3. **(Chat)** "O time quer implementar 8 features em 3 horas. Baseado na complexidade, ajude-me a cortar para as 3 mais criticas para o ciclo mensal de pagamento."

## Se Você Ficar Travado (Defaults de Emergência)

- **Travou na priorização?** Aplique regra: "Se afeta o ciclo mensal de pagamento → v1. Se não → backlog."
- **Não sabe escrever issue?** Copie o template de `04-evolucao/GUIDE.md` e adapte.
- **Time quer tudo no escopo?** Diga "temos 3 horas de implementação; escolham 3 features."
- **Dúvida de negócio sem resposta?** Documente como premissa e siga.

## Dependências - Quem Depende de Você

| Persona | Relação | Artefato |
|---------|---------|----------|
| Requirements Engineer | Depende de VOCÊ | Priorização de regras para converter em EARS |
| Technical Lead | Depende de VOCÊ | Escopo definido para calibrar Estágio 3 |
| Developer | Depende de VOCÊ (E4) | Issues bem escritas para Agent |
| Enterprise Architect | VOCÊ depende dele | Mapa de integrações para decisões de escopo |

## Como Você É Avaliado

- **Rubrica A2 (Coerência da Spec):** escopo claro, não-escopo documentado.
- **Rubrica A7 (Agent Experience):** issues com contexto suficiente para Agent produzir PR útil.
- Avaliada indiretamente em **A6 (Colaboração):** PO que protege foco do time.

- Paula
