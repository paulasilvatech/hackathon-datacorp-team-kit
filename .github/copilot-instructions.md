# GitHub Copilot Instructions - Hackathon DATACORP 2026

## Contexto do Projeto

Este repositório faz parte do **Hackathon DATACORP 2026 - Agentic DevOps Platform**.  
Você está modernizando o sistema **SIFAP** (Sistema de Fiscalização e Administração de Pagamentos) de Natural/Adabas para stack moderna.

## Stack Alvo

- **Backend:** Java 21 + Spring Boot 3.3 + JPA/Hibernate + PostgreSQL 16
- **Frontend:** Next.js 15 (App Router) + TypeScript + Tailwind CSS + shadcn/ui
- **Containers:** Docker + Docker Compose
- **IaC:** Terraform para Azure
- **CI/CD:** GitHub Actions

## Regras de Geração de Código

- Sempre use Java 21 features (records, sealed classes, pattern matching)
- RESTful APIs seguem convenção: `/api/v1/{resource}`
- Nomes de classes em inglês, comentários em inglês
- Testes unitários obrigatórios para lógica de negócio
- Nunca expor dados sensíveis (CPF, valor de benefício) em logs

## Personas Ativas Neste Time

<!-- TODO: Cada time preenche aqui as 10 personas ativas -->
- [ ] Product Owner
- [ ] Requirements Engineer
- [ ] Enterprise Architect
- [ ] Software Architect
- [ ] Technical Lead
- [ ] Developer
- [ ] DBA
- [ ] QA Engineer
- [ ] DevOps Engineer
- [ ] Tech Writer

## Como Usar o Copilot

1. **Chat** - para explorar o legado e planejar
2. **Edits** - para implementar multi-arquivo
3. **Agent** - para features autônomas completas

## Referencias

Materiais de referencia sao disponibilizados pelos facilitadores no inicio do evento:

- Specky SDD (plugin)
- Cenario SIFAP Legado (bundle entregue na Etapa 1, coloque em `02-cenario-sifap-legado/`)
- Spec SIFAP 2.0 de referencia
- Prototipo SIFAP 2.0 de referencia
