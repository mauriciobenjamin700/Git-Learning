# Guia Completo de Git: Do Básico ao Avançado

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

## Conclusão

Este tutorial cobriu os principais conceitos e comandos do Git, fornecendo uma base sólida para gerenciar seus projetos de desenvolvimento de software. Explore a documentação oficial do Git e outros recursos online para aprofundar seus conhecimentos e dominar o poder do controle de versão.
