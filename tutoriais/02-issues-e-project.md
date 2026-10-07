# Tutorial 2 — Issues e GitHub Project

[← Voltar à central](../README.md)

| | |
|---|---|
| **Para que serve** | Registrar uma demanda de forma clara e acompanhar em que etapa ela está. |
| **Quem usa** | Todos. O Tech Lead cria e refina; DEV e QA atualizam e comentam. |
| **Ao final você saberá** | Escrever uma Issue completa, preencher os campos do Project e mover o Status corretamente. |

---

## O que é uma Issue (e por que ela importa)

A **Issue** é o registro oficial de uma tarefa: uma funcionalidade, um defeito, um teste ou um documento. É nela que ficam o objetivo, os responsáveis, o prazo e toda a conversa sobre a tarefa.

> 💡 Pense assim: **se não está na Issue, não aconteceu.** Mensagens no WhatsApp ou conversas no corredor não servem como evidência.

O **GitHub Project** é o quadro (tipo Kanban) que mostra todas as Issues da turma e em que etapa cada uma está.

## Quem cria cada tipo de Issue

| Tipo | Quem normalmente cria |
|---|---|
| Funcionalidade | Tech Lead, a partir de uma necessidade definida pelo professor |
| Defeito (bug) | Quem encontrou: QA, Tech Lead ou DEV |
| Teste | QA |
| Documentação | Responsável definido na demanda |

O professor pode criar ou alterar qualquer Issue para formalizar uma decisão acadêmica ou de produto.

---

## Passo 1: abrir o formulário correto

1. No repositório, clique em **Issues**.
2. Clique em **New issue**.
3. Escolha o **modelo** adequado (funcionalidade, bug, teste ou documentação).

> ⚠️ Não use Issue em branco. Os modelos garantem que nenhuma informação importante fique de fora.

## Passo 2: escrever um bom título

O título deve dizer **qual resultado** será entregue.

| ✅ Bom | ❌ Ruim |
|---|---|
| `[FEATURE] Exibir detalhes de um local acessível` | `Fazer página` |
| `[BUG] Mensagem de erro não aparece quando a API falha` | `Erro` |

## Passo 3: preencher o corpo da Issue

O modelo vai pedir:

- **Contexto** — por que essa tarefa existe.
- **Objetivo** — o que deve estar pronto no final.
- **Escopo** — o que faz parte da tarefa.
- **Fora do escopo** — o que **não** faz parte (evita trabalho a mais).
- **Critérios de aceite** — como saber se ficou pronto.
- **Dependências** — o que precisa existir antes.
- **Evidências esperadas** — prints, vídeos, links.

### Como escrever critérios de aceite

Um critério de aceite precisa ser **observável**: qualquer pessoa consegue verificar se foi atendido ou não.

```text
- [ ] Ao acessar /locais/42, o nome e o endereço do local são exibidos.
- [ ] Enquanto a API responde, uma mensagem de carregamento é apresentada.
- [ ] Se a API falhar, uma mensagem de erro é mostrada ao usuário.
- [ ] A página pode ser percorrida pelo teclado.
```

> ❌ Evite "funcionar corretamente" ou "ficar bonito". Ninguém consegue testar isso.

## Passo 4: completar os metadados

Na lateral direita da Issue, preencha:

| Campo | O que colocar |
|---|---|
| **Assignees** | Responsável principal |
| **Labels** | Tipo da demanda e situações especiais (ex.: `bloqueada`) |
| **Projects** | Project da turma |
| **Milestone** | CP1, CP2 ou CP3 |
| **Campos do Project** | Squad, Esforço, Prioridade, Data limite e QA responsável |

> ⚠️ A Issue só pode ir para `Pronta para iniciar` quando **todos** esses campos estiverem preenchidos.

## Passo 5: mover o Status no Project

O Status mostra em que etapa a tarefa está. Este é o mapa do ciclo de uma demanda:

| Status | Quando usar | Quem move |
|---|---|---|
| `Em refinamento` | A Issue ainda precisa de detalhes | Tech Lead |
| `Pronta para iniciar` | Todas as informações estão completas | Tech Lead |
| `Em desenvolvimento` | O DEV começou a trabalhar | DEV |
| `Em revisão técnica` | O Pull Request foi aberto | DEV |
| `Em testes do QA` | A revisão técnica foi aprovada | Tech Lead |
| `Correção solicitada` | Revisão ou QA pediram correções | Tech Lead ou QA |
| `Aprovada` | O QA aprovou | QA |
| `Concluída` | O merge foi feito | Tech Lead (ou automático) |
| `Bloqueada` | Existe um impedimento real | Quem está bloqueado |

```text
Em refinamento → Pronta para iniciar → Em desenvolvimento → Em revisão técnica
→ Em testes do QA → Aprovada → Concluída
         (Correção solicitada e Bloqueada podem acontecer no meio do caminho)
```

## Passo 6: comentar de forma útil

Comentários registram **fatos e decisões**. Um bom comentário responde: o que fiz, onde, o que falta e quando volto a atualizar.

```text
Iniciei a implementação em 20/08, na branch feature/42-detalhe-local.
Dependência: endpoint GET /locais/:id.
Próxima atualização prevista: 21/08.
```

> ❌ Evite comentários vagos como "estou fazendo", "deu erro" ou "não consegui".

## Passo 7: ligar o Pull Request à Issue

No corpo do Pull Request, escreva:

```text
Closes #42
```

Como `develop` é a branch padrão, a Issue será **fechada automaticamente** quando o Pull Request for integrado.

---

## E se der errado?

| Problema | O que fazer |
|---|---|
| Não encontro o modelo de Issue | Avise o Tech Lead; não crie em branco. |
| Não consigo editar campos do Project | Confirme se a Issue foi adicionada ao Project da turma (campo **Projects**). |
| A Issue não fechou após o merge | O Pull Request não tinha `Closes #NUMERO`. O Tech Lead fecha manualmente com justificativa. |

---

## Checklist da Issue pronta

- [ ] Objetivo claro.
- [ ] Escopo e fora do escopo definidos.
- [ ] Critérios de aceite testáveis.
- [ ] Responsável e QA definidos.
- [ ] Squad, esforço e prioridade definidos.
- [ ] Data limite e Milestone definidos.
- [ ] Dependências registradas.

---

[← Tutorial 1](01-primeiro-acesso.md) · [Próximo: Tutorial 3 — DEV →](03-dev-branch-commits-pr.md)
