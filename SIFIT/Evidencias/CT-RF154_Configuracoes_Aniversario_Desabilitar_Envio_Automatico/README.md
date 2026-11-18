# Evidência — CT-RF154: Desabilitar o envio automático de aniversário

- **Fonte:** [Jam 4 — Desativação do envio automático de aniversário](https://jam.dev/c/ee8a2ba9-164c-42bb-8efe-927dd6c534d5).
- **Autor exibido:** Pedro Figueiredo.
- **Gravação:** 16/11/2026, 23:15:01 BRT, com duração de 19,89 s.
- **Revisão:** 18/11/2026.
- **Caso:** [CT-RF154](../../Cenario_Teste/CT-RF154_Configuracoes_Aniversario_Desabilitar_Envio_Automatico.md).
- **Defeito:** Nenhum no fluxo avaliado.
- **Ambiente:** https://sifit.centrion.com.br/configuracoes · Chrome 157.0.8103.79 / Windows 10 (x86) · vídeo de 1918 × 998.

## Resultado e origem

O salvamento de Desabilitado retornou HTTP 200 com `verifica_erro: false`. Após recarregar, a consulta devolveu `enviar_mensagens_aniversario: nao` e o seletor mostrou Desabilitado. O POST de restauração para Habilitado retornou sucesso.

**Status:** Aprovado conforme a gravação.

## Arquivos

| Arquivo | Conteúdo | SHA-256 |
| --- | --- | --- |
| [envio_habilitado_00-01.jpg](envio_habilitado_00-01.jpg) | Envio automático em Habilitado antes da edição. | `47c7e4aab1e75f87fa8b8b7d859fb9dd6f7a8b08c060475ab989e85e608511e8` |
| [envio_desabilitado_00-15.jpg](envio_desabilitado_00-15.jpg) | Envio automático em Desabilitado após recarregar e reabrir Aniversário. | `2424878abafc8073e24d35ea81018959a92cde1afe62363aff84e20b88fd108d` |
| [linha_do_tempo.txt](linha_do_tempo.txt) | Cronologia de ações, rede e quadros consultados no Jam. | — |
| [origem.url](origem.url) | Endereço original do Jam. | — |

## Limites

Os recortes e a cronologia omitem valores dos campos de integração, identificadores de conta e dados de autenticação. A gravação integral fica no Jam.

Os canais estavam desmarcados na gravação. O disparo de mensagens e a interação com canais já habilitados não foram exercitados.
