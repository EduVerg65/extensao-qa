# 🧪 Cenário 51: Cadastro de despesa fixa com duas requisições de criação

**Caso de teste:** CT-RF51

**Módulo:** Financeiro / Despesas Fixas / Cadastro

**Status:** A validar — regra ou contexto pendente.

**Gravação:** 15/11/2026, 19:07 BRT. **Revisão documental:** 15/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Cadastrar uma despesa fixa informando nome, status, valor e recorrência e apresentá-la na listagem, com uma única gravação. |
| Requisito | [RF51](../Analise%20de%20requisitos.md#rf51) — referência de QA; confirmação de produto pendente. |
| Tipo / prioridade | Exploratório / regra a confirmar; Média, proposta para triagem. |
| Defeito | Sem defeito confirmado. |
| Encaminhamento | Confirmar se o segundo POST de criação gerou um registro adicional ou foi descartado, capturando corpos e respostas das duas chamadas em nova execução; registrar defeito apenas se houver duplicidade confirmada. |
| Fonte | [Jam — Despesas Fixas](https://jam.dev/c/a4bac99d-e436-4792-831e-8c3a875272bb) e [evidências locais](../Evidencias/CT-RF47_Cadastro_Despesa_Fixa/README.md). A mesma gravação é a fonte de [CT-RF50](CT-RF50_Filtros_Despesas_Fixas.md), [CT-RF52](CT-RF52_Exclusao_Despesa_Fixa.md) e [CT-RF53](CT-RF53_Edicao_Despesa_Fixa.md). |

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
| Dados | Despesa "teste gg", status Inativo, valor 150 e recorrência "1 Dia" como referência histórica; base com 16 despesas antes do cadastro. |

## Pré-condições

- Sessão autenticada com acesso a Despesas Fixas e à ação Nova Despesa.
- Quantidade de despesas, códigos e valor listado registrados antes da inclusão.
- Nome de despesa de teste disponível, sem conflito com registros existentes.
- Antes de uma nova execução, identificar versão, permissões e dados de referência e preparar a captura de interface e rede.

## Cenário BDD

```gherkin
Cenário: Cadastrar uma despesa fixa
  Dado que a tela Despesas Fixas apresenta a listagem de despesas
  Quando o usuário informar nome, status, valor e recorrência na Nova Despesa
  E confirmar em Salvar Despesa
  Então o sistema deve criar uma única despesa
  E apresentar o novo registro na listagem
  E atualizar os cartões de resumo
```

## Passos para execução ou reteste

1. Acessar Despesas Fixas e registrar a listagem, os códigos e os cartões.
2. Acionar Nova Despesa e preencher nome, status, valor e recorrência.
3. Acionar Salvar Despesa uma única vez.
4. Conferir a mensagem, o novo registro, o código atribuído e os cartões.
5. Conferir na rede o número de requisições de criação e, após recarga, a quantidade de registros.

Este procedimento orienta a próxima execução. A evidência atual cobre o trecho gravado e os limites descritos abaixo; passos complementares não recebem resultado de execução nesta revisão.

## Resultado esperado

A despesa é criada uma única vez, passa a constar na listagem com o código atribuído e os cartões refletem a inclusão.

## Resultado obtido na gravação

A despesa foi criada (código 23) e passou a constar na listagem, mas o clique único em Salvar Despesa gerou duas requisições de criação com HTTP 201.

| Tempo | Registro |
| --- | --- |
| 0:26–0:34 | Formulário "Nova Despesa" com Código vazio, Nome "teste gg", Status "Inativo", Valor 150 e Recorrência "1 Dia". |
| 0:35 | Um clique em Salvar Despesa: `POST /api/cria/despesa-fixa/1` com HTTP 201 (226 ms), corpo `{"recorrencia": "1 dia", "nome": "teste gg", "valor": "150", "status": "inativo"}` e resposta `{"verifica_erro": false, "id": 23}`. |
| 0:35 | Um segundo `POST /api/cria/despesa-fixa/1` com HTTP 201 (58 ms), precedido de `OPTIONS` HTTP 204; corpo e resposta indisponíveis no Jam. |
| 0:36 | Listagem com 17 despesas; cartões Despesas 17, Ativas 15, Inativas 2 e Valor Listado R$ 8.210,00. |
| 0:42 | Filtro Nome "teste": três linhas (#5, #7 e #23); o código 23 "teste gg" tem valor R$ 150,00, recorrência "1 Dia" e status inativo. |

**Conclusão:** A validar. O cadastro cria a despesa de código 23 e a listagem passa de 16 para 17 registros, mas duas requisições de criação com HTTP 201 foram enviadas para um único clique; não foi confirmado se a segunda gerou um registro adicional ou foi descartada, de modo que não se registra defeito antes dessa verificação.

## Critérios de aceitação para nova execução

1. Um único clique em Salvar Despesa gera uma única requisição de criação e um único registro.
2. O código é atribuído pelo sistema e não duplica um código existente.
3. A listagem e os cartões de resumo refletem a inclusão.
4. A mensagem de sucesso ou de erro é apresentada ao usuário.
5. A despesa permanece após recarga da página.

## Próxima ação e verificações complementares

Reproduzir capturando corpos e respostas das duas requisições e conferir a quantidade de registros após recarga. Permanecem fora do cenário gravado: nome vazio, nome duplicado, valor inválido, mensagem de confirmação e persistência após recarga.

## Observação sobre a contagem de registros

Após o cadastro a listagem passa de 16 para 17 registros (um único registro novo visível, código 23) e, após a exclusão desse registro em [CT-RF52](CT-RF52_Exclusao_Despesa_Fixa.md), volta a 16. O quadro de 0:42 não mostra um segundo registro com o mesmo nome, o que é compatível com descarte da segunda chamada ou com um registro oculto; a evidência não distingue as hipóteses.

## Observação sobre o campo Código

O campo Código do formulário aparece vazio no cadastro e o registro recebe o código 23 (os códigos visíveis na listagem chegavam a #19; o restante da lista não foi exibido); a numeração não sequencial é compatível com atribuição automática, como em [CT-RF30](CT-RF30_Cadastro_GrupoMuscular.md), sem confirmação do produto.

## Evidências e limites

- [Jam original — Despesas Fixas](https://jam.dev/c/a4bac99d-e436-4792-831e-8c3a875272bb).
- [Arquivos, origem e limites](../Evidencias/CT-RF47_Cadastro_Despesa_Fixa/README.md).
- [Formulário em 0:34](../Evidencias/CT-RF47_Cadastro_Despesa_Fixa/modal_nova_despesa_00-34.png), [Listagem em 0:36](../Evidencias/CT-RF47_Cadastro_Despesa_Fixa/lista_apos_cadastro_00-36.png), [Filtro "teste" em 0:42](../Evidencias/CT-RF47_Cadastro_Despesa_Fixa/filtro_teste_00-42.png), [Requisição de criação](../Evidencias/CT-RF47_Cadastro_Despesa_Fixa/requisicao_criar.png), [Resposta de criação](../Evidencias/CT-RF47_Cadastro_Despesa_Fixa/resposta_criar.png), [Lista de rede](../Evidencias/CT-RF47_Cadastro_Despesa_Fixa/rede_lista.png).
- [Linha do tempo](../Evidencias/CT-RF47_Cadastro_Despesa_Fixa/linha_do_tempo.txt).

Foram consultados os painéis Info, Console, Network e Actions do Jam, o corpo e a resposta da primeira requisição de criação e os quadros do vídeo; o corpo e a resposta da segunda requisição estão indisponíveis. As capturas foram extraídas da reprodução do Jam. A persistência após recarga e a existência de um registro adicional não foram verificadas. Não houve nova execução, inspeção do código, acesso ao banco ou correção da aplicação. O vídeo permanece no Jam.

Análise documental da gravação consultada em 15/11/2026. Esta inclusão não executa novamente o sistema e não constitui reteste. Versão da aplicação, zoom e classificação do ambiente não foram confirmados.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf51) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
