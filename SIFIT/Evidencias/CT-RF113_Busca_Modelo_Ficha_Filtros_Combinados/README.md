# Evidência — CT-RF113: Buscar modelos de ficha com filtros combinados

- **Fonte:** [Jam original](https://jam.dev/c/006f9722-e643-4b65-904a-25471a7b90ed).
- **Autor exibido:** Pedro Figueiredo.
- **Gravação:** 16/11/2026, 22:27:13 BRT, com duração de 15,22 s.
- **Revisão:** 17/11/2026.
- **Caso:** [CT-RF113](../../Cenario_Teste/CT-RF113_Busca_Modelo_Ficha_Filtros_Combinados.md).
- **Defeito:** nenhum confirmado. Ponto a validar.
- **Ambiente:** https://sifit.centrion.com.br/fichas-treino-modelo · Chrome 157.0.8103.79, Windows 10 (x86), vídeo de 1918 × 998.

## Resultado e origem

Os três filtros foram preenchidos e a busca manteve “Nenhum modelo de ficha encontrado” com 0 registros. O GET retornou HTTP 200 com `[]` e a URL registrada não continha os valores digitados.

**Status:** A validar — regra ou contexto pendente.

## Arquivos

| Arquivo | Conteúdo | SHA-256 |
| --- | --- | --- |
| [filtros_combinados_sem_resultados_00-13.jpg](filtros_combinados_sem_resultados_00-13.jpg) | Três filtros preenchidos e resultado vazio após Buscar. | `092311ba25143d4c7e4169623a31de8c8a44cba65be3f1586b0637ab6c7600d4` |
| [linha_do_tempo.txt](linha_do_tempo.txt) | Cronologia de ações, rede e quadros consultados no Jam. | — |
| [origem.url](origem.url) | Endereço do Jam original. | — |

## Limites

Esta pasta contém a cronologia, a origem e os recortes dos quadros consultados. O vídeo permanece no Jam.

A resposta vazia e a ausência de parâmetros na URL não permitem distinguir filtragem local de critérios ignorados. Confirmar a lógica de combinação com o produto e usar dados que diferenciem os resultados.

A revisão se limita ao material gravado. A execução do sistema para as verificações complementares está prevista no caso de teste.
