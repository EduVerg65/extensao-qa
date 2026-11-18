# 🧪 Cenário 106: Abrir os resultados de Risco de Evasão pela Central

**Caso de teste:** CT-RF106

**Módulo:** Inteligência e Automação / Central / Resultados de risco

**Status:** Aprovado conforme a gravação.

**Gravação:** 16/11/2026, 21:38:29 BRT. **Revisão documental:** 17/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Consultar o relatório existente de Risco de Evasão pela ação Ver resultados e conferir o total e a distribuição por nível. |
| Requisito | [RF106](../Analise%20de%20requisitos.md#rf106) — referência de QA. |
| Tipo / prioridade | Funcional manual / consulta de relatório · Média, proposta para triagem. |
| Defeito | Nenhum no fluxo avaliado |
| Encaminhamento | Usar como regressão da consulta e retestar cada filtro com uma base de teste com níveis distintos. |
| Fonte | [Jam — PED-05 — Ver resultados de Risco de Evasão](https://jam.dev/c/ac5bce26-f4a8-401b-bb23-d09d5253751a) e [evidências locais](../Evidencias/CT-RF138_Central_Abrir_Resultados_Risco_Evasao/README.md). A consulta em Resultados IA está no [CT-RF108](CT-RF108_Central_Resultados_IA_Execucao_Evasao.md). |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/inteligencia-automacao |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.79 / Windows 10 (x86), conforme os metadados do Jam. |
| Tela / arquivo de vídeo | Tela 1536 × 799 informada no Jam. Vídeo em 1918 × 998. |
| Duração | 18,86 s |
| Localização | Brasil. |
| Versão / zoom / classificação do ambiente | A confirmar antes de nova execução. |
| Dados | Relatório existente com total 23: zero alto, 23 médio e zero baixo. |

## Pré-condições

- Sessão autenticada com acesso à Central e uma execução de Risco de Evasão já registrada.
- Identificar a versão e registrar os valores iniciais e as permissões no próximo teste.

## Cenário BDD

```gherkin
Cenário: Abrir os resultados de Risco de Evasão pela Central
  Dado que a Central apresenta uma execução anterior de Risco de Evasão
  Quando o usuário clicar em Ver resultados
  Então o relatório deve abrir com os totais e a distribuição do resultado existente
  E a interface deve disponibilizar os controles de filtro por nível
```

## Passos para execução ou reteste

1. Localizar o cartão Risco de Evasão que possui um resultado anterior.
2. Clicar em Ver resultados e aguardar a consulta.
3. Conferir o título, os cartões de risco e os controles de filtro.
4. Comparar os totais exibidos com o resumo da API.

Este procedimento orienta a próxima execução. O resultado abaixo se limita ao trecho registrado no Jam.

## Resultado esperado

Ver resultados abre o relatório existente com o total de registros e a distribuição por nível, de acordo com a consulta.

## Resultado obtido na gravação

Ver resultados abriu o Relatório de Risco de Evasão. A API retornou HTTP 200 e total 23, com todos os registros em risco médio. O painel mostrou os mesmos valores e os controles Todos, Alto, Médio e Baixo.

| Tempo | Registro |
| --- | --- |
| 0:00–0:07 | Cartão Risco de Evasão exibe Ver resultados. O usuário aciona a consulta. |
| 0:08–0:12 | O relatório abre, com 23 registros e totais 0, 23 e 0 por nível. |
| 0:13–0:18 | O painel permanece aberto para consulta. |

**Rede:**

- 0:07,18  GET `/api/automacoes/risco-evasao/resultados/1` (HTTP 200). Resumo com total 23, alto 0, médio 23 e baixo 0.

**Conclusão:** Aprovado conforme a gravação. A evidência cobre a abertura e os totais. O funcionamento dos filtros de nível não foi verificado. A documentação usa apenas totais agregados e o recorte do cabeçalho do relatório.

## Critérios de aceitação para nova execução

1. Ver resultados abre o relatório da execução existente.
2. O total geral e os totais por nível coincidem com a resposta.
3. Os filtros de nível aparecem no relatório.

## Próxima ação e verificações complementares

Usar como regressão da consulta e retestar cada filtro com uma base de teste com níveis distintos.

## Evidências e limites

- [Jam — PED-05 — Ver resultados de Risco de Evasão](https://jam.dev/c/ac5bce26-f4a8-401b-bb23-d09d5253751a).
- [Arquivos, origem e limites](../Evidencias/CT-RF138_Central_Abrir_Resultados_Risco_Evasao/README.md).
- [Cartão Risco de Evasão com a ação Ver resultados](../Evidencias/CT-RF138_Central_Abrir_Resultados_Risco_Evasao/botao_ver_resultados_00-06.jpg), [Resumo de risco com os totais e os controles de filtro](../Evidencias/CT-RF138_Central_Abrir_Resultados_Risco_Evasao/resumo_risco_00-12.jpg).
- [Linha do tempo](../Evidencias/CT-RF138_Central_Abrir_Resultados_Risco_Evasao/linha_do_tempo.txt).

A revisão documental se baseia nos quadros do vídeo e nos eventos capturados pelo Jam. As verificações complementares ficam para uma nova rodada de testes.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf106) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
