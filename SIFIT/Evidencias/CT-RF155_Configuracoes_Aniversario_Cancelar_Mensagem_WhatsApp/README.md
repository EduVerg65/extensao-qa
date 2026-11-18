# Evidência — CT-RF155: Cancelar a edição da mensagem de aniversário do WhatsApp

- **Fonte:** [Jam 5 — Cancelamento da edição da mensagem de WhatsApp](https://jam.dev/c/a58b851c-77c2-4a49-be3b-8a5c007d2bcb).
- **Autor exibido:** Pedro Figueiredo.
- **Gravação:** 16/11/2026, 23:17:29 BRT, com duração de 20,95 s.
- **Revisão:** 18/11/2026.
- **Caso:** [CT-RF155](../../Cenario_Teste/CT-RF155_Configuracoes_Aniversario_Cancelar_Mensagem_WhatsApp.md).
- **Defeito:** Nenhum no fluxo avaliado.
- **Ambiente:** https://sifit.centrion.com.br/configuracoes · Chrome 157.0.8103.79 / Windows 10 (x86) · vídeo de 1918 × 998.

## Resultado e origem

Cancelar retornou à Página Inicial. Ao abrir Configurações e voltar a Aniversário, o canal estava desmarcado. Quando foi marcado novamente, apareceu a mensagem anterior. A tentativa de edição ficou sem POST de salvamento.

**Status:** Aprovado conforme a gravação.

## Arquivos

| Arquivo | Conteúdo | SHA-256 |
| --- | --- | --- |
| [mensagem_editada_antes_de_cancelar_00-09.jpg](mensagem_editada_antes_de_cancelar_00-09.jpg) | Texto temporário no campo WhatsApp antes de Cancelar. | `43299038d442172af003ae2fda3bc59d7a8665ef095aba4fc0ecb06cd47a32e6` |
| [mensagem_anterior_apos_reabrir_00-20.jpg](mensagem_anterior_apos_reabrir_00-20.jpg) | Texto anterior exibido após retornar e selecionar WhatsApp novamente. | `e6f45b2422216fc7ed263606cd94cc635f9edcd205f40fe46beea446faadada4` |
| [linha_do_tempo.txt](linha_do_tempo.txt) | Cronologia de ações, rede e quadros consultados no Jam. | — |
| [origem.url](origem.url) | Endereço original do Jam. | — |

## Limites

Os recortes e a cronologia omitem valores dos campos de integração, identificadores de conta e dados de autenticação. A gravação integral fica no Jam.

O resultado cobre o cancelamento antes de salvar na aba Aniversário. O envio da mensagem não foi exercitado.
