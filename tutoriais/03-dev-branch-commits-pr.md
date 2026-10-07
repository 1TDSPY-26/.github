# Tutorial 3 — DEV: branch, commits, push e Pull Request

[← Voltar à central](../README.md)

| | |
|---|---|
| **Para que serve** | Executar uma demanda do início ao fim sem mexer diretamente em `develop` ou `main`. |
| **Quem usa** | DEV (e qualquer pessoa que vá alterar código). |
| **Pré-requisito** | [Tutorial 1](01-primeiro-acesso.md) concluído e uma Issue em `Pronta para iniciar` atribuída a você. |

---

## Visão geral

O trabalho do DEV tem quatro fases:

```text
1. COMEÇAR          2. DESENVOLVER         3. ENVIAR                  4. DEPOIS DO MERGE
atualizar develop → commits pequenos   → publicar a branch       → limpar a branch local
criar a branch      testar localmente     abrir o Pull Request
avisar na Issue     atualizar com develop acompanhar CI e revisões
```

> ⚠️ **Antes de tudo:** não comece só porque recebeu uma mensagem. Abra a Issue e confirme que ela está em `Pronta para iniciar` e que você é o responsável.

---

## Fase 1 — Começar

### Passo 1: atualizar a develop

```bash
git switch develop
git pull origin develop
```

✅ **Resultado esperado:** `Already up to date.` ou a lista de arquivos baixados, sem erros.

> ⚠️ Se o `pull` der erro, **não crie a branch**. Resolva primeiro ou peça ajuda na Issue.

### Passo 2: criar a branch da Issue

Use o Git Flow com o **número da Issue** + uma descrição curta:

```bash
git flow feature start 42-detalhe-local
```

O Git Flow cria a branch `feature/42-detalhe-local` a partir da `develop` e já muda para ela.

✅ **Resultado esperado:** `git branch --show-current` mostra `feature/42-detalhe-local`.

Regras para o nome:

- letras minúsculas e hífens;
- número real da Issue no começo;
- descrição curta (2 a 4 palavras).

| ✅ Bom | ❌ Ruim |
|---|---|
| `42-detalhe-local` | `minha-branch` |
| `57-corrige-mensagem-erro` | `Teste_Final2` |

> 💡 Use `feature` para funcionalidade, correção comum, documentação, teste ou refatoração. `hotfix` é reservado para correção **urgente** do que já está em produção.

### Passo 3: registrar o início na Issue

1. Mova o Status para `Em desenvolvimento`.
2. Comente o nome da branch.
3. Registre dependências relevantes.

---

## Fase 2 — Desenvolver

### Passo 4: trabalhar somente no escopo

Deixe os critérios de aceite abertos enquanto programa. **Não misture outra funcionalidade** na mesma branch.

De tempos em tempos, confira o que mudou:

```bash
git status   # quais arquivos foram alterados
git diff     # o que mudou dentro deles (ainda sem commit)
```

### Passo 5: fazer commits

Um **commit** é uma "foto" de uma alteração, com uma mensagem explicando o que foi feito. Adicione **apenas os arquivos relacionados**:

```bash
git add src/pages/DetalheLocal.tsx
git add src/services/locais-service.ts
git commit -m "feat: exibe detalhes do local acessível"
```

Use o prefixo que descreve o tipo da mudança:

| Prefixo | Quando usar | Exemplo |
|---|---|---|
| `feat:` | nova funcionalidade | `feat: exibe detalhes do local acessível` |
| `fix:` | correção | `fix: trata falha ao carregar detalhes do local` |
| `docs:` | documentação | `docs: documenta endpoint de consulta por id` |
| `test:` | testes | `test: adiciona cenário de local inexistente` |
| `refactor:` | reorganização sem mudar comportamento | `refactor: separa consulta de local no service` |

> ❌ Não faça commits vazios, artificiais ou com mensagens como `alteração`, `teste` ou `final`.

### Passo 6: testar localmente

```bash
npm run lint
npm run build
npm run test --if-present
```

✅ **Resultado esperado:** os três comandos terminam sem erros.

Depois, rode a aplicação (`npm run dev`) e confira:

- [ ] caminho principal (o que a Issue pede);
- [ ] pelo menos um cenário de erro;
- [ ] estado de carregamento;
- [ ] navegação por teclado, foco e rótulos;
- [ ] tela em tamanhos diferentes (responsividade);
- [ ] todos os critérios de aceite.

