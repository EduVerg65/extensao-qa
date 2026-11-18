# Evidência — CT-RF117: Cancelar uma alteração nas Configurações sem salvar

- **Fonte:** [Jam original](https://jam.dev/c/e8faa199-1177-4563-8b00-590606669a1d).
- **Autor exibido:** Pedro Figueiredo.
- **Gravação:** 16/11/2026, 22:05:00 BRT, com duração de 20,02 s.
- **Revisão:** 17/11/2026.
- **Caso:** [CT-RF117](../../Cenario_Teste/CT-RF117_Configuracoes_Cancelar_Alteracao.md).
- **Defeito:** Nenhum no fluxo avaliado.
- **Ambiente:** https://sifit.centrion.com.br/configuracoes · Chrome 157.0.8103.79 / Windows 10 (x86) · vídeo de 1918 × 998.

## Resultado e origem

O valor 1100 foi editado para 15. Cancelar levou à Página Inicial. Após voltar a Configurações, o campo mostrou 1100 e o GET retornou `dias_ausente: 1100`. A gravação não contém chamada a `/api/configuracoes/alterar/1`.

**Status:** Aprovado conforme a gravação.

## Arquivos

| Arquivo | Conteúdo | SHA-256 |
| --- | --- | --- |
| [dias_editados_00-07.jpg](dias_editados_00-07.jpg) | Valor 15 no formulário antes de cancelar. | `12e677c765271b91eb976d92c2465526256f34c88eaac738cb470450a5b1b595` |
| [dias_apos_cancelar_00-16.jpg](dias_apos_cancelar_00-16.jpg) | Valor 1100 após voltar a Configurações. | `6f588f3fc20babdc84c0c637fa11cdc0ab8b952fc8bb8a5d965e5359b9ae46f7` |
| [linha_do_tempo.txt](linha_do_tempo.txt) | Cronologia de ações, rede e quadros consultados no Jam. | — |
| [origem.url](origem.url) | Endereço original do Jam. | — |

## Limites

Esta pasta contém a cronologia, a origem e os recortes dos quadros consultados. O vídeo permanece no Jam.

O cancelamento foi verificado para uma alteração no campo de dias de ausência na aba Home. Alterações simultâneas e as demais abas ficam para nova execução.
