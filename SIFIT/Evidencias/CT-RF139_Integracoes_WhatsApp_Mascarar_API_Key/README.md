# Evidência — CT-RF139: Mascarar a API Key no formulário de WhatsApp

- **Fonte:** [Jam 1 — Mascaramento da API Key](https://jam.dev/c/ef0b67d5-1eea-49b7-84ea-bb306143df4a).
- **Autor exibido:** Pedro Figueiredo.
- **Gravação:** 16/11/2026, 23:37:22 BRT, com duração de 24,98 s.
- **Revisão:** 17/11/2026.
- **Caso:** [CT-RF139](../../Cenario_Teste/CT-RF139_Integracoes_WhatsApp_Mascarar_API_Key.md).
- **Defeito:** Nenhum no fluxo avaliado.
- **Ambiente:** https://sifit.centrion.com.br/configuracoes · Chrome 157.0.8103.79 / Windows 10 (x86) · vídeo de 1918 × 998.

## Resultado e origem

A máscara permaneceu ao editar a API Key e após recarregar a página e voltar à aba Integrações. Os eventos de digitação identificaram o controle como `input` do tipo `password`. Houve reconsulta da configuração, sem POST de salvamento no trecho.

**Status:** Aprovado conforme a gravação.

## Arquivos

| Arquivo | Conteúdo | SHA-256 |
| --- | --- | --- |
| [api_key_durante_edicao_00-07.jpg](api_key_durante_edicao_00-07.jpg) | Campo API Key durante a edição, com caracteres mascarados. | `daa3cc4a6ed71a8dcf76b27d32facf9d97642c8d7aa7b433dda0663976e6100d` |
| [api_key_ao_reabrir_00-21.jpg](api_key_ao_reabrir_00-21.jpg) | Campo API Key ainda mascarado após reabrir a aba. | `37647728d71b169e1120eff6b95bec9620ff2e514ffc6f352fdf695d786da42a` |
| [linha_do_tempo.txt](linha_do_tempo.txt) | Cronologia de ações, rede e quadros consultados no Jam. | — |
| [origem.url](origem.url) | Endereço original do Jam. | — |

## Limites

Os recortes e a cronologia omitem valores dos campos de integração, identificadores de conta e dados de autenticação. A gravação integral fica no Jam.

A aprovação cobre o mascaramento visual e a ausência de envio ao editar sem salvar. A gravação não verifica proteção em trânsito ou em armazenamento.
