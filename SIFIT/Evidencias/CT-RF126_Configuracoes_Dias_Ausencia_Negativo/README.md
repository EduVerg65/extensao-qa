# Evidência — CT-RF126: Bloquear número negativo no campo de dias de ausência

- **Fonte:** [Jam original](https://jam.dev/c/d5786f67-6e5f-44f5-bbba-fbd763a88740).
- **Autor exibido:** Pedro Figueiredo.
- **Gravação:** 16/11/2026, 22:00:22 BRT, com duração de 25,75 s.
- **Revisão:** 17/11/2026.
- **Caso:** [CT-RF126](../../Cenario_Teste/CT-RF126_Configuracoes_Dias_Ausencia_Negativo.md).
- **Defeito:** [BUG-047](../../Relatorio-de-Bugs.md#bug-047), em triagem.
- **Ambiente:** https://sifit.centrion.com.br/configuracoes · Chrome 157.0.8103.79 / Windows 10 (x86) · vídeo de 1918 × 998.

## Resultado e origem

O POST com `dias_ausente=-1` retornou HTTP 200 com `verifica_erro: false`. Após recarregar, o campo exibiu -1 e o GET confirmou `dias_ausente: -1`. No fim, 1100 foi reenviado com HTTP 200.

**Status:** Reprovado nas evidências.

## Arquivos

| Arquivo | Conteúdo | SHA-256 |
| --- | --- | --- |
| [dias_negativo_antes_00-06.jpg](dias_negativo_antes_00-06.jpg) | Valor -1 antes de salvar. | `1ee5a73ec7858a9a1d6e9ee244ba699d65fb3ddc9fbe4e882ab05d370a7d2ea6` |
| [dias_negativo_recarga_00-13.jpg](dias_negativo_recarga_00-13.jpg) | Valor -1 após recarregar. | `df339e0f19929aeb6e81e4df7272004492b13f5e5498d5991b57de983cade0d3` |
| [linha_do_tempo.txt](linha_do_tempo.txt) | Cronologia de ações, rede e quadros consultados no Jam. | — |
| [origem.url](origem.url) | Endereço original do Jam. | — |

## Limites

Esta pasta contém a cronologia e os recortes dos quadros consultados. A gravação integral fica no Jam.

A evidência confirma a persistência de -1. O efeito sobre a classificação de clientes ausentes e a abrangência para outros negativos não foram exercitados.
