# 🧪 Cenário 153: Buscar modelos de ficha com filtros combinados

**Caso de teste:** CT-RF153

**Módulo:** Configurações / Modelo Ficha / Filtros combinados

**Status:** A validar — regra ou contexto pendente.

**Gravação:** 16/11/2026, 22:27:13 BRT. **Revisão documental:** 17/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Verificar a aplicação conjunta dos filtros Código, Título e Criador em uma busca com resultados de controle. |
| Requisito | [RF153](../Analise%20de%20requisitos.md#rf153) — referência de QA. Confirmação de produto pendente. |
| Tipo / prioridade | Funcional manual / combinação de filtros · Média, proposta para triagem. |
| Defeito | Sem defeito confirmado |
| Encaminhamento | Reexecutar com registros que correspondam a todos os filtros e a apenas parte deles. Confirmar onde a filtragem é feita. |
| Fonte | [Jam — Modelos de Ficha (PED-29)](https://jam.dev/c/006f9722-e643-4b65-904a-25471a7b90ed) e [evidências locais](../Evidencias/CT-RF113_Busca_Modelo_Ficha_Filtros_Combinados/README.md). |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/fichas-treino-modelo |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.79 / Windows 10 (x86), conforme os metadados do Jam. |
| Tela / arquivo de vídeo | 1536 × 799 informados no Jam. Vídeo em 1918 × 998. |
| Duração | 15,22 s |
| Localização | Brasil. |
| Versão / zoom / classificação do ambiente | A confirmar antes de nova execução. |
| Dados | Código 989898, Título PEDRO-01 e Criador PEDRO-01. Listagem inicialmente vazia. |

## Pré-condições

- Sessão autenticada e modelos de controle que satisfaçam todos os critérios ou apenas parte deles.
- Identificar a versão e preparar a captura da listagem, do formulário ou dos filtros e dos eventos de rede pertinentes.

## Cenário BDD

```gherkin
Cenário: Buscar modelos de ficha com filtros combinados
  Dado que existem modelos que atendem aos três filtros e modelos que atendem apenas a parte deles
  Quando o usuário buscar com Código, Título e Criador preenchidos
  Então a listagem deve exibir somente modelos que atendam aos três critérios
  E o sistema deve mostrar 0 registros quando a combinação não tiver correspondência
```

## Passos para execução ou reteste

1. Preparar um modelo que corresponda aos três filtros e outros que correspondam a apenas parte deles.
2. Aplicar os três filtros em uma combinação que deve retornar o modelo de controle.
3. Alterar um critério para uma combinação sem correspondência e buscar novamente.
4. Comparar linhas e contagem com os controles e registrar a resposta de rede.

Este procedimento orienta a próxima execução. O resultado abaixo se limita ao trecho registrado no Jam.

## Resultado esperado

Como critério de QA, a pesquisa lista a interseção dos três filtros. Uma combinação sem correspondência mostra a mensagem de estado vazio com 0 registros.

## Resultado obtido na gravação

Os três filtros foram preenchidos e a busca manteve “Nenhum modelo de ficha encontrado” com 0 registros. O GET retornou HTTP 200 com `[]` e a URL registrada não continha os valores digitados.

| Tempo | Registro |
| --- | --- |
| 0:00–0:09 | Preenche Código com 989898 e Título e Criador com PEDRO-01. |
| 0:11 | Aciona Buscar. GET retorna HTTP 200 com `[]`. |
| 0:13 | A tela mantém os três valores exibidos e 0 registros. |

**Rede:** Em 0:11, GET `/api/fichas-modelo/1` com HTTP 200 e corpo `[]` (2 B). O evento não mostra os filtros na URL.

**Conclusão:** A validar — regra ou contexto pendente. A resposta vazia e a ausência de parâmetros na URL não permitem distinguir filtragem local de critérios ignorados. Confirmar a lógica de combinação com o produto e usar dados que diferenciem os resultados.

## Critérios de aceitação para nova execução

1. A busca com os três filtros é acionada e mantém os critérios informados.
2. Com a regra de interseção confirmada, somente o modelo compatível com os três critérios é listado.
3. Alterar um critério para uma combinação impossível exibe 0 registros e a mensagem de estado vazio.

## Próxima ação e verificações complementares

Reexecutar com registros que correspondam a todos os filtros e a apenas parte deles. Confirmar onde a filtragem é feita.

## Evidências e limites

- [Jam original — PED-29](https://jam.dev/c/006f9722-e643-4b65-904a-25471a7b90ed).
- [Arquivos, origem e limites](../Evidencias/CT-RF113_Busca_Modelo_Ficha_Filtros_Combinados/README.md).
- [Filtros combinados sem resultados em 0:13](../Evidencias/CT-RF113_Busca_Modelo_Ficha_Filtros_Combinados/filtros_combinados_sem_resultados_00-13.jpg).
- [Linha do tempo](../Evidencias/CT-RF113_Busca_Modelo_Ficha_Filtros_Combinados/linha_do_tempo.txt).

Foram consultados os metadados, os eventos de rede e de interação e os quadros do vídeo. Os recortes estão na pasta de evidências. O vídeo permanece no Jam.

A revisão documental de 17/11/2026 registra a execução gravada. As verificações complementares ficam para uma nova rodada de testes.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf153) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
