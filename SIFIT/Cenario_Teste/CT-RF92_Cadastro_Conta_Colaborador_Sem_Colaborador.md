# 🧪 Cenário 92: Conta a pagar a colaborador é cadastrada sem colaborador informado

**Caso de teste:** CT-RF92

**Módulo:** Financeiro / Contas a Pagar / Cadastro

**Status:** Reprovado nas evidências — conta de colaborador gravada sem colaborador; defeito em triagem.

**Gravação:** 15/11/2026, 21:58 BRT. **Revisão documental:** 15/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Cadastrar uma conta a pagar do tipo Pagto. Colaborador exigindo a identificação do colaborador favorecido antes da gravação. |
| Requisito | [RF92](../Analise%20de%20requisitos.md#rf92) — referência de QA; confirmação de produto pendente. |
| Tipo / prioridade | Funcional manual / teste negativo; Alta, proposta para triagem. |
| Defeito | [BUG-039](../Relatorio-de-Bugs.md#bug-039), em triagem. |
| Encaminhamento | Confirmar com o produto a obrigatoriedade do colaborador no tipo Pagto. Colaborador, reproduzir com o formulário em branco e retestar o envio válido e a persistência. |
| Fonte | [Jam — Contas a Pagar](https://jam.dev/c/5d0afaf4-5abd-4e85-923f-27448304a9ef) e [evidências locais](../Evidencias/CT-RF92_Cadastro_Conta_Colaborador_Sem_Colaborador/README.md). A mesma gravação é a fonte de [CT-RF91](CT-RF91_Filtros_Contas_Pagar.md), [CT-RF93](CT-RF93_Busca_Colaborador_Conta_Pagar.md), [CT-RF94](CT-RF94_Visualizacao_Conta_Pagar.md) e [CT-RF95](CT-RF95_Exclusao_Conta_Pagar.md). |

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
| Dados | Conta do tipo Pagto. Colaborador, título "sdfsdfsdfsdf", status Cancelado, tipo de despesa Fixa, documento "sdfsdfsdf", valor 2342,34 e observação "dasdasd"; campos Código e Colaborador vazios. |

## Pré-condições

- Sessão autenticada com acesso à tela Contas a Pagar.
- Base de contas a pagar conhecida (contas de código 27 e 28 no início da gravação), com fornecedores, colaboradores, categorias e locais de pagamento cadastrados.
- Antes de uma nova execução, identificar versão, permissões e dados de referência e preparar a captura de interface e rede.

## Cenário BDD

```gherkin
Cenário: Exigir o colaborador em conta do tipo Pagto. Colaborador
  Dado que o formulário Cadastrar Conta a Pagar está com o tipo Pagto. Colaborador
  Quando o usuário preencher os demais campos sem informar o colaborador e acionar Salvar
  Então o sistema deve impedir o envio e indicar que o colaborador é obrigatório
  E nenhuma conta deve ser criada sem favorecido
```

## Passos para execução ou reteste

1. Acionar Nova Conta e selecionar o tipo Pagto. Colaborador.
2. Preencher título, documento, categoria, valor e demais campos obrigatórios sem informar o colaborador (Código e Colaborador vazios).
3. Acionar Salvar e observar a mensagem de validação e a rede.
4. Conferir a listagem e a coluna Fornecedor / Colaborador da conta criada.
5. Repetir informando o colaborador e comparar.

Este procedimento orienta a próxima execução. A evidência atual cobre o trecho gravado e os limites descritos abaixo; passos complementares não recebem resultado de execução nesta revisão.

## Resultado esperado

Para o tipo Pagto. Colaborador, o sistema exige a identificação do colaborador e impede a gravação enquanto o campo estiver vazio, com mensagem clara.

## Resultado obtido na gravação

A conta foi gravada (`POST cadastrar-conta-pagar/1`, HTTP 201, `verifica_erro` false) com `tipo_conta` "PAG_COLABORADOR" e `colaborador_recebedor_id` e `colaborador_nome` vazios; na listagem a conta de código 29 aparece com "-" na coluna Fornecedor / Colaborador e status Cancelado. Nenhuma mensagem de validação foi apresentada.

| Tempo | Registro |
| --- | --- |
| 0:15 | Formulário Cadastrar Conta a Pagar: tipo "Pagto. Colaborador", campos Código e Colaborador vazios e botão Pesquisar ao lado. |
| 0:25–0:28 | Busca de colaborador com o termo "sds" sem resultado (modal Buscar Colaborador com a tabela vazia); modal fechado sem colaborador selecionado. |
| 0:41 | Formulário preenchido (título, documento, valor 2342,34, observação) com Código e Colaborador ainda vazios. |
| 0:42 | Clique em Salvar: `POST cadastrar-conta-pagar/1` com HTTP 201. |
| 0:50 | Listagem com a conta de código 29, título "sdfsdfsdfdf", coluna Fornecedor / Colaborador "-" e status Cancelado; Contas Listadas 3. |

**Rede:** `POST /api/cadastrar-conta-pagar/1` (HTTP 201, 27 B) com `"tipo_conta": "PAG_COLABORADOR"`, `"colaborador_recebedor_id": ""`, `"colaborador_nome": ""` e `"fornecedor_id": ""`; resposta `{"verifica_erro": false}`.

**Conclusão:** Reprovado nas evidências. A conta do tipo Pagto. Colaborador foi gravada sem colaborador, sem mensagem de validação. A reprovação se apoia na expectativa de que um pagamento a colaborador exija o favorecido; a regra não foi informada e o campo não indica obrigatoriedade no quadro consultado.

## Critérios de aceitação para nova execução

1. Conta do tipo Pagto. Colaborador exige o colaborador antes da gravação.
2. A ausência do colaborador gera mensagem de validação junto ao campo.
3. O servidor rejeita a criação sem colaborador, independentemente da interface.
4. A listagem apresenta o colaborador na coluna Fornecedor / Colaborador.
5. Conta com colaborador informado é gravada e listada corretamente.

## Próxima ação e verificações complementares

Registrar o BUG-039 em triagem, confirmar a regra com o produto e reproduzir capturando a mensagem, o corpo e a resposta; testar também o tipo de fornecedor sem fornecedor.

## Observação sobre o status inicial

A conta foi cadastrada com status "Cancelado" e tipo de despesa "Fixa", valores escolhidos na própria gravação; o status inicial padrão e o efeito do cancelamento nos cartões não foram informados.

## Evidências e limites

- [Jam original — Contas a Pagar](https://jam.dev/c/5d0afaf4-5abd-4e85-923f-27448304a9ef).
- [Arquivos, origem e limites](../Evidencias/CT-RF92_Cadastro_Conta_Colaborador_Sem_Colaborador/README.md).
- [Formulário em 0:15](../Evidencias/CT-RF92_Cadastro_Conta_Colaborador_Sem_Colaborador/formulario_tipo_colaborador_00-15.png), [Formulário preenchido em 0:41](../Evidencias/CT-RF92_Cadastro_Conta_Colaborador_Sem_Colaborador/formulario_preenchido_00-41.png), [Listagem em 0:50](../Evidencias/CT-RF92_Cadastro_Conta_Colaborador_Sem_Colaborador/lista_apos_cadastro_00-50.png), [Corpo da requisição cadastrar-conta-pagar](../Evidencias/CT-RF92_Cadastro_Conta_Colaborador_Sem_Colaborador/requisicao_cadastrar.png), [Resposta da requisição](../Evidencias/CT-RF92_Cadastro_Conta_Colaborador_Sem_Colaborador/resposta_cadastrar.png), [Lista de rede](../Evidencias/CT-RF92_Cadastro_Conta_Colaborador_Sem_Colaborador/rede_lista.jpg).
- [Linha do tempo](../Evidencias/CT-RF92_Cadastro_Conta_Colaborador_Sem_Colaborador/linha_do_tempo.txt).

Foram consultados os painéis Info, Console, Network e Actions do Jam e os quadros do vídeo. As capturas foram extraídas da reprodução do Jam. Não houve nova execução, inspeção do código, acesso ao banco ou correção da aplicação. O vídeo permanece no Jam.

Análise documental da gravação consultada em 15/11/2026. Esta inclusão não executa novamente o sistema e não constitui reteste. Versão da aplicação, zoom e classificação do ambiente não foram confirmados.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf92) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
