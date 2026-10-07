# Tutorial 5 — QA: plano, execução, defeitos e decisão

[← Voltar à central](../README.md)

| | |
|---|---|
| **Para que serve** | Verificar os critérios de aceite com evidências e impedir que uma demanda com defeito avance sem registro. |
| **Quem usa** | QA (*Quality Assurance*, ou Garantia da Qualidade). |
| **Quando entra** | Depois que o Tech Lead aprova a revisão técnica e a Issue vai para `Em testes do QA`. |

---

## Regra de independência

O QA **não testa a própria implementação** e **não faz merge**. O papel do QA é: planejar → executar → registrar → decidir, sempre com base nos critérios de aceite.

```text
Preparar → Criar Issue de teste → Executar → Registrar evidências → (Registrar defeitos) → Decidir → (Retestar)
```

---

## Passo 1: preparar o teste

Antes de começar, confira se tem tudo de que precisa:

- [ ] Issue refinada, com critérios de aceite;
- [ ] Pull Request relacionado;
- [ ] revisão técnica concluída;
- [ ] CI verde;
- [ ] ambiente de teste indicado pelo professor disponível;
- [ ] dados de teste necessários.

> ⚠️ Se faltar alguma dessas condições, a decisão é **Bloqueado**, não **Reprovado**. Falta de ambiente não é defeito do código.

## Passo 2: criar a Issue de teste

1. **Issues → New issue** → modelo de **teste**.
2. Relacione a Issue da funcionalidade e o Pull Request.
3. Descreva ambiente, dados e cenários.
4. Defina o **resultado esperado** de cada cenário.

## Passo 3: executar os testes

Abra o ambiente indicado pelo professor e teste:

1. caminho principal;
2. entrada inválida;
3. resposta vazia;
4. falha da API (quando possível);
5. carregamento;
6. navegação por teclado;
7. foco visível;
8. rótulos e mensagens;
9. tamanhos de tela previstos;
10. critérios específicos da Issue.

> ⚠️ Não aprove olhando apenas uma captura de tela. **Use a funcionalidade de verdade.**

## Passo 4: registrar as evidências

Para cada cenário, registre:

| Campo | Exemplo |
|---|---|
| Ação realizada | Acessei `/locais/42` com a API desligada |
| Resultado esperado | Mensagem "Não foi possível carregar o local" |
| Resultado observado | Tela em branco |
| Status | ❌ Falhou |
| Evidência | Print ou vídeo curto anexado |

> 💡 Remova dados pessoais e credenciais das imagens e logs antes de anexar.

📝 Organize tudo usando o [modelo de relatório do QA](../modelos/modelo-relatorio-qa.md): identificação, critérios, cenários, defeitos, reteste e decisão em um só lugar.

## Passo 5: registrar um defeito

Encontrou um problema? Abra uma Issue com o modelo de **bug** e informe:

1. passos para reproduzir;
2. resultado esperado e resultado obtido;
3. ambiente e versão testada;
4. evidência;
5. severidade (tabela abaixo);
6. Issue original e Pull Request relacionados;
7. responsável pela correção.

| Severidade | Significado | Efeito |
|---|---|---|
| 🔴 Crítica | Segurança, perda de dados, sistema fora do ar ou fluxo essencial impossível | Bloqueia a release |
| 🟠 Alta | Critério importante não funciona | Bloqueia a demanda |
| 🟡 Média | Impacto parcial ou existe alternativa | Correção planejada |
| 🟢 Baixa | Detalhe visual ou de texto de baixo impacto | Não bloqueia sozinha |

## Passo 6: tomar a decisão

| Decisão | Quando usar | O que fazer |
|---|---|---|
| ✅ **Aprovado** | Todos os critérios atendidos, sem falha relevante. | Aprove o PR · registre o resumo dos testes · mova a Issue para `Aprovada`. |
| ☑️ **Aprovado com ressalva** | Limitação pequena, registrada e aceita, que não impede o objetivo. | Registre a ressalva e a Issue de correção · explique por que não bloqueia · aprove o PR · mova para `Aprovada`. |
| ❌ **Reprovado** | Um critério relevante falhou. | Use **Request changes** no PR · relacione os defeitos · mova para `Correção solicitada` · aguarde novo push e faça o reteste. |
| ⏸️ **Bloqueado** | Não dá para concluir o teste por falta de ambiente, dependência ou dado. | Não aprove nem reprove · registre o impedimento · mova para `Bloqueada` · mencione Tech Lead e, se preciso, o professor. |

Registre a decisão e a justificativa nas seções **Decisão** e **Justificativa da decisão** do [relatório do QA](../modelos/modelo-relatorio-qa.md).

## Passo 7: fazer o reteste

Quando o DEV enviar a correção:

1. confirme que existe um novo commit;
2. aguarde o CI ficar verde;
3. use a nova versão no ambiente indicado;
4. repita o cenário que falhou;
5. faça **regressão** nos caminhos relacionados (verificar se nada que funcionava quebrou);
6. registre o novo resultado;
7. só então altere a decisão.

---

## Regra de justiça

Reprovar corretamente uma funcionalidade **não prejudica o QA**. Uma reprovação com evidência protege o projeto e mostra que você cumpriu sua responsabilidade.

## E se der errado?

| Problema | O que fazer |
|---|---|
| Não há ambiente de teste publicado | Registre **Bloqueado por ausência de ambiente** ([Tutorial 6](06-ci-cd.md#parte-b-ambiente-de-teste)). |
| O DEV enviou commits depois da minha aprovação | Sua aprovação não cobre o código novo. Teste de novo. |
| Não sei se é defeito ou fora do escopo | Compare com os critérios de aceite. Se não estiver lá, comente na Issue e mencione o Tech Lead. |

---

[← Tutorial 4](04-tech-lead-revisao-merge.md) · [Próximo: Tutorial 6 — CI e CD →](06-ci-cd.md)
