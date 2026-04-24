---
title: "Ficha da Persona - Software Architect"
description: "O que o Software Architect faz dentro do time de 10 durante o Dia 2 do Hackathon SERPRO 2026."
author: "Paula Silva, Americas Software GBB, Microsoft"
date: "2026-04-18"
version: "1.0.0"
persona_id: "04"
tags: ["persona", "software-architect", "hackathon", "SERPRO"]
---

# Persona - Software Architect

## Quem é essa pessoa

Dono da estrutura interna do sistema. Decide como os módulos se organizam, onde os bounded contexts começam e terminam, que abstrações ficam expostas e quais ficam privadas. É quem mantém o Modular Monolith modular de verdade.

## Missão no hackathon

Produzir o C4 Nível 2 e 3 coerentes com a spec. Definir os bounded contexts do SIFAP 2.0 (Beneficiary, Agreement, Payment, Adjustment, Cycle, Audit) e o padrão de comunicação entre eles. Garantir que o código do Estágio 3 respeita as fronteiras desenhadas.

## Seu papel no framework Agentic Legacy Modernization

Este hackathon aplica o framework **Agentic Legacy Modernization** - uma abordagem de modernizacao de sistemas legado usando agentes de IA especializados em cada fase. O pipeline completo esta descrito no `01-blueprint/HACKATHON-BLUEPRINT.md`. Sua persona mapeia para o pipeline assim:

- **Agentes relevantes**: Analysis Agent (E2), Review Agent (E3)
- **Fase do framework**: Application Carving → Translation
- **Seu papel no pipeline**: Define bounded contexts e garante Modular Monolith coerente

## Onde você aparece por estágio

| Estágio | Você faz isto | Entregável que depende de você |
|---|---|---|
| 1. Arqueologia | Identifica os conceitos recorrentes nos Naturals e começa a propor os bounded contexts candidatos. | Lista inicial de módulos/contextos |
| 2. Spec Greenfield | Desenha o C4 Nível 2 e Nível 3 para pelo menos dois contextos. Escreve a ADR do Modular Monolith. | Diagramas C4 + ADRs 1 e 2 |
| 3. Reconstrução | Estabelece a estrutura inicial do projeto Spring (packages, camadas). Revê PRs que cruzam fronteira de contexto. | `pom.xml` + layout de módulos + revisão de PRs estruturais |
| 4. Evolução com Agent | Valida se o PR do Agent respeita as fronteiras. Rejeita fusões que furam modularidade. | Modularidade preservada |

## Ferramentas e primitives

- **Copilot Edits** para criar esqueleto de módulos em paralelo.
- **Specky** - fase 3 (Context) e fase 4 (Architecture Decisions) são o seu terreno.
- **Mermaid / C4** para diagramas.
- Skills específicas de SA do `25-personas-primitives` - prompts para decisão entre padrões (hexagonal vs camadas, por exemplo).

## Cheat sheets que você usa

- `cheat-sheets/specky-workflow.md` - fases 3 e 4.
- `cheat-sheets/model-routing.md` - Opus 4.6 para decisões; Sonnet 4.6 para edição em lote.

## Como se sai bem

- O layout de pacotes reflete os bounded contexts, não as camadas técnicas.
- Suas ADRs são curtas, específicas e citam o documento 13 seção 5 quando relevante.
- O Modular Monolith permanece monolito em deploy mas modular em código.
- Você refaz fronteiras quando necessário em vez de "pedir perdão depois".

## Como se perde

- Deixa o time organizar por camadas técnicas (controller/service/repository) em vez de contextos.
- Escreve ADR genérica ("vamos usar Spring Boot") que não é decisão real.
- Permite que dois contextos importem classes um do outro diretamente.
- Tenta forçar hexagonal rigoroso onde não há nenhum benefício.

## Se você acumulou duas personas

- **SA + Enterprise Architect** se o time é pequeno (você faz C4 1 e 2/3).
- **SA + Technical Lead** é a acumulação mais produtiva - você desenha e toca o código.

## 3 Prompts Exemplares

1. **(Chat)** "Com base nestes requisitos EARS, proponha os bounded contexts do SIFAP 2.0. Para cada contexto liste: entidades, servicos expostos, e dependencias com outros contextos."
2. **(Edits)** "No projeto Spring Boot, crie a estrutura de pacotes para um novo bounded context 'notification' seguindo o padrao dos existentes (domain/application/infrastructure)."
3. **(Chat)** "Revise este PR e identifique imports que cruzam fronteira de bounded context. Para cada violacao, sugira como isolar."

## Se Você Ficar Travado (Defaults de Emergência)

- **Bounded contexts confusos?** Comece com 4: Beneficiary, Payment, Audit, Admin. É o que o protótipo já usa.
- **Diagrama C4 L2 travou?** Use o exemplo em `02-spec-moderna/GUIDE.md` como ponto de partida.
- **Time organizou por camadas em vez de contextos?** Não refatore agora - documente na ADR e corrija se sobrar tempo.
- **Dúvida se algo é domain ou application?** "Se é regra de negócio pura, é domain. Se orquestra, é application."

## Dependências - Quem Depende de Você

| Persona | Relação | Artefato |
|---------|---------|----------|
| Enterprise Architect | VOCÊ depende dele | C4 L1 para desenhar L2/L3 |
| Developer | Depende de VOCÊ | Estrutura de pacotes para implementar |
| Technical Lead | Depende de VOCÊ | Padrões de módulo para enforcement |
| DBA | Depende de VOCÊ | Fronteiras de contexto para model de dados |

## Como Você É Avaliado

- **Rubrica A2 (Spec):** C4 L2/L3 coerentes com requisitos.
- **Rubrica A3 (Integridade Técnica):** bounded contexts respeitados no código.
- Critério: "Nenhum import cruza fronteira de contexto sem justificativa."

- Paula
