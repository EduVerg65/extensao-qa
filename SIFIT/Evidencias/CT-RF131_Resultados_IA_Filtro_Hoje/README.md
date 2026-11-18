# Evidência — CT-RF131: Filtrar Resultados da Inteligência por Hoje

- **Fonte:** [Jam original](https://jam.dev/c/a83c4c74-0b8e-4242-9612-0202c9063d56).
- **Autor exibido:** Pedro Figueiredo.
- **Gravação:** 16/11/2026, 21:47:54 BRT, com duração de 11,96 s.
- **Revisão:** 17/11/2026.
- **Caso:** [CT-RF131](../../Cenario_Teste/CT-RF131_Resultados_IA_Filtro_Hoje.md).
- **Defeito:** Nenhum no fluxo avaliado.
- **Ambiente:** https://sifit.centrion.com.br/inteligencia/resultados · Chrome 157.0.8103.79 / Windows 10 (x86) · vídeo de 1918 × 998.

## Resultado e origem

Hoje foi selecionado e o GET retornou `periodo: hoje` e `dias: 1`. Aniversariantes mudou de 2 para 0. Automações, relatórios e quantidade de itens na linha do tempo permaneceram em 3, de acordo com a resposta.

**Status:** Aprovado conforme a gravação.

## Arquivos

| Arquivo | Conteúdo | SHA-256 |
| --- | --- | --- |
| [resultados_7_dias_00-03.jpg](resultados_7_dias_00-03.jpg) | Últimos 7 dias com dois aniversariantes. | `5d6a8b17288fb796435c597ac8467eef3789787d639970f167cebc7217f2f80c` |
| [resultados_hoje_00-10.jpg](resultados_hoje_00-10.jpg) | Hoje selecionado e zero aniversariantes. | `7c09c7cdc131717e4db06580845b88d083749a390e41096fb8010ef6d5ab1814` |
| [linha_do_tempo.txt](linha_do_tempo.txt) | Cronologia de ações, rede e quadros consultados no Jam. | — |
| [origem.url](origem.url) | Endereço original do Jam. | — |

## Limites

Esta pasta contém a cronologia e os recortes dos quadros consultados. A gravação integral fica no Jam.

A troca do filtro e o retorno da API foram confirmados. O limite de horário do dia e o fuso usado pelo sistema não foram validados com dados controlados.
