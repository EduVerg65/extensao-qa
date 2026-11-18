# 🧪 Cenário 100: Cadastro de anamnese — erro de servidor ao salvar ou aplicar

**Caso de teste:** CT-RF100

**Módulo:** Saúde / Fichas Anamnese

**Status:** Reprovado nas evidências.

**Gravação:** 15/11/2026, 22h07 BRT. **Revisão documental:** 15/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Selecionar um aluno, preencher as respostas de um modelo de anamnese e salvar o registro (como rascunho ou aplicando definitivamente) e confirmar que o backend processa a gravação sem erro. |
| Requisito | [RF100](../Analise%20de%20requisitos.md#rf100) |
| Tipo / prioridade | Funcional manual, análise de evidências / Alta, proposta para triagem. |
| Defeito | [BUG-032](../Relatorio-de-Bugs.md#bug-032) |
| Encaminhamento | Investigar a rotina de servidor acionada por `/api/anamnese/aplicar/{id}` e `/api/anamnese/rascunho/{id}`; obter logs do backend para identificar a exceção por trás do erro genérico; corrigir e retestar o cadastro completo de uma anamnese. |
| Fonte | [Jam — Fichas de Anamnese](https://jam.dev/c/7be0fe71-3419-4050-b63f-473d943fa08e) |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/anamneses |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.78 / Windows (x86) 11. |
| Tela / arquivo de vídeo | 1920 × 911 informados no Jam. |
| Duração | 1 min 28 s |
| Rede | Classificada como rápida no Jam: mais de 10 Mbps, latência de 50 ms. |
| Localização | Brasil. |
| Servidor | Respostas com `plataforma: hospedagem`, `servidor: hcdn`. |
| Versão / zoom / classificação do ambiente | Não confirmados; registrar antes de nova execução. |
| Dados | Usar dados de teste conhecidos conforme as pré-condições abaixo; valores da gravação (aluno, modelo e respostas) são referência histórica, sem copiar credenciais. |

## Pré-condições

- Sessão autenticada com permissão para cadastrar anamneses.
- Existir ao menos um aluno cadastrado e selecionável na busca da tela de Nova Anamnese.
- Existir ao menos um modelo de anamnese com uma ou mais perguntas cadastradas.
- Antes de uma nova execução, identificar versão, permissões e dados de referência e preparar a captura de interface e rede.

## Cenário BDD

```gherkin
Cenário: Cadastrar uma anamnese para um aluno
  Dado que o usuário está autenticado na tela Fichas de Anamnese
  E seleciona um aluno existente e um modelo de anamnese
  Quando responder a(s) pergunta(s) do modelo
  E acionar o botão Salvar (aplicar) ou Salvar rascunho
  Então o sistema deve registrar a anamnese sem erro
  E o registro deve ficar disponível para consulta posterior
```

## Passos para execução ou reteste

1. Acessar a tela Fichas de Anamnese autenticado e abrir "Nova Anamnese".
2. Buscar e selecionar um aluno existente; avançar.
3. Selecionar um modelo de anamnese; avançar até a(s) pergunta(s).
4. Preencher a resposta da pergunta e avançar até a revisão final.
5. Acionar "Salvando..." (aplicar) e conferir a resposta da API no painel de rede.
6. Repetir o mesmo preenchimento acionando "Salvar rascunho" em vez de aplicar, para comparar o comportamento entre as duas rotinas.
7. Repetir o procedimento com um segundo modelo de anamnese, para verificar se o erro se repete independentemente do modelo e da resposta informada.

Este procedimento orienta a próxima execução. A evidência atual cobre o trecho gravado e os limites descritos abaixo; a repetição controlada deste fluxo não recebe resultado de execução nesta revisão.

## Resultado esperado

Ao preencher as respostas de uma anamnese e acionar "Salvar rascunho" ou a aplicação definitiva, o backend deve processar a gravação e retornar sucesso, tornando o registro disponível para consulta, sem exigir mensagem de erro genérica ao usuário.

## Resultado obtido na gravação

Ao longo da gravação, o usuário tenta cadastrar uma anamnese para o aluno "Jorge" por quatro vezes (variando a resposta e, em duas delas, o modelo selecionado) e tenta salvar como rascunho por três vezes. Todas as sete tentativas — tanto pela rota de aplicar quanto pela de rascunho — retornam **HTTP 500** com o mesmo corpo de erro genérico, independentemente do modelo de anamnese (`modelo_id` 3 ou 5) ou da resposta enviada ("Esse", "Esssssss" ou "Agachamento"). Em nenhum momento da gravação uma anamnese é salva com sucesso.

**Momentos e registros:**

| Tempo | Registro |
| --- | --- |
| 0:05–0:12 | Abre "Nova Anamnese", busca e seleciona o aluno "Jorge"; avança. |
| 0:16–0:21 | Seleciona o modelo de anamnese (modelo identificado na interface como "Triplet 2", pergunta única "qual é o exercício") e abre o campo de resposta. |
| 0:23 | Digita a resposta "Esse" na pergunta 1. |
| 0:25–0:28 | Avança até a revisão final; clica no botão de aplicar ("Salvando..."). |
| 0:28 (rede) | `POST https://backendsifit.centrion.com.br/api/anamnese/aplicar/1` com `{"modelo_id":3,"respostas":[{"pergunta_id":"5","resposta":"Esse"}],"status":"concluida"}` retorna **HTTP 500**, `{"verifica_erro": true, "mensagem": "Erro interno inesperado."}`. |
| 0:30–0:38 | Fecha o aviso de erro; reabre a resposta pelo ícone de edição e altera o texto para "Esssssss"; avança novamente até a revisão (confirmada na interface: pergunta "quais tipos", resposta "Esssssss"). |
| 0:39 | Clica novamente em aplicar. `POST /api/anamnese/aplicar/1` com a resposta atualizada retorna **HTTP 500** com o mesmo corpo de erro. |
| 0:41–0:42 | Volta uma etapa e aciona "Salvar rascunho". `POST /api/anamnese/rascunho/1` (sem o campo `status`) retorna **HTTP 500**, mesmo corpo de erro — `data: Segunda-feira, 16 de novembro de 2026, 01:05:48 GMT`. |
| 0:44–0:55 | Reinicia o preenchimento; seleciona um segundo modelo de anamnese; digita a resposta "Agachamento" (eventos de digitação registrados como "UM" seguido de "gachamento", resultando no texto final "Agachamento"); revisa a resposta pelo ícone de visualização. |
| 0:56 | Clica em aplicar. `POST /api/anamnese/aplicar/1` retorna **HTTP 500**, mesmo corpo de erro. |
| 0:58–1:03 | Volta, repete a navegação entre etapas (incluindo um Ctrl+C sobre o campo de resposta) e aciona novamente "Salvar rascunho". `POST /api/anamnese/rascunho/1` retorna **HTTP 500**, mesmo corpo de erro. |
| 1:05–1:10 | Repete a navegação (incluindo um Ctrl+V sobre o campo de resposta) e aciona "Salvar rascunho" mais uma vez. `POST /api/anamnese/rascunho/1` retorna **HTTP 500**, mesmo corpo de erro. |
| 1:11–1:12 | Avança e aciona aplicar pela última vez. `POST /api/anamnese/aplicar/1` com `{"modelo_id":5,"respostas":[{"pergunta_id":"5","resposta":"Agachamento"}],"status":"concluida"}` retorna **HTTP 500**, mesmo corpo de erro. |
| 1:13–1:17 | Fecha os avisos de erro, volta e fecha o formulário de nova anamnese sem salvar nenhum registro. |
| 1:18–1:28 | Retorna à listagem, pesquisa "ggg" (sem resultado visível na gravação), clica nos cartões de estatística e em filtros de seleção da tela; nenhuma nova requisição de erro ocorre neste trecho final. |

**Requisição enviada na primeira tentativa de aplicar (0:28):**

```json
{
  "modelo_id": 3,
  "respostas": [
    { "pergunta_id": "5", "resposta": "Esse" }
  ],
  "status": "concluida"
}
```

**Resposta do servidor, idêntica nas sete tentativas (quatro em `aplicar`, três em `rascunho`):**

```json
{
  "verifica_erro": true,
  "mensagem": "Erro interno inesperado."
}
```

**Requisição enviada na última tentativa de aplicar (1:12), com modelo e resposta diferentes:**

```json
{
  "modelo_id": 5,
  "respostas": [
    { "pergunta_id": "5", "resposta": "Agachamento" }
  ],
  "status": "concluida"
}
```

**Cabeçalhos registrados:** `content-type: application/json; charset=utf-8`, `comprimento-do-conteúdo: 64`; data registrada em uma das tentativas de rascunho: `Segunda-feira, 16 de novembro de 2026, 01:05:48 GMT` (compatível com 22h07 BRT de 15/11/2026, considerando o fuso UTC−3 do carimbo informado pelo Jam).

**Conclusão:** Reprovado nas evidências. As duas rotinas de gravação de anamnese (`aplicar` e `rascunho`) retornam consistentemente HTTP 500 com a mesma mensagem genérica, em ambos os endpoints, em dois modelos de anamnese diferentes e com respostas de conteúdo distinto. Nenhuma anamnese é cadastrada com sucesso ao longo de toda a gravação.

## Critérios de aceitação para nova execução

1. Ao preencher corretamente as respostas de um modelo de anamnese e acionar "Salvar rascunho", o backend grava o rascunho e retorna sucesso.
2. Ao preencher corretamente as respostas e acionar a aplicação definitiva, o backend grava a anamnese com `status: "concluida"` e retorna sucesso.
3. O comportamento é validado para mais de um modelo de anamnese e mais de um aluno.
4. Uma anamnese salva com sucesso fica disponível para consulta na listagem.
5. Caso a mensagem "Erro interno inesperado." continue a ocorrer para um cenário específico (por exemplo, pergunta sem resposta ou modelo sem perguntas cadastradas), o sistema deve informar uma mensagem de validação específica em vez do erro genérico de servidor.

## Próxima ação e verificações complementares

Investigar a rotina de servidor acionada pelos endpoints `/api/anamnese/aplicar/{id}` e `/api/anamnese/rascunho/{id}`, com acesso a logs do backend para identificar a exceção real por trás da mensagem genérica "Erro interno inesperado.". O padrão de resposta é idêntico ao já registrado em [BUG-016](../Relatorio-de-Bugs.md#bug-016) e [BUG-024](../Relatorio-de-Bugs.md#bug-024), o que sugere tratamento de erro genérico centralizado no backend que oculta a causa real de falhas distintas; confirmar se a causa aqui é a mesma dessas ocorrências ou uma falha independente específica do módulo de anamnese. Verificar também se o identificador final da URL (`1` em ambos os endpoints) corresponde ao `empresa_id` e não ao id do aluno, do modelo ou da anamnese, seguindo o mesmo padrão de nomenclatura já observado nas investigações de Grupos.

A gravação não permite determinar se a falha está relacionada ao conteúdo das respostas, à estrutura do payload enviado pelo frontend, a uma pergunta ou campo obrigatório não preenchido, ou a uma falha de servidor anterior ao processamento dos dados; não houve acesso a logs do servidor nem consulta direta ao banco de dados.

## Manifestações relacionadas na mesma gravação

Não foram identificadas outras manifestações distintas na mesma gravação: o trecho final (1:17 a 1:28), de retorno à listagem, busca e uso de filtros, não produz novos erros nem evidências adicionais relevantes a este cenário.

## Evidências e limites

- [Jam original — Fichas de Anamnese](https://jam.dev/c/7be0fe71-3419-4050-b63f-473d943fa08e).
- Painel Informações do Jam: URL, carimbo de data/hora, sistema, navegador, tamanho da janela e rede.
- Painel Rede do Jam: sete requisições com HTTP 500 (quatro em `POST /api/anamnese/aplicar/1`, três em `POST /api/anamnese/rascunho/1`) entre 0:28 e 1:12, com cabeçalhos, corpo de solicitação e corpo de resposta.
- Painel Console do Jam, visão de atividade do usuário: cronologia completa de cliques, digitações e erros de rede entre 0:00 e 1:28.
- Quadros e registros de rede consultados: 0:28, 0:39, 0:42, 0:56, 1:03, 1:10 e 1:12.
- Pasta local de evidências: a criar em `Evidencias/CT-RF59_Cadastro_Anamnese/`; até lá, a fonte é o Jam indicado acima.

Não foram registradas mensagens de console JavaScript na visão consultada, apenas os eventos de interação e de rede. A causa real do erro HTTP 500 não foi determinada: não houve acesso a logs do servidor, ao código das rotinas de aplicar/rascunho, nem consulta ao banco de dados. Não foi possível confirmar, pela gravação, se as sete tentativas afetaram o mesmo registro de anamnese em rascunho ou se cada tentativa criou ou tentou criar um registro novo.

Análise documental da gravação consultada em 15/11/2026, com leitura direta dos painéis do Jam. Esta inclusão não executa novamente o sistema, não corrige a aplicação e não constitui reteste. Versão da aplicação, zoom e classificação do ambiente não foram confirmados.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
