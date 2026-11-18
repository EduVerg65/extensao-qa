# 🧪 Cenário 122: Filtrar Resultados da Inteligência pelos últimos 90 dias

**Caso de teste:** CT-RF122

**Módulo:** Inteligência / Resultados IA / Filtros de período

**Status:** Aprovado conforme a gravação.

**Gravação:** 16/11/2026, 21:50:51 BRT. **Revisão documental:** 17/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Atualizar os cartões e a linha do tempo quando o usuário seleciona Últimos 90 dias em Resultados da Inteligência. |
| Requisito | [RF122](../Analise%20de%20requisitos.md#rf122) — referência de QA. |
| Tipo / prioridade | Funcional manual / filtragem · Média, proposta para triagem. |
| Defeito | Nenhum no fluxo avaliado |
| Encaminhamento | Usar como regressão e criar dados nas datas-limite dos períodos para conferir a inclusão e a exclusão. |
| Fonte | [Jam — PED-12 — Últimos 90 dias](https://jam.dev/c/1728cfc2-1d36-4ea4-ab68-68a84458c359) e [evidências locais](../Evidencias/CT-RF122_Resultados_IA_Filtro_90_Dias/README.md). |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/inteligencia/resultados |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.79 / Windows 10 (x86), conforme os metadados do Jam. |
| Tela / arquivo de vídeo | Tela 1536 × 799 informada no Jam. Vídeo em 1918 × 998. |
| Duração | 23,32 s |
| Localização | Brasil. |
| Versão / zoom / classificação do ambiente | A confirmar antes de nova execução. |
| Dados | Períodos com 3, 12 e 20 automações executadas para 7, 30 e 90 dias, respectivamente. |

## Pré-condições

- Sessão autenticada com acesso a Resultados IA e automações registradas em datas que diferenciem os períodos de 7, 30 e 90 dias.
- Identificar a versão e registrar os valores iniciais e as permissões no próximo teste.

## Cenário BDD

```gherkin
Cenário: Filtrar Resultados da Inteligência pelos últimos 90 dias
  Dado que Resultados da Inteligência tem dados de períodos diferentes
  Quando o usuário selecionar Últimos 90 dias
  Então o sistema deve indicar o período ativo e carregar os respectivos resultados
  E os cartões e a linha do tempo devem refletir os dados retornados para esse período
```

## Passos para execução ou reteste

1. Abrir Resultados IA e registrar os cartões e a linha do tempo no filtro de 7 dias.
2. Selecionar Últimos 90 dias e conferir o período ativo, os cartões e a resposta da API.
3. Selecionar Últimos 30 dias e comparar os resultados.
4. Voltar a Últimos 90 dias e verificar a repetição dos resultados no mesmo conjunto de dados.

Este procedimento orienta a próxima execução. O resultado abaixo se limita ao trecho registrado no Jam.

## Resultado esperado

O filtro selecionado é destacado. Cartões e linha do tempo acompanham o período consultado, e voltar aos 90 dias restaura os resultados desse período.

## Resultado obtido na gravação

A seleção de 90 dias exibiu 20 automações executadas, 20 relatórios enviados e 31 aniversariantes. No filtro de 30 dias, os cartões mostraram 12, 12 e 6. Ao voltar para 90 dias, os totais foram repetidos. A API retornou 15 itens na linha do tempo para 90 dias, 12 para 30 e 3 para 7.

| Tempo | Registro |
| --- | --- |
| 0:05–0:06 | Recarrega a página. Últimos 7 dias exibe 3 automações e 3 relatórios. |
| 0:07–0:10 | Seleciona Últimos 90 dias. Os dois cartões passam a 20. |
| 0:17–0:19 | Alterna para 30 dias e volta a 90 dias. Os totais passam de 12 para 20. |

**Rede:**

- 0:05,22  GET `/api/inteligencia/resultados/1?periodo=7` (HTTP 200). Linha do tempo com 3 itens.
- 0:07,74  GET com `periodo=90` (HTTP 200). 20 automações, 20 relatórios e 15 itens de linha do tempo.
- 0:17,94  GET com `periodo=30` (HTTP 200). 12 automações, 12 relatórios e 12 itens de linha do tempo.
- 0:19,21  Novo GET com `periodo=90` (HTTP 200), com os mesmos totais da primeira consulta de 90 dias.

**Conclusão:** Aprovado conforme a gravação. A aprovação cobre a troca de filtros e a correspondência entre interface e resposta da API. O recorte nas datas-limite e a regra de cartões que permaneceram constantes não foram conferidos com uma base controlada.

## Critérios de aceitação para nova execução

1. O filtro de 90 dias permanece destacado após carregar.
2. Os cartões e a linha do tempo correspondem à resposta para o período selecionado.
3. Alternar entre 30 e 90 dias atualiza os resultados e reaplicar o mesmo filtro reproduz o resultado da base estável.

## Próxima ação e verificações complementares

Usar como regressão e criar dados nas datas-limite dos períodos para conferir a inclusão e a exclusão.

## Evidências e limites

- [Jam original — PED-12 — Últimos 90 dias](https://jam.dev/c/1728cfc2-1d36-4ea4-ab68-68a84458c359).
- [Arquivos, origem e limites](../Evidencias/CT-RF122_Resultados_IA_Filtro_90_Dias/README.md).
- [Últimos 7 dias com três automações e três relatórios](../Evidencias/CT-RF122_Resultados_IA_Filtro_90_Dias/resultados_7_dias_00-06.jpg), [Últimos 90 dias com 20 automações e 20 relatórios](../Evidencias/CT-RF122_Resultados_IA_Filtro_90_Dias/resultados_90_dias_00-10.jpg).
- [Linha do tempo](../Evidencias/CT-RF122_Resultados_IA_Filtro_90_Dias/linha_do_tempo.txt).

A revisão documental se baseia nos quadros do vídeo e nos eventos capturados pelo Jam. As verificações complementares ficam para uma nova rodada de testes.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf122) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
