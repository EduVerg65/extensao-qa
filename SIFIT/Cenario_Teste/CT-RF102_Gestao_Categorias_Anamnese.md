# 🧪 Cenário 102: Gestão de categorias de anamnese — filtro, busca, cadastro, edição e exclusão

**Caso de teste:** CT-RF102

**Módulo:** Saúde / Categorias (Anamnese)

**Status:** Aprovado conforme a gravação.

**Gravação:** 16/11/2026, 15h24 BRT. **Revisão documental:** 16/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Filtrar categorias de anamnese por status, pesquisar pelo campo de busca, cadastrar uma nova categoria, editá-la três vezes (ícone, nome e status), cancelar uma quarta tentativa de edição sem salvar e excluir a categoria, confirmando que o backend processa cada operação sem erro. |
| Requisito | [RF102](../Analise%20de%20requisitos.md#rf102) |
| Tipo / prioridade | Funcional manual, análise de evidências / Média. |
| Defeito | Nenhum identificado no fluxo avaliado. |
| Encaminhamento | Nenhuma ação corretiva necessária; manter o cenário como referência de regressão para a tela de Categorias de Anamnese. |
| Fonte | [Jam — Categorias de Anamnese](https://jam.dev/c/fdb1c9f8-c428-4726-9742-617800325d09) |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/anamnese/categorias |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.78 / Windows 11. |
| Duração | 1 min 35 s |
| Localização | Brasil. |
| Servidor | Respostas com `plataforma: hospedagem`, `servidor: hcdn`, `x-powered-by: PHP/8.2.35`. |
| Versão / zoom / classificação do ambiente | Não confirmados; registrar antes de nova execução. |
| Dados | Usar dados de teste conhecidos conforme as pré-condições abaixo; valores da gravação (nome, cor, ícone e status da categoria) são referência histórica, sem copiar credenciais. |

## Pré-condições

- Sessão autenticada com permissão para gerenciar categorias de anamnese.
- Existir ao menos uma categoria de anamnese já cadastrada, para exercitar o filtro por status e a busca.
- Antes de uma nova execução, identificar versão, permissões e dados de referência e preparar a captura de interface e rede.

## Cenário BDD

```gherkin
Cenário: Gerenciar categorias de anamnese
  Dado que o usuário está autenticado na tela Categorias de Anamnese
  Quando filtrar as categorias por status e pesquisar pelo campo de busca
  E cadastrar uma nova categoria
  E editar a categoria cadastrada mais de uma vez
  E cancelar uma tentativa de edição sem salvar
  E excluir a categoria
  Então o sistema deve processar cada operação sem erro
  E refletir o resultado na listagem de categorias
```

## Passos para execução ou reteste

1. Acessar a tela Categorias de Anamnese autenticado.
2. Alternar o filtro "Todos os status" entre as opções disponíveis, conferindo o comportamento do filtro.
3. Digitar e apagar termos no campo de busca, conferindo o comportamento do filtro de texto.
4. Acionar "Nova Categoria"; preencher o nome, selecionar um ícone e uma cor da paleta, mantendo o status padrão, e salvar.
5. Reabrir a categoria pela ação de editar, alterar apenas o ícone e salvar.
6. Reabrir a categoria, corrigir o nome e salvar novamente.
7. Reabrir a categoria, alterar o status e salvar uma terceira vez.
8. Abrir a edição uma quarta vez e cancelar sem salvar, conferindo que nenhuma alteração é enviada ao backend.
9. Excluir, pelo ícone de lixeira do cartão, a categoria usada no teste.

Este procedimento orienta a próxima execução. A evidência atual cobre o trecho gravado e os limites descritos abaixo; a repetição controlada deste fluxo não recebe resultado de execução nesta revisão.

## Resultado esperado

Ao filtrar, pesquisar, cadastrar, editar, cancelar uma edição e excluir categorias de anamnese, o backend deve processar cada operação e retornar sucesso, refletindo o resultado atualizado na listagem, sem exigir mensagem de erro ao usuário, e sem enviar requisição alguma quando a edição é cancelada.

## Resultado obtido na gravação

Ao longo da gravação, o usuário alterna o filtro "Todos os status" por seis vezes, digita e apaga seis termos distintos no campo de busca (incluindo um termo acentuado), cadastra uma nova categoria ("Novo", ícone bicicleta, cor da paleta "doce", status INATIVO), edita essa categoria três vezes seguidas (ícone, depois nome, depois status), testa novamente o filtro de status por mais oito vezes entre as edições, abre uma quarta edição e a cancela sem salvar, e por fim exclui a categoria. Todas as sete requisições identificadas aos endpoints `/api/categorias-anamnese/*` retornam **HTTP 200 ou 201**, sem nenhuma ocorrência de erro 4xx ou 5xx. A única requisição não relacionada ao backend do SIFIT é um *beacon* de telemetria de uma extensão de antivírus do navegador (`gc.kis.v2.scr.kaspersky-labs.com`), também com retorno de sucesso e sem relação com a aplicação. Não foram registradas mensagens de erro no console. O filtro de status e a busca por texto não geram requisição de rede própria, sendo aplicados no próprio navegador (client-side).

**Momentos e registros:**

| Tempo | Registro |
| --- | --- |
| 0:04–0:08 | Alterna o filtro "Todos os status" por seis vezes seguidas, sem gerar requisição de rede. |
| 0:09–0:26 | Clica no campo de busca e digita/apaga seis termos distintos ("novamente", "ua", "g", "Deadá", "gua", "ali"), sem gerar requisição de rede. |
| 0:28 | Aciona "Nova Categoria". |
| 0:29–0:38 | Preenche o nome ("Novo") e interage com os seletores de ícone/cor. |
| 0:42 | Seleciona o ícone de bicicleta (`bi-bicicleta`). |
| 0:45–0:49 | Seleciona a paleta de cores "doce". |
| 0:52 (rede) | Aciona "Salvar". `POST /api/categorias-anamnese/salvar/1` retorna **HTTP 201**, com corpo `{"nome": "Novo ", "cor": "#d97706", "icone": "bi-bicycle", "status": "INATIVO"}` e resposta `{"verifica_erro": false, "id": 6}`. |
| (rede) | `GET /api/categorias-anamnese/1` retorna **HTTP 200** (atualização da listagem). |
| 0:57 | Aciona a ação de editar (ícone de lápis) na categoria recém-criada. |
| 0:59 (rede) | Seleciona o ícone de estrela (`bi-estrela`) e aciona "Salvar". `POST /api/categorias-anamnese/alterar/1` retorna **HTTP 200** (ícone alterado; nome e status mantidos). |
| 1:01–1:09 | Reabre a edição e corrige o nome para "Novo estrela" (apaga e redigita parte do texto). |
| 1:12 (rede) | Aciona "Salvar". `POST /api/categorias-anamnese/alterar/1` retorna **HTTP 200**, com corpo `{"id": 6, "nome": "Novo estrela", "cor": "#d97706", "icone": "bi-star", "status": "INATIVO"}`. |
| 1:13–1:16 | Alterna o filtro "Todos os status" por mais quatro vezes, sem gerar requisição de rede. |
| 1:17–1:18 | Reabre a edição e altera o campo de status. |
| 1:19 (rede) | Aciona "Salvar". `POST /api/categorias-anamnese/alterar/1` retorna **HTTP 200**, com corpo `{"id": 6, "nome": "Novo estrela", "cor": "#d97706", "icone": "bi-star", "status": "ATIVO"}`. |
| 1:20–1:24 | Alterna o filtro "Todos os status" por mais quatro vezes, sem gerar requisição de rede. |
| 1:25–1:27 | Reabre a edição uma quarta vez; clica no seletor de status e no campo de nome, sem digitar nada. |
| 1:28 | Aciona "Cancelar". Nenhuma requisição é enviada ao backend — a categoria permanece com os valores salvos na etapa anterior (nome "Novo estrela", ícone estrela, status ATIVO). |
| 1:30 (rede) | Aciona a exclusão (ícone de lixeira). `POST /api/categorias-anamnese/deletar/1` retorna **HTTP 200**. |
| 1:31 | Fecha uma mensagem/indicador de confirmação; a gravação é encerrada em 1:35 sem nova requisição. |

**Requisição de cadastro, com resposta HTTP 201 (0:52):**

```
POST https://backendsifit.centrion.com.br/api/categorias-anamnese/salvar/1
Corpo: {"nome": "Novo ", "cor": "#d97706", "icone": "bi-bicycle", "status": "INATIVO"}
Resposta: HTTP 201 Created — {"verifica_erro": false, "id": 6}
```

**Requisições de edição, todas com resposta HTTP 200 (0:59, 1:12 e 1:19):**

```
POST https://backendsifit.centrion.com.br/api/categorias-anamnese/alterar/1
Resposta: HTTP 200 OK (três ocorrências — ícone, depois nome, depois status)
```

**Requisição de exclusão, com resposta HTTP 200 (1:30):**

```
POST https://backendsifit.centrion.com.br/api/categorias-anamnese/deletar/1
Resposta: HTTP 200 OK
```

**Cabeçalhos registrados:** `plataforma: hospedagem`, `servidor: hcdn`, `x-powered-by: PHP/8.2.35`; data registrada em requisições próximas ao fim da gravação: `Segunda-feira, 16 de novembro de 2026, 18:23:37 GMT` (compatível com 15h24 BRT de 16/11/2026, considerando o fuso UTC−3).

**Conclusão:** Aprovado conforme a gravação. Filtro por status, busca por texto, cadastro, três edições sucessivas, o cancelamento correto de uma quarta edição e a exclusão de uma categoria de anamnese são concluídos com sucesso, sem qualquer resposta de erro do backend do SIFIT ao longo de toda a gravação.

## Critérios de aceitação para reteste

1. O filtro de status e a busca por texto na listagem de categorias aplicam-se de forma consistente, sem gerar erro.
2. Uma nova categoria é cadastrada com nome, cor, ícone e status, e passa a constar na listagem.
3. Uma categoria cadastrada pode ser editada mais de uma vez (ícone, nome e status, isoladamente ou em conjunto), preservando as alterações salvas.
4. Ao cancelar uma edição em andamento, nenhuma alteração é enviada ao backend e os valores salvos anteriormente são mantidos.
5. Uma categoria pode ser excluída e deixa de constar na listagem após a exclusão.
6. Nenhuma das operações acima deve retornar erro HTTP 4xx ou 5xx em uso normal.

## Ponto a confirmar

Assim como observado em [CT-RF101](CT-RF101_Gestao_Modelos_Anamnese.md), os endpoints de escrita e leitura (`salvar/1`, `alterar/1`, `deletar/1` e `GET /api/categorias-anamnese/1`) usam o mesmo sufixo numérico `1`, independentemente da categoria criada, editada ou excluída (identificada na interface como categoria "6"). Isso reforça a hipótese já registrada de que esse identificador final corresponde ao `empresa_id` da conta autenticada, e não ao id do próprio registro. Também vale registrar, para confirmação com a equipe de desenvolvimento, a diferença de código de status entre operações semelhantes neste módulo: o cadastro retorna HTTP 201 (esperado para criação), enquanto as edições e a exclusão retornam HTTP 200 — um padrão mais previsível do que o observado em CT-RF101, onde edição e exclusão retornaram 201. Por fim, a ferramenta de gravação (Jam) apresentou instabilidade ao exibir os cabeçalhos de detalhe de algumas requisições diferentes com o mesmo identificador de requisição e o mesmo horário — tratado como uma limitação da ferramenta de captura, já que a URL, o método e o código de status de cada requisição permaneceram corretos e distintos ao serem reconferidos.

## Evidências e limites

- [Jam original — Categorias de Anamnese](https://jam.dev/c/fdb1c9f8-c428-4726-9742-617800325d09).
- Painel Informações do Jam: URL, carimbo de data/hora, sistema, navegador e duração.
- Painel Rede do Jam: sete requisições aos endpoints `/api/categorias-anamnese/*`, todas com HTTP 200 ou 201, entre 0:52 e 1:30; nenhuma requisição ao backend do SIFIT com erro 4xx ou 5xx em toda a gravação.
- Painel Ações do Jam: cronologia completa de cliques, digitações e navegações entre 0:00 e 1:35.
- Painel Console do Jam: nenhuma mensagem de erro registrada.
- Quadros e registros de rede consultados: 0:52, 0:59, 1:12, 1:19 e 1:30.
- Pasta local de evidências: a criar em `Evidencias/CT-RF61_Gestao_Categorias_Anamnese/`; até lá, a fonte é o Jam indicado acima.

Não foi possível confirmar, pela gravação, a quantidade total de categorias existentes antes do início do teste, nem se a categoria editada e excluída era exclusiva deste teste ou compartilhada com outro fluxo. O filtro por status e a busca por texto foram exercitados apenas pela interação registrada no painel Ações, sem captura de tela da listagem filtrada resultante em cada termo testado.

Análise documental da gravação consultada em 16/11/2026, com leitura direta dos painéis do Jam. Esta inclusão não executa novamente o sistema, não corrige a aplicação e não constitui reteste. Versão da aplicação, zoom e classificação do ambiente não foram confirmados.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
