---
title: "Programas Natural - Legado SIFAP"
description: "Programas-fonte Natural/ADABAS que compõem o sistema legado de processamento de transações do SIFAP"
author: "Paula Silva, Americas Software GBB, Microsoft"
date: "2026-04-23"
version: "1.0.0"
status: "approved"
tags: ["natural", "adabas", "legacy", "sifap", "programs"]
---

<!-- markdownlint-disable MD013 MD025 MD026 MD028 MD029 MD034 MD040 MD051 MD060 -->

# Programas Natural

> Arquivos-fonte Natural (`.NSN`) que implementam a lógica de negócio legada do SIFAP no mainframe.

## Conteúdo

### Processamento Batch

| Programa       | Descrição                                           |
| -------------- | --------------------------------------------------- |
| `BATCHCON.NSN` | Conciliação batch - reconcilia pagamentos com o SIAFI |
| `BATCHPGT.NSN` | Pagamento batch - gera ciclos mensais de pagamento  |
| `BATCHREL.NSN` | Relatório batch - produz relatórios gerenciais      |

### Cadastro (CRUD)

| Programa        | Descrição                   |
| --------------- | --------------------------- |
| `CADBENEF.NSN`  | Cadastro de beneficiário    |
| `CADDEPEND.NSN` | Cadastro de dependente      |
| `CADPROG.NSN`   | Cadastro de programa social |

### Cálculo

| Programa       | Descrição                         |
| -------------- | --------------------------------- |
| `CALCBENF.NSN` | Cálculo do valor do benefício     |
| `CALCCORR.NSN` | Cálculo de correção/ajuste        |
| `CALCDSCT.NSN` | Cálculo de desconto               |

### Consulta

| Programa       | Descrição                |
| -------------- | ------------------------ |
| `CONSBENF.NSN` | Consulta de beneficiário |

### Validação

| Programa       | Descrição                    |
| -------------- | ---------------------------- |
| `VALBENEF.NSN` | Regras de validação de beneficiário |
| `VALDOCS.NSN`  | Validação de documentos      |
| `VALELEG.NSN`  | Validação de elegibilidade   |

### Relatórios

| Programa       | Descrição                 |
| -------------- | ------------------------- |
| `RELAUDIT.NSN` | Geração de relatório de auditoria |
| `RELPGT.NSN`   | Geração de relatório de pagamento |

## Uso

Estes arquivos são **material de referência somente leitura**. Durante o Estágio 1 (Arqueologia), os times analisam estes programas para extrair regras de negócio e mapeá-las para classes de serviço Java.

## Navegação

| Pai                                  | Início                            |
| ------------------------------------ | --------------------------------- |
| [02 - Cenário Legado](../README.md)  | [Raiz do Workspace](../../README.md) |
