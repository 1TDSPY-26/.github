# 📚 Central de dúvidas — 1TDSPY-26

Bem-vindo(a)! Aqui estão os tutoriais e as respostas para as dúvidas mais comuns sobre como trabalhamos no projeto **Portal Locais Acessíveis**: Issues, branches, Pull Requests, CI, testes e releases.

| | |
|---|---|
| 🌐 **Projeto no ar** | [portal-locais-acessiveis-prod.up.railway.app](https://portal-locais-acessiveis-prod.up.railway.app/) |
| 💻 **Repositório do projeto** | [1TDSPY-26/portal-locais-acessiveis](https://github.com/1TDSPY-26/portal-locais-acessiveis) |
| ❓ **Perguntas frequentes** | [duvidas-frequentes.md](duvidas-frequentes.md) |

---

## 🚀 Comece aqui

1. **Nunca acessou o projeto?** Faça o [Tutorial 1 — Primeiro acesso](tutoriais/01-primeiro-acesso.md).
2. **Descubra seu papel** na tabela abaixo e leia os tutoriais indicados.
3. **Tem uma dúvida específica?** Procure em [Encontre sua dúvida](#-encontre-sua-dúvida) ou nas [perguntas frequentes](duvidas-frequentes.md).

---

## 👤 Qual é o meu papel?

| Papel | O que faz | Leia, nesta ordem |
|---|---|---|
| **DEV** | Desenvolve as demandas. | [1](tutoriais/01-primeiro-acesso.md) → [2](tutoriais/02-issues-e-project.md) → [3](tutoriais/03-dev-branch-commits-pr.md) → [6](tutoriais/06-ci-cd.md) → [7](tutoriais/07-correcoes-conflitos-bloqueios.md) |
| **Tech Lead** | Refina as Issues, revisa o código, faz o merge e conduz a release. | [1](tutoriais/01-primeiro-acesso.md) → [2](tutoriais/02-issues-e-project.md) → [4](tutoriais/04-tech-lead-revisao-merge.md) → [6](tutoriais/06-ci-cd.md) → [7](tutoriais/07-correcoes-conflitos-bloqueios.md) → [8](tutoriais/08-release.md) |
| **QA** | Testa, registra defeitos e decide se a demanda está aprovada. | [1](tutoriais/01-primeiro-acesso.md) → [2](tutoriais/02-issues-e-project.md) → [5](tutoriais/05-qa-testes.md) → [6](tutoriais/06-ci-cd.md) → [8](tutoriais/08-release.md) |

Antes de cada etapa, confira o [Tutorial 9 — Checklists por papel](tutoriais/09-checklists-por-papel.md).

---

## 🔎 Encontre sua dúvida

### Eu quero…

| Eu quero… | Vá para |
|---|---|
| Instalar o Git Flow | [Tutorial 1 · Passo 2](tutoriais/01-primeiro-acesso.md#passo-2-conferir-as-ferramentas-instaladas) |
| Clonar o projeto | [Tutorial 1 · Passo 4](tutoriais/01-primeiro-acesso.md#passo-4-clonar-o-repositório) |
| Rodar o projeto no meu computador | [Tutorial 1 · Passo 8](tutoriais/01-primeiro-acesso.md#passo-8-executar-o-projeto) |
| Escrever uma Issue boa | [Tutorial 2 · Passo 3](tutoriais/02-issues-e-project.md#passo-3-preencher-o-corpo-da-issue) |
| Saber qual Status usar no Project | [Tutorial 2 · Passo 5](tutoriais/02-issues-e-project.md#passo-5-mover-o-status-no-project) |
| Criar a branch da minha tarefa | [Tutorial 3 · Passo 2](tutoriais/03-dev-branch-commits-pr.md#passo-2-criar-a-branch-da-issue) |
| Escrever uma mensagem de commit | [Tutorial 3 · Passo 5](tutoriais/03-dev-branch-commits-pr.md#passo-5-fazer-commits) |
| Abrir um Pull Request | [Tutorial 3 · Passo 9](tutoriais/03-dev-branch-commits-pr.md#passo-9-abrir-o-pull-request) |
| Revisar um Pull Request | [Tutorial 4 · Parte B](tutoriais/04-tech-lead-revisao-merge.md#parte-b-fazer-a-revisão-técnica) |
| Fazer o merge | [Tutorial 4 · Parte C](tutoriais/04-tech-lead-revisao-merge.md#parte-c-fazer-o-merge) |
| Registrar um defeito (bug) | [Tutorial 5 · Passo 5](tutoriais/05-qa-testes.md#passo-5-registrar-um-defeito) |
| Decidir se aprovo ou reprovo (QA) | [Tutorial 5 · Passo 6](tutoriais/05-qa-testes.md#passo-6-tomar-a-decisão) |
| Preparar a release do CP | [Tutorial 8](tutoriais/08-release.md) |

### Aconteceu…

| Aconteceu… | Vá para |
|---|---|
| `git flow` não é reconhecido | [Tutorial 1 · E se der errado?](tutoriais/01-primeiro-acesso.md#e-se-der-errado) |
| O CI ficou vermelho ❌ | [Tutorial 6 · Encontrar o erro](tutoriais/06-ci-cd.md#passo-a-passo-para-encontrar-o-erro) |
| Pediram correção no meu PR | [Tutorial 7 · Parte A](tutoriais/07-correcoes-conflitos-bloqueios.md#parte-a-corrigir-depois-de-uma-revisão) |
| Deu conflito no merge | [Tutorial 7 · Parte C](tutoriais/07-correcoes-conflitos-bloqueios.md#parte-c-resolver-um-conflito) |
| Comecei um merge errado | [Tutorial 7 · Parte D](tutoriais/07-correcoes-conflitos-bloqueios.md#parte-d-cancelar-um-merge-ainda-não-concluído) |
| Estou bloqueado(a) | [Tutorial 7 · Parte E](tutoriais/07-correcoes-conflitos-bloqueios.md#parte-e-registrar-um-bloqueio) |
| Não há ambiente para testar (QA) | [Tutorial 6 · Parte B](tutoriais/06-ci-cd.md#parte-b-ambiente-de-teste) |

---

## 🔁 O fluxo de uma demanda

Toda demanda deixa este rastro de evidências:

```text
Issue → branch → commits → Pull Request → CI → revisão técnica → teste do QA → merge
```

| Etapa | Quem age | Status no Project |
|---|---|---|
| Issue refinada | Tech Lead | `Em refinamento` → `Pronta para iniciar` |
| Branch e commits | DEV | `Em desenvolvimento` |
| Pull Request + CI | DEV | `Em revisão técnica` |
| Revisão técnica | Tech Lead | `Em testes do QA` (ou `Correção solicitada`) |
| Teste do QA | QA | `Aprovada` (ou `Correção solicitada` / `Bloqueada`) |
| Merge | Tech Lead | `Concluída` |

> **Por que isso importa?** Sem Issue, a responsabilidade não está definida. Sem Pull Request, a revisão e o teste não ficam registrados. Sem CI verde, a alteração não está pronta para ser integrada.

---

## 📖 Todos os tutoriais

1. [Primeiro acesso, clone e execução](tutoriais/01-primeiro-acesso.md)
2. [Issues e GitHub Project](tutoriais/02-issues-e-project.md)
3. [DEV: branch, commits, push e Pull Request](tutoriais/03-dev-branch-commits-pr.md)
4. [Tech Lead: refinamento, revisão e merge](tutoriais/04-tech-lead-revisao-merge.md)
5. [QA: plano, execução, defeitos e decisão](tutoriais/05-qa-testes.md)
6. [CI e CD: entender os resultados automáticos](tutoriais/06-ci-cd.md)
7. [Correções, conflitos e bloqueios](tutoriais/07-correcoes-conflitos-bloqueios.md)
8. [Release do CP](tutoriais/08-release.md)
9. [Checklists rápidos por papel](tutoriais/09-checklists-por-papel.md)

## 📝 Modelos

- [Registro de bloqueio](modelos/modelo-bloqueio.md) — para registrar um impedimento na Issue.
- [Relatório semanal do Tech Lead](modelos/modelo-relatorio-tech-lead.md) — acompanhamento das squads.
- [Relatório do QA](modelos/modelo-relatorio-qa.md) — resultado dos testes de uma demanda e decisão do QA.
- [Relatório de Release](modelos/modelo-release.md) — versão do CP, decisão GO/NO-GO e publicação.

---

## 📘 Glossário

| Termo | Em linguagem simples |
|---|---|
| **Issue** | Registro oficial de uma tarefa: funcionalidade, defeito, teste ou documento. |
| **GitHub Project** | Quadro que mostra todas as Issues e em que etapa cada uma está. |
| **Branch** | Uma "cópia de trabalho" separada, para mexer no código sem afetar o dos outros. |
| **Commit** | Uma "foto" de uma alteração no código, com mensagem e autor. |
| **Push** | Enviar seus commits do computador para o GitHub. |
| **Pull Request (PR)** | Pedido para revisar e integrar sua branch na `develop`. |
| **Review** | Revisão registrada dentro do Pull Request. |
| **Merge** | Juntar uma branch aprovada em outra. |
| **Conflito** | Quando duas pessoas mudaram as mesmas linhas e o Git pede para você escolher. |
| **Git Flow** | Extensão do Git que padroniza os nomes das branches (`feature/`, `release/`, `hotfix/`). |
| **`develop`** | Branch onde o trabalho da turma é integrado. |
| **`main`** | Branch com a versão oficial publicada. |
| **CI** | Verificação automática (lint, build e testes) a cada push. |
| **CD** | Publicação automática depois de uma alteração autorizada. Por enquanto, a publicação é controlada pelo professor. |
| **Lint** | Ferramenta que verifica regras de estilo e erros comuns no código. |
| **Build** | Gerar a versão final da aplicação, pronta para publicar. |
| **Preview** | Versão temporária da aplicação, quando um ambiente de teste for disponibilizado. |
| **QA** | *Quality Assurance* — quem garante a qualidade testando os critérios de aceite. |
| **Critério de aceite** | Condição observável que diz se a tarefa está pronta. |
| **Regressão** | Testar de novo o que já funcionava para garantir que nada quebrou. |
| **Release** | Versão oficial do projeto entregue em um CP. |
| **GO / NO-GO** | Decisão do QA de publicar (GO) ou não publicar (NO-GO) uma release. |

---

## 🆘 Não achei minha resposta

1. Procure nas [perguntas frequentes](duvidas-frequentes.md).
2. Registre a dúvida **na própria Issue** e mencione o Tech Lead (`@usuario-do-tech-lead`), explicando o que tentou.
3. Se for um impedimento real, registre um [bloqueio](tutoriais/07-correcoes-conflitos-bloqueios.md#parte-e-registrar-um-bloqueio).

> ⏰ Não espere o prazo terminar para comunicar um problema.
