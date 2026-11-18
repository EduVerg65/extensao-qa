# Evidência — CT-RF112: Buscar modelo de ficha por título inexistente

- **Fonte:** [Jam original](https://jam.dev/c/0c385452-2aeb-427f-8159-79549fe7371d).
- **Autor exibido:** Pedro Figueiredo.
- **Gravação:** 16/11/2026, 22:24:36 BRT, com duração de 10,30 s.
- **Revisão:** 17/11/2026.
- **Caso:** [CT-RF112](../../Cenario_Teste/CT-RF112_Busca_Modelo_Ficha_Titulo_Inexistente.md).
- **Defeito:** nenhum confirmado. Ponto a validar.
- **Ambiente:** https://sifit.centrion.com.br/fichas-treino-modelo · Chrome 157.0.8103.79, Windows 10 (x86), vídeo de 1918 × 998.

## Resultado e origem

O título PEDRO-01 foi preenchido e a busca acionada. A tela apresentou carregamento e depois “Nenhum modelo de ficha encontrado”, com 0 registros. O GET capturado retornou HTTP 200 com `[]`.

**Status:** A validar — regra ou contexto pendente.

## Arquivos

| Arquivo | Conteúdo | SHA-256 |
| --- | --- | --- |
| [titulo_sem_resultados_00-09.jpg](titulo_sem_resultados_00-09.jpg) | Título PEDRO-01 e mensagem de estado vazio após Buscar. | `cd7a9c416ee7e87bd80840533afa97983623d4bd53012e24dc1cd563583bb8a3` |
| [linha_do_tempo.txt](linha_do_tempo.txt) | Cronologia de ações, rede e quadros consultados no Jam. | — |
| [origem.url](origem.url) | Endereço do Jam original. | — |

## Limites

Esta pasta contém a cronologia, a origem e os recortes dos quadros consultados. O vídeo permanece no Jam.

A gravação começa com a listagem vazia. O comportamento com títulos registrados e o tipo de correspondência (exata ou parcial) precisam de confirmação.

A revisão se limita ao material gravado. A execução do sistema para as verificações complementares está prevista no caso de teste.
