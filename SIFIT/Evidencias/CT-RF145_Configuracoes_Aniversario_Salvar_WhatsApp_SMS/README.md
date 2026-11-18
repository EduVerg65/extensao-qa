# Evidência — CT-RF145: Salvar mensagens de aniversário para WhatsApp e SMS

- **Fonte:** Jam 1 — Mensagens de aniversário por WhatsApp e SMS (gravação restrita por conter dados de integração).
- **Autor exibido:** Pedro Figueiredo.
- **Gravação:** 16/11/2026, 23:21:59 BRT, com duração de 32,65 s.
- **Revisão:** 17/11/2026.
- **Caso:** [CT-RF145](../../Cenario_Teste/CT-RF145_Configuracoes_Aniversario_Salvar_WhatsApp_SMS.md).
- **Defeito:** Nenhum no fluxo avaliado.
- **Ambiente:** https://sifit.centrion.com.br/configuracoes · Chrome 157.0.8103.79 / Windows 10 (x86) · vídeo de 1918 × 998.

## Resultado e origem

O salvamento retornou HTTP 200 com `verifica_erro: false`. A consulta depois de recarregar confirmou os canais WhatsApp e SMS habilitados e os textos WHATS e SMS. Ao reabrir a aba, os dois canais e os textos salvos apareceram novamente.

**Status:** Aprovado conforme a gravação.

## Arquivos

| Arquivo | Conteúdo | SHA-256 |
| --- | --- | --- |
| [mensagens_antes_de_salvar_00-21.jpg](mensagens_antes_de_salvar_00-21.jpg) | Canais WhatsApp e SMS marcados e respectivos textos antes de salvar. | `72ddc38d82e564a9a999326773a463f4c4751dbb19d857c19c3fc7fbacf5c483` |
| [mensagens_apos_reabrir_00-31.jpg](mensagens_apos_reabrir_00-31.jpg) | Canais e mensagens após recarregar e reabrir a aba. | `261bde56482cce133f26bbdb09d372d7e62418acbff520508cef0281543922fa` |
| [linha_do_tempo.txt](linha_do_tempo.txt) | Cronologia de ações, rede e quadros consultados no Jam. | — |
| [origem.url](origem.url) | Página testada. O link da gravação fica restrito. | — |

## Limites

Os recortes e a cronologia omitem valores dos campos de integração, identificadores de conta e dados de autenticação. A gravação integral fica no Jam.

A gravação verifica a configuração. O disparo automático, a entrega e a substituição das variáveis das mensagens estão fora da evidência.
