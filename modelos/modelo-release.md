# Relatório de Release

[← Voltar à central](../README.md)

> **Quando usar:** no fim de cada CP, pelo Tech Lead junto com os QAs, ao preparar e publicar a release. **Onde registrar:** no Pull Request `release/cpN → main` e na descrição da GitHub Release. Passo a passo no [Tutorial 8](../tutoriais/08-release.md).
>
> Copie a partir da linha abaixo e preencha.

---

## Identificação

- Turma:
- CP:
- Release:
- Branch:
- Tag:
- Data:
- Tech Leads:
- QAs responsáveis:

## Objetivo da versão

Descreva o resultado principal desta Release.

## Demandas incluídas

| Issue | Pull Request | Squad | Responsável | Resultado do QA |
|---|---|---|---|---|
| # | # |  |  |  |

## Demandas retiradas

| Issue | Motivo | Decisão registrada por |
|---|---|---|
| # |  |  |

## Defeitos conhecidos

| Issue | Gravidade | Impacto | Solução temporária |
|---|---|---|---|
| # |  |  |  |

## Verificações

- [ ] `npm run lint` aprovado.
- [ ] `npm run build` aprovado.
- [ ] Teste de regressão executado.
- [ ] Rotas verificadas.
- [ ] CRUD verificado, quando aplicável.
- [ ] Teclado, foco, rótulos e contraste revisados.
- [ ] Nenhuma credencial foi publicada.
- [ ] README atualizado.
- [ ] Link do deploy conferido.

## Decisão do QA

- [ ] Go — pode publicar.
- [ ] Go com ressalvas — pode publicar com pendências registradas.
- [ ] No-Go — não deve publicar.

Justificativa:

## Autorização do professor

- [ ] Autorizada.
- [ ] Bloqueada.

Observações:

## Publicação

- Pull Request para `main`:
- Commit publicado:
- Link de produção: https://portal-locais-acessiveis-prod.up.railway.app/
- Data e horário da verificação:

## Retorno à versão anterior

Informe a tag ou o commit da última versão válida e como restaurá-la em caso de falha.

