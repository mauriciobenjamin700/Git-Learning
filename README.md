# Guia Sobre Git: Do Básico ao Avançado Feito Pela IA Gemini

Este tutorial irá guiá-lo através dos fundamentos do Git, desde a configuração inicial até recursos avançados, capacitando você a controlar totalmente seus projetos de desenvolvimento de software.

Conteúdo:

- Parte 1: Fundamentos do Git.
  - Introdução ao Git.
  - Configuração Inicial.
  - Criação de Repositórios.
  - Fluxo de Trabalho Básico.
  - Comandos Essenciais:
    - git init,
    - git clone,
    - git add,
    - git commit,
    - git status,
    - git log,
    - git diff.
  
- Parte 2: Trabalhando com Branches
  - O Poder das Branches
  - Comandos de Branch:
    - git branch
    - git checkout
    - git merge

- Parte 3: Colaboração com o Git
  - Repositórios Remotos
  - Comandos Remotos:
    - git remote
    - git fetch
    - git pull
    - git push

- Parte 4: Recursos Avançados do Git
- Stashing: `git stash`
- Revertendo Mudanças: `git revert`
- Redefinindo o Histórico: `git reset`
- Cherry-picking: `git cherry-pick`
- Rebase: `git rebase`
- Submódulos: `git submodule`

## Parte 1: Fundamentos do Git

### Introdução

Git é um sistema de controle de versão distribuído que permite rastrear alterações em arquivos ao longo do tempo e colaborar com outras pessoas em projetos. Em essência, o Git cria instantâneos de seu projeto, chamados commits, permitindo que você reverta para versões anteriores, compare alterações e trabalhe em recursos simultaneamente.

### Configuração Inicial

Após instalar o Git, você precisa configurar sua identidade

```bash
git config --global user.name "Seu Nome"
git config --global user.email "seu_email@example.com"
```

Esses detalhes serão associados a cada commit que você fizer.

### Criação de Repositórios

1. Inicializando um repositório em um diretório existente:

    ```bash
        cd /caminho/para/seu/projeto
        git init
    ```

    Isso cria um diretório `.git` oculto dentro do projeto, transformando-o em um repositório Git.

2. Clonando um repositório remoto:

    ```bash
    git clone <url_do_repositorio>
    ```

    Isso copia o repositório remoto para o seu computador.

    Exemplo: `git clone https://github.com/usuario/repositorio.git`

### Fluxo de Trabalho Básico

O ciclo de vida básico de um arquivo no Git:

1. Untracked: Arquivo novo, ainda não monitorado pelo Git.
2. Staged: Arquivo modificado adicionado à área de staging, pronto para ser incluído no próximo commit.
3. Committed: Arquivo salvo no histórico do Git como parte de um commit.

### Comandos Essenciais do Git

#### git init

**Descrição:** Inicializa um novo repositório Git no diretório atual.

**Parâmetros:** Nenhum parâmetro específico.

**Exemplo:**

```bash
git init
```

#### git clone

**Descrição:** Cria uma cópia local de um repositório Git existente.

**Parâmetros:**

- `<url_do_repositorio>`: A URL do repositório que você deseja clonar.

**Exemplos:**

```bash
git clone https://github.com/usuario/repositorio.git
git clone git@github.com:usuario/repositorio.git
```

#### git add

**Descrição:** Adiciona arquivos modificados à área de staging, preparando-os para o próximo commit.

**Parâmetros:**

- `<arquivo>`: Adiciona um único arquivo.
- `.`: Adiciona todos os arquivos modificados no diretório atual.
- `-A`: Adiciona todos os arquivos modificados no projeto.

**Exemplos:**

```bash
git add index.html
git add .
git add -A
```

#### git commit

**Descrição:** Cria um novo commit, salvando as alterações na área de staging no histórico do repositório.

**Parâmetros:**

- `-m "<mensagem_de_commit>"`: Especifica uma mensagem descritiva para o commit.

