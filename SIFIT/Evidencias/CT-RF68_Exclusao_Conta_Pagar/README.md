# Evidência — CT-RF68: Exclusão de conta a pagar com confirmação

- **Fonte:** [Jam original](https://jam.dev/c/5d0afaf4-5abd-4e85-923f-27448304a9ef).
- **Autor exibido:** Gustavo Pelissari Oenning.
- **Gravação:** 15/11/2026, 21:58 BRT; duração de 1 min.
- **Revisão:** 15/11/2026.
- **Caso:** [CT-RF68](../../Cenario_Teste/CT-RF68_Exclusao_Conta_Pagar.md).
- **Defeito:** nenhum no fluxo avaliado.
- **Ambiente:** https://sifit.centrion.com.br/contas-pagar; Chrome 157.0.8103.78, Windows 11 (x86), janela 1920 × 911.

## Resultado e origem

A exclusão da conta 29 pede confirmação, retorna HTTP 200 sem erro e a listagem volta a apresentar apenas as contas 27 e 28.

**Status:** Aprovado conforme a gravação.

## Arquivos

| Arquivo | Conteúdo | SHA-256 |
| --- | --- | --- |
| [confirmar_exclusao_00-54.png](confirmar_exclusao_00-54.png) | Diálogo de confirmação em 0:54. | `e6181ca9f3a625853b3a2e2322d870128e6cec8f19981cac7bedb70685353426` |
| [lista_apos_exclusao_00-59.png](lista_apos_exclusao_00-59.png) | apenas as contas 27 e 28. | `6696e65063bb5a1cb6c08753fa7356730d0111f0ef8c2f933e92a9b1781bbfbb` |
| [requisicao_deletar.png](requisicao_deletar.png) | id 29. | `97eb75910b11239f6a0a8d7f78a5760af8524f5725ca3d241a16e42acb65e514` |
| [resposta_deletar.png](resposta_deletar.png) | verifica_erro false. | `54f53285a7d655d1c25253e7b0164d9a649699f2b068238c4880748c43bf5615` |
| [rede_lista.jpg](rede_lista.jpg) | primeiras 31 entradas da gravação. | `b80601de3e09b18c93ee63df32a0b2dd01269fbc1b86a85f60904fca406fc507` |
| [linha_do_tempo.txt](linha_do_tempo.txt) | Cronologia de ações, digitação e rede do Jam. | — |
| [origem.url](origem.url) | Endereço original do Jam. | — |

## Limites

Esta pasta contém documentação da consulta, capturas extraídas da reprodução do Jam e a cronologia; não contém cópia do vídeo, e nenhum hash de vídeo foi gerado. As capturas mostram o botão de reprodução do Jam sobreposto. A mesma gravação é a fonte de vários casos.

Não foram confirmados Cancelar, a persistência após recarga e a exclusão de contas pagas ou vinculadas.

Não houve execução da aplicação, inspeção de código, acesso ao banco ou reteste nesta revisão.
