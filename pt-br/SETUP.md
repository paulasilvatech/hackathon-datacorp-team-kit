---
title: "Guia de Setup — Do Zero ao Código"
description: "Passo a passo completo e amigável para iniciantes: criar o repositório GitHub do time, adicionar membros, ativar o Copilot, instalar o Spec-Kit oficial do GitHub, definir a estratégia de branches e configurar o kit Copilot de cada persona"
locale: "pt-br"
canonical_path: "SETUP.md"
author: "Paula Silva, Americas Software GBB, Microsoft"
date: "2026-04-29"
version: "2.1.0"
status: "approved"
tags:
  [
    "setup",
    "onboarding",
    "github",
    "copilot",
    "spec-kit",
    "hackathon",
    "datacorp",
    "iniciante",
  ]
---

<!-- markdownlint-disable MD013 MD025 MD026 MD028 MD029 MD034 MD040 MD051 MD060 -->

# Guia de Setup — Do Zero ao Código

> **Vocês são 5 pessoas. Cada pessoa usa 2 personas. Vocês têm um dia de trabalho.** Este guia leva vocês de "ainda não temos nada" até "primeiro commit enviado, Copilot funcionando, todas as personas prontas" em **45 minutos**.
>
> **Todas as pessoas do time devem acompanhar no próprio laptop.** Uma pessoa compartilha a tela com os passos, e as outras 4 repetem. Ao final, cada laptop estará totalmente configurado.
>
> ⚠️ **Usuários de Windows**: todos os comandos de terminal abaixo assumem **Git Bash** ou **WSL**. **Não** use PowerShell ou CMD — `cp -R`, `chmod`, `rm -rf` e a sintaxe de heredoc não vão funcionar.

## Sumário

