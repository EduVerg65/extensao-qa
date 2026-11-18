# 🧪 Cenário 105: Executar Risco de Evasão manualmente pela Central

**Caso de teste:** CT-RF105

**Módulo:** Inteligência e Automação / Central / Execução manual

**Status:** Aprovado conforme a gravação.

**Gravação:** 16/11/2026, 21:33:26 BRT. **Revisão documental:** 17/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Executar Risco de Evasão pelo botão Executar agora e conferir o novo resultado na Central. |
| Requisito | [RF105](../Analise%20de%20requisitos.md#rf105) — referência de QA. |
| Tipo / prioridade | Funcional manual / execução e atualização · Média, proposta para triagem. |
| Defeito | Nenhum no fluxo avaliado |
| Encaminhamento | Usar como regressão para execução manual. Validar a entrega pelo canal em um teste dedicado, com destinatários de teste. |
| Fonte | [Jam — PED-04 — Executar Risco de Evasão](https://jam.dev/c/be5418c7-8d87-4b6c-9c64-a9b33b5f7da6) e [evidências locais](../Evidencias/CT-RF137_Central_Risco_Evasao_Executar_Agora/README.md). A consulta em Resultados IA está no [CT-RF108](CT-RF108_Central_Resultados_IA_Execucao_Evasao.md). |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/inteligencia-automacao |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.79 / Windows 10 (x86), conforme os metadados do Jam. |
| Tela / arquivo de vídeo | Tela 1536 × 799 informada no Jam. Vídeo em 1918 × 998. |
| Duração | 30,21 s |
| Localização | Brasil. |
| Versão / zoom / classificação do ambiente | A confirmar antes de nova execução. |
| Dados | O histórico começa com a execução anterior de 22/10. O novo resultado agrega 23 registros, todos em risco médio. |

## Pré-condições

- Sessão autenticada com acesso à Central. Automação Risco de Evasão ativa em ambiente de teste autorizado.
- Identificar a versão e registrar os valores iniciais e as permissões no próximo teste.

## Cenário BDD

```gherkin
Cenário: Executar Risco de Evasão manualmente pela Central
  Dado que Risco de Evasão está ativa na Central
  Quando o usuário clicar em Executar agora
  Então a execução deve terminar com sucesso e carregar o relatório
  E a Central deve atualizar a última execução e a atividade recente
```

## Passos para execução ou reteste

1. Registrar o horário da última execução, o cartão e a atividade recente.
2. Clicar em Executar agora e aguardar a resposta.
3. Conferir o novo relatório, os totais e o registro de execução na Central.
4. Acionar Atualizar e confirmar que a última execução permanece no resumo.

Este procedimento orienta a próxima execução. O resultado abaixo se limita ao trecho registrado no Jam.

## Resultado esperado

O comando executa a automação com sucesso, apresenta o relatório do novo processamento e registra a nova execução na Central.

## Resultado obtido na gravação

O POST retornou HTTP 200 e `verifica_erro: false`. O resumo da execução e o relatório indicaram 23 registros em risco médio e zero em risco alto e baixo. A Central apresentou a nova execução às 00:32 e o resumo continuou mostrando esse horário após Atualizar.

| Tempo | Registro |
| --- | --- |
| 0:00–0:09 | Central mostra a execução anterior. O usuário aciona Executar agora. |
| 0:10–0:12 | Aparecem a nova execução, a atividade recente e o relatório agregado. |
| 0:22–0:24 | Aciona Atualizar e confere que a última execução permanece. |

**Rede:**

- 0:09,51  Clique em Executar agora. O POST `/api/automacoes/risco-evasao/executar/1` retornou HTTP 200, com `verifica_erro: false` e 23 analisados.
- 0:10,12  GET `/api/automacoes/risco-evasao/resultados/1` (HTTP 200), com 23 em risco médio, zero em alto e zero em baixo.
- 0:10,21  GETs de resumo e execuções (HTTP 200), com a nova execução às 00:32 no resumo do SIFIT.
- 0:22,04  Atualizar reconsultou resumo, execuções e automações (HTTP 200). A última execução permaneceu às 00:32.

**Conclusão:** Aprovado conforme a gravação. A aprovação se limita à execução e à exibição do resultado na Central. O horário é a referência exibida no SIFIT. A entrega pelo canal de notificação não foi verificada. Os recortes mostram apenas informações agregadas.

## Critérios de aceitação para nova execução

1. Executar agora retorna sucesso.
2. O novo relatório apresenta o resumo devolvido pela API.
3. A última execução e a atividade recente são atualizadas e permanecem após Atualizar.

## Próxima ação e verificações complementares

Usar como regressão para execução manual. Validar a entrega pelo canal em um teste dedicado, com destinatários de teste.

## Evidências e limites

- [Jam — PED-04 — Executar Risco de Evasão](https://jam.dev/c/be5418c7-8d87-4b6c-9c64-a9b33b5f7da6).
- [Arquivos, origem e limites](../Evidencias/CT-RF137_Central_Risco_Evasao_Executar_Agora/README.md).
- [Resumo da Central antes da execução manual](../Evidencias/CT-RF137_Central_Risco_Evasao_Executar_Agora/central_antes_executar_00-08.jpg), [Resumo e atividade recente depois da execução e da atualização](../Evidencias/CT-RF137_Central_Risco_Evasao_Executar_Agora/central_apos_executar_00-23.jpg).
- [Linha do tempo](../Evidencias/CT-RF137_Central_Risco_Evasao_Executar_Agora/linha_do_tempo.txt).

A revisão documental se baseia nos quadros do vídeo e nos eventos capturados pelo Jam. As verificações complementares ficam para uma nova rodada de testes.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf105) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
