# Tutorial 8 — Release do CP

[← Voltar à central](../README.md)

| | |
|---|---|
| **Para que serve** | Transformar o que foi aprovado na `develop` em uma versão estável publicada na `main`. |
| **Quem usa** | Tech Lead (conduz), QA (regressão e GO/NO-GO), DEV (correções autorizadas), professor (autoriza). |
| **Quando** | No fim de cada CP (CP1, CP2, CP3), na data definida pelo professor. |

**Release** é a versão oficial, liberada e identificada do projeto. A versão em produção fica em:
🌐 [portal-locais-acessiveis-prod.up.railway.app](https://portal-locais-acessiveis-prod.up.railway.app/)

---

## Linha do tempo

```text
1. Congelamento  →  2. Branch release/cpN  →  3. Regressão do QA  →  4. Tratar defeitos
→  5. GO / NO-GO  →  6. PR release → main  →  7. Aprovar e publicar  →  8. GitHub Release
→  9. Sincronizar develop
```

## Quem faz o quê

| Papel | Responsabilidade |
|---|---|
| Professor | Autoriza a publicação final. |
| Tech Lead | Prepara a branch e o Pull Request da release. |
| QA | Executa a regressão e emite a decisão GO/NO-GO. |
| DEV | Corrige **apenas** defeitos autorizados durante o congelamento. |

> 💡 **GO/NO-GO** é a decisão de publicar (**GO**) ou não publicar (**NO-GO**) a versão.

---

## Passo 1: iniciar o congelamento (feature freeze)

A partir da data definida:

1. **nenhuma funcionalidade nova** entra;
2. confirme que as Issues previstas estão aprovadas ou formalmente replanejadas;
3. registre as demandas que saíram da release;
4. confira bloqueios e defeitos abertos.

## Passo 2: criar a branch de release

O Tech Lead executa:

```bash
git switch develop
git pull origin develop
git flow release start cp1
git flow release publish cp1
```

Troque `cp1` por `cp2` ou `cp3` conforme o ciclo.

✅ **Resultado esperado:** a branch `release/cp1` aparece no GitHub.

> ⚠️ Não execute `git flow release finish`. A integração é feita pelo Pull Request protegido.

## Passo 3: executar a regressão

**Regressão** é testar de novo o sistema inteiro para garantir que nada que funcionava quebrou. O QA testa na branch ou no ambiente de release indicado pelo professor:

- [ ] rotas principais;
- [ ] funcionalidades do CP;
- [ ] integrações;
- [ ] estados de erro, vazio e carregamento;
- [ ] teclado e foco;
- [ ] responsividade;
- [ ] build;
- [ ] riscos corrigidos desde a última aprovação.

## Passo 4: tratar defeitos

| Severidade | Efeito durante o congelamento |
|---|---|
| 🔴 Crítica | Bloqueia a release. |
| 🟠 Alta | Bloqueia a demanda relacionada. |
| 🟡 Média | Exige decisão registrada. |
| 🟢 Baixa | Pode ser replanejada. |

Toda correção precisa de **Issue, branch, Pull Request, CI e reteste**.

> ⚠️ Não corrija direto na branch de release sem autorização e rastreabilidade.

## Passo 5: emitir GO / NO-GO

O QA registra:

- versão testada;
- cenários executados;
- defeitos abertos;
- riscos aceitos;
- decisão **GO**, **GO com ressalvas** (pode publicar com pendências registradas) ou **NO-GO**;
- evidências.

📝 Use o [modelo de relatório de Release](../modelos/modelo-release.md) — a seção **Decisão do QA** já traz as três opções.

## Passo 6: abrir o Pull Request para a main

O Tech Lead abre o PR:

```text
base: main
compare: release/cp1
```

O corpo do PR deve conter:

- Milestone do CP;
- resumo da versão;
- Issues entregues e Issues replanejadas;
- resultado da regressão e decisão do QA;
- link ou identificação do ambiente testado;
- riscos conhecidos;
- pedido de autorização ao professor.

## Passo 7: aprovar e publicar

1. Aguarde o CI verde.
2. O QA aprova a release.
3. O professor autoriza e aprova.
4. O Tech Lead faz o merge em `main`.
5. O professor executa (ou libera) a publicação controlada da `main`.
6. A equipe abre a [URL de produção](https://portal-locais-acessiveis-prod.up.railway.app/) e confirma que a nova versão está no ar.

## Passo 8: criar a GitHub Release

1. No repositório, abra **Releases**.
2. Clique em **Draft a new release**.
3. Crie a tag, por exemplo: `cp1-2026-2`.
4. Selecione `main` como alvo.
5. Use um título como `CP1 — Fundação e MVP de leitura`.
6. Preencha a descrição usando o [modelo de relatório de Release](../modelos/modelo-release.md), incluindo a seção **Publicação** e a de **Retorno à versão anterior**.
7. Publique.

## Passo 9: sincronizar a develop

Depois da publicação, leve a versão final de volta para a `develop` com outro Pull Request:

```text
base: develop
compare: main
```

Depois do CI e das aprovações, faça o merge. Isso evita que a `develop` fique diferente do que foi publicado.

Por fim, o Tech Lead limpa a branch local:

```bash
git switch develop
git pull origin develop
git branch -d release/cp1
git fetch --prune
```

---

## Checklist final

- [ ] Feature freeze cumprido.
- [ ] Regressão registrada.
- [ ] QA emitiu GO.
- [ ] CI verde.
- [ ] Professor autorizou.
- [ ] Merge em `main` concluído.
- [ ] Produção validada em [portal-locais-acessiveis-prod.up.railway.app](https://portal-locais-acessiveis-prod.up.railway.app/).
- [ ] GitHub Release publicada.
- [ ] `develop` sincronizada.

---

[← Tutorial 7](07-correcoes-conflitos-bloqueios.md) · [Próximo: Tutorial 9 — Checklists →](09-checklists-por-papel.md)
