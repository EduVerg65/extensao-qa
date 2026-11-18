# 🧪 Cenário 19: Visualização dos dados de uma conta a pagar

**Caso de teste:** CT-RF19

**Módulo:** Operação da Academia / Contas a Pagar / Visualização

**Status:** Aprovado conforme a gravação.

**Gravação:** 15/11/2026, 21:58 BRT. **Revisão documental:** 15/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Abrir a conta pela lupa da listagem e apresentar as informações gerais, os dados da conta, do colaborador e do documento. |
| Requisito | [RF19](../Analise%20de%20requisitos.md#rf19) — referência de QA; confirmação de produto pendente. |
| Tipo / prioridade | Funcional manual / regressão; Baixa, proposta para triagem. |
| Defeito | Nenhum no fluxo avaliado |
| Encaminhamento | Sem reteste corretivo pendente; manter como regressão. Conferir a conta com dados completos de colaborador ou fornecedor e o rótulo do tipo. |
| Fonte | [Jam — Contas a Pagar](https://jam.dev/c/5d0afaf4-5abd-4e85-923f-27448304a9ef) e [evidências locais](../Evidencias/CT-RF94_Visualizacao_Conta_Pagar/README.md). A mesma gravação é a fonte de [CT-RF16](CT-RF16_Filtros_Contas_Pagar.md), [CT-RF17](CT-RF17_Cadastro_Conta_Colaborador_Sem_Colaborador.md), [CT-RF18](CT-RF18_Busca_Colaborador_Conta_Pagar.md) e [CT-RF20](CT-RF20_Exclusao_Conta_Pagar.md). |

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
| Dados | Conta de código 29 (título "sdfsdfsdfdf", valor R$ 2.342,34, vencimento 15/11/2026, status Cancelado), cadastrada na própria gravação. |

## Pré-condições

- Sessão autenticada com acesso à tela Contas a Pagar.
- Base de contas a pagar conhecida (contas de código 27 e 28 no início da gravação), com fornecedores, colaboradores, categorias e locais de pagamento cadastrados.
- Antes de uma nova execução, identificar versão, permissões e dados de referência e preparar a captura de interface e rede.

## Cenário BDD

```gherkin
Cenário: Visualizar uma conta a pagar
  Dado que a listagem apresenta a conta de código 29
  Quando o usuário acionar a lupa da linha
  Então o modal Visualizar Conta a Pagar deve apresentar as informações gerais, os dados da conta, do colaborador e do documento
  E o botão Fechar deve retornar à listagem
```

## Passos para execução ou reteste

1. Acessar Contas a Pagar e localizar uma conta na listagem.
2. Acionar a lupa da linha e conferir as seções do modal.
3. Comparar os dados com os informados no cadastro.
4. Fechar o modal e conferir a listagem.
5. Repetir com conta de fornecedor e com colaborador informado.

Este procedimento orienta a próxima execução. A evidência atual cobre o trecho gravado e os limites descritos abaixo; passos complementares não recebem resultado de execução nesta revisão.

## Resultado esperado

O modal apresenta os dados da conta correspondentes ao cadastro, com rótulos legíveis, e fecha sem alterar a listagem.

## Resultado obtido na gravação

A lupa da conta 29 abriu o modal Visualizar Conta a Pagar com o selo CANCELADO, funcionário cadastrante "Jair", data de lançamento 15/11/2026, tipo exibido como "PAG_COLABORADOR", tipo de despesa "fixa", título, valor R$ 2.342,34, vencimento 15/11/2026, dados do documento e observação "dasdasd"; a seção Dados do Colaborador ficou sem código e nome. O botão Fechar retornou à listagem.

| Tempo | Registro |
| --- | --- |
| 0:52 | Clique na lupa: `POST seleciona-conta-pagar/1` (HTTP 200); modal com informações gerais, dados da conta, dados do colaborador, documento e observação. |
| 0:53 | Clique em Fechar: modal fechado e listagem restaurada. |

**Rede:** `POST /api/seleciona-conta-pagar/1` (HTTP 200, 1,3 KiB) e `GET /api/empresa/moedas/1` (HTTP 200).

**Conclusão:** Aprovado conforme a gravação. O modal apresenta os dados gravados da conta e fecha corretamente. A aprovação se limita ao exemplo gravado; o tipo aparece com o código interno "PAG_COLABORADOR" e a seção do colaborador está vazia, o que decorre do CT-RF17.

## Critérios de aceitação para nova execução

1. O modal apresenta os dados da conta selecionada conforme gravados.
2. Os rótulos exibidos ao usuário são legíveis (sem códigos internos).
3. As seções do colaborador ou do fornecedor apresentam o favorecido quando informado.
4. O botão Fechar retorna à listagem sem alterações.
5. A consulta não altera a conta.

## Próxima ação e verificações complementares

Usar como regressão. Permanecem fora do cenário: conta de fornecedor, conta com colaborador informado, conta paga e conta atrasada, e a revisão do rótulo do tipo.

## Observação sobre o tipo exibido

O tipo da conta aparece como "PAG_COLABORADOR", valor interno enviado ao servidor, enquanto o formulário usa o rótulo "Pagto. Colaborador"; o ponto não gera defeito antes de a regra de interface ser informada.

## Evidências e limites

- [Jam original — Contas a Pagar](https://jam.dev/c/5d0afaf4-5abd-4e85-923f-27448304a9ef).
- [Arquivos, origem e limites](../Evidencias/CT-RF94_Visualizacao_Conta_Pagar/README.md).
- [Modal Visualizar Conta a Pagar em 0:52](../Evidencias/CT-RF94_Visualizacao_Conta_Pagar/visualizar_conta_00-52.png), [Lista de rede](../Evidencias/CT-RF94_Visualizacao_Conta_Pagar/rede_lista.jpg).
- [Linha do tempo](../Evidencias/CT-RF94_Visualizacao_Conta_Pagar/linha_do_tempo.txt).

Foram consultados os painéis Info, Console, Network e Actions do Jam e os quadros do vídeo. As capturas foram extraídas da reprodução do Jam. Não houve nova execução, inspeção do código, acesso ao banco ou correção da aplicação. O vídeo permanece no Jam.

Análise documental da gravação consultada em 15/11/2026. Esta inclusão não executa novamente o sistema e não constitui reteste. Versão da aplicação, zoom e classificação do ambiente não foram confirmados.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf19) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
