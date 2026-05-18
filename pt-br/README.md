---
title: "Kit do Time — Português (BR)"
description: "Versão didática em português do kit do workshop. Os assets técnicos (legacy/, persona-kits/, .github/, scripts/) ficam no raiz do kit e não são duplicados por idioma."
locale: "pt-br"
canonical_path: "06-kit-repositorio-times/README.md"
author: "Paula Silva, Americas Software GBB, Microsoft"
date: "2026-05-18"
version: "1.0.0"
status: "approved"
tags: ["kit", "pt-br", "didatico", "workshop"]
---

# Kit do Time — Português (BR)

> 🌐 **Idiomas:** [English 🇬🇧](../en/README.md) · **Português 🇧🇷 (aqui)** · [Español 🇲🇽](../es/README.md)

> **COMECE AQUI** se você é participante do workshop.
>
> 1. Leia [`TEAM-FLOW.md`](TEAM-FLOW.md) — como vocês 5 cobrem 10 personas em 5 pares (10 minutos)
> 2. Leia suas duas cartas de persona em [`personas/`](personas/) (15 minutos)
> 3. Abra o guia do Stage 1 em [`01-arqueologia/GUIDE.md`](01-arqueologia/GUIDE.md)

## Ferramentas aprovadas — somente estas

O workshop roda em **stack fixa**. Misturar ferramentas alternativas fragmenta o time e quebra a rastreabilidade spec → código → teste.

| Use | Não use |
|-----|---------|
| **VS Code** (ou Insiders) | Cursor, Windsurf, IntelliJ, Eclipse, Sublime, plugins de Neovim |
| **GitHub Copilot** — modos Chat + Edits + Agent (Copilot Workspace OK) | Cline, Continue, Aider, Codeium, Tabnine |
| **GitHub Copilot CLI** *(opcional)* | ChatGPT / Claude.ai na web para gerar código (quebra o histórico do Copilot Chat) |
| **Spec-Kit** (plugin `specky-sdd`) — o motor de SDD | Kiro, GitHub Spec, pipelines de SDD em YAML custom |
| **GitHub** (Issues, PRs, Actions, Projects) | — |
| **Docker / Docker Compose** | instalações locais de Postgres/Node/Java que divergem do devcontainer |
| **Terraform** (Azure provider) | — |

O racional completo e o que o CI verifica estão em [`../.github/copilot-instructions.md`](../.github/copilot-instructions.md).

## Duas camadas de agente — ambas obrigatórias

O kit traz **duas camadas de agente** que cobrem eixos diferentes (papel × estágio). Use as duas.

| Camada | O que | Quando | Como |
|--------|-------|--------|------|
| [`../persona-kits/`](../persona-kits/) | Um kit por persona (agent + prompts + skills + MCP) | Instalado às 09:00, vive o dia inteiro | Cada pessoa copia seus 2 kits via `cp -r ../persona-kits/XX-*/.github/* .github/` |
| [`../agent-kits/`](../agent-kits/) | Quatro agentes por estágio: `@archaeologist`, `@architect`, `@builder`, `@evolution` | Selecionado a cada estágio pelo time | Abra o Copilot Chat → seletor de agentes → escolha o agente do estágio → cole o prompt de abertura do README do kit |

**Não são duplicados.** `persona-kits/` configura **seu Copilot para o seu papel**. `agent-kits/` coordena **o time para o estágio atual**. Um Stage 1 típico fica assim:

1. Você já carregou seu persona-kit (ex.: Requirements Engineer) → slash commands como `/ears-convert` funcionam.
2. O time seleciona `@archaeologist` no chat → a conversa entra em modo arqueologia.
3. Você pergunta ao `@archaeologist` para resumir `BATCHPGT.NSN` → resposta com enquadramento de arqueologia.
4. Você roda `/ears-convert` sobre o que descobriu → seu persona-kit de RE assume e devolve YAML com a linha `source_legacy:`.

O diagrama completo da integração está em [`../.github/copilot-instructions.md`](../.github/copilot-instructions.md).

## Como este folder se organiza

O kit é **trilíngue**, mas usa **estrutura híbrida**: apenas a documentação instrucional é traduzida; os assets técnicos ficam no raiz do kit e são compartilhados.

