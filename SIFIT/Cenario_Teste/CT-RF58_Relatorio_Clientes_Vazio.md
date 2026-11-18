# 🧪 Cenário 58: Relatório de Clientes gera arquivo vazio

**Caso de teste:** CT-RF58

**Módulo:** Relatórios / Clientes

**Status:** Reprovado nas evidências — arquivo gerado vazio (0 bytes); defeito em triagem.

**Gravação:** 15/11/2026, 19:09 BRT. **Revisão documental:** 15/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Gerar o relatório de Clientes em PDF para o período informado e apresentar o conteúdo ao usuário, inclusive quando não houver registros. |
| Requisito | [RF58](../Analise%20de%20requisitos.md#rf58) — referência de QA; confirmação de produto pendente. |
| Tipo / prioridade | Funcional manual / manifestação observada; Alta, proposta para triagem. |
| Defeito | [BUG-023](../Relatorio-de-Bugs.md#bug-023), em triagem. |
| Encaminhamento | Investigar a geração do PDF de Clientes com logs do servidor, comparar com os relatórios que abrem e retestar com e sem registros no período. |
| Fonte | [Jam — Relatórios](https://jam.dev/c/3b4777a4-e1b0-4038-9b06-26c73669d7d1) e [evidências locais](../Evidencias/CT-RF54_Relatorio_Clientes_Vazio/README.md). A mesma gravação é a fonte de [CT-RF54](CT-RF54_Relatorio_Matriculas.md), [CT-RF55](CT-RF55_Relatorio_Contas_Receber.md), [CT-RF56](CT-RF56_Relatorio_Contas_Pagar_Pagas.md), [CT-RF57](CT-RF57_Relatorio_Avaliacoes_Vazio.md), [CT-RF59](CT-RF59_Relatorio_Colaboradores_Vazio.md) e [CT-RF60](CT-RF60_Relatorio_Caixas_Vazio.md). |

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
| Dados | Tipo de relatório "Clientes"; período 01/11/2026 a 15/11/2026; formato de saída PDF; `relatorio (3).pdf` (19:09:17), com 0 bytes (correspondência inferida) |

## Pré-condições

- Sessão autenticada com permissão para gerar relatórios.
- Período e filtros do relatório registrados; base com e sem registros no período conhecida.
- Visualizador de PDF disponível e pasta de downloads conferida antes e depois da geração.
- Antes de uma nova execução, identificar versão, permissões e dados de referência e preparar a captura de interface e rede.

## Cenário BDD

```gherkin
Cenário: Gerar o relatório de Clientes em PDF
  Dado que o usuário seleciona o tipo "Clientes" e o período
  Quando acionar Gerar Relatório
  Então o sistema deve gerar um arquivo PDF válido
  E o arquivo deve abrir com o cabeçalho, o período e os registros do período
  E, sem registros, deve apresentar o relatório vazio com totais zerados ou mensagem explícita
```

## Passos para execução ou reteste

1. Acessar Relatórios, selecionar o tipo "Clientes" e preencher o período.
2. Acionar Gerar Relatório.
3. Conferir a requisição de geração e o arquivo baixado (tamanho e abertura).
4. Abrir o PDF e conferir cabeçalho, período e registros.
5. Repetir com período sem registros e com outros filtros.

Este procedimento orienta a próxima execução. A evidência atual cobre o trecho gravado e os limites descritos abaixo; passos complementares não recebem resultado de execução nesta revisão.

## Resultado esperado

O sistema gera um PDF válido com o conteúdo do relatório de Clientes, ou um relatório vazio explícito quando não houver registros.

## Resultado obtido na gravação

A geração do relatório de Clientes conclui a requisição com HTTP 200, mas o arquivo baixado tem 0 bytes e não abre; nenhuma mensagem de erro foi observada.

| Tempo | Registro |
| --- | --- |
| 0:23 | Formulário "Gerar Relatório" com o tipo "Clientes" ("Cadastro e situação dos alunos"), Data início 01/11/2026 e Data fim 15/11/2026. |
| 19:09:17 (arquivo) | `relatorio (3).pdf` com 0 bytes; correspondência com Clientes inferida pela ordem dos downloads. |
| rede | `POST /api/relatorio/1` com HTTP 200 compatível com o arquivo; corpo e resposta indisponíveis no Jam. |

**Rede:** a lista de rede da gravação tem nove entradas: um `OPTIONS` HTTP 204 e oito `POST /api/relatorio/1` com HTTP 200 (um por arquivo baixado), com corpos e respostas indisponíveis no Jam.

**Conclusão:** Reprovado nas evidências. O relatório de Clientes retorna HTTP 200 e baixa um arquivo de 0 bytes, que não abre; a falha afeta também Avaliações, Clientes, Colaboradores e Caixas (mesmo defeito, em triagem). A causa não foi determinada.

## Critérios de aceitação para nova execução

1. O arquivo gerado é um PDF válido, com tamanho maior que zero, que abre no visualizador.
2. O relatório apresenta cabeçalho, período, filtros e registros do período.
3. Sem registros, o relatório apresenta a estrutura com totais zerados ou mensagem explícita, sem arquivo vazio.
4. Falhas de geração são informadas ao usuário, sem resposta HTTP 200 com arquivo vazio.
5. O nome e o tipo do arquivo correspondem ao relatório solicitado.

## Próxima ação e verificações complementares

Investigar a geração com os logs do servidor e comparar com os relatórios de Matrículas, Contas a Receber e Contas a Pagar, que abrem. Permanecem fora do cenário gravado: período com registros conhecidos, outros filtros e o conteúdo da resposta da requisição.

## Observação sobre a correspondência dos arquivos

A correspondência entre este arquivo e o tipo de relatório é inferida pela ordem dos downloads e pela ordem de seleção dos tipos no vídeo (os arquivos 5 a 7 foram identificados pelo conteúdo e seguem a mesma ordem); o corpo da requisição não foi capturado pelo Jam.

## Evidências e limites

- [Jam original — Relatórios](https://jam.dev/c/3b4777a4-e1b0-4038-9b06-26c73669d7d1).
- [Arquivos, origem e limites](../Evidencias/CT-RF54_Relatorio_Clientes_Vazio/README.md).
- [Arquivo 3](../Evidencias/CT-RF54_Relatorio_Clientes_Vazio/relatorio_3_vazio.pdf), [Formulário em 0:23](../Evidencias/CT-RF54_Relatorio_Clientes_Vazio/formulario_clientes_00-23.png), [Lista de rede](../Evidencias/CT-RF54_Relatorio_Clientes_Vazio/rede_lista.png).
- [Linha do tempo](../Evidencias/CT-RF54_Relatorio_Clientes_Vazio/linha_do_tempo.txt).

Foram consultados os painéis Info, Console e Network do Jam, os quadros do vídeo e os arquivos baixados (tamanhos, hashes e carimbos de hora). A atividade do usuário não foi registrada no Console do Jam. As capturas foram extraídas da reprodução do Jam. O conteúdo da resposta das requisições não foi capturado. Não houve nova execução, inspeção do código, acesso ao banco ou correção da aplicação. O vídeo permanece no Jam.

Análise documental da gravação consultada em 15/11/2026. Esta inclusão não executa novamente o sistema e não constitui reteste. Versão da aplicação, zoom e classificação do ambiente não foram confirmados.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf58) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
