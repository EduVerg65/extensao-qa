# 🧪 Cenário 134: Atualizar a Central de Automações

**Caso de teste:** CT-RF134

**Módulo:** Inteligência e Automação / Central / Atualização

**Status:** Aprovado conforme a gravação.

**Gravação:** 16/11/2026, 21:25:26 BRT. **Revisão documental:** 17/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Reconsultar o resumo, a atividade recente e os cartões ao acionar Atualizar na Central de Automações. |
| Requisito | [RF134](../Analise%20de%20requisitos.md#rf134) — referência de QA. |
| Tipo / prioridade | Funcional manual / atualização de dados · Média, proposta para triagem. |
| Defeito | Nenhum no fluxo avaliado |
| Encaminhamento | Usar como regressão e repetir com uma alteração conhecida na base e com uma resposta de erro controlada. |
| Fonte | [Jam — PED-01 — Atualizar Central de Automações](https://jam.dev/c/efe35b08-8733-434c-a6fa-32c45e248ae1) e [evidências locais](../Evidencias/CT-RF134_Central_Automacoes_Atualizar/README.md). |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/inteligencia-automacao |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.79 / Windows 10 (x86), conforme os metadados do Jam. |
| Tela / arquivo de vídeo | Tela 1920 × 999 informada no Jam. Vídeo em 1918 × 998. |
| Duração | 20,16 s |
| Localização | Brasil. |
| Versão / zoom / classificação do ambiente | A confirmar antes de nova execução. |
| Dados | Uma automação ativa. O resumo apresenta a última execução em 22/10/2026 às 13:36 e a API retorna zero relatórios no mês. |

## Pré-condições

- Sessão autenticada com acesso à Central e pelo menos uma automação disponível. Registrar o estado inicial.
- Identificar a versão e registrar os valores iniciais e as permissões no próximo teste.

## Cenário BDD

```gherkin
Cenário: Atualizar a Central de Automações
  Dado que a Central de Automações está carregada
  Quando o usuário clicar em Atualizar
  Então o sistema deve consultar novamente o resumo, as execuções e a lista de automações
  E a Central deve mostrar os dados retornados e permanecer utilizável
```

## Passos para execução ou reteste

1. Abrir a Central e registrar os totais, o estado dos cartões e a atividade recente.
2. Acionar Atualizar e aguardar a conclusão.
3. Conferir as requisições e os dados apresentados.
4. Repetir a atualização e comparar os resultados quando a base não tiver mudado.

Este procedimento orienta a próxima execução. O resultado abaixo se limita ao trecho registrado no Jam.

## Resultado esperado

A Central reconsulta os três conjuntos de dados com sucesso. Uma base estável mantém os mesmos indicadores e a mesma atividade recente.

## Resultado obtido na gravação

Foram acionadas quatro atualizações. Em cada uma, os GETs de resumo, execuções e automações retornaram HTTP 200. O resumo continuou indicando uma automação ativa e a última execução de 22/10/2026 às 13:36. A última atividade retornada pela API correspondeu a esse horário.

| Tempo | Registro |
| --- | --- |
| 0:00–0:05 | Confere os cartões e o resumo inicial. |
| 0:06–0:09 | Aciona Atualizar três vezes. As consultas terminam com HTTP 200 e os indicadores se mantêm. |
| 0:17–0:19 | Aciona Atualizar novamente e confirma o mesmo estado da Central. |

**Rede:**

- 0:06,05  GET `/api/automacoes/resumo/1`, GET `/api/automacoes/execucoes/1` e GET `/api/automacoes/1` (HTTP 200 nas três consultas).
- 0:07,79, 0:08,99 e 0:17,28–0:17,29  As mesmas consultas foram realizadas novamente com HTTP 200.

**Conclusão:** Aprovado conforme a gravação. A gravação verifica atualização com dados estáveis. A reação a uma mudança da base e o tratamento de falhas de rede não foram exercitados.

## Critérios de aceitação para nova execução

1. Atualizar reconsulta resumo, execuções e automações.
2. Os indicadores e a atividade recente refletem os dados recebidos.
3. Com a base estável, as consultas repetidas mantêm os mesmos valores.

## Próxima ação e verificações complementares

Usar como regressão e repetir com uma alteração conhecida na base e com uma resposta de erro controlada.

## Evidências e limites

- [Jam original — PED-01 — Atualizar Central de Automações](https://jam.dev/c/efe35b08-8733-434c-a6fa-32c45e248ae1).
- [Arquivos, origem e limites](../Evidencias/CT-RF134_Central_Automacoes_Atualizar/README.md).
- [Resumo e cartões antes de acionar Atualizar](../Evidencias/CT-RF134_Central_Automacoes_Atualizar/central_antes_00-03.jpg), [Resumo e cartões depois da última atualização](../Evidencias/CT-RF134_Central_Automacoes_Atualizar/central_apos_atualizar_00-18.jpg).
- [Linha do tempo](../Evidencias/CT-RF134_Central_Automacoes_Atualizar/linha_do_tempo.txt).

A revisão documental se baseia nos quadros do vídeo e nos eventos capturados pelo Jam. As verificações complementares ficam para uma nova rodada de testes.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf134) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
