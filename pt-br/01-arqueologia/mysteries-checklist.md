<!-- markdownlint-disable MD013 MD025 MD026 MD028 MD029 MD034 MD040 MD051 MD060 -->

# Checklist de Mistérios do SIFAP

> Há **10 regras de negócio escondidas** e **3 easter eggs** plantados no código legado. Quanto mais seu time encontrar, melhor a nota na rubrica (dimensão A1).

## Por que isso existe

Em sistemas legados de verdade, regras de negócio críticas frequentemente ficam escondidas em código sem comentário, em constantes mágicas, em casos especiais sem justificativa. A facilitadora plantou 10 dessas armadilhas no SIFAP justamente para treinar o olhar do time. Quem aprende a achar mistérios no workshop, acha em produção.

## Como funciona

- Cada mistério vale 1–3 pontos dependendo da dificuldade
- Total possível: **32 pontos**
- Os mistérios estão distribuídos nos 15 programas .NSN e nos 4 DDMs
- Nenhum mistério está documentado em `legacy-docs/` (os docs estão desatualizados de propósito!)

## Regras de Negócio Escondidas (10)

Marque [x] quando encontrar:

- [ ] **MYS-001** (★★): Um programa modifica silenciosamente o status do beneficiário baseado em um critério demográfico. Onde? Por quê?
- [ ] **MYS-002** (★): Um limite numérico está hardcoded no código mas contradiz a capacidade definida no DDM. Qual é o limite? Em qual programa?
- [ ] **MYS-003** (★★★): Uma variável misteriosa é usada em cálculos mas nunca foi documentada — ninguém sabe de onde veio a constante. Qual variável?
- [ ] **MYS-004** (★★★): Em um mês específico do ano, o cálculo de benefício muda completamente. Qual mês? O que muda?
- [ ] **MYS-005** (★★★): O sistema usa uma técnica de arredondamento que causa perda sistemática de centavos. Qual técnica? Onde?
- [ ] **MYS-006** (★★): Um tipo de desconto ignora uma regra de limite que se aplica a todos os outros. Qual tipo? Por quê?
- [ ] **MYS-007** (★): Certos CPFs são aceitos sem validação real. Quais? Isso é um bug ou feature?
- [ ] **MYS-008** (★): Beneficiários de uma região específica pulam TODAS as verificações de elegibilidade. Qual região?
- [ ] **MYS-009** (★★): O processamento batch segue uma ordem que não é a mais lógica, mas que virou dependência de outros sistemas. Qual ordem?
- [ ] **MYS-010** (★★★): Um tipo de evento de auditoria é sistematicamente ocultado dos relatórios. Qual tipo? Isso é intencional ou bug?

## Easter Eggs (3)

- [ ] **EGG-001** (★): Um bloco de código comentado referencia uma política econômica dos anos 90 que nunca foi removida. Qual política?
- [ ] **EGG-002** (★): Um programa tem uma função de validação especial que aceita certos documentos sem verificação. Parece um backdoor de teste. Onde?
- [ ] **EGG-003** (★): Código morto referencia uma integração com uma empresa que não existe mais. Qual empresa?

## Inconsistências entre Documentação e Código (bônus)

- [ ] **INC-001**: Um limite documentado diverge do que o código permite
- [ ] **INC-002**: O documento de arquitetura original não menciona uma estrutura de dados que foi adicionada depois
- [ ] **INC-003**: Regras críticas de cálculo não aparecem em nenhum documento
- [ ] **INC-004**: Dois programas usam métodos de arredondamento diferentes para o mesmo tipo de valor

## Pontuação

| Faixa        | Classificação                           |
| ------------ | --------------------------------------- |
| 26–32 pontos | Excelente — arqueologia completa!       |
| 18–25 pontos | Sólido — bom trabalho de investigação   |
| 10–17 pontos | Satisfatório — encontrou o básico       |
| 0–9 pontos   | Precisa melhorar — explore mais a fundo |

## Dicas

- Use **Copilot Chat** para perguntar sobre cada programa: _"Tem alguma lógica escondida neste código? Existe alguma condição que parece um workaround ou caso especial não documentado?"_
- Compare o que a **documentação diz** com o que o **código faz** — as inconsistências são intencionais
- Os DDMs também contêm pistas em seus comentários
- Se travar, levante a mão — o facilitador pode dar uma dica calibrada após 90 minutos
