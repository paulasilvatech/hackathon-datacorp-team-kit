---
title: "Estagio 4 - Evolucao com Agentes"
description: "Guia para usar GitHub Copilot Agent Mode e Terraform para evoluir o SIFAP 2.0"
---

# Estagio 4 - Evolucao com Agentes (3 horas)

## Objetivo

Usar o **GitHub Copilot Agent Mode** para implementar features completas via Issues e Pull Requests, e explorar a infraestrutura como codigo (Terraform) para deploy na Azure.

---

## Parte 1: GitHub Copilot Agent Mode (2 horas)

### O que e o Agent Mode?

O **Copilot Agent Mode** e o terceiro modo do GitHub Copilot (alem de Chat e Edits). No Agent Mode, voce:

1. **Escreve uma Issue no GitHub** descrevendo a feature completa
2. **Aciona o Agent** no VS Code (via painel Copilot → "Start Agent" ou pelo Copilot Workspace no github.com)
3. **O Agent analisa todo o codebase**, planeja as mudancas, implementa codigo + testes + docs
4. **Abre um Pull Request** para voce revisar

Pense no Agent como um **dev junior muito rapido** - ele faz o trabalho braçal, mas VOCE precisa revisar tudo antes de mergear.

> **Diferenca entre os 3 modos:**
> - **Chat**: voce pergunta, Copilot responde (exploração, duvidas)
> - **Edits**: voce seleciona arquivos e descreve a mudanca, Copilot edita (implementacao guiada)
> - **Agent**: voce descreve a feature inteira via Issue, Copilot implementa sozinho (delegacao)

### Como escrever uma boa Issue para o Agent

Uma Issue bem escrita e 80% do sucesso. Siga este formato:

---

#### Exemplo Real: Notificacao de Pagamento por Email

```markdown
## Titulo
Adicionar notificacao por email na confirmacao de pagamento

## Descricao
Quando um pagamento for confirmado (status mudando de PENDING para APPROVED),
o sistema deve enviar um email de notificacao ao beneficiario informando
o valor e a data do pagamento.

## Requisitos Funcionais
- [ ] Quando o status de um pagamento mudar para APPROVED, enviar email
- [ ] O email deve conter: nome do beneficiario, valor, data, numero do pagamento
- [ ] Se o envio falhar, registrar no log de auditoria (nao bloquear o pagamento)
- [ ] O template do email deve ser configuravel

## Requisitos Tecnicos
- [ ] Criar um EmailService no modulo payment/application
- [ ] Usar Spring Mail com configuracao via application.yml
- [ ] Criar teste unitario mockando o envio de email
- [ ] Criar teste de integracao com MailHog (container Docker)
- [ ] Adicionar variavel SMTP_HOST no docker-compose.yml

## Arquitetura
- Seguir a estrutura modular existente (domain/application/infrastructure)
- O EmailService deve ser injetado no PaymentService
- Usar eventos Spring (ApplicationEvent) para desacoplar

## Criterios de Aceite
- [ ] Teste unitario passando
- [ ] Teste de integracao passando
- [ ] docker compose up funcional com MailHog
- [ ] Email recebido no MailHog ao aprovar pagamento via Swagger

## Contexto
- Backend: Java 21 + Spring Boot 3
- Modulo relevante: src/.../payment/
- Referencia: PaymentService.java, PaymentController.java
```

---

### Checklist para escrever Issues

Antes de submeter a Issue para o Agent, verifique:

- [ ] **Titulo claro** - descreve a feature em uma frase
- [ ] **Descricao com contexto** - o Agent precisa entender o "por que"
- [ ] **Requisitos como checklist** - itens verificaveis
- [ ] **Requisitos tecnicos** - onde no codigo, quais padroes seguir
- [ ] **Criterios de aceite** - como saber que esta pronto
- [ ] **Referencias a arquivos** - ajuda o Agent a encontrar o codigo certo

### Workflow do Agent

1. **Crie a Issue** no GitHub com o formato acima
2. **Acione o Agent** (via Copilot Workspace ou VS Code)
3. **Aguarde o PR** - o Agent trabalha e abre um PR
4. **Revise o PR** usando o checklist abaixo
5. **Solicite ajustes** se necessario (comente no PR)
6. **Faca merge** quando estiver satisfeito

---

### Como Revisar um PR do Agent (Checklist de Qualidade)

Quando o Agent abrir um PR, revise com cuidado:

#### Corretude
- [ ] O codigo compila sem erros?
- [ ] Os testes passam? (`./mvnw test`)
- [ ] A funcionalidade funciona como descrito na Issue?

#### Arquitetura
- [ ] Segue a estrutura modular (domain/application/infrastructure)?
- [ ] Nao ha imports circulares entre modulos?
- [ ] A camada domain nao importa classes de infrastructure?

#### Qualidade
- [ ] Nomes de classes, metodos e variaveis sao claros?
- [ ] Ha tratamento de erros adequado?
- [ ] Ha validacao de entrada (Bean Validation)?
- [ ] Nao ha credenciais hardcoded?

#### Testes
- [ ] Ha testes unitarios para a logica de negocio?
- [ ] Ha testes de integracao para os endpoints?
- [ ] Os testes cobrem casos de erro (nao apenas o happy path)?

#### Documentacao
- [ ] Endpoints novos aparecem no Swagger?
- [ ] Ha JavaDoc nos metodos publicos?
- [ ] O README foi atualizado se necessario?

---

