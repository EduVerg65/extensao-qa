# 🧪 Cenário 114: Filtrar Resultados da Inteligência pelos últimos 7 dias

**Caso de teste:** CT-RF114

**Módulo:** Inteligência / Resultados IA / Filtros de período

**Status:** Aprovado conforme a gravação.

**Gravação:** 16/11/2026, 21:48:38 BRT. **Revisão documental:** 17/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Voltar de Hoje a Últimos 7 dias e atualizar o resumo com o recorte semanal. |
| Requisito | [RF114](../Analise%20de%20requisitos.md#rf114) — referência de QA. |
| Tipo / prioridade | Funcional manual / filtragem · Média, proposta para triagem. |
| Defeito | Nenhum no fluxo avaliado |
| Encaminhamento | Usar como regressão e preparar dados nos dias de fronteira para verificar inclusão e exclusão. |
| Fonte | [Jam — PED-10 — Últimos 7 dias](https://jam.dev/c/cbf45b87-b7b6-4314-a359-c5e706aa755e) e [evidências locais](../Evidencias/CT-RF132_Resultados_IA_Filtro_7_Dias/README.md). A comparação com 90 dias está no [CT-RF116](CT-RF116_Resultados_IA_Filtro_90_Dias.md). |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/inteligencia/resultados |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.79 / Windows 10 (x86), conforme os metadados do Jam. |
| Tela / arquivo de vídeo | Tela 1536 × 799 informada no Jam. Vídeo em 1918 × 998. |
| Duração | 14,38 s |
| Localização | Brasil. |
| Versão / zoom / classificação do ambiente | A confirmar antes de nova execução. |
| Dados | Hoje retornou zero aniversariantes e o recorte semanal retornou dois. Nos dois períodos, foram retornadas três automações e três relatórios. |

## Pré-condições

- Sessão autenticada com acesso a Resultados IA e dados distintos entre Hoje e Últimos 7 dias.
- Identificar a versão e registrar os valores iniciais e as permissões no próximo teste.

## Cenário BDD

```gherkin
Cenário: Filtrar Resultados da Inteligência pelos últimos 7 dias
  Dado que Resultados IA está no filtro Hoje
  Quando o usuário selecionar Últimos 7 dias
  Então a API deve retornar a consulta de sete dias e o controle deve ficar destacado
  E a página deve refletir os dados desse período
```

## Passos para execução ou reteste

1. Abrir Resultados IA e consultar Hoje.
2. Registrar os indicadores, especialmente o cartão Aniversariantes.
3. Clicar em Últimos 7 dias e conferir o parâmetro de rede e a resposta.
4. Comparar os cartões e a cronologia com a resposta de sete dias.

Este procedimento orienta a próxima execução. O resultado abaixo se limita ao trecho registrado no Jam.

## Resultado esperado

Últimos 7 dias fica selecionado, a API retorna sete dias e a página exibe o conjunto correspondente.

## Resultado obtido na gravação

A consulta de Hoje retornou zero aniversariantes. Após selecionar Últimos 7 dias, o GET com `periodo=7` retornou `dias: 7` e dois aniversariantes, exibidos na interface. Automações, relatórios e quantidade de itens da cronologia continuaram em 3.

| Tempo | Registro |
| --- | --- |
| 0:05–0:06 | Após recarregar, recebe a consulta padrão de 7 dias. |
| 0:06–0:08 | Seleciona Hoje e confere zero aniversariantes. |
| 0:08–0:12 | Volta a Últimos 7 dias. O cartão passa a mostrar dois. |

**Rede:**

- 0:05,37  GET `/api/inteligencia/resultados/1?periodo=7` (HTTP 200) na recarga inicial.
- 0:06,95  GET com `periodo=hoje` (HTTP 200), com zero aniversariantes.
- 0:08,37  Novo GET com `periodo=7` (HTTP 200), com `dias: 7`, dois aniversariantes e três itens na linha do tempo.

**Conclusão:** Aprovado conforme a gravação. Foi confirmada a mudança de recorte na interface e na API. A fronteira dos sete dias e a data de cada item não foram validadas com uma base controlada.

## Critérios de aceitação para nova execução

1. Últimos 7 dias fica destacado após a seleção.
2. O GET identifica `periodo=7` e retorna `dias: 7`.
3. A interface reflete os indicadores e a cronologia do recorte retornado.

## Próxima ação e verificações complementares

Usar como regressão e preparar dados nos dias de fronteira para verificar inclusão e exclusão.

## Evidências e limites

- [Jam original — PED-10 — Últimos 7 dias](https://jam.dev/c/cbf45b87-b7b6-4314-a359-c5e706aa755e).
- [Arquivos, origem e limites](../Evidencias/CT-RF132_Resultados_IA_Filtro_7_Dias/README.md).
- [Hoje selecionado com zero aniversariantes](../Evidencias/CT-RF132_Resultados_IA_Filtro_7_Dias/resultados_hoje_00-07.jpg), [Últimos 7 dias selecionado com dois aniversariantes](../Evidencias/CT-RF132_Resultados_IA_Filtro_7_Dias/resultados_7_dias_00-12.jpg).
- [Linha do tempo](../Evidencias/CT-RF132_Resultados_IA_Filtro_7_Dias/linha_do_tempo.txt).

A revisão documental se baseia nos quadros do vídeo e nos eventos capturados pelo Jam. As verificações complementares ficam para uma nova rodada de testes.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf114) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
