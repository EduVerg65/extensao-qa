# Evidência — CT-RF136: Ativar Aniversariantes e conferir a persistência e o contador

- **Fonte:** [Jam original](https://jam.dev/c/60c724da-6760-4238-91f5-2ddad8f42bb3).
- **Autor exibido:** Pedro Figueiredo.
- **Gravação:** 16/11/2026, 21:31:02 BRT, com duração de 19,17 s.
- **Revisão:** 17/11/2026.
- **Caso:** [CT-RF136](../../Cenario_Teste/CT-RF136_Central_Ativar_Aniversariantes_Contador.md).
- **Defeito:** [BUG-049](../../Relatorio-de-Bugs.md#bug-049), em triagem.
- **Ambiente:** https://sifit.centrion.com.br/inteligencia-automacao · Chrome 157.0.8103.79 / Windows 10 (x86) · vídeo de 1918 × 998.

## Resultado e origem

O POST de ativação retornou sucesso e o cartão passou a indicar o estado ativo, mas o resumo ainda retornou `ativas: 1`. O contador chegou a dois quando o usuário acionou Atualizar, e a listagem confirmou Aniversariantes com `ativo: 1`. Em seguida, a desativação de restauração retornou sucesso e o contador voltou a um.

**Status:** Reprovado nas evidências.

## Arquivos

| Arquivo | Conteúdo | SHA-256 |
| --- | --- | --- |
| [aniversariantes_ativa_contador_um_00-07.jpg](aniversariantes_ativa_contador_um_00-07.jpg) | Aniversariantes ativa com contador ainda em uma automação. | `9299058113ed48b2b7f4c4e119a1baccd155a0d212cef8b01332a8481ee84fb2` |
| [aniversariantes_apos_atualizar_00-11.jpg](aniversariantes_apos_atualizar_00-11.jpg) | Aniversariantes ativa e contador em dois após Atualizar. | `1e23b69eb7f2d863330934e9cdac548c7b958f567068138108cc32d94d0ac227` |
| [linha_do_tempo.txt](linha_do_tempo.txt) | Cronologia de ações, rede e quadros consultados no Jam. | — |
| [origem.url](origem.url) | Endereço original do Jam. | — |

## Limites

Esta pasta contém a cronologia e os recortes dos quadros consultados. A gravação integral fica no Jam.

O estado ativo persistiu após Atualizar. A divergência observada ocorreu entre o cartão e o resumo depois do salvamento da ativação. A gravação não confirma a causa no servidor.
