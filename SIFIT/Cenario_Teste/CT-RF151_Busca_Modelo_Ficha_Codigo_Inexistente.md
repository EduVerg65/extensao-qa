# 🧪 Cenário 151: Buscar modelo de ficha por código inexistente

**Caso de teste:** CT-RF151

**Módulo:** Configurações / Modelo Ficha / Busca por código

**Status:** A validar — regra ou contexto pendente.

**Gravação:** 16/11/2026, 22:23:48 BRT. **Revisão documental:** 17/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Exibir zero resultados e uma mensagem clara ao buscar por um código ausente em uma base com modelos cadastrados. |
| Requisito | [RF151](../Analise%20de%20requisitos.md#rf151) — referência de QA. Confirmação de produto pendente. |
| Tipo / prioridade | Funcional manual / busca negativa · Média, proposta para triagem. |
| Defeito | Sem defeito confirmado |
| Encaminhamento | Reexecutar com um código existente e um comprovadamente ausente na mesma base. |
| Fonte | [Jam — Modelos de Ficha (PED-27)](https://jam.dev/c/c1aecaa8-39c7-49b0-89af-9de47a68ba40) e [evidências locais](../Evidencias/CT-RF111_Busca_Modelo_Ficha_Codigo_Inexistente/README.md). |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/fichas-treino-modelo |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.79 / Windows 10 (x86), conforme os metadados do Jam. |
| Tela / arquivo de vídeo | 1536 × 799 informados no Jam. Vídeo em 1918 × 998. |
| Duração | 10,07 s |
| Localização | Brasil. |
| Versão / zoom / classificação do ambiente | A confirmar antes de nova execução. |
| Dados | Código 989898. Título e Criador vazios. A interface já mostrava 0 registros antes da busca. |

## Pré-condições

- Sessão autenticada e base de controle com pelo menos um modelo de código conhecido e um código comprovadamente ausente.
- Identificar a versão e preparar a captura da listagem, do formulário ou dos filtros e dos eventos de rede pertinentes.

## Cenário BDD

```gherkin
Cenário: Buscar modelo de ficha por código inexistente
  Dado que há modelos cadastrados e o código consultado não pertence a nenhum deles
  Quando o usuário buscar somente por esse código
  Então a listagem deve exibir zero resultados e informar que nenhum modelo foi encontrado
  E nenhum modelo com outro código deve ser exibido
```

## Passos para execução ou reteste

1. Confirmar um código existente e um código ausente nos dados de controle.
2. Buscar pelo código ausente, com Título e Criador vazios.
3. Conferir a mensagem, a contagem e o retorno registrado.
4. Repetir com o código existente para confirmar o funcionamento do filtro.

Este procedimento orienta a próxima execução. O resultado abaixo se limita ao trecho registrado no Jam.

## Resultado esperado

A pesquisa pelo código ausente exibe a mensagem de lista vazia e 0 registros, mesmo com outros modelos disponíveis.

## Resultado obtido na gravação

A tela já mostrava 0 registros antes da digitação. Após buscar por 989898, exibiu “Nenhum modelo de ficha encontrado” e 0 registros. A consulta capturada retornou HTTP 200 com `[]`.

| Tempo | Registro |
| --- | --- |
| 0:00–0:05 | Parte de 0 registros e preenche Código com 989898. |
| 0:06 | Aciona a busca. GET retorna HTTP 200 com `[]`. |
| 0:09 | Tela apresenta a mensagem de estado vazio e 0 registros. |

**Rede:** Em 0:06, GET `/api/fichas-modelo/1` com HTTP 200 e corpo `[]` (2 B). A URL capturada não contém parâmetros de filtro.

**Conclusão:** A validar — regra ou contexto pendente. O estado vazio foi observado. A base de controle e a busca positiva não aparecem na gravação, por isso a eficácia do filtro por código permanece a validar.

## Critérios de aceitação para nova execução

1. A busca pelo código ausente mostra a mensagem de estado vazio e 0 registros.
2. Registros com outro código ficam fora do resultado.
3. A busca de controle com código existente identifica o modelo correspondente.

## Próxima ação e verificações complementares

Reexecutar com um código existente e um comprovadamente ausente na mesma base.

## Evidências e limites

- [Jam original — PED-27](https://jam.dev/c/c1aecaa8-39c7-49b0-89af-9de47a68ba40).
- [Arquivos, origem e limites](../Evidencias/CT-RF111_Busca_Modelo_Ficha_Codigo_Inexistente/README.md).
- [Busca por código sem resultados em 0:09](../Evidencias/CT-RF111_Busca_Modelo_Ficha_Codigo_Inexistente/codigo_sem_resultados_00-09.jpg).
- [Linha do tempo](../Evidencias/CT-RF111_Busca_Modelo_Ficha_Codigo_Inexistente/linha_do_tempo.txt).

Foram consultados os metadados, os eventos de rede e de interação e os quadros do vídeo. Os recortes estão na pasta de evidências. O vídeo permanece no Jam.

A revisão documental de 17/11/2026 registra a execução gravada. As verificações complementares ficam para uma nova rodada de testes.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf151) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