### Passo 7: atualizar a branch com a develop

Enquanto você trabalhava, outras pessoas podem ter integrado código na `develop`. Traga essas mudanças para a sua branch:

```bash
git fetch origin
git merge origin/develop
```

✅ **Resultado esperado:** `Already up to date.` ou um merge concluído sem conflitos.

Se aparecer **conflito**, siga o [Tutorial 7](07-correcoes-conflitos-bloqueios.md#parte-c-resolver-um-conflito). Depois da atualização, rode lint e build de novo.

> ⚠️ Nunca use `git push --force`.

---

## Fase 3 — Enviar

### Passo 8: publicar a branch

No **primeiro** envio:

```bash
git flow feature publish 42-detalhe-local
```

Nos envios seguintes da mesma branch, basta:

```bash
git push
```

✅ **Resultado esperado:** a branch `feature/42-detalhe-local` aparece no GitHub.

### Passo 9: abrir o Pull Request

O **Pull Request (PR)** é o pedido para que seu código seja revisado e integrado à `develop`.

1. No GitHub, clique em **Compare & pull request** (ou **Pull requests → New pull request**).
2. Confira as branches:
   - **base:** `develop`
   - **compare:** a sua branch
3. Escreva um título claro.
4. No corpo, mantenha a linha que liga o PR à Issue:

   ```text
   Closes #42
   ```

5. Preencha todo o template: o que foi feito, **como testar**, evidências (imagens ou links) e autoria/colaboração.
6. Clique em **Create pull request**.

### Passo 10: acompanhar o CI e pedir revisão

1. Aguarde o CI (verificação automática). Veja o [Tutorial 6](06-ci-cd.md).
2. Confirme que `lint-build-test` ficou **verde** ✅.
3. Se o professor disponibilizou um ambiente de teste, faça um teste rápido nele.
4. Mova a Issue para `Em revisão técnica`.
5. Solicite o Tech Lead como revisor (**Reviewers**).

### Passo 11: responder às revisões

Se o Tech Lead ou o QA pedirem correções:

1. **não** crie outro Pull Request;
2. continue na **mesma branch**;
3. faça as alterações e crie novos commits;
4. rode lint e build;
5. envie com `git push` (o PR é atualizado sozinho);
6. responda aos comentários;
7. solicite nova revisão.

Mais detalhes no [Tutorial 7](07-correcoes-conflitos-bloqueios.md#parte-a-corrigir-depois-de-uma-revisão).

---

## Fase 4 — Depois do merge

### Passo 12: limpar a branch local

**Somente depois que o merge for feito no GitHub:**

```bash
git switch develop
git pull origin develop
git branch -d feature/42-detalhe-local
git fetch --prune
```

> ⚠️ **Não use `git flow feature finish`.** Esse comando faz o merge no seu computador, pulando o CI, a revisão e o QA. Neste projeto, o merge acontece **somente pelo Pull Request**, depois de todas as aprovações.

---

## Erros que invalidam o fluxo

- Desenvolver sem Issue em `Pronta para iniciar`.
- Criar a branch a partir de código desatualizado.
- Fazer push direto em `develop` ou `main`.
- Misturar várias demandas na mesma branch.
- Esconder erro de lint ou build.
- Abrir o Pull Request para a branch errada.
- Executar `git flow feature finish` e integrar localmente.
- Aprovar ou integrar o próprio trabalho.
- Apagar evidências para "limpar" o histórico.

## E se der errado?

| Problema | O que fazer |
|---|---|
| Fiz commits na `develop` por engano | Não faça push. Peça ajuda ao Tech Lead na Issue antes de qualquer outro comando. |
| `git flow feature start` diz que a branch já existe | Ela já foi criada antes. Use `git switch feature/NUMERO-descricao`. |
| O PR aponta para `main` | Edite o PR e troque a **base** para `develop`. |
| O CI ficou vermelho | Veja o [Tutorial 6](06-ci-cd.md#passo-a-passo-para-encontrar-o-erro). |

---

[← Tutorial 2](02-issues-e-project.md) · [Próximo: Tutorial 4 — Tech Lead →](04-tech-lead-revisao-merge.md)
