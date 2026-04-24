---
title: "Ficha da Persona - QA Engineer"
description: "O que o QA Engineer faz dentro do time de 10 durante o Dia 2 do Hackathon SERPRO 2026."
author: "Paula Silva, Americas Software GBB, Microsoft"
date: "2026-04-18"
version: "1.0.0"
persona_id: "08"
tags: ["persona", "qa-engineer", "hackathon", "SERPRO", "testing"]
---

# Persona - QA Engineer

## Quem é essa pessoa

Quem transforma requisito em teste executável. No SIFAP 2.0, é quem garante que a regra de cálculo de pagamento sobreviva a qualquer refatoração do Estágio 3 e que o batch do ciclo mensal funciona dentro das fronteiras previstas.

## Missão no hackathon

Definir a estratégia de testes do projeto. Escrever testes críticos (não 100% de cobertura; os certos). Validar a rastreabilidade spec → teste. Proteger o time de falso verde no CI.

## Seu papel no framework Agentic Legacy Modernization

Este hackathon aplica o framework **Agentic Legacy Modernization** - uma abordagem de modernizacao de sistemas legado usando agentes de IA especializados em cada fase. O pipeline completo esta descrito no `01-blueprint/HACKATHON-BLUEPRINT.md`. Sua persona mapeia para o pipeline assim:

- **Agentes relevantes**: Test Gen Agent (E3), Security Agent (E3)
- **Fase do framework**: Translation and Test Generation → Validation
- **Seu papel no pipeline**: Garante cobertura de teste e valida equivalencia funcional legado→moderno

## Onde você aparece por estágio

| Estágio | Você faz isto | Entregável que depende de você |
|---|---|---|
| 1. Arqueologia | Identifica cenários críticos a partir dos Naturals (casos de canto do ciclo mensal, rejeição do BB). | Lista de cenários críticos |
| 2. Spec Greenfield | Valida que cada requisito EARS é testável. Propõe critérios de aceitação concretos. | Critérios de teste por requisito |
| 3. Reconstrução | Escreve testes de unidade e integração para o núcleo (cálculo de pagamento, ajuste, reconciliação). Mantém CI verde. | Suíte de teste + pipeline verde |
| 4. Evolução com Agent | Exige que o PR do Agent venha com testes próprios. Valida cobertura dos cenários novos. | Coverage coerente com a feature |

## Ferramentas e primitives

- **Copilot Chat** para gerar cenários de teste a partir de requisitos EARS.
- **Copilot Edits** para gerar esqueletos de JUnit em lote.
- **Testcontainers** para integração com PostgreSQL real.
- **Specky** - fase 9 (Test Strategy) é o seu território.
- **MCP do GitHub Actions** para monitorar o CI.

## Cheat sheets que você usa

- `cheat-sheets/specky-workflow.md` - fase 9.
- `cheat-sheets/copilot-3-modes.md` - você usa Edits para criar o esqueleto e Chat para conversar sobre o que falta cobrir.

## Como se sai bem

- Cobertura nos caminhos que importam: cálculo de pagamento, reconciliação BB, ajustes com aprovação dupla.
- Testes rápidos - a suíte inteira roda em menos de dois minutos.
- Testes que quebram ao primeiro bug, não "testes que passam sempre".
- Você diz "esse PR não entra sem teste" sem drama.

## Como se perde

- Persegue 100% de cobertura e perde o Estágio 3.
- Escreve testes que testam o framework, não o domínio.
- Aceita mocks onde Testcontainers era o certo.
- Deixa o CI vermelho por 20 minutos esperando alguém olhar.

## Se você acumulou duas personas

- **QA + Developer** é a mais comum e produtiva.
- **QA + Requirements Engineer** também funciona - você escreve o requisito e o teste.
- Evite **QA + DevOps** no mesmo cérebro: sobrecarrega demais no Estágio 3.

## 3 Prompts Exemplares

1. **(Chat)** "Para o requisito EARS 'Quando ciclo gerado, criar pagamentos para ATIVOS': gere 5 cenarios de teste cobrindo happy path, nenhum ativo, beneficiario suspenso, valor zero, e erro de banco."
2. **(Edits)** "No arquivo PaymentCycleServiceTest.java, adicione testes de integracao com Testcontainers que: inserem beneficiario, criam ciclo, geram pagamentos, e verificam valores."
3. **(Chat)** "Analise a cobertura atual dos testes e identifique os 3 caminhos mais criticos sem teste. Priorize pelo impacto no beneficiario."

## Se Você Ficar Travado (Defaults de Emergência)

- Não sabe JUnit 5? Copie o padrão de `CpfTest.java` - @Test, @DisplayName, AssertJ assertions.
- Testcontainers não funciona? Precisa de Docker rodando. Alternativa: teste unitário com Mockito.
- Muitos cenários, pouco tempo? Foque em 3: (a) criar beneficiário, (b) gerar pagamento, (c) mudança de status. São os críticos.
- CI vermelho? Rode `mvn test` local primeiro. Se passa local mas falha no CI, é problema de environment (Docker/Testcontainers).

## Dependências - Quem Depende de Você

| Persona | Relação | Artefato |
|---------|---------|----------|
| Requirements Engineer | VOCÊ depende dele | Requisitos testáveis com critérios |
| Developer | VOCÊ depende dele | Código para testar |
| Technical Lead | Depende de VOCÊ | Pipeline verde |
| DevOps Engineer | Depende de VOCÊ | CI confiável |

## Como Você É Avaliado

- Rubrica A3 (Integridade Técnica): testes passando, CI verde
- Rubrica A2 (Spec): cada requisito tem critério de verificação
- Critério: "Testes que quebram ao primeiro bug, não testes que passam sempre"

- Paula
