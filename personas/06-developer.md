---
title: "Ficha da Persona - Developer"
description: "O que o Developer faz dentro do time de 10 durante o Dia 2 do Hackathon SERPRO 2026."
author: "Paula Silva, Americas Software GBB, Microsoft"
date: "2026-04-18"
version: "1.0.0"
persona_id: "06"
tags: ["persona", "developer", "hackathon", "SERPRO"]
---

# Persona - Developer

## Quem é essa pessoa

Você escreve o código. Mais do que isso: você é quem usa o Copilot o dia inteiro em todos os três modos e traduz ideias em diff. No Estágio 3 você é o peso pesado da produção.

## Missão no hackathon

Transformar a spec em código que sobe. Usar Copilot com consciência - Chat para entender, Edits para produzir, Agent para delegar. Empurrar diariamente.

## Seu papel no framework Agentic Legacy Modernization

Este hackathon aplica o framework **Agentic Legacy Modernization** - uma abordagem de modernizacao de sistemas legado usando agentes de IA especializados em cada fase. O pipeline completo esta descrito no `01-blueprint/HACKATHON-BLUEPRINT.md`. Sua persona mapeia para o pipeline assim:

- **Agentes relevantes**: Translation Agent (E3), Review Agent (E3)
- **Fase do framework**: Translation and Test Generation
- **Seu papel no pipeline**: Implementa a traducao de Natural → Java guiado pela spec EARS

## Onde você aparece por estágio

| Estágio | Você faz isto | Entregável que depende de você |
|---|---|---|
| 1. Arqueologia | Lê programas Natural com Copilot Chat. Produz resumo legível para o resto do time. | Resumos narrativos dos programas |
| 2. Spec Greenfield | Participa de pair com Requirements Engineer para antecipar problemas de implementação. | Sinais preventivos na spec |
| 3. Reconstrução | Implementa, testa, abre PR, revisa PR, implementa de novo. | Backend + frontend do seu fatiamento |
| 4. Evolução com Agent | Assiste o Agent trabalhar. Intervém quando ele perde o caminho. Finaliza o que ele não terminou. | PR do Agent em forma mergeável |

## Ferramentas e primitives

- **Copilot Chat** - entendimento e discussão de design.
- **Copilot Edits** - sua ferramenta principal no Estágio 3.
- **Copilot Agent** - no Estágio 4, é você quem opera o Agent pelo time ou ao lado do TL.
- **Specky** - consumidor dos artefatos do SA e RE; produz código guiado pela spec.
- **MCP do GitHub** para trabalhar com issues e PRs sem sair do VS Code.

## Cheat sheets que você usa

- `cheat-sheets/copilot-3-modes.md` - é o seu mapa do dia.
- `cheat-sheets/specky-workflow.md` - fases 5 a 10.
- `cheat-sheets/model-routing.md` - Haiku 4.5 para trechos simples, Sonnet 4.6 como padrão, Opus 4.6 para design.

## Como se sai bem

- Usa os três modos do Copilot deliberadamente - não é sempre Chat.
- Commits pequenos e pull requests pequenos.
- Escreve teste ao mesmo tempo que escreve o código.
- Não se apaixona por uma abstração no meio do Estágio 3.

## Como se perde

- Trabalha oito horas em um único branch gigante.
- Usa Agent para tarefa que Edits resolveria em 5 minutos.
- Escreve código sem teste e descobre que nada funciona às 16:30.
- Vai para Opus 4.6 sempre - vai gastar tempo demais esperando.

## Se você acumulou duas personas

- **Developer + Technical Lead** - muito comum.
- **Developer + QA Engineer** - você escreve a feature e os testes, na mesma cabeça.
- **Developer + DevOps Engineer** em time pequeno - você empacota e sobe.

## 3 Prompts Exemplares

1. **(Chat)** "Explique o programa CALCDSCT.NSN do SIFAP legado e identifique a regra de teto de descontos. Depois, me ajude a implementar o equivalente em Java seguindo o padrao do PaymentService existente."
2. **(Edits)** "Selecione BeneficiaryEntity.java, BeneficiaryService.java e BeneficiaryController.java. Adicione um campo 'email' ao beneficiario: entity, service, controller, migration, e teste."
3. **(Agent)** "Implemente a feature descrita nesta Issue: [cole a issue]. Respeite a arquitetura de 3 camadas e inclua testes."

## Se Você Ficar Travado (Defaults de Emergência)

- Código não compila? `mvn test-compile` para ver o erro exato. Geralmente é import faltando.
- Não sabe a estrutura de pacotes? Olhe `beneficiary/` como referência: domain/ → application/ → infrastructure/.
- Copilot gerando código ruim? Mude de Chat para Edits - selecione os arquivos relevantes e descreva a mudança.
- Teste falhando? Leia a mensagem de erro. Se é NPE, provavelmente falta mock. Se é assertion, o valor esperado está errado.

## Dependências - Quem Depende de Você

| Persona | Relação | Artefato |
|---------|---------|----------|
| Software Architect | VOCÊ depende dele | Estrutura de pacotes e bounded contexts |
| Requirements Engineer | VOCÊ depende dele | Requisitos claros para implementar |
| Technical Lead | Depende de VOCÊ | PRs para revisar |
| QA Engineer | Depende de VOCÊ | Código testável |
| DBA | VOCÊ depende dele | Migrations e modelo de dados |

## Como Você É Avaliado

- Rubrica A3 (Integridade Técnica): endpoints funcionais, testes passando
- Rubrica A4 (Uso Consciente do Copilot): alternância deliberada entre Chat, Edits e Agent
- Critério: "Commits pequenos, PRs revisáveis, testes escritos junto com o código"

- Paula
