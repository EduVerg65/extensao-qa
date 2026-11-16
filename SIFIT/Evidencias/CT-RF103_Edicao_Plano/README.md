# Evidência — CT-RF103: Edição de plano pelo modal Editar Plano

- **Fonte:** [Jam original](https://jam.dev/c/233c5d21-e108-4a55-b6f6-8738cb3fc6a6).
- **Autor exibido:** Gustavo Pelissari Oenning.
- **Gravação:** 15/11/2026, 21:54 BRT; duração de 1 min 10 s.
- **Revisão:** 15/11/2026.
- **Caso:** [CT-RF103](../../Cenario_Teste/CT-RF103_Edicao_Plano.md).
- **Defeito:** nenhum no fluxo avaliado.
- **Ambiente:** https://sifit.centrion.com.br/planos; Chrome 157.0.8103.78, Windows 11 (x86), janela 1920 × 855.

## Resultado e origem

O modal abre com os dados do plano 41, o benefício é gravado com POST plano/update/1 (HTTP 200, verifica_erro false) e a listagem é recarregada.

**Status:** Aprovado conforme a gravação.

## Arquivos

| Arquivo | Conteúdo | SHA-256 |
| --- | --- | --- |
| [editar_plano_01-02.png](editar_plano_01-02.png) | plano 41 "Teste Final". | `040025d689747d0ba36c0d339d221df968833090c6020b19e608b41477dbd327` |
| [resposta_seleciona_plano.png](resposta_seleciona_plano.png) | dados do plano 41. | `b16a3d72776b3b8d03cb795c7eaac9466e21ef6626818fb99ca983bf782163b6` |
| [requisicao_update.png](requisicao_update.png) | id 41 e benefícios. | `2dd285dc09e224ed077ab5dcfe55f292f83e98c9cfa94010aa7a237f75e43cf0` |
| [resposta_update.png](resposta_update.png) | verifica_erro false. | `0dc9b6f1cf5c8679b8b9fc33b659b5e8cd09edc219e0f42bbaacff6d8767c325` |
| [rede_lista.jpg](rede_lista.jpg) | 25 entradas da gravação. | `d8b0d95f516867210a9b7d5d3914346c72dcc0258acd9fbd9a5ee593f60110b7` |
| [linha_do_tempo.txt](linha_do_tempo.txt) | Cronologia de ações, digitação e rede do Jam. | — |
| [origem.url](origem.url) | Endereço original do Jam. | — |

## Limites

Esta pasta contém documentação da consulta, capturas extraídas da reprodução do Jam e a cronologia; não contém cópia do vídeo, e nenhum hash de vídeo foi gerado. As capturas mostram o botão de reprodução do Jam sobreposto. A mesma gravação é a fonte de vários casos.

Não foram confirmados a persistência após recarga, a edição dos demais campos e o efeito no cartão Ativos.

Não houve execução da aplicação, inspeção de código, acesso ao banco ou reteste nesta revisão.
