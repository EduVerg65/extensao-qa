# Evidência — CT-RF42: Solicitação de saque no painel Pagar.me

- **Fonte:** [Jam original](https://jam.dev/c/e6e551ef-9196-4c79-b6a2-89747b1e8b33).
- **Autor exibido:** Gustavo Pelissari Oenning.
- **Gravação:** 15/11/2026, 19:06 BRT; duração de 1 min 11 s.
- **Revisão:** 15/11/2026.
- **Caso:** [CT-RF42](../../Cenario_Teste/CT-RF42_Solicitacao_Saque_PagarMe.md).
- **Defeito:** nenhum confirmado; ponto a validar.
- **Ambiente:** https://sifit.centrion.com.br/pagarme; Chrome 157.0.8103.78, Windows 11 (x86), janela 1920 × 911.

## Resultado e origem

Em 0:03, o clique em Confirmar Saque (valor 1000, saldo disponível "R$ --") gera `OPTIONS` HTTP 204 e `POST` de nome `sacar-saldo` com HTTP 200. Em 0:05 o formulário está fechado e a interface não apresenta mensagem de resultado.

**Status:** A validar — regra ou contexto pendente.

## Arquivos

| Arquivo | Conteúdo | SHA-256 |
| --- | --- | --- |
| [painel_00-00.png](painel_00-00.png) | painel Pagar.me com os indicadores de saldo como "R$ --". | `c64163bf6d45180dd89cc25fe87b3559bd2daf17544cb783e6da049efee9e74f` |
| [saque_formulario_00-04.png](saque_formulario_00-04.png) | formulário Solicitar Saque com valor 1000 e saldo "R$ --". | `f15145c99ed7f0d7cdd2b93c52853ca7e649ab943a15f184df697e0ba52f20b6` |
| [apos_saque_00-05.png](apos_saque_00-05.png) | formulário fechado, sem mensagem visível. | `418ea52b877eef971bc4b1cb1f3af9856a898c30e4d46e1b245f55897d7855ef` |
| [rede_lista.png](rede_lista.png) | entradas da gravação, incluindo OPTIONS e POST de saque. | `913dde8fcc507730737f892085ebbf9fd2dc4b0ca0a36cf33fc6a56b90229cf7` |
| [linha_do_tempo.txt](linha_do_tempo.txt) | Cronologia de ações, digitação e rede do Jam. | — |
| [origem.url](origem.url) | Endereço original do Jam. | — |

## Limites

Esta pasta contém documentação da consulta, capturas extraídas da reprodução do Jam e a cronologia; não contém cópia do vídeo, e nenhum hash de vídeo foi gerado. As capturas mostram o botão de reprodução do Jam sobreposto. A mesma gravação é a fonte de vários casos.

O corpo da requisição e da resposta de saque está indisponível no Jam. Não foram confirmados o registro do saque, a regra de saldo e a mensagem de retorno.

Não houve execução da aplicação, inspeção de código, acesso ao banco ou reteste nesta revisão.
