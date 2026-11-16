# Evidência — CT-RF94: Visualização dos dados de uma conta a pagar

- **Fonte:** [Jam original](https://jam.dev/c/5d0afaf4-5abd-4e85-923f-27448304a9ef).
- **Autor exibido:** Gustavo Pelissari Oenning.
- **Gravação:** 15/11/2026, 21:58 BRT; duração de 1 min.
- **Revisão:** 15/11/2026.
- **Caso:** [CT-RF94](../../Cenario_Teste/CT-RF94_Visualizacao_Conta_Pagar.md).
- **Defeito:** nenhum no fluxo avaliado.
- **Ambiente:** https://sifit.centrion.com.br/contas-pagar; Chrome 157.0.8103.78, Windows 11 (x86), janela 1920 × 911.

## Resultado e origem

A lupa abre o modal com os dados da conta 29 (cancelada, R$ 2.342,34, vencimento 15/11/2026) e o botão Fechar retorna à listagem; o tipo é exibido como PAG_COLABORADOR.

**Status:** Aprovado conforme a gravação.

## Arquivos

| Arquivo | Conteúdo | SHA-256 |
| --- | --- | --- |
| [visualizar_conta_00-52.png](visualizar_conta_00-52.png) | conta 29, selo CANCELADO e seções preenchidas. | `4c7436cd2bd69270015dae278c99a6b04d21e5c798077d96c3d01fab351832a9` |
| [rede_lista.jpg](rede_lista.jpg) | primeiras 31 entradas da gravação. | `b80601de3e09b18c93ee63df32a0b2dd01269fbc1b86a85f60904fca406fc507` |
| [linha_do_tempo.txt](linha_do_tempo.txt) | Cronologia de ações, digitação e rede do Jam. | — |
| [origem.url](origem.url) | Endereço original do Jam. | — |

## Limites

Esta pasta contém documentação da consulta, capturas extraídas da reprodução do Jam e a cronologia; não contém cópia do vídeo, e nenhum hash de vídeo foi gerado. As capturas mostram o botão de reprodução do Jam sobreposto. A mesma gravação é a fonte de vários casos.

Não foram confirmados contas de outros tipos e status, o rótulo esperado do tipo e o conteúdo completo do modal.

Não houve execução da aplicação, inspeção de código, acesso ao banco ou reteste nesta revisão.
