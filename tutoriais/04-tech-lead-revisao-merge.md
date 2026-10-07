# Tutorial 4 — Tech Lead: refinamento, revisão e merge

[← Voltar à central](../README.md)

| | |
|---|---|
| **Para que serve** | Transformar necessidades em tarefas executáveis, revisar o código e integrar somente o que foi aprovado. |
| **Quem usa** | Tech Lead. |
| **Está dividido em** | [Parte A — Refinar](#parte-a-refinar-uma-demanda) · [Parte B — Revisar](#parte-b-fazer-a-revisão-técnica) · [Parte C — Integrar (merge)](#parte-c-fazer-o-merge) |

---

## Onde o Tech Lead atua no fluxo

```text
Issue (A: refinar) → branch → commits → Pull Request → CI → (B: revisar) → QA → (C: merge)
```

> ⚠️ **Regra de ouro:** o Tech Lead **não aprova o próprio trabalho**. Se você for autor de uma demanda, outro Tech Lead ou revisor autorizado faz a revisão técnica, e o QA responsável faz a validação funcional.

---

## Parte A: refinar uma demanda

**Objetivo:** deixar a Issue tão clara que o DEV consiga trabalhar sem adivinhar nada.

### Passo 1: partir de uma necessidade aprovada

A demanda deve vir do professor, do backlog autorizado ou de um defeito validado.

### Passo 2: abrir o formulário certo

1. **Issues → New issue**.
2. Escolha funcionalidade, defeito ou documentação.
3. Preencha objetivo, escopo, fora do escopo, dependências e riscos.

### Passo 3: escrever critérios verificáveis

Cada critério deve ter uma resposta objetiva: **atendido** ou **não atendido**. Quando fizer sentido, cubra:

- resultado principal;
- carregamento;
- erro;
- lista vazia;
- teclado e foco;
- responsividade;
- integração com a API.

Veja exemplos no [Tutorial 2](02-issues-e-project.md#como-escrever-critérios-de-aceite).

### Passo 4: planejar

Defina: responsável, QA responsável, squad, **esforço (1, 2, 3 ou 5)**, prioridade, data limite, Milestone e dependências.

> 💡 Se a demanda passar de **5 pontos** de esforço, divida-a em Issues menores antes de começar.

### Passo 5: liberar

Mova de `Em refinamento` para `Pronta para iniciar` **somente** quando todos os campos estiverem completos e o conteúdo necessário já tiver sido apresentado em aula ou autorizado.

**✔ Checklist da Parte A:** objetivo · escopo/fora do escopo · critérios testáveis · responsável e QA · squad/esforço/prioridade · prazo e Milestone · dependências e riscos.

---

## Parte B: fazer a revisão técnica

**Objetivo:** garantir que o código está correto, seguro e dentro do escopo antes de ir para o QA.

### Passo 1: conferir a ligação com a Issue

No Pull Request, confira:

- [ ] base é `develop`;
- [ ] nome da branch tem o número da Issue;
- [ ] corpo tem `Closes #NUMERO`;
- [ ] escopo bate com a Issue;
- [ ] há instruções de teste;
- [ ] autoria e evidências estão presentes.

### Passo 2: conferir o CI

O check `lint-build-test` deve estar **verde** ✅. Se estiver vermelho ❌, devolva o PR ao autor **antes** de revisar o código.

### Passo 3: revisar os arquivos

1. Abra a aba **Files changed**.
2. Leia cada arquivo alterado e marque **Viewed** ao terminar.
3. Observe:
   - tipagem;
   - legibilidade;
   - separação de responsabilidades;
   - tratamento de erros;
   - segurança;
   - acessibilidade;
   - alterações fora do escopo;
   - credenciais ou dados pessoais indevidos.

### Passo 4: comentar no ponto exato

Clique no `+` ao lado da linha e escreva um comentário **específico**, que diga o problema e o que se espera:

```text
Este fetch precisa de tratamento para resposta não OK antes de converter o JSON.
Inclua o cenário de erro previsto no critério 3.
```

> ❌ Evite comentários vagos como "arrumar", "está errado" ou "melhorar código".

### Passo 5: concluir a revisão

Clique em **Review changes** e escolha:

| Opção | Quando usar |
|---|---|
| **Approve** | Tecnicamente pronto para o QA. |
| **Request changes** | Há correções obrigatórias. |
| **Comment** | Observação que não bloqueia. |

Depois de aprovar:

1. mova a Issue para `Em testes do QA`;
2. solicite o QA responsável;
3. **ainda não faça o merge**.

**✔ Checklist da Parte B:** PR ligado à Issue · CI verde · arquivos revisados · comentários específicos · revisão concluída · QA acionado.

---

## Parte C: fazer o merge

**Objetivo:** integrar à `develop` somente o que passou por todas as etapas.

O merge **só pode acontecer** quando:

- [ ] o CI está verde;
- [ ] todas as conversas estão resolvidas;
- [ ] o Tech Lead aprovou tecnicamente;
- [ ] o QA registrou resultado aprovado;
- [ ] o ambiente indicado pelo professor foi validado (quando existir);
- [ ] não existe bloqueio aberto.

### Passo 1: conferir a decisão do QA

Leia o relatório ou a Issue de teste. Não confie apenas no selo verde de aprovação.

### Passo 2: conferir commits recentes

Se o autor enviou commits **depois** das aprovações, peça nova revisão. Uma aprovação antiga não cobre código novo.

### Passo 3: integrar

1. Clique em **Merge pull request**.
2. Escolha **Create a merge commit**.
3. Confirme o merge.

> ⚠️ Não use **bypass** de proteção sem autorização do professor.

### Passo 4: verificar o fechamento

1. A Issue foi fechada?
2. O Status no Project está `Concluída`?
3. A branch remota foi removida?
4. Se `Closes #NUMERO` não fechou a Issue, relacione o PR e feche manualmente com uma justificativa.

---

## E se der errado?

| Problema | O que fazer |
|---|---|
| O botão de merge está bloqueado | Falta CI verde, aprovação ou resolver conversas. Confira a lista da Parte C. |
| O PR tem conflito com `develop` | Peça ao DEV para atualizar a branch ([Tutorial 7](07-correcoes-conflitos-bloqueios.md#parte-b-atualizar-a-branch-com-a-develop)). |
| O PR mistura várias demandas | Use **Request changes** e peça para separar em PRs diferentes. |

Para registrar o acompanhamento semanal, use o [modelo de relatório do Tech Lead](../modelos/modelo-relatorio-tech-lead.md).

---

[← Tutorial 3](03-dev-branch-commits-pr.md) · [Próximo: Tutorial 5 — QA →](05-qa-testes.md)
