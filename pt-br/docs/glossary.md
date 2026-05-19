---
title: "Glossário de Domínio — SIFAP 2.0"
description: "Glossário autoritativo da equipe. Preenchido durante o Estágio 1 (Arqueologia) pelo Tech Writer + Requirements Engineer."
author: "Tech Writer (time)"
date: "2026-04-29"
version: "0.1.0"
status: "draft"
tags: ["glossary", "domain", "sifap", "stage-1"]
---

<!-- markdownlint-disable MD013 MD025 MD026 MD028 MD029 MD034 MD040 MD051 MD060 -->

# Glossário de Domínio

> Fonte única da verdade para termos de domínio. Todo novo termo entra aqui ANTES de aparecer em código, specs ou tickets. O Tech Writer é responsável por este arquivo.

## Como adicionar um termo

1. Use este formato:

```markdown
### Term

- **Source:** Natural program or DDM where the term originates (e.g., `CADBENEF.NSN:42`)
- **Definition:** Short definition (1–2 sentences)
- **English equivalent:** If the legacy term is in Portuguese
- **Used in:** REQ-IDs, files, modules
```

2. Mantenha os termos em ordem alfabética dentro de cada seção.
3. Se duas pessoas da equipe discordarem de uma definição, registre isso como uma decisão e acione o Requirements Engineer.

---

## A

### Adabas

- **Source:** Legacy data store
- **Definition:** Banco de dados mainframe em estilo NoSQL multi-value usado pelo sistema legado SIFAP. DDMs (Data Definition Modules) do Adabas descrevem registros.
- **Used in:** todos os programas `.NSN` em `02-cenario-sifap-legado/natural-programs/`

## B

### Beneficiário (Beneficiary)

- **Source:** `BENEFICIARIO.ddm`
- **Definition:** Pessoa que recebe pagamentos de benefício social pelo SIFAP.
- **English equivalent:** Beneficiary
- **Used in:** REQ-BEN-\*, `BeneficiaryEntity.java`

## C

### Ciclo (Cycle)

- **Source:** `BATCHPGT.NSN`
- **Definition:** Execução mensal de geração de pagamentos que produz registros de pagamento para todos os beneficiários elegíveis.
- **English equivalent:** Payment cycle
- **Used in:** REQ-PAY-\*, `PaymentCycleService.java`

### CPF

- **Source:** Brazilian Federal tax ID
- **Definition:** Identificador nacional de contribuinte com 11 dígitos, usado como identificador principal de beneficiários. Validado com o algoritmo módulo-11.
- **Used in:** toda a lógica de identificação de beneficiários

## D

### DDM (Data Definition Module)

- **Source:** Adabas
- **Definition:** Definicao de schema para um registro Adabas. O SIFAP usa 4 DDMs: Beneficiary, Payment, Social Program, Audit.
- **Used in:** archaeology + schema mapping

---

## Como facilitadores usam este arquivo

A pessoa facilitadora confere este glossário em toda transição de estágio. Um glossário com menos de 30 termos ao fim do Estágio 1 é um sinal de que a equipe não investigou com profundidade suficiente.
