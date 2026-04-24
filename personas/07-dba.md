---
title: "Ficha da Persona - DBA"
description: "O que o DBA faz dentro do time de 10 durante o Dia 2 do Hackathon SERPRO 2026."
author: "Paula Silva, Americas Software GBB, Microsoft"
date: "2026-04-18"
version: "1.0.0"
persona_id: "07"
tags: ["persona", "dba", "hackathon", "SERPRO", "PostgreSQL"]
---

# Persona - DBA

## Quem é essa pessoa

Dono dos dados. No SIFAP legado, isso significa entender os 4 DDMs Adabas com MU e PE, com denormalização pragmática, com índices ancestrais. No SIFAP 2.0 significa desenhar um esquema PostgreSQL 16 que preserva a integridade lógica do negócio sem herdar as cicatrizes do Adabas.

## Missão no hackathon

Traduzir o modelo Adabas para um esquema relacional que funciona. Garantir migrations idempotentes (Flyway). Desenhar índices e particionamento para que o ciclo mensal caiba em 2h. Proteger a rastreabilidade (audit store).

## Seu papel no framework Agentic Legacy Modernization

Este hackathon aplica o framework **Agentic Legacy Modernization** - uma abordagem de modernizacao de sistemas legado usando agentes de IA especializados em cada fase. O pipeline completo esta descrito no `01-blueprint/HACKATHON-BLUEPRINT.md`. Sua persona mapeia para o pipeline assim:

- **Agentes relevantes**: Analysis Agent (E1), Translation Agent (E3)
- **Fase do framework**: Assessment → Translation (data layer)
- **Seu papel no pipeline**: Traduz DDMs Adabas → schema PostgreSQL preservando integridade

## Onde você aparece por estágio

| Estágio | Você faz isto | Entregável que depende de você |
|---|---|---|
| 1. Arqueologia | Lê os 4 DDMs. Mapeia MU/PE para entidades relacionais candidatas. Identifica campos-chave. | Mapa DDM → entidade relacional |
| 2. Spec Greenfield | Desenha o modelo de dados lógico. Escreve a ADR do PostgreSQL (ADR 2 da referência). | Modelo de dados + ADR 002 |
| 3. Reconstrução | Escreve migrations Flyway. Define índices. Popula dados de teste. Responde dúvidas de JPA/Hibernate. | Esquema PostgreSQL + seed |
| 4. Evolução com Agent | Revisa se o PR do Agent toca no schema de maneira segura (nova migration, não alteração retroativa). | Integridade de schema |

## Ferramentas e primitives

- **Copilot Chat** para traduzir DDM Adabas → SQL PostgreSQL.
- **Copilot Edits** para gerar migrations em lote.
- **MCP do PostgreSQL** (se disponível no devcontainer) para introspection e queries.
- **Specky** - fase 4 consome seu modelo de dados.

## Cheat sheets que você usa

- `cheat-sheets/specky-workflow.md` - como declarar modelo de dados que Specky valida na fase 4.
- `cheat-sheets/model-routing.md` - Sonnet 4.6 é suficiente para a maior parte do seu trabalho.

## Como se sai bem

- Todas as migrations são reversíveis ou substituídas por nova migration em vez de alteradas.
- Você descobre (e documenta) qual MU do Adabas precisa virar tabela relacionada, não coluna `JSONB`.
- Seus índices cobrem as queries críticas do ciclo mensal.
- O audit store é append-only de verdade - sem DELETE em nenhum lugar.

## Como se perde

- Denormaliza por costume Adabas.
- Esquece de indexar e a query do ciclo é lenta.
- Usa `JSONB` para tudo porque "é flexível".
- Deixa migration não-idempotente e o devcontainer do colega quebra.

## Se você acumulou duas personas

- **DBA + Developer** é comum; você escreve suas migrations e algumas queries.
- **DBA + DevOps Engineer** se o time tem perfil mais ops - você cuida do PostgreSQL e do Terraform que o provisiona.

## 3 Prompts Exemplares

1. **(Chat)** "Leia o DDM BENEFICIARIO.ddm do Adabas e traduza para schema PostgreSQL 16. O grupo PE (periodic) de dependentes deve virar tabela separada ou JSONB? Justifique."
2. **(Edits)** "Crie uma migration Flyway V5__add_indexes.sql com indices para: busca por CPF, listagem de pagamentos por ciclo+status, auditoria por tipo+data."
3. **(Chat)** "Revise este schema e identifique: campos sem NOT NULL que precisam, foreign keys faltando, e indices para o ciclo mensal de 3.8M pagamentos."

## Se Você Ficar Travado (Defaults de Emergência)

- Não sabe formato DDM? Abra `02-cenario-sifap-legado/adabas-ddms/BENEFICIARIO.ddm` - tem comentários explicando cada campo.
- Migration quebrou? NUNCA edite migration existente. Crie nova: `V5__fix_xxx.sql`.
- Qual índice criar? Regra: "Se aparece em WHERE ou JOIN e a tabela tem >100K linhas, crie índice."
- PostgreSQL offline? Verifique se Docker está rodando: `docker ps | grep postgres`.

## Dependências - Quem Depende de Você

| Persona | Relação | Artefato |
|---------|---------|----------|
| Software Architect | VOCÊ depende dele | Fronteiras de contexto para model |
| Developer | Depende de VOCÊ | Migrations prontas para código JPA |
| DevOps Engineer | Depende de VOCÊ | Schema estável para Terraform |
| QA Engineer | Depende de VOCÊ | Dados de teste (seed) |

## Como Você É Avaliado

- Rubrica A3 (Integridade Técnica): migrations idempotentes, schema consistente com entities JPA
- Rubrica A1 (Arqueologia): mapa DDM→entidade relacional documentado
- Critério: "Audit store é append-only. Nenhum DELETE no schema de auditoria."

- Paula
