# 🧪 Cenário 39: Cadastro de modalidade em SifitBox – Turmas

**Caso de teste:** CT-RF39

**Módulo:** SifitBox / Modalidades / Cadastro

**Status:** Aprovado conforme a gravação.

**Gravação:** 15/11/2026, 18:51 BRT. **Revisão documental:** 15/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Cadastrar uma modalidade informando nome, descrição e status, e apresentá-la na listagem de Modalidades. |
| Requisito | [RF39](../Analise%20de%20requisitos.md#rf39) |
| Tipo / prioridade | Funcional manual, análise de evidências / Média, proposta para triagem. |
| Defeito | Nenhum no fluxo avaliado |
| Encaminhamento | Sem reteste corretivo pendente; manter como regressão. |
| Fonte | [Jam — SifitBox – Turmas](https://jam.dev/c/ee9a133b-d6b1-442d-b4b0-dd87595b7e70) e [evidências locais](../Evidencias/CT-RF39_Cadastro_Modalidade/README.md). A mesma gravação é a fonte de [CT-RF40](CT-RF40_Exclusao_Turmas_Modalidades.md) e [CT-RF41](CT-RF41_Cadastro_Turma_Sem_Modalidade.md). |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/sifitbox/turmas |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.78 / Windows (x86) 11. |
| Tela / arquivo de vídeo | 1920 × 911 informados no Jam. |
| Duração | 1 min 39 s |
| Rede | Classificada como rápida no Jam: 6,8 Mbps, latência de 50 ms. |
| Localização | Brasil. |
| Usuário exibido | Jair, conforme o canto superior direito da tela. |
| Versão / zoom / classificação do ambiente | Não confirmados; registrar antes de nova execução. |
| Dados | Três modalidades existentes (Leo valeska, Modalidade Manual SIFIT 2026 e Modalidade Maromba); nome "teste", descrição "teste" e status Ativo como referência histórica. |

## Pré-condições

- Sessão autenticada com acesso a SifitBox – Turmas e à ação de cadastrar modalidade.
- Listagem de Modalidades conhecida, com a quantidade de registros anotada antes da inclusão.
- Nome de modalidade de teste disponível, sem conflito com registros existentes.
- Antes de uma nova execução, identificar versão, permissões e dados de referência e preparar a captura de interface e rede.

## Cenário BDD

```gherkin
Cenário: Cadastrar uma modalidade
  Dado que a tela SifitBox – Turmas apresenta a listagem de Modalidades
  Quando o usuário informar o nome, a descrição e o status da modalidade
  E acionar o botão de envio de Modalidade
  Então o sistema deve criar a modalidade
  E apresentar o novo registro na listagem com o status informado
  E limpar o formulário de Modalidade
```

## Passos para execução ou reteste

1. Acessar SifitBox – Turmas e registrar as modalidades e seus status.
2. Preencher Nome e Descrição da modalidade e manter o status Ativo.
3. Acionar o botão de envio de Modalidade.
4. Conferir a mensagem, o novo registro na listagem, o status e o formulário.
5. Recarregar a página e consultar novamente a listagem para conferir a persistência.

Este procedimento orienta a próxima execução. A evidência atual cobre o trecho gravado e os limites descritos abaixo; passos complementares, como a recarga da página, não recebem resultado de execução nesta revisão.

## Resultado esperado

A modalidade é criada, passa a constar na listagem com o status informado e o formulário é limpo.

## Resultado obtido na gravação

O cadastro foi concluído: a modalidade "teste" passou a constar na listagem com o status "ativo".

| Tempo | Registro |
| --- | --- |
| 0:00 | Listagem de Modalidades com três registros (Leo valeska, Modalidade Manual SIFIT 2026 e Modalidade Maromba). |
| 1:15–1:17 | Digitação de "teste" nos campos Nome e Descrição do formulário de Modalidade; status Ativo. |
| 1:28 | Formulário de Modalidade ainda preenchido; listagem com três registros. |
| 1:33–1:34 | Cliques nos botões de envio; `POST /api/sifitbox/modalidades/salvar/1` retorna **HTTP 201** (145 B), precedido de `OPTIONS` HTTP 204. |
| 1:35 | Listagem com quatro modalidades; "teste" aparece com o status "ativo" e o formulário de Modalidade está vazio. Um `GET` atualiza a lista. |

**Requisição de criação:** `{"id": {}, "nome": "teste", "descricao": "teste", "status": "ativo"}`.

**Resposta de criação:** `{"id": 4, "empresa_id": 1, "nome": "teste", "descricao": "teste", "status": "ativo", "created_at": "2026-11-15 21:51:31", "updated_at": "2026-11-15 21:51:31"}`.

**Conclusão:** Aprovado conforme a gravação. A modalidade é criada com HTTP 201 e o registro retornado coincide com os dados informados. A aprovação se limita ao exemplo gravado; não significa validação de todas as variações do fluxo.

## Critérios de aceitação para nova execução

1. O formulário permite informar nome, descrição e status e cria a modalidade ao confirmar.
2. A resposta retorna sucesso e o registro com os dados informados e o status escolhido.
3. A listagem passa a exibir a nova modalidade e o formulário é limpo.
4. A modalidade permanece após recarga da página.
5. Dados inválidos ou ausentes recebem validação específica, sem HTTP 500.

## Próxima ação e verificações complementares

Usar como regressão. Permanecem fora do cenário gravado: nome vazio, nome duplicado, limites de tamanho, caracteres especiais, status Inativo no cadastro, mensagem de confirmação e persistência após recarga.

## Observações sobre o payload e a listagem

O corpo enviado inclui `"id": {}` (objeto vazio) em vez de ausência do campo ou valor nulo, e as respostas de turmas trazem `instrutor_id` e `instrutor_nome` também como objetos vazios. O sistema aceitou o envio, e o comportamento não foi tratado como defeito; o contrato da API não foi fornecido.

As três modalidades anteriores aparecem com o status "inativo" na mesma listagem em que o filtro de status exibe "Ativo", enquanto a nova modalidade aparece como "ativo". O comportamento é analisado em [CT-RF40](CT-RF40_Exclusao_Turmas_Modalidades.md) e se relaciona ao ponto a validar de [CT-RF16](CT-RF16_Exclusao_Modalidade.md). Não foi observada mensagem de confirmação nos quadros consultados.

## Evidências e limites

- [Jam original — SifitBox – Turmas](https://jam.dev/c/ee9a133b-d6b1-442d-b4b0-dd87595b7e70).
- [Arquivos, origem e limites](../Evidencias/CT-RF39_Cadastro_Modalidade/README.md).
- [Formulário preenchido em 1:17](../Evidencias/CT-RF39_Cadastro_Modalidade/formulario_modalidade_01-17.png), [listagem após o cadastro em 1:35](../Evidencias/CT-RF39_Cadastro_Modalidade/lista_apos_cadastro_01-35.png), [requisição de criação](../Evidencias/CT-RF39_Cadastro_Modalidade/requisicao_salvar.png) e [resposta de criação](../Evidencias/CT-RF39_Cadastro_Modalidade/resposta_salvar.png).
- [Linha do tempo](../Evidencias/CT-RF39_Cadastro_Modalidade/linha_do_tempo.txt).

Foram consultados os painéis Info, Console (atividade do usuário e erros de rede), Network e Actions do Jam, o corpo da requisição e da resposta de criação e os quadros do vídeo. As capturas foram extraídas da reprodução do Jam e mostram o botão de reprodução sobreposto. O botão exato acionado em 1:33 e em 1:34 não foi identificado com certeza nos quadros; a associação do envio à modalidade apoia-se no corpo da requisição. A persistência após recarga, a mensagem de confirmação e a regra de status não foram verificadas. Não houve nova execução, inspeção do código, acesso ao banco ou correção da aplicação. O vídeo permanece no Jam.

Análise documental da gravação consultada em 15/11/2026. Esta inclusão não executa novamente o sistema e não constitui reteste. Versão da aplicação, zoom e classificação do ambiente não foram confirmados.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf39) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
