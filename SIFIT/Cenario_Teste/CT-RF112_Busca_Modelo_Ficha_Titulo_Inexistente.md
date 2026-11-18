# 🧪 Cenário 112: Buscar modelo de ficha por título inexistente

**Caso de teste:** CT-RF112

**Módulo:** Treinamento / Modelos de Ficha / Busca por título

**Status:** A validar — regra ou contexto pendente.

**Gravação:** 16/11/2026, 22:24:36 BRT. **Revisão documental:** 17/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Exibir zero resultados quando nenhum modelo satisfaz o filtro por título em uma base com registros. |
| Requisito | [RF112](../Analise%20de%20requisitos.md#rf112) — referência de QA. Confirmação de produto pendente. |
| Tipo / prioridade | Funcional manual / busca negativa · Média, proposta para triagem. |
| Defeito | Sem defeito confirmado |
| Encaminhamento | Reexecutar com título existente e inexistente e confirmar o critério de correspondência com o produto. |
| Fonte | [Jam — Modelos de Ficha (PED-28)](https://jam.dev/c/0c385452-2aeb-427f-8159-79549fe7371d) e [evidências locais](../Evidencias/CT-RF112_Busca_Modelo_Ficha_Titulo_Inexistente/README.md). |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/fichas-treino-modelo |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.79 / Windows 10 (x86), conforme os metadados do Jam. |
| Tela / arquivo de vídeo | 1536 × 799 informados no Jam. Vídeo em 1918 × 998. |
| Duração | 10,30 s |
| Localização | Brasil. |
| Versão / zoom / classificação do ambiente | A confirmar antes de nova execução. |
| Dados | Título PEDRO-01, com Código e Criador vazios. A listagem já indicava 0 registros. |

## Pré-condições

- Sessão autenticada e base de controle com títulos conhecidos, incluindo um termo sem correspondência.
- Identificar a versão e preparar a captura da listagem, do formulário ou dos filtros e dos eventos de rede pertinentes.

## Cenário BDD

```gherkin
Cenário: Buscar modelo de ficha por título inexistente
  Dado que há modelos cadastrados e nenhum título corresponde ao termo de teste
  Quando o usuário buscar somente pelo título inexistente
  Então a listagem deve exibir zero resultados e informar que nenhum modelo foi encontrado
  E a indicação de carregamento deve terminar após a resposta
```

## Passos para execução ou reteste

1. Confirmar títulos existentes e preparar um termo sem correspondência na base.
2. Buscar pelo termo somente em Título.
3. Aguardar o fim do carregamento e conferir a mensagem, a contagem e a resposta.
4. Repetir com um título conhecido e conferir a lista obtida.

Este procedimento orienta a próxima execução. O resultado abaixo se limita ao trecho registrado no Jam.

## Resultado esperado

O carregamento termina e a busca pelo título inexistente exibe o estado vazio com 0 registros.

## Resultado obtido na gravação

O título PEDRO-01 foi preenchido e a busca acionada. A tela apresentou carregamento e depois “Nenhum modelo de ficha encontrado”, com 0 registros. O GET capturado retornou HTTP 200 com `[]`.

| Tempo | Registro |
| --- | --- |
| 0:00–0:05 | Parte de 0 registros e preenche Título com PEDRO-01. |
| 0:06–0:07 | Aciona Buscar. O GET retorna HTTP 200 com `[]` e a interface mostra carregamento durante a busca. |
| 0:09 | Tela apresenta a mensagem de estado vazio e 0 registros. |

**Rede:** Em 0:06, GET `/api/fichas-modelo/1` com HTTP 200 e corpo `[]` (2 B), sem parâmetros de filtro visíveis na URL capturada.

**Conclusão:** A validar — regra ou contexto pendente. A gravação começa com a listagem vazia. O comportamento com títulos registrados e o tipo de correspondência (exata ou parcial) precisam de confirmação.

## Critérios de aceitação para nova execução

1. A busca sem correspondência apresenta a mensagem de estado vazio e 0 registros.
2. A indicação de carregamento termina após a resposta.
3. A busca de controle encontra um título existente segundo a regra de correspondência acordada.

## Próxima ação e verificações complementares

Reexecutar com título existente e inexistente e confirmar o critério de correspondência com o produto.

## Evidências e limites

- [Jam original — PED-28](https://jam.dev/c/0c385452-2aeb-427f-8159-79549fe7371d).
- [Arquivos, origem e limites](../Evidencias/CT-RF112_Busca_Modelo_Ficha_Titulo_Inexistente/README.md).
- [Busca por título sem resultados em 0:09](../Evidencias/CT-RF112_Busca_Modelo_Ficha_Titulo_Inexistente/titulo_sem_resultados_00-09.jpg).
- [Linha do tempo](../Evidencias/CT-RF112_Busca_Modelo_Ficha_Titulo_Inexistente/linha_do_tempo.txt).

Foram consultados os metadados, os eventos de rede e de interação e os quadros do vídeo. Os recortes estão na pasta de evidências. O vídeo permanece no Jam.

A revisão documental de 17/11/2026 registra a execução gravada. As verificações complementares ficam para uma nova rodada de testes.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf112) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
