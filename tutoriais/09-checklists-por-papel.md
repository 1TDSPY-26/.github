# Tutorial 9 — Checklists rápidos por papel

[← Voltar à central](../README.md)

Use esta página como **conferência rápida** antes de cada etapa. Cada bloco tem um link para o tutorial completo, caso algum item não esteja claro.

**Ir para:** [DEV](#dev-antes-de-iniciar) · [Tech Lead](#tech-lead-antes-de-liberar-a-issue) · [QA](#qa-antes-de-testar) · [Todos](#todos-antes-da-validação-individual)

---

## DEV antes de iniciar

📖 [Tutorial 3 — Fase 1](03-dev-branch-commits-pr.md#fase-1--começar)

- [ ] Li a Issue inteira.
- [ ] A Issue está `Pronta para iniciar`.
- [ ] Sou o responsável indicado.
- [ ] `develop` está atualizada.
- [ ] Criei a branch com o número da Issue.
- [ ] Registrei o início na Issue.

## DEV antes do Pull Request

📖 [Tutorial 3 — Fases 2 e 3](03-dev-branch-commits-pr.md#fase-2--desenvolver)

- [ ] Atendi aos critérios de aceite.
- [ ] Não misturei outra demanda.
- [ ] Os commits têm mensagens claras.
- [ ] Executei lint.
- [ ] Executei build.
- [ ] Executei os testes disponíveis.
- [ ] Testei erro, carregamento e acessibilidade aplicáveis.
- [ ] Atualizei a branch com `develop`.
- [ ] Não enviei `.env`, senha, token ou dado pessoal.
- [ ] O Pull Request aponta para `develop`.
- [ ] Usei `Closes #NUMERO`.
- [ ] Expliquei como testar.

---

## Tech Lead antes de liberar a Issue

📖 [Tutorial 4 — Parte A](04-tech-lead-revisao-merge.md#parte-a-refinar-uma-demanda)

- [ ] Objetivo definido.
- [ ] Escopo e fora do escopo definidos.
- [ ] Critérios testáveis.
- [ ] Responsável e QA definidos.
- [ ] Squad, esforço e prioridade definidos.
- [ ] Data limite e Milestone definidos.
- [ ] Dependências e riscos registrados.
- [ ] Conteúdo já apresentado ou autorizado.

## Tech Lead antes do merge

📖 [Tutorial 4 — Parte C](04-tech-lead-revisao-merge.md#parte-c-fazer-o-merge)

- [ ] PR relacionado à Issue.
- [ ] Base é `develop`.
- [ ] Escopo conferido.
- [ ] CI verde.
- [ ] Código revisado.
- [ ] Conversas resolvidas.
- [ ] QA aprovou a versão mais recente.
- [ ] Ambiente indicado validado, quando disponível.
- [ ] Nenhum bloqueio aberto.
- [ ] O autor não aprovou o próprio trabalho.

---

## QA antes de testar

📖 [Tutorial 5 — Passos 1 e 2](05-qa-testes.md#passo-1-preparar-o-teste)

- [ ] Critérios de aceite disponíveis.
- [ ] Revisão técnica concluída.
- [ ] CI verde.
- [ ] Ambiente de teste disponível ou bloqueio registrado.
- [ ] Dados e ambiente preparados.
- [ ] Plano de teste registrado.

## QA antes de decidir

📖 [Tutorial 5 — Passo 6](05-qa-testes.md#passo-6-tomar-a-decisão)

- [ ] Caminho principal executado.
- [ ] Erros aplicáveis executados.
- [ ] Carregamento e vazio verificados.
- [ ] Teclado, foco e rótulos verificados.
- [ ] Responsividade verificada.
- [ ] Evidências anexadas.
- [ ] Defeitos possuem Issue e severidade.
- [ ] Decisão e justificativa registradas.

---

## Todos antes da validação individual

Na validação individual, você precisa mostrar **o que você fez**. Confira se consegue:

- [ ] localizar minhas Issues;
- [ ] localizar minhas branches e commits;
- [ ] localizar meus Pull Requests, reviews ou testes;
- [ ] explicar uma decisão que eu tomei;
- [ ] demonstrar minha contribuição;
- [ ] reconhecer limitações e pendências reais;
- [ ] comparar o que foi planejado com o que foi entregue.

> 💡 No GitHub, use os filtros `author:SEU-USUARIO` (PRs e Issues) e `assignee:SEU-USUARIO` (Issues atribuídas a você) para encontrar tudo rapidamente.

---

[← Tutorial 8](08-release.md) · [Voltar à central](../README.md)