```
06-kit-repositorio-times/
│
├── pt-br/ ← VOCÊ ESTÁ AQUI
│ ├── README.md
│ ├── TEAM-FLOW.md
│ ├── 01-arqueologia/
│ │ ├── GUIDE.md
│ │ ├── LEGACY-EXPLORATION-CHECKLIST.md
│ │ └── ...
│ ├── 02-spec-moderna/
│ ├── 03-implementacao/
│ ├── 04-evolucao/
│ ├── personas/
│ ├── cheat-sheets/
│ └── docs/
│
├── es/ (espelho em espanhol latam neutro)
├── en/ (espelho em inglês)
│
├── legacy/ ← compartilhado, NÃO traduzido (parte da imersão 1997)
├── persona-kits/ ← compartilhado, NÃO traduzido (definições de agentes Copilot)
├── .github/ ← compartilhado, NÃO traduzido (workflows e templates)
├── scripts/ ← compartilhado, NÃO traduzido (setup.sh e check.sh)
├── .devcontainer/ ← compartilhado, NÃO traduzido
└── plugins/ ← compartilhado (em produção)
```

## Por que estrutura híbrida

- **Sem duplicação de código.** Os 15 programas Natural, 4 DDMs e os 10 persona-kits ficam em um lugar só. Atualização em 1 lugar, não em 3.
- **Imersão preservada.** Os documentos em `legacy/legacy-docs/` estão em português de 1997-2018 de propósito. Traduzir quebraria a autenticidade do cenário.
- **Agentes Copilot são código.** Os arquivos em `.github/` e `persona-kits/` são consumidos por ferramentas, não por humanos. Tradução não ajuda.
- **Cada idioma é navegável.** Dentro de `pt-br/` você tem um kit completo de conteúdo didático, com links relativos para os assets compartilhados (`../legacy/`, `../persona-kits/`).

## O que está traduzido nesta amostra

| Arquivo | Status |
|---------|--------|
| [`01-arqueologia/GUIDE.md`](01-arqueologia/GUIDE.md) | ✅ Reescrito no padrão didático completo |
| Todos os outros 27 arquivos | ⏳ Aguardando aprovação do padrão |

## O padrão didático aplicado

Todo arquivo traduzido segue esta estrutura:

1. **Eyebrow + frase-chave** — em uma frase, o que você vai fazer aqui
2. **Por que isso importa** — contexto narrativo, não burocrático
3. **Como pensar nisso** — modelo mental antes do passo a passo
4. **Passo a passo numerado** — cada passo com o comando, o output esperado e o "porque"
5. **Exemplo concreto** — um caso completo do início ao fim
6. **Armadilhas comuns** — "se você está fazendo X, está errado, faça Y"
7. **Como saber que terminou** — DoD verificável
8. **Próximo passo** — handoff explícito para qual par

## Regras de tradução

| Mantém em inglês | Traduz |
|------------------|--------|
| Nomes de produtos: GitHub Copilot, Spec-Kit, Next.js, Spring Boot, Terraform, PostgreSQL, Azure, Docker | Verbos, narrativa, exemplos |
| Termos técnicos consagrados: REQ-ID, EARS, ADR, C4, CI/CD, PR, commit, branch, MCP, DDM, OAuth2, JWT, IaC | Conceitos pedagógicos: "uma especificação é como…" |
| Comandos shell, código, paths, nomes de arquivo | Banners, headings, listas |
| Conteúdo do `.github/`, `persona-kits/`, `legacy/` | Definições, "Por que", "Como pensar" |

## Como esta amostra deve ser avaliada

Por favor, leia [`01-arqueologia/GUIDE.md`](01-arqueologia/GUIDE.md) com essas perguntas em mente:

1. **Um dev sênior brasileiro entende o que precisa fazer?** Se sim, padrão aprovado.
2. **O "por que" está claro em cada decisão importante?** Não basta dizer o que fazer.
3. **O exemplo concreto da seção "do legado à linha do catálogo" ajuda a fixar o padrão de rastreabilidade?** Esse é o conceito mais importante do dia.
4. **As armadilhas batem com o que você viu na edição anterior?** Adicionar / remover conforme sua memória do workshop anterior.
5. **O tom está adequado?** Optei por "você" direto, parceiro, sem formalidade excessiva.

Após sua aprovação (ou pedido de ajustes), aplico o mesmo padrão para os 27 arquivos restantes × 3 idiomas.

— Paula