**Exemplos:**

```bash
git commit -m "Adicionado arquivo index.html"
git commit -m "Correções de bugs"
```

#### git status

**Descrição:** Exibe o estado atual do repositório Git, incluindo arquivos modificados, área de staging e branches ativas.

**Parâmetros:** Nenhum parâmetro específico.

**Exemplo:**

```bash
git status
```

#### git log

**Descrição:** Mostra o histórico de commits do repositório Git.

**Parâmetros:**

- `-n <número>`: Limita o número de commits exibidos.
- `--oneline`: Mostra os commits em uma única linha.
- `--author="<autor>"`: Filtra commits por autor.

**Exemplos:**

```bash
git log
git log -n 5
git log --oneline
git log --author="Seu Nome"
```

#### git diff

**Descrição:** Mostra as diferenças entre commits, arquivos ou a área de staging.

**Parâmetros:**

- `<commit1> <commit2>`: Compara dois commits específicos.
- `<arquivo>`: Compara um arquivo com sua versão no último commit.

**Exemplos:**

```bash
git diff HEAD~1 HEAD
git diff style.css
```

## Parte 2: Trabalhando com Branches

### O Poder das Branches

Branches são como linhas de desenvolvimento paralelas, permitindo que você trabalhe em recursos, correções de bugs ou experimentos sem afetar a linha principal do desenvolvimento (branch `main` ou `master`).

### Comandos de Branch

#### git branch

- **Descrição:** Lista as branches existentes no repositório.
- **Parâmetros:**
  - `<nome_da_branch>`: Cria uma nova branch.
  - `-d <nome_da_branch>`: Exclui uma branch.
  - `git fetch --prune` :Exclui do history branch removidas

- **Exemplos:**

    ```bash
    git branch
    git branch nova-feature
    git branch -d feature-antiga
    ```

#### git checkout

- **Descrição:** Alterna para uma branch diferente.
- **Parâmetros:**
  - `<nome_da_branch>`: Alterna para a branch especificada.
  - `-b <nome_da_branch>`: Cria uma nova branch e alterna para ela.
- **Exemplos:**

    ```bash
    git checkout main
    git checkout nova-feature
    git checkout -b correcao-de-bug
    ```

#### git merge

- **Descrição:** Mescla uma branch na branch atual.
- **Parâmetros:**
  - `<nome_da_branch>`: Nome da branch que você deseja mesclar.
-**Exemplo:**

    ```bash
    git checkout main
    git merge nova-feature
    ```

## Parte 3: Colaboração com o Git

### Repositórios Remotos

Repositórios remotos são cópias do seu repositório armazenadas em um servidor, como GitHub, GitLab ou Bitbucket. Eles permitem a colaboração com outras pessoas e atuam como backup do seu código.

### Comandos Remotos

#### git remote

- **Descrição:** Gerencia repositórios remotos.
- **Parâmetros:**
  - `add <nome> <url>`: Adiciona um novo repositório remoto.
  - `-v`: Lista os repositórios remotos configurados.
  - `remove <nome>`: Remove um repositório remoto.

- **Exemplos:**

    ```bash
    git remote add origin https://github.com/usuario/repositorio.git
    git remote -v
    git remote remove origin
    ```

#### git fetch

- **Descrição:** Baixa alterações de um repositório remoto sem mesclá-las na sua branch atual.
- **Parâmetros:**
  - `<nome_do_remoto>`: Nome do repositório remoto (por exemplo, `origin`).
- **Exemplo:**

    ```bash
    git fetch origin
    ```

#### git pull

- **Descrição:** Baixa alterações de um repositório remoto e mescla-as na sua branch atual.
- **Parâmetros:**
  - `<nome_do_remoto> <nome_da_branch>`: Especifica o repositório remoto e a branch.
- **Exemplo:**

    ```bash
    git pull origin main
    ```

#### git push

