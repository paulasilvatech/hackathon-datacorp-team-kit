---
title: "Checklist de Exploração do Legado — OBRIGATÓRIO antes do Estágio 2"
description: "Portão duro: todo time precisa analisar os 15 programas Natural e os 4 DDMs antes de abrir o Estágio 2. Requisitos EARS sem rastreabilidade ao legado são rejeitados."
locale: "pt-br"
canonical_path: "06-kit-repositorio-times/01-arqueologia/LEGACY-EXPLORATION-CHECKLIST.md"
author: "Paula Silva, Americas Software GBB, Microsoft"
date: "2026-05-18"
version: "1.0.0"
status: "approved"
tags: ["legado", "exploracao", "gate", "estagio-1", "obrigatorio", "pt-br"]
---

# Checklist de Exploração do Legado

> **HARD GATE ANTES DO ESTÁGIO 2.** Nenhum requisito EARS é aceito sem referência a um arquivo de programa Natural ou DDM. Requisitos greenfield (sem paralelo no legado) precisam ser marcados `[GREENFIELD]` e justificados por escrito na spec.
>
> Por quê? Na edição anterior do workshop, vários times pularam a exploração do legado e escreveram specs baseadas apenas no brief de modernização. O resultado foram specs que não preservavam as regras de negócio reais dos 29 anos do SIFAP. **Desta vez, o portão é obrigatório.**

---

## 1. A Regra Dura

```
Todo REQ-ID no seu SPECIFICATION.md PRECISA ter uma linha `source_legacy` que
aponte para um dos seguintes:
 - um programa .NSN específico em legacy/natural-programs/ (idealmente com faixa de linhas)
 - um arquivo .ddm específico em legacy/adabas-ddms/
 - a string literal [GREENFIELD] com justificativa de 1 linha
```

