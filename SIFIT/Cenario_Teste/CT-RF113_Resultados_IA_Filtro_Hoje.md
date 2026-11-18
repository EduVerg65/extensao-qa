# 🧪 Cenário 113: Filtrar Resultados da Inteligência por Hoje

**Caso de teste:** CT-RF113

**Módulo:** Inteligência / Resultados IA / Filtros de período

**Status:** Aprovado conforme a gravação.

**Gravação:** 16/11/2026, 21:47:54 BRT. **Revisão documental:** 17/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Selecionar Hoje e refletir o recorte de um dia nos resultados e nos indicadores apresentados. |
| Requisito | [RF113](../Analise%20de%20requisitos.md#rf113) — referência de QA. |
| Tipo / prioridade | Funcional manual / filtragem · Média, proposta para triagem. |
| Defeito | Nenhum no fluxo avaliado |
| Encaminhamento | Usar como regressão e conferir o recorte com eventos antes e depois da virada do dia. |
| Fonte | [Jam — PED-09 — Hoje](https://jam.dev/c/a83c4c74-0b8e-4242-9612-0202c9063d56) e [evidências locais](../Evidencias/CT-RF131_Resultados_IA_Filtro_Hoje/README.md). A comparação com 90 dias está no [CT-RF116](CT-RF116_Resultados_IA_Filtro_90_Dias.md). |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/inteligencia/resultados |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.79 / Windows 10 (x86), conforme os metadados do Jam. |
| Tela / arquivo de vídeo | Tela 1536 × 799 informada no Jam. Vídeo em 1918 × 998. |
| Duração | 11,96 s |
| Localização | Brasil. |
| Versão / zoom / classificação do ambiente | A confirmar antes de nova execução. |
| Dados | Últimos 7 dias exibiu dois aniversariantes. Hoje exibiu zero. Nos dois períodos, havia três automações e três relatórios. |

## Pré-condições

- Sessão autenticada com acesso a Resultados IA e valores de referência para Hoje e Últimos 7 dias.
- Identificar a versão e registrar os valores iniciais e as permissões no próximo teste.

## Cenário BDD

```gherkin
Cenário: Filtrar Resultados da Inteligência por Hoje
  Dado que Resultados IA apresenta a consulta de Últimos 7 dias
  Quando o usuário selecionar Hoje
  Então a tela deve destacar Hoje e consultar o recorte de um dia
  E os cartões e a linha do tempo devem acompanhar o retorno desse período
```

## Passos para execução ou reteste

1. Abrir Resultados IA e registrar o período inicial.
2. Selecionar Hoje e verificar o destaque do controle.
3. Conferir os cartões, a linha do tempo e o período retornado pela API.
4. Comparar os indicadores com os do filtro anterior.

Este procedimento orienta a próxima execução. O resultado abaixo se limita ao trecho registrado no Jam.

## Resultado esperado

Hoje é destacado e a API retorna o período de um dia. A tela reflete os dados desse recorte.

## Resultado obtido na gravação

Hoje foi selecionado e o GET retornou `periodo: hoje` e `dias: 1`. Aniversariantes mudou de 2 para 0. Automações, relatórios e quantidade de itens na linha do tempo permaneceram em 3, de acordo com a resposta.

| Tempo | Registro |
| --- | --- |
| 0:02–0:03 | A página carrega Últimos 7 dias com dois aniversariantes. |
| 0:04–0:05 | Seleciona Hoje e recebe os resultados do recorte. |
| 0:06–0:10 | O cartão Aniversariantes mostra zero. A linha do tempo continua com três itens. |

**Rede:**

- 0:02,05  GET `/api/inteligencia/resultados/1?periodo=7` (HTTP 200), com `dias: 7` e dois aniversariantes.
- 0:04,62  GET com `periodo=hoje` (HTTP 200), com `dias: 1`, zero aniversariantes e três itens na linha do tempo.

**Conclusão:** Aprovado conforme a gravação. A troca do filtro e o retorno da API foram confirmados. O limite de horário do dia e o fuso usado pelo sistema não foram validados com dados controlados.

## Critérios de aceitação para nova execução

1. Hoje fica destacado após a consulta.
2. A API identifica o período de um dia.
3. Os indicadores exibidos correspondem à resposta desse período.

## Próxima ação e verificações complementares

Usar como regressão e conferir o recorte com eventos antes e depois da virada do dia.

## Evidências e limites

- [Jam original — PED-09 — Hoje](https://jam.dev/c/a83c4c74-0b8e-4242-9612-0202c9063d56).
- [Arquivos, origem e limites](../Evidencias/CT-RF131_Resultados_IA_Filtro_Hoje/README.md).
- [Últimos 7 dias com dois aniversariantes](../Evidencias/CT-RF131_Resultados_IA_Filtro_Hoje/resultados_7_dias_00-03.jpg), [Hoje selecionado e zero aniversariantes](../Evidencias/CT-RF131_Resultados_IA_Filtro_Hoje/resultados_hoje_00-10.jpg).
- [Linha do tempo](../Evidencias/CT-RF131_Resultados_IA_Filtro_Hoje/linha_do_tempo.txt).

A revisão documental se baseia nos quadros do vídeo e nos eventos capturados pelo Jam. As verificações complementares ficam para uma nova rodada de testes.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf113) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
