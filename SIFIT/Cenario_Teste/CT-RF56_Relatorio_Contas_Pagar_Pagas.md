# 🧪 Cenário 56: Relatório de Contas a Pagar (Pagas) sem registros

**Caso de teste:** CT-RF56

**Módulo:** Relatórios / Contas a Pagar

**Status:** A validar — regra ou contexto pendente.

**Gravação:** 15/11/2026, 19:09 BRT. **Revisão documental:** 15/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Gerar o relatório de Contas a Pagar (Pagas) em PDF e apresentar os pagamentos do período ou a estrutura vazia com totais. |
| Requisito | [RF56](../Analise%20de%20requisitos.md#rf56) — referência de QA; confirmação de produto pendente. |
| Tipo / prioridade | Exploratório / regra a confirmar; Média, proposta para triagem. |
| Defeito | Sem defeito confirmado. |
| Encaminhamento | Confirmar se existem contas pagas no período informado e, se existirem, investigar a ausência; sem registros, o comportamento é compatível com o esperado. Registrar defeito apenas se houver divergência com os dados do módulo Contas a Pagar. |
| Fonte | [Jam — Relatórios](https://jam.dev/c/3b4777a4-e1b0-4038-9b06-26c73669d7d1) e [evidências locais](../Evidencias/CT-RF52_Relatorio_Contas_Pagar_Pagas/README.md). A mesma gravação é a fonte de [CT-RF54](CT-RF54_Relatorio_Matriculas.md), [CT-RF55](CT-RF55_Relatorio_Contas_Receber.md), [CT-RF57](CT-RF57_Relatorio_Avaliacoes_Vazio.md), [CT-RF58](CT-RF58_Relatorio_Clientes_Vazio.md), [CT-RF59](CT-RF59_Relatorio_Colaboradores_Vazio.md) e [CT-RF60](CT-RF60_Relatorio_Caixas_Vazio.md). |

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
| Dados | Tipo "Contas a Pagar" com período 01/11/2026 a 15/11/2026; arquivo `relatorio (7).pdf` (7.872 bytes). |

## Pré-condições

- Sessão autenticada com permissão para gerar relatórios.
- Contas a pagar pagas no período conhecidas (fornecedor, vencimento, pagamento e valores).
- Visualizador de PDF disponível.
- Antes de uma nova execução, identificar versão, permissões e dados de referência e preparar a captura de interface e rede.

## Cenário BDD

```gherkin
Cenário: Gerar o relatório de Contas a Pagar (Pagas)
  Dado que o usuário seleciona o tipo "Contas a Pagar" e o período
  Quando acionar Gerar Relatório
  Então o PDF deve apresentar as contas pagas do período
  E, sem contas pagas, deve apresentar a estrutura vazia com totalizadores zerados
```

## Passos para execução ou reteste

1. Registrar as contas a pagar pagas do período no módulo correspondente.
2. Acessar Relatórios, selecionar "Contas a Pagar" e preencher o período.
3. Acionar Gerar Relatório.
4. Abrir o PDF e conferir cabeçalho, colunas, linhas e totalizadores.
5. Repetir com período que contenha pagamentos.

Este procedimento orienta a próxima execução. A evidência atual cobre o trecho gravado e os limites descritos abaixo; passos complementares não recebem resultado de execução nesta revisão.

## Resultado esperado

O PDF apresenta as contas pagas do período, ou a estrutura vazia com totalizadores zerados quando não houver pagamentos.

## Resultado obtido na gravação

O PDF abre e apresenta a estrutura do relatório sem nenhuma linha, com os totalizadores R$ 0,00 e R$ 0,00.

| Tempo | Registro |
| --- | --- |
| 0:48 | Formulário com o tipo "Contas a Pagar" e período 01/11/2026 a 15/11/2026. |
| 19:09:44 (arquivo) | `relatorio (7).pdf`, 7.872 bytes; `POST /api/relatorio/1` com HTTP 200 na lista de rede. |
| PDF | "Relatório de Contas a Pagar (Pagas)"; Período 01/11/2026 até 15/11/2026; colunas Data Venc., Fornecedor / Favorecido, Tipo Pagto, Data Pagto, Valor Bruto e Valor Líquido. |
| PDF | Nenhuma linha; "TOTALIZADORES: R$ 0,00  R$ 0,00". |

**Conclusão:** A validar. O relatório abre com a estrutura esperada e totalizadores zerados, o que é coerente com um período sem contas pagas; como o conteúdo do módulo Contas a Pagar no período não foi conferido, não se registra defeito.

## Critérios de aceitação para nova execução

1. O PDF abre e apresenta cabeçalho, período e colunas do relatório.
2. As contas pagas do período aparecem com valores bruto e líquido coerentes com o módulo.
3. Sem contas pagas, o relatório apresenta a estrutura vazia com totalizadores zerados ou mensagem explícita.
4. Os totalizadores correspondem às linhas apresentadas.
5. O título do relatório identifica o filtro aplicado (Pagas).

## Próxima ação e verificações complementares

Conferir as contas a pagar do período no módulo e reexecutar com um período que contenha pagamentos. Permanecem fora do cenário gravado: contas pendentes, outros filtros e o conteúdo da resposta.

## Observação sobre o filtro de pagas

O título do PDF é "Relatório de Contas a Pagar (Pagas)", enquanto o formulário do quadro de 0:48 não mostra um filtro de status; a regra do produto sobre quais contas o relatório abrange não foi fornecida.

## Evidências e limites

- [Jam original — Relatórios](https://jam.dev/c/3b4777a4-e1b0-4038-9b06-26c73669d7d1).
- [Arquivos, origem e limites](../Evidencias/CT-RF52_Relatorio_Contas_Pagar_Pagas/README.md).
- [Relatório de Contas a Pagar (Pagas)](../Evidencias/CT-RF52_Relatorio_Contas_Pagar_Pagas/relatorio_7_contas_pagar_pagas.pdf), [primeira página do PDF](../Evidencias/CT-RF52_Relatorio_Contas_Pagar_Pagas/relatorio_7_contas_pagar_pagas_pagina1.png), [Formulário em 0:48](../Evidencias/CT-RF52_Relatorio_Contas_Pagar_Pagas/formulario_contas_pagar_00-48.png), [Lista de rede](../Evidencias/CT-RF52_Relatorio_Contas_Pagar_Pagas/rede_lista.png).
- [Linha do tempo](../Evidencias/CT-RF52_Relatorio_Contas_Pagar_Pagas/linha_do_tempo.txt).

Foram consultados os painéis Info, Console e Network do Jam, o quadro do vídeo e o conteúdo do PDF baixado. A atividade do usuário não foi registrada no Console do Jam e a correspondência do arquivo com o tipo foi identificada pelo conteúdo. As contas a pagar do período no módulo não foram conferidas. Não houve nova execução, inspeção do código, acesso ao banco ou correção da aplicação. O vídeo permanece no Jam.

Análise documental da gravação consultada em 15/11/2026. Esta inclusão não executa novamente o sistema e não constitui reteste. Versão da aplicação, zoom e classificação do ambiente não foram confirmados.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf56) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
