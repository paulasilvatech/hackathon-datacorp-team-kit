---
title: "Runbook — Repositório da Equipe SIFAP 2.0"
description: "Como executar o sistema localmente, em CI e no Azure"
author: "DevOps Engineer (time)"
date: "2026-04-29"
version: "1.0.0"
status: "draft"
tags: ["runbook", "operations", "devops", "deploy"]
---

<!-- markdownlint-disable MD013 MD025 MD026 MD028 MD029 MD034 MD040 MD051 MD060 -->

# Runbook

> O que fazer quando algo roda (ou não roda). O DevOps Engineer é responsável por este arquivo.

## Local — primeira vez

```bash
./scripts/setup.sh # checks tools, clones reference, sets up symlinks
docker compose up -d # spins up Postgres + backend + frontend
```

Depois:

- Backend health: <http://localhost:8080/actuator/health>
- Swagger UI: <http://localhost:8080/swagger-ui.html>
- Frontend: <http://localhost:3001>

As credenciais padrão estão documentadas em `prototype/README.md`.

## Local — diariamente

```bash
docker compose up -d # if it's down
./scripts/check.sh # before pushing
git status # never commit symlinks (legacy/, prototype/, infra/)
```

## CI

Acionado automaticamente em push para `main`, `develop`, `spec/**`, `impl/**`.

| Workflow           | O que faz                                                                  | Quando                            |
| ------------------ | -------------------------------------------------------------------------- | --------------------------------- |
| `ci.yml`           | Backend `mvn verify`, frontend lint+test+typecheck, Terraform fmt+validate | Todo push e PR                    |
| `spec-quality.yml` | markdownlint + rastreabilidade de REQ-ID                                   | Quando `**.md` ou `specs/` mudam |

Verifique runs com falha na aba Actions. Corrija localmente com `./scripts/check.sh`.

## Azure — Estágio 4

O Estágio 4 é quando a equipe aplica Terraform em uma subscription sandbox fornecida pelas pessoas facilitadoras.

```bash
cd infra
terraform init
terraform plan -var-file=envs/dev/terraform.tfvars
terraform apply -var-file=envs/dev/terraform.tfvars
```

> Cada equipe tem uma quota de subscription única. Marque todo recurso com `team=team-XX` ou seu apply falhará.

## Problemas comuns

| Sintoma                                   | Causa provável                     | Correção                                             |
| ----------------------------------------- | ---------------------------------- | ---------------------------------------------------- |
| `docker compose up` trava                 | Porta 5432 / 8080 / 3000 já em uso | `lsof -i :5432` e encerre o processo                 |
| `mvn verify` falha em Testcontainers      | Docker não está em execução        | Inicie o Docker Desktop                              |
| `pnpm test` falha em snapshots            | Componente mudou intencionalmente  | `pnpm test -- -u` para atualizar                     |
| `terraform apply` rejeitado               | Tag `team=` ausente                | Adicione a tag ao recurso com falha                  |
| GitHub Actions não consegue acessar Azure | OIDC subject claim mismatch        | Rode novamente `az ad sp create-for-rbac` por equipe |

## Quando escalar para uma pessoa facilitadora

- Build ainda falhando apos 20 minutos de debug.
- A subscription Azure parece suspensa.
- Qualquer coisa irreversível (por exemplo, `terraform destroy` executado por engano).

Use o formato de escalonamento de 3 linhas de [TEAM-FLOW.md §4](../TEAM-FLOW.md).
