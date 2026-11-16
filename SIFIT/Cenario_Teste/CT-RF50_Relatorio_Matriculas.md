# 🧪 Cenário 50: Relatório de Matrículas em PDF

**Caso de teste:** CT-RF50

**Módulo:** Relatórios / Matrículas

**Status:** Aprovado conforme a gravação.

**Gravação:** 15/11/2026, 19:09 BRT. **Revisão documental:** 15/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Gerar o relatório de Matrículas em PDF para o período informado e apresentar as matrículas do período com valor e quantidade. |
| Requisito | [RF50](../Analise%20de%20requisitos.md#rf50) — referência de QA; confirmação de produto pendente. |
| Tipo / prioridade | Funcional manual / regressão; Média, proposta para triagem. |
| Defeito | Nenhum no fluxo avaliado |
| Encaminhamento | Sem reteste corretivo pendente; manter como regressão. Conferir o conteúdo com as matrículas cadastradas no período. |
| Fonte | [Jam — Relatórios](https://jam.dev/c/3b4777a4-e1b0-4038-9b06-26c73669d7d1) e [evidências locais](../Evidencias/CT-RF50_Relatorio_Matriculas/README.md). A mesma gravação é a fonte de [CT-RF51](CT-RF51_Relatorio_Contas_Receber.md), [CT-RF52](CT-RF52_Relatorio_Contas_Pagar_Pagas.md), [CT-RF53](CT-RF53_Relatorio_Avaliacoes_Vazio.md), [CT-RF54](CT-RF54_Relatorio_Clientes_Vazio.md), [CT-RF55](CT-RF55_Relatorio_Colaboradores_Vazio.md) e [CT-RF56](CT-RF56_Relatorio_Caixas_Vazio.md). |

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
| Dados | Tipo "Matrículas" com Plano "Todos", Tipo de Pagto "Todos" e período 01/11/2026 a 15/11/2026; arquivo `relatorio (5).pdf` (7.784 bytes). |

## Pré-condições

- Sessão autenticada com permissão para gerar relatórios.
- Matrículas do período conhecidas (cliente, plano, grupo, datas e valor).
- Visualizador de PDF disponível.
- Antes de uma nova execução, identificar versão, permissões e dados de referência e preparar a captura de interface e rede.

## Cenário BDD

```gherkin
Cenário: Gerar o relatório de Matrículas em PDF
  Dado que o usuário seleciona o tipo "Matrículas" e o período
  Quando acionar Gerar Relatório
  Então o sistema deve gerar um PDF válido com as matrículas do período
  E apresentar a quantidade de registros
```

## Passos para execução ou reteste

1. Acessar Relatórios, selecionar "Matrículas", manter Plano e Tipo de Pagto em "Todos" e preencher o período.
2. Acionar Gerar Relatório.
3. Abrir o PDF e conferir cabeçalho, período, colunas, registros e quantidade.
4. Comparar com as matrículas cadastradas no período.
5. Repetir com filtros de plano e de pagamento e com período sem matrículas.

Este procedimento orienta a próxima execução. A evidência atual cobre o trecho gravado e os limites descritos abaixo; passos complementares não recebem resultado de execução nesta revisão.

## Resultado esperado

O PDF abre e apresenta o cabeçalho, o período e as matrículas do período com os valores e a quantidade de registros.

## Resultado obtido na gravação

O PDF foi gerado e abre; apresenta uma matrícula no período informado.

| Tempo | Registro |
| --- | --- |
| 0:38 | Formulário "Gerar Relatório" com o tipo "Matrículas", Plano "Todos", Tipo de Pagto "Todos", Data início 01/11/2026 e Data fim 15/11/2026. |
| 19:09:33 (arquivo) | `relatorio (5).pdf`, 7.784 bytes; `POST /api/relatorio/1` com HTTP 200 na lista de rede. |
| PDF | "Relatório de Matrículas"; emitido em 15/11/2026; Data Inicial 01/11/2026; Data Final 15/11/2026; colunas Cliente, Plano, Grupo, Data Inicial, Data Final e Valor Total. |
| PDF | Uma linha: Aluno Demonstracao Manual Sifit; Plano Diário; Treino Livre; 11/11/2026 a 11/11/2026; R$ 20,00; "Quantidade de registros: 1". |

**Conclusão:** Aprovado conforme o PDF. O relatório é gerado com o cabeçalho, o período e uma matrícula com valor e quantidade coerentes entre si. A aprovação se limita ao exemplo; não significa validação do conteúdo contra todas as matrículas cadastradas.

## Critérios de aceitação para nova execução

1. O PDF abre e apresenta cabeçalho, período e colunas do relatório.
2. Os registros correspondem às matrículas do período e aos filtros informados.
3. O valor e a quantidade de registros são coerentes com as linhas.
4. Sem matrículas no período, o relatório apresenta a estrutura vazia explícita.
5. Os filtros de Plano e de Tipo de Pagto restringem o conteúdo.

## Próxima ação e verificações complementares

Usar como regressão. Permanecem fora do cenário gravado: conferência com a lista de matrículas do módulo, filtros de plano e de pagamento, mais de um registro e período sem matrículas.

## Observação sobre o conteúdo

O relatório apresenta uma única matrícula (Plano Diário, R$ 20,00, 11/11/2026), a mesma matrícula cujo valor aparece como "----" em [CT-RF51](CT-RF51_Relatorio_Contas_Receber.md); a conferência com a lista de matrículas do módulo não foi realizada.

## Evidências e limites

- [Jam original — Relatórios](https://jam.dev/c/3b4777a4-e1b0-4038-9b06-26c73669d7d1).
- [Arquivos, origem e limites](../Evidencias/CT-RF50_Relatorio_Matriculas/README.md).
- [Relatório de Matrículas](../Evidencias/CT-RF50_Relatorio_Matriculas/relatorio_5_matriculas.pdf), [primeira página do PDF](../Evidencias/CT-RF50_Relatorio_Matriculas/relatorio_5_matriculas_pagina1.png), [Formulário em 0:38](../Evidencias/CT-RF50_Relatorio_Matriculas/formulario_matriculas_00-38.png), [Lista de rede](../Evidencias/CT-RF50_Relatorio_Matriculas/rede_lista.png).
- [Linha do tempo](../Evidencias/CT-RF50_Relatorio_Matriculas/linha_do_tempo.txt).

Foram consultados os painéis Info, Console e Network do Jam, o quadro do vídeo e o conteúdo do PDF baixado. A atividade do usuário não foi registrada no Console do Jam e a correspondência do arquivo com o tipo foi identificada pelo conteúdo. O conteúdo não foi conferido contra a lista de matrículas do módulo. Não houve nova execução, inspeção do código, acesso ao banco ou correção da aplicação. O vídeo permanece no Jam.

Análise documental da gravação consultada em 15/11/2026. Esta inclusão não executa novamente o sistema e não constitui reteste. Versão da aplicação, zoom e classificação do ambiente não foram confirmados.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf50) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
