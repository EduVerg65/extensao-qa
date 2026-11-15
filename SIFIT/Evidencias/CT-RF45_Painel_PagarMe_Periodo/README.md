# Evidência — CT-RF45: Painel Pagar.me mantém Recebimentos e gráfico ao trocar o período

- **Fonte:** [Jam original](https://jam.dev/c/e6e551ef-9196-4c79-b6a2-89747b1e8b33).
- **Autor exibido:** Gustavo Pelissari Oenning.
- **Gravação:** 15/11/2026, 19:06 BRT; duração de 1 min 11 s.
- **Revisão:** 15/11/2026.
- **Caso:** [CT-RF45](../../Cenario_Teste/CT-RF45_Painel_PagarMe_Periodo.md).
- **Defeito:** [BUG-021](../../Relatorio-de-Bugs.md#bug-021), em triagem.
- **Ambiente:** https://sifit.centrion.com.br/pagarme; Chrome 157.0.8103.78, Windows 11 (x86), janela 1920 × 911.

## Resultado e origem

No quadro de 0:00 o seletor mostra "Últimos 30 dias" e o cartão Recebimentos apresenta R$ 38.420,00; no quadro de 0:25 o seletor mostra "Últimos 7 dias" e o valor e o gráfico permanecem idênticos. Os indicadores de saldo aparecem como "R$ --" durante toda a gravação.

**Status:** Reprovado nas evidências — recebimentos e gráfico não mudam com o período; defeito em triagem.

## Arquivos

| Arquivo | Conteúdo | SHA-256 |
| --- | --- | --- |
| [painel_00-00.png](painel_00-00.png) | período "Últimos 30 dias", Recebimentos R$ 38.420,00 e gráfico. | `c64163bf6d45180dd89cc25fe87b3559bd2daf17544cb783e6da049efee9e74f` |
| [painel_periodo_7dias_00-25.png](painel_periodo_7dias_00-25.png) | seletor em "Últimos 7 dias" com o mesmo valor e o mesmo gráfico. | `c56ed2bd2579c1f20e263b8a5e536e6ca8ba0cf3b6df87218bf9a560e89affe6` |
| [rede_lista.png](rede_lista.png) | grupos de POST ver-saldo, pagarme, recebiveis e transacoes. | `913dde8fcc507730737f892085ebbf9fd2dc4b0ca0a36cf33fc6a56b90229cf7` |
| [linha_do_tempo.txt](linha_do_tempo.txt) | Cronologia de ações, digitação e rede do Jam. | — |
| [origem.url](origem.url) | Endereço original do Jam. | — |

## Limites

Esta pasta contém documentação da consulta, capturas extraídas da reprodução do Jam e a cronologia; não contém cópia do vídeo, e nenhum hash de vídeo foi gerado. As capturas mostram o botão de reprodução do Jam sobreposto. A mesma gravação é a fonte de vários casos.

Os corpos das requisições não foram capturados. O clique no seletor não consta na cronologia; a leitura do eixo de datas é aproximada. Não foi confirmado se o painel usa dados reais ou de demonstração.

Não houve execução da aplicação, inspeção de código, acesso ao banco ou reteste nesta revisão.
