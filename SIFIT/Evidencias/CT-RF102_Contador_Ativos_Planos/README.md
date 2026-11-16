# Evidência — CT-RF102: Cartão Ativos de Planos aumenta ao cadastrar e editar planos inativos

- **Fonte:** [Jam original](https://jam.dev/c/233c5d21-e108-4a55-b6f6-8738cb3fc6a6).
- **Autor exibido:** Gustavo Pelissari Oenning.
- **Gravação:** 15/11/2026, 21:54 BRT; duração de 1 min 10 s.
- **Revisão:** 15/11/2026.
- **Caso:** [CT-RF102](../../Cenario_Teste/CT-RF102_Contador_Ativos_Planos.md).
- **Defeito:** [BUG-041](../../Relatorio-de-Bugs.md#bug-041), em triagem.
- **Ambiente:** https://sifit.centrion.com.br/planos; Chrome 157.0.8103.78, Windows 11 (x86), janela 1920 × 855.

## Resultado e origem

Cadastrar um plano com status inativo elevou Ativos de 29 para 30 e editar o plano inativo 41 elevou Ativos para 31, sem mudança de status nas requisições.

**Status:** Reprovado nas evidências — cartão Ativos aumenta com planos inativos; defeito em triagem.

## Arquivos

| Arquivo | Conteúdo | SHA-256 |
| --- | --- | --- |
| [cartoes_antes_00-03.png](cartoes_antes_00-03.png) | Planos 40 e Ativos 29. | `72263246002ca75dcf9e3deb4956c71ca2cb05078d5bb52d114034ba03b19cf2` |
| [cartoes_apos_cadastro_00-53.png](cartoes_apos_cadastro_00-53.png) | Planos 41 e Ativos 30 após cadastrar plano inativo. | `7fd65e798574751e9c96dff4ea0bcaa5f3bca56e47fc3c0c81655c9a21748704` |
| [cartoes_apos_edicao_01-08.png](cartoes_apos_edicao_01-08.png) | Planos 41 e Ativos 31 após editar plano inativo. | `c3ed99dfee5304ebdbc4f8bddbbf82705afaa1ecd7d65f20e625099954a497c7` |
| [requisicao_salvar.png](requisicao_salvar.png) | status inativo. | `48a69f59f5494fa99d0bf0359a8b7a1ab1d62de96977d9afda4b7220e0024881` |
| [rede_lista.jpg](rede_lista.jpg) | 25 entradas da gravação. | `d8b0d95f516867210a9b7d5d3914346c72dcc0258acd9fbd9a5ee593f60110b7` |
| [linha_do_tempo.txt](linha_do_tempo.txt) | Cronologia de ações, digitação e rede do Jam. | — |
| [origem.url](origem.url) | Endereço original do Jam. | — |

## Limites

Esta pasta contém documentação da consulta, capturas extraídas da reprodução do Jam e a cronologia; não contém cópia do vídeo, e nenhum hash de vídeo foi gerado. As capturas mostram o botão de reprodução do Jam sobreposto. A mesma gravação é a fonte de vários casos.

Não foram confirmados a regra de cálculo do cartão e a contagem de planos ativos da listagem.

Não houve execução da aplicação, inspeção de código, acesso ao banco ou reteste nesta revisão.
