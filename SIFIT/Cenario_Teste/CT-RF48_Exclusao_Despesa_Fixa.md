# 🧪 Cenário 48: Exclusão de despesa fixa com confirmação

**Caso de teste:** CT-RF48

**Módulo:** Financeiro / Despesas Fixas / Exclusão

**Status:** Aprovado conforme a gravação.

**Gravação:** 15/11/2026, 19:07 BRT. **Revisão documental:** 15/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Excluir uma despesa fixa pela lixeira, com confirmação prévia, atualizando a listagem e os cartões. |
| Requisito | [RF48](../Analise%20de%20requisitos.md#rf48) — referência de QA; confirmação de produto pendente. |
| Tipo / prioridade | Funcional manual / regressão; Média, proposta para triagem. |
| Defeito | Nenhum no fluxo avaliado |
| Encaminhamento | Sem reteste corretivo pendente; manter como regressão. Confirmar o tratamento de exclusões com vínculos e a persistência após recarga. |
| Fonte | [Jam — Despesas Fixas](https://jam.dev/c/a4bac99d-e436-4792-831e-8c3a875272bb) e [evidências locais](../Evidencias/CT-RF48_Exclusao_Despesa_Fixa/README.md). A mesma gravação é a fonte de [CT-RF46](CT-RF46_Filtros_Despesas_Fixas.md), [CT-RF47](CT-RF47_Cadastro_Despesa_Fixa.md) e [CT-RF49](CT-RF49_Edicao_Despesa_Fixa.md). |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/despesas-fixas |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.78 / Windows (x86) 11. |
| Tela / arquivo de vídeo | 1920 × 911 informados no Jam. |
| Duração | 52 s |
| Rede | Classificada como rápida no Jam: 6,8 Mbps, latência de 50 ms. |
| Localização | Brasil. |
| Usuário exibido | Jair, conforme o canto superior direito da tela. |
| Versão / zoom / classificação do ambiente | Não confirmados; registrar antes de nova execução. |
| Dados | Despesa de código 23 "teste gg" (inativa, R$ 150,00) criada no CT-RF47; filtro Nome "teste" aplicado; base com 17 despesas antes da exclusão. |

## Pré-condições

- Sessão autenticada com permissão para excluir despesas fixas.
- Despesa de teste com código, valor e status registrados antes da exclusão.
- Quantidade de despesas e cartões registrados antes da exclusão.
- Antes de uma nova execução, identificar versão, permissões e dados de referência e preparar a captura de interface e rede.

## Cenário BDD

```gherkin
Cenário: Excluir uma despesa fixa com confirmação
  Dado que a listagem apresenta a despesa de teste
  Quando o usuário acionar a lixeira da despesa
  E confirmar a exclusão no diálogo
  Então o sistema deve excluir a despesa
  E removê-la da listagem
  E atualizar os cartões de resumo
```

## Passos para execução ou reteste

1. Registrar a listagem, os códigos e os cartões; filtrar pela despesa de teste.
2. Acionar a lixeira da despesa.
3. Conferir o diálogo de confirmação e confirmar.
4. Conferir a listagem, os cartões e a requisição de exclusão.
5. Recarregar a página e consultar novamente a despesa.

Este procedimento orienta a próxima execução. A evidência atual cobre o trecho gravado e os limites descritos abaixo; passos complementares não recebem resultado de execução nesta revisão.

## Resultado esperado

O sistema pede confirmação, exclui a despesa permitida, remove o registro da listagem e atualiza os cartões.

## Resultado obtido na gravação

Após a confirmação, a despesa foi excluída: saiu da listagem e os cartões voltaram aos valores anteriores ao cadastro.

| Tempo | Registro |
| --- | --- |
| 0:42 | Filtro Nome "teste" com #5, #7 e #23 "teste gg"; cartões Despesas 17, Ativas 15, Inativas 2 e Valor Listado R$ 250,00. |
| 0:44 | Clique na lixeira da linha #23. |
| 0:44–0:45 | Diálogo com o texto "Deseja excluir a despesa fixa?" e as ações Cancelar e Confirmar; clique em Confirmar em 0:45. |
| 0:45 | `OPTIONS` HTTP 204 e `POST /api/deleta/despesa-fixa/1` com HTTP 200 (58 ms), corpo `{"id": 23}` e resposta `{"verifica_erro": false}`; um `GET` atualiza a lista. |
| 0:46–0:51 | Listagem sem a despesa 23: Despesas 16, Ativas 15, Inativas 1 e Valor Listado R$ 100,00 (filtro "teste" com #5 e #7). |

**Conclusão:** Aprovado conforme a gravação. A exclusão pede confirmação, retorna sucesso e a listagem e os cartões passam de 17 para 16 despesas e de 2 para 1 inativa. A aprovação se limita ao exemplo gravado; não significa validação de todas as variações do fluxo.

## Critérios de aceitação para nova execução

1. A ação de exclusão apresenta confirmação explícita antes de efetivar a operação.
2. A exclusão permitida remove o registro da listagem e atualiza os cartões.
3. A resposta informa sucesso e o resultado se mantém após recarga da página.
4. Cancelar no diálogo preserva o registro.
5. Despesas com vínculo impeditivo recebem mensagem específica, sem erro interno.

## Próxima ação e verificações complementares

Usar como regressão. Permanecem fora do cenário gravado: Cancelar no diálogo, despesa com vínculos, persistência após recarga e a natureza da exclusão (física ou lógica).

## Observação sobre a natureza da exclusão

A despesa 23 desaparece da listagem e o total volta a 16, o que é compatível com exclusão física ou com inativação ocultada pelo filtro; como o filtro de status estava em "Todos", a hipótese de exclusão lógica seria visível como inativa e não foi observada. A regra do produto não foi fornecida.

## Evidências e limites

- [Jam original — Despesas Fixas](https://jam.dev/c/a4bac99d-e436-4792-831e-8c3a875272bb).
- [Arquivos, origem e limites](../Evidencias/CT-RF48_Exclusao_Despesa_Fixa/README.md).
- [Diálogo em 0:44](../Evidencias/CT-RF48_Exclusao_Despesa_Fixa/confirmar_exclusao_00-44.png), [Listagem em 0:51](../Evidencias/CT-RF48_Exclusao_Despesa_Fixa/lista_final_00-51.png), [Requisição de exclusão](../Evidencias/CT-RF48_Exclusao_Despesa_Fixa/requisicao_deletar.png), [Resposta de exclusão](../Evidencias/CT-RF48_Exclusao_Despesa_Fixa/resposta_deletar.png).
- [Linha do tempo](../Evidencias/CT-RF48_Exclusao_Despesa_Fixa/linha_do_tempo.txt).

Foram consultados os painéis Info, Console, Network e Actions do Jam, o corpo e a resposta da exclusão e os quadros do vídeo. As capturas foram extraídas da reprodução do Jam. A persistência após recarga e a natureza da exclusão não foram verificadas. Não houve nova execução, inspeção do código, acesso ao banco ou correção da aplicação. O vídeo permanece no Jam.

Análise documental da gravação consultada em 15/11/2026. Esta inclusão não executa novamente o sistema e não constitui reteste. Versão da aplicação, zoom e classificação do ambiente não foram confirmados.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf48) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
