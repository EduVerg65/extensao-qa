# Evidência — CT-RF43: Criação de cobrança no painel Pagar.me

- **Fonte:** [Jam original](https://jam.dev/c/e6e551ef-9196-4c79-b6a2-89747b1e8b33).
- **Autor exibido:** Gustavo Pelissari Oenning.
- **Gravação:** 15/11/2026, 19:06 BRT; duração de 1 min 11 s.
- **Revisão:** 15/11/2026.
- **Caso:** [CT-RF43](../../Cenario_Teste/CT-RF43_Criacao_Cobranca_PagarMe.md).
- **Defeito:** nenhum no fluxo avaliado.
- **Ambiente:** https://sifit.centrion.com.br/pagarme; Chrome 157.0.8103.78, Windows 11 (x86), janela 1920 × 911.

## Resultado e origem

Em 0:30, o clique em Criar Cobrança (descrição "11111", valor 11111, método PIX) gera `OPTIONS` HTTP 204 e `POST` de nome `criar-cobranca` com HTTP 200. Em 0:31 o sistema apresenta o diálogo "Cobrança criada com sucesso!".

**Status:** Aprovado conforme a gravação.

## Arquivos

| Arquivo | Conteúdo | SHA-256 |
| --- | --- | --- |
| [nova_cobranca_00-29.png](nova_cobranca_00-29.png) | formulário Nova Cobrança preenchido (descrição, valor e PIX). | `256be0e03ea806b7683d4cb31e6fbfb89388c38d74a0e6c25702c2763a5d9244` |
| [cobranca_sucesso_00-31.png](cobranca_sucesso_00-31.png) | diálogo "Cobrança criada com sucesso!" (com o botão de reprodução do Jam sobreposto). | `4bfa927d6184459d6072b4f2fb6d38be80a34d2ba70bf120e8eccaf5f3dee061` |
| [rede_lista.png](rede_lista.png) | entradas da gravação, incluindo OPTIONS e POST de criar-cobranca. | `913dde8fcc507730737f892085ebbf9fd2dc4b0ca0a36cf33fc6a56b90229cf7` |
| [linha_do_tempo.txt](linha_do_tempo.txt) | Cronologia de ações, digitação e rede do Jam. | — |
| [origem.url](origem.url) | Endereço original do Jam. | — |

## Limites

Esta pasta contém documentação da consulta, capturas extraídas da reprodução do Jam e a cronologia; não contém cópia do vídeo, e nenhum hash de vídeo foi gerado. As capturas mostram o botão de reprodução do Jam sobreposto. A mesma gravação é a fonte de vários casos.

O corpo e a resposta da criação estão indisponíveis no Jam. Não foram verificados a presença da cobrança em Transações recentes, o link gerado e outros métodos de pagamento.

Não houve execução da aplicação, inspeção de código, acesso ao banco ou reteste nesta revisão.