## Parte 2: Terraform e Infraestrutura (1 hora)

### Visao Geral

Os modulos Terraform para deploy na Azure estao em:

```
05-terraform-azure/
|-- main.tf                  # Modulo raiz
|-- variables.tf             # Variaveis de entrada
|-- outputs.tf               # Saidas
|-- modules/
|   |-- resource-group/      # Grupo de recursos Azure
|   |-- container-registry/  # ACR para imagens Docker
|   |-- container-apps/      # Azure Container Apps
|   |-- postgresql/          # Azure Database for PostgreSQL
|   |-- key-vault/           # Azure Key Vault para secrets
|   |-- monitoring/          # Application Insights + Log Analytics
```

### O que explorar

1. **Leia o `main.tf`** - entenda como os modulos se conectam
2. **Veja as variaveis** - quais parametros sao configuraveis?
3. **Estude os outputs** - quais informacoes o Terraform exporta?
4. **Verifique o Key Vault** - como secrets sao gerenciados?

### Terraform na Pratica

Os modulos Terraform estao em `05-terraform-azure/`:

| Modulo | O que provisiona | Recurso Azure |
|--------|-----------------|---------------|
| `compute/` | Backend Java | App Service (B1 dev, P1v3 prod) |
| `database/` | Banco de dados | PostgreSQL Flexible Server |
| `frontend/` | Frontend Next.js | Static Web App |
| `registry/` | Imagens Docker | Azure Container Registry |
| `security/` | Segredos | Key Vault |
| `observability/` | Monitoramento | Application Insights + Log Analytics |
| `identity/` | Identidade | Azure AD / Entra ID |

#### Para explorar (nao precisa aplicar):

```bash
cd 05-terraform-azure/envs/dev
terraform init          # Inicializa providers
terraform plan          # Mostra o que SERIA criado (sem aplicar)
```

Exemplo de saida do `terraform plan`:
```
Plan: 12 to add, 0 to change, 0 to destroy.

  + azurerm_resource_group.sifap
  + azurerm_postgresql_flexible_server.sifap
  + azurerm_service_plan.sifap
  + azurerm_linux_web_app.sifap_backend
  + azurerm_static_web_app.sifap_frontend
  + azurerm_key_vault.sifap
  + azurerm_application_insights.sifap
  + azurerm_container_registry.sifap
  ...
```

> **Escopo do hackathon**: Explore e entenda os modulos. NAO aplique (`terraform apply`) - isso criaria recursos Azure com custo real. O `terraform plan` e suficiente para demonstrar conhecimento.

### Quando o Agent Falha

O Copilot Agent nao e perfeito. Problemas comuns:

| Sintoma | Causa provavel | O que fazer |
|---------|---------------|-------------|
| PR nao compila | Issue sem contexto tecnico suficiente | Adicione: arquitetura esperada, arquivos de referencia, padroes a seguir |
| Testes faltando no PR | Issue nao pediu testes | Adicione checkbox: "Incluir testes unitarios e de integracao" |
| Imports cruzam bounded context | Agent ignora fronteiras de modulo | Rejeite o PR, adicione na Issue: "Respeitar fronteiras domain/application/infrastructure" |
| PR com logica incorreta | Requisito ambiguo | Reescreva o requisito em EARS e abra nova Issue |
| Agent trava ou demora muito | Codebase grande demais | Restrinja o escopo: aponte arquivos especificos na Issue |

**Regra de ouro**: Se o Agent errou, a causa quase sempre esta na Issue. Melhore a Issue antes de tentar de novo.

### CI/CD: GitHub Actions

Os workflows de CI/CD estao em:

```
.github/workflows/
|-- ci.yml            # Build + test em cada PR
|-- cd-staging.yml    # Deploy automatico para staging
|-- cd-production.yml # Deploy para producao (manual approval)
```

#### Workflow de CI (ci.yml)

- Roda em cada Pull Request
- Passos: checkout -> setup Java 21 -> build -> test -> lint
- Se falhar, o PR nao pode ser mergeado

#### Workflow de CD (cd-staging.yml)

- Roda apos merge na branch `develop`
- Passos: build Docker image -> push para ACR -> deploy para Container Apps (staging)

---

## Entregaveis do Estagio 4

Ao final do Estagio 4, seu time deve ter:

- [ ] **2 Issues** criadas no formato adequado para o Agent
- [ ] **2 PRs** gerados pelo Agent (um para cada Issue)
- [ ] **1 feature mergeada** - pelo menos um PR deve ser aprovado e mergeado
- [ ] **Relatorio de experiencia com Agent** (arquivo: `04-evolucao/agent-experience-report.md`)

## Prompts para Copilot Chat

1. "Crie uma GitHub Issue para o Copilot Agent implementar [funcionalidade]"
2. "Revise este PR gerado pelo Agent e liste problemas de qualidade"
3. "Explique este modulo Terraform: [cole o codigo]"
4. "Quais recursos Azure este Terraform vai criar?"
5. "Crie um diagrama dos recursos Azure definidos neste Terraform"
6. "Como este workflow de CI/CD garante qualidade antes do deploy?"
7. "Sugira melhorias de seguranca para esta configuracao Terraform"

## Dica de Ouro

O Agent e tao bom quanto a Issue que voce escreve. Gaste **mais tempo na Issue** e **menos tempo corrigindo o PR**. Uma Issue com contexto claro, requisitos especificos e referencias a arquivos produz PRs muito melhores.
