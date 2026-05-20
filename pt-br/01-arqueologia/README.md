---
title: "Estágio 1 — Arqueologia"
description: "Etapa de análise do código legado: explorar os programas Natural do SIFAP, extrair regras de negócio e construir o glossário do domínio."
locale: "pt-br"
canonical_path: "06-kit-repositorio-times/01-arqueologia/README.md"
author: "Paula Silva, Americas Software GBB, Microsoft"
date: "2026-05-18"
version: "2.0.0"
status: "approved"
tags: ["estagio-1", "arqueologia", "legado", "analise", "workshop", "pt-br"]
---

<!-- markdownlint-disable MD013 MD025 MD026 MD028 MD029 MD034 MD040 MD051 MD060 -->

# Estágio 1 — Arqueologia

> **LEIA PRIMEIRO:** [`LEGACY-EXPLORATION-CHECKLIST.md`](LEGACY-EXPLORATION-CHECKLIST.md) — portão duro antes do Estágio 2.
>
> Explore o sistema SIFAP legado com Copilot Ask e os agentes de etapa. Extraia regras de negócio, construa um glossário e mapeie dependências. Todo artefato produzido aqui alimenta o Estágio 2; especificações sem rastreabilidade ao legado são rejeitadas pelo CI.

## Onde isso encaixa no SDLC

![Linha do tempo do dia: pré-evento, 4 estágios e demo, com as três passagens H1, H2, H3](assets/timeline-stages.svg)

## Quem trabalha aqui

Todos os 5 pares trabalham em paralelo, cada um responsável por 3 programas Natural. O **Par 1 (Visão)** lidera a síntese ao final do estágio. Veja [`GUIDE.md`](GUIDE.md) para a divisão completa.

## Conteúdo

| Arquivo                                                              | Propósito                                                               |
| -------------------------------------------------------------------- | ----------------------------------------------------------------------- |
| [`LEGACY-EXPLORATION-CHECKLIST.md`](LEGACY-EXPLORATION-CHECKLIST.md) | **PORTÃO DURO.** Posse de programa por par + DoD para abrir o Estágio 2 |
| [`GUIDE.md`](GUIDE.md)                                               | Guia passo a passo deste estágio                                        |
| [`glossary.md`](glossary.md)                                         | Modelo de glossário de termos do domínio                                |
| [`business-rules-catalog.md`](business-rules-catalog.md)             | Catálogo de regras de negócio extraídas (`Programa Fonte` obrigatório)  |
| [`dependency-map.md`](dependency-map.md)                             | Modelo de mapeamento de dependências do sistema                         |
| [`discovery-report.md`](discovery-report.md)                         | Modelo de relatório de descobertas                                      |
| [`mysteries-checklist.md`](mysteries-checklist.md)                   | Checklist de lógica escondida para os times                             |
| [`mysteries-found.md`](mysteries-found.md)                           | Modelo para registrar mistérios descobertos                             |

O código legado em si fica em [`../legado-natural/`](../legado-natural/) (compartilhado pelo kit).

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
<a href="GUIDE.md"><strong>Estágio 1 — Arqueologia</strong></a><br/>
<sub>13:00–14:30 · Ler o legado e catalogar regras de negócio.</sub>
</td>
</tr>
</table>

<sub>↑ <a href="../README.md">Voltar ao Kit PT-BR</a></sub>

— Paula
