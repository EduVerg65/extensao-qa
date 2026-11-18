# 🧪 Cenário 108: Conferir a execução de Risco de Evasão na Central e em Resultados IA

**Caso de teste:** CT-RF108

**Módulo:** Inteligência e Automação / Risco de Evasão

**Status:** Aprovado conforme a gravação.

**Gravação:** 16/11/2026, 21:56:07 BRT. **Revisão documental:** 17/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Refletir a nova execução da automação Risco de Evasão na Central e no resumo de Resultados IA. |
| Requisito | [RF108](../Analise%20de%20requisitos.md#rf108) — referência de QA. |
| Tipo / prioridade | Funcional manual / execução e rastreabilidade · Média, proposta para triagem. |
| Defeito | Nenhum no fluxo avaliado |
| Encaminhamento | Usar como regressão da integração entre telas. Verificar entrega pelo canal em um caso dedicado, com destinatários de teste. |
| Fonte | [Jam — PED-14 — Execução de Risco de Evasão](https://jam.dev/c/efe26a44-458a-4802-bd48-8e23c5ac5fd9) e [evidências locais](../Evidencias/CT-RF123_Central_Resultados_IA_Execucao_Evasao/README.md). |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/inteligencia-automacao |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.79 / Windows 10 (x86), conforme os metadados do Jam. |
| Tela / arquivo de vídeo | Tela 1536 × 799 informada no Jam. Vídeo em 1918 × 998. |
| Duração | 32,12 s |
| Localização | Brasil. |
| Versão / zoom / classificação do ambiente | A confirmar antes de nova execução. |
| Dados | A Central indicava a execução anterior às 00:35 e 3 relatórios enviados no mês. O painel passou a indicar 00:55 e 4 relatórios. |

## Pré-condições

- Sessão autenticada com acesso à Central e a Resultados IA. Automação Risco de Evasão habilitada em ambiente de teste autorizado.
- Identificar a versão e registrar os valores iniciais e as permissões no próximo teste.

## Cenário BDD

```gherkin
Cenário: Conferir a execução de Risco de Evasão na Central e em Resultados IA
  Dado que a automação Risco de Evasão está ativa e a última execução está registrada
  Quando o usuário acionar Executar agora e consultar Resultados IA
  Então a Central deve apresentar a execução mais recente
  E Resultados IA deve incluir a execução no período correspondente
```

## Passos para execução ou reteste

1. Registrar a última execução e os cartões da Central de Automações.
2. Clicar em Executar agora no cartão Risco de Evasão e conferir a atividade recente.
3. Abrir Resultados IA e selecionar Hoje.
4. Comparar a execução na linha do tempo e em Automações mais eficientes com o registro da Central.

Este procedimento orienta a próxima execução. O resultado abaixo se limita ao trecho registrado no Jam.

## Resultado esperado

A Central é atualizada após a execução e o mesmo registro aparece em Resultados IA no filtro que inclui a data da execução.

## Resultado obtido na gravação

O POST da automação retornou HTTP 200. A Central atualizou a última execução de 00:35 para 00:55 e os relatórios enviados no mês de 3 para 4. Em Resultados IA, Hoje mostrou 4 automações e 4 relatórios. A execução mais recente retornada pela API coincide com o horário de 00:55 mostrado na Central.

| Tempo | Registro |
| --- | --- |
| 0:00–0:04 | Executa Risco de Evasão. A Central passa a mostrar 00:55 e 4 relatórios enviados no mês. |
| 0:07–0:12 | Confere o relatório identificado como Risco de Evasão e a atividade recente. |
| 0:17–0:20 | Abre Resultados IA e ativa Hoje. |
| 0:22–0:30 | Confere a linha do tempo e o resumo da automação mais recente. |

**Rede:**

- 0:02,13  POST `/api/automacoes/risco-evasao/executar/1` (HTTP 200). Em seguida, GETs de resultados, resumo e execuções retornaram HTTP 200.
- 0:18,08  GET `/api/inteligencia/resultados/1?periodo=7` (HTTP 200), com quatro execuções.
- 0:20,37  GET com `periodo=hoje` (HTTP 200), com quatro execuções e `executado_em` mais recente às 00:55:14 na resposta.

**Conclusão:** Aprovado conforme a gravação. A hora de 00:55 é a referência exibida pelo SIFIT. O teste valida a exibição do mesmo registro nas duas telas. O recebimento efetivo pelo canal de envio e a regra dos cartões de risco não foram verificados.

## Critérios de aceitação para nova execução

1. A execução manual retorna sucesso e atualiza a atividade recente.
2. Resultados IA inclui a execução no período correto.
3. A automação e o horário de última execução coincidem nas duas telas.

## Próxima ação e verificações complementares

Usar como regressão da integração entre telas. Verificar entrega pelo canal em um caso dedicado, com destinatários de teste.

## Evidências e limites

- [Jam original — PED-14 — Execução de Risco de Evasão](https://jam.dev/c/efe26a44-458a-4802-bd48-8e23c5ac5fd9).
- [Arquivos, origem e limites](../Evidencias/CT-RF123_Central_Resultados_IA_Execucao_Evasao/README.md).
- [Central atualizada com última execução às 00:55](../Evidencias/CT-RF123_Central_Resultados_IA_Execucao_Evasao/central_ultima_execucao_00-04.jpg), [Resultados IA no filtro Hoje e linha do tempo de Risco de Evasão](../Evidencias/CT-RF123_Central_Resultados_IA_Execucao_Evasao/resultados_hoje_00-22.jpg).
- [Linha do tempo](../Evidencias/CT-RF123_Central_Resultados_IA_Execucao_Evasao/linha_do_tempo.txt).

A revisão documental se baseia nos quadros do vídeo e nos eventos capturados pelo Jam. As verificações complementares ficam para uma nova rodada de testes.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf108) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
