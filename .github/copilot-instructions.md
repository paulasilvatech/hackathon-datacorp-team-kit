# GitHub Copilot Instructions — Legacy Modernization Workshop

> These instructions tell Copilot what your team is building, what stack to use,
> what conventions to follow, and what NOT to do. They apply to the entire team
> repository.

## Project Context

This repository belongs to a workshop team modernizing the legacy **SIFAP**
(Sistema de Fiscalização e Administração de Pagamentos) from Natural/Adabas to
a modern stack. The reference workspace lives in
[`workshop-legacy-modernization-datacorp`](https://github.com/paulasilvatech/workshop-legacy-modernization-datacorp).

## Target Stack

- **Backend:** Java 21 + Spring Boot 3.3 + JPA/Hibernate + PostgreSQL 16
- **Frontend:** Next.js 15 (App Router) + TypeScript 5 (strict) + Tailwind CSS + shadcn/ui
- **Containers:** Docker + Docker Compose
- **IaC:** Terraform (Azure provider ~> 3.x)
- **CI/CD:** GitHub Actions
- **Testing:** JUnit 5 + Testcontainers (backend); Vitest + Testing Library (frontend)

## Code Generation Rules

### Java
- Use Java 21 features: records for DTOs, sealed interfaces for discriminated unions, pattern matching, virtual threads
- `Optional` properly — never return `null` from public methods
- `@Transactional` only on the service layer, never on repositories
- Validate inputs at the controller layer with `@Valid` + Bean Validation
- Class names in English; comments in English
- Unit tests are mandatory for business logic
- Never expose sensitive data (CPF, benefit values) in logs — mask them

### TypeScript / Next.js
- `strict: true` in `tsconfig.json` — no exceptions
- Use server actions for mutations; never expose secrets in client components
- Prefer `async/await` over `.then()` chains
- Named exports only — no default exports from component files

### REST APIs
- Path convention: `/api/v1/{resource}`
- Use HTTP verbs correctly (`GET`, `POST`, `PUT`, `PATCH`, `DELETE`)
- Return appropriate status codes (`201` for creation, `204` for no content, `409` for conflict)
- All endpoints must have OpenAPI/Swagger annotations

### Terraform
- Every resource must have `tags` including `project`, `environment`, `owner`
- Secrets via `azurerm_key_vault_secret` only — never in `locals` or `variables`
- One module per Azure service area (networking, compute, database, monitoring)
- `terraform fmt` and `terraform validate` must pass before commit

## Security Rules (OWASP Top 10)

- Validate input at every system boundary
- Never hardcode secrets, API keys, or credentials
- SQL queries via JPA/JPQL only — no string concatenation
- CORS configured explicitly — no wildcard `*` in production
- Authentication via OAuth2/JWT (Spring Security on the backend)
- All Azure resources use Managed Identity for service-to-service auth

## Spec-Driven Development (Specky)

- Every requirement uses **EARS notation** (Easy Approach to Requirements Syntax)
- Every requirement has a unique **REQ-ID** in the format `REQ-NNN`
- **Every requirement carries a `source_legacy:` line** pointing to `legacy/natural-programs/*.NSN`, `legacy/adabas-ddms/*.ddm`, or `[GREENFIELD] + justification`. The CI `legacy-traceability` job rejects PRs that violate this. See [`01-arqueologia/LEGACY-EXPLORATION-CHECKLIST.md`](../01-arqueologia/LEGACY-EXPLORATION-CHECKLIST.md).
- Tests trace to REQ-IDs via inline comments
- Branch strategy: one branch per spec, named `spec/<NNN>-<feature>`
- Merge order: `spec/*` → `develop` → `stage` → `main`

## Legacy Exploration — MANDATORY

Before writing any EARS in Stage 2, your pair MUST have read the assigned Natural programs in [`legacy/natural-programs/`](../legacy/natural-programs/) and DDMs in [`legacy/adabas-ddms/`](../legacy/adabas-ddms/). Specs written without legacy reading lose 29 years of business rules. The HARD GATE matrix lives in [`01-arqueologia/LEGACY-EXPLORATION-CHECKLIST.md`](../01-arqueologia/LEGACY-EXPLORATION-CHECKLIST.md).

## The 5 Pairs and 10 Personas

> **Each team has 5 people. Each person wears 2 personas (1 pair).** No internal handoff between personas in a pair — continuous collaboration. Update the names below with your team's assignments.

| Pair | Persona A | Persona B | SDLC phase |
|------|-----------|-----------|------------|
| 1 · Vision | [ ] 01 Product Owner — name? | [ ] 02 Requirements Engineer — name? | Discovery + Specification |
| 2 · Architecture | [ ] 03 Enterprise Architect — name? | [ ] 04 Software Architect — name? | Specification + Design |
| 3 · Implementation | [ ] 05 Technical Lead — name? | [ ] 06 Developer — name? | Implementation + Evolution |
| 4 · Quality | [ ] 07 DBA — name? | [ ] 08 QA Engineer — name? | Implementation (data + tests) |
| 5 · Operations | [ ] 09 DevOps Engineer — name? | [ ] 10 Tech Writer — name? | Cross-cutting + Evolution |

See [`TEAM-FLOW.md`](../TEAM-FLOW.md) for handoff diagrams and the daily timeline.

## How to Use Copilot (3 modes)

| Mode | When to use | Example |
|------|-------------|---------|
| **Chat** | Explore, plan, debate trade-offs | "Explain this Natural program line by line" |
| **Edits** | Multi-file implementation with review | "Create the `notification` bounded context with domain/application/infrastructure" |
| **Agent** | Delegate complete features via an Issue | "Implement REQ-PAY-03: cycle generation with audit log" |

> See [`cheat-sheets/copilot-3-modes.md`](../cheat-sheets/copilot-3-modes.md) for
> detailed guidance and prompt examples.

## Hard Rules — Don't Do These

- ❌ Don't generate code without first checking the existing prototype in [`prototype/`](../prototype) (symlinked by `scripts/setup.sh`)
- ❌ Don't write an EARS without `source_legacy:` — CI will reject the PR
- ❌ Don't add dependencies without justification in an ADR
- ❌ Don't write tests after the fact — write them as you implement
- ❌ Don't expose secrets in commit messages, logs, or PR descriptions
- ❌ Don't merge to `main` without at least one cross-pair review
- ❌ Don't skip the handoff walkthroughs at stage transitions (see [`TEAM-FLOW.md`](../TEAM-FLOW.md))

## References

- [Team Flow](../TEAM-FLOW.md) — daily timeline, handoffs, escalation
- [Personas](../personas/) — your 2 role cards (one per persona in your pair)
- [Persona Kits](../persona-kits/) — Copilot agents, prompts, skills (copy your 2 kits into this `.github/`)
- [Cheat Sheets](../cheat-sheets/) — Copilot, Specky, model routing
- [Bundled Legacy](../legacy/) — what you're modernizing (15 .NSN programs + 4 DDMs)
- [`01-arqueologia/LEGACY-EXPLORATION-CHECKLIST.md`](../01-arqueologia/LEGACY-EXPLORATION-CHECKLIST.md) — HARD GATE before Stage 2
- [Reference Prototype](../prototype) — running starter code (symlink, created by setup.sh)
- [Infrastructure modules](../infra) — Terraform Azure modules (symlink, created by setup.sh)
- [Specky SDD Plugin](https://github.com/paulasilvatech/specky) — Spec-Driven Development engine
- Trilingual didactic docs: [`pt-br/`](../pt-br/) · [`es/`](../es/) · [`en/`](../en/)
