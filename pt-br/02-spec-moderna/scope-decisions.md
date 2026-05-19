---
title: "Decisões de Escopo — SIFAP 2.0"
description: "Modelo para registrar o que migra, descarta ou evolui no SIFAP 2.0. Decisão liderada pelo Par 1 (Product Owner)."
locale: "pt-br"
canonical_path: "06-kit-repositorio-times/02-spec-moderna/scope-decisions.md"
author: "Paula Silva, Americas Software GBB, Microsoft"
date: "2026-05-18"
version: "1.0.0"
status: "template"
tags: ["estagio-2", "escopo", "template", "pt-br"]
---

<!-- markdownlint-disable MD013 MD025 MD026 MD028 MD029 MD034 MD040 MD051 MD060 -->

# Decisões de Escopo — SIFAP 2.0

> Para cada funcionalidade encontrada no Estágio 1, decida: **Migrar**, **Descartar** ou **Evoluir**.
>
> - **Migrar**: trazer para o SIFAP 2.0 como está (mesma lógica, nova tecnologia)
> - **Descartar**: não trazer — funcionalidade obsoleta ou desnecessária
> - **Evoluir**: trazer E melhorar (nova UX, novo fluxo, nova capacidade)

**Time**: [Nome do Time]
**Data**: 19/05/2026
**Edição**:
**Par 1 (Product Owner) responsável**: [Nome]

## Por que isso importa

O escopo é o que protege o time de chegar às 17h00 com 12 features pela metade. Se o Par 1 não cortar, o Estágio 3 não fecha. **Decisão difícil é tomada aqui, não no Estágio 3.**

## Como decidir

Pergunte de cada funcionalidade:

1. **Afeta o ciclo mensal de pagamento?** Sim → Migrar. Não → considere descartar.
2. **Tem uso documentado nos últimos 12 meses?** Não → descartar.
3. **Faz parte de um relatório regulatório obrigatório (TCU, CGU, BB)?** Sim → Migrar como está.
4. **Tem uma versão moderna mais barata de implementar?** Sim → Evoluir.

---

## Decisões por Funcionalidade

| #   | Funcionalidade            | Decisão                      | Justificativa | Regra de Negócio (BR-XXX) | Prioridade           |
| --- | ------------------------- | ---------------------------- | ------------- | ------------------------- | -------------------- |
| 1   | Cadastro de Beneficiários | Migrar / Descartar / Evoluir |               |                           | Alta / Média / Baixa |
| 2   | Consulta de Beneficiários |                              |               |                           |                      |
| 3   | Registro de Pagamentos    |                              |               |                           |                      |
| 4   | Processamento Batch       |                              |               |                           |                      |
| 5   | Cálculo de Benefícios     |                              |               |                           |                      |
| 6   | Validação de CPF          |                              |               |                           |                      |
| 7   | Relatórios                |                              |               |                           |                      |
| 8   | Auditoria                 |                              |               |                           |                      |
| 9   | Gestão de Usuários        |                              |               |                           |                      |
| 10  |                           |                              |               |                           |                      |
| 11  |                           |                              |               |                           |                      |
| 12  |                           |                              |               |                           |                      |

> Adicione linhas para cada funcionalidade identificada no `discovery-report.md` do Estágio 1.

---

## Funcionalidades Novas (não existem no legado)

> Liste funcionalidades que o SIFAP 2.0 deveria ter e que não existem no sistema legado. Cada uma vira REQ-ID com `source_legacy: [GREENFIELD] <justificativa>`.

| #   | Funcionalidade Nova | Justificativa | Prioridade | Complexidade |
| --- | ------------------- | ------------- | ---------- | ------------ |
| N1  |                     |               |            |              |
| N2  |                     |               |            |              |
| N3  |                     |               |            |              |

---

## Resumo de Escopo

| Decisão   | Quantidade | Percentual |
| --------- | ---------- | ---------- |
| Migrar    |            |            |
| Descartar |            |            |
| Evoluir   |            |            |
| **Total** |            | 100%       |

## Riscos de Escopo

> Liste os riscos das decisões tomadas:

| Risco | Probabilidade        | Impacto              | Mitigação |
| ----- | -------------------- | -------------------- | --------- |
|       | Alta / Média / Baixa | Alto / Médio / Baixo |           |

## Aprovação

- [ ] Par 1 (Product Owner) aprovou as decisões de escopo
- [ ] Par 2 (Enterprise Architect) validou a viabilidade técnica
- [ ] Par 3 (Technical Lead) confirmou que cabe nas 3 horas do Estágio 3
- [ ] Time concordou com as prioridades

> **Aprovação obrigatória na Passagem #2** (~16:00). Sem ela, o Estágio 3 não começa.

— Paula
