# 🧪 Cenário 49: Edição de despesa fixa

**Caso de teste:** CT-RF49

**Módulo:** Financeiro / Despesas Fixas / Edição

**Status:** Aprovado conforme a gravação.

**Gravação:** 15/11/2026, 19:07 BRT. **Revisão documental:** 15/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Abrir uma despesa fixa para edição, alterar a recorrência e salvar, refletindo a alteração na listagem. |
| Requisito | [RF49](../Analise%20de%20requisitos.md#rf49) — referência de QA; confirmação de produto pendente. |
| Tipo / prioridade | Funcional manual / regressão; Média, proposta para triagem. |
| Defeito | Nenhum no fluxo avaliado |
| Encaminhamento | Sem reteste corretivo pendente; manter como regressão. Confirmar o pré-preenchimento da recorrência no formulário de edição. |
| Fonte | [Jam — Despesas Fixas](https://jam.dev/c/a4bac99d-e436-4792-831e-8c3a875272bb) e [evidências locais](../Evidencias/CT-RF49_Edicao_Despesa_Fixa/README.md). A mesma gravação é a fonte de [CT-RF46](CT-RF46_Filtros_Despesas_Fixas.md), [CT-RF47](CT-RF47_Cadastro_Despesa_Fixa.md) e [CT-RF48](CT-RF48_Exclusao_Despesa_Fixa.md). |

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
| Dados | Despesa de código 7 "teste 323" (valor R$ 50,00, status ativo, recorrência "1 Mês"), alterada para a recorrência "7 Dias". |

## Pré-condições

- Sessão autenticada com permissão para editar despesas fixas.
- Despesa de teste com todos os campos registrados antes da edição.
- Antes de uma nova execução, identificar versão, permissões e dados de referência e preparar a captura de interface e rede.

## Cenário BDD

```gherkin
Cenário: Editar a recorrência de uma despesa fixa
  Dado que a listagem apresenta a despesa de teste
  Quando o usuário abrir a despesa para edição
  E alterar a recorrência e acionar Salvar Despesa
  Então o sistema deve atualizar a mesma despesa
  E apresentar a nova recorrência na listagem sem criar registro adicional
```

## Passos para execução ou reteste

1. Registrar a despesa na listagem (código, nome, valor, recorrência e status).
2. Acionar a ação de abrir a despesa e conferir o formulário Editar Despesa e o pré-preenchimento.
3. Alterar a recorrência e acionar Salvar Despesa.
4. Conferir a listagem, a quantidade de registros e a requisição de edição.
5. Recarregar a página e consultar novamente a despesa.

Este procedimento orienta a próxima execução. A evidência atual cobre o trecho gravado e os limites descritos abaixo; passos complementares não recebem resultado de execução nesta revisão.

## Resultado esperado

O formulário é preenchido com os dados da despesa; ao salvar, a mesma despesa é atualizada, a listagem apresenta a nova recorrência e nenhum registro adicional é criado.

## Resultado obtido na gravação

A despesa 7 foi aberta para edição, a recorrência foi alterada para "7 Dias" e salva, e a listagem passou a exibir "7 Dias" para o código 7.

| Tempo | Registro |
| --- | --- |
| 0:46 | Clique em botão de ação da linha #7 "teste 323": `POST /api/seleciona/despesa-fixa/1` (corpo `{"id": 7}`) retorna HTTP 200 com a despesa (valor 50, recorrência "1 Mês", status "ativo"). |
| 0:48 | Formulário "Editar Despesa" com Código 7, Nome "teste 323", Status "Ativo", Valor 50 e o seletor Recorrência sem valor visível no quadro; cliques nos seletores de Status e Recorrência. |
| 0:49 | Clique em Salvar Despesa: `POST /api/edita/despesa-fixa/1` com HTTP 200, corpo `{"id": 7, "recorrencia": "7 dias", "nome": "teste 323", "valor": 50, "status": "ativo"}` e resposta `{"verifica_erro": false}`; um `GET` atualiza a lista. |
| 0:51 | Listagem (filtro "teste") com #5 "Teste" (1 Mês) e #7 "teste 323" (R$ 50,00; 7 Dias; ativo); Despesas 16, Ativas 15, Inativas 1. |

**Conclusão:** Aprovado conforme a gravação. A edição atualiza a mesma despesa (código 7), a listagem apresenta a nova recorrência e a quantidade de registros se mantém. A aprovação se limita ao exemplo gravado; não significa validação de todas as variações do fluxo.

## Critérios de aceitação para nova execução

1. O formulário de edição é preenchido com todos os dados da despesa, incluindo a recorrência.
2. Salvar atualiza a mesma despesa, sem criar registro adicional.
3. A listagem apresenta a nova recorrência e os cartões permanecem coerentes.
4. A alteração permanece após recarga da página.
5. Cancelar descarta as alterações.

## Próxima ação e verificações complementares

Usar como regressão. Permanecem fora do cenário gravado: edição de nome, valor e status, Cancelar, mensagem de confirmação e persistência após recarga.

## Observação sobre o pré-preenchimento da recorrência

A resposta de `seleciona` traz a recorrência "1 Mês", mas o quadro de 0:48 mostra o seletor Recorrência sem valor visível, e os envios usam valores em minúsculas ("1 dia", "7 dias"). É compatível com falta de correspondência entre o valor retornado e as opções do seletor, mas o quadro não distingue a falta de pré-preenchimento de uma leitura durante a interação; o ponto permanece a confirmar e não foi tratado como defeito.

## Evidências e limites

- [Jam original — Despesas Fixas](https://jam.dev/c/a4bac99d-e436-4792-831e-8c3a875272bb).
- [Arquivos, origem e limites](../Evidencias/CT-RF49_Edicao_Despesa_Fixa/README.md).
- [Formulário em 0:48](../Evidencias/CT-RF49_Edicao_Despesa_Fixa/editar_despesa_00-48.png), [Listagem em 0:51](../Evidencias/CT-RF49_Edicao_Despesa_Fixa/lista_final_00-51.png), [Resposta de seleção](../Evidencias/CT-RF49_Edicao_Despesa_Fixa/resposta_seleciona.png), [Requisição de edição](../Evidencias/CT-RF49_Edicao_Despesa_Fixa/requisicao_editar.png), [Resposta de edição](../Evidencias/CT-RF49_Edicao_Despesa_Fixa/resposta_editar.png).
- [Linha do tempo](../Evidencias/CT-RF49_Edicao_Despesa_Fixa/linha_do_tempo.txt).

Foram consultados os painéis Info, Console, Network e Actions do Jam, o corpo e a resposta de seleção e de edição e os quadros do vídeo. As capturas foram extraídas da reprodução do Jam. A persistência após recarga, o pré-preenchimento da recorrência e a mensagem de confirmação não foram verificados. Não houve nova execução, inspeção do código, acesso ao banco ou correção da aplicação. O vídeo permanece no Jam.

Análise documental da gravação consultada em 15/11/2026. Esta inclusão não executa novamente o sistema e não constitui reteste. Versão da aplicação, zoom e classificação do ambiente não foram confirmados.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf49) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
