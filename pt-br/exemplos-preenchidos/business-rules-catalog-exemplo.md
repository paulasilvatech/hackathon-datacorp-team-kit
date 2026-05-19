---
title: "Catálogo de Regras de Negócio — Exemplo Preenchido"
description: "Exemplo de como o business-rules-catalog.md do Estágio 1 fica quando bem feito. Use como referência de profundidade — não copie literalmente."
locale: "pt-br"
canonical_path: "pt-br/exemplos-preenchidos/business-rules-catalog-exemplo.md"
author: "Paula Silva, Americas Software GBB, Microsoft"
date: "2026-05-19"
version: "1.0.0"
status: "approved"
tags: ["exemplo", "business-rules", "estagio-1", "pt-br"]
---

<!-- markdownlint-disable MD013 MD025 MD026 MD028 MD029 MD034 MD040 MD051 MD060 -->

# Catálogo de Regras de Negócio — Exemplo Preenchido

> **⚠️ Este é um EXEMPLO** para você ver como fica pronto. **O seu** `01-arqueologia/business-rules-catalog.md` deve ter no mínimo **15 regras** ao final do Estágio 1.

## Metadados

- **Time:** Time Beta (exemplo)
- **Data:** 19/05/2026
- **Programas cobertos:** CALCDSCT, CALCBENF, VALELEG, CADBENEF, BATCHPGT
- **Total de regras catalogadas:** 18 (5 mostradas abaixo)

---

## Como ler o catálogo

| Coluna | O que vai aqui |
|---|---|
| **ID** | `BR-NNN` em sequência |
| **Regra** | Uma frase. Sem ambiguidade. |
| **Programa Fonte** | `caminho/arquivo.NSN#L<início>-L<fim>` — **obrigatório** |
| **Campos DDM** | Quais campos do banco a regra usa |
| **Risco** | CRÍTICO / ALTO / MÉDIO / BAIXO |
| **Notas** | Contexto histórico, exceções, evidência adicional |

---

## Catálogo

### BR-001 · Teto de descontos não judiciais

| Campo | Valor |
|---|---|
| **Regra** | O total de descontos não judiciais (tipo ≠ J) não pode exceder 30% do valor bruto do pagamento. Descontos judiciais (tipo J) não têm teto. |
| **Programa Fonte** | `legado-natural/natural-programs/CALCDSCT.NSN#L142-L148` |
| **Campos DDM** | `PAGAMENTO.VLR-BRUTO`, `PAGAMENTO.VLR-DESCONTO`, `BENEFICIARIO.DESCONTOS.TIPO-DSCT` |
| **Risco** | 🔴 CRÍTICO |
| **Notas** | Adicionado em 12/04/2007 (MARCIA HELENA) para tratar pensão alimentícia. Sem isso o sistema viola decisões judiciais. |

### BR-002 · Validação de CPF módulo 11

| Campo | Valor |
|---|---|
| **Regra** | Todo CPF cadastrado deve passar na validação de dígito verificador módulo 11 da Receita Federal. |
| **Programa Fonte** | `legado-natural/natural-programs/CADBENEF.NSN#L78-L112` |
| **Campos DDM** | `BENEFICIARIO.CPF` |
| **Risco** | 🔴 CRÍTICO |
| **Notas** | Implementação no legado é própria; não usa biblioteca externa. CPFs como `111.111.111-11` precisam ser rejeitados. |

### BR-003 · Faixas progressivas de contribuição social

| Campo | Valor |
|---|---|
| **Regra** | Contribuição social é progressiva por faixa: até R$ 500 = 3%, até R$ 1.000 = 5%, até R$ 2.000 = 7,5%, acima de R$ 2.000 = 10%. |
| **Programa Fonte** | `legado-natural/natural-programs/CALCDSCT.NSN#L56-L72` |
| **Campos DDM** | `PAGAMENTO.VLR-BRUTO` |
| **Risco** | 🔴 CRÍTICO |
| **Notas** | Tabela hardcoded em `#FAIXA-CONTRIB(1..4)`. Alterada em 30/09/2015 (ANDERSON LIMA). Valores tributários — qualquer erro vira passivo. |

### BR-004 · Bloqueio de status INACTIVE → ACTIVE direto

| Campo | Valor |
|---|---|
| **Regra** | Beneficiário com status `INACTIVE` não pode voltar diretamente para `ACTIVE` — precisa passar por revisão (status `PENDING_REVIEW`). |
| **Programa Fonte** | `legado-natural/natural-programs/VALELEG.NSN#L201-L218` |
| **Campos DDM** | `BENEFICIARIO.STATUS` |
| **Risco** | 🟡 ALTO |
| **Notas** | Fraude conhecida: até 1999 era possível reativar direto. Acórdão TCU 2034/2002 exige revisão antes da reativação. |

### BR-005 · Geração de ciclo de pagamento mensal

| Campo | Valor |
|---|---|
| **Regra** | O ciclo de pagamento mensal é gerado no 5º dia útil do mês corrente, processando todos os beneficiários com status `ACTIVE` na data de corte (último dia do mês anterior). |
| **Programa Fonte** | `legado-natural/natural-programs/BATCHPGT.NSN#L88-L142` |
| **Campos DDM** | `BENEFICIARIO.STATUS`, `PAGAMENTO.COMPETENCIA`, `PAGAMENTO.DATA-EMISSAO` |
| **Risco** | 🔴 CRÍTICO |
| **Notas** | A data de corte é o que define **quem entra no ciclo**. Beneficiário que ficou ACTIVE no dia 1º do mês corrente NÃO entra. Foi causa de duas auditorias em 2018. |

---

## Estatísticas (Exemplo)

| Métrica | Valor |
|---|---|
| Total de regras | 18 |
| 🔴 Críticas | 8 |
| 🟡 Altas | 6 |
| 🟢 Médias/baixas | 4 |
| Com `Programa Fonte` preenchido | 18 (100%) ✅ |
| Programas cobertos | 5 de 15 (33%) |
| Próximo bloco | CALCBENF, CALCCORR, RELPGT |

> **Meta do Estágio 1:** chegar a ≥15 regras com 100% de rastreabilidade. Este exemplo está no caminho.

---

## O que torna este catálogo "bom"

- ✅ **Toda linha tem `Programa Fonte` com `#L<inicio>-L<fim>`** — sem isso, o CI rejeita.
- ✅ **Notas históricas presentes** — qual auditor exigiu, qual data, qual mudança.
- ✅ **Campos DDM listados** — facilita o trabalho do DBA no Estágio 3.
- ✅ **Risco classificado** — Estágio 2 prioriza pelos CRÍTICOS.
- ❌ Sem genericismos do tipo *"o sistema deve estar correto"*. Toda regra é específica e testável.

---

## Navegação

| Anterior | Início | Próximo |
| --- | --- | --- |
| [Exemplos](README.md) | [Kit PT-BR](../README.md) | [SPECIFICATION (exemplo)](SPECIFICATION-exemplo.md) |
