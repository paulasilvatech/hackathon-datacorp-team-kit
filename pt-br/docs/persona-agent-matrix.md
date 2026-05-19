---
title: "Matriz Persona × Agente"
description: "Mapeamento 10×4 completo de como cada persona interage com cada agente de etapa"
author: "Paula Silva, AI-Native Software Engineer, Americas Global Black Belt at Microsoft"
date: "2026-04-29"
version: "1.0.0"
status: "approved"
tags: ["personas", "agents", "matrix", "roles", "hackathon"]
---

<!-- markdownlint-disable MD013 MD025 MD026 MD028 MD029 MD034 MD040 MD051 MD060 -->

# Matriz Persona × Agente

Esta matriz mapeia cada persona para cada agente, mostrando quem faz o que em cada estágio do workshop. Use-a para entender seu papel em cada momento do dia.

**Como ler este documento:**

1. Encontre a linha da sua persona
2. Leia horizontalmente para ver seu nível de intensidade em cada estágio
3. Para stages em que você é **PROTAGONIST** ou **Secondary**, leia as orientações detalhadas abaixo
4. Abra o README do agent kit do estágio atual para ver o workflow completo

## A Matriz

| #   | Persona               | @archaeologist  | @architect      | @builder        | @evolution      |
| --- | --------------------- | --------------- | --------------- | --------------- | --------------- |
| 01  | Product Owner         | Observer        | Secondary       | Observer        | Secondary       |
| 02  | Requirements Engineer | **PROTAGONIST** | Secondary       | Observer        | Observer        |
| 03  | Enterprise Architect  | Secondary       | Secondary       | Observer        | Observer        |
| 04  | Software Architect    | Observer        | **PROTAGONIST** | Secondary       | Observer        |
| 05  | Technical Lead        | Observer        | Secondary       | Secondary       | **PROTAGONIST** |
| 06  | Developer             | Observer        | Observer        | **PROTAGONIST** | Secondary       |
| 07  | DBA                   | Secondary       | Observer        | Secondary       | Observer        |
| 08  | QA Engineer           | Observer        | Observer        | Secondary       | Secondary       |
| 09  | DevOps Engineer       | Observer        | Observer        | Secondary       | Secondary       |
| 10  | Tech Writer           | Secondary       | Observer        | Observer        | Secondary       |

**PROTAGONIST** = Conduz o uso do agente; é responsável pelas entregas do estágio.
**Secondary** = Contribui ativamente; trabalha em par com a pessoa protagonista.
**Observer** = Acompanha pelo chat; pronta para ajudar quando sua especialidade for necessária.

## Orientação por Célula

### Estágio 1 — @archaeologist

| Persona                                 | O que você faz                                                                                                                                                                                            |
| --------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Requirements Engineer** (PROTAGONIST) | Conduz a exploração. Abra cada programa Natural, peça ao agente para ajudar a decodificá-lo e capture regras de negócio como requisitos em rascunho. Você é responsável pelo rascunho das business rules. |
| Tech Writer (Secondary)                 | Construa o glossário de domínio em tempo real. Toda vez que a equipe encontrar um termo — nome de variável, rótulo de campo, propósito de sub-rotina — adicione-o ao glossário com uma definição.         |
| Enterprise Architect (Secondary)        | Foque no panorama geral: quais sistemas externos o código legado chama? Quais entradas batch vêm de onde? Comece a rascunhar o system context.                                                            |
| DBA (Secondary)                         | Foque nos DDMs. Documente tipos de campo, descriptors, estruturas MU/PE e relações entre arquivos. Isso se torna seu data map.                                                                            |
| Product Owner (Observer)                | Escute e valide. Quando a equipe propuser uma interpretação de regra de negócio, confirme ou questione com base em seu entendimento de domínio.                                                           |
| All others (Observer)                   | Acompanhem o chat. Quando alguém perguntar sobre um padrão na sua área de especialidade (por exemplo, Developer vê um cálculo que reconhece), manifeste-se.                                               |

### Estágio 2 — @architect

