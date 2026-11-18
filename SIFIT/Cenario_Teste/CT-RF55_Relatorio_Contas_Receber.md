# 🧪 Cenário 55: Relatório de Contas a Receber sem Valor a Receber

**Caso de teste:** CT-RF55

**Módulo:** Relatórios / Contas a Receber

**Status:** Reprovado nas evidências — Valor a Receber ausente em todas as linhas; defeito em triagem.

**Gravação:** 15/11/2026, 19:09 BRT. **Revisão documental:** 15/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Gerar o relatório de Contas a Receber pendentes em PDF apresentando, para cada conta, o valor a receber e os totais do período. |
| Requisito | [RF55](../Analise%20de%20requisitos.md#rf55) — referência de QA; confirmação de produto pendente. |
| Tipo / prioridade | Funcional manual / manifestação observada; Alta, proposta para triagem. |
| Defeito | [BUG-022](../Relatorio-de-Bugs.md#bug-022), em triagem. |
| Encaminhamento | Investigar a origem do Valor a Receber no relatório, comparar com o módulo Contas a Receber e retestar com valores conhecidos. |
| Fonte | [Jam — Relatórios](https://jam.dev/c/3b4777a4-e1b0-4038-9b06-26c73669d7d1) e [evidências locais](../Evidencias/CT-RF51_Relatorio_Contas_Receber/README.md). A mesma gravação é a fonte de [CT-RF54](CT-RF54_Relatorio_Matriculas.md), [CT-RF56](CT-RF56_Relatorio_Contas_Pagar_Pagas.md), [CT-RF57](CT-RF57_Relatorio_Avaliacoes_Vazio.md), [CT-RF58](CT-RF58_Relatorio_Clientes_Vazio.md), [CT-RF59](CT-RF59_Relatorio_Colaboradores_Vazio.md) e [CT-RF60](CT-RF60_Relatorio_Caixas_Vazio.md). |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/relatorios |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.78 / Windows (x86) 11. |
| Tela / arquivo de vídeo | 1920 × 911 informados no Jam. |
| Duração | 58 s |
| Rede | Classificada como rápida no Jam: 6,8 Mbps, latência de 50 ms. |
| Localização | Brasil. |
| Usuário exibido | Jair, conforme o canto superior direito da tela. |
| Versão / zoom / classificação do ambiente | Não confirmados; registrar antes de nova execução. |
| Dados | Tipo "Contas a Receber" com Tipo de Pagamento "Todos", Status "Pendente", Detalhado desmarcado e período 01/11/2026 a 15/11/2026; arquivo `relatorio (6).pdf` (7.882 bytes). |

## Pré-condições

- Sessão autenticada com permissão para gerar relatórios.
- Contas a receber pendentes do período conhecidas (cliente, conta, vencimento e valor).
- Visualizador de PDF disponível.
- Antes de uma nova execução, identificar versão, permissões e dados de referência e preparar a captura de interface e rede.

## Cenário BDD

```gherkin
Cenário: Gerar o relatório de Contas a Receber pendentes
  Dado que existem contas a receber pendentes no período
  Quando o usuário gerar o relatório de Contas a Receber com Status "Pendente"
  Então o PDF deve apresentar o valor a receber de cada conta
  E apresentar os totais coerentes com as linhas
```

## Passos para execução ou reteste

1. Acessar Relatórios, selecionar "Contas a Receber", Status "Pendente" e o período.
2. Acionar Gerar Relatório.
3. Abrir o PDF e conferir cliente, conta, vencimento, valor a receber e totais.
4. Comparar com as contas pendentes do módulo Contas a Receber.
5. Repetir com Detalhado e com outros status.

Este procedimento orienta a próxima execução. A evidência atual cobre o trecho gravado e os limites descritos abaixo; passos complementares não recebem resultado de execução nesta revisão.

## Resultado esperado

Cada conta pendente apresenta o valor a receber e os totais correspondem às linhas apresentadas.

## Resultado obtido na gravação

O PDF abre e lista três contas pendentes, mas a coluna Valor a Receber apresenta "----" em todas as linhas.

| Tempo | Registro |
| --- | --- |
| 0:43 | Formulário com o tipo "Contas a Receber", Tipo de Pagamento "Todos", Status "Pendente", opção Detalhado e período 01/11/2026 a 15/11/2026. |
| 19:09:39 (arquivo) | `relatorio (6).pdf`, 7.882 bytes; `POST /api/relatorio/1` com HTTP 200 na lista de rede. |
| PDF | "Relatório de Contas a Receber"; Status: pendente; colunas Cliente, Conta, D Vencimento e Valor a Receber. |
| PDF | Três linhas: Aluno Demonstracao Manual Sifit (conta "Plano Plano Diário", 11/11/2026), Rafael Testeira ("Matrícula", 14/11/2026) e Marcelo Longo Zandonadi ("Matrícula", 14/11/2026); Valor a Receber "----" nas três. |
| PDF | "Quantidade de registros: 3"; "Valor Recebido: R$ 0,00". |

**Conclusão:** Reprovado nas evidências. O relatório lista as contas pendentes, mas não apresenta o valor a receber de nenhuma delas, o que impede o uso financeiro do relatório. A causa não foi determinada.

## Critérios de aceitação para nova execução

1. Cada conta pendente apresenta o valor a receber no relatório.
2. Os totais do relatório correspondem às linhas apresentadas.
3. Os valores coincidem com os do módulo Contas a Receber para as mesmas contas.
4. Rótulos e colunas são legíveis e sem duplicação (por exemplo, "D Vencimento" e "Plano Plano Diário").
5. Sem valor disponível, o relatório apresenta indicação explícita e não um marcador.

## Próxima ação e verificações complementares

Comparar com as contas do módulo Contas a Receber e reexecutar com valores conhecidos e a opção Detalhado. Permanecem fora do cenário gravado: outros status, Tipo de Pagamento específico e o conteúdo da resposta da requisição.

## Observação sobre os rótulos

A coluna de vencimento é rotulada "D Vencimento" e a primeira conta aparece como "Plano Plano Diário" (repetição da palavra); o total apresentado é "Valor Recebido: R$ 0,00" em um relatório de contas pendentes. Os pontos não foram classificados como defeitos independentes.

## Evidências e limites

- [Jam original — Relatórios](https://jam.dev/c/3b4777a4-e1b0-4038-9b06-26c73669d7d1).
- [Arquivos, origem e limites](../Evidencias/CT-RF51_Relatorio_Contas_Receber/README.md).
- [Relatório de Contas a Receber](../Evidencias/CT-RF51_Relatorio_Contas_Receber/relatorio_6_contas_receber.pdf), [primeira página do PDF](../Evidencias/CT-RF51_Relatorio_Contas_Receber/relatorio_6_contas_receber_pagina1.png), [Formulário em 0:43](../Evidencias/CT-RF51_Relatorio_Contas_Receber/formulario_contas_receber_00-43.png), [Lista de rede](../Evidencias/CT-RF51_Relatorio_Contas_Receber/rede_lista.png).
- [Linha do tempo](../Evidencias/CT-RF51_Relatorio_Contas_Receber/linha_do_tempo.txt).

Foram consultados os painéis Info, Console e Network do Jam, o quadro do vídeo e o conteúdo do PDF baixado. A atividade do usuário não foi registrada no Console do Jam e a correspondência do arquivo com o tipo foi identificada pelo conteúdo. O conteúdo não foi comparado com o módulo Contas a Receber. Não houve nova execução, inspeção do código, acesso ao banco ou correção da aplicação. O vídeo permanece no Jam.

Análise documental da gravação consultada em 15/11/2026. Esta inclusão não executa novamente o sistema e não constitui reteste. Versão da aplicação, zoom e classificação do ambiente não foram confirmados.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf55) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
