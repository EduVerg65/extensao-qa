# Evidência — CT-RF148: Rejeitar código hexadecimal inválido na Cor Secundária

- **Fonte:** [Jam 4 — Validação da Cor Secundária](https://jam.dev/c/41aaf50a-2506-471a-8eeb-943674571771).
- **Autor exibido:** Pedro Figueiredo.
- **Gravação:** 16/11/2026, 23:26:21 BRT, com duração de 19,35 s.
- **Revisão:** 17/11/2026.
- **Caso:** [CT-RF148](../../Cenario_Teste/CT-RF148_Configuracoes_Design_Validar_Cor_Secundaria.md).
- **Defeito:** [BUG-051](../../Relatorio-de-Bugs.md#bug-051), em triagem.
- **Ambiente:** https://sifit.centrion.com.br/configuracoes · Chrome 157.0.8103.79 / Windows 10 (x86) · vídeo de 1918 × 998.

## Resultado e origem

As duas tentativas retornaram HTTP 200 com `verifica_erro: false`. O GET após recarregar devolveu `cor_secundaria: #ZZZZZZ` e o campo ainda mostrou esse valor ao reabrir a aba. Não houve indicação de rejeição na gravação. Ao reabrir, a amostra da Cor Secundária ficou sem a cor preta original.

**Status:** Reprovado nas evidências.

## Arquivos

| Arquivo | Conteúdo | SHA-256 |
| --- | --- | --- |
| [cor_secundaria_invalida_00-08.jpg](cor_secundaria_invalida_00-08.jpg) | Cor Secundária inválida durante o fluxo de salvamento. | `3148f98ee9d06d664f23644a58a8215c4a18b21015add3d7316a587c4e8abe87` |
| [cor_secundaria_invalida_persistida_00-16.jpg](cor_secundaria_invalida_persistida_00-16.jpg) | Mesmo valor inválido após recarregar e reabrir a aba. | `8cf049ef7ac0066bbfff24ffe050e94a0ed8a8bf0ab5a93279b22d932e726e1a` |
| [linha_do_tempo.txt](linha_do_tempo.txt) | Cronologia de ações, rede e quadros consultados no Jam. | — |
| [origem.url](origem.url) | Endereço original do Jam. | — |

## Limites

Os recortes e a cronologia omitem valores dos campos de integração, identificadores de conta e dados de autenticação. A gravação integral fica no Jam.

O defeito foi confirmado pela leitura posterior. O efeito do código inválido nos ambientes online não foi avaliado.
