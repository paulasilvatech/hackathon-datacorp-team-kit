---
title: "Ficha da Persona - Technical Lead"
description: "O que o Technical Lead faz dentro do time de 10 durante o Dia 2 do Hackathon SERPRO 2026."
author: "Paula Silva, Americas Software GBB, Microsoft"
date: "2026-04-18"
version: "1.0.0"
persona_id: "05"
tags: ["persona", "technical-lead", "hackathon", "SERPRO"]
---

# Persona - Technical Lead

## Quem é essa pessoa

O elo entre arquitetura e código do dia a dia. Decide padrões de implementação (convenções de código, estilo de testes, estrutura de módulos), destrava o time quando alguém fica preso em detalhe técnico, e é o responsável por garantir que no fim do Estágio 3 a aplicação de fato sobe com `docker compose up`.

## Missão no hackathon

Manter velocidade de execução no Estágio 3. Escolher batalhas técnicas que valem a pena. Destravar rapidamente. Revisar PRs com critério mas sem obstrução.

## Seu papel no framework Agentic Legacy Modernization

Este hackathon aplica o framework **Agentic Legacy Modernization** - uma abordagem de modernizacao de sistemas legado usando agentes de IA especializados em cada fase. O pipeline completo esta descrito no `01-blueprint/HACKATHON-BLUEPRINT.md`. Sua persona mapeia para o pipeline assim:

- **Agentes relevantes**: Review Agent (E3), Test Gen Agent (E3)
- **Fase do framework**: Translation and Test Generation
- **Seu papel no pipeline**: Garante qualidade da traducao e coordena implementacao paralela

## Onde você aparece por estágio

| Estágio | Você faz isto | Entregável que depende de você |
|---|---|---|
| 1. Arqueologia | Participa da análise do legado priorizando programas críticos. Estima complexidade. | Priorização baseada em esforço |
| 2. Spec Greenfield | Valida que a spec é realista nas 3h do Estágio 3. Sinaliza "isso não cabe". | Calibração de escopo |
| 3. Reconstrução | Destrava. Decide padrões (estilo de testes, transações, tratamento de erro). Revê todos os PRs. | Aplicação rodando end-to-end |
| 4. Evolução com Agent | Revisa o PR do Agent linha a linha antes do merge. | PR em qualidade de produção |

## Ferramentas e primitives

- **Copilot Edits** para refatoração em lote.
- **Copilot Chat** como par para decisões de design local.
- **Specky** - apoio nas fases 5 (Implementation Plan) e 6 (Task Breakdown).
- **MCP do Git** para revisão de PR.

## Cheat sheets que você usa

- Todos os três cheat sheets. Você é o mais versátil.
- `cheat-sheets/copilot-3-modes.md` em especial - você alterna entre os três o tempo todo.

## Como se sai bem

- Responde dúvida técnica em até 5 minutos. Não deixa ninguém trancado.
- Faz review que avança o PR, não review que trava.
- Escolhe dois padrões-chave no início do Estágio 3 e defende sem negociar (ex: "tudo transacional via `@Transactional` na camada de serviço").
- Mantém `main` verde o tempo todo.

## Como se perde

- Tenta escrever metade do código sozinho.
- Review bloqueante por detalhes estéticos.
- Muda padrão no meio do Estágio 3.
- Não detecta gargalo e o `docker compose up` não sobe no fim.

## Se você acumulou duas personas

- **TL + Developer** é o par natural - você lidera e continua escrevendo código.
- **TL + Software Architect** se o time tem quem cubra dev.
- Evite **TL + QA** no mesmo cérebro: o papel de quem pergunta "cobriu teste?" fica mais forte em pessoa diferente.

## 3 Prompts Exemplares

1. **(Chat)** "Revise este PR: verifica se segue as 3 camadas (domain/application/infrastructure), se o teste cobre happy path + erro, e se ha import cruzando bounded context."
2. **(Chat)** "Temos 3 devs e 3 horas. Features pendentes: [liste]. Crie um plano distribuindo por dev considerando dependencias e complexidade."
3. **(Chat)** "O `docker compose up` falha com este erro: [cole]. Diagnostique a causa raiz e proponha fix."

## Se Você Ficar Travado (Defaults de Emergência)

- **Docker não sobe?** Verifique: porta 5432 ocupada? `docker ps` mostra containers antigos? `docker compose down && docker compose up -d`.
- **Time lento?** Pare, redistribua: "Dev A faz endpoint, Dev B faz migration, QA faz teste. Merge em 45 min."
- **PR conflitante?** `git pull --rebase` e resolve. Não deixe branch divergir mais que 2h.
- **Não sabe decidir padrão?** Escolha o que o protótipo já usa. Copie o estilo de `BeneficiaryService.java`.

## Dependências - Quem Depende de Você

| Persona | Relação | Artefato |
|---------|---------|----------|
| Software Architect | VOCÊ depende dele | Estrutura de pacotes definida |
| Product Owner | VOCÊ depende dele | Escopo calibrado |
| Developer | Depende de VOCÊ | Padrões e review |
| QA Engineer | Depende de VOCÊ | Pipeline verde para rodar testes |
| DevOps Engineer | Depende de VOCÊ | Build estável para pipeline |

## Como Você É Avaliado

- **Rubrica A3 (Integridade Técnica):** aplicação sobe com `docker compose up`.
- **Rubrica A6 (Colaboração):** ninguém travado por mais de 20 minutos.
- Critério: "`main` verde o tempo todo, PRs revisados em menos de 15 minutos."

- Paula
