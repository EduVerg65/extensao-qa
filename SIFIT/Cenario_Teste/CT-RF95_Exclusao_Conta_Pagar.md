# 🧪 Cenário 95: Exclusão de conta a pagar com confirmação

**Caso de teste:** CT-RF95

**Módulo:** Financeiro / Contas a Pagar / Exclusão

**Status:** Aprovado conforme a gravação.

**Gravação:** 15/11/2026, 21:58 BRT. **Revisão documental:** 15/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Excluir uma conta a pagar pela lixeira da listagem, após confirmação, removendo-a da listagem. |
| Requisito | [RF95](../Analise%20de%20requisitos.md#rf95) — referência de QA; confirmação de produto pendente. |
| Tipo / prioridade | Funcional manual / regressão; Média, proposta para triagem. |
| Defeito | Nenhum no fluxo avaliado |
| Encaminhamento | Sem reteste corretivo pendente; manter como regressão. Conferir a exclusão de conta paga ou vinculada ao caixa, a persistência após recarga e a ação de cancelar. |
| Fonte | [Jam — Contas a Pagar](https://jam.dev/c/5d0afaf4-5abd-4e85-923f-27448304a9ef) e [evidências locais](../Evidencias/CT-RF95_Exclusao_Conta_Pagar/README.md). A mesma gravação é a fonte de [CT-RF91](CT-RF91_Filtros_Contas_Pagar.md), [CT-RF92](CT-RF92_Cadastro_Conta_Colaborador_Sem_Colaborador.md), [CT-RF93](CT-RF93_Busca_Colaborador_Conta_Pagar.md) e [CT-RF94](CT-RF94_Visualizacao_Conta_Pagar.md). |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/contas-pagar |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.78 / Windows (x86) 11. |
| Tela / arquivo de vídeo | 1920 × 911 informados no Jam. |
| Duração | 1 min |
| Rede | Classificada como rápida no Jam: 7,8 Mbps, latência de 50 ms. |
| Localização | Brasil. |
| Usuário exibido | Jair, conforme o canto superior direito da tela. |
| Versão / zoom / classificação do ambiente | Não confirmados; registrar antes de nova execução. |
| Dados | Conta de código 29, criada na própria gravação (status Cancelado, valor R$ 2.342,34). |

## Pré-condições

- Sessão autenticada com acesso à tela Contas a Pagar.
- Base de contas a pagar conhecida (contas de código 27 e 28 no início da gravação), com fornecedores, colaboradores, categorias e locais de pagamento cadastrados.
- Antes de uma nova execução, identificar versão, permissões e dados de referência e preparar a captura de interface e rede.

## Cenário BDD

```gherkin
Cenário: Excluir uma conta a pagar com confirmação
  Dado que a listagem apresenta a conta de código 29
  Quando o usuário acionar a lixeira e confirmar o diálogo
  Então a conta deve ser removida
  E a listagem deve deixar de apresentá-la
```

## Passos para execução ou reteste

1. Acessar Contas a Pagar e localizar uma conta descartável.
2. Acionar a lixeira e conferir o diálogo de confirmação.
3. Cancelar e conferir que a conta permanece.
4. Acionar novamente e confirmar; observar a requisição e a resposta.
5. Conferir a listagem e, após recarga, a ausência da conta.

Este procedimento orienta a próxima execução. A evidência atual cobre o trecho gravado e os limites descritos abaixo; passos complementares não recebem resultado de execução nesta revisão.

## Resultado esperado

O diálogo pede confirmação; ao confirmar, a requisição de exclusão retorna sem erro e a conta deixa de aparecer na listagem, inclusive após recarga.

## Resultado obtido na gravação

A lixeira da conta 29 abriu um diálogo de confirmação; ao confirmar, `POST deletar-conta-pagar/1` (corpo {"id": 29}) retornou HTTP 200 com `{"verifica_erro": false}` e a listagem voltou a apresentar apenas as duas contas iniciais (27 e 28), com Contas Listadas 2.

| Tempo | Registro |
| --- | --- |
| 0:54 | Clique na lixeira da conta 29: diálogo de confirmação (Cancelar e botão de confirmação). |
| 0:54–0:55 | Confirmação: `POST deletar-conta-pagar/1` com o id 29, HTTP 200 e `verifica_erro` false. |
| 0:59 | Listagem com duas contas (27 e 28) e Contas Listadas 2; a conta 29 não é mais exibida. |

**Rede:** `POST /api/deletar-conta-pagar/1` (HTTP 200, 23 B) com corpo `{"id": 29}` e resposta `{"verifica_erro": false}`, seguido de nova listagem (HTTP 200, 2,2 KiB).

**Conclusão:** Aprovado conforme a gravação. A exclusão pede confirmação e remove a conta sem erro. A aprovação se limita ao exemplo gravado; a persistência após recarga, a ação Cancelar e a exclusão de contas pagas não foram verificadas.

## Critérios de aceitação para nova execução

1. A exclusão exige confirmação do usuário.
2. Cancelar preserva a conta.
3. Confirmar remove a conta sem erro e atualiza a listagem e os cartões.
4. A conta excluída não reaparece após recarga.
5. Contas vinculadas a pagamentos ou ao caixa têm tratamento explícito.

## Próxima ação e verificações complementares

Usar como regressão. Permanecem fora do cenário: cancelar o diálogo, recarga após a exclusão, exclusão de conta paga ou vinculada ao caixa e erro do servidor.

## Evidências e limites

- [Jam original — Contas a Pagar](https://jam.dev/c/5d0afaf4-5abd-4e85-923f-27448304a9ef).
- [Arquivos, origem e limites](../Evidencias/CT-RF95_Exclusao_Conta_Pagar/README.md).
- [Diálogo de confirmação em 0:54.](../Evidencias/CT-RF95_Exclusao_Conta_Pagar/confirmar_exclusao_00-54.png), [Listagem em 0:59](../Evidencias/CT-RF95_Exclusao_Conta_Pagar/lista_apos_exclusao_00-59.png), [Corpo da requisição deletar-conta-pagar](../Evidencias/CT-RF95_Exclusao_Conta_Pagar/requisicao_deletar.png), [Resposta da exclusão](../Evidencias/CT-RF95_Exclusao_Conta_Pagar/resposta_deletar.png), [Lista de rede](../Evidencias/CT-RF95_Exclusao_Conta_Pagar/rede_lista.jpg).
- [Linha do tempo](../Evidencias/CT-RF95_Exclusao_Conta_Pagar/linha_do_tempo.txt).

Foram consultados os painéis Info, Console, Network e Actions do Jam e os quadros do vídeo. As capturas foram extraídas da reprodução do Jam. Não houve nova execução, inspeção do código, acesso ao banco ou correção da aplicação. O vídeo permanece no Jam.

Análise documental da gravação consultada em 15/11/2026. Esta inclusão não executa novamente o sistema e não constitui reteste. Versão da aplicação, zoom e classificação do ambiente não foram confirmados.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf95) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
