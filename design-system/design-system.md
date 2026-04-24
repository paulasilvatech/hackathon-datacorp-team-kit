---
title: "Design System, Hackathon DATACORP 2026"
description: "Documentação textual do design system aplicado ao Hackathon DATACORP 2026, baseado na paleta Microsoft com semântica de modernização agêntica de legado"
author: "Paula Silva, Americas Software GBB, Microsoft"
date: "2026-04-23"
version: "1.0.1"
status: "approved"
related:
  - design-system/tokens.json
  - design-system/hackathon-datacorp-design-system.html
  - design-system/dist/tokens.css
  - design-system/dist/tailwind.config.js
tags: ["design-system", "hackathon", "DATACORP", "microsoft-palette", "modernization"]
---

## Change Log

| Versão | Data | Autor | Mudanças |
|--------|------|-------|----------|
| 1.0.0 | 2026-04-18 | Paula Silva, Americas Software GBB, Microsoft | Primeira versão do Design System, gerada a partir do showcase HTML e do tokens.json via Copilot |

---

## Sumário

1. [Introdução](#introdução)
2. [Filosofia e princípios](#filosofia-e-princípios)
3. [Semântica das 4 cores](#semântica-das-4-cores)
4. [Tokens de cor](#tokens-de-cor)
5. [Tipografia](#tipografia)
6. [Espaçamento](#espaçamento)
7. [Componentes base](#componentes-base)
8. [Componentes específicos do hackathon](#componentes-específicos-do-hackathon)
9. [Variante escura, slide divisor](#variante-escura-slide-divisor)
10. [Aplicação por estágio do Dia 2](#aplicação-por-estágio-do-dia-2)
11. [Como consumir o design system](#como-consumir-o-design-system)
12. [Regras de governança](#regras-de-governança)
13. [Glossário](#glossário)
14. [Referências](#referências)

---

## Introdução

Este documento é a ponte textual do Design System do Hackathon DATACORP 2026. Ele explica o sistema em linguagem humana: os princípios que guiam as decisões, a semântica por trás de cada escolha visual, as regras de uso dos componentes, e o porquê de cada token existir do jeito que existe. Se você já leu o `tokens.json` e achou árido demais, este é o lugar para entender o raciocínio. Se você abriu o `hackathon-datacorp-design-system.html` e ficou curioso sobre a lógica, também é aqui.

O design system opera em quatro camadas. A Camada 1 é o `tokens.json`, a fonte de verdade programática: todos os valores primitivos vivem ali, e nenhum outro arquivo inventa números por conta própria. A Camada 2 é este documento, que explica o sistema em prosa. A Camada 3 é o showcase HTML (`hackathon-datacorp-design-system.html`), que demonstra visualmente cada decisão. A Camada 4 compreende os arquivos derivados (`tokens.css` e `tailwind.config.js`), que traduzem os tokens em formatos consumíveis por código. Cada camada tem um público principal, e nenhuma substitui as outras.

O design system atende a três públicos ao mesmo tempo. Desenvolvedores vão encontrar aqui os tokens que precisam importar e as regras de composição dos componentes. Designers e criadores de conteúdo vão encontrar a semântica das cores, os princípios de uso, e a lógica de aplicação em slides, handouts e materiais de time. IAs agênticas (GitHub Copilot, Claude Code, e o Cowork Blueprint) vão encontrar uma especificação textual autoritativa que guia a geração de artefatos visuais e documentos coerentes com o sistema.

---

## Filosofia e princípios

Antes de mergulhar nos tokens, vale entender as quatro ideias que governam o sistema. Cada regra de uso dos componentes, cada escolha de cor, e cada decisão tipográfica tem origem em um desses princípios. Quando surgir dúvida sobre como aplicar o design system, volte aqui.

### 2.1 Cor é semântica

As quatro cores Microsoft não são acentos decorativos escolhidos por estética. Cada uma carrega um significado fixo no contexto de modernização agêntica de legado. Vermelho é legado. Verde é moderno. Azul é tooling. Amarelo é agentes. Usar uma dessas cores fora da sua semântica quebra o sistema, porque confunde quem está lendo o artefato sobre o que ele está olhando. Um slide sobre agentes com eyebrow vermelho manda o sinal errado, mesmo que visualmente pareça OK.

### 2.2 Um acento dominante por slide ou artefato

Cada artefato (slide, handout, pôster de sala, card de time) deve ter uma cor de acento dominante, escolhida conforme o tema principal do conteúdo. As outras três cores Microsoft podem aparecer em pills, badges, e marcadores menores, mas apenas quando esses elementos carregam o significado semântico correto da cor. Misturar os quatro acentos em proporções iguais num único slide dilui a identidade e elimina o benefício do sistema semântico.

### 2.3 Neutros fazem o trabalho pesado

Texto, linhas divisórias, fundos e superfícies são sempre neutros: `color.neutral.ink` para texto primário (`#1A1A1A`), `color.neutral.bg` para fundos (`#F7F7F5`), `color.neutral.rule` para separadores (`#E5E5E0`). As quatro cores Microsoft entram como marcadores pontuais: eyebrows, pills, barras coloridas no topo de cards, big numbers de destaque. Elas nunca ocupam áreas grandes de um artefato. Isso garante que o sistema permaneça legível e que o acento tenha impacto visual real quando aparece.

### 2.4 Legacy e Modern têm dualidade posicional

Quando um artefato compara o sistema legado e o sistema moderno lado a lado, o legado vai à esquerda e o moderno vai à direita. O legado é associado ao vermelho (MS-RED, `#F25022`) e o moderno ao verde (MS-GREEN, `#7FBA00`). Essa direção não se inverte, porque a leitura ocidental vai da esquerda para a direita e isso reforça a narrativa temporal: vínhamos de lá (legado, esquerda, passado) e estamos indo para cá (moderno, direita, futuro). O componente Legacy vs Modern split implementa essa regra estruturalmente.

---

## Semântica das 4 cores

Esta é a seção central do design system. Tudo que aparece visualmente nos artefatos do hackathon tem uma justificativa que começa aqui. Cada cor tem papel fixo, e conhecer esse papel é o que diferencia quem está aplicando o sistema de quem está apenas usando cores bonitas.

### 3.1 Vermelho, MS-RED, `#F25022`

O vermelho representa o sistema SIFAP na sua forma original: escrito em Natural com banco Adabas, em produção desde 1997, com décadas de dívida técnica acumulada. É a cor da arqueologia digital, dos gaps de documentação, das regras de negócio escondidas em subrotinas sem comentário, das limitações do 4GL que ninguém mais consegue explicar, da equipe original que já se aposentou. Quando você vê vermelho num artefato do hackathon, está olhando para algo que pertence ao passado que está sendo modernizado.

O vermelho também carrega a dimensão do risco e da atenção. Big numbers mostrando LOC de código Natural, tempo acumulado de manutenção, cobertura de testes próxima de zero, regras de negócio sem especificação formal: todos esses contextos pedem vermelho. Não porque o legado seja errado (ele funciona e está em produção), mas porque ele representa o ponto de partida que precisa de cuidado e atenção durante a transição.

**Quando usar:**
- Eyebrows de slides sobre o Estágio 1, Arqueologia Digital
- Pills marcando `legacy`, `Natural`, `Adabas`, `SIFAP 1.0`
- Big numbers de dívida técnica (LOC, tempo de manutenção, cobertura zero)
- Componente Legacy vs Modern split, lado esquerdo
- Stage cards do Estágio 1 (barra superior vermelha)
- Indicadores de gap ou risco em qualquer estágio

**Quando não usar:**
- Slides sobre ferramentas modernas ou stack de reconstrução
- Indicadores de sucesso, gate criteria atingido, testes passando
- Contextos sobre agentes de IA ou prompts

**Exemplos no hackathon:**
- Slide de abertura do Estágio 1 com eyebrow `ESTÁGIO 01 · ARQUEOLOGIA DIGITAL` em MS-RED
- Card mostrando `287.000 LOC` em Natural com big number vermelho
- Pill `legacy` ao lado do nome de um módulo do SIFAP 1.0

### 3.2 Verde, MS-GREEN, `#7FBA00`

O verde representa o SIFAP 2.0 que os times vão construir durante o hackathon: Java Spring Boot 3, Next.js 15, PostgreSQL 16, arquitetura Modular Monolith com bounded contexts bem definidos. É a cor do código moderno entregue, dos testes passando na pipeline do GitHub Actions, do Docker Compose rodando localmente sem erro, do deploy no Azure confirmado, do gate criteria atingido no Estágio 3.

Verde é a cor da chegada, não da jornada. Ela aparece quando algo foi validado, entregue, ou confirmado como correto. Durante o Estágio 3 (Reconstrução), que é o estágio mais longo do Dia 2, o verde vai dominar os artefatos porque é o momento em que os times estão ativamente construindo o sistema moderno.

**Quando usar:**
- Eyebrows de slides sobre reconstrução e entrega
- Status de build verde, pipeline passando, testes OK
- Pills de entregáveis validados: `Spring Boot`, `PostgreSQL`, `SIFAP 2.0`
- Stage cards do Estágio 3 (barra superior verde)
- Componente Legacy vs Modern split, lado direito
- Gate criteria atingido, feature mergeada, bounded context extraído

**Quando não usar:**
- Slides de diagnóstico ou arqueologia do sistema legado
- Contextos sobre agentes ou prompts (esses são amarelos)
- Indicadores de risco ou gap

**Exemplos no hackathon:**
- Slide de abertura do Estágio 3 com eyebrow `ESTÁGIO 03 · RECONSTRUÇÃO` em MS-GREEN
- Pill `Java Spring Boot 3` em verde ao lado de um módulo reconstruído
- Big number mostrando cobertura de testes atingida no gate criteria

### 3.3 Azul, MS-BLUE, `#00A4EF`

O azul representa o tooling que os devs DATACORP vão usar durante os dois dias: VS Code com extensões, GitHub Copilot nos três modos (Chat, Edits, Agent), Docker para containerização local, Terraform para infraestrutura como código, GitHub Actions para CI/CD, Azure como plataforma de deploy. É a cor da superfície onde o trabalho acontece, não do trabalho em si.

A distinção entre azul (tooling) e amarelo (agentes) é importante. Copilot como produto e plataforma é azul. Os prompts, skills, e instructions personalizados que os times constroem durante o hackathon são amarelos. O Estágio 2 (Spec Greenfield) usa azul como cor dominante porque é o momento em que os times estão aprendendo a usar as ferramentas de especificação, incluindo o Specky como plugin SDD.

**Quando usar:**
- Pills de ferramenta: `VS Code`, `GitHub Copilot`, `Docker`, `Terraform`, `Azure`
- Eyebrows de slides sobre tooling e infraestrutura
- Referências ao Estágio 2, Spec Greenfield
- Stage cards do Estágio 2 (barra superior azul)
- Elementos que representam a plataforma de desenvolvimento

**Quando não usar:**
- Slides sobre o sistema legado ou arqueologia
- Contextos de agentes personalizados, prompts, ou skills desenvolvidas pelos times
- Indicadores de entrega ou sucesso (esses são verdes)

**Exemplos no hackathon:**
- Slide de abertura do Estágio 2 com eyebrow `ESTÁGIO 02 · SPEC GREENFIELD` em MS-BLUE
- Pills `GitHub Actions`, `Docker`, `Azure` em azul num slide de arquitetura de entrega
- Persona pills com dot azul para arquitetos e tech leads

### 3.4 Amarelo, MS-YELLOW, `#FFB900`

O amarelo representa os 13 agentes do framework Agentic Legacy Modernization, o Specky como plugin SDD central, os prompts que os times vão usar e criar, as skills e instructions configuradas no Copilot, e toda a camada de inteligência artificial do hackathon. É a cor da orquestração agêntica, do pensamento automatizado, da IA que amplifica o trabalho dos devs.

O Estágio 4 (Evolução com Agent) usa amarelo como cor dominante porque é o momento em que os times aplicam agents para evoluir o SIFAP 2.0 além do que conseguiriam manualmente. O amarelo também é a cor padrão dos eyebrows sobre dark background (slides divisores), porque o contraste amarelo sobre preto é o mais dramático do sistema.

**Quando usar:**
- Eyebrows de slides sobre agentes e IA
- Pills marcando `@agent`, `prompt`, `skill`, `SDD`
- Blocos descrevendo os 13 agentes do framework
- Stage cards do Estágio 4 (barra superior amarela)
- Eyebrows em slides com dark variant (divisores de estágio)
- Agent blocks com ícone no slot amarelo

**Quando não usar:**
- Contextos de entrega ou reconstrução (esses são verdes)
- Slides sobre tooling genérico como Docker ou Terraform (esses são azuis)
- Indicadores de risco ou legado

**Exemplos no hackathon:**
- Slide de abertura do Estágio 4 com eyebrow `ESTÁGIO 04 · EVOLUÇÃO COM AGENT` em MS-YELLOW
- Agent block mostrando o `@discovery-agent` com ícone no slot amarelo
- Pill `@specky` em amarelo num slide sobre SDD

---

## Tokens de cor

Esta seção lista todos os tokens de cor do sistema, organizados por grupo. Os valores aqui são exatamente os mesmos do `tokens.json`. Sempre que você precisar de um valor de cor para código, consulte o `tokens.json` diretamente: ele é a fonte de verdade. Este documento usa os mesmos valores para que a referência seja completa mesmo fora do IDE.

### 4.1 Grupo `color.ms`, paleta Microsoft

| Token | Valor | Descrição |
|-------|-------|-----------|
| `color.ms.red.50` | `#FFF0EB` | Red background wash, fundos tênues e badges de legado |
| `color.ms.red.100` | `#FFD6C7` | Red soft tint, superfícies de hover e labels de atenção |
| `color.ms.red.500` | `#F25022` | Red base, acento primário de legado e gaps |
| `color.ms.red.700` | `#B33816` | Red deep, texto sobre fundos claros e hover states |
| `color.ms.green.50` | `#F1F8E3` | Green background wash, fundos tênues de sucesso |
| `color.ms.green.100` | `#D8EDA5` | Green soft tint, superfícies de sucesso e badges de moderno |
| `color.ms.green.500` | `#7FBA00` | Green base, acento de moderno e sucesso |
| `color.ms.green.700` | `#5A8500` | Green deep, texto sobre fundos claros |
| `color.ms.blue.50` | `#E5F6FD` | Blue background wash, fundos tênues de tooling |
| `color.ms.blue.100` | `#B8E5FA` | Blue soft tint, superfícies de referência a ferramentas |
| `color.ms.blue.500` | `#00A4EF` | Blue base, acento de tooling e Copilot |
| `color.ms.blue.700` | `#0076AC` | Blue deep, texto sobre fundos claros |
| `color.ms.yellow.50` | `#FFF7E0` | Yellow background wash, fundos tênues de agentes |
| `color.ms.yellow.100` | `#FFE79C` | Yellow soft tint, superfícies de destaque de agentes |
| `color.ms.yellow.500` | `#FFB900` | Yellow base, acento de agentes e IA |
| `color.ms.yellow.700` | `#B88500` | Yellow deep, texto sobre fundos claros |
| `color.ms.gray` | `#737373` | Microsoft wordmark gray, contextos de referência à marca |

### 4.2 Grupo `color.neutral`, escala neutra

| Token | Valor | Descrição |
|-------|-------|-----------|
| `color.neutral.ink` | `#1A1A1A` | Texto primário, títulos, conteúdo dominante |
| `color.neutral.ink-2` | `#3A3A3A` | Texto secundário, subtítulos, conteúdo de apoio |
| `color.neutral.ink-3` | `#737373` | Texto terciário, captions, metadados |
| `color.neutral.paper` | `#FFFFFF` | Fundo de card, superfícies internas |
| `color.neutral.bg` | `#F7F7F5` | Fundo de slide, página, superfície externa |
| `color.neutral.bg-alt` | `#ECECE8` | Fundo alternativo, zona de separação |
| `color.neutral.rule` | `#E5E5E0` | Linhas divisórias sutis |
| `color.neutral.rule-2` | `#CECEC7` | Linhas divisórias fortes, bordas de card |

### 4.3 Grupo `color.semantic`, aliases semânticos

Os tokens semânticos referenciam os tokens base via aliases (`{color.ms.red.500}`). Eles existem para que o código fale sobre intenção (`color.semantic.legacy`) em vez de falar sobre pigmento (`color.ms.red.500`). Use os tokens semânticos sempre que possível em componentes e templates.

| Token | Referência | Descrição |
|-------|-----------|-----------|
| `color.semantic.legacy` | `{color.ms.red.500}` | Cor do legado SIFAP, Natural, Adabas, dívida técnica |
| `color.semantic.modern` | `{color.ms.green.500}` | Cor do moderno SIFAP 2.0, Spring Boot, PostgreSQL |
| `color.semantic.tooling` | `{color.ms.blue.500}` | Cor do tooling, Copilot, VS Code, Docker, Azure |
| `color.semantic.agent` | `{color.ms.yellow.500}` | Cor dos agentes IA, Specky, SDD, prompts |
| `color.semantic.accent` | `{color.ms.red.500}` | Acento primário default do design system |
| `color.semantic.accent-ink` | `{color.ms.red.700}` | Acento hover e texto, variante escura |

### 4.4 Grupo `color.dark`, paleta de variante escura

| Token | Valor | Descrição |
|-------|-------|-----------|
| `color.dark.bg` | `#141414` | Fundo de slide dark, divisor de estágio |
| `color.dark.surface` | `#1C1C1A` | Card ou bloco sobre fundo dark |
| `color.dark.ink` | `#F0F0F0` | Texto primário sobre dark |
| `color.dark.ink-2` | `#C7C7C2` | Texto secundário sobre dark |
| `color.dark.ink-3` | `#999995` | Texto terciário sobre dark |
| `color.dark.rule` | `#2E2E2A` | Linhas divisórias sobre dark |

---

## Tipografia

A tipografia do design system foi escolhida para funcionar em dois contextos muito específicos: slides projetados em tela grande para grupos (1920x1080, vistas de 4 a 6 metros) e documentos densos lidos em tela. Inter cuida do conteúdo, JetBrains Mono cuida da marcação. A combinação cria uma hierarquia visual clara sem precisar de muito peso extra ou ornamento.

### 5.1 Famílias

**Inter** (`typography.family.sans`) é a família principal, usada em títulos, subtítulos, corpo de texto, e qualquer conteúdo que precisa ser lido com fluência. É otimizada para telas e tem excelente legibilidade em tamanhos grandes e médios.

**JetBrains Mono** (`typography.family.mono`) é a família monoespaçada, usada em eyebrows, numbers em contexto de metadado, código, tokens, e qualquer elemento que funciona como marcação ou etiqueta. O caráter técnico do mono comunica "isso é dado estruturado", diferenciando visualmente marcadores de conteúdo.

### 5.2 Pesos disponíveis

O sistema usa cinco pesos, todos de Inter (JetBrains Mono usa os pesos 400, 500 e 600):

| Token | Valor | Uso típico |
|-------|-------|------------|
| `typography.weight.light` | 300 | Big number stats em slides |
| `typography.weight.regular` | 400 | Corpo de texto, subtítulos, captions |
| `typography.weight.medium` | 500 | Títulos principais, eyebrows, names em cards |
| `typography.weight.semibold` | 600 | Labels de ênfase, ícones de agentes em mono |
| `typography.weight.bold` | 700 | Uso reservado para destaques pontuais |

### 5.3 Escala tipográfica

A escala foi calibrada para slides 1920x1080. A regra principal: nunca abaixo de 24px em qualquer elemento de slide. Em sala de workshop, o slide é projetado a pelo menos 4 metros do público, e tipografia menor que 24px vira ilegível para qualquer pessoa sentada além da segunda fileira.

| Nível | Token | Tamanho | Line height | Tracking | Peso | Família | Uso |
|-------|-------|---------|-------------|----------|------|---------|-----|
| Título | `typography.scale.title` | 72px | 1.02 | -0.02em | 500 | Inter | Título principal de slide |
| Subtítulo | `typography.scale.subtitle` | 44px | 1.15 | -0.015em | 400 | Inter | Subtítulo de slide, texto destacado |
| Corpo | `typography.scale.body` | 30px | 1.35 | 0 | 400 | Inter | Corpo de texto padrão em slide |
| Pequeno | `typography.scale.small` | 24px | 1.4 | 0 | 400 | Inter | Texto pequeno, captions, legendas |
| Eyebrow | `typography.scale.eyebrow` | 24px | 1.2 | 0.12em | 500 | JetBrains Mono | Eyebrow, marcação de categoria, sempre uppercase |
| Big number | `typography.scale.big-num` | 240px | 0.9 | -0.04em | 300 | Inter | Big number stat, destaque numérico |
| Título de seção | `typography.scale.section-title` | 160px | 0.95 | -0.035em | 500 | Inter | Título de slide divisor dark |

O eyebrow merece uma nota especial: ele usa JetBrains Mono com letra-spacing larga (0.12em) e uppercase porque precisa funcionar como rótulo de categoria, não como título. Quando você vê `ESTÁGIO 01 · ARQUEOLOGIA DIGITAL` no topo de um slide, o eyebrow sinaliza: "este é o contexto do que vem a seguir", sem competir visualmente com o título principal.

---

## Espaçamento

O sistema usa uma régua base de 8px. Todos os tokens de espaçamento são múltiplos ou composições desse valor base, o que garante que qualquer combinação de tokens resulte em alinhamentos coerentes. Essa é a mesma régua usada no Portal Gov QA e outros projetos da Paula Silva, criando consistência entre sistemas diferentes.

| Token | Valor | Uso típico |
|-------|-------|------------|
| `spacing.xs` | 8px | Gap entre elementos muito próximos, margem de dot |
| `spacing.sm` | 16px | Padding interno de pills e chips |
| `spacing.md` | 28px | Gap entre cards e itens de lista, padding de stage card |
| `spacing.lg` | 48px | Padding interno de blocks e cards |
| `spacing.xl` | 80px | Padding vertical de slide (topo e base) |
| `spacing.2xl` | 120px | Padding extra grande para slides com muito respiro |

Para referência rápida: o slide padrão (1920x1080) usa `spacing.xl` (80px) como padding vertical e 100px como padding horizontal (definido diretamente nos metadados em `meta.slide-dimensions.padding-horizontal`). O gap entre cards numa grade usa `spacing.md` (28px). O padding interno de um block card usa `spacing.lg` (48px) aproximado para 36px conforme especificado em `component.block.padding`.

---

## Componentes base

Os componentes base são os blocos de construção que aparecem em praticamente todos os artefatos do hackathon. Cada um tem uma função específica e consome um conjunto definido de tokens. Entender quando usar cada um é mais importante do que memorizar os tokens: a função guia a escolha.

### 7.1 Eyebrow, marcação de categoria

O eyebrow é o rótulo que aparece acima do título principal de um slide ou de um bloco de conteúdo. Ele responde à pergunta: "qual é o contexto ou categoria deste conteúdo?" Nunca é o conteúdo principal em si.

**Quando usar:** Para identificar o estágio atual (Arqueologia, Spec, Reconstrução, Evolução), a categoria do slide (legado, moderno, tooling, agente), ou o bounded context sendo discutido.

**Estrutura:**
```html
<div class="eyebrow" style="
  font-family: 'JetBrains Mono', monospace;
  font-size: 24px;
  letter-spacing: 0.12em;
  text-transform: uppercase;
  font-weight: 500;
  color: var(--ms-red);
">ESTÁGIO 01 · ARQUEOLOGIA DIGITAL</div>
```

**Tokens consumidos:** `typography.scale.eyebrow`, `typography.family.mono`, `color.semantic.legacy` (ou outra cor semântica conforme contexto).

### 7.2 Pill, chip de categorização

O pill é um chip compacto que categoriza um elemento: uma ferramenta, um estágio, um tipo de artefato, um módulo do sistema. Ele usa borda colorida sem preenchimento de fundo (exceto neutro), o que permite empilhar múltiplos pills sem criar ruído visual.

**Quando usar:** Para etiquetar ferramentas, bounded contexts, tipos de entregável, ou qualquer categoria que precisa aparecer inline com texto.

**Estrutura:**
```html
<span class="pill" style="
  display: inline-flex;
  padding: 8px 18px;
  border: 1px solid var(--ms-red);
  color: var(--ms-red);
  font-family: 'JetBrains Mono', monospace;
  font-size: 22px;
  border-radius: 4px;
  background: #FFFFFF;
">legacy</span>
```

**Tokens consumidos:** `component.pill.padding`, `component.pill.font-family`, `component.pill.font-size`, `component.pill.variant.red` (ou outra variante).

### 7.3 Block, card informativo

O block é o card de conteúdo padrão do sistema. Tem um label de categoria em mono (usando a cor semântica), um nome em Inter medium, e uma descrição em ink-3. Serve para apresentar qualquer entidade estruturada: agente, módulo, persona, ferramenta.

**Quando usar:** Para apresentar elementos que têm nome, descrição, e categoria (bounded context, módulo do sistema, agente, ferramenta).

**Estrutura:**
```html
<div class="block" style="
  border: 1px solid #CECEC7;
  padding: 36px 40px;
  background: #FFFFFF;
  display: flex;
  flex-direction: column;
  gap: 12px;
">
  <div style="font-family: 'JetBrains Mono', monospace; font-size: 18px; color: #F25022; text-transform: uppercase; letter-spacing: 0.1em; font-weight: 500;">BOUNDED CONTEXT</div>
  <div style="font-size: 34px; font-weight: 500; color: #1A1A1A;">Gestão de Contratos</div>
  <div style="font-size: 20px; color: #737373; line-height: 1.4;">Módulo responsável pelo ciclo de vida de contratos de auxílio rural.</div>
</div>
```

**Tokens consumidos:** `component.block.padding`, `component.block.background`, `component.block.border-color`, `component.block.label-color`, `component.block.name-font-size`, `component.block.desc-color`.

### 7.4 Big number stat, destaque numérico

O big number stat destaca um número com impacto máximo, seguido de um label de contexto em mono. É o componente de dados quantitativos do sistema, criado para slides onde um número precisa ser o centro da atenção.

**Quando usar:** Para mostrar LOC de código Natural, tempo de manutenção acumulado, cobertura de testes, número de bounded contexts extraídos, ou qualquer métrica que merece destaque visual.

**Estrutura:**
```html
<div class="stat">
  <div style="font-size: 240px; font-weight: 300; letter-spacing: -0.04em; line-height: 0.9; color: #F25022;">287K</div>
  <div style="font-family: 'JetBrains Mono', monospace; font-size: 16px; color: #737373; letter-spacing: 0.1em; text-transform: uppercase; margin-top: 10px;">LINHAS DE CÓDIGO NATURAL</div>
</div>
```

**Tokens consumidos:** `typography.scale.big-num`, `typography.family.mono`, `color.semantic.legacy` (para números de legado), `color.neutral.ink-3` (para o label).

### 7.5 Tabela, para listas estruturadas

A tabela segue o estilo do próprio design system: sem zebra striping colorido, bordas neutras, cabeçalho em mono medium, células em Inter regular. O objetivo é legibilidade máxima, não decoração.

**Quando usar:** Para listas comparativas, mapeamentos de módulos para bounded contexts, inventário de agentes, ou qualquer dado que tenha dimensões múltiplas.

**Tokens consumidos:** `color.neutral.rule`, `color.neutral.rule-2`, `typography.family.mono`, `typography.family.sans`, `color.neutral.ink`, `color.neutral.ink-3`.

---

## Componentes específicos do hackathon

Estes quatro componentes existem exclusivamente no contexto do Hackathon DATACORP 2026. Eles encapsulam padrões de informação que se repetem durante os dois dias do evento e que precisam de consistência visual para funcionar bem em materiais de sala, handouts, e slides.

### 8.1 Stage card, os 4 estágios do Dia 2

O stage card representa um dos quatro estágios do Dia 2 do hackathon. Tem uma barra colorida no topo (6px, a cor do estágio), número do estágio em mono, nome do estágio, horário, e descrição curta. É o componente mais usado nos materiais de sala.

**Quando usar:** Em slides de overview do Dia 2, em handouts de time, em pôsteres de sala que mostram o cronograma.

**Estrutura:**
```html
<div class="stage-card" style="
  border: 1px solid #E5E5E0;
  border-top: 6px solid #F25022;
  background: #FFFFFF;
  padding: 28px;
">
  <div style="font-family: 'JetBrains Mono', monospace; font-size: 14px; color: #F25022; letter-spacing: 0.1em; text-transform: uppercase; margin-bottom: 12px;">ESTÁGIO 01</div>
  <div style="font-size: 26px; font-weight: 500; color: #1A1A1A; margin-bottom: 8px;">Arqueologia Digital</div>
  <div style="font-family: 'JetBrains Mono', monospace; font-size: 16px; color: #737373; margin-bottom: 16px;">09:00 a 12:00</div>
  <div style="font-size: 18px; color: #737373; line-height: 1.4;">Entender o que o SIFAP faz antes de tocar no código.</div>
</div>
```

**Tokens consumidos:** `component.stage-card.padding`, `component.stage-card.border-top-width`, `component.stage-card.border-top-color.stage-1` (ou stage-2/3/4), `component.stage-card.background`, `component.stage-card.border-color`.

### 8.2 Persona pill, as 10 personas dos times

O persona pill identifica a persona de um membro de time. Tem um dot colorido (a cor do cluster da persona), o nome da persona, e usa Inter medium. As 10 personas são agrupadas em quatro clusters: product (vermelho), architect (azul), build (verde), ops (amarelo).

**Quando usar:** Em slides de composição de time, em handouts de times, em materiais que listam as personas envolvidas num estágio.

**Estrutura:**
```html
<span class="persona-pill" style="
  display: inline-flex;
  align-items: center;
  gap: 10px;
  padding: 10px 18px;
  border: 1px solid #CECEC7;
  background: #FFFFFF;
  font-family: 'Inter', sans-serif;
  font-size: 20px;
  font-weight: 500;
  border-radius: 4px;
  color: #1A1A1A;
">
  <span style="width: 8px; height: 8px; border-radius: 50%; background: #00A4EF; display: inline-block;"></span>
  Tech Lead
</span>
```

**Tokens consumidos:** `component.persona-pill.padding`, `component.persona-pill.border-radius`, `component.persona-pill.font-size`, `component.persona-pill.dot-size`, `component.persona-pill.dot-color.architect` (ou product/build/ops).

### 8.3 Agent block, os 13 agentes do framework

O agent block representa um dos 13 agentes do framework Agentic Legacy Modernization. Tem um slot de ícone com fundo amarelo claro e borda amarela (onde vai um emoji ou sigla do agente), o nome canônico do agente em mono amarelo, e a descrição do papel do agente em Inter.

**Quando usar:** Em slides que apresentam o framework de agentes, em handouts sobre o Estágio 4, em qualquer material que lista agentes disponíveis para os times.

**Estrutura:**
```html
<div class="agent-block" style="
  display: grid;
  grid-template-columns: 60px 1fr;
  gap: 20px;
  align-items: start;
  border: 1px solid #CECEC7;
  background: #FFFFFF;
  padding: 24px 28px;
">
  <div style="width: 52px; height: 52px; background: #FFF7E0; border: 1px solid #FFB900; display: flex; align-items: center; justify-content: center; font-family: 'JetBrains Mono', monospace; color: #B88500; font-weight: 600;">🔍</div>
  <div>
    <div style="font-family: 'JetBrains Mono', monospace; font-size: 20px; color: #B88500; letter-spacing: 0.08em; text-transform: uppercase; font-weight: 500; margin-bottom: 6px;">@DISCOVERY-AGENT</div>
    <div style="font-size: 24px; font-weight: 500; color: #1A1A1A; margin-bottom: 4px;">Discovery Agent</div>
    <div style="font-size: 18px; color: #737373; line-height: 1.4;">Mapeia o código Natural para identificar bounded contexts e regras de negócio implícitas.</div>
  </div>
</div>
```

**Tokens consumidos:** `component.agent-block.padding`, `component.agent-block.icon-slot-size`, `component.agent-block.icon-slot-background`, `component.agent-block.icon-slot-border`, `component.agent-block.title-color`.

### 8.4 Legacy vs Modern split, dualidade visual SIFAP

O split é o componente que coloca legado e moderno lado a lado numa divisão 50/50. Legado sempre à esquerda (fundo avermelhado suave, label em `color.ms.red.700`), moderno sempre à direita (fundo esverdeado suave, label em `color.ms.green.700`). A direção não inverte: leitura da esquerda para direita reflete a jornada temporal do hackathon.

**Quando usar:** Em slides que comparam o SIFAP 1.0 e o SIFAP 2.0 diretamente, em handouts de bounded context que mostram o módulo legado e o equivalente moderno.

**Estrutura:**
```html
<div class="split" style="display: grid; grid-template-columns: 1fr 1fr; border: 1px solid #E5E5E0;">
  <div style="padding: 36px 40px; background: #FAF4F2; border-right: 1px solid #E5E5E0;">
    <div style="font-family: 'JetBrains Mono', monospace; font-size: 16px; letter-spacing: 0.12em; text-transform: uppercase; font-weight: 500; color: #B33816; margin-bottom: 16px;">LEGADO · SIFAP 1.0</div>
    <div style="font-size: 32px; font-weight: 500; color: #1A1A1A; margin-bottom: 12px;">Módulo CONTRATO</div>
    <div style="font-family: 'JetBrains Mono', monospace; font-size: 18px; color: #737373; margin-bottom: 20px;">Natural 4GL, Adabas, 4.200 LOC</div>
    <div style="font-size: 20px; color: #3A3A3A; line-height: 1.45;">Lógica de negócio misturada com persistência. Zero testes. Documentação desatualizada desde 2003.</div>
  </div>
  <div style="padding: 36px 40px; background: #F4F8E8;">
    <div style="font-family: 'JetBrains Mono', monospace; font-size: 16px; letter-spacing: 0.12em; text-transform: uppercase; font-weight: 500; color: #5A8500; margin-bottom: 16px;">MODERNO · SIFAP 2.0</div>
    <div style="font-size: 32px; font-weight: 500; color: #1A1A1A; margin-bottom: 12px;">Bounded Context: Contratos</div>
    <div style="font-family: 'JetBrains Mono', monospace; font-size: 18px; color: #737373; margin-bottom: 20px;">Spring Boot 3, PostgreSQL 16, 87% cobertura</div>
    <div style="font-size: 20px; color: #3A3A3A; line-height: 1.45;">Domínio isolado com testes de integração. Documentação gerada via Specky. Deploy automatizado.</div>
  </div>
</div>
```

**Tokens consumidos:** `color.ms.red.700`, `color.ms.green.700`, `color.neutral.rule`, `color.neutral.ink`, `color.neutral.ink-2`, `color.neutral.ink-3`, `spacing.lg`.

---

## Variante escura, slide divisor

A variante escura existe para um caso específico: slides de transição entre estágios e divisores conceituais de grande impacto. Não é o estilo padrão do sistema, que é claro. É uma quebra intencional de ritmo que sinaliza: "estamos passando para um novo capítulo".

O fundo dark usa `color.dark.bg` (`#141414`). Superfícies sobre o fundo usam `color.dark.surface` (`#1C1C1A`). O texto primário é `color.dark.ink` (`#F0F0F0`), texto secundário `color.dark.ink-2` (`#C7C7C2`), texto terciário `color.dark.ink-3` (`#999995`). Linhas divisórias usam `color.dark.rule` (`#2E2E2A`).

O eyebrow padrão sobre dark é em MS-YELLOW (`#FFB900`). A razão é contraste: amarelo sobre preto tem o maior contraste dos quatro acentos e cria o efeito dramático correto para uma slide de transição. O título principal em slides dark usa `typography.scale.section-title` (160px, weight 500, tracking -0.035em), que preenche a tela com impacto máximo.

**Quando usar a variante dark:**
- Slides divisores de estágio (abrindo cada um dos 4 estágios do Dia 2)
- Transições conceituais que marcam uma mudança de tema importante
- Slides de quote ou declaração de princípio que precisam de destaque

**Quando não usar:**
- Conteúdo instrucional regular (manter fundo claro para legibilidade)
- Slides com muito texto ou tabelas (o contraste dark é ótimo para impacto, não para densidade de informação)

---

## Aplicação por estágio do Dia 2

Esta tabela é o mapa operacional do design system durante o Dia 2 do hackathon (28 de abril). Cada estágio tem uma cor dominante, e esse mapeamento determina como os materiais de sala são diferenciados visualmente. Os facilitadores conseguem identificar em qual estágio estão só de olhar para a cor do slide.

| Estágio | Horário | Cor dominante | Token | Aplicação nos artefatos |
|---------|---------|---------------|-------|------------------------|
| 01 Arqueologia Digital | 09:00 a 12:00 | MS-RED | `color.ms.red.500` (#F25022) | Eyebrows de slides em vermelho, big numbers de dívida técnica, pills `legacy`, `Natural`, `Adabas`, barra do stage card vermelha, pôster de sala com acento vermelho |
| 02 Spec Greenfield | 13:00 a 14:00 | MS-BLUE | `color.ms.blue.500` (#00A4EF) | Eyebrows em azul, pills de ferramentas (`Specky`, `GitHub Copilot`, `VS Code`), referências ao SDD, barra do stage card azul, materiais sobre a Specify Phase |
| 03 Reconstrução | 14:00 a 17:00 | MS-GREEN | `color.ms.green.500` (#7FBA00) | Eyebrows em verde, pills de entregáveis validados (`Spring Boot`, `PostgreSQL`), big numbers de cobertura e LOC moderno, barra do stage card verde, checklist de gate criteria |
| 04 Evolução com Agent | 17:00 a 18:30 | MS-YELLOW | `color.ms.yellow.500` (#FFB900) | Eyebrows em amarelo, agent blocks dos 13 agentes, pills `@agent`, `prompt`, `skill`, barra do stage card amarela, slides de apresentação final |

Os horários acima são os horários do Dia 2 e estão fixados nos tokens em `meta.stage-map`. Qualquer artefato que referencia estágios deve usar esses horários exatos.

---

## Como consumir o design system

O design system tem quatro camadas, e cada consumidor tem um ponto de entrada diferente. Esta seção explica o caminho correto para cada tipo de uso.

### 11.1 Para desenvolvedores frontend (Next.js do protótipo SIFAP 2.0)

Importe o `tailwind.config.js` da Camada 4 no seu projeto Next.js. Ele expõe todos os tokens como classes Tailwind (exemplos: `bg-ms-red`, `text-semantic-legacy`, `p-sp-md`, `text-sp-lg`). Depois de importar, use as classes diretamente no seu JSX sem precisar consultar o `tokens.json` manualmente.

```bash
# O arquivo está em design-system/dist/tailwind.config.js
# Copie ou referencie em tailwind.config.ts do seu projeto Next.js
```

### 11.2 Para desenvolvedores de artefatos HTML (slides, documentos)

Importe o `tokens.css` da Camada 4, que expõe todos os tokens como CSS custom properties. Depois, use `var(--color-ms-red-500)`, `var(--spacing-xl)`, `var(--typography-scale-title-font-size)` diretamente no seu CSS.

```html
<link rel="stylesheet" href="design-system/dist/tokens.css">
```

### 11.3 Para designers (Figma, ferramentas visuais)

Abra o `hackathon-datacorp-design-system.html` no navegador como referência visual. Todos os componentes, cores, e espaçamentos estão demonstrados ali com os valores exatos. Para copiar um valor de cor, consulte a tabela na seção 4 deste documento ou abra o `tokens.json` para os valores primitivos.

### 11.4 Para IAs agênticas (Copilot, Cowork, Claude Code)

Use o `tokens.json` como referência autoritativa ao gerar artefatos visuais. O arquivo tem a estrutura W3C Design Tokens com valores exatos de cor, tipografia, espaçamento, e componentes. Ao pedir para uma IA gerar um artefato, inclua uma instrução como esta no prompt:

```
Crie um artefato seguindo o design system em design-system/tokens.json.
Aplique a cor MS-RED (#F25022, token color.ms.red.500) para contextos de legado.
Use a cor MS-GREEN (#7FBA00, token color.ms.green.500) para contextos de sistema moderno.
Eyebrows usam JetBrains Mono, 24px, uppercase, tracking 0.12em.
Títulos usam Inter 500, 72px.
Fundo de slide: #F7F7F5 (color.neutral.bg). Texto primário: #1A1A1A (color.neutral.ink).
```

---

## Regras de governança

O design system é versionado com semver (major.minor.patch). A versão atual é 1.0.0.

**Quem pode modificar:** Paula Silva como autora original. Durante o hackathon (27 e 28 de abril de 2026), modificações são congeladas para garantir consistência dos materiais em sala.

**Como propor mudanças:** Registre a mudança proposta com justificativa (por que a mudança é necessária, o que quebra se não for feita, qual o impacto visual). Mudanças que alteram valores de cores base ou semântica das cores são breaking changes e requerem bump de major version.

**Tipos de versão:**
- **Patch (1.0.x):** Correção de typos, ajuste de description de token, documentação adicional sem alterar valores
- **Minor (1.x.0):** Adição de novos tokens ou componentes sem alterar tokens existentes
- **Major (x.0.0):** Alteração de valores de tokens existentes, mudança de semântica de cor, remoção de tokens

**Como comunicar breaking changes:** Atualizar o change log neste documento com a versão, data, autor, e descrição das mudanças. Se tokens forem renomeados ou removidos, listar explicitamente os tokens afetados e o que substituiu cada um.

**Arquivos derivados:** Após qualquer mudança nos tokens, regenerar `tokens.css` e `tailwind.config.js` rodando os prompts 03 e 04 do pacote de prompts. O `design-system.md` pode precisar de atualização manual se a semântica mudar.

---

## Glossário

Esta seção define os termos técnicos usados neste documento. Termos de domínio do projeto aparecem com o contexto de uso no hackathon.

**Eyebrow:** Elemento tipográfico posicionado acima do título principal. Usa JetBrains Mono, uppercase, tracking longo (0.12em). Identifica categoria, estágio, ou contexto do slide.

**Pill:** Chip compacto de categorização. Borda colorida, fundo neutro, texto em mono. Usado para etiquetar ferramentas, tipos de entregável, módulos, e categorias inline.

**Block:** Card informativo estruturado com label de categoria, nome e descrição. Componente genérico que representa qualquer entidade com esses três campos.

**Big number stat:** Componente de destaque numérico. Número em 240px weight 300 seguido de label de contexto em mono. Usado para métricas de impacto em slides de abertura de estágio.

**Stage card:** Card específico do hackathon representando um dos 4 estágios do Dia 2. Barra colorida de 6px no topo indica o estágio.

**Persona pill:** Variante do pill para identificar personas de time. Inclui dot colorido de cluster (product, architect, build, ops).

**Agent block:** Componente de apresentação dos 13 agentes do framework Agentic Legacy Modernization. Slot de ícone com fundo amarelo, nome canônico do agente, e descrição.

**MU (Modernization Unit):** Unidade de trabalho do framework Agentic Legacy Modernization. Cada MU representa um pacote de funcionalidade a ser migrada.

**PE (Persona Engineer):** Papel dentro dos times do hackathon. Cada PE tem uma especialidade e um cluster de atuação.

**EARS (Easy Approach to Requirements Syntax):** Sintaxe estruturada para escrita de requisitos usada no Estágio 2 (Spec Greenfield).

**SDD (Specification-Driven Development):** Abordagem de desenvolvimento onde a especificação formal precede a implementação. O Specky é o plugin SDD central do hackathon.

**Modular Monolith:** Arquitetura alvo do SIFAP 2.0. Monolito com bounded contexts bem definidos, coesos internamente e fracamente acoplados entre si. Não é microserviços.

**Bounded context:** Unidade de domínio no Modular Monolith. Cada bounded context tem seu modelo de dados próprio, suas regras de negócio, e sua fronteira explícita. O carving de bounded contexts é o principal entregável do Estágio 1.

**Strangler Fig Pattern:** Padrão de coexistência entre sistema legado e sistema moderno durante a migração. O SIFAP 1.0 continua em produção enquanto o SIFAP 2.0 é construído ao lado, com rotas gradualmente migradas.

**Specky:** Plugin SDD desenvolvido para o hackathon, integrado ao VS Code via GitHub Copilot. Automatiza a geração de especificações EARS e conecta especificação ao código.

**Agentic Legacy Modernization:** Nome canônico do framework de modernização agêntica desenvolvido por Paula Silva. Os 13 agentes do framework executam tarefas específicas de arqueologia, especificação, reconstrução e evolução de sistemas legados.

---

## Referências

- **Showcase HTML:** `design-system/hackathon-datacorp-design-system.html` (Camada 3, demonstração visual completa do design system)
- **Tokens JSON:** `design-system/tokens.json` (Camada 1, fonte de verdade programática)
- **Tokens CSS:** `design-system/dist/tokens.css` (Camada 4, CSS custom properties derivadas do tokens.json)
- **Tailwind Config:** `design-system/dist/tailwind.config.js` (Camada 4, Tailwind classes derivadas do tokens.json)
- **Pacote de prompts:** `design-system/README.md` (Guia de uso dos 4 prompts que geram as 4 camadas)
- **W3C Design Tokens Format:** [design-tokens.github.io/community-group/format](https://design-tokens.github.io/community-group/format/) (Especificação do formato usado no tokens.json)
- **Framework Agentic Legacy Modernization:** Documentação canônica nos arquivos Doc 11, Doc 12, e Doc 13 do projeto Hackathon DATACORP 2026 (briefing completo em `briefing-cowork-blueprint-sifap-v2.md`)
