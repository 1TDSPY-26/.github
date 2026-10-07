# ❓ Perguntas frequentes

[← Voltar à central](README.md)

Respostas curtas para as dúvidas mais comuns. Cada resposta tem um link para o tutorial completo.

**Ir para:** [Ambiente](#-ambiente-e-instalação) · [Git e branches](#-git-e-branches) · [Pull Request e CI](#-pull-request-e-ci) · [Revisão e QA](#-revisão-e-qa) · [Bloqueios e prazos](#-bloqueios-e-prazos) · [Release](#-release)

---

## 🛠️ Ambiente e instalação

**O comando `git flow` não é reconhecido. O que faço?**
O Git Flow não está instalado. No Windows: `winget install GitTower.GitFlowNext`; no macOS: `brew install git-flow-avh`; no Linux: `sudo apt install git-flow`. Feche e reabra o terminal.
📖 [Tutorial 1 · Passo 2](tutoriais/01-primeiro-acesso.md#passo-2-conferir-as-ferramentas-instaladas)

**Abri o repositório e deu erro 404.**
Você ainda não aceitou o convite da organização **1TDSPY-26** ou está logado com outra conta.
📖 [Tutorial 1 · Passo 1](tutoriais/01-primeiro-acesso.md#passo-1-aceitar-o-convite-da-organização)

**Preciso rodar `git flow init` toda vez?**
Não. Apenas **uma vez em cada clone** do repositório, com a `develop` selecionada.
📖 [Tutorial 1 · Passo 6](tutoriais/01-primeiro-acesso.md#passo-6-inicializar-o-git-flow)

**Qual a diferença entre `npm ci` e `npm install`?**
`npm ci` instala exatamente as versões do `package-lock.json` — é o que usamos para todos terem o mesmo ambiente. `npm install` só é usado quando o lock precisa ser atualizado.
📖 [Tutorial 1 · Passo 7](tutoriais/01-primeiro-acesso.md#passo-7-instalar-as-dependências)

**O projeto já veio com erro antes de eu mexer. Começo assim mesmo?**
Não. Registre o problema na Issue e avise o Tech Lead.
📖 [Tutorial 1 · Passo 9](tutoriais/01-primeiro-acesso.md#passo-9-validar-lint-e-build)

**Onde vejo o projeto publicado?**
Em [portal-locais-acessiveis-prod.up.railway.app](https://portal-locais-acessiveis-prod.up.railway.app/). Essa é a versão da `main` (produção).

---

## 🌿 Git e branches

**Em qual branch eu começo?**
Sempre a partir da `develop` atualizada (`git switch develop` + `git pull origin develop`).
📖 [Tutorial 3 · Passo 1](tutoriais/03-dev-branch-commits-pr.md#passo-1-atualizar-a-develop)

**Como devo nomear minha branch?**
Número da Issue + descrição curta, em minúsculas e com hífens: `git flow feature start 42-detalhe-local`.
📖 [Tutorial 3 · Passo 2](tutoriais/03-dev-branch-commits-pr.md#passo-2-criar-a-branch-da-issue)

**Uso `feature` ou `hotfix` para corrigir um bug?**
`feature` para correções comuns. `hotfix` só para correção **urgente** do que já está em produção.

**Posso fazer push direto na `develop` ou na `main`?**
Não. Todo código entra por Pull Request.

**Posso usar `git flow feature finish`?**
Não. Ele faz o merge no seu computador e pula CI, revisão e QA. O merge é feito **somente pelo Pull Request**.
📖 [Tutorial 3 · Passo 12](tutoriais/03-dev-branch-commits-pr.md#passo-12-limpar-a-branch-local)

**Como escrevo a mensagem de commit?**
Use um prefixo + o que foi feito: `feat: exibe detalhes do local acessível`, `fix: trata falha ao carregar detalhes`.
📖 [Tutorial 3 · Passo 5](tutoriais/03-dev-branch-commits-pr.md#passo-5-fazer-commits)

**Deu conflito. E agora?**
Abra os arquivos indicados no `git status`, escolha ou combine as versões, apague os marcadores `<<<<<<<`, `=======`, `>>>>>>>` e finalize com commit e push. Se não entender as versões, peça ajuda ao Tech Lead.
📖 [Tutorial 7 · Parte C](tutoriais/07-correcoes-conflitos-bloqueios.md#parte-c-resolver-um-conflito)

**Posso usar `git push --force` ou `git reset --hard`?**
Não. Eles apagam trabalho e histórico. Se começou um merge errado e ainda não fez commit, use `git merge --abort`.
📖 [Tutorial 7 · Parte D](tutoriais/07-correcoes-conflitos-bloqueios.md#parte-d-cancelar-um-merge-ainda-não-concluído)

---

## 🔀 Pull Request e CI

**Para qual branch eu abro o Pull Request?**
Base `develop`, compare a sua branch. Só PRs de release vão para a `main`.
📖 [Tutorial 3 · Passo 9](tutoriais/03-dev-branch-commits-pr.md#passo-9-abrir-o-pull-request)

**Para que serve o `Closes #42`?**
Liga o PR à Issue e a fecha automaticamente quando o merge na `develop` for feito.
📖 [Tutorial 2 · Passo 7](tutoriais/02-issues-e-project.md#passo-7-ligar-o-pull-request-à-issue)

**O CI ficou vermelho. O que faço?**
Clique em **Details** no check `lint-build-test`, abra a primeira etapa vermelha e leia o erro. Reproduza localmente com `npm run lint` / `npm run build`, corrija e faça push na mesma branch.
📖 [Tutorial 6 · Parte A](tutoriais/06-ci-cd.md#passo-a-passo-para-encontrar-o-erro)

**CI verde significa que está tudo certo?**
Não. Significa que as verificações automáticas passaram. Ainda faltam a revisão técnica e o teste do QA.

**Pediram correção. Abro outro PR?**
Não. Continue na mesma branch, faça novos commits e `git push` — o PR é atualizado sozinho.
📖 [Tutorial 7 · Parte A](tutoriais/07-correcoes-conflitos-bloqueios.md#parte-a-corrigir-depois-de-uma-revisão)

**Posso colocar uma chave de API em uma variável `VITE_`?**
Não. Tudo que começa com `VITE_` vai para o navegador e qualquer pessoa vê. Nunca envie `.env` ao GitHub.
📖 [Tutorial 6 · Regras de segurança](tutoriais/06-ci-cd.md#regras-de-segurança)

---

## ✅ Revisão e QA

**Posso aprovar meu próprio Pull Request?**
Não. Nem DEV, nem Tech Lead, nem QA aprovam o próprio trabalho.

**O autor enviou commits depois da aprovação. Vale a aprovação antiga?**
Não. Código novo precisa de nova revisão e novo teste.

**Não há ambiente de teste. Reprovo a demanda?**
Não. Registre **Bloqueado por ausência de ambiente**.
📖 [Tutorial 5 · Passo 6](tutoriais/05-qa-testes.md#passo-6-tomar-a-decisão)

**Qual a diferença entre Aprovado, Aprovado com ressalva, Reprovado e Bloqueado?**
Veja a tabela de decisões do QA e registre a sua no relatório.
📖 [Tutorial 5 · Passo 6](tutoriais/05-qa-testes.md#passo-6-tomar-a-decisão) · 📝 [Modelo de relatório do QA](modelos/modelo-relatorio-qa.md)

**Como classifico a severidade de um defeito?**
Crítica (bloqueia release), Alta (bloqueia demanda), Média (correção planejada), Baixa (não bloqueia sozinha).
📖 [Tutorial 5 · Passo 5](tutoriais/05-qa-testes.md#passo-5-registrar-um-defeito)

**Reprovar uma demanda me prejudica?**
Não. Uma reprovação com evidência mostra que o QA cumpriu seu papel.

---

## ⏸️ Bloqueios e prazos

**O que conta como bloqueio?**
Um impedimento real que você não resolve só continuando a tarefa (ex.: API fora do ar). Não ter começado ou não ter lido a Issue **não** é bloqueio.
📖 [Tutorial 7 · Parte E](tutoriais/07-correcoes-conflitos-bloqueios.md#parte-e-registrar-um-bloqueio)

**Como registro um bloqueio?**
Comente na Issue **antes do prazo** com: o que bloqueia, data, tentativas, dependência, impacto, quem pode ajudar e próxima revisão. Aplique a label `bloqueada` e mova para `Bloqueada`.
📝 [Modelo de bloqueio](modelos/modelo-bloqueio.md)

**Um bloqueio aceito garante nota?**
Não. Ele gera replanejamento (novo prazo, divisão da tarefa etc.).

**Onde tiro dúvidas que não estão aqui?**
Na própria Issue, mencionando o Tech Lead e explicando o que você já tentou.

---

## 🏷️ Release

**O que é o congelamento (feature freeze)?**
Período antes da release em que nenhuma funcionalidade nova entra; só correções autorizadas.
📖 [Tutorial 8 · Passo 1](tutoriais/08-release.md#passo-1-iniciar-o-congelamento-feature-freeze)

**O que é GO / NO-GO?**
A decisão do QA de publicar (GO), publicar com pendências registradas (GO com ressalvas) ou não publicar (NO-GO) a versão.
📖 [Tutorial 8 · Passo 5](tutoriais/08-release.md#passo-5-emitir-go--no-go) · 📝 [Modelo de relatório de Release](modelos/modelo-release.md)

**Quem publica a versão em produção?**
O professor, a partir da `main`, depois do GO do QA e do merge da release.
📖 [Tutorial 8 · Passo 7](tutoriais/08-release.md#passo-7-aprovar-e-publicar)

---

[← Voltar à central](README.md)
