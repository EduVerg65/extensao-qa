# Evidência — CT-RF111: Buscar modelo de ficha por código inexistente

- **Fonte:** [Jam original](https://jam.dev/c/c1aecaa8-39c7-49b0-89af-9de47a68ba40).
- **Autor exibido:** Pedro Figueiredo.
- **Gravação:** 16/11/2026, 22:23:48 BRT, com duração de 10,07 s.
- **Revisão:** 17/11/2026.
- **Caso:** [CT-RF111](../../Cenario_Teste/CT-RF111_Busca_Modelo_Ficha_Codigo_Inexistente.md).
- **Defeito:** nenhum confirmado. Ponto a validar.
- **Ambiente:** https://sifit.centrion.com.br/fichas-treino-modelo · Chrome 157.0.8103.79, Windows 10 (x86), vídeo de 1918 × 998.

## Resultado e origem

A tela já mostrava 0 registros antes da digitação. Após buscar por 989898, exibiu “Nenhum modelo de ficha encontrado” e 0 registros. A consulta capturada retornou HTTP 200 com `[]`.

**Status:** A validar — regra ou contexto pendente.

## Arquivos

| Arquivo | Conteúdo | SHA-256 |
| --- | --- | --- |
| [codigo_sem_resultados_00-09.jpg](codigo_sem_resultados_00-09.jpg) | Código 989898 e mensagem de estado vazio após Buscar. | `d6fcc27d071667530e50e7056fba14dbf261f740132c48526ef6ba987ff7f3ed` |
| [linha_do_tempo.txt](linha_do_tempo.txt) | Cronologia de ações, rede e quadros consultados no Jam. | — |
| [origem.url](origem.url) | Endereço do Jam original. | — |

## Limites

Esta pasta contém a cronologia, a origem e os recortes dos quadros consultados. O vídeo permanece no Jam.

O estado vazio foi observado. A base de controle e a busca positiva não aparecem na gravação, por isso a eficácia do filtro por código permanece a validar.

A revisão se limita ao material gravado. A execução do sistema para as verificações complementares está prevista no caso de teste.
