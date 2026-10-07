# Tutorial 7 — Correções, conflitos e bloqueios

[← Voltar à central](../README.md)

| | |
|---|---|
| **Para que serve** | Saber o que fazer quando pedem correção, quando o Git mostra conflito ou quando você está impedido de continuar. |
| **Quem usa** | Principalmente DEV, mas bloqueios valem para todos. |
| **Está dividido em** | [A — Correção após revisão](#parte-a-corrigir-depois-de-uma-revisão) · [B — Atualizar a branch](#parte-b-atualizar-a-branch-com-a-develop) · [C — Conflito](#parte-c-resolver-um-conflito) · [D — Cancelar merge](#parte-d-cancelar-um-merge-ainda-não-concluído) · [E — Bloqueio](#parte-e-registrar-um-bloqueio) |

---

## Parte A: corrigir depois de uma revisão

Quando o Tech Lead ou o QA usam **Request changes**:

1. leia **todos** os comentários;
2. se não entendeu algo, responda perguntando antes de alterar;
3. continue na **mesma branch** (não crie outro PR);
4. altere somente o necessário;
5. rode lint, build e testes;
6. crie um commit de correção e faça push;
7. responda ao comentário indicando o commit;
8. solicite nova revisão.

```bash
git add src/pages/DetalheLocal.tsx
git commit -m "fix: trata local inexistente na página de detalhes"
git push
```

✅ **Resultado esperado:** o novo commit aparece no Pull Request e o CI roda de novo.

> ⚠️ Não marque uma conversa como **Resolved** sem aplicar a correção ou registrar a decisão combinada.

---

## Parte B: atualizar a branch com a develop

Faça isso antes de abrir o Pull Request ou quando o Tech Lead pedir:

```bash
git switch feature/42-detalhe-local
git fetch origin
git merge origin/develop
```

✅ **Resultado esperado:** `Already up to date.` ou um merge concluído. Se não houve conflito, teste e faça `git push`.

Se aparecer `CONFLICT`, vá para a Parte C.

---

## Parte C: resolver um conflito

### O que é um conflito?

Acontece quando você e outra pessoa alteraram **as mesmas linhas** do mesmo arquivo. O Git não sabe qual versão manter e pede para você decidir.

### Passo a passo

1. Veja quais arquivos estão em conflito:

   ```bash
   git status
   ```

   Eles aparecem como `both modified`.

2. Abra cada arquivo. O Git marca o trecho em conflito assim:

   ```text
   <<<<<<< HEAD
   seu conteúdo
   =======
   conteúdo vindo de develop
   >>>>>>> origin/develop
   ```

   - Entre `<<<<<<< HEAD` e `=======`: **a sua versão**.
   - Entre `=======` e `>>>>>>> origin/develop`: **a versão da develop**.

3. Escolha uma versão ou **combine** as duas.
4. **Apague todos os marcadores** (`<<<<<<<`, `=======`, `>>>>>>>`).
5. Salve o arquivo.

### Exemplo: antes e depois

**Antes** (com conflito):

```tsx
<<<<<<< HEAD
<h1>Detalhes do local</h1>
=======
<h1 className="titulo">Detalhes</h1>
>>>>>>> origin/develop
```

**Depois** (combinando as duas — texto novo + classe da develop):

```tsx
<h1 className="titulo">Detalhes do local</h1>
```

### Finalizar

6. Rode lint e build.
7. Adicione os arquivos resolvidos, finalize o merge e envie:

```bash
git add ARQUIVOS_RESOLVIDOS
git commit -m "chore: resolve conflito com develop"
git push
```

✅ **Resultado esperado:** `git status` mostra *"nothing to commit, working tree clean"*.

> 💡 No VS Code, os botões **Accept Current**, **Accept Incoming** e **Accept Both** ajudam a resolver.

> ⚠️ Se você não entende as duas versões, **não escolha aleatoriamente**. Mencione o Tech Lead na Issue.

---

## Parte D: cancelar um merge ainda não concluído

Começou a atualização errada e **ainda não fez o commit**? Volte ao estado anterior:

```bash
git merge --abort
```

Depois, peça orientação.

> ⚠️ Não use `git reset --hard` nem `git push --force` para "consertar". Esses comandos apagam trabalho e histórico.

---

## Parte E: registrar um bloqueio

### O que é um bloqueio?

É um **impedimento real**, que não se resolve apenas continuando a tarefa. Exemplo: a API que você precisa está fora do ar.

### Como registrar (antes do prazo!)

Comente na Issue seguindo este formato:

```text
Bloqueio: endpoint GET /locais/:id retorna erro 500.
Data e hora: 25/08/2026 às 20h15.
Tentativas: conferi URL, parâmetro e chamada no Postman.
Dependência: correção ou orientação da equipe de API.
Impacto: não consigo validar o estado de sucesso da página de detalhes.
Ajuda solicitada: @tech-lead e professor.
Próxima revisão: 26/08 às 18h.
```

Para casos mais complexos, use o [modelo completo de bloqueio](../modelos/modelo-bloqueio.md).

Depois:

1. aplique a label `bloqueada`;
2. mude o Status para `Bloqueada`;
3. preencha Saúde como `Em risco`;
4. registre o motivo no Project;
5. mencione quem pode ajudar.

### O que NÃO é bloqueio

- não ter começado a tarefa;
- não ter lido a Issue;
- avisar só depois do prazo;
- dificuldade comum que ainda não foi investigada;
- depender de algo que já estava disponível;
- falta de organização sem comunicação prévia.

> 💡 Um bloqueio aceito gera **replanejamento** (novo prazo, divisão da tarefa etc.). Ele **não** garante nota integral automaticamente.

---

[← Tutorial 6](06-ci-cd.md) · [Próximo: Tutorial 8 — Release →](08-release.md)
