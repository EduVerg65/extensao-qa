# Evidência — CT-RF100: Alternância de tema e painel de notificações em Planos

- **Fonte:** [Jam original](https://jam.dev/c/233c5d21-e108-4a55-b6f6-8738cb3fc6a6).
- **Autor exibido:** Gustavo Pelissari Oenning.
- **Gravação:** 15/11/2026, 21:54 BRT; duração de 1 min 10 s.
- **Revisão:** 15/11/2026.
- **Caso:** [CT-RF100](../../Cenario_Teste/CT-RF100_Tema_Notificacoes_Planos.md).
- **Defeito:** nenhum no fluxo avaliado.
- **Ambiente:** https://sifit.centrion.com.br/planos; Chrome 157.0.8103.78, Windows 11 (x86), janela 1920 × 855.

## Resultado e origem

A alternância de tema gera POST usuario/tema com HTTP 200 e a interface muda de tema; o painel de Notificações abre com as abas Tudo e Não lidas, sem pendências.

**Status:** Aprovado conforme a gravação.

## Arquivos

| Arquivo | Conteúdo | SHA-256 |
| --- | --- | --- |
| [tema_escuro_00-16.png](tema_escuro_00-16.png) | tela Planos. | `f6bb06ecaf4607cfb5ca25c2bc22394d31ddc68030a34e2243355a6727cf2782` |
| [notificacoes_00-19.png](notificacoes_00-19.png) | abas Tudo e Não lidas, sem pendências. | `7b2e1e17f2d620d2b8c31469ca7e755b0f7be0fc7c8c56e6f111b22ca4419ea4` |
| [rede_lista.jpg](rede_lista.jpg) | 25 entradas da gravação, com os POST de tema. | `d8b0d95f516867210a9b7d5d3914346c72dcc0258acd9fbd9a5ee593f60110b7` |
| [linha_do_tempo.txt](linha_do_tempo.txt) | Cronologia de ações, digitação e rede do Jam. | — |
| [origem.url](origem.url) | Endereço original do Jam. | — |

## Limites

Esta pasta contém documentação da consulta, capturas extraídas da reprodução do Jam e a cronologia; não contém cópia do vídeo, e nenhum hash de vídeo foi gerado. As capturas mostram o botão de reprodução do Jam sobreposto. A mesma gravação é a fonte de vários casos.

Não foram confirmados a persistência após recarga, o painel com pendências e o ícone de perfil.

Não houve execução da aplicação, inspeção de código, acesso ao banco ou reteste nesta revisão.
