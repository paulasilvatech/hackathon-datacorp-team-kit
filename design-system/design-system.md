---
title: "Design System, Hackathon DATACORP 2026"
description: "Textual documentation of the design system applied to Hackathon DATACORP 2026, based on the Microsoft palette with semantic framing for agentic legacy modernization"
author: "Paula Silva, AI-Native Software Engineer, Americas Global Black Belt at Microsoft"
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

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 1.0.0 | 2026-04-18 | Paula Silva, AI-Native Software Engineer, Americas Global Black Belt at Microsoft | Initial Design System version, generated from showcase HTML and tokens.json via Copilot |

---

## Table of Contents

1. [Introduction](#introduction)
2. [Philosophy and Principles](#philosophy-and-principles)
3. [Semantics of the 4 Colors](#semantics-of-the-4-colors)
4. [Color Tokens](#color-tokens)
5. [Typography](#typography)
6. [Spacing](#spacing)
7. [Base Components](#base-components)
8. [Hackathon-Specific Components](#hackathon-specific-components)
9. [Dark Variant, Divider Slide](#dark-variant-divider-slide)
10. [Application by Day 2 Stage](#application-by-day-2-stage)
11. [How to Consume the Design System](#how-to-consume-the-design-system)
12. [Governance Rules](#governance-rules)
13. [Glossário](#glossário)
14. [References](#references)

---

## Introduction

This document is the textual bridge for the Design System of Hackathon DATACORP 2026. It explains the system in human language: the principles that guide decisions, the semantics behind each visual choice, the rules for using components, and why each token exists as it does. If you have read `tokens.json` and found it too dry, this is where to understand the reasoning. If you opened `hackathon-datacorp-design-system.html` and were curious about the logic, this is also the place.

The design system operates in four layers. Layer 1 is `tokens.json`, the programmatic source of truth: all primitive values live there, and no other file invents numbers on its own. Layer 2 is this document, which explains the system in prose. Layer 3 is the HTML showcase (`hackathon-datacorp-design-system.html`), which visually demonstrates each decision. Layer 4 comprises the derived files (`tokens.css` and `tailwind.config.js`), which translate tokens into formats consumable by code. Each layer has a primary audience, and none replaces the others.

The design system serves three audiences simultaneously. Developers will find here the tokens they need to import and the rules for composing components. Designers and content creators will find the color semantics, usage principles, and logic for applying them to slides, handouts, and team materials. Agentic AIs (GitHub Copilot, Claude Code, and the Cowork Blueprint) will find an authoritative textual specification that guides the generation of visual artifacts and documents coherent with the system.

---

## Philosophy and Principles

Before diving into tokens, it is worth understanding the four ideas that govern the system. Every rule for using components, every color choice, and every typographic decision originates from one of these principles. When doubt arises about how to apply the design system, come back here.

### 2.1 Color Is Semantic

The four Microsoft colors are not decorative accents chosen for aesthetics. Each carries a fixed meaning in the context of agentic legacy modernization. Red is legacy. Green is modern. Blue is tooling. Yellow is agents. Using one of these colors outside its semantic meaning breaks the system, because it confuses anyone reading the artifact about what they are looking at. A slide about agents with a red eyebrow sends the wrong signal, even if it looks visually okay.

### 2.2 One Dominant Accent Per Slide or Artifact

Each artifact (slide, handout, room poster, team card) should have one dominant accent color, chosen according to the main theme of the content. The other three Microsoft colors may appear in pills, badges, and smaller markers, but only when those elements carry the correct semantic meaning of the color. Mixing the four accents in equal proportions on a single slide dilutes identity and eliminates the benefit of the semantic system.

### 2.3 Neutrals Do the Heavy Lifting

Text, dividing lines, backgrounds, and surfaces are always neutral: `color.neutral.ink` for primary text (`#1A1A1A`), `color.neutral.bg` for backgrounds (`#F7F7F5`), `color.neutral.rule` for separators (`#E5E5E0`). The four Microsoft colors enter as point markers: eyebrows, pills, colored bars on top of cards, big numbers of emphasis. They never occupy large areas of an artifact. This ensures the system remains legible and the accent has real visual impact when it appears.

### 2.4 Legacy and Modern Have Positional Duality

When an artifact compares the legacy system and modern system side by side, legacy goes on the left and modern goes on the right. Legacy is associated with red (MS-RED, `#F25022`) and modern with green (MS-GREEN, `#7FBA00`). This direction never reverses, because Western reading flows left to right and this reinforces the temporal narrative: we came from there (legacy, left, past) and we are going here (modern, right, future). The Legacy vs Modern split component implements this rule structurally.

---

## Semantics of the 4 Colors

This section is central to the design system. Everything that appears visually in hackathon artifacts has a justification that begins here. Each color has a fixed role, and knowing that role is what differentiates someone applying the system from someone just using pretty colors.

### 3.1 Red, MS-RED, `#F25022`

Red represents the SIFAP system in its original form: written in Natural with Adabas bank, in production since 1997, with decades of accumulated technical debt. It is the color of digital archaeology, documentation gaps, business rules hidden in uncommented subroutines, 4GL limitations that nobody can explain anymore, the original team that has already retired. When you see red in a hackathon artifact, you are looking at something that belongs to the past being modernized.

Red also carries the dimension of risk and attention. Big numbers showing Natural code LOC, accumulated maintenance time, test coverage near zero, business rules without formal specification: all these contexts call for red. Not because legacy is wrong (it works and is in production), but because it represents the starting point that needs care and attention during the transition.

**When to use:**
- Eyebrows on slides about Stage 1, Digital Archaeology
- Pills marking `legacy`, `Natural`, `Adabas`, `SIFAP 1.0`
- Big numbers of technical debt (LOC, maintenance time, zero coverage)
- Legacy vs Modern split component, left side
- Stage cards for Stage 1 (red top bar)
- Risk or gap indicators at any stage

**When not to use:**
- Slides about modern tools or rebuild stack
- Success indicators, gate criteria met, tests passing
- Contexts about AI agents or prompts

**Examples in the hackathon:**
- Stage 1 opening slide eyebrow `STAGE 01 · DIGITAL ARCHAEOLOGY` in MS-RED
- Card showing `287,000 LOC` in Natural with red big number

### 3.2 Green, MS-GREEN, `#7FBA00`

Green represents SIFAP 2.0 that teams will build during the hackathon: Java Spring Boot 3, Next.js 15, PostgreSQL 16, Modular Monolith architecture with well-defined bounded contexts. It is the color of modern code delivered, tests passing in the GitHub Actions pipeline, Docker Compose running locally without error, Azure deployment confirmed, gate criteria met in Stage 3.

Green is the color of arrival, not of journey. It appears when something has been validated, delivered, or confirmed as correct. During Stage 3 (Reconstruction), which is the longest stage of Day 2, green will dominate artifacts because it is the moment teams are actively building the modern system.

**When to use:**
- Eyebrows on slides about reconstruction and delivery
- Green build status, pipeline passing, tests OK
- Pills of validated deliverables: `Spring Boot`, `PostgreSQL`, `SIFAP 2.0`
- Stage cards for Stage 3 (green top bar)
- Legacy vs Modern split component, right side
- Gate criteria met, feature merged, bounded context extracted

**When not to use:**
- Diagnostic or archaeology slides of legacy system
- Contexts about agents or prompts (those are yellow)
- Risk or gap indicators

**Examples in the hackathon:**
- Stage 3 opening slide eyebrow `STAGE 03 · RECONSTRUCTION` in MS-GREEN
- Pill `Java Spring Boot 3` in green next to a rebuilt module
- Big number showing test coverage reached at gate criteria

### 3.3 Blue, MS-BLUE, `#00A4EF`

Blue represents the tooling that DATACORP developers will use during the two days: VS Code with extensions, GitHub Copilot in three modes (Chat, Edits, Agent), Docker for local containerization, Terraform for infrastructure as code, GitHub Actions for CI/CD, Azure as the deployment platform. It is the color of the surface where work happens, not the work itself.

The distinction between blue (tooling) and yellow (agents) is important. Copilot as product and platform is blue. The custom prompts, skills, and instructions teams build during the hackathon are yellow. Stage 2 (Greenfield Spec) uses blue as the dominant color because it is the moment teams are learning to use specification tools, including Specky as an SDD plugin.

**When to use:**
- Tool pills: `VS Code`, `GitHub Copilot`, `Docker`, `Terraform`, `Azure`
- Eyebrows on slides about tooling and infrastructure
- References to Stage 2, Greenfield Spec
- Stage cards for Stage 2 (blue top bar)
- Elements representing the development platform

**When not to use:**
- Slides about legacy system or archaeology
- Contexts of custom agents, prompts, or skills developed by teams
- Delivery or success indicators (those are green)

**Examples in the hackathon:**
- Stage 2 opening slide eyebrow `STAGE 02 · GREENFIELD SPEC` in MS-BLUE
- Pills `GitHub Actions`, `Docker`, `Azure` in blue on an architecture slide
- Architect and tech lead persona pills with blue dot

### 3.4 Yellow, MS-YELLOW, `#FFB900`

Yellow represents the 13 agents of the Agentic Legacy Modernization framework, Specky as the central SDD plugin, the prompts teams will use and create, the skills and instructions configured in Copilot, and the entire AI intelligence layer of the hackathon. It is the color of agentic orchestration, automated thinking, AI that amplifies developer work.

Stage 4 (Evolution with Agent) uses yellow as the dominant color because it is the moment teams apply agents to evolve SIFAP 2.0 beyond what they could accomplish manually. Yellow is also the default eyebrow color on dark backgrounds (divider slides), because the yellow-on-black contrast is the most dramatic in the system.

**When to use:**
- Eyebrows on slides about agents and AI
- Pills marking `@agent`, `prompt`, `skill`, `SDD`
- Blocks describing the 13 agents of the framework
- Stage cards for Stage 4 (yellow top bar)
- Eyebrows on slides with dark variant (stage dividers)
- Agent blocks with icon in yellow slot

**When not to use:**
- Contexts of delivery or reconstruction (those are green)
- Slides about generic tooling like Docker or Terraform (those are blue)
- Risk or legacy indicators

**Examples in the hackathon:**
- Stage 4 opening slide eyebrow `STAGE 04 · EVOLUTION WITH AGENT` in MS-YELLOW
- Agent block showing `@discovery-agent` with icon in yellow slot
- Pill `@specky` in yellow on an SDD slide

---

## Color Tokens

This section lists all color tokens in the system, organized by group. The values here are exactly the same as in `tokens.json`. Whenever you need a color value for code, consult `tokens.json` directly: it is the source of truth. This document uses the same values so the reference is complete even outside the IDE.

### 4.1 Group `color.ms`, Microsoft Palette

| Token | Value | Description |
|-------|-------|-------------|
| `color.ms.red.50` | `#FFF0EB` | Red background wash, subtle backgrounds and legacy badges |
| `color.ms.red.100` | `#FFD6C7` | Red soft tint, hover surfaces and attention labels |
| `color.ms.red.500` | `#F25022` | Red base, primary accent of legacy and gaps |
| `color.ms.red.700` | `#B33816` | Red deep, text on light backgrounds and hover states |
| `color.ms.green.50` | `#F1F8E3` | Green background wash, subtle success backgrounds |
| `color.ms.green.100` | `#D8EDA5` | Green soft tint, success surfaces and modern badges |
| `color.ms.green.500` | `#7FBA00` | Green base, accent for modern and success |
| `color.ms.green.700` | `#5A8500` | Green deep, text on light backgrounds |
| `color.ms.blue.50` | `#E5F6FD` | Blue background wash, subtle tooling backgrounds |
| `color.ms.blue.100` | `#B8E5FA` | Blue soft tint, tool reference surfaces |
| `color.ms.blue.500` | `#00A4EF` | Blue base, accent for tooling and Copilot |
| `color.ms.blue.700` | `#0076AC` | Blue deep, text on light backgrounds |
| `color.ms.yellow.50` | `#FFF7E0` | Yellow background wash, subtle agent backgrounds |
| `color.ms.yellow.100` | `#FFE79C` | Yellow soft tint, agent emphasis surfaces |
| `color.ms.yellow.500` | `#FFB900` | Yellow base, accent for agents and AI |
| `color.ms.yellow.700` | `#B88500` | Yellow deep, text on light backgrounds |
| `color.ms.gray` | `#737373` | Microsoft wordmark gray, brand reference contexts |

### 4.2 Group `color.neutral`, Neutral Scale

| Token | Value | Description |
|-------|-------|-------------|
| `color.neutral.ink` | `#1A1A1A` | Primary text, titles, dominant content |
| `color.neutral.ink-2` | `#3A3A3A` | Secondary text, subtitles, supporting content |
| `color.neutral.ink-3` | `#737373` | Tertiary text, captions, metadata |
| `color.neutral.paper` | `#FFFFFF` | Card background, internal surfaces |
| `color.neutral.bg` | `#F7F7F5` | Slide background, page, external surface |
| `color.neutral.bg-alt` | `#ECECE8` | Alternative background, separation zone |
| `color.neutral.rule` | `#E5E5E0` | Subtle dividing lines |
| `color.neutral.rule-2` | `#CECEC7` | Strong dividing lines, card borders |

### 4.3 Group `color.semantic`, Semantic Aliases

Semantic tokens reference base tokens via aliases (`{color.ms.red.500}`). They exist so code speaks about intention (`color.semantic.legacy`) instead of pigment (`color.ms.red.500`). Use semantic tokens whenever possible in components and templates.

| Token | Reference | Description |
|-------|-----------|-------------|
| `color.semantic.legacy` | `{color.ms.red.500}` | Color of legacy SIFAP, Natural, Adabas, technical debt |
| `color.semantic.modern` | `{color.ms.green.500}` | Color of modern SIFAP 2.0, Spring Boot, PostgreSQL |
| `color.semantic.tooling` | `{color.ms.blue.500}` | Color of tooling, Copilot, VS Code, Docker, Azure |
| `color.semantic.agent` | `{color.ms.yellow.500}` | Color of AI agents, Specky, SDD, prompts |
| `color.semantic.accent` | `{color.ms.red.500}` | Primary default accent of the design system |
| `color.semantic.accent-ink` | `{color.ms.red.700}` | Accent hover and text, dark variant |

### 4.4 Group `color.dark`, Dark Variant Palette

| Token | Value | Description |
|-------|-------|-------------|
| `color.dark.bg` | `#141414` | Dark slide background, stage divider |
| `color.dark.surface` | `#1C1C1A` | Card or block on dark background |
| `color.dark.ink` | `#F0F0F0` | Primary text on dark |
| `color.dark.ink-2` | `#C7C7C2` | Secondary text on dark |
| `color.dark.ink-3` | `#999995` | Tertiary text on dark |
| `color.dark.rule` | `#2E2E2A` | Dividing lines on dark |

---

## Typography

The typography of the design system was chosen to work in two very specific contexts: slides projected on large screens for groups (1920x1080, viewed from 4 to 6 meters) and dense documents read on screen. Inter handles content, JetBrains Mono handles markup. The combination creates clear visual hierarchy without needing much extra weight or ornament.

### 5.1 Families

**Inter** (`typography.family.sans`) is the primary family, used in titles, subtitles, body text, and any content that needs to be read with fluency. It is optimized for screens and has excellent legibility at large and medium sizes.

**JetBrains Mono** (`typography.family.mono`) is the monospaced family, used in eyebrows, numbers in metadata context, code, tokens, and any element that functions as markup or label. The technical character of mono communicates "this is structured data," visually differentiating markers from content.

### 5.2 Available Weights

The system uses five weights, all from Inter (JetBrains Mono uses weights 400, 500, and 600):

| Token | Value | Typical Use |
|-------|-------|------------|
| `typography.weight.light` | 300 | Big number stats on slides |
| `typography.weight.regular` | 400 | Body text, subtitles, captions |
| `typography.weight.medium` | 500 | Main titles, eyebrows, names on cards |
| `typography.weight.semibold` | 600 | Emphasis labels, agent icons in mono |
| `typography.weight.bold` | 700 | Reserved for punctual highlights |

### 5.3 Typographic Scale

The scale was calibrated for 1920x1080 slides. Primary rule: never below 24px on any slide element. In a workshop room, the slide is projected at least 4 meters from the audience, and typography smaller than 24px becomes illegible for anyone sitting beyond the second row.

| Level | Token | Size | Line Height | Tracking | Weight | Family | Use |
|-------|-------|------|-------------|----------|--------|--------|-----|
| Title | `typography.scale.title` | 72px | 1.02 | -0.02em | 500 | Inter | Main slide title |
| Subtitle | `typography.scale.subtitle` | 44px | 1.15 | -0.015em | 400 | Inter | Slide subtitle, emphasized text |
| Body | `typography.scale.body` | 30px | 1.35 | 0 | 400 | Inter | Default slide body text |
| Small | `typography.scale.small` | 24px | 1.4 | 0 | 400 | Inter | Small text, captions, legends |
| Eyebrow | `typography.scale.eyebrow` | 24px | 1.2 | 0.12em | 500 | JetBrains Mono | Eyebrow, category marker, always uppercase |
| Big Number | `typography.scale.big-num` | 240px | 0.9 | -0.04em | 300 | Inter | Big number stat, numerical emphasis |
| Section Title | `typography.scale.section-title` | 160px | 0.95 | -0.035em | 500 | Inter | Dark divider slide title |

The eyebrow deserves special note: it uses JetBrains Mono with wide letter-spacing (0.12em) and uppercase because it must function as a category label, not a title. When you see `STAGE 01 · DIGITAL ARCHAEOLOGY` at the top of a slide, the eyebrow signals: "this is the context for what comes next," without competing visually with the main title.

---

## Spacing

The system uses an 8px base grid. All spacing tokens are multiples or compositions of this base value, ensuring that any combination of tokens results in coherent alignments. This is the same grid used in Portal Gov QA and other Paula Silva projects, creating consistency across different systems.

| Token | Value | Typical Use |
|-------|-------|------------|
| `spacing.xs` | 8px | Gap between very close elements, dot margin |
| `spacing.sm` | 16px | Internal padding of pills and chips |
| `spacing.md` | 28px | Gap between cards and list items, stage card padding |
| `spacing.lg` | 48px | Internal padding of blocks and cards |
| `spacing.xl` | 80px | Slide vertical padding (top and bottom) |
| `spacing.2xl` | 120px | Extra-large padding for spacious slides |

Quick reference: the standard slide (1920x1080) uses `spacing.xl` (80px) as vertical padding and 100px as horizontal padding (defined directly in metadata as `meta.slide-dimensions.padding-horizontal`). The gap between cards in a grid uses `spacing.md` (28px). The internal padding of a block card uses `spacing.lg` (48px), rounded to 36px as specified in `component.block.padding`.

---

## Base Components

Base components are the building blocks that appear in nearly all hackathon artifacts. Each has a specific function and consumes a defined set of tokens. Understanding when to use each is more important than memorizing tokens: the function guides the choice.

### 7.1 Eyebrow, Category Marker

The eyebrow is the label that appears above the main title of a slide or content block. It answers the question: "what is the context or category of this content?" It never is the main content itself.

**When to use:** To identify the current stage (Archaeology, Spec, Reconstruction, Evolution), the slide category (legacy, modern, tooling, agent), or the bounded context being discussed.

**Structure:**
```html
<div class="eyebrow" style="
  font-family: 'JetBrains Mono', monospace;
  font-size: 24px;
  letter-spacing: 0.12em;
  text-transform: uppercase;
  font-weight: 500;
  color: var(--ms-red);
">STAGE 01 · DIGITAL ARCHAEOLOGY</div>
```

**Tokens consumed:** `typography.scale.eyebrow`, `typography.family.mono`, `color.semantic.legacy` (or other semantic color as context).

### 7.2 Pill, Categorization Chip

The pill is a compact chip that categorizes an element: a tool, a stage, an artifact type, a system module. It uses a colored border without background fill (except neutral), allowing multiple pills to stack without creating visual noise.

**When to use:** To label tools, bounded contexts, deliverable types, or any category that needs to appear inline with text.

**Structure:**
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

**Tokens consumed:** `component.pill.padding`, `component.pill.font-family`, `component.pill.font-size`, `component.pill.variant.red` (or other variant).

### 7.3 Block, Informational Card

The block is the default content card in the system. It has a category label in mono (using semantic color), a name in Inter medium, and a description in ink-3. It serves to present any structured entity: agent, module, persona, tool.

**When to use:** To present elements that have name, description, and category (bounded context, system module, agent, tool).

**Structure:**
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
  <div style="font-size: 34px; font-weight: 500; color: #1A1A1A;">Contract Management</div>
  <div style="font-size: 20px; color: #737373; line-height: 1.4;">Module responsible for managing the lifecycle of rural aid contracts.</div>
</div>
```

**Tokens used:** `component.block.padding`, `component.block.background`, `component.block.border-color`, `component.block.label-color`, `component.block.name-font-size`, `component.block.desc-color`.

### 7.4 Big number stat - Numeric Highlight

The big number stat highlights a number with maximum impact, followed by a context label in mono. It is the quantitative data component of the system, created for slides where a number needs to be the center of attention.

**When to use:** To show LOC of Natural code, accumulated maintenance time, test coverage, number of bounded contexts extracted, or any metric that deserves visual emphasis.

**Structure:**
```html
<div class="stat">
  <div style="font-size: 240px; font-weight: 300; letter-spacing: -0.04em; line-height: 0.9; color: #F25022;">287K</div>
  <div style="font-family: 'JetBrains Mono', monospace; font-size: 16px; color: #737373; letter-spacing: 0.1em; text-transform: uppercase; margin-top: 10px;">LINES OF NATURAL CODE</div>
</div>
```

**Tokens used:** `typography.scale.big-num`, `typography.family.mono`, `color.semantic.legacy` (for legacy numbers), `color.neutral.ink-3` (for label).

### 7.5 Table - For Structured Lists

The table follows the design system style: no colored zebra striping, neutral borders, header in mono medium, cells in Inter regular. The goal is maximum readability, not decoration.

**When to use:** For comparative lists, module-to-bounded-context mappings, agent inventory, or any data with multiple dimensions.

**Tokens used:** `color.neutral.rule`, `color.neutral.rule-2`, `typography.family.mono`, `typography.family.sans`, `color.neutral.ink`, `color.neutral.ink-3`.

---

## Hackathon-Specific Components

These four components exist exclusively in the context of Hackathon DATACORP 2026. They encapsulate information patterns that repeat during the two days of the event and require visual consistency to work well in room materials, handouts, and slides.

### 8.1 Stage card - The 4 Day 2 Stages

The stage card represents one of the four stages of Day 2 of the hackathon. It has a colored bar at the top (6px, the stage color), stage number in mono, stage name, time, and short description. It is the most used component in room materials.

**When to use:** In Day 2 overview slides, team handouts, room posters showing the schedule.

**Estrutura:**
```html
<div class="stage-card" style="
  border: 1px solid #E5E5E0;
  border-top: 6px solid #F25022;
  background: #FFFFFF;
  padding: 28px;
">
  <div style="font-family: 'JetBrains Mono', monospace; font-size: 14px; color: #F25022; letter-spacing: 0.1em; text-transform: uppercase; margin-bottom: 12px;">STAGE 01</div>
  <div style="font-size: 26px; font-weight: 500; color: #1A1A1A; margin-bottom: 8px;">Digital Archaeology</div>
  <div style="font-family: 'JetBrains Mono', monospace; font-size: 16px; color: #737373; margin-bottom: 16px;">09:00 to 12:00</div>
  <div style="font-size: 18px; color: #737373; line-height: 1.4;">Understand what SIFAP does before touching the code.</div>
</div>
```

**Tokens used:** `component.stage-card.padding`, `component.stage-card.border-top-width`, `component.stage-card.border-top-color.stage-1` (or stage-2/3/4), `component.stage-card.background`, `component.stage-card.border-color`.

### 8.2 Persona pill - The 10 Team Personas

The persona pill identifies a team member's persona. It has a colored dot (the persona cluster color), the persona name, and uses Inter medium. The 10 personas are grouped into four clusters: product (red), architect (blue), build (green), ops (yellow).

**When to use:** In team composition slides, team handouts, materials listing personas involved in a stage.

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

**Tokens used:** `component.persona-pill.padding`, `component.persona-pill.border-radius`, `component.persona-pill.font-size`, `component.persona-pill.dot-size`, `component.persona-pill.dot-color.architect` (or product/build/ops).

### 8.3 Agent block - The 13 Agents of the Framework

The agent block represents one of the 13 agents of the Agentic Legacy Modernization framework. It has an icon slot with light yellow background and yellow border (where an emoji or agent abbreviation goes), the agent's canonical name in mono yellow, and a description of the agent's role in Inter.

**When to use:** In slides presenting the agent framework, in handouts about Stage 4, in any material listing agents available to teams.

**Structure:**
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
    <div style="font-size: 18px; color: #737373; line-height: 1.4;">Maps Natural code to identify bounded contexts and implicit business rules.</div>
  </div>
</div>
```

**Tokens used:** `component.agent-block.padding`, `component.agent-block.icon-slot-size`, `component.agent-block.icon-slot-background`, `component.agent-block.icon-slot-border`, `component.agent-block.title-color`.

### 8.4 Legacy vs Modern split - SIFAP Visual Duality

The split is the component that places legacy and modern side by side in a 50/50 division. Legacy always on the left (soft reddish background, label in `color.ms.red.700`), modern always on the right (soft greenish background, label in `color.ms.green.700`). The direction does not reverse: left-to-right reading reflects the temporal journey of the hackathon.

**When to use:** In slides comparing SIFAP 1.0 and SIFAP 2.0 directly, in bounded context handouts showing the legacy module and modern equivalent.

**Estrutura:**
```html
<div class="split" style="display: grid; grid-template-columns: 1fr 1fr; border: 1px solid #E5E5E0;">
  <div style="padding: 36px 40px; background: #FAF4F2; border-right: 1px solid #E5E5E0;">
    <div style="font-family: 'JetBrains Mono', monospace; font-size: 16px; letter-spacing: 0.12em; text-transform: uppercase; font-weight: 500; color: #B33816; margin-bottom: 16px;">LEGACY - SIFAP 1.0</div>
    <div style="font-size: 32px; font-weight: 500; color: #1A1A1A; margin-bottom: 12px;">CONTRACT Module</div>
    <div style="font-family: 'JetBrains Mono', monospace; font-size: 18px; color: #737373; margin-bottom: 20px;">Natural 4GL, Adabas, 4,200 LOC</div>
    <div style="font-size: 20px; color: #3A3A3A; line-height: 1.45;">Business logic mixed with persistence. Zero tests. Documentation outdated since 2003.</div>
  </div>
  <div style="padding: 36px 40px; background: #F4F8E8;">
    <div style="font-family: 'JetBrains Mono', monospace; font-size: 16px; letter-spacing: 0.12em; text-transform: uppercase; font-weight: 500; color: #5A8500; margin-bottom: 16px;">MODERN - SIFAP 2.0</div>
    <div style="font-size: 32px; font-weight: 500; color: #1A1A1A; margin-bottom: 12px;">Bounded Context: Contracts</div>
    <div style="font-family: 'JetBrains Mono', monospace; font-size: 18px; color: #737373; margin-bottom: 20px;">Spring Boot 3, PostgreSQL 16, 87% coverage</div>
    <div style="font-size: 20px; color: #3A3A3A; line-height: 1.45;">Isolated domain with integration tests. Documentation generated via Specky. Automated deployment.</div>
  </div>
</div>
```

**Tokens consumidos:** `color.ms.red.700`, `color.ms.green.700`, `color.neutral.rule`, `color.neutral.ink`, `color.neutral.ink-2`, `color.neutral.ink-3`, `spacing.lg`.

---

## Dark Variant - Divider Slide

The dark variant exists for a specific case: transition slides between stages and major conceptual dividers. It is not the system's standard style, which is light. It is an intentional break in rhythm that signals: "we are moving to a new chapter".

The dark background uses `color.dark.bg` (`#141414`). Surfaces on the background use `color.dark.surface` (`#1C1C1A`). Primary text is `color.dark.ink` (`#F0F0F0`), secondary text `color.dark.ink-2` (`#C7C7C2`), tertiary text `color.dark.ink-3` (`#999995`). Divider lines use `color.dark.rule` (`#2E2E2A`).

The standard eyebrow on dark is MS-YELLOW (`#FFB900`). The reason is contrast: yellow on black has the highest contrast of the four accents and creates the right dramatic effect for a transition slide. The main title on dark slides uses `typography.scale.section-title` (160px, weight 500, tracking -0.035em), which fills the screen with maximum impact.

**When to use the dark variant:**
- Stage divider slides (opening each of the 4 Day 2 stages)
- Conceptual transitions that mark an important theme change
- Quote or principle declaration slides that need emphasis

**When not to use:**
- Regular instructional content (keep background light for readability)
- Slides with lots of text or tables (dark contrast is great for impact, not for information density)

---

## Application by Day 2 Stage

This table is the operational map of the design system during Day 2 of the hackathon (April 28). Each stage has a dominant color, and this mapping determines how room materials are visually differentiated. Facilitators can identify which stage they are in just by looking at the slide color.

| Stage | Time | Dominant Color | Token | Application in Artifacts |
|-------|------|--------|-------|----------|
| 01 Digital Archaeology | 09:00 to 12:00 | MS-RED | `color.ms.red.500` (#F25022) | Red eyebrows on slides, big numbers of technical debt, pills `legacy`, `Natural`, `Adabas`, red stage card bar, room poster with red accent |
| 02 Modern Spec | 13:00 to 14:00 | MS-BLUE | `color.ms.blue.500` (#00A4EF) | Blue eyebrows, tool pills (`Specky`, `GitHub Copilot`, `VS Code`), SDD references, blue stage card bar, materials on Spec Phase |
| 03 Implementation | 14:00 to 17:00 | MS-GREEN | `color.ms.green.500` (#7FBA00) | Green eyebrows, validated deliverable pills (`Spring Boot`, `PostgreSQL`), coverage and modern LOC big numbers, green stage card bar, gate criteria checklist |
| 04 Evolution with Agent | 17:00 to 18:30 | MS-YELLOW | `color.ms.yellow.500` (#FFB900) | Yellow eyebrows, agent blocks from 13 agents, pills `@agent`, `prompt`, `skill`, yellow stage card bar, final presentation slides |

The times above are Day 2 times and are fixed in the tokens in `meta.stage-map`. Any artifact that references stages should use these exact times.

---

## How to Consume the Design System

The design system has four layers, and each consumer has a different entry point. This section explains the correct path for each type of use.

### 11.1 For Frontend Developers (Next.js of SIFAP 2.0 Prototype)

Import the `tailwind.config.js` from Layer 4 in your Next.js project. It exposes all tokens as Tailwind classes (examples: `bg-ms-red`, `text-semantic-legacy`, `p-sp-md`, `text-sp-lg`). After importing, use the classes directly in your JSX without needing to consult the `tokens.json` manually.

```bash
# File is in design-system/dist/tailwind.config.js
# Copy or reference in tailwind.config.ts of your Next.js project
```

### 11.2 For HTML Artifact Developers (Slides, Documents)

Import the `tokens.css` from Layer 4, which exposes all tokens as CSS custom properties. Then, use `var(--color-ms-red-500)`, `var(--spacing-xl)`, `var(--typography-scale-title-font-size)` directly in your CSS.

```html
<link rel="stylesheet" href="design-system/dist/tokens.css">
```

### 11.3 For Designers (Figma, Visual Tools)

Open the `hackathon-datacorp-design-system.html` in your browser as a visual reference. All components, colors, and spacing are demonstrated there with exact values. To copy a color value, refer to the table in section 4 of this document or open `tokens.json` for primitive values.

### 11.4 For Agentic AIs (Copilot, Cowork, Claude Code)

Use the `tokens.json` as the authoritative reference when generating visual artifacts. The file has W3C Design Tokens structure with exact color, typography, spacing, and component values. When asking an AI to generate an artifact, include an instruction like this in your prompt:

```
Create an artifact following the design system in design-system/tokens.json.
Apply MS-RED (#F25022, token color.ms.red.500) for legacy contexts.
Use MS-GREEN (#7FBA00, token color.ms.green.500) for modern system contexts.
Eyebrows use JetBrains Mono, 24px, uppercase, tracking 0.12em.
Titles use Inter 500, 72px.
Slide background: #F7F7F5 (color.neutral.bg). Primary text: #1A1A1A (color.neutral.ink).
```

---

## Governance Rules

The design system is versioned with semver (major.minor.patch). The current version is 1.0.0.

**Who can modify:** Paula Silva as original author. During the hackathon (April 27-28, 2026), modifications are frozen to ensure consistency of room materials.

**How to propose changes:** Register the proposed change with justification (why the change is needed, what breaks if it is not made, what the visual impact is). Changes that alter base color values or color semantics are breaking changes and require a major version bump.

**Tipos de versão:**
- **Patch (1.0.x):** Correção de typos, ajuste de description de token, documentação adicional sem alterar valores
- **Minor (1.x.0):** Adição de novos tokens ou componentes sem alterar tokens existentes
- **Major (x.0.0):** Alteração de valores de tokens existentes, mudança de semântica de cor, remoção de tokens

**Como comunicar breaking changes:** Atualizar o change log neste documento com a versão, data, autor, e descrição das mudanças. Se tokens forem renomeados ou removidos, listar explicitamente os tokens afetados e o que substituiu cada um.

**Arquivos derivados:** Após qualquer mudança nos tokens, regenerar `tokens.css` e `tailwind.config.js` rodando os prompts 03 e 04 do pacote de prompts. O `design-system.md` pode precisar de atualização manual se a semântica mudar.

---

## Glossário

Esta seção define os termos técnicos usados neste documento. Termos de domínio do projeto aparecem com o contexto de uso no hackathon.

**Eyebrow:** Typography element positioned above the main title. Uses JetBrains Mono, uppercase, long tracking (0.12em). Identifies category, stage, or slide context.

**Pill:** Chip compacto de categorização. Borda colorida, fundo neutro, texto em mono. Usado para etiquetar ferramentas, tipos de entregável, módulos, e categorias inline.

**Block:** Card informativo estruturado com label de categoria, nome e descrição. Componente genérico que representa qualquer entidade com esses três campos.

**Big number stat:** Numeric highlight component. 240px number at weight 300 followed by a context label in mono. Used for impact metrics on stage opening slides.

**Stage card:** Hackathon-specific card representing one of the 4 stages of Day 2. A 6px colored bar at the top indicates the stage.

**Persona pill:** Pill variant used to identify team personas. Includes a colored cluster dot (product, architect, build, ops).

**Agent block:** Presentation component for the 13 agents of the Agentic Legacy Modernization framework. Icon slot with yellow background, canonical agent name, and description.

**MU (Modernization Unit):** Work unit of the Agentic Legacy Modernization framework. Each MU represents a feature package to be migrated.

**PE (Persona Engineer):** Role within the hackathon teams. Each PE has a specialty and an area cluster.

**EARS (Easy Approach to Requirements Syntax):** Structured syntax for writing requirements, used in Stage 2 (Spec Greenfield).

**SDD (Specification-Driven Development):** Development approach where the formal specification precedes implementation. Specky is the central SDD plugin of the hackathon.

**Modular Monolith:** Target architecture for SIFAP 2.0. A monolith with well-defined bounded contexts that are internally cohesive and loosely coupled. Not microservices.

**Bounded context:** Domain unit in the Modular Monolith. Each bounded context owns its data model, business rules, and explicit boundary. Carving bounded contexts is the main Stage 1 deliverable.

**Strangler Fig Pattern:** Coexistence pattern between legacy and modern systems during migration. SIFAP 1.0 stays in production while SIFAP 2.0 is built alongside, with routes gradually migrated over.

**Specky:** SDD plugin built for the hackathon, integrated into VS Code through GitHub Copilot. Automates the generation of EARS specifications and connects spec to code.

**Agentic Legacy Modernization:** Canonical name of the agentic modernization framework created by Paula Silva. The 13 framework agents run specific tasks across archaeology, specification, reconstruction, and evolution of legacy systems.

---

## References

- **Showcase HTML:** `design-system/hackathon-datacorp-design-system.html` (Layer 3, full visual demonstration of the design system)
- **Tokens JSON:** `design-system/tokens.json` (Layer 1, programmatic source of truth)
- **Tokens CSS:** `design-system/dist/tokens.css` (Layer 4, CSS custom properties derived from tokens.json)
- **Tailwind Config:** `design-system/dist/tailwind.config.js` (Layer 4, Tailwind classes derived from tokens.json)
- **Prompt pack:** `design-system/README.md` (Usage guide for the 4 prompts that generate the 4 layers)
- **W3C Design Tokens Format:** [design-tokens.github.io/community-group/format](https://design-tokens.github.io/community-group/format/) (Specification of the format used in tokens.json)
- **Agentic Legacy Modernization framework:** Canonical documentation in files Doc 11, Doc 12, and Doc 13 of the Hackathon DATACORP 2026 project (full briefing in `briefing-cowork-blueprint-sifap-v2.md`)

---

| Previous | Home |
|:---------|-----:|
| [← Design System Home](README.md) | [Workspace Root](../README.md) |
