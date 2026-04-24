---
title: "Estagio 1 - Arqueologia Digital"
description: "Guia passo a passo para analise arqueologica do sistema SIFAP legado"
---

# Estagio 1 - Arqueologia Digital (3 horas)

## Objetivo

Explorar o sistema legado SIFAP (Natural/Adabas) e extrair regras de negocio, dependencias e "misterios" - logica escondida sem documentacao.

## Onde encontrar o codigo legado

> O cenario legado (SIFAP) sera disponibilizado pelos facilitadores no inicio da Etapa 1. Copie o bundle entregue para dentro da raiz do seu repositorio, na pasta `02-cenario-sifap-legado/`, e use os caminhos abaixo.

| Recurso | Caminho | Quantidade |
|---------|---------|------------|
| Programas Natural | `02-cenario-sifap-legado/natural-programs/` | 15 arquivos .NSN |
| DDMs Adabas | `02-cenario-sifap-legado/adabas-ddms/` | 4 arquivos .ddm |
| Documentacao parcial | `02-cenario-sifap-legado/legacy-docs/` | 3 docs desatualizados |
| README do sistema | `02-cenario-sifap-legado/README.md` | 1 arquivo |

## Workflow (3 horas)

### Hora 1 - Reconhecimento (09:15-10:15)

1. **Todos**: Leiam o README.md do SIFAP (15 min) - entender historia, equipe, criticidade
2. **Requirements Engineer + Tech Writer**: Iniciem o glossario - abram cada .NSN e anotem abreviacoes
3. **Enterprise Architect**: Comece o mapa de dependencias - quais programas chamam quais?
4. **Developer + DBA**: Abram os 4 DDMs - mapeiem campos para entidades modernas

### Hora 2 - Extracao (10:15-11:15)

5. **Todos em pares**: Cada par analisa 3 programas .NSN - encontrem regras de negocio
6. **Use Copilot Chat**: Peca ao Copilot para explicar cada programa
7. **Documente**: Para cada regra encontrada, registre no catalogo

### Hora 3 - Sintese (11:15-12:00)

8. **Tech Writer**: Consolide o glossario (minimo 30 termos)
9. **Enterprise Architect**: Finalize o mapa de dependencias em Mermaid
10. **Requirements Engineer**: Consolide o catalogo de regras
11. **Product Owner**: Priorize as regras - quais migrar primeiro?
12. **QA Engineer**: Liste os "misterios" encontrados

## Prompts para Copilot Chat

Use estes prompts para explorar o codigo legado:

1. "Explique este programa Natural linha por linha: [cole o codigo]"
2. "Quais regras de negocio estao implementadas neste codigo?"
3. "Quais campos do DDM este programa le e escreve?"
4. "Encontre todos os valores hardcoded neste programa e explique o que fazem"
5. "Este programa tem alguma logica condicional que nao esta documentada nos comentarios?"
6. "Compare CALCBENF.NSN e BATCHPGT.NSN - ha duplicacao de logica?"
7. "Quais programas dependem do DDM BENEFICIARIO?"
8. "Explique a diferenca entre os status A, S, C, I, D no contexto do SIFAP"
9. "Este codigo tem alguma regra que parece um workaround ou hack?"
10. "Crie um diagrama Mermaid das dependencias entre os 15 programas"

## Criterio de "Pronto"

Ao final do Estagio 1, seu time deve ter:

- [ ] Glossario com 30+ termos (arquivo: `01-arqueologia/glossary.md`)
- [ ] Catalogo de regras de negocio (arquivo: `01-arqueologia/business-rules-catalog.md`)
- [ ] Mapa de dependencias em Mermaid (arquivo: `01-arqueologia/dependency-map.md`)
- [ ] Lista de misterios encontrados (arquivo: `01-arqueologia/mysteries-found.md`)
- [ ] Relatorio de descoberta (arquivo: `01-arqueologia/discovery-report.md`)

## Dica de Ouro - Caca aos Misterios!

Existem **10 regras de negocio escondidas**, **3 easter eggs** e **4 inconsistencias** plantados no codigo legado. Abra o arquivo `mysteries-checklist.md` neste diretorio - ele lista o que procurar (sem dar as respostas!).

Seu time e avaliado na rubrica (dimensao A1) pela quantidade e qualidade dos misterios encontrados. Total possivel: **32 pontos**.

Apos 90 minutos, o **facilitador** (pessoa da equipe organizadora com cordao azul, circulando pela sala) pode dar dicas calibradas se seu time estiver travado. Levante a mao!
