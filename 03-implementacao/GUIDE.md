---
title: "Estagio 3 - Implementacao"
description: "Guia para implementar o SIFAP 2.0 usando o prototipo como base"
author: "Paula Silva, Americas Software GBB, Microsoft"
date: "2026-04-23"
version: "1.1.0"
status: "approved"
tags: ["stage-3", "implementation", "java", "nextjs", "postgres", "prototype"]
---

# 💻 Estagio 3: Implementacao

> ⏱️ **Duracao.** 3 horas. Aqui a especificacao vira codigo que roda. Este e o estagio onde a maior parte dos times passa mais tempo, e onde Copilot Agent brilha mais.

<p align="center">
  <img src="../assets/stage-flow.svg" alt="Jornada dos 4 estagios do hackathon" width="100%"/>
</p>

---

## 📑 Sumario

1. [Onde estamos na jornada](#-onde-estamos-na-jornada)
2. [Objetivo](#-objetivo)
3. [Getting Started](#-getting-started-primeiros-15-minutos)
4. [Features sugeridas](#-features-sugeridas)
5. [Testes](#-testes)
6. [Criterio de Pronto](#-criterio-de-pronto)
7. [Navegacao](#-navegacao)

---

## 🎬 Onde estamos na jornada

O mapa esta desenhado. A spec esta escrita. Agora o time transforma requisitos em algo que roda no navegador e responde no terminal. O prototipo fornecido ja tem a casca: backend Java, frontend Next, banco Postgres, docker-compose. Seu trabalho e vestir a casca com as regras que voces especificaram.

> 💡 **Analogia.** Se o estagio 2 foi a planta do arquiteto, o estagio 3 e o canteiro de obras. Voces nao estao construindo do zero, estao completando os comodos da casa que ja tem fundacao e paredes.

---

## 🎯 Objetivo

Estender o prototipo funcional do SIFAP 2.0, implementando as funcionalidades priorizadas no Estagio 2. O prototipo ja possui a estrutura base. Seu time vai adicionar features, corrigir bugs e escrever testes.

---

## 🚀 Getting Started (primeiros 15 minutos)

### 1. Subir o ambiente

```bash
# Na raiz do repositorio (04-prototipo-sifap-moderno/)
docker compose up -d
```

Isso inicia:
- **PostgreSQL 16** na porta 5432
- **Backend (Java 21 + Spring Boot 3)** na porta 8080
- **Frontend (Next.js 15)** na porta **3000** (local) ou **3001** (root docker-compose)

> **ATENCAO**: Se voce executou `docker compose up` da RAIZ do workspace (recomendado), o frontend esta em **http://localhost:3001**. Se executou de dentro de `04-prototipo-sifap-moderno/`, esta em **http://localhost:3000**.

### 2. Verificar que tudo funciona

- Backend health: http://localhost:8080/actuator/health
- Swagger UI: http://localhost:8080/swagger-ui.html
- Frontend: http://localhost:3001 (ou 3000 se compose local)

### 3. Credenciais padrao

| Usuario | Senha | Perfil | O que pode fazer |
|---------|-------|--------|-----------------|
| `admin` | `serpro2026` | ADMIN | Tudo: gerenciar usuarios, configuracoes |
| `operator1` | `serpro2026` | OPERADOR | Cadastrar beneficiarios, registrar pagamentos |
| `auditor1` | `serpro2026` | AUDITOR | Consultar, gerar relatorios, auditar |

### 4. Testar a API no Swagger

Acesse http://localhost:8080/swagger-ui.html e teste:
1. `POST /api/v1/auth/login` com `{"username": "admin", "password": "serpro2026"}`
2. Copie o token JWT retornado
3. Clique em "Authorize" no Swagger e cole o token
4. Teste os endpoints de beneficiarios e pagamentos

---

## 🏗️ Estrutura do Backend

O backend segue uma arquitetura de **monolito modular** com 4 modulos e 3 camadas cada:

```
src/main/java/br/gov/serpro/sifap/
|
|-- beneficiary/          # Modulo: Beneficiarios
|   |-- domain/           # Entidades e regras de negocio
|   |-- application/      # Servicos e DTOs
|   |-- infrastructure/   # Controllers, Repositories, Entities JPA
|
|-- payment/              # Modulo: Pagamentos
|   |-- domain/
|   |-- application/
|   |-- infrastructure/
|
|-- audit/                # Modulo: Auditoria
|   |-- domain/
|   |-- application/
|   |-- infrastructure/
|
|-- admin/                # Modulo: Administracao
|   |-- domain/
|   |-- application/
|   |-- infrastructure/
```

### Camadas (de dentro para fora)

| Camada | Responsabilidade | Exemplos |
|--------|-----------------|----------|
| **domain** | Regras de negocio puras, sem dependencia de framework | Enums de status, interfaces de repositorio, value objects |
| **application** | Casos de uso, orquestracao | Services, Request/Response DTOs |
| **infrastructure** | Detalhes tecnicos, I/O | Controllers REST, Entities JPA, Repositories Spring Data |

### Regra de ouro

A camada `domain` **nunca** importa classes de `infrastructure`. O fluxo e sempre: Controller -> Service -> Repository (interface no domain, implementacao na infrastructure).

---

## 🧩 Como Adicionar uma Nova Feature

Siga estes 5 passos para cada funcionalidade:

### Passo 1: Criar/atualizar a entidade de dominio

```java
// src/.../payment/domain/PaymentStatus.java
public enum PaymentStatus {
    PENDING, APPROVED, REJECTED, CANCELLED
}
```

### Passo 2: Criar o servico

```java
// src/.../payment/application/PaymentService.java
@Service
public class PaymentService {
    // Injete o repositorio, implemente a logica
}
```

### Passo 3: Criar o controller

```java
// src/.../payment/infrastructure/PaymentController.java
@RestController
@RequestMapping("/api/v1/payments")
public class PaymentController {
    // Injete o service, exponha os endpoints
}
```

### Passo 4: Criar a migracao de banco

```sql
-- src/main/resources/db/migration/V2__add_payment_status.sql
ALTER TABLE payments ADD COLUMN status VARCHAR(20) DEFAULT 'PENDING';
```

> **Importante**: Use Flyway. Nunca altere migracoes existentes - sempre crie novas (V2__, V3__, etc.).

### Passo 5: Escrever testes

```java
// src/test/.../payment/application/PaymentServiceTest.java
@SpringBootTest
class PaymentServiceTest {
    @Test
    void shouldCalculatePaymentCorrectly() {
        // Arrange, Act, Assert
    }
}
```

---

## ✏️ Workflow com Copilot Edits

Para implementar funcionalidades rapidamente com Copilot:

1. **Selecione os arquivos** relevantes no VS Code (Ctrl+clique)
2. **Abra Copilot Edits** (Ctrl+Shift+I)
3. **Descreva a mudanca** em linguagem natural:
   > "Adicione um endpoint PUT /api/v1/beneficiaries/{id}/status que permite
   > alterar o status do beneficiario. Valide que a transicao de status e valida
   > (ATIVO -> SUSPENSO e permitido, INATIVO -> ATIVO nao e). Crie o teste."
4. **Revise o diff** antes de aceitar - verifique se segue a arquitetura
5. **Rode os testes** para confirmar

---

## 🧪 Testes

### Rodar todos os testes

```bash
cd 04-prototipo-sifap-moderno/backend
./mvnw test
```

### Requisitos

- **Docker deve estar rodando** - os testes usam Testcontainers para subir um PostgreSQL real
- Java 21 instalado (ou use o DevContainer)

### Tipos de teste esperados

| Tipo | Onde | O que testa |
|------|------|-------------|
| Unitario | `*ServiceTest.java` | Logica de negocio isolada |
| Integracao | `*ControllerTest.java` | Endpoint completo (HTTP -> DB) |
| Repositorio | `*RepositoryTest.java` | Queries customizadas |

---

## ⚛️ Frontend

### Rodar o frontend localmente

```bash
cd 04-prototipo-sifap-moderno/frontend
npm install
npm run dev
```

Acesse http://localhost:3000

### Arquitetura Frontend

O frontend usa **Next.js 15 com App Router** e **Server Components**:

```
src/app/
|-- layout.tsx              # Layout raiz
|-- page.tsx                # Pagina inicial
|-- (auth)/
|   |-- login/page.tsx      # Pagina de login
|-- (dashboard)/
|   |-- beneficiaries/      # CRUD de beneficiarios
|   |-- payments/           # CRUD de pagamentos
|   |-- audit/              # Logs de auditoria
|   |-- admin/              # Gestao de usuarios
```

### Padrao de Server Components

- **Server Components** (padrao): Buscam dados no servidor, sem JavaScript no cliente
- **Client Components** (`"use client"`): Apenas quando precisa de interatividade (formularios, modais)

---

---

## 🔗 Rastreabilidade: Requisito para Codigo para Teste

Para cada feature que implementar, mantenha a rastreabilidade com a spec:

| Requisito EARS | Codigo | Teste |
|---------------|--------|-------|
| REQ-BEN-01: "O SIFAP deve validar CPF com modulo-11" | `Cpf.java` (domain) | `CpfTest.java` - 11 testes |
| REQ-PAY-03: "Quando ciclo gerado, criar pagamentos para ATIVOS" | `PaymentCycleService.generate()` | `PaymentCycleServiceTest.generate_openCycle` |
| REQ-AUD-01: "Quando entidade alterada, gravar auditoria" | `AuditService.record()` | `SifapApplicationIntegrationTest` |

Ao adicionar uma feature, documente no seu commit: "Implements REQ-XXX". Isso fecha o ciclo spec → code → test.

---

## 🛠️ Troubleshooting

| Problema | Solucao |
|----------|---------|
| `docker compose up` falha | Verifique: Docker Desktop rodando? Portas 5432/8080/3000 livres? Tente `docker compose down && docker compose up -d` |
| Backend nao conecta ao PostgreSQL | Verifique se o container postgres esta healthy: `docker compose ps` |
| Frontend mostra "Failed to load" | Backend esta rodando? Teste: `curl http://localhost:8080/actuator/health` |
| Login retorna "Invalid credentials" | Use: admin / serpro2026. Verifique se V4__auth.sql rodou (Flyway) |
| Teste falha com Testcontainers | Docker Desktop deve estar rodando. Alternativa: teste unitario com Mockito |
| Migration falha ao subir | NUNCA edite migration existente. Crie nova (V5__, V6__...) |
| `mvn test-compile` erro de import | Verifique se o pacote segue a estrutura: domain/ → application/ → infrastructure/ |
| Swagger UI nao aparece | Acesse: http://localhost:8080/swagger-ui/index.html (caminho alternativo) |

---

## ✅ Criterio de Pronto

Ao final do Estagio 3, seu time deve ter:

- [ ] Backend funcional com pelo menos 2 novos endpoints implementados
- [ ] Frontend com pelo menos 1 nova tela ou melhoria significativa
- [ ] Testes passando: `./mvnw test` sem falhas
- [ ] `docker compose up` funcional - qualquer avaliador pode subir o sistema
- [ ] Swagger UI mostrando todos os endpoints documentados
- [ ] Pelo menos 1 regra de negocio do Estagio 1 implementada e testada

## 💬 Prompts para Copilot Chat

1. "Crie um endpoint REST para [funcionalidade] seguindo a arquitetura existente"
2. "Escreva um teste de integracao para o endpoint [endpoint]"
3. "Adicione validacao Bean Validation no DTO [classe]"
4. "Crie uma migracao Flyway para adicionar [tabela/coluna]"
5. "Implemente a regra de negocio BR-XXX: [descricao da regra]"
6. "Crie um componente React Server Component para listar [entidade]"
7. "Adicione tratamento de erro para o caso de [cenario]"
8. "Refatore este service para separar a logica de [responsabilidade]"

## 🏆 Dica de Ouro

Nao tente implementar tudo. Foque em **qualidade sobre quantidade**. Um endpoint bem feito, com testes, validacao e documentacao vale mais do que 5 endpoints quebrados.

---

## 🧭 Navegacao

| ⬅️ Anterior | 🏠 Home | ➡️ Proximo |
|---|---|---|
| [📜 Estagio 2: Spec Moderna](../02-spec-moderna/GUIDE.md) | [README do kit](../README.md) | [🚀 Estagio 4: Evolucao](../04-evolucao/GUIDE.md) |

> Autoria: Paula Silva, Americas Software GBB, Microsoft.
