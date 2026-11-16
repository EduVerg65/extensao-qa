# 🧪 Cenário 60: Gestão de modelos de anamnese — busca, cadastro, edição e exclusão

**Caso de teste:** CT-RF60

**Módulo:** Treinamento / Fichas de Anamnese (Modelos de Anamnese)

**Status:** Aprovado conforme a gravação.

**Gravação:** 15/11/2026, 23h34 BRT. **Revisão documental:** 16/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Buscar e filtrar modelos de anamnese existentes, cadastrar um novo modelo com perguntas selecionadas do banco de perguntas, editar um modelo por duas vezes e excluir modelos, confirmando que o backend processa todas as operações sem erro. |
| Requisito | [RF60](../Analise%20de%20requisitos.md#rf60) |
| Tipo / prioridade | Funcional manual, análise de evidências / Média. |
| Defeito | Nenhum identificado no fluxo avaliado. |
| Encaminhamento | Nenhuma ação corretiva necessária; manter o cenário como referência de regressão para a tela de Modelos de Anamnese. |
| Fonte | [Jam — Modelos de Anamnese](https://jam.dev/c/4c1e9deb-20ca-417f-ad09-48749857266e) |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/anamnese/modelos |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.78 / Windows (x86) 11. |
| Tela / arquivo de vídeo | 1920 × 911 informados no Jam. |
| Duração | 2 min 32 s |
| Rede | Classificada como rápida no Jam: mais de 10 Mbps, latência de 50 ms. |
| Localização | Brasil. |
| Servidor | Respostas com `plataforma: hospedagem`, `servidor: hcdn`. |
| Versão / zoom / classificação do ambiente | Não confirmados; registrar antes de nova execução. |
| Dados | Usar dados de teste conhecidos conforme as pré-condições abaixo; valores da gravação (nome do modelo, respostas e perguntas do banco) são referência histórica, sem copiar credenciais. |

## Pré-condições

- Sessão autenticada com permissão para gerenciar modelos de anamnese.
- Existir ao menos um modelo de anamnese já cadastrado, para exercitar busca, filtro, edição e exclusão.
- Existir um banco de perguntas com itens cadastrados e pesquisáveis, para seleção ao montar um novo modelo.
- Antes de uma nova execução, identificar versão, permissões e dados de referência e preparar a captura de interface e rede.

## Cenário BDD

```gherkin
Cenário: Gerenciar modelos de anamnese
  Dado que o usuário está autenticado na tela Modelos de Anamnese
  Quando buscar e filtrar os modelos existentes
  E cadastrar um novo modelo com perguntas selecionadas do banco de perguntas
  E editar um modelo cadastrado
  E excluir um ou mais modelos
  Então o sistema deve processar cada operação sem erro
  E refletir o resultado na listagem de modelos
```

## Passos para execução ou reteste

1. Acessar a tela Modelos de Anamnese autenticado.
2. Digitar um termo na busca de modelos e no filtro de status, conferindo o comportamento do filtro.
3. Abrir a pré-visualização de um modelo existente e fechá-la.
4. Acionar "Novo Modelo"; preencher nome e descrição do modelo.
5. Buscar no banco de perguntas e adicionar três perguntas ao modelo.
6. Alternar a pré-visualização do modelo e acionar "Salvar".
7. Reabrir um modelo pela ação de editar, alterar o texto de uma pergunta e salvar.
8. Repetir a edição do mesmo modelo uma segunda vez e salvar novamente.
9. Excluir, pela ação do cartão, os modelos usados no teste, confirmando a exclusão quando solicitado.

Este procedimento orienta a próxima execução. A evidência atual cobre o trecho gravado e os limites descritos abaixo; a repetição controlada deste fluxo não recebe resultado de execução nesta revisão.

## Resultado esperado

Ao buscar, filtrar, cadastrar, editar e excluir modelos de anamnese, o backend deve processar cada operação e retornar sucesso, refletindo o resultado atualizado na listagem, sem exigir mensagem de erro ao usuário.

## Resultado obtido na gravação

Ao longo da gravação, o usuário busca e filtra os modelos de anamnese existentes, pré-visualiza um modelo, cadastra um novo modelo com três perguntas selecionadas do banco de perguntas, edita esse modelo por duas vezes e exclui dois modelos usados no teste. Todas as quinze requisições identificadas aos endpoints `/api/modelos-anamnese/*` retornam **HTTP 200 ou 201**, sem nenhuma ocorrência de erro 4xx ou 5xx. A única requisição com status de erro em toda a gravação é um descarte (**HTTP 499**) de um *beacon* de analytics do Google (`www.google.com.br/.../ads/ga-audiences`), sem relação com o backend do SIFIT.

**Momentos e registros:**

| Tempo | Registro |
| --- | --- |
| 0:03–0:15 | Digita e apaga um termo na busca de modelos; interage várias vezes com o filtro "Todos os status". |
| 0:19–0:21 | Abre a pré-visualização de um modelo existente pelo cartão e a fecha. |
| 0:22 | Aciona "Novo Modelo"; navega para `/anamnese/modelos/novo`. |
| 0:24–0:52 | Preenche o nome do modelo ("Modelos", corrigido) e a descrição ("Esse modelo"). |
| 0:54–1:46 | Pesquisa no banco de perguntas e adiciona três perguntas ao modelo (ícone "+" acionado em 1:21, 1:22 e 1:46). |
| 1:52 | Alterna a pré-visualização do modelo montado. |
| 1:57 (rede) | Aciona "Salvar". `POST https://backendsifit.centrion.com.br/api/modelos-anamnese/salvar/1` retorna **HTTP 201**; navega de volta para a listagem `/anamnese/modelos`. |
| 1:58 | `GET https://www.google.com.br/.../ads/ga-audiences` (beacon de analytics, alheio ao backend do SIFIT) retorna **HTTP 499** (requisição cancelada pelo navegador). |
| 2:00–2:04 | Interage novamente com o filtro de status; abre e fecha a pré-visualização de outro modelo. |
| 2:06–2:07 | Aciona a ação de editar em um cartão; navega para `/anamnese/modelos/6`. |
| 2:09–2:11 | Edita o texto de uma pergunta do modelo (apaga e corrige um caractere). |
| 2:12 (rede) | Aciona "Salvar". `POST /api/modelos-anamnese/alterar/1` retorna **HTTP 201**; navega de `/anamnese/modelos/6` de volta para `/anamnese/modelos`. |
| 2:14–2:17 | Abre e fecha a pré-visualização de um cartão; aciona novamente a edição do mesmo modelo; navega para `/anamnese/modelos/6`. |
| 2:19 (rede) | Aciona "Salvar" uma segunda vez. `POST /api/modelos-anamnese/alterar/1` retorna **HTTP 201**; navega de volta para `/anamnese/modelos`. |
| 2:21 | Aciona a ação de excluir em um cartão e confirma a opção no menu. `POST /api/modelos-anamnese/deletar/1` retorna **HTTP 201**. |
| 2:23 | Repete a exclusão em um segundo cartão. `POST /api/modelos-anamnese/deletar/1` retorna **HTTP 201**. |
| 2:26–2:29 | Confirma um diálogo de exclusão e fecha uma mensagem de confirmação; nenhuma nova requisição de erro ocorre neste trecho final. |

**Requisição de cadastro, com resposta HTTP 201 (1:57):**

```
POST https://backendsifit.centrion.com.br/api/modelos-anamnese/salvar/1
Resposta: HTTP 201 Created
```

**Requisições de edição, ambas com resposta HTTP 201 (2:12 e 2:19):**

```
POST https://backendsifit.centrion.com.br/api/modelos-anamnese/alterar/1
Resposta: HTTP 201 Created (duas ocorrências)
```

**Requisições de exclusão, ambas com resposta HTTP 201 (2:21 e 2:23):**

```
POST https://backendsifit.centrion.com.br/api/modelos-anamnese/deletar/1
Resposta: HTTP 201 Created (duas ocorrências)
```

**Cabeçalhos registrados:** `plataforma: hospedagem`, `servidor: hcdn`, `x-powered-by: PHP/8.2.35`; data registrada na requisição de cadastro: `Segunda-feira, 16 de novembro de 2026, 02:33:41 GMT` (compatível com 23h34 BRT de 15/11/2026, considerando o fuso UTC−3). Os corpos de solicitação e de resposta das chamadas de API não foram capturados pelo Jam ("Corpo indisponível — a página foi atualizada ou houve navegação antes da conclusão da solicitação"), uma limitação da ferramenta e não um comportamento do sistema.

**Conclusão:** Aprovado conforme a gravação. Busca, filtro, pré-visualização, cadastro com perguntas do banco, duas edições e duas exclusões de modelos de anamnese são concluídos com sucesso, sem qualquer resposta de erro do backend do SIFIT ao longo de toda a gravação.

## Critérios de aceitação para reteste

1. A busca e o filtro de status na listagem de modelos retornam resultados consistentes com o termo e o status informados.
2. Um novo modelo é cadastrado com nome, descrição e perguntas do banco, e passa a constar na listagem.
3. Um modelo cadastrado pode ser editado mais de uma vez, preservando as alterações salvas.
4. Um modelo pode ser excluído e deixa de constar na listagem após a exclusão.
5. Nenhuma das operações acima deve retornar erro HTTP 4xx ou 5xx em uso normal.

## Ponto a confirmar

Os três endpoints de escrita observados (`salvar/1`, `alterar/1` e `deletar/1`) e o endpoint de leitura (`GET /api/modelos-anamnese/1`) usam o mesmo sufixo numérico `1`, independentemente do modelo criado, editado ou excluído (identificado na interface como modelo "6"). Isso é compatível com a hipótese já registrada em [CT-RF59](CT-RF59_Cadastro_Anamnese.md) de que esse identificador final corresponde ao `empresa_id` da conta autenticada, e não ao id do modelo — o que também explicaria por que a mesma rota de leitura não gerou conflito ao alternar entre os modelos "6" e outros durante a gravação. Adicionalmente, a resposta do `GET /api/modelos-anamnese/1` (uma leitura) retorna **HTTP 201** em vez do código 200 mais usual para esse tipo de operação; como o valor permanece na faixa de sucesso (2xx) e não impede o funcionamento observado, isso não é tratado como defeito nesta revisão, mas fica registrado para confirmação em conjunto com a equipe de desenvolvimento.

## Evidências e limites

- [Jam original — Modelos de Anamnese](https://jam.dev/c/4c1e9deb-20ca-417f-ad09-48749857266e).
- Painel Informações do Jam: URL, carimbo de data/hora, sistema, navegador, tamanho da janela e rede.
- Painel Rede do Jam: quinze requisições aos endpoints `/api/modelos-anamnese/*`, todas com HTTP 200 ou 201, entre 0:00 e 2:29; nenhuma requisição ao backend do SIFIT com erro 4xx ou 5xx em toda a gravação.
- Painel Ações do Jam: cronologia completa de cliques, digitações e navegações entre 0:00 e 2:32.
- Quadros e registros de rede consultados: 1:57, 2:12, 2:19, 2:21 e 2:23.
- Pasta local de evidências: a criar em `Evidencias/CT-RF60_Gestao_Modelos_Anamnese/`; até lá, a fonte é o Jam indicado acima.

Não foram registradas mensagens de console JavaScript na visão consultada, apenas os eventos de interação e de rede. Os corpos de solicitação e de resposta das chamadas de API não foram capturados pelo Jam, o que impede confirmar o conteúdo exato enviado e recebido em cada operação; a confirmação de sucesso baseia-se nos códigos de status HTTP e na navegação observada após cada ação. Não foi possível confirmar, pela gravação, a quantidade total de modelos existentes antes do início do teste, nem se os modelos editados e excluídos eram exclusivos deste teste ou compartilhados com outro fluxo.

Análise documental da gravação consultada em 16/11/2026, com leitura direta dos painéis do Jam. Esta inclusão não executa novamente o sistema, não corrige a aplicação e não constitui reteste. Versão da aplicação, zoom e classificação do ambiente não foram confirmados.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
