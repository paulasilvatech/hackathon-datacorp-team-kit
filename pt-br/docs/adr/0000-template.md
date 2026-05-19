---
title: "Template de ADR"
description: "Template para Architecture Decision Records"
status: "template"
---

<!-- markdownlint-disable MD013 MD025 MD026 MD028 MD029 MD034 MD040 MD051 MD060 -->

# ADR-NNNN: <Título curto e decisivo>

> Substitua `NNNN` pelo próximo número sequencial (por exemplo, `0007`).
> Substitua este blockquote inteiro por um resumo de 1 linha da decisão.

| Campo      | Valor                                            |
| ---------- | ------------------------------------------------ |
| Status     | proposed \| accepted \| deprecated \| superseded |
| Date       | YYYY-MM-DD                                       |
| Authors    | <Persona — Name>                                 |
| Supersedes | ADR-NNNN \| N/A                                  |

## Contexto

Qual é o problema que estamos vendo e que motiva esta decisão? Referencie o
objetivo de negocio, a restricao legada ou a necessidade de stakeholder.

Seja especifico. Cite REQ-IDs ou programas em `02-cenario-sifap-legado/` quando relevante.

## Decisão

A mudança que estamos propondo ou com a qual concordamos. Use um ou dois parágrafos.

Declare a decisão em voz ativa: "We will adopt …", "We will not migrate …".

## Alternativas consideradas

Liste pelo menos 2 alternativas. Para cada uma, explique por que foi rejeitada.

| Alternativa | Por que foi rejeitada |
| ----------- | --------------------- |
| Option A    | …                     |
| Option B    | …                     |

## Consequências

O que fica mais fácil? O que fica mais difícil? Há novos riscos?

- **Easier:** …
- **Harder:** …
- **Risks:** …
- **Mitigations:** …

## Relacionado

- REQ-IDs: …
- ADRs: …
- Source files: …

## Referências

- Cite docs, RFCs ou pesquisas que embasaram a decisão.
