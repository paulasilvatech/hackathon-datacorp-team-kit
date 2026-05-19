---
title: "Template: Bounded Contexts"
description: "Esqueleto para definições de bounded contexts via /carve-bounded-contexts"
author: "Paula Silva, AI-Native Software Engineer, Americas Global Black Belt at Microsoft"
date: "2026-04-29"
version: "1.0.0"
status: "approved"
tags: ["template", "bounded-contexts", "architect", "stage-2"]
---

<!-- markdownlint-disable MD013 MD025 MD026 MD028 MD029 MD034 MD040 MD051 MD060 -->


<!-- Como usar: execute /carve-bounded-contexts. Clone o bloco de contexto para cada um. -->

# Mapa de Bounded Contexts

## Avaliações de Hipóteses

### <!-- placeholder: Name --> — <!-- placeholder: ACCEPTED/REJECTED -->

| Critério              | Avaliação            | Evidência            |
| --------------------- | -------------------- | -------------------- |
| Coesão                | <!-- placeholder --> | <!-- placeholder --> |
| Acoplamento           | <!-- placeholder --> | <!-- placeholder --> |
| Frequência de mudança | <!-- placeholder --> | <!-- placeholder --> |

## Bounded Contexts Finais

### <!-- placeholder: Context Name -->

- **Responsabilidade:** <!-- placeholder -->
- **Dados sob ownership:** <!-- placeholder -->
- **Interface pública:** <!-- placeholder -->
- **Por que é seu próprio contexto:** <!-- placeholder -->

## Comunicação Entre Contextos

| De  | Para | Mecanismo | Dados |
| --- | ---- | --------- | ----- |

```mermaid
flowchart LR
    CTX1["Context 1"] -->|"calls"| CTX2["Context 2"]
    classDef ctx fill:#0f172a,stroke:#334155,color:#e2e8f0
    class CTX1,CTX2 ctx
```

---

**Lembrete de Definition of Done:** Hipóteses avaliadas, rejeições documentadas, 2-5 contextos nomeados, Mermaid renderiza.
