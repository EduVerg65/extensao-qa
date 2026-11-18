# Evidência — CT-RF123: Conferir a execução de Risco de Evasão na Central e em Resultados IA

- **Fonte:** [Jam original](https://jam.dev/c/efe26a44-458a-4802-bd48-8e23c5ac5fd9).
- **Autor exibido:** Pedro Figueiredo.
- **Gravação:** 16/11/2026, 21:56:07 BRT, com duração de 32,12 s.
- **Revisão:** 17/11/2026.
- **Caso:** [CT-RF123](../../Cenario_Teste/CT-RF123_Central_Resultados_IA_Execucao_Evasao.md).
- **Defeito:** Nenhum no fluxo avaliado.
- **Ambiente:** https://sifit.centrion.com.br/inteligencia-automacao · Chrome 157.0.8103.79 / Windows 10 (x86) · vídeo de 1918 × 998.

## Resultado e origem

O POST da automação retornou HTTP 200. A Central atualizou a última execução de 00:35 para 00:55 e os relatórios enviados no mês de 3 para 4. Em Resultados IA, Hoje mostrou 4 automações e 4 relatórios. A execução mais recente retornada pela API coincide com o horário de 00:55 mostrado na Central.

**Status:** Aprovado conforme a gravação.

## Arquivos

| Arquivo | Conteúdo | SHA-256 |
| --- | --- | --- |
| [central_ultima_execucao_00-04.jpg](central_ultima_execucao_00-04.jpg) | Central atualizada com última execução às 00:55. | `a3fd92afe744e36ad29e00b0b50a2c447fd005675e2d573f5b31a31bd49d68e3` |
| [resultados_hoje_00-22.jpg](resultados_hoje_00-22.jpg) | Resultados IA no filtro Hoje e linha do tempo de Risco de Evasão. | `76a2eccd10688d42dd841f108066a89ceaa055f699210c44e0f899b517ba80bb` |
| [linha_do_tempo.txt](linha_do_tempo.txt) | Cronologia de ações, rede e quadros consultados no Jam. | — |
| [origem.url](origem.url) | Endereço original do Jam. | — |

## Limites

Esta pasta contém a cronologia e os recortes dos quadros consultados. A gravação integral fica no Jam.

A hora de 00:55 é a referência exibida pelo SIFIT. O teste valida a exibição do mesmo registro nas duas telas. O recebimento efetivo pelo canal de envio e a regra dos cartões de risco não foram verificados.
