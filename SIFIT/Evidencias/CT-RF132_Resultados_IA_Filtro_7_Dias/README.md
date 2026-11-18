# Evidência — CT-RF132: Filtrar Resultados da Inteligência pelos últimos 7 dias

- **Fonte:** [Jam original](https://jam.dev/c/cbf45b87-b7b6-4314-a359-c5e706aa755e).
- **Autor exibido:** Pedro Figueiredo.
- **Gravação:** 16/11/2026, 21:48:38 BRT, com duração de 14,38 s.
- **Revisão:** 17/11/2026.
- **Caso:** [CT-RF132](../../Cenario_Teste/CT-RF132_Resultados_IA_Filtro_7_Dias.md).
- **Defeito:** Nenhum no fluxo avaliado.
- **Ambiente:** https://sifit.centrion.com.br/inteligencia/resultados · Chrome 157.0.8103.79 / Windows 10 (x86) · vídeo de 1918 × 998.

## Resultado e origem

A consulta de Hoje retornou zero aniversariantes. Após selecionar Últimos 7 dias, o GET com `periodo=7` retornou `dias: 7` e dois aniversariantes, exibidos na interface. Automações, relatórios e quantidade de itens da cronologia continuaram em 3.

**Status:** Aprovado conforme a gravação.

## Arquivos

| Arquivo | Conteúdo | SHA-256 |
| --- | --- | --- |
| [resultados_hoje_00-07.jpg](resultados_hoje_00-07.jpg) | Hoje selecionado com zero aniversariantes. | `37219604cc0d3b77c8fb81d91725e26b6a70e308e8f39f274b242d71c4174e32` |
| [resultados_7_dias_00-12.jpg](resultados_7_dias_00-12.jpg) | Últimos 7 dias selecionado com dois aniversariantes. | `d0c603a3d5ef3b58a5e121e06211c6daa6f918d301c520a8c04f1bedc2fa75b5` |
| [linha_do_tempo.txt](linha_do_tempo.txt) | Cronologia de ações, rede e quadros consultados no Jam. | — |
| [origem.url](origem.url) | Endereço original do Jam. | — |

## Limites

Esta pasta contém a cronologia e os recortes dos quadros consultados. A gravação integral fica no Jam.

Foi confirmada a mudança de recorte na interface e na API. A fronteira dos sete dias e a data de cada item não foram validadas com uma base controlada.
