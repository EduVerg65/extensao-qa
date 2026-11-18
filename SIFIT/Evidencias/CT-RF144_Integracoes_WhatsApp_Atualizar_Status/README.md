# Evidência — CT-RF144: Consultar novamente o status da integração de WhatsApp

- **Fonte:** [Jam 6 — Atualização manual de status](https://jam.dev/c/0da79ab0-b557-46af-a48c-60c1a8a62628).
- **Autor exibido:** Pedro Figueiredo.
- **Gravação:** 16/11/2026, 23:45:52 BRT, com duração de 18,67 s.
- **Revisão:** 17/11/2026.
- **Caso:** [CT-RF144](../../Cenario_Teste/CT-RF144_Integracoes_WhatsApp_Atualizar_Status.md).
- **Defeito:** [BUG-050](../../Relatorio-de-Bugs.md#bug-050) na tentativa posterior de conexão.
- **Ambiente:** https://sifit.centrion.com.br/configuracoes · Chrome 157.0.8103.79 / Windows 10 (x86) · vídeo de 1918 × 998.

## Resultado e origem

Sete cliques dispararam sete GETs bem-sucedidos. As respostas mantiveram `status: desconectado` e `conectado: false`, e `ultima_verificacao` avançou de 02:45:19 para 02:45:27 conforme os valores da API. Uma ação posterior, Conectar WhatsApp, exibiu “Erro ao conectar” e também apresentou a divergência registrada no BUG-050.

**Status:** Aprovado conforme a gravação.

## Arquivos

| Arquivo | Conteúdo | SHA-256 |
| --- | --- | --- |
| [atualizar_status_00-06.jpg](atualizar_status_00-06.jpg) | Cartão Atualizar Status durante a sequência de consultas. | `468559a96b737b9ccb612842a9ee7b0632b11c09e03fe3ee4f6e12c4f210b3d3` |
| [erro_ao_conectar_00-16.jpg](erro_ao_conectar_00-16.jpg) | Mensagem exibida após a tentativa adicional de conexão. | `ca3bb43f3e5a7977747341ae0036840dd486b73085aa4125d686fc26731e32bb` |
| [linha_do_tempo.txt](linha_do_tempo.txt) | Cronologia de ações, rede e quadros consultados no Jam. | — |
| [origem.url](origem.url) | Endereço original do Jam. | — |

## Limites

Os recortes e a cronologia omitem valores dos campos de integração, identificadores de conta e dados de autenticação. A gravação integral fica no Jam.

A aprovação cobre o comando de consulta e a resposta em estado desconectado. A gravação não mostra a atualização visual do cartão de resumo após os cliques. A conexão posterior tem evidência vinculada ao BUG-050.
