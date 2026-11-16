# Evidência — CT-RF58: Alternância de tema e painel de notificações em Prospecção

- **Fonte:** [Jam original](https://jam.dev/c/308607ff-8abc-40af-8c7c-429ce506ed64).
- **Autor exibido:** Gustavo Pelissari Oenning.
- **Gravação:** 15/11/2026, 21:52 BRT; duração de 1 min 2 s.
- **Revisão:** 15/11/2026.
- **Caso:** [CT-RF58](../../Cenario_Teste/CT-RF58_Tema_Notificacoes_Prospeccao.md).
- **Defeito:** nenhum no fluxo avaliado.
- **Ambiente:** https://sifit.centrion.com.br/prospeccao; Chrome 157.0.8103.78, Windows 11 (x86), janela 1920 × 911.

## Resultado e origem

A alternância de tema gera POST usuario/tema com HTTP 200 e a interface muda de tema; o painel de Notificações abre com as abas Tudo e Não lidas e a mensagem de estado sem pendências.

**Status:** Aprovado conforme a gravação.

## Arquivos

| Arquivo | Conteúdo | SHA-256 |
| --- | --- | --- |
| [tema_escuro_00-01.png](tema_escuro_00-01.png) | botão Escuro ativo na tela Prospecção. | `ba5e2e09086a8cbaacc1d43e03b1910584c17cdc99d762d9b5a015588ba1f934` |
| [notificacoes_00-03.png](notificacoes_00-03.png) | abas Tudo e Não lidas e estado sem pendências. | `c007155b5906e8d78d48da2d6819eb3784d90937800e76339dbc1270b6c0e016` |
| [rede_lista.jpg](rede_lista.jpg) | 16 entradas da gravação, com os POST de tema nas primeiras linhas. | `086e2ef346f296db2a43a6e695d9ae73ca4e84b7afb12f71364230da20f4bc52` |
| [linha_do_tempo.txt](linha_do_tempo.txt) | Cronologia de ações, digitação e rede do Jam. | — |
| [origem.url](origem.url) | Endereço original do Jam. | — |

## Limites

Esta pasta contém documentação da consulta, capturas extraídas da reprodução do Jam e a cronologia; não contém cópia do vídeo, e nenhum hash de vídeo foi gerado. As capturas mostram o botão de reprodução do Jam sobreposto. A mesma gravação é a fonte de vários casos.

Não foram confirmados a persistência após recarga, o painel com pendências e o comportamento do ícone de perfil.

Não houve execução da aplicação, inspeção de código, acesso ao banco ou reteste nesta revisão.
