---
title: "Ficha da Persona - DevOps Engineer"
description: "O que o DevOps Engineer faz dentro do time de 10 durante o Dia 2 do Hackathon SERPRO 2026."
author: "Paula Silva, Americas Software GBB, Microsoft"
date: "2026-04-18"
version: "1.0.0"
persona_id: "09"
tags: ["persona", "devops-engineer", "hackathon", "SERPRO", "terraform", "github-actions"]
---

# Persona - DevOps Engineer

## Quem é essa pessoa

Dono do caminho do código até algo que roda. No hackathon, você é quem garante que o `docker compose up` funciona em qualquer máquina do time, que o CI verifica o que importa, e que o Terraform descreve a topologia-alvo no Azure mesmo que não seja aplicado no dia.

## Missão no hackathon

Pipeline verde. Build reprodutível. Deploy descrito em código. Observabilidade mínima funcional (health check, logs estruturados).

## Seu papel no framework Agentic Legacy Modernization

Este hackathon aplica o framework **Agentic Legacy Modernization** - uma abordagem de modernizacao de sistemas legado usando agentes de IA especializados em cada fase. O pipeline completo esta descrito no `01-blueprint/HACKATHON-BLUEPRINT.md`. Sua persona mapeia para o pipeline assim:

- **Agentes relevantes**: Deployment Agent (E4), Security Agent (E3)
- **Fase do framework**: Coexistence and Traffic Migration
- **Seu papel no pipeline**: Provisiona infraestrutura e configura pipeline CI/CD para deploy continuo

## Onde você aparece por estágio

| Estágio | Você faz isto | Entregável que depende de você |
|---|---|---|
| 1. Arqueologia | Estabiliza o devcontainer se algo estiver quebrando. Prepara docker-compose do PostgreSQL e ferramentas auxiliares. | Devcontainer e compose estáveis |
| 2. Spec Greenfield | Escreve a ADR da estratégia de deploy (ADR 5 da referência) e participa do desenho de infra. | ADR 005 + rascunho Terraform |
| 3. Reconstrução | Mantém GitHub Actions de build e testes. Publica imagem Docker. Deixa Terraform descrito. | Pipeline verde + Terraform `plan` válido |
| 4. Evolução com Agent | Se o PR do Agent mexer em pipeline ou infra, você é a pessoa que valida. | Pipeline ainda verde pós-Agent |

## Ferramentas e primitives

- **Copilot Chat** para gerar workflows GitHub Actions.
- **Copilot Edits** para Terraform em lote.
- **MCP do Azure / Terraform** se estiverem habilitados no devcontainer.
- **Specky** - fase 10 (Deployment) passa por você.
- **Dev Containers** spec - é você quem entende o `devcontainer.json`.

## Cheat sheets que você usa

- `cheat-sheets/specky-workflow.md` - fase 10.
- `cheat-sheets/copilot-3-modes.md` - você usa bastante Agent para cadeias longas de CI.

## Como se sai bem

- `docker compose up -d` sobe aplicação + banco em menos de 60s.
- Pipeline do `main` faz lint + teste + build de imagem.
- Terraform `plan` roda sem erro mesmo que não aplique.
- Logs estruturados (JSON) e endpoint `/actuator/health` já funcionam no Estágio 3.

## Como se perde

- Deixa devcontainer instável e o time perde 1h no início.
- CI que só roda teste unitário (sem build de imagem, sem lint).
- Terraform com 500 linhas e nenhuma saída que faz sentido.
- Segredo de verdade no `.env` versionado.

## Se você acumulou duas personas

- **DevOps + DBA** - você cuida do Postgres + provisionamento.
- **DevOps + Tech Writer** - no Estágio 4, você documenta o runbook enquanto monitora o Agent.

## 3 Prompts Exemplares

1. **(Chat)** "Crie um workflow GitHub Actions .github/workflows/ci.yml que: roda no push, configura Java 21 com cache Maven, roda testes, e builda imagem Docker."
2. **(Edits)** "Otimize o Dockerfile do backend: adicione cache de dependencias Maven, reduza imagem final com Alpine, e adicione health check."
3. **(Chat)** "O `docker compose up` leva 3 minutos para iniciar. Analise os Dockerfiles e docker-compose.yml e proponha 3 otimizacoes."

## Se Você Ficar Travado (Defaults de Emergência)

- Docker compose não sobe? Checklist: (1) Docker Desktop rodando? (2) Portas 5432/8080/3000 livres? (3) `docker compose down && docker compose up -d` (4) `docker compose logs` para ver erro.
- CI falha? Olhe os logs do GitHub Actions. Erro mais comum: versão Java errada ou cache miss.
- Terraform plan falha? Verifique: (1) `terraform init` rodou? (2) Provider version compatível? (3) Variáveis obrigatórias preenchidas?
- Não sabe GitHub Actions? Copie o workflow em `.github/workflows/build.yml` e adapte.

## Dependências - Quem Depende de Você

| Persona | Relação | Artefato |
|---------|---------|----------|
| Technical Lead | VOCÊ depende dele | Build estável para pipeline |
| Enterprise Architect | VOCÊ depende dele | Topologia para Terraform |
| Developer | Depende de VOCÊ | Devcontainer funcionando, CI verde |
| DBA | Depende de VOCÊ (infra) | PostgreSQL provisionado |
| QA Engineer | Depende de VOCÊ | Pipeline para rodar testes |

## Como Você É Avaliado

- Rubrica A3 (Integridade Técnica): `docker compose up` funciona, CI verde
- Rubrica A4 (Copilot): uso de Agent para pipeline complexo
- Critério: "Build reprodutível. Qualquer máquina do time roda o compose em menos de 60s."

- Paula
