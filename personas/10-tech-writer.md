---
title: "Ficha da Persona - Tech Writer"
description: "O que o Tech Writer faz dentro do time de 10 durante o Dia 2 do Hackathon SERPRO 2026."
author: "Paula Silva, Americas Software GBB, Microsoft"
date: "2026-04-18"
version: "1.0.0"
persona_id: "10"
tags: ["persona", "tech-writer", "hackathon", "SERPRO"]
---

# Persona - Tech Writer

## Quem é essa pessoa

Quem transforma decisão em memória durável. Sem Tech Writer consciente, ADRs viram arquivos vazios, README fica no "instale as dependências", e nada do que foi descoberto sobrevive à última hora do hackathon.

## Missão no hackathon

Manter a documentação viva durante o dia - não ao final. README que cresce, ADRs escritas no momento da decisão, change log presente. Escrever o relatório de experiência do Agent no Estágio 4.

## Seu papel no framework Agentic Legacy Modernization

Este hackathon aplica o framework **Agentic Legacy Modernization** - uma abordagem de modernizacao de sistemas legado usando agentes de IA especializados em cada fase. O pipeline completo esta descrito no `01-blueprint/HACKATHON-BLUEPRINT.md`. Sua persona mapeia para o pipeline assim:

- **Agentes relevantes**: Documentation Agent (transversal)
- **Fase do framework**: Todas as fases (documentacao continua)
- **Seu papel no pipeline**: Mantem rastreabilidade e documenta decisoes para audit trail

## Onde você aparece por estágio

| Estágio | Você faz isto | Entregável que depende de você |
|---|---|---|
| 1. Arqueologia | Mantém glossário e catálogo em formato legível. Escreve o relatório de descoberta no fim do estágio. | Relatório Estágio 1 |
| 2. Spec Greenfield | Revisa a spec para consistência, terminologia e clareza. Formata ADRs com o template. | Spec e ADRs em formato padrão |
| 3. Reconstrução | README do projeto vira real, não placeholder. Documenta decisões no `docs/` à medida que surgem. | README + `docs/` populados |
| 4. Evolução com Agent | Observa o Agent trabalhar e escreve o relatório honesto da experiência (o que foi bom, o que foi mau, o que aprendeu). | Relatório final do Estágio 4 |

## Ferramentas e primitives

- **Copilot Chat** para revisão de estilo e clareza.
- **Cowork** se precisar redigir documento mais longo.
- **markdown-writer** skill para README e ADRs estruturados.
- **MCP do GitHub** para commits no `docs/` enquanto outras pessoas mexem em código.

## Cheat sheets que você usa

- `cheat-sheets/specky-workflow.md` - o plugin gera documentação em cada fase, e você mantém consistência entre o que ele produz e o que o time escreve à mão.
- `cheat-sheets/model-routing.md` - Haiku 4.5 para revisão de estilo, Sonnet 4.6 para redação.

## Como se sai bem

- Cada ADR tem: contexto, decisão, consequências. Não mais, não menos.
- README evolui a cada hora, não só no final.
- Terminologia do projeto é consistente (se chamou "ciclo", não vira "rodada" no parágrafo seguinte).
- Relatório do Estágio 4 é honesto sobre o Agent - não tenta vender.

## Como se perde

- Esperou o Estágio 3 terminar para começar a escrever.
- ADRs de uma linha ("decidimos usar X").
- README que ainda diz "TODO: adicionar instruções" no final.
- Relatório do Agent que diz só "funcionou bem".

## Se você acumulou duas personas

- **Tech Writer + Product Owner** - você escreve o "porquê" do projeto.
- **Tech Writer + DevOps Engineer** - você documenta enquanto pipeline roda.
- **Tech Writer + Requirements Engineer** é forte para time pequeno - você estrutura e redige.

## 3 Prompts Exemplares

1. **(Chat)** "Revise este README e identifique: secoes com TODO, terminologia inconsistente, informacoes desatualizadas (portas, credenciais, endpoints). Proponha correcoes."
2. **(Edits)** "No arquivo ADR-001.md, complete as secoes Context, Decision e Consequences usando o template em 02-spec-moderna/ADR-TEMPLATE.md."
3. **(Chat)** "Crie um relatorio honesto da experiencia com o Copilot Agent: o que funcionou, o que surpreendeu, o que falhou. Baseie no template 04-evolucao/agent-experience-report.md."

## Se Você Ficar Travado (Defaults de Emergência)

- Não sabe formato ADR? Abra `02-spec-moderna/ADR-TEMPLATE.md` - copie e preencha.
- README está vazio? Comece com: (1) O que é o sistema, (2) Como rodar, (3) Endpoints disponíveis. O resto pode crescer.
- Glossário parado? Peça ao Copilot: "Liste todas as abreviações encontradas nos arquivos .NSN do SIFAP e expanda cada uma."
- Relatório do Agent vazio? Abra `04-evolucao/agent-experience-report.md` - o template tem seções prontas para preencher.

## Dependências - Quem Depende de Você

| Persona | Relação | Artefato |
|---------|---------|----------|
| Todos | VOCÊ depende deles | Decisões e código para documentar |
| Product Owner | Depende de VOCÊ | Glossário e relatórios legíveis |
| QA Engineer | Depende de VOCÊ (indireta) | Terminologia consistente na spec |
| Facilitadora (Paula) | Depende de VOCÊ | Relatório final do Estágio 4 |

## Como Você É Avaliado

- Rubrica A2 (Spec): documentação consistente, terminologia padronizada
- Rubrica A7 (Agent): relatório honesto e detalhado
- Critério: "README evoluiu a cada hora. ADRs têm contexto, decisão e consequências. Nada diz TODO."

- Paula
