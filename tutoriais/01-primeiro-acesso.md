# Tutorial 1 — Primeiro acesso, clone e execução

[← Voltar à central](../README.md)

| | |
|---|---|
| **Para que serve** | Deixar o projeto da turma funcionando no seu computador. |
| **Quem usa** | Todos (DEV, Tech Lead e QA). Faça uma única vez por computador. |
| **Tempo estimado** | 20 a 40 minutos. |
| **Ao final você terá** | O repositório clonado, a branch `develop` selecionada, o Git Flow configurado e a aplicação abrindo no navegador. |

---

## O que você precisa antes de começar

- Conta no GitHub com e-mail verificado.
- Convite da organização **1TDSPY-26** aceito (Passo 1).
- [Git](https://git-scm.com/install/windows) instalado ([versão para Mac](https://git-scm.com/install/mac)).
- Um terminal: Git Bash (Windows), Terminal (macOS/Linux) ou o terminal do VS Code.
- Extensão **Git Flow** instalada (o Passo 2 mostra como).
- Node.js na versão indicada pelo professor.
- Visual Studio Code.

---

## Passo 1: aceitar o convite da organização

1. Entre no GitHub.
2. Abra suas notificações ou o e-mail do convite.
3. Clique em **Join** ou **Accept invitation**.

✅ **Resultado esperado:** ao abrir `https://github.com/1TDSPY-26`, você vê o repositório `portal-locais-acessiveis`.

> ⚠️ **Erro 404 ao abrir o repositório?** O convite ainda não foi aceito ou você entrou com outra conta do GitHub.

## Passo 2: conferir as ferramentas instaladas

No terminal, execute um comando por vez:

```bash
git --version
git flow version
node --version
npm --version
```

✅ **Resultado esperado:** cada comando mostra um número de versão (ex.: `git version 2.45.0`).

Se algum comando responder *"command not found"* ou *"não é reconhecido"*, instale a ferramenta antes de continuar.

<details>
<summary><strong>Não tenho o Git Flow — como instalar</strong></summary>

**Windows** (PowerShell ou Git Bash):

```bash
winget install GitTower.GitFlowNext
```

**macOS** (Homebrew):

```bash
brew install git-flow-avh
```

**Linux** (Debian/Ubuntu):

```bash
sudo apt install git-flow
```

Feche e abra o terminal novamente e confirme:

```bash
git flow version
```

</details>

## Passo 3: configurar sua autoria no Git

O Git grava seu nome e e-mail em cada commit. Isso é a **prova individual** do que você fez.

```bash
git config --global user.name "Seu Nome Completo"
git config --global user.email "seu-email@exemplo.com"
```

Use o **mesmo e-mail da sua conta do GitHub**. Para conferir:

```bash
git config --global user.name
git config --global user.email
```

✅ **Resultado esperado:** aparecem o seu nome e o seu e-mail.

> ⚠️ Nunca use o nome ou o e-mail de outro integrante. Commits com autoria errada não contam como seus.

## Passo 4: clonar o repositório

"Clonar" é baixar uma cópia do repositório para o seu computador.

1. Abra o repositório no GitHub e clique no botão verde **Code**.
2. Selecione **HTTPS** e copie a URL.
3. No terminal, entre na pasta onde você guarda seus projetos e execute:

```bash
git clone https://github.com/1TDSPY-26/portal-locais-acessiveis.git
cd portal-locais-acessiveis
```

> 💡 Se você guarda projetos em `Documents/GitHub`, o projeto ficará em `~/Documents/GitHub/portal-locais-acessiveis`. A pasta é só um exemplo — use a que preferir.

✅ **Resultado esperado:** o terminal agora está dentro da pasta `portal-locais-acessiveis`.

## Passo 5: confirmar que você está na develop

```bash
git branch --show-current
```

✅ **Resultado esperado:**

```text
develop
```

Se aparecer outra branch (por exemplo, `main`), troque para a `develop` e atualize:

```bash
git switch develop
git pull origin develop
```

> 💡 **Por que `develop`?** É a branch onde o trabalho da turma é integrado. A `main` guarda apenas versões oficiais (releases).

## Passo 6: inicializar o Git Flow

O Git Flow precisa ser configurado **uma vez em cada clone**. Ainda na `develop`, execute:

```bash
git flow init
```

O comando fará algumas perguntas:

1. Branch de produção → confirme `main`.
2. Branch de desenvolvimento → confirme `develop`.
3. Prefixos (`feature/`, `release/`, `hotfix/`…) → apenas pressione `Enter` em cada um.

✅ **Resultado esperado:** o comando termina sem erros e você continua na `develop`.

## Passo 7: instalar as dependências

```bash
npm ci
```

`npm ci` instala **exatamente** as versões registradas no `package-lock.json`, assim todos da turma têm o mesmo ambiente.

✅ **Resultado esperado:** aparece uma pasta `node_modules` e nenhuma mensagem de `ERR!`.

## Passo 8: executar o projeto

```bash
npm run dev
```

Abra no navegador o endereço mostrado pelo Vite, normalmente:

```text
http://localhost:5173
```

✅ **Resultado esperado:** a página do Portal Locais Acessíveis abre no navegador.

## Passo 9: validar lint e build

Pare o servidor com `Ctrl + C` e execute:

```bash
npm run lint
npm run build
```

✅ **Resultado esperado:** os dois comandos terminam sem erros.

> ⚠️ Se o projeto já vier com erro **antes** de você mexer em qualquer coisa, não comece a demanda. Registre o problema na Issue e avise o Tech Lead.

## Passo 10: abrir o projeto no editor

```bash
code .
```

> 🍎 **macOS:** se `code` não for reconhecido, abra o VS Code, pressione `Cmd + Shift + P`, digite **Shell Command: Install 'code' command in PATH** e selecione a opção. Só é preciso fazer isso uma vez.

---

## E se der errado?

| Problema | O que fazer |
|---|---|
| `git flow` não é reconhecido | Instale pelo bloco "Não tenho o Git Flow" no [Passo 2](#passo-2-conferir-as-ferramentas-instaladas) e reabra o terminal. |
| Erro 404 ou *"Repository not found"* no clone | Confirme se aceitou o convite e se está logado na conta certa. |
| O clone pede usuário e senha | Use o login pelo navegador (Git Credential Manager). Nunca coloque sua senha em arquivos do projeto. |
| `npm ci` falha | Confira a versão do Node.js com o professor e rode de novo. Se persistir, registre na Issue. |
| `npm run dev` diz que a porta está em uso | Feche outro terminal com o projeto rodando ou use o endereço que o Vite sugerir. |

---

## Checklist

- [ ] Convite aceito.
- [ ] Repositório `1TDSPY-26/portal-locais-acessiveis` clonado.
- [ ] Autoria do Git configurada com meu nome e e-mail.
- [ ] Branch atual é `develop`.
- [ ] Git Flow inicializado neste clone.
- [ ] `npm ci` concluído.
- [ ] Aplicação abriu no navegador.
- [ ] Lint e build executados sem erros.

---

[Próximo: Tutorial 2 — Issues e GitHub Project →](02-issues-e-project.md)
