---
applyTo: "docs/**/*.md"
---

# Convenções de Documentação de Requisitos

## Formato
- Notação EARS para requisitos formais
- Given/When/Then para critérios de aceitação
- Numeração sequencial dentro de features
- MUST/SHALL para obrigatório, SHOULD para recomendado
- **Todo requisito carrega uma linha `source_legacy:`** apontando para `legacy/natural-programs/*.NSN`, `legacy/adabas-ddms/*.ddm` ou `[GREENFIELD] + justification`. O CI rejeita requisitos sem essa linha.
