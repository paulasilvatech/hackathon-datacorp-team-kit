---
title: "Relatório de Descoberta — Estágio 1: Arqueologia Digital"
description: "Template consolidado para encerrar o Estágio 1: o que o time descobriu, o que migrar/descartar/evoluir e o que o Estágio 2 precisa saber antes de começar."
locale: "pt-br"
canonical_path: "06-kit-repositorio-times/01-arqueologia/discovery-report.md"
author: "Paula Silva, Americas Software GBB, Microsoft"
date: "2026-05-18"
version: "1.0.0"
status: "template"
tags: ["estagio-1", "relatorio", "descoberta", "template", "pt-br"]
---

# Relatório de Descoberta — Estágio 1: Arqueologia Digital

> Este documento consolida todas as descobertas do Estágio 1.
> Preencha cada seção com as conclusões do time. **Este é o input principal do Estágio 2** — sem ele, a especificação vira chute.

**Time**: [Nome do Time]
**Data**: 19/05/2026
**Edição**: 
**Participantes**: [Liste os membros e suas personas]

---

## 1. Sumário Executivo

> Em 3 a 5 frases, resuma o que o time descobriu sobre o SIFAP legado.
> O que é este sistema? Qual sua criticidade? Qual o estado do código?

[Escreva aqui]

---

## 2. Visão Geral do Sistema

### 2.1 Propósito do SIFAP
[Descreva o que o sistema faz com base na análise do código]

### 2.2 Arquitetura Legada
[Descreva a arquitetura: quantos programas, DDMs, fluxos principais]

### 2.3 Usuários e Perfis
[Quem usa o sistema? Quais perfis de acesso existem?]

---

## 3. Principais Descobertas

### 3.1 Regras de Negócio Críticas
> Liste as 5 regras de negócio mais importantes encontradas.

1. [Regra + referência ao catálogo BR-XXX]
2.
3.
4.
5.

### 3.2 Dependências Complexas
> Quais programas estão mais acoplados? Onde há risco de efeito cascata?

[Descreva]

### 3.3 Dívida Técnica Identificada
> Que problemas no código legado vão complicar a migração?

- [ ] [Problema 1]
- [ ] [Problema 2]
- [ ] [Problema 3]

### 3.4 Gaps de Documentação
> O que a documentação existente NÃO cobre?

[Descreva]

---

## 4. Mistérios e Riscos

### 4.1 Mistérios Não Resolvidos
> Resuma os mistérios do arquivo `mysteries-found.md` que permanecem sem explicação.

| ID | Descrição | Risco para Migração |
|----|-----------|----------------------|
| | | |

### 4.2 Riscos para o Estágio 2
> O que o time de especificação precisa saber antes de começar?

1. [Risco 1]
2. [Risco 2]
3. [Risco 3]

---

## 5. Recomendações

### 5.1 O que migrar primeiro
> Com base na priorização do Par 1 (Product Owner), quais funcionalidades devem ser migradas primeiro?

| Prioridade | Funcionalidade | Justificativa |
|------------|----------------|---------------|
| 1 | | |
| 2 | | |
| 3 | | |

### 5.2 O que descartar
> Funcionalidades que provavelmente não precisam ser migradas:

- [Funcionalidade]: [Motivo para descartar]

### 5.3 O que evoluir
> Funcionalidades que devem ser migradas E melhoradas:

- [Funcionalidade]: [Como melhorar]

---

## 6. Métricas do Estágio

| Métrica | Valor |
|---------|-------|
| Programas analisados | ___ / 15 |
| DDMs mapeados | ___ / 4 |
| Regras de negócio encontradas | ___ |
| Regras escondidas encontradas | ___ / 10 |
| Easter eggs encontrados | ___ / 3 |
| Termos no glossário | ___ |
| Mistérios catalogados | ___ |
| Tempo total gasto | ___ horas |

---

## 7. Notas para o Próximo Estágio

> Deixe aqui mensagens para o time no Estágio 2 (Especificação Moderna):

[Escreva aqui]

---

## Definition of Done deste relatório

- [ ] Todas as seções acima preenchidas (sem placeholders).
- [ ] Pelo menos 5 regras críticas listadas em §3.1, cada uma referenciando uma `BR-XXX` do catálogo.
- [ ] Decisões de migrar/descartar/evoluir em §5 cobrem as 8+ funcionalidades principais.
- [ ] Métricas de §6 conferem com os outros artefatos (glossary.md, business-rules-catalog.md, mysteries-found.md).

— Paula
