# 🧪 Cenário 63: Visualização e edição de lead na tela Prospecção

**Caso de teste:** CT-RF63

**Módulo:** Prospecção / Leads / Visualização e edição

**Status:** Aprovado conforme a gravação.

**Gravação:** 15/11/2026, 21:52 BRT. **Revisão documental:** 15/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Abrir um lead pela lupa da listagem, alterar o nome e salvar, refletindo a alteração na listagem. |
| Requisito | [RF63](../Analise%20de%20requisitos.md#rf63) — referência de QA; confirmação de produto pendente. |
| Tipo / prioridade | Funcional manual / regressão; Média, proposta para triagem. |
| Defeito | Nenhum no fluxo avaliado |
| Encaminhamento | Sem reteste corretivo pendente; manter como regressão. Confirmar a persistência após recarga, a edição dos demais campos e o título do modal. |
| Fonte | [Jam — Prospecção](https://jam.dev/c/308607ff-8abc-40af-8c7c-429ce506ed64) e [evidências locais](../Evidencias/CT-RF63_Edicao_Lead_Prospeccao/README.md). A mesma gravação é a fonte de [CT-RF58](CT-RF58_Tema_Notificacoes_Prospeccao.md), [CT-RF59](CT-RF59_Busca_Leads_Prospeccao.md), [CT-RF60](CT-RF60_Filtro_Estagio_Leads.md), [CT-RF61](CT-RF61_Cadastro_Lead_Prospeccao.md) e [CT-RF62](CT-RF62_Telefone_Lead_Sem_Validacao.md). |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/prospeccao |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.78 / Windows (x86) 11. |
| Tela / arquivo de vídeo | 1920 × 911 informados no Jam. |
| Duração | 1 min 2 s |
| Rede | Classificada como rápida no Jam: 5,4 Mbps, latência de 100 ms. |
| Localização | Brasil. |
| Usuário exibido | Jair, conforme o canto superior direito da tela. |
| Versão / zoom / classificação do ambiente | Não confirmados; registrar antes de nova execução. |
| Dados | Lead de código 10 (nome "teste", estágio Interessado) com o nome alterado para "testetete". |

## Pré-condições

- Sessão autenticada com acesso à tela Prospecção.
- Base de leads conhecida, com códigos, nomes e estágios registrados antes da execução.
- Antes de uma nova execução, identificar versão, permissões e dados de referência e preparar a captura de interface e rede.

## Cenário BDD

```gherkin
Cenário: Editar o nome de um lead
  Dado que a listagem apresenta o lead de código 10
  Quando o usuário abrir o lead pela lupa, alterar o nome e acionar Salvar Lead
  Então a alteração deve ser enviada ao servidor sem erro
  E a listagem deve apresentar o novo nome
```

## Passos para execução ou reteste

1. Acessar Prospecção e localizar um lead na listagem.
2. Acionar a lupa da linha e conferir os dados no modal.
3. Alterar o nome (e, em outra execução, estágio, e-mail, telefone e observação) e acionar Salvar Lead.
4. Conferir a requisição de atualização, a resposta e a listagem.
5. Recarregar a página e conferir a persistência.

Este procedimento orienta a próxima execução. A evidência atual cobre o trecho gravado e os limites descritos abaixo; passos complementares não recebem resultado de execução nesta revisão.

## Resultado esperado

O modal apresenta os dados do lead, a alteração é enviada com HTTP 200 e sem erro, e a listagem mostra o novo valor, que permanece após recarga.

## Resultado obtido na gravação

A lupa do lead 10 abriu o modal "Visualizar Lead" com os dados do registro (código 10, estágio Interessado); o nome foi alterado para "testetete" e, ao salvar, `POST /api/atualizar-lead/1` retornou HTTP 200 com `{"verifica_erro": false}`; a listagem apresentou "testetete" em 1:01.

| Tempo | Registro |
| --- | --- |
| 0:45 | Clique na lupa da linha do lead 10: `POST buscar-lead/1` (HTTP 200) com os dados do lead e `GET planos/1` (HTTP 200). |
| 0:47 | Modal "Visualizar Lead": estágio atual Interessado, código 10, nome "teste", estágio Interessado. |
| 0:54–0:57 | Nome alterado para "testetete" no próprio modal; clique em Salvar Lead em 0:57. |
| 0:57–1:01 | `POST atualizar-lead/1` (HTTP 200, {"verifica_erro": false}); nova chamada `GET leads/1`; a listagem filtrada por "tes" apresenta "Teste A" (código 4) e "testetete" (código 10). |

**Rede:** `POST /api/buscar-lead/1` (corpo {"id": 10}; resposta com o lead completo), `GET /api/planos/1` (HTTP 200, 8,1 KiB), `POST /api/atualizar-lead/1` (corpo {"id": 10, "nome": "testetete", ...}; resposta {"verifica_erro": false}) e `GET /api/leads/1` (HTTP 200, 1,9 KiB).

**Conclusão:** Aprovado conforme a gravação. O lead é aberto, o nome é atualizado com HTTP 200 e a listagem reflete a alteração. A aprovação se limita ao nome; os demais campos, a persistência após recarga e o título "Visualizar Lead" em um modal editável não foram verificados.

## Critérios de aceitação para nova execução

1. A lupa abre o modal com os dados do lead selecionado.
2. A alteração de qualquer campo é enviada ao servidor e gravada sem erro.
3. A listagem reflete o novo valor sem recarga manual.
4. O valor permanece após recarregar a página.
5. O título do modal corresponde à ação disponível (visualizar ou editar).

## Próxima ação e verificações complementares

Usar como regressão. Permanecem fora do cenário gravado: edição de estágio, e-mail, telefone e observação, campos obrigatórios vazios, recarga da página e a revisão do título do modal.

## Observação sobre o título do modal

O modal tem o título "Visualizar Lead" e o botão "Salvar Lead" e permite edição; o texto pode induzir o usuário a entender que a tela é somente de consulta. O ponto não gera defeito antes de a regra de interface ser informada.

## Observação sobre a data de criação

O lead de código 10 aparece com a data 16/11/2026 na listagem, enquanto a gravação ocorreu em 15/11/2026, às 21:52 BRT; a diferença é compatível com horário do servidor em UTC, sem confirmação, e não entra no veredito.

## Evidências e limites

- [Jam original — Prospecção](https://jam.dev/c/308607ff-8abc-40af-8c7c-429ce506ed64).
- [Arquivos, origem e limites](../Evidencias/CT-RF63_Edicao_Lead_Prospeccao/README.md).
- [Modal Visualizar Lead em 0:47](../Evidencias/CT-RF63_Edicao_Lead_Prospeccao/visualizar_lead_00-47.png), [Nome em edição em 0:57 (recorte do quadro; e-mail e telefone omitidos).](../Evidencias/CT-RF63_Edicao_Lead_Prospeccao/nome_editado_00-57.png), [Listagem em 1:01](../Evidencias/CT-RF63_Edicao_Lead_Prospeccao/lista_apos_edicao_01-01.png), [Corpo da requisição buscar-lead](../Evidencias/CT-RF63_Edicao_Lead_Prospeccao/requisicao_buscar.png), [Resposta de buscar-lead](../Evidencias/CT-RF63_Edicao_Lead_Prospeccao/resposta_buscar.png), [Corpo da requisição atualizar-lead](../Evidencias/CT-RF63_Edicao_Lead_Prospeccao/requisicao_atualizar.png), [Resposta de atualizar-lead](../Evidencias/CT-RF63_Edicao_Lead_Prospeccao/resposta_atualizar.png).
- [Linha do tempo](../Evidencias/CT-RF63_Edicao_Lead_Prospeccao/linha_do_tempo.txt).

Foram consultados os painéis Info, Console, Network e Actions do Jam e os quadros do vídeo. As capturas foram extraídas da reprodução do Jam; quadros com o e-mail digitado no formulário não foram incluídos nem recortados com esse dado. Os recortes do modal omitem o e-mail e o telefone. A edição dos demais campos, a persistência após recarga e a validação de campos obrigatórios não foram exercitadas. Não houve nova execução, inspeção do código, acesso ao banco ou correção da aplicação. O vídeo permanece no Jam.

Análise documental da gravação consultada em 15/11/2026. Esta inclusão não executa novamente o sistema e não constitui reteste. Versão da aplicação, zoom e classificação do ambiente não foram confirmados.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf63) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
