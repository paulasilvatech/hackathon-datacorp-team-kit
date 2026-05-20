<!-- markdownlint-disable MD013 MD025 MD026 MD028 MD029 MD034 MD040 MD051 MD060 -->

# @archaeologist — Estágio 1: Arqueologia


> **Para quem é isto?** Para o time durante o Estágio 1 — todos os 5 pares em paralelo.
>
> **O que você terá ao final desta leitura:**
>
> 1. Como ativar o agente `@archaeologist` no Copilot Chat
> 2. Prompts típicos para extração de regras
> 3. O que o agente NÃO faz (não escreve código moderno)

> Use este agente quando a equipe estiver lendo o legado. Ele ajuda a observar, catalogar e perguntar melhor. Ele não reescreve código e não inventa regra de negócio.

## Objetivo da etapa

Transformar arquivos Natural/Adabas em evidências úteis para o Estágio 2: glossário, regras de negócio, mapa de dependências, DDMs compreendidos e mistérios registrados.

## Quando usar

- **Horário:** 11:00–12:00 + 13:30–14:00.
- **Protagonista:** Requirements Engineer.
- **Suporte forte:** Tech Writer, Enterprise Architect e DBA.
- **Pré-requisito:** pasta `legado-natural/` disponível no workspace.

## Passo a passo com o agente

1. Abra o Copilot Chat no VS Code.
2. Selecione o agente `@archaeologist`.
3. Cole o prompt de abertura abaixo.
4. Leia um programa por vez. Não pule arquivos porque parecem simples.
5. Para cada achado, registre evidência com caminho e, quando possível, linha.
6. Ao final, confira a Definição de Pronto antes do Passagem #1.

```text
Estou iniciando o Estágio 1 — Arqueologia.
Temos código Natural/Adabas em legado-natural/.
Ajude o time a explorar sistematicamente: programas, DDMs, CALLNATs,
regras de negócio, mistérios e riscos de migração.
Comece me dizendo qual arquivo abrir primeiro e que perguntas fazer.
```

## O que perguntar

| Situação | Prompt útil |
| --- | --- |
| Programa Natural desconhecido | "Leia este programa comigo e separe entrada, processamento, saída e regra de negócio." |
| DDM Adabas | "Explique estes campos, marque MU/PE/DE e sugira mapeamento PostgreSQL." |
| Regra ambígua | "Não invente. Registre como mistério, com hipótese, evidência e impacto." |
| CALLNAT | "Mapeie quem chama quem e gere um Mermaid simples." |

## Definição de Pronto

- [ ] Glossário com pelo menos 30 termos relevantes.
- [ ] Catálogo de regras com programa-fonte preenchido.
- [ ] Mapa de dependências cobrindo os programas lidos.
- [ ] DDMs principais com campos, tipos e observações de modelagem.
- [ ] Pelo menos 5 mistérios documentados com evidência.
- [ ] Relatório de descoberta pronto para o Passagem #1 (~14:30).

## Anti-padrões

| Não faça | Faça |
| --- | --- |
| Pedir "resuma tudo" sem abrir arquivo | Abra um arquivo e leia com o agente |
| Transformar hipótese em requisito | Marque como mistério até haver evidência |
| Editar o legado | Trate `legado-natural/` como somente leitura |
| Começar arquitetura no Estágio 1 | Guarde ideias para o `@architect` |

## Navegação

| Anterior | Início | Próximo |
| --- | --- | --- |
| [Visão dos Agent Kits](../README.md) | [Kit PT-BR](../../README.md) | [@architect](../02-architect/README.md) |

— Paula
