---
title: "Scripts Auxiliares"
description: "Scripts de bootstrap e verificação de qualidade para o repositório da equipe"
author: "Paula Silva, Americas Software GBB, Microsoft"
date: "2026-04-29"
version: "1.0.0"
status: "approved"
tags: ["scripts", "bootstrap", "ci", "workshop"]
---

<!-- markdownlint-disable MD013 MD025 MD026 MD028 MD029 MD034 MD040 MD051 MD060 -->

# Scripts

| Script                 | O que ele faz                                                                                                           |
| ---------------------- | ----------------------------------------------------------------------------------------------------------------------- |
| [`setup.sh`](setup.sh) | Faz o bootstrap do repositório da equipe — verifica pré-requisitos, clona materiais de referência, inicializa `specs/` |
| [`check.sh`](check.sh) | Executa todos os gates de CI localmente (testes do backend, lint/teste do frontend, Terraform fmt)                      |

## Uso

```bash
chmod +x scripts/*.sh

# Configuração inicial
./scripts/setup.sh

# Antes de cada push
./scripts/check.sh
```

## Observações

- `setup.sh` clona os materiais de referência em `reference/` e cria symlinks para `prototype/` e `infra/`. A pasta `legado-natural/` já vem incluída no kit. Sobrescreva o repositório de origem com `WORKSHOP_REPO=...`.
- Os symlinks estão no gitignore — eles servem apenas para conveniência local.
- `check.sh` ignora qualquer verificação cuja pasta ainda não exista (assim ele funciona durante os estágios iniciais).
---

### Continuar a leitura

<table width="100%">
<tr>
<td width="50%" valign="top" align="left">
<sub><strong>← ANTERIOR</strong></sub><br/>
<a href="../README.md"><strong>Kit PT-BR</strong></a><br/>
<sub>Hub deste folder: comece aqui se nunca abriu o kit.</sub>
</td>
<td width="50%" valign="top" align="right">
<sub><strong>PRÓXIMO →</strong></sub><br/>
<a href="../SETUP.md"><strong>SETUP</strong></a><br/>
<sub>Setup do laptop: Git, VS Code, Copilot, Spec-Kit, branch protection.</sub>
</td>
</tr>
</table>

<sub>↑ <a href="../README.md">Voltar ao Kit PT-BR</a></sub>
