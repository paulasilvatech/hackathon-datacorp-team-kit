---
title: "Arquivos DDM Adabas - Legado SIFAP"
description: "Arquivos Data Definition Module que descrevem a estrutura do banco Adabas usada pelo sistema SIFAP legado"
author: "Paula Silva, Americas Software GBB, Microsoft"
date: "2026-04-23"
version: "1.0.0"
status: "approved"
tags: ["adabas", "ddm", "legacy", "sifap", "database"]
---

<!-- markdownlint-disable MD013 MD025 MD026 MD028 MD029 MD034 MD040 MD051 MD060 -->

# Arquivos DDM Adabas

> Data Definition Modules que descrevem a estrutura física e lógica do banco Adabas usado pelo sistema SIFAP legado.

## Conteúdo

| Arquivo               | Descrição                                                        |
| --------------------- | ---------------------------------------------------------------- |
| `BENEFICIARIO.ddm`    | Registro mestre de beneficiário - dados pessoais, documentos, inscrição |
| `PAGAMENTO.ddm`       | Registro de transação de pagamento - valores, datas, status      |
| `PROGRAMA-SOCIAL.ddm` | Definições de programa social - regras, limites, elegibilidade   |
| `AUDITORIA.ddm`       | Trilha de auditoria - quem alterou o quê e quando                |

## Uso

Estes arquivos são **material de referência somente leitura** para os times do workshop durante o estágio de Arqueologia (Estágio 1). Mapeie cada campo DDM para um campo de entidade JPA no sistema modernizado.

## Navegação

| Pai                                  | Início                            |
| ------------------------------------ | --------------------------------- |
| [02 - Cenário Legado](../README.md)  | [Raiz do Workspace](../../README.md) |
