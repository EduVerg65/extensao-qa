# Evidência — CT-RF156: Inserir variáveis na mensagem de aniversário do WhatsApp

- **Fonte:** [Jam 6 — Inserção de variáveis na mensagem de WhatsApp](https://jam.dev/c/fb2c4949-c68d-4f90-b47c-44da9dbe58a3).
- **Autor exibido:** Pedro Figueiredo.
- **Gravação:** 16/11/2026, 23:20:07 BRT, com duração de 32,14 s.
- **Revisão:** 18/11/2026.
- **Caso:** [CT-RF156](../../Cenario_Teste/CT-RF156_Configuracoes_Aniversario_Inserir_Variaveis_WhatsApp.md).
- **Defeito:** Nenhum no fluxo avaliado.
- **Ambiente:** https://sifit.centrion.com.br/configuracoes · Chrome 157.0.8103.79 / Windows 10 (x86) · vídeo de 1918 × 998.

## Resultado e origem

Os cliques acrescentaram `{nome_aluno}`, `{primeiro_nome}`, `{data_aniversario}` e `{idade}` ao texto editado. Cancelar voltou à Página Inicial. Após reabrir Aniversário e marcar WhatsApp, a mensagem anterior reapareceu. O trecho não registra POST de salvamento.

**Status:** Aprovado conforme a gravação.

## Arquivos

| Arquivo | Conteúdo | SHA-256 |
| --- | --- | --- |
| [variaveis_inseridas_00-16.jpg](variaveis_inseridas_00-16.jpg) | Variáveis selecionadas no painel aparecem no campo da mensagem. | `1b7b73dfc78f59a13bfeabaf90cbc95e6d0bbeffd00e6231f730eb0d014203ae` |
| [mensagem_apos_cancelar_00-29.jpg](mensagem_apos_cancelar_00-29.jpg) | Modelo anterior reaparece após cancelar e voltar ao formulário. | `d9b3055cc551bcf4ca64f43e21e1150753d7c67ea639f4afa7f280dfb208864b` |
| [linha_do_tempo.txt](linha_do_tempo.txt) | Cronologia de ações, rede e quadros consultados no Jam. | — |
| [origem.url](origem.url) | Endereço original do Jam. | — |

## Limites

Os recortes e a cronologia omitem valores dos campos de integração, identificadores de conta e dados de autenticação. A gravação integral fica no Jam.

O caso verifica a inserção dos marcadores no editor e o descarte da edição. A substituição por dados reais e o envio não foram exercitados.
