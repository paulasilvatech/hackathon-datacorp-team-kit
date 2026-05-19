---
title: "Modelo de ADR"
description: "Modelo para registros de decisão de arquitetura"
status: "template"
---

<!-- markdownlint-disable MD013 MD025 MD026 MD028 MD029 MD034 MD040 MD051 MD060 -->

# ADR-NNNN: <Título curto e decisivo>

> Substitua `NNNN` pelo próximo número sequencial (por exemplo, `0007`).
> Substitua este bloco de citação inteiro por um resumo de 1 linha da decisão.

| Campo      | Valor                                            |
| ---------- | ------------------------------------------------ |
| Status     | proposto \| aceito \| descontinuado \| substituído |
| Data       | YYYY-MM-DD                                       |
| Autores    | <Persona — Nome>                                 |
| Substitui  | ADR-NNNN \| N/A                                  |

## Contexto

Qual é o problema que estamos vendo e que motiva esta decisão? Referencie o
objetivo de negócio, a restrição legada ou a necessidade de stakeholder.

Seja específico. Cite REQ-IDs ou programas em `02-cenario-sifap-legado/` quando relevante.

## Decisão

A mudança que estamos propondo ou com a qual concordamos. Use um ou dois parágrafos.

Declare a decisão em voz ativa: "Vamos adotar …", "Não vamos migrar …".

## Alternativas consideradas

Liste pelo menos 2 alternativas. Para cada uma, explique por que foi rejeitada.

| Alternativa | Por que foi rejeitada |
| ----------- | --------------------- |
| Opção A     | …                     |
| Opção B     | …                     |

## Consequências

O que fica mais fácil? O que fica mais difícil? Há novos riscos?

- **Mais fácil:** …
- **Mais difícil:** …
- **Riscos:** …
- **Mitigações:** …

## Relacionado

- REQ-IDs: …
- ADRs: …
- Arquivos-fonte: …

## Referências

- Cite docs, RFCs ou pesquisas que embasaram a decisão.
