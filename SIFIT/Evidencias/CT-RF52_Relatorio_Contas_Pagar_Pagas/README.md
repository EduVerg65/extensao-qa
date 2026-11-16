# Evidência — CT-RF52: Relatório de Contas a Pagar (Pagas) sem registros

- **Fonte:** [Jam original](https://jam.dev/c/3b4777a4-e1b0-4038-9b06-26c73669d7d1).
- **Autor exibido:** Gustavo Pelissari Oenning.
- **Gravação:** 15/11/2026, 19:09 BRT; duração de 58 s.
- **Revisão:** 15/11/2026.
- **Caso:** [CT-RF52](../../Cenario_Teste/CT-RF52_Relatorio_Contas_Pagar_Pagas.md).
- **Defeito:** nenhum confirmado; ponto a validar.
- **Ambiente:** https://sifit.centrion.com.br/relatorios; Chrome 157.0.8103.78, Windows 11 (x86), janela 1920 × 911.

## Resultado e origem

O PDF `relatorio (7).pdf` abre e apresenta a estrutura de "Relatório de Contas a Pagar (Pagas)" para 01/11/2026 até 15/11/2026, sem linhas e com "TOTALIZADORES: R$ 0,00 R$ 0,00".

**Status:** A validar — regra ou contexto pendente.

## Arquivos

| Arquivo | Conteúdo | SHA-256 |
| --- | --- | --- |
| [relatorio_7_contas_pagar_pagas.pdf](relatorio_7_contas_pagar_pagas.pdf) | PDF sem linhas e com totalizadores R$ 0,00. | `3aa12ce66680e6ad8609e4618b96d124f8ae6948ce3d2d8c863d88a416d208d8` |
| [formulario_contas_pagar_00-48.png](formulario_contas_pagar_00-48.png) | tipo Contas a Pagar com o período. | `0a273f0f99e50abc9180470287e3fbb867bdfe2ab238593d2c17d461b67da493` |
| [rede_lista.png](rede_lista.png) | oito POST relatorio (HTTP 200) e um OPTIONS. | `ecd2414b90cbba8bf93464a4691473a1881f9089b4d3a45cd6d145f309dba798` |
| [relatorio_7_contas_pagar_pagas_pagina1.png](relatorio_7_contas_pagar_pagas_pagina1.png) | Primeira página do PDF (`relatorio (7).pdf`) renderizada para consulta; o PDF original segue no arquivo acima. | `f63e1cde9cff523eb7cfa1a000012fe68bdc599027c5605d23bd66bdf58c9f5d` |
| [linha_do_tempo.txt](linha_do_tempo.txt) | Cronologia de ações, digitação e rede do Jam. | — |
| [origem.url](origem.url) | Endereço original do Jam. | — |

## Limites

Esta pasta contém documentação da consulta, capturas extraídas da reprodução do Jam e a cronologia; não contém cópia do vídeo, e nenhum hash de vídeo foi gerado. As capturas mostram o botão de reprodução do Jam sobreposto. A mesma gravação é a fonte de vários casos.

As contas a pagar do período no módulo não foram conferidas; o comportamento com pagamentos e a regra do escopo do filtro "Pagas" não foram exercitados ou fornecidos.

Não houve execução da aplicação, inspeção de código, acesso ao banco ou reteste nesta revisão.