- [📋 Antes de Começar — Modelo Mental](#-antes-de-começar--modelo-mental)
- [✅ Passo 1 — Verifique se seu laptop tem os pré-requisitos](#-passo-1--verifique-se-seu-laptop-tem-os-pré-requisitos)
- [👥 Passo 2 — Crie o repositório GitHub do time (somente lead)](#-passo-2--crie-o-repositório-github-do-time-somente-lead)
- [📥 Passo 3 — Faça o bootstrap do repositório do time a partir deste kit (somente lead)](#-passo-3--faça-o-bootstrap-do-repositório-do-time-a-partir-deste-kit-somente-lead)
- [🛡️ Passo 4 — Proteja a branch `main` (somente lead)](#%EF%B8%8F-passo-4--proteja-a-branch-main-somente-lead)
- [🎟️ Passo 5 — Adicione os outros 4 membros do time (somente lead)](#%EF%B8%8F-passo-5--adicione-os-outros-4-membros-do-time-somente-lead)
- [💻 Passo 6 — Cada membro clona o repositório do time](#-passo-6--cada-membro-clona-o-repositório-do-time)
- [🤖 Passo 7 — Ative o GitHub Copilot no VS Code (todos)](#-passo-7--ative-o-github-copilot-no-vs-code-todos)
- [🎭 Passo 8 — Instale o kit Copilot da sua persona (todos)](#-passo-8--instale-o-kit-copilot-da-sua-persona-todos)
- [📐 Passo 9 — Instale o Spec-Kit (todos)](#-passo-9--instale-o-spec-kit-todos)
- [🎯 Passo 10 — Use o fluxo Spec-Kit (todos)](#-passo-10--use-o-fluxo-spec-kit-todos)
- [🌿 Passo 11 — Entenda a estratégia de branches](#-passo-11--entenda-a-estratégia-de-branches)
- [🔄 Passo 12 — Fluxo diário por persona](#-passo-12--fluxo-diário-por-persona)
- [🚦 Passo 13 — Rode o smoke test (time inteiro, às 09:30)](#-passo-13--rode-o-smoke-test-time-inteiro-às-0930)
- [🆘 Troubleshooting](#-troubleshooting)

---

## 📋 Antes de Começar — Modelo Mental

Você vai terminar com **3 repositórios no seu laptop**:

```
~/Code/
├── kit/                            (this team-kit, READ-ONLY reference)
├── reference/sifap-legacy/         (legacy SIFAP code, READ-ONLY reference)
└── hackathon-team-XX/              (YOUR team's working repo — where you commit)
```

| Repo                | O que você faz com ele                                       | Onde ele fica                                                        |
| ------------------- | ------------------------------------------------------------ | -------------------------------------------------------------------- |
| `team-kit`          | Você lê a documentação e copia partes dele uma vez no início | github.com/paulasilvatech/hackathon-datacorp-team-kit (public)       |
| `sifap-legacy`      | Você lê durante o Stage 1 — nunca edita                      | github.com/paulasilvatech/sifap-legacy (public)                      |
| `hackathon-team-XX` | **Todo o seu trabalho vai aqui**                             | github.com/<YOUR_GITHUB_USER>/hackathon-team-XX (private, você cria) |

> **Regra-chave.** Nunca faça push para o kit ou para o sifap-legacy. Os commits do seu time vão somente para `hackathon-team-XX`.

---

## ✅ Passo 1 — Verifique se seu laptop tem os pré-requisitos

**Cada membro do time roda este checklist no próprio laptop.**

| Ferramenta         | Versão mínima | Como verificar                           | Se estiver faltando                                 |
| ------------------ | ------------- | ---------------------------------------- | --------------------------------------------------- |
| **Git**            | 2.40+         | Abra um terminal, digite `git --version` | <https://git-scm.com/downloads>                     |
| **Conta GitHub**   | —             | Acesse github.com e faça sign in         | <https://github.com/signup>                         |
| **GitHub CLI**     | 2.40+         | `gh --version`                           | <https://cli.github.com>                            |
| **VS Code**        | 1.93+         | Abra o VS Code, **Help → About**         | <https://code.visualstudio.com/download>            |
| **Docker Desktop** | 4.30+         | `docker --version` E abra o app Docker   | <https://www.docker.com/products/docker-desktop>    |
| **Java 21 JDK**    | 21            | `java -version`                          | <https://learn.microsoft.com/java/openjdk/download> |
| **Node.js**        | 20 LTS        | `node --version`                         | <https://nodejs.org/en/download>                    |

> **Faltando a maioria desses itens?** O caminho mais rápido é usar o **dev container** (Passo 6.4). Ele inclui todas as ferramentas. Você só precisa que o Docker Desktop esteja rodando.

### Verificação de licença (uma pessoa verifica pelo time)

1. Abra <https://github.com/settings/copilot> no navegador.
2. Você deve ver **"Active subscription"** (Individual) ou **"Business plan"** no topo.
3. Se você vir "Get GitHub Copilot", levante a mão para o time de facilitadores do cordão azul.

---

## 👥 Passo 2 — Crie o repositório GitHub do time (somente lead)

**Escolham uma pessoa para ser o team lead** (normalmente quem cobre a persona Technical Lead no Par 3). Somente o lead faz os Passos 2 a 5. As outras 4 pessoas aguardam e seguem a partir do Passo 6.

### Opção A — usando o site (mais fácil para iniciantes)

1. Abra <https://github.com/new> no navegador.
2. Preencha:
   - **Owner**: **seu próprio usuário GitHub** (**não** escolha `paulasilvatech` — os times não têm permissão de admin lá). Se o seu time tiver uma organização GitHub própria e você for admin dela, pode usá-la.
   - **Repository name**: `hackathon-team-XX` (substitua XX pelo número do seu time, por exemplo, `hackathon-team-01`)
   - **Description**: `Hackathon DATACORP 2026 — Team XX`
   - **Visibility**: **Private** ✅
3. **NÃO** marque nenhuma caixa de inicialização. Deixe todas desmarcadas:
   - ❌ Add a README file
   - ❌ Add .gitignore
   - ❌ Choose a license
4. Clique no botão verde **Create repository**.

> **Por que vazio?** No Passo 3, o lead vai enviar todo o conteúdo do team-kit como primeiro commit. Começar vazio evita conflitos de merge.

Você agora deve ver a página "Quick setup" do GitHub com instruções de push. Mantenha essa aba aberta.

### Opção B — usando a GitHub CLI (mais rápido, mas exige mais digitação)

Abra um terminal e rode:

```bash
# Sign in once per laptop — opens a browser to authorize
gh auth login

# Create the repo (replace 01 with your team number)
# Use just the repo name — no owner prefix. Creates the repo under YOUR GitHub user.
# The repo must be empty (no --add-readme) so the bootstrap push in Step 3 works.
gh repo create hackathon-team-01 \
  --private \
  --description "Hackathon DATACORP 2026 — Team 01"
```

Se o comando imprimir uma URL terminando em `hackathon-team-01`, está pronto.

---

## 📥 Passo 3 — Faça o bootstrap do repositório do time a partir deste kit (somente lead)

Agora copiamos tudo deste team-kit para o repositório vazio do time, para que vocês tenham todos os templates, personas, scripts e workflows de CI prontos.

```bash
# 1. Pick a folder for all your code
mkdir -p ~/Code && cd ~/Code

# 2. Clone this team kit (read-only reference)
git clone https://github.com/paulasilvatech/hackathon-datacorp-team-kit.git kit

# 3. Create a local repo from the kit (excluding kit's git history)
cp -R kit hackathon-team-01
cd hackathon-team-01
rm -rf .git
git init -b main
git remote add origin https://github.com/<YOUR_GITHUB_USER>/hackathon-team-01.git

# 4. Make scripts executable (one-time fix)
chmod +x scripts/*.sh
```

### Rode o script de bootstrap

Isso clona o repositório read-only `sifap-legacy` dentro de `reference/`, cria o symlink `legacy/` e inicializa a base de specs usada pelo Spec-Kit.

```bash
./scripts/setup.sh
```

Se terminar com **"Done."** e listar "Next steps", está tudo certo. Se der erro, veja a seção [Troubleshooting](#-troubleshooting).

### Primeiro commit e push

```bash
git add -A
git commit -m "chore: bootstrap team kit"
git push -u origin main
```

Você deve ver "Branch 'main' set up to track remote branch 'main' from 'origin'." Isso significa que o push funcionou.

> ⚠️ **Importante.** De agora em diante, você nunca deve fazer push diretamente para `main`. O Passo 4 protege essa branch.

### Crie a branch de integração `develop`

```bash
git checkout -b develop
git push -u origin develop
```

`develop` é onde as branches de feature de todo mundo serão integradas. Promoções para `main` acontecem via PR depois de cada estágio.

---

## 🛡️ Passo 4 — Proteja a branch `main` (somente lead)

Isso impede que qualquer pessoa (exceto o admin do repositório) faça push direto para `main`. Toda mudança deve passar por um Pull Request.

> ⚠️ **Contas GitHub Free**: proteção de branch em repositórios **privados** exige **GitHub Pro**, **GitHub Team** ou **GitHub Enterprise**. Se sua conta está no plano gratuito, deixe o repositório **público** ou pule este passo (cumpram a regra de não fazer push direto por convenção).

### Usando o site

1. Vá para **Settings** → **Branches** (barra lateral esquerda).
2. Em **Branch protection rules**, clique em **Add rule**.
3. Branch name pattern: `main`
4. Marque:
   - **Require a pull request before merging** ✅
   - **Require approvals** — defina como `1`
   - **Require conversation resolution before merging** ✅
5. Clique em **Create**.

### Usando a CLI

```bash
gh api -X PUT "repos/<YOUR_GITHUB_USER>/hackathon-team-01/branches/main/protection" \
  --input - <<'JSON'
{
  "required_status_checks": null,
  "enforce_admins": true,
  "required_pull_request_reviews": {
    "required_approving_review_count": 1,
    "dismiss_stale_reviews": false,
    "require_code_owner_reviews": false
  },
  "restrictions": null,
  "required_conversation_resolution": true
}
JSON
```

> **Por que isso importa.** Sem essa regra, alguém do time eventualmente vai enviar um typo para `main` no minuto 90 e o demo vai falhar no minuto 480. Custo: 30 segundos. Economia: horas.

---

## 🎟️ Passo 5 — Adicione os outros 4 membros do time (somente lead)

O lead convida o restante do time para que todo mundo possa fazer push e pull.

### Opção A — usando o site

1. Vá para o repositório no GitHub: `https://github.com/<YOUR_GITHUB_USER>/hackathon-team-XX`
2. Clique em **Settings** (aba superior — exige permissão de admin, que o lead tem).
3. Na barra lateral esquerda, clique em **Collaborators**.
4. Clique em **Add people**.
5. Digite o usuário GitHub (por exemplo, `alice-builder`) e escolha na lista.
6. **Choose the role**: escolha **Write** (não Admin, não Read).
7. Clique em **Add ... to this repository**.
8. Repita para as outras 3 pessoas.

> **Dica.** Cada pessoa convidada recebe um email e uma notificação dentro do GitHub. Ela precisa clicar em **Accept invitation** antes de conseguir fazer push.

### Opção B — usando a CLI

Uma vez por colega:

```bash
# Replace alice with the actual GitHub username
gh api -X PUT "repos/<YOUR_GITHUB_USER>/hackathon-team-01/collaborators/alice" \
  -f permission=write
```

Ou em loop:

```bash
for user in alice bob carla dani; do
  gh api -X PUT "repos/<YOUR_GITHUB_USER>/hackathon-team-01/collaborators/${user}" \
    -f permission=write
done
```

---

## 💻 Passo 6 — Cada membro clona o repositório do time

**Agora todo mundo entra.** Os outros 4 membros do time fazem isto.

### 6.1 Aceite o convite

1. Abra o email do GitHub com o título **"[username] invited you to ..."** (ou confira o ícone de sino 🔔 em github.com).
2. Clique em **View invitation** → **Accept invitation**.

### 6.2 Clone e mude para `develop`

```bash
mkdir -p ~/Code && cd ~/Code

# Replace 01 with your actual team number, and <YOUR_GITHUB_USER> with the lead's username
git clone https://github.com/<YOUR_GITHUB_USER>/hackathon-team-01.git
cd hackathon-team-01

# Switch to the develop branch (where day-to-day work happens)
git checkout develop
```

### 6.3 Abra no VS Code

```bash
code .
```

### 6.4 Reabra no Dev Container (altamente recomendado)

O repositório inclui `.devcontainer/devcontainer.json`. O dev container tem Java 21, Node 20, Docker-in-Docker e as extensões do Copilot já fixadas em versões conhecidas e boas.

1. O VS Code mostra um popup no canto inferior direito: **"Folder contains a Dev Container configuration. Reopen in Container?"** → clique em **Reopen in Container**.
2. Se você perdeu o popup: abra a Command Palette (`Ctrl+Shift+P` no Windows/Linux, `Cmd+Shift+P` no Mac) e escolha **Dev Containers: Reopen in Container**.
3. Aguarde 2 a 5 minutos na primeira vez. O VS Code reconstrói o ambiente.
4. Quando o canto inferior esquerdo mostrar **"Dev Container: SIFAP 2.0 …"**, você está dentro.

### 6.5 Faça o bootstrap também na sua máquina

Mesmo que o lead já tenha feito o bootstrap do repositório, cada membro precisa materializar localmente o symlink `legacy/`:

```bash
./scripts/setup.sh
```

---

## 🤖 Passo 7 — Ative o GitHub Copilot no VS Code (todos)

Cada pessoa faz isto no próprio laptop.

### 7.1 Faça sign in

1. No VS Code, olhe para a barra de status inferior. Clique no ícone do **Copilot** (🤖).
2. Escolha **Sign in with GitHub**.
3. Uma janela do navegador abre. Clique em **Authorize Visual Studio Code**.
4. Volte para o VS Code. Aguarde "Copilot ready" perto do canto inferior direito.

### 7.2 Abra o painel do Copilot Chat

| SO              | Atalho       |
| --------------- | ------------ |
| Mac             | `Cmd+Ctrl+I` |
| Windows / Linux | `Ctrl+Alt+I` |

Um painel abre à direita.

### 7.3 Verifique se os 3 modos estão disponíveis

No topo do painel de chat há um dropdown:

| Modo      | Quando usar                                                      |
| --------- | ---------------------------------------------------------------- |
| **Ask**   | Fazer perguntas, explorar código, discutir opções                |
| **Plan**  | Planejar mudanças multi-arquivo antes da execução                |
| **Agent** | Delegar uma feature inteira via Issue e depois revisar o PR      |

Clique no dropdown para confirmar que os três aparecem. Se **Plan** ou **Agent** não aparecerem, atualize o VS Code para uma versão recente ou use VS Code Insiders, que sempre tem o mais novo primeiro.

### 7.4 Smoke test do Copilot

No painel de Chat, digite:

```
What stack are we using on this project?
```

Ele deve responder com **Java 21 + Spring Boot 3.3 + Next.js 15 + PostgreSQL 16**. Se não responder, o arquivo `.github/copilot-instructions.md` do projeto não está sendo carregado — veja [Troubleshooting](#-troubleshooting).

---

## 🎭 Passo 8 — Instale o kit Copilot da sua persona (todos)

Cada uma das 10 personas do workshop tem um **kit Copilot correspondente**. Como o time tem 5 pessoas e cada pessoa usa duas personas, você instala os dois kits do seu par.

### 8.1 Encontre seu papel

Abra `persona-kits/` no VS Code. Você verá 10 pastas, numeradas de 01 a 10. Dentro da pasta do seu papel, leia `PERSONA.md` de ponta a ponta (~10 minutos). Ele diz:

- O que você faz nos 4 estágios
- Qual modo do Copilot usar
- Prompts específicos que você pode copiar/colar
- De quem você depende e quem depende de você

### 8.2 Instale seu kit

Cada persona fica inteiramente consolidada em `persona-kits/<role>/`. A mesma pasta contém a carta da persona e o kit Copilot:

- `PERSONA.md` — responsabilidades, handoffs, prompts de exemplo e rubrica do papel
- `.github/agents/<role>.agent.md` — agente Copilot pré-configurado
- `.github/prompts/<command>.prompt.md` — slash commands para tarefas recorrentes
- `.github/skills/<skill>/SKILL.md` — modelos mentais reutilizáveis
- `mcp.json` — configuração de servidor MCP (se houver)

Para instalar seu kit, copie o conteúdo de `.github/` dele para `.github/` no repositório do time:

```bash
# Replace XX-your-role with your actual persona id
# e.g., 06-developer, 09-devops-engineer, 10-tech-writer
cp -r persona-kits/XX-your-role/.github/* .github/

# If your kit has mcp.json, copy it into .vscode/
[ -f persona-kits/XX-your-role/mcp.json ] && \
  mkdir -p .vscode && \
  cp persona-kits/XX-your-role/mcp.json .vscode/mcp.json
```

### 8.3 Mapeamento persona-para-kit

As 10 personas cobertas pelas 5 pessoas do time estão nestes 10 kits:

| Persona | Kit consolidado |
| --- | --- |
| Product Owner | `persona-kits/01-product-owner/PERSONA.md` |
| Requirements Engineer | `persona-kits/02-requirements-engineer/PERSONA.md` |
| Enterprise Architect | `persona-kits/03-enterprise-architect/PERSONA.md` |
| Software Architect | `persona-kits/04-software-architect/PERSONA.md` |
| Technical Lead | `persona-kits/05-technical-lead/PERSONA.md` |
| Developer | `persona-kits/06-developer/PERSONA.md` |
| DBA | `persona-kits/07-dba/PERSONA.md` |
| QA Engineer | `persona-kits/08-qa-engineer/PERSONA.md` |
| DevOps Engineer | `persona-kits/09-devops-engineer/PERSONA.md` |
| Tech Writer | `persona-kits/10-tech-writer/PERSONA.md` |

### 8.4 Atualize o `copilot-instructions.md` do time

Depois que cada persona instalar seu kit, o **team lead** atualiza o arquivo `.github/copilot-instructions.md` com os nomes de todo mundo. Encontre esta seção:

```markdown
## Active Personas on This Team

- [ ] 01 — Product Owner
- [ ] 02 — Requirements Engineer
      ...
```

Marque as caixas e escreva o nome ao lado de cada papel:

```markdown
- [x] 01 — Product Owner — Maria Santos
- [x] 02 — Requirements Engineer — João Silva
- [x] 03 — Enterprise Architect — Ana Costa
      ...
```

Faça commit e push para `develop`. Agora as sugestões do Copilot sabem quem está no seu time.

---

## 📐 Passo 9 — Instale o Spec-Kit (todos)

[**Spec-Kit**](https://github.com/github/spec-kit) é o toolkit oficial do GitHub para desenvolvimento orientado por especificação. Use para **rascunhos rápidos de features** no Stage 2.

### 9.1 Instale o Specify CLI no seu laptop

O comando oficial usa `uv` e instala diretamente do repositório `github/spec-kit`. Substitua `vX.Y.Z` pela versão mais recente em <https://github.com/github/spec-kit/releases>.

```bash
uv tool install specify-cli --from git+https://github.com/github/spec-kit.git@vX.Y.Z
specify version
```

### 9.2 Inicialize no repositório do time

Rode isto uma vez, na raiz do repositório do time:

```bash
specify init . --integration copilot
```

Isso cria a configuração `.specify/`, scripts de automação e os slash commands `/speckit.*` para o GitHub Copilot.

### 9.3 Verifique os comandos no Copilot

Depois de recarregar o VS Code, os comandos principais devem aparecer no painel do Copilot:

| Comando | Quando usar |
| --- | --- |
| `/speckit.constitution` | Define princípios, padrões e gates do projeto |
| `/speckit.specify` | Cria a spec da feature |
| `/speckit.clarify` | Resolve ambiguidades antes do plano |
| `/speckit.plan` | Cria o plano técnico |
| `/speckit.tasks` | Gera tasks implementáveis |
| `/speckit.analyze` | Checa consistência e cobertura |
| `/speckit.implement` | Implementa a feature guiada pela spec |

### 9.4 Escreva uma feature

No Copilot Chat:

```text
/speckit.specify Allow operators to generate a monthly payment cycle for active beneficiaries. Preserve legacy traceability with source_legacy for every requirement.
```

O Spec-Kit cria uma branch numerada e a estrutura:

```text
specs/001-payment-cycle-generation/
├── spec.md
└── (outros artefatos criados nos próximos comandos)
```

Em seguida, rode:

```text
/speckit.clarify
/speckit.plan Use Java 21, Spring Boot 3.3, PostgreSQL 16, Next.js 15 and the modular monolith architecture from the workshop.
/speckit.tasks
```

### 9.5 Regra do workshop

Todo requisito que vier do legado continua precisando de `source_legacy:` apontando para `.NSN` ou `.ddm`. Requisitos sem paralelo no legado usam `[GREENFIELD]` com justificativa.

---

## 🎯 Passo 10 — Use o fluxo Spec-Kit (todos)

Para o workshop, use esta sequência única do Spec-Kit:

| Fase | Comando | Saída principal | Persona dona |
| --- | --- | --- | --- |
| Constituição | `/speckit.constitution` | `.specify/memory/constitution.md` | Technical Lead + Architect |
| Spec | `/speckit.specify` | `specs/<feature>/spec.md` | Requirements Engineer |
| Clarificação | `/speckit.clarify` | Perguntas resolvidas na spec | Requirements Engineer + Product Owner |
| Plano | `/speckit.plan` | `specs/<feature>/plan.md` | Software Architect |
| Tasks | `/speckit.tasks` | `specs/<feature>/tasks.md` | Technical Lead |
| Análise | `/speckit.analyze` | Lacunas e inconsistências | QA Engineer + Architect |
| Implementação | `/speckit.implement` | Código + testes guiados pela spec | Developer + QA Engineer |

> **Gates LGTM.** O time revisa explicitamente `spec.md`, `plan.md` e `tasks.md` antes de implementar.

---

## 🌿 Passo 11 — Entenda a estratégia de branches

Seu time tem **5 categorias de branches**. Use o tipo certo para o trabalho certo.

```
main                    ← release-ready, protected, 1 reviewer required
develop                 ← integration of all features
spec/NNN-feature        ← Specification work (Stage 2)
impl/NNN-feature        ← Implementation work (Stage 3)
infra/NNN-azure         ← Infrastructure work (Stage 4)
```

### Convenção de nomes

| Tipo           | Padrão                 | Exemplo                             |
| -------------- | ---------------------- | ----------------------------------- |
| Spec           | `spec/NNN-kebab-name`  | `spec/001-payment-cycle-generation` |
| Implementation | `impl/NNN-kebab-name`  | `impl/001-payment-cycle-generation` |
| Infrastructure | `infra/NNN-kebab-name` | `infra/001-azure-deployment`        |

`NNN` é o número da feature (corresponde à pasta em `specs/NNN-...`).

### Criando uma branch de feature

```bash
# Make sure you're on develop with latest changes
git checkout develop
git pull

# Create your feature branch
git checkout -b spec/001-payment-cycle-generation

# Work, commit
git add -A
git commit -m "feat(payments): draft EARS requirements for cycle generation"

# Push to origin
git push -u origin spec/001-payment-cycle-generation
```

### Abrindo um Pull Request

1. Depois do push, o GitHub imprime uma URL como `https://github.com/.../pull/new/spec/001-...`. Clique nela (ou cole no navegador).
2. Título: use Conventional Commits — `feat(payments): add cycle generation spec`
3. Descrição: o GitHub carrega automaticamente o template (`.github/PULL_REQUEST_TEMPLATE.md`). Preencha:
   - **What changed** (um parágrafo)
   - **REQ-IDs implemented** (por exemplo, `REQ-PAY-014, REQ-PAY-015`)
   - **How to test** (o reviewer faz pull e roda isto)
   - **Linked issues** (por exemplo, `Closes #12`)
4. **Reviewers**: adicione pelo menos uma pessoa de outra persona.
5. Clique em **Create pull request**.
6. O CI roda (workflow `.github/workflows/ci.yml`). Aguarde o check verde.
7. Depois da aprovação, clique em **Rebase and merge** (não Merge commit, não Squash).
8. Delete a branch de feature quando solicitado.

---

## 🔄 Passo 12 — Fluxo diário por persona

Cada persona tem um **loop diário padrão**. Rode-o quantas vezes forem necessárias durante o dia.

### 🧠 Product Owner / Requirements Engineer

```
1. Read the Stage 1 findings (glossary, business rules catalog)
2. Run /speckit.specify "feature-name" with source_legacy guidance
3. Run /speckit.clarify and validate with stakeholder personas (PO + EA)
4. Run /speckit.plan with the workshop stack and architecture choices
5. Run /speckit.tasks after the plan is approved
6. Open a PR on branch spec/NNN-feature-name
7. Hand off to Software Architect (LGTM gate)
```

### 🏗️ Enterprise Architect / Software Architect

```
1. Pull latest develop
2. git checkout spec/NNN-feature-name (read the EARS spec)
3. Run /speckit.plan → produces plan.md, research.md and contracts
4. Add ADRs in docs/adr/ for non-trivial decisions
5. Open a PR — review the spec PR's design section
6. Hand off to Tech Lead (LGTM gate)
```

### 🧠 Technical Lead

```
1. Read the approved `plan.md` and ADRs
2. Run /speckit.tasks → produces tasks.md with task IDs (T001, T002, ...)
3. Open a GitHub Issue per task using .github/ISSUE_TEMPLATE/task.yml
4. Assign each issue to a Developer / DBA / QA
5. Watch CI green/red, unblock people
```

### 💻 Developer

```
1. Pick a task issue (T-NNN) from the team board
2. git checkout -b impl/NNN-task-name (from develop)
3. In Copilot, run /implement (your prompt is in 06-developer/.github/prompts/)
4. Tests first (red), code (green), refactor
5. ./scripts/check.sh (mirrors CI)
6. git commit, git push, open PR
7. Tag the issue with "Closes #NN" in the PR body
```

### 🗃️ DBA

```
1. Pick a schema/migration task
2. git checkout -b impl/NNN-migration-name
3. Add Flyway migration in backend/src/main/resources/db/migration/
4. Run /migration prompt (in 07-dba/.github/prompts/)
5. Test locally with docker compose up
6. Open PR, request Developer review
```

### 🧪 QA Engineer

```
1. Watch every implementation PR
2. Run /coverage-gaps prompt to find uncovered REQ-IDs
3. Add tests on the implementation branch (pair with Developer)
4. /test-strategy prompt produces a test plan for new features
5. Block merge if coverage drops below 70%
```

### ⚙️ DevOps Engineer

```
1. Pick an infra task (Azure setup, CI/CD, deployment)
2. git checkout -b infra/NNN-azure-foo
3. Edit infra/ Terraform modules
4. terraform fmt + terraform validate locally
5. Run /iac-module prompt (in 09-devops-engineer/.github/prompts/)
6. Open PR, the workflows/ci.yml runs Terraform validation
```

### 📝 Tech Writer

```
1. After every merge to develop, scan for ADR/glossary drift
2. Run /doc-drift prompt (in 10-tech-writer/.github/prompts/)
3. Update docs/glossary.md, docs/adr/, READMEs
4. Open a small PR per documentation update
```

---

## 🚦 Passo 13 — Rode o smoke test (time inteiro, às 09:30)

O team lead lê cada item em voz alta. Cada pessoa confirma no próprio laptop.

- [ ] Cada membro clonou `hackathon-team-XX`
- [ ] Cada membro consegue rodar `git checkout develop && git pull origin develop` (acesso de escrita confirmado)
- [ ] CI rodou no commit de bootstrap — check verde na aba **Actions**
- [ ] `docker compose up -d` conclui com sucesso (ou o facilitador entrega o tarball do prototype no Stage 3)
- [ ] Cada Copilot Chat responde "What stack are we using?" com a resposta certa
- [ ] Cada membro instalou o Spec-Kit oficial: `specify version` imprime uma versão
- [ ] Os comandos `/speckit.*` aparecem no Copilot depois de `specify init . --integration copilot`
- [ ] Abrir **New issue** no GitHub mostra 3 templates (spec, adr, task)
- [ ] Todos os 5 membros do time aparecem em repo Settings → Collaborators
- [ ] Cada persona leu sua carta em `persona-kits/XX-role/PERSONA.md`
- [ ] O team lead atualizou `.github/copilot-instructions.md` com os nomes de todo mundo
- [ ] Cada persona instalou seu kit: `cp -r persona-kits/XX/.github/* .github/`
- [ ] [`TEAM-FLOW.md`](TEAM-FLOW.md) foi lido em voz alta uma vez (a linha do tempo do dia)

Quando os 13 itens estiverem verdes, seu time está pronto para o **Stage 1: Archaeology**.

---

## 🆘 Troubleshooting

### Copilot não lê `copilot-instructions.md`

- O VS Code precisa estar aberto **na raiz do repositório**, não dentro de uma subpasta.
- Reinicie o VS Code depois de editar o arquivo.
- Em Settings, verifique se `github.copilot.chat.useProjectInstructions` está como `true` (padrão na 1.93+).

### `gh repo create` retorna 422

- O nome já está em uso. Aumente o número (`hackathon-team-01b`).
- Ou crie pelo site (Opção A em [§2](#-passo-2--crie-o-repositório-github-do-time-somente-lead)).

### `specify init` falha ou os comandos `/speckit.*` não aparecem

- Confirme que `uv`, Python 3.11+ e Git estão instalados.
- Rode `specify version` para garantir que você instalou o CLI oficial.
- Reexecute `specify init . --integration copilot` na raiz do repositório.
- Recarregue o VS Code: Command Palette → **Developer: Reload Window**.

### CI falha no primeiro push com "no tests found"

- Esperado. O workflow `ci.yml` só roda jobs cujos caminhos mudaram. Quando código backend/frontend entrar, os jobs relevantes vão rodar.

### Docker compose up trava ou falha

- As portas 5432, 8080 ou 3000 podem estar em uso. Rode:

  ```bash
  lsof -i :5432 -i :8080 -i :3000
  ```

  Mate o processo que está ocupando a porta (`kill -9 <PID>`) e tente de novo.

- Garanta que o Docker Desktop está **rodando** (o ícone na barra de menu deve estar estável, não animado).

### Copilot Agent mode não aparece no dropdown

- Atualize o VS Code para **1.93 ou posterior** (ou instale **VS Code Insiders**, que sempre tem esse recurso).
- Recarregue a janela: Command Palette → **Developer: Reload Window**.

### "Permission denied" ao fazer push para `main`

- A proteção de branch (Passo 4) está fazendo seu trabalho. Abra um Pull Request a partir da sua branch de feature.

### Fiz pull do `develop` mais recente, mas minha IDE ainda mostra código antigo

- Recarregue a janela do VS Code: Command Palette → **Developer: Reload Window**.
- Se você estiver dentro de um dev container, às vezes também precisa: Command Palette → **Dev Containers: Rebuild Container**.

### A instalação do persona kit quebrou minha pasta `.github/`

- O `.github/` do kit foi feito para **adicionar** ao que já existe, não sobrescrever.
- Se algo parecer quebrado: `git checkout main -- .github/` para restaurar, depois `cp -r persona-kits/XX/.github/* .github/` de novo.

---

## 🧭 Navegação

| Pai                 | Home                   | Próximo                      |
| ------------------- | ---------------------- | ---------------------------- |
| [README](README.md) | [Kit PT-BR](README.md) | [TEAM-FLOW.md](TEAM-FLOW.md) |

— Paula
