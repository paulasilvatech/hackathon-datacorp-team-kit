# Plugin do GitHub Issues

## O que ele faz

Cria e sincroniza issues do GitHub a partir de tarefas de especificação SDD.
Cria issues em lote a partir de TASKS.md, mantém a rastreabilidade por REQ-ID e
gerencia labels e milestones.

## Use este plugin quando

- Criar issues a partir de TASKS.md
- Sincronizar artefatos SDD com um quadro de projeto do GitHub
- Abrir um conjunto de issues para trabalho em equipe em paralelo no workshop

## Ferramentas fornecidas

### `create_issue`

Cria uma única issue do GitHub a partir de uma descrição de tarefa.

### `create_issues_from_tasks`

Analisa TASKS.md e cria issues em lote, uma por tarefa, preservando a
rastreabilidade por REQ-ID no corpo.

### `add_labels`

Adiciona labels (função da persona, prioridade, área) a uma issue existente.

### `link_issues`

Adiciona referências `Depends on #N` entre issues para espelhar dependências de
tarefas.

### `move_to_milestone`

Vincula issues a uma milestone (por exemplo, 'Estágio 3 - Implementação').

## Configuração

### Configuração obrigatória

- `repo`: destino `owner/repo` para criação de issues.
- `github_token`: PAT com escopo `issues:write` (use a env var
  `GITHUB_TOKEN`, nunca inline).
- `tasks_file`: caminho para `TASKS.md` (padrão `specs/001-*/TASKS.md`).

### Configuração opcional

- `label_map`: mapeamento de pasta de persona para label (por exemplo,
  `01-product-owner` -> `role/po`).
- `milestone`: milestone a vincular.
- `dry_run`: pré-visualização sem criar (padrão `true`).

## Padrão de uso

```text
@copilot using github-issues plugin, sync TASKS.md to <target>.
```

O Copilot invoca o plugin, o plugin lê a fonte da verdade em markdown e aplica
as mudanças ao sistema de destino.

## Segurança

- Sempre leia credenciais de variáveis de ambiente. Nunca coloque um PAT inline
  em um prompt ou arquivo de configuração commitado no repo.
- Mantenha `dry_run` como `true` por padrão. Só defina como `false` depois de
  pré-visualizar a saída.
- Toda operação registra a trilha REQ-ID em que atuou, para que você possa
  correlacionar mudanças com o histórico da especificação.

## Antipadrões

- Usar o plugin como fonte da verdade. A fonte da verdade vive em markdown sob
  `specs/`; o plugin é um mecanismo de sincronização.
- Executar com `dry_run: false` antes de revisar a pré-visualização.
- Commitar PATs no repo.

## Gate de qualidade

Toda sincronização deve preservar a rastreabilidade por REQ-ID. Se um sistema de
destino não puder armazenar o REQ-ID (rastreador legado), o plugin se recusa a
executar.
