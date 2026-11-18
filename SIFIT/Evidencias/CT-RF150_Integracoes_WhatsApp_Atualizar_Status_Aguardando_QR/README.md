# Evidência — CT-RF150: Atualizar a verificação do WhatsApp enquanto aguarda QR Code

- **Fonte:** Jam 6 — Atualização de status enquanto aguarda QR Code (gravação restrita por conter dados de integração).
- **Autor exibido:** Pedro Figueiredo.
- **Gravação:** 16/11/2026, 23:36:13 BRT, com duração de 25,37 s.
- **Revisão:** 17/11/2026.
- **Caso:** [CT-RF150](../../Cenario_Teste/CT-RF150_Integracoes_WhatsApp_Atualizar_Status_Aguardando_QR.md).
- **Defeito:** Nenhum no fluxo avaliado.
- **Ambiente:** https://sifit.centrion.com.br/configuracoes · Chrome 157.0.8103.79 / Windows 10 (x86) · vídeo de 1918 × 998.

## Resultado e origem

Antes da consulta, a tela mostrava 02:32 em Última Verificação. A API devolveu `status: conectando`, `conectado: false` e o horário 02:35:45. Ao retornar ao resumo, o painel indicava 02:35 e continuava em Aguardando QR Code.

**Status:** Aprovado conforme a gravação.

## Arquivos

| Arquivo | Conteúdo | SHA-256 |
| --- | --- | --- |
| [status_e_verificacao_antes_00-01.jpg](status_e_verificacao_antes_00-01.jpg) | Status Aguardando QR Code e horário de verificação antes da consulta. | `791992b74abaf074773972f1673fe52cc5186c20806835f7193036497b1ddebd` |
| [status_e_verificacao_apos_00-22.jpg](status_e_verificacao_apos_00-22.jpg) | Mesmo status e novo horário de verificação depois de Atualizar. | `db5b64e0307e93ce139d19a4606814d58894fe0d591ec36ae085cfe9ae433e3f` |
| [linha_do_tempo.txt](linha_do_tempo.txt) | Cronologia de ações, rede e quadros consultados no Jam. | — |
| [origem.url](origem.url) | Página testada. O link da gravação fica restrito. | — |

## Limites

Os recortes e a cronologia omitem valores dos campos de integração, identificadores de conta e dados de autenticação. A gravação integral fica no Jam.

O horário citado é o exibido pelo SIFIT e pela API. A gravação cobre a consulta em espera. Pareamento e mudança para conectado não foram exercitados.
