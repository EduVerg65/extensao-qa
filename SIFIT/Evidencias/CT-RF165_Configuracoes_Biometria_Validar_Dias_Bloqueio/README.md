# Evidência — CT-RF165: Validar dias negativos para travar a catraca

- **Fonte:** [Jam 9 — Validação de dias de bloqueio da catraca](https://jam.dev/c/f607bc49-184f-4d55-81ab-7db825af6021).
- **Autor exibido:** Pedro Figueiredo.
- **Gravação:** 16/11/2026, 23:07:08 BRT, com duração de 15,68 s.
- **Revisão:** 18/11/2026.
- **Caso:** [CT-RF165](../../Cenario_Teste/CT-RF165_Configuracoes_Biometria_Validar_Dias_Bloqueio.md).
- **Defeito:** [BUG-054](../../Relatorio-de-Bugs.md#bug-054), em triagem.
- **Ambiente:** https://sifit.centrion.com.br/configuracoes · Chrome 157.0.8103.79 / Windows 10 (x86) · vídeo de 1918 × 998.

## Resultado e origem

O POST enviou `dias_bloqueio: -1` e retornou HTTP 200 com `verifica_erro: false`. Depois de recarregar, o GET e o campo mostraram 0. A captura não registrou uma orientação específica sobre a entrada negativa.

**Status:** Reprovado nas evidências.

## Arquivos

| Arquivo | Conteúdo | SHA-256 |
| --- | --- | --- |
| [dias_bloqueio_negativo_00-04.jpg](dias_bloqueio_negativo_00-04.jpg) | Travar Catraca Após (dias) em -1 antes de salvar. | `7ab9068e8b7a0cf7878b168d5671a751c299823e2afe7de279b07c74eddcc3b7` |
| [dias_bloqueio_zero_apos_recarregar_00-12.jpg](dias_bloqueio_zero_apos_recarregar_00-12.jpg) | Campo exibe 0 após recarregar e retornar a Biometria. | `430da8943f20883cbdde9da2cb8effbfc0fa2272549f30228b9f35e1ba332c47` |
| [linha_do_tempo.txt](linha_do_tempo.txt) | Cronologia de ações, rede e quadros consultados no Jam. | — |
| [origem.url](origem.url) | Endereço original do Jam. | — |

## Limites

Os recortes e a cronologia omitem credenciais, valores de conexão e conteúdo que identifica terceiros. A gravação integral fica no Jam.

A consulta devolveu 0. A gravação não determina se esse valor resultou de normalização ou se o sistema preservou o valor anterior.
