## Como iniciar sua Issue com Git Flow

Este guia mostra o passo a passo para preparar o ambiente local e criar a branch da sua tarefa usando o Git Flow, antes de começar a desenvolver.

### Pré-requisitos

- [Git](https://git-scm.com/install/windows) instalado (para o Mac - [Git Mac](https://git-scm.com/install/mac)).
- Git Bash (ou outro terminal de sua preferência) instalado.
- Acesso ao repositório da organização no GitHub.

### Clonar o repositório

Abra o Git Bash em uma pasta local onde você guarda seus projetos e execute:

```bash
git clone https://github.com/1TDSPY-26/portal-locais-acessiveis.git
```

> 💡 Exemplo: se você guarda seus projetos em `Documents/GitHub`, o repositório ficará em `~/Documents/GitHub/portal-locais-acessiveis`. O caminho é apenas um exemplo — use a pasta que preferir.

Depois de clonar, entre na pasta do projeto:

```bash
cd portal-locais-acessiveis
```

### Verificar se você já possui o Git Flow

```bash
git flow version
```

- **Se o comando retornar uma versão** → o Git Flow já está instalado. Siga para o [passo 3](#3-conferir-a-branch-atual).
- **Se o comando não for reconhecido** → o Git Flow ainda não está instalado. Siga o passo abaixo e depois volte para o passo 3.

<details>
<summary>Não tenho o Git Flow instalado — como instalar</summary>

No Windows, instale pelo `winget`:

```bash
winget install GitTower.GitFlowNext
```

Em outros sistemas, você também pode instalar com o gerenciador de pacotes correspondente:

```bash
# macOS (Homebrew)
brew install git-flow-avh

# Linux (Debian/Ubuntu)
sudo apt install git-flow
```

Depois de instalar, confirme novamente:

```bash
git flow version
```

Com o retorno de uma versão, continue no passo 3.

</details>

### Conferir a branch atual

```bash
git branch -a
```

Se você **não** estiver na `main`, mude para ela:

```bash
git switch main
```

Confirme novamente que está na branch correta:

```bash
git branch -a
```

### Inicializar o Git Flow

Com a `main` selecionada, execute:

```bash
git flow init
```

Confirme todas as perguntas com as respostas padrão (pressione `Enter` em cada uma), sem alterar nada.

### Voltar para a branch `develop`

```bash
git switch develop
```

Valide que está na branch correta:

```bash
git branch -a
```

### Criar a branch da sua tarefa

Com o Git Flow inicializado e já na `develop`, crie a branch da sua Issue:

```bash
git flow feature start nome-da-branch
```

Publique a branch para que ela fique disponível no GitHub:

```bash
git flow feature publish nome-da-branch
```

### Abrir o projeto no editor

```bash
code .
```
> 🍎 No macOS, se o comando `code` não for reconhecido, abra o VS Code, pressione `Cmd + Shift + P`, digite **Shell Command: Install 'code' command in PATH** e selecione essa opção. Isso só precisa ser feito uma vez.

Pronto! Agora você pode trabalhar na sua branch e realizar as mudanças necessárias de acordo com as informações da sua Issue.