- **Descrição:** Envia seus commits locais para um repositório remoto.
- **Parâmetros:**
  - `<nome_do_remoto> <nome_da_branch>`: Especifica o repositório remoto e a branch.
  - `-u`: Define o repositório remoto como upstream, simplificando futuros pushes.
- **Exemplos:**

    ```bash
    git push origin main
    git push -u origin main
    ```

## Parte 4: Recursos Avançados do Git

Nesta parte, exploraremos funcionalidades mais complexas do Git que te auxiliarão a gerenciar seus projetos com maestria e flexibilidade.

### 1. Stashing: Git Stash

O `git stash` é um recurso prático para salvar temporariamente suas alterações sem precisar realizar um commit. Isso é útil quando você deseja trocar de branch ou manter seu diretório de trabalho limpo.

**Comandos Básicos:**

- `git stash save <mensagem>`: Salva o stash atual com uma mensagem descritiva.
- `git stash list`: Lista todos os stashes salvos.
- `git stash pop`: Aplica o último stash salvo e o remove da lista.
- `git stash apply <id>`: Aplica um stash específico pelo seu identificador.
- `git stash drop <id>`: Remove um stash específico pelo seu identificador.

**Exemplo:**

```bash
git stash save "Mudanças no layout"
git stash list
git stash pop
git stash apply 2
git stash drop 1
```

### 2. Revertendo Mudanças: Git Revert

O `git revert` cria um novo commit que reverte as alterações introduzidas por um commit anterior. Isso é útil para desfazer erros ou mudanças indesejadas.

**Comando:**

- `git revert <commit_hash>`: Reverte o commit especificado pelo hash.

**Exemplo:**

```bash
git revert 1a2b3c4d
```
Logo em seguida, use este comando para descartas as mudanças feitas

```bash
git push --force
```

### 3. Redefinindo o Histórico: Git Reset

O `git reset` redefine o estado atual da branch para um commit específico, com diferentes modos para lidar com as alterações.

**Modos:**

- `soft`: Move o ponteiro da branch, mas mantém as alterações na área de staging.
- `mixed`: Move o ponteiro da branch e descarta as alterações da área de staging.
- `hard`: Move o ponteiro da branch e descarta todas as alterações, incluindo commits não enviados.

**Comando:**

- `git reset <modo> <commit_hash>`: Redefine o estado para o commit especificado, usando o modo desejado.

**Exemplo:**

```bash
git reset --soft HEAD~1  # Move o ponteiro para o commit anterior, mantendo as alterações na área de staging.
git reset HEAD~2        # Move o ponteiro 2 commits para trás, descartando as alterações da área de staging.
git reset --hard 1a2b3c4d # Move o ponteiro para o commit especificado, descartando todas as alterações (USE COM CAUTELA!).
```

**Atenção:** Redefinir o histórico com `--hard` pode resultar em perda de dados. Utilize com cautela!

### 4. Cherry-picking: Git Cherry-pick

O `git cherry-pick` aplica um commit específico de uma branch em outra. Isso é útil para transferir commits seletivamente entre branches.

**Comando:**

- `git cherry-pick <commit_hash>`: Aplica o commit especificado pelo hash na branch atual.

**Exemplo:**

```bash
git cherry-pick a1b2c3d4
```

### 5. Rebase: Git Rebase

O `git rebase` reaplica commits de uma branch em cima de outra, criando um histórico linear. Isso é útil para manter um histórico de commits mais limpo e organizado.

**Comando:**

- `git rebase <nova_base>`: Reaplica os commits da branch atual em cima da branch ou commit especificado como `nova_base`.

**Exemplo:**

```bash
git rebase main
```

**Atenção:** O rebase altera o histórico do repositório. Evite rebasing em branches que já foram compartilhadas com outros desenvolvedores.

### 6. Submódulos: Git Submodule

O `git submodule` permite incluir outros repositórios Git como subdiretórios dentro do seu projeto principal. Isso é útil para organizar projetos modulares ou reutilizar código de outros repositórios.