| Persona                              | O que você faz                                                                                                                                                                                                                      |
| ------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Software Architect** (PROTAGONIST) | Lidera a definição de bounded contexts. Use o data map e o call graph do Estágio 1 para identificar limites naturais. Desenhe diagramas C4. Escreva os primeiros ADRs.                                                                |
| Requirements Engineer (Secondary)    | Transforme as business rules do Estágio 1 em requisitos EARS formais com IDs `REQ-NNN`. Cada requisito precisa de acceptance criteria. Trabalhe com Software Architect para garantir que os requisitos mapeiem para bounded contexts. |
| Enterprise Architect (Secondary)     | Valide o system context diagram. Garanta que pontos de integração (batch feeds, APIs externas, autenticação) estejam capturados. Revise ADRs quanto à consistência arquitetural.                                                    |
| Product Owner (Secondary)            | Priorize requisitos. Com tempo limitado, a equipe não consegue implementar tudo. Ajude a decidir quais requisitos são must-have vs. nice-to-have.                                                                                   |
| Technical Lead (Observer)            | Comece a pensar na ordem de implementação. Qual bounded context a equipe deve construir primeiro? Quais são as dependências?                                                                                                        |
| All others (Observer)                | Revisem a especificação emergente. Sinalizem qualquer coisa que pareça incompleta ou inconsistente da perspectiva de vocês.                                                                                                         |

### Estágio 3 — @builder

| Persona                        | O que você faz                                                                                                                                                                        |
| ------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Developer** (PROTAGONIST)    | Escreve código. Use o builder agent para gerar entidades JPA, serviços Spring, controllers REST e páginas Next.js. Todo trecho de código rastreia para um `REQ-NNN`.                  |
| DBA (Secondary)                | É responsável pela camada de banco de dados. Revise mapeamentos de entidade, escreva migrações Flyway, valide se o schema PostgreSQL representa corretamente o data model do Estágio 2. |
| QA Engineer (Secondary)        | Escreva testes junto com Developer. Para cada serviço, produza pelo menos um teste happy-path e um error-path. Monitore cobertura e sinalize lacunas.                                 |
| Technical Lead (Secondary)     | Revise o código à medida que ele é produzido. Verifique violações de padrão (sem campos `@Autowired`, sem retornos `null`, sem `any` em TypeScript). Faça merge de PRs.               |
| Software Architect (Secondary) | Valide se a implementação corresponde ao design. Se Developer estiver desviando dos limites dos bounded contexts, sinalize cedo.                                                      |
| All others (Observer)          | Disponíveis para perguntas. Developer pode precisar de esclarecimento de domínio que apenas Product Owner ou Requirements Engineer consegue fornecer.                                 |

### Estágio 4 — @evolution

| Persona                          | O que você faz                                                                                                                                                                 |
| -------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Technical Lead** (PROTAGONIST) | Escreva GitHub Issues para o Copilot Agent executar. Revise PRs gerados por IA. Decida o que fazer merge e o que rejeitar. É responsável por integração e prontidão para demo. |
| DevOps Engineer (Secondary)      | Escreva o workflow do GitHub Actions e os módulos Terraform. Garanta tagging adequado, gerenciamento de secrets e configuração de recursos.                                    |
| QA Engineer (Secondary)          | Valide se o pipeline de CI inclui todos os quality gates: lint, build, test. Revise resultados de testes de PRs gerados por IA.                                                |
| Developer (Secondary)            | Revise código gerado por IA quanto à corretude. Você conhece melhor a codebase — detecte erros lógicos que checks automatizados podem não pegar.                               |
| Tech Writer (Secondary)          | Refine o README, documente o roteiro de demo e garanta que as notas da retrospectiva capturem os aprendizados da equipe.                                                       |
| Product Owner (Secondary)        | Ajude a priorizar o que precisa funcionar para a demo vs. o que pode ser adiado. Prepare a narrativa para a apresentação de 3 minutos.                                         |
| All others (Observer)            | Contribuam com observações de retrospectiva. O que surpreendeu vocês? O que fariam de forma diferente?                                                                         |

## Sugestão de Ordem de Leitura

1. Leia o `PERSONA.md` do seu papel em [`persona-kits/`](../persona-kits/) — entenda pelo que você é responsável
2. Leia sua **linha nesta matriz** — entenda sua intensidade em cada estágio
3. Quando um novo estágio começar, abra o **README do agent kit** desse estágio em [`agent-kits/`](../agent-kits/)
4. Ative o **agent** do estágio atual e comece a trabalhar

## Referências

- Agent kits: [`agent-kits/`](../agent-kits/README.md)
- Arquitetura dos agentes: [`docs/4-agents-explained.md`](4-agents-explained.md)
- Persona kits consolidados: [`persona-kits/`](../persona-kits/)

---

| Anterior                     | Início                             | Próximo                                       |
| ---------------------------- | ---------------------------------- | --------------------------------------------- |
| [Início dos Docs](README.md) | [Início do Team Kit](../README.md) | [4 Agentes Explicados](4-agents-explained.md) |
