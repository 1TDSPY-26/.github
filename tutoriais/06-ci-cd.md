# Tutorial 6 — CI, publicação e CD

[← Voltar à central](../README.md)

| | |
|---|---|
| **Para que serve** | Entender os resultados automáticos do GitHub e saber o que fazer quando algo falha. |
| **Quem usa** | Todos. DEV corrige o CI; Tech Lead e QA conferem antes de aprovar. |
| **Está dividido em** | [Parte A — CI](#parte-a-entender-o-ci) · [Parte B — Ambiente de teste](#parte-b-ambiente-de-teste) · [Parte C — Produção](#parte-c-publicação-em-produção) |

---

## Os termos, em linguagem simples

| Termo | O que é |
|---|---|
| **CI** — *Continuous Integration* (Integração Contínua) | Um robô do GitHub que, a cada push, instala o projeto, roda o lint, gera o build e executa os testes. |
| **CD** — *Continuous Deployment* (Implantação Contínua) | Publicação automática de uma versão depois de uma alteração autorizada. |
| **Deploy** | Colocar a aplicação no ar, acessível pela internet. |
| **Preview** | Uma publicação temporária para teste, quando estiver disponível. |

Nesta turma:

- o **CI é automático** em todo Pull Request;
- a **publicação é controlada pelo professor** enquanto o CD seguro não estiver habilitado;
- **não existe Preview automático garantido** para cada PR. Use apenas o ambiente informado oficialmente na Issue ou pelo professor.

🌐 **Produção:** [portal-locais-acessiveis-prod.up.railway.app](https://portal-locais-acessiveis-prod.up.railway.app/)

---

## Parte A: entender o CI

No Pull Request, o check `lint-build-test` pode aparecer em três cores:

| Cor | Significado | O que fazer |
|---|---|---|
| 🟡 Amarelo | Ainda está rodando. | Aguarde. Não peça aprovação final. |
| 🟢 Verde | Todas as etapas automáticas passaram. | Siga para a revisão. Verde **não substitui** revisão técnica nem teste do QA. |
| 🔴 Vermelho | Alguma etapa falhou. | O PR **não** está pronto. Encontre e corrija o erro (abaixo). |

### Passo a passo para encontrar o erro

1. Abra o Pull Request.
2. Desça até a área de **Checks** (verificações).
3. Clique em **Details** ao lado de `lint-build-test`.
4. Abra o job que falhou.
5. Expanda a **primeira** etapa vermelha.
6. Leia a mensagem de erro (normalmente nas últimas linhas).

✅ **Resultado esperado:** você sabe em qual etapa falhou e qual arquivo/linha causou o erro.

### Erros mais comuns

| Etapa | Causa provável | Como resolver |
|---|---|---|
| `npm ci` | `package-lock.json` ausente ou desatualizado | Rode `npm install`, confira as mudanças e faça commit do `package-lock.json`. |
| lint | Variável não usada, regra quebrada, importação errada | Rode `npm run lint` localmente e corrija. |
| build | Erro de TypeScript, importação ou configuração | Rode `npm run build` localmente e corrija. |
| test | Comportamento esperado não foi atendido | Rode os testes e corrija a implementação. |

### Como corrigir o CI

Na **mesma branch**, reproduza localmente:

```bash
npm ci
npm run lint
npm run build
npm run test --if-present
```

Corrija, e então:

```bash
git add ARQUIVOS_CORRIGIDOS
git commit -m "fix: corrige falha identificada no CI"
git push
```

O push dispara o CI de novo automaticamente. **Não abra outro Pull Request.**

> 💡 Use **Re-run jobs** apenas quando a falha foi externa ou temporária (ex.: instabilidade do GitHub). Rodar de novo não conserta código com erro.

---

## Parte B: ambiente de teste

Quando o professor disponibilizar uma URL de teste:

1. confirme qual branch ou commit foi publicado;
2. confira se a URL está registrada na Issue ou no Pull Request;
3. abra o ambiente;
4. teste a funcionalidade;
5. registre a versão e o horário do teste;
6. não aprove um código diferente daquele que o CI analisou.

> ⚠️ Se não houver ambiente publicado, o QA registra **Bloqueado por ausência de ambiente**, e **não** Reprovado.

---

## Parte C: publicação em produção

A branch `main` representa a versão autorizada para produção, publicada em [portal-locais-acessiveis-prod.up.railway.app](https://portal-locais-acessiveis-prod.up.railway.app/).

A publicação só acontece depois de:

1. CI verde;
2. regressão feita pelo QA;
3. decisão **GO** do QA;
4. aprovação do professor;
5. merge da Release em `main`.

> 💡 **GO** = autorização técnica para publicar. **NO-GO** = publicação bloqueada.

Enquanto o CD automático não estiver habilitado, o professor faz a publicação controlada a partir de `main`. Depois de publicada, a equipe abre a URL de produção e confirma que a versão nova está no ar ([Tutorial 8](08-release.md)).

---

## O que cada verificação prova (e o que não prova)

| Verificação | Prova que… | Não prova que… |
|---|---|---|
| lint | o código segue as regras estáticas | a tela funciona |
| build | TypeScript e empacotamento concluíram | os critérios foram atendidos |
| testes automáticos | os cenários programados passaram | todos os cenários possíveis funcionam |
| ambiente publicado | a aplicação pode ser acessada | ela tem qualidade funcional |
| revisão técnica | o código foi analisado | a experiência do usuário está completa |
| QA | os critérios foram executados | não existe nenhum defeito |

## Regras de segurança

> ⚠️ Variáveis que começam com `VITE_` são enviadas ao navegador e **qualquer pessoa pode vê-las**. Nunca coloque senha, token privado ou segredo nelas.

> ⚠️ Nunca envie ao GitHub: arquivos `.env`, a pasta `.vercel` ou tokens de publicação.

---

[← Tutorial 5](05-qa-testes.md) · [Próximo: Tutorial 7 — Correções, conflitos e bloqueios →](07-correcoes-conflitos-bloqueios.md)