**Comandos Básicos:**

- `git submodule add <url> <caminho>`: Adiciona um novo submódulo ao projeto.
- `git submodule update`: Atualiza os submódulos para suas versões mais recentes.

**Exemplo:**

```bash
git submodule add https://github.com/usuario/submodulo.git lib/submodulo
git submodule update
```
## Visão geral do GitFlow (o mapa mental)

* **main**: estado em produção. Cada commit em `main` deveria corresponder a uma versão lançada (tag).
* **develop**: integração do “próximo release”. É onde as features se juntam.
* **Branches de apoio**:

  * **feature/**\*: desenvolvimentos isolados que partem de `develop` e voltam para `develop`.
  * **release/**\*: estabilização do próximo release (freeze). Parte de `develop`, volta para `main` (com tag) e para `develop`.
  * **hotfix/**\*: correção crítica em produção. Parte de `main`, volta para `main` (com tag) e para `develop`.
  * (Opcional) **support/**\* ou **maintenance/**\*: manter versões antigas em paralelo.

Diagrama (simplificado):

```
main     ──●───────M─────────●─────────M───>
             \               /           \
develop  ──●──●──M──●──●───M───────────────M─>
            \     \          \
feature/x    ●──●──M          \
feature/y       ●──●──M        \
release/1.4                ●───M───(tag v1.4.0)
hotfix/1.4.1                          ●─M─(tag v1.4.1)
```

* `M` = merge.
* Tags (ex.: `v1.4.0`) marcam versões produzidas.

---

## Fluxos passo a passo

### 1) Preparação do repositório

```bash
git init
git checkout -b main
git commit --allow-empty -m "chore: initial commit"
git checkout -b develop   # develop nasce a partir de main
git push -u origin main
git push -u origin develop
```

### 2) Nova feature

* Origem: `develop` → **feature/**.
* Retorno: **merge para `develop`** via PR.

```bash
git checkout develop
git pull
git checkout -b feature/login
# ... commits ...
git push -u origin feature/login
# Abra PR: feature/login -> develop (CI, code review)
# Merge aprovado e delete a branch
```

### 3) Preparar um release

* Origem: `develop` → **release/**.
* Objetivo: congelar features, só pequenos ajustes/bugs e *version bump*.
* Retorno: merge para `main` **com tag** + merge de volta em `develop`.

```bash
git checkout develop
git pull
git checkout -b release/1.4.0
# bump de versão, changelog, últimos fixes
git push -u origin release/1.4.0
# PR: release/1.4.0 -> main (deploy/release)
# Depois marque a tag:
git checkout main
git merge --no-ff release/1.4.0 -m "release: 1.4.0"
git tag -a v1.4.0 -m "Release 1.4.0"
git push origin main --tags
# Traga de volta para develop:
git checkout develop
git merge --no-ff release/1.4.0 -m "chore: merge back release 1.4.0"
git push
```

### 4) Hotfix em produção

* Origem: `main` → **hotfix/**.
* Retorno: merge para `main` **com tag** + merge de volta em `develop`.

```bash
git checkout main
git pull
git checkout -b hotfix/1.4.1
# corrigir bug crítico
git push -u origin hotfix/1.4.1
# PR: hotfix/1.4.1 -> main
git checkout main
git merge --no-ff hotfix/1.4.1 -m "hotfix: 1.4.1"
git tag -a v1.4.1 -m "Hotfix 1.4.1"
git push origin main --tags
# merge back
git checkout develop
git merge --no-ff hotfix/1.4.1 -m "chore: merge back hotfix 1.4.1"
git push
```

---

## Convenções úteis

**Nomes de branches**

* `feature/<escopo>-<assunto>` → `feature/auth-login`, `feature/catalogo-filtro`
* `release/<MAJOR.MINOR.PATCH>` → `release/2.3.0`
* `hotfix/<MAJOR.MINOR.PATCH>` → `hotfix/2.3.1`

**Versionamento**

* Use **SemVer**: `MAJOR.MINOR.PATCH`

  * `MAJOR`: mudanças incompatíveis.
  * `MINOR`: novas funcionalidades compatíveis.
  * `PATCH`: correções.

**Merges**

* Gitflow clássico usa `--no-ff` para preservar a história de branches.
* Em PRs, muitas equipes preferem **squash** para histórico mais limpo (decida e padronize).

**Commits**

* Mensagens claras; muitas equipes usam **Conventional Commits** (`feat:`, `fix:`, `chore:`…).
* Evite rebase em branches já publicados, a não ser que toda a equipe concorde (risco de reescrever histórico).

---

## Integração com CI/CD (recomendado)

* **feature/**: build + testes (nenhum deploy).
* **develop**: integração contínua do próximo release (ambiente de **homologação**/staging).
* **release/**: testes de regressão, scan de segurança, geração de artefatos candidatos.
* **main**: pipeline de **produção** (deploy, tag, geração de release notes).
* **hotfix/**: caminho rápido para produção, com gates mínimos necessários.

**Proteções**

* Branch protection para `main` e `develop` (reviews obrigatórios, status checks verdes).
* Regras de quem pode criar/mergear `release/` e `hotfix/`.

---

## Quando Gitflow é uma boa

* Times médios/grandes com **janelas de release** claras.
* Produtos com **publicações menos frequentes** (ex.: mensal, trimestral).
* Ambientes regulados/legados, **múltiplas versões em suporte**.

## Quando pode atrapalhar

* Equipes que fazem **deploy contínuo** (muito frequente).
* Projetos que preferem **trunk-based** ou **GitHub Flow** (apenas `main`, feature branches curtas, deploy direto).
* Se `develop` vira uma “fila de espera” longa (risco de “merge hell”).

**Alternativas rápidas**

* **GitHub Flow**: `main` + feature branches + PR + deploy contínuo.
* **GitLab Flow**: aproxima branches de ambientes (ex.: `production`, `preprod`) — útil com múltiplos ambientes.

---

## Anti-padrões comuns (e como evitar)

* **Esquecer o merge de volta do hotfix para `develop`** → divergência de código.
  *Checklist de release/hotfix* obrigatório.
* **Release branch recebendo novas features** → quebre o freeze; crie outra `release/` quando pronto.
* **Features muito longas** → mantenha pequenas e integre cedo (feature toggles ajudam).
* **CI fraco** → sem testes, Gitflow vira burocracia; invista nos pipelines.

---

## Cheatsheet rápido

```bash
# criar develop (uma vez)
git checkout -b develop && git push -u origin develop

# feature
git checkout develop
git checkout -b feature/<nome>
# ... commits ...
git push -u origin feature/<nome>
# PR -> develop

# release
git checkout develop
git checkout -b release/<x.y.z>
# bump versão, fix, teste
# PR -> main
git tag -a v<x.y.z> -m "Release <x.y.z>"
# merge back -> develop

# hotfix
git checkout main
git checkout -b hotfix/<x.y.z>
# fix crítico
# PR -> main
git tag -a v<x.y.z> -m "Hotfix <x.y.z>"
# merge back -> develop
```

---

## Dicas para adoção suave

* Escreva um **README de fluxo** no repositório (com exemplos de branch names, política de merge e de tags).
* Crie **templates de PR** e **checklists de release/hotfix**.
* Configure **proteções de branch** e **ambientes de deploy** (staging/production).
* Faça um **workshop curto** com o time e simule: 1 feature, 1 release, 1 hotfix.

## Conclusão

Este tutorial cobriu os principais conceitos e comandos do Git, fornecendo uma base sólida para gerenciar seus projetos de desenvolvimento de software. Explore a documentação oficial do Git e outros recursos online para aprofundar seus conhecimentos e dominar o poder do controle de versão.