O CI rejeita PRs para `develop` se algum REQ-ID estiver sem a linha `source_legacy`. Facilitadores verificam por amostragem no H2 (Handoff #2, ~14:30).

---

## 2. Os 15 Programas Natural — Quem Lê o Quê

Cada par fica com 3 programas. **Nenhum programa pode ficar sem leitor.**

| Par | Programas para ler | Por quê |
|-----|---------------------|---------|
| **1 · Visão** (PO + RE) | `CADBENEF.NSN`, `CADDEPEND.NSN`, `CADPROG.NSN` | Lógica de cadastro = entidades centrais que viram sujeitos das EARS |
| **2 · Arquitetura** (EA + SA) | `BATCHPGT.NSN`, `BATCHREL.NSN`, `BATCHCON.NSN` | Fluxos batch revelam fronteiras de módulo (bounded contexts) |
| **3 · Implementação** (TL + Dev) | `CALCBENF.NSN`, `CALCCORR.NSN`, `CALCDSCT.NSN` | Cálculos são onde o código moderno vai morar; vocês precisam reproduzi-los |
| **4 · Qualidade** (DBA + QA) | `VALBENEF.NSN`, `VALDOCS.NSN`, `VALELEG.NSN` | Validações viram testes; o DBA também mapeia campos dos DDMs |
| **5 · Operações** (DevOps + TW) | `CONSBENF.NSN`, `RELPGT.NSN`, `RELAUDIT.NSN` | Caminhos de leitura alimentam o glossário e o runbook |

### Checklist por programa (marque em `01-arqueologia/business-rules-catalog.md`)

Para cada programa do seu par, preencha estes 5 campos:

- [ ] Nome do programa + autor + ano da última modificação
- [ ] Inputs (quais DDMs ele lê)
- [ ] Outputs (quais DDMs ele escreve)
- [ ] Outros programas que ele chama (cadeia de CALLNAT)
- [ ] **Pelo menos 1 regra de negócio extraída como linha em `business-rules-catalog.md`** com `Programa Fonte` e idealmente faixa de linhas

`Programa Fonte` vazio = linha inválida.

---

## 3. Os 4 DDMs — Mapeamento de Campos

O Par 4 (DBA + QA) lidera. Todos os outros pares contribuem com revisão.

| DDM | Dono | Artefato-alvo em PostgreSQL |
|-----|------|------------------------------|
| `BENEFICIARIO.ddm` | Par 4 | Tabela `beneficiary` |
| `PAGAMENTO.ddm` | Par 4 | Tabela `payment` |
| `PROGRAMA-SOCIAL.ddm` | Par 4 | Tabela `social_program` |
| `AUDITORIA.ddm` | Par 4 | Tabela `audit_event` |

Para cada DDM:

- [ ] Listou cada campo com tipo (A/N/D/etc.) e tamanho
- [ ] Marcou explicitamente os campos `MU` (multi-valor) e `PE` (grupo periódico)
- [ ] Propôs mapeamento PostgreSQL (tipo da coluna, nulabilidade, tabela de relação para MU/PE)
- [ ] Identificou pelo menos 1 anti-padrão (desnormalização, constantes mágicas, …)

---

## 4. Caça aos Mistérios — Cota Mínima

Existem **10 regras de negócio escondidas**, **3 easter eggs** e **4 inconsistências** plantadas no código legado. Veja [`mysteries-checklist.md`](mysteries-checklist.md) para a lista da caça (sem respostas).

**Cota para passar pelo portão:** pelo menos **5 mistérios** documentados em `mysteries-found.md` com:

- O mistério em si (uma frase)
- Onde foi encontrado (arquivo + faixa de linhas)
- Por que importa (impacto se não preservado)

---

## 5. Verificação Antes de Abrir o Estágio 2

Por volta de 11h45 um facilitador vai checar o trabalho do seu par contra esta matriz. Não dá para passar para o Estágio 2 com linha vermelha.

| Artefato | Caminho | Critério do portão |
|----------|---------|---------------------|
| Glossário | `01-arqueologia/glossary.md` | ≥ 30 termos, cada um com `legacy source` se veio do código |
| Catálogo de regras de negócio | `01-arqueologia/business-rules-catalog.md` | ≥ 15 regras, **100% com `Programa Fonte` não-vazio** |
| Mapa de dependências | `01-arqueologia/dependency-map.md` | Grafo Mermaid cobrindo todos os 15 programas .NSN (sem órfãos) |
| Mistérios encontrados | `01-arqueologia/mysteries-found.md` | ≥ 5 mistérios com evidência arquivo+linha |
| Relatório de descoberta | `01-arqueologia/discovery-report.md` | Todas as seções preenchidas (sem placeholders) |

---

## 6. Trecho de Formato Obrigatório (leve para o Estágio 2)

Quando começar a escrever EARS no Estágio 2, **todo requisito precisa seguir este formato**:

```yaml
REQ-PAY-001:
 pattern: event-driven
 text: "When a payment cycle is generated, the SIFAP shall create payment records
 for every beneficiary with status ACTIVE."
 source_legacy: legacy/natural-programs/BATCHPGT.NSN#L120-L168
 acceptance: "10 active + 2 suspended beneficiaries produces 10 payment records."
```

Caso greenfield (sem paralelo no legado):

```yaml
REQ-AUTH-001:
 pattern: ubiquitous
 text: "The SIFAP shall authenticate users via OAuth2 with JWT tokens."
 source_legacy: "[GREENFIELD] Legacy used terminal session auth; modern API needs token auth."
 acceptance: "Unauthenticated requests return 401."
```

> Spec sem linha `source_legacy` = inválida. Os validadores do Specky no CI bloqueiam.

---

## Navegação

| Anterior | Início | Próximo |
|----------|--------|---------|
| [Estágio 1 — README](README.md) | [Kit PT-BR](../README.md) | [GUIDE do Estágio 1](GUIDE.md) |

— Paula
