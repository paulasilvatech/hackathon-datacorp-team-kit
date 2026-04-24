---
title: "Cheat Sheet - GitHub Copilot nos 3 Modos"
description: "Uma página. Quando usar Chat, Edits ou Agent. Frases que funcionam. Erros típicos."
author: "Paula Silva, AI-Native Software Engineer, Americas Global Black Belt at Microsoft"
date: "2026-04-18"
version: "1.0.0"
tags: ["cheat-sheet", "copilot", "hackathon", "SERPRO"]
---

# GitHub Copilot nos 3 Modos - Cheat Sheet

## Decisão rápida

| Situação | Modo | Por quê |
|---|---|---|
| Entender código, discutir design, planejar abordagem | **Chat** | Conversa, baixo custo, reversível |
| Criar/editar múltiplos arquivos relacionados de uma vez | **Edits** | Visão multi-arquivo, você revisa diff |
| Delegar tarefa completa (issue → PR) | **Agent** | Trabalha sozinho, você revê no fim |

## Chat - Conversa

**Use quando**: você ainda não sabe o que quer; quer entender; quer discutir; quer avaliar trade-off.

**Frases que funcionam:**
- "Explique o que faz este programa Natural linha por linha."
- "Que riscos tem usar `JSONB` para armazenar histórico de contas bancárias?"
- "Resuma este DDM em 5 linhas para alguém que não sabe Adabas."
- "Desafie a seguinte ADR: `{colar ADR}`."

**Erros típicos:**
- Usar Chat para gerar arquivo. Use Edits.
- Aceitar resposta sem validar. Copilot alucina - sempre confira.
- Prompt curto demais ("ajuda"). Dê contexto: o que tem, o que quer, o que já tentou.

## Edits - Edição em lote

**Use quando**: você sabe o que quer; quer mudanças em vários arquivos; tem contexto estruturado.

**Frases que funcionam:**
- "Crie os módulos `beneficiary`, `agreement`, `payment` com estrutura de packages Spring Boot padrão."
- "Adicione teste unitário para cada método público do `PaymentService`."
- "Renomeie `Convenio` para `Agreement` em todo o projeto e atualize referências."
- "Para cada migration Flyway existente, adicione rollback comentado."

**Erros típicos:**
- Escopo largo demais. Divida em passos.
- Não revisar o diff. Sempre olhe antes de aceitar.
- Misturar mudanças lógicas com renomeio. Um PR por propósito.

## Agent - Delegação com autonomia

**Use quando**: você tem uma issue bem descrita, aceita que ele demore, está disposto a revisar PR gerado por alguém que não é você.

**Como preparar**:
1. Escreva a issue com **contexto, critério de aceitação, escopo**.
2. Aponte arquivos relevantes ("olhe `docs/adr/001.md` antes de começar").
3. Diga o que NÃO fazer ("não altere o schema do PostgreSQL").

**Acompanhamento**: não opere enquanto o Agent corre. Deixe-o ir. Verifique a cada ~10 min se o caminho faz sentido.

**Revisão do PR do Agent**: exatamente igual a PR humano. Review expresso ainda é review.

**Erros típicos:**
- Issue vaga → Agent entrega lixo.
- Disparar Agent em tarefa de 5 min que Edits resolveria.
- Mergear sem revisar porque "é só o Agent".

## Regra de bolso

> Se você não soubesse que é IA, você aceitaria este código em seu projeto? Se não, rejeite ou refine. Copilot acelera quem sabe; não substitui julgamento.

- Paula
