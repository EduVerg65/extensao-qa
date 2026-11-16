# Evidência — CT-RF92: Conta a pagar a colaborador é cadastrada sem colaborador informado

- **Fonte:** [Jam original](https://jam.dev/c/5d0afaf4-5abd-4e85-923f-27448304a9ef).
- **Autor exibido:** Gustavo Pelissari Oenning.
- **Gravação:** 15/11/2026, 21:58 BRT; duração de 1 min.
- **Revisão:** 15/11/2026.
- **Caso:** [CT-RF92](../../Cenario_Teste/CT-RF92_Cadastro_Conta_Colaborador_Sem_Colaborador.md).
- **Defeito:** [BUG-039](../../Relatorio-de-Bugs.md#bug-039), em triagem.
- **Ambiente:** https://sifit.centrion.com.br/contas-pagar; Chrome 157.0.8103.78, Windows 11 (x86), janela 1920 × 911.

## Resultado e origem

A conta do tipo Pagto. Colaborador foi gravada com HTTP 201 sem colaborador informado e listada com "-" no colaborador, sem mensagem de validação.

**Status:** Reprovado nas evidências — conta de colaborador gravada sem colaborador; defeito em triagem.

## Arquivos

| Arquivo | Conteúdo | SHA-256 |
| --- | --- | --- |
| [formulario_tipo_colaborador_00-15.png](formulario_tipo_colaborador_00-15.png) | tipo Pagto. Colaborador com Código e Colaborador vazios. | `2356aa15921456743718cf011ec469db51f824a9f13278445e65359341c49d4c` |
| [formulario_preenchido_00-41.png](formulario_preenchido_00-41.png) | colaborador não informado. | `c081fd33ffe0a2c8b4782df7946be360e9155267f03c4a2f23b9e396d245d556` |
| [lista_apos_cadastro_00-50.png](lista_apos_cadastro_00-50.png) | conta 29 com "-" em Fornecedor / Colaborador. | `beef155265eb912304656d592c9bfbdaf7a8b0537d8888c8947f112f16e8cea6` |
| [requisicao_cadastrar.png](requisicao_cadastrar.png) | colaborador_recebedor_id vazio. | `484ed7332d5229c222c9d954f39510390345edcc771ac3014ed5341976698ff1` |
| [resposta_cadastrar.png](resposta_cadastrar.png) | verifica_erro false. | `e85f4ea3cbba1daaeb697ec5c0f68c8a691b7658a2dafae392f1f69e138bdf2f` |
| [rede_lista.jpg](rede_lista.jpg) | primeiras 31 entradas da gravação. | `b80601de3e09b18c93ee63df32a0b2dd01269fbc1b86a85f60904fca406fc507` |
| [linha_do_tempo.txt](linha_do_tempo.txt) | Cronologia de ações, digitação e rede do Jam. | — |
| [origem.url](origem.url) | Endereço original do Jam. | — |

## Limites

Esta pasta contém documentação da consulta, capturas extraídas da reprodução do Jam e a cronologia; não contém cópia do vídeo, e nenhum hash de vídeo foi gerado. As capturas mostram o botão de reprodução do Jam sobreposto. A mesma gravação é a fonte de vários casos.

Não foram confirmados a regra do campo, a validação no servidor e o comportamento do tipo fornecedor sem fornecedor.

Não houve execução da aplicação, inspeção de código, acesso ao banco ou reteste nesta revisão.
