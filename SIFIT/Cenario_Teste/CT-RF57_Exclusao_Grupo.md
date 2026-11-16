# 🧪 Cenário 57: Exclusão de grupo

**Caso de teste:** CT-RF57

**Módulo:** Treinamento / Grupos

**Status:** Reprovado nas evidências.

**Gravação:** 15/11/2026, 21h03 BRT. **Revisão documental:** 15/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Excluir um grupo pela listagem ou informar, de forma tratável, por que a exclusão não pode ser concluída. |
| Requisito | [RF57](../Analise%20de%20requisitos.md#rf57) |
| Tipo / prioridade | Funcional manual, análise de evidências / Alta, proposta para triagem. |
| Defeito | [BUG-024](../Relatorio-de-Bugs.md#bug-024) |
| Encaminhamento | Investigar o HTTP 500 com logs do servidor e vínculos do registro; corrigir e retestar os cenários permitido e impedido. |
| Fonte | [Jam — Tela de Grupos](https://jam.dev/c/b1231a75-1a65-4bf0-b795-f52a8c7d3365) |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/grupos |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.78 / Windows (x86) 11. |
| Tela / arquivo de vídeo | 1920 × 911 informados no Jam. |
| Duração | 1 min 38 s |
| Rede | Classificada como rápida no Jam: mais de 10 Mbps, latência de 50 ms. |
| Localização | Brasil. |
| Servidor | Respostas com `x-powered-by: PHP/8.2.35`, `servidor: hcdn`, `plataforma: hospedagem`. |
| Versão / zoom / classificação do ambiente | Não confirmados; registrar antes de nova execução. |
| Dados | Usar dados de teste conhecidos conforme as pré-condições abaixo; valores da gravação são referência histórica, sem copiar credenciais. |

## Pré-condições

- Sessão autenticada com permissão para excluir grupos.
- Existir na listagem um grupo de teste cuja exclusão seja permitida pelas regras do produto.
- Conhecer previamente os vínculos do registro escolhido (treinos, fichas ou turmas associadas), para distinguir impedimento de regra de falha do servidor.
- Antes de uma nova execução, identificar versão, permissões e dados de referência e preparar a captura de interface e rede.

## Cenário BDD

```gherkin
Cenário: Excluir um grupo pela listagem
  Dado que o usuário está autenticado na tela Grupos
  E existe o grupo de código 1 ("Treino Livre") na listagem
  Quando acionar o ícone de exclusão na linha do grupo
  E confirmar a exclusão no diálogo "Deseja deletar o Grupo?"
  Então o sistema deve concluir a exclusão e atualizar a listagem e os contadores
  E não deve retornar erro interno do servidor
```

## Passos para execução ou reteste

1. Acessar a tela Grupos autenticado e registrar o estado inicial da listagem e dos contadores.
2. Acionar o ícone de lixeira na linha do grupo de teste.
3. Confirmar a ação no diálogo "Deseja deletar o Grupo?".
4. Conferir a mensagem apresentada, a listagem, os contadores e a requisição correspondente no painel de rede.
5. Recarregar a página e consultar novamente o registro para verificar a persistência do resultado.

Este procedimento orienta a próxima execução. A evidência atual cobre o trecho gravado e os limites descritos abaixo; passos complementares, como a recarga da página e a consulta ao banco, não recebem resultado de execução nesta revisão.

## Resultado esperado

Concluir a exclusão permitida, remover o registro da listagem e atualizar os contadores; ou, quando houver impedimento de regra, apresentar uma mensagem específica e tratável, sem erro interno do servidor.

## Resultado obtido na gravação

Após a confirmação, a requisição de exclusão retorna HTTP 500 em ambas as tentativas registradas. O grupo de código 1 ("Treino Livre") permanece na listagem e os contadores de cartões (Grupos, Ativos, Mostrar Home, Caixa Externo) não se alteram entre as tentativas.

**Momentos e registros:**

| Tempo | Registro |
| --- | --- |
| 1:19 | Clique no ícone de exclusão da linha do grupo código 1 (`i.bi bi-lixo`). |
| 1:20 | Diálogo "Deseja deletar o Grupo?" com as ações "Cancelar" e "Confirmar". Listagem com 10 registros (Grupos 10, Ativos 10). |
| 1:21 | `POST https://backendsifit.centrion.com.br/api/deleta/grupo/1` retorna **HTTP 500** em 987 ms. |
| 1:23–1:28 | Interações subsequentes na interface (fechamento de diálogo e alternância de tema), sem alteração da listagem. |
| 1:30 | Nova tentativa pelo mesmo fluxo de exclusão. Segundo `POST /api/deleta/grupo/1` retorna **HTTP 500** em 230 ms. |

**Resposta do servidor nas duas tentativas:**

```json
{
  "verifica_erro": true,
  "mensagem": "Erro interno inesperado."
}
```

**Cabeçalhos registrados:** `content-type: application/json; charset=utf-8`, `content-length: 64`, `content-encoding: br`, `x-powered-by: PHP/8.2.35`. Primeira tentativa em `Seg, 16 de nov de 2026 00:03:09 GMT`, `x-hcdn-request-id: 8f18afe5ff0e3a9e3d1c944d69811576-asc-edge13`; segunda em `00:03:19 GMT`, `x-hcdn-request-id: bc5d59dc99d0c01de186f1b3125a9b80-asc-edge13`.

**Conclusão:** Reprovado nas evidências. O erro, o endpoint e a mensagem genérica — idêntica à observada em [CT-RF29](CT-RF29_Exclusao_GrupoMuscular.md) para a exclusão de grupo muscular — estão registrados; a causa do HTTP 500 não foi determinada.

## Critérios de aceitação para nova execução

1. A ação de exclusão apresenta confirmação explícita antes de efetivar a operação.
2. Para um registro cuja exclusão é permitida, a requisição retorna sucesso, o registro deixa a listagem e os contadores são atualizados.
3. Para um registro com vínculo impeditivo, o sistema apresenta mensagem específica sobre o impedimento, sem HTTP 500.
4. Nenhum cenário de exclusão retorna erro interno do servidor.
5. O resultado se mantém após recarga da página e nova consulta.

## Próxima ação e verificações complementares

Investigar o HTTP 500 com os logs do servidor e os vínculos do grupo de código 1; corrigir e retestar os cenários permitido e impedido. Verificar se o registro permanece íntegro após a falha, já que duas tentativas foram enviadas para o mesmo recurso.

A gravação não permite distinguir entre falha de infraestrutura, exceção não tratada na aplicação e restrição de integridade referencial não capturada. O endpoint `/api/deleta/grupo/{id}` e a mensagem genérica retornada coincidem exatamente com os já registrados em [BUG-016](../Relatorio-de-Bugs.md#bug-016) para `/api/deleta/grupo-muscular/{id}`, o que sugere uma causa comum no tratamento de exclusões do backend, a confirmar com a equipe responsável.

Não foi possível confirmar visualmente, nos quadros consultados, o texto do diálogo de erro apresentado após a falha (o componente de alerta aparece e é fechado em menos de um segundo na gravação); a evidência de rede e console, porém, confirma de forma inequívoca a falha e o endpoint.

## Manifestações relacionadas na mesma gravação

A gravação cobre também o cadastro de um novo grupo ("Treino sla", código 11) na tela Grupos, concluído com sucesso antes da tentativa de exclusão aqui documentada; esse fluxo será tratado em cenário próprio para não reunir causas distintas em um mesmo registro.

A listagem apresentada nos quadros deste cenário já reflete esse cadastro; isso não altera o resultado da exclusão.

## Evidências e limites

- [Jam original — Tela de Grupos](https://jam.dev/c/b1231a75-1a65-4bf0-b795-f52a8c7d3365).
- Painel Informações do Jam: URL, carimbo de data/hora, sistema, navegador, tamanho da janela e rede.
- Painel Rede do Jam: lista filtrada por erros, cabeçalhos e corpo de resposta das duas requisições de exclusão.
- Painel Console do Jam, visão de atividade do usuário: cronologia completa de cliques, digitação e erros de rede entre 0:00 e 1:38.
- Quadros consultados: 0:00, 0:19, 0:43, 1:05, 1:13, 1:20, 1:21 e 1:28.
- Pasta local de evidências: a criar em `Evidencias/CT-RF57_Exclusao_Grupo/`; até lá, a fonte é o Jam indicado acima.

Não foram registradas mensagens de console JavaScript na visão consultada, apenas os erros de rede. A causa do HTTP 500 não foi determinada: não houve acesso a logs do servidor, ao corpo completo da resposta além dos 64 bytes retornados, nem consulta ao banco de dados. A persistência do registro após a falha não foi confirmada por recarga de página. O cenário de exclusão com impedimento de regra não foi exercitado.

Análise documental da gravação consultada em 15/11/2026, com leitura direta dos painéis do Jam. Esta inclusão não executa novamente o sistema, não corrige a aplicação e não constitui reteste. Versão da aplicação, zoom e classificação do ambiente não foram confirmados.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
