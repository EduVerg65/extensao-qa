# Evidência — CT-RF143: Tratar falha ao conectar WhatsApp via Evolution API

- **Fonte:** [Jam 5 — Tentativas de conexão pela Evolution API](https://jam.dev/c/087b5e4f-7d73-4be3-979d-9a39f474b836).
- **Autor exibido:** Pedro Figueiredo.
- **Gravação:** 16/11/2026, 23:44:10 BRT, com duração de 20,55 s.
- **Revisão:** 17/11/2026.
- **Caso:** [CT-RF143](../../Cenario_Teste/CT-RF143_Integracoes_WhatsApp_Conectar_Evolution.md).
- **Defeito:** [BUG-050](../../Relatorio-de-Bugs.md#bug-050), em triagem.
- **Ambiente:** https://sifit.centrion.com.br/configuracoes · Chrome 157.0.8103.79 / Windows 10 (x86) · vídeo de 1918 × 998.

## Resultado e origem

A tela exibiu “Falha ao conectar na Evolution API” nas duas tentativas e não apresentou QR Code utilizável. Em ambas, o POST retornou HTTP 200 com `verifica_erro: false`, `status: conectando` e `conectado: false`. A resposta continha a mensagem de falha, em desacordo com a flag `verifica_erro`.

**Status:** Reprovado nas evidências.

## Arquivos

| Arquivo | Conteúdo | SHA-256 |
| --- | --- | --- |
| [conectar_whatsapp_00-01.jpg](conectar_whatsapp_00-01.jpg) | Ação Conectar WhatsApp antes da primeira tentativa. | `ab248a63cfeb6e5873f8f44f9f6d7f1c6292e89821f10525f73970ad9607b60a` |
| [falha_evolution_00-16.jpg](falha_evolution_00-16.jpg) | Mensagem de falha exibida pela interface. | `fee29a8bffa3c7e43eb2d9236e0c4e521294a2a3771a440fda880a141636ca73` |
| [linha_do_tempo.txt](linha_do_tempo.txt) | Cronologia de ações, rede e quadros consultados no Jam. | — |
| [origem.url](origem.url) | Endereço original do Jam. | — |

## Limites

Os recortes e a cronologia omitem valores dos campos de integração, identificadores de conta e dados de autenticação. A gravação integral fica no Jam.

Os parâmetros do provedor não foram validados. A causa da falha de conexão e o caminho de sucesso exigem testes controlados. O defeito registrado é a divergência da flag de erro.
