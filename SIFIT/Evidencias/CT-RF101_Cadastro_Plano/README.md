# Evidência — CT-RF101: Cadastro de plano pelo modal Novo Plano

- **Fonte:** [Jam original](https://jam.dev/c/233c5d21-e108-4a55-b6f6-8738cb3fc6a6).
- **Autor exibido:** Gustavo Pelissari Oenning.
- **Gravação:** 15/11/2026, 21:54 BRT; duração de 1 min 10 s.
- **Revisão:** 15/11/2026.
- **Caso:** [CT-RF101](../../Cenario_Teste/CT-RF101_Cadastro_Plano.md).
- **Defeito:** nenhum no fluxo avaliado.
- **Ambiente:** https://sifit.centrion.com.br/planos; Chrome 157.0.8103.78, Windows 11 (x86), janela 1920 × 855.

## Resultado e origem

Salvar Plano gerou POST plano/salvar/1 com HTTP 200 e id 66, e o cartão Planos passou de 40 para 41.

**Status:** Aprovado conforme a gravação.

## Arquivos

| Arquivo | Conteúdo | SHA-256 |
| --- | --- | --- |
| [modal_novo_plano_00-24.png](modal_novo_plano_00-24.png) | formulário vazio. | `407021ee320140693fe233962946781124f19703566d45ed14439e6f16531c96` |
| [modal_preenchido_00-46.png](modal_preenchido_00-46.png) | plano rerererere, status Inativo. | `77aa25ecda852d40f0a2ece8a37f175504e8d3bd86f140a74abc2370f68fd67a` |
| [cartoes_apos_cadastro_00-53.png](cartoes_apos_cadastro_00-53.png) | Planos 41 e Ativos 30. | `7fd65e798574751e9c96dff4ea0bcaa5f3bca56e47fc3c0c81655c9a21748704` |
| [requisicao_salvar.png](requisicao_salvar.png) | Corpo da requisição plano/salvar (início do corpo). | `48a69f59f5494fa99d0bf0359a8b7a1ab1d62de96977d9afda4b7220e0024881` |
| [resposta_salvar.png](resposta_salvar.png) | id 66. | `b76f78f82d6fb7447d4f9aa6fdd08325c60527a7311d9c6c5483f841053dc6b3` |
| [rede_lista.jpg](rede_lista.jpg) | 25 entradas da gravação. | `d8b0d95f516867210a9b7d5d3914346c72dcc0258acd9fbd9a5ee593f60110b7` |
| [linha_do_tempo.txt](linha_do_tempo.txt) | Cronologia de ações, digitação e rede do Jam. | — |
| [origem.url](origem.url) | Endereço original do Jam. | — |

## Limites

Esta pasta contém documentação da consulta, capturas extraídas da reprodução do Jam e a cronologia; não contém cópia do vídeo, e nenhum hash de vídeo foi gerado. As capturas mostram o botão de reprodução do Jam sobreposto. A mesma gravação é a fonte de vários casos.

Não foram confirmados a linha do plano na listagem, os campos obrigatórios e a gravação dos benefícios.

Não houve execução da aplicação, inspeção de código, acesso ao banco ou reteste nesta revisão.
