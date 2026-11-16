# Evidência — CT-RF51: Relatório de Contas a Receber sem Valor a Receber

- **Fonte:** [Jam original](https://jam.dev/c/3b4777a4-e1b0-4038-9b06-26c73669d7d1).
- **Autor exibido:** Gustavo Pelissari Oenning.
- **Gravação:** 15/11/2026, 19:09 BRT; duração de 58 s.
- **Revisão:** 15/11/2026.
- **Caso:** [CT-RF51](../../Cenario_Teste/CT-RF51_Relatorio_Contas_Receber.md).
- **Defeito:** [BUG-022](../../Relatorio-de-Bugs.md#bug-022), em triagem.
- **Ambiente:** https://sifit.centrion.com.br/relatorios; Chrome 157.0.8103.78, Windows 11 (x86), janela 1920 × 911.

## Resultado e origem

O PDF `relatorio (6).pdf` abre e lista três contas pendentes (Aluno Demonstracao Manual Sifit, Rafael Testeira e Marcelo Longo Zandonadi), mas a coluna Valor a Receber apresenta "----" nas três linhas; o rodapé informa "Quantidade de registros: 3" e "Valor Recebido: R$ 0,00".

**Status:** Reprovado nas evidências — Valor a Receber ausente em todas as linhas; defeito em triagem.

## Arquivos

| Arquivo | Conteúdo | SHA-256 |
| --- | --- | --- |
| [relatorio_6_contas_receber.pdf](relatorio_6_contas_receber.pdf) | PDF com três contas e Valor a Receber "----". | `3113e9c447f0c3d9eb81d236b1aaa73cf67d01e51cea2c7be26b7d4236f7d7ae` |
| [formulario_contas_receber_00-43.png](formulario_contas_receber_00-43.png) | tipo Contas a Receber, Status Pendente. | `f74919c5d905ed611fd23150892816efc767a7fbbbde87fdb092122516552b92` |
| [rede_lista.png](rede_lista.png) | oito POST relatorio (HTTP 200) e um OPTIONS. | `ecd2414b90cbba8bf93464a4691473a1881f9089b4d3a45cd6d145f309dba798` |
| [relatorio_6_contas_receber_pagina1.png](relatorio_6_contas_receber_pagina1.png) | Primeira página do PDF (`relatorio (6).pdf`) renderizada para consulta; o PDF original segue no arquivo acima. | `885b3fda306153f3f4fc4b583996fff1b6b9000e6a3797f412a9ebb1bdb82acc` |
| [linha_do_tempo.txt](linha_do_tempo.txt) | Cronologia de ações, digitação e rede do Jam. | — |
| [origem.url](origem.url) | Endereço original do Jam. | — |

## Limites

Esta pasta contém documentação da consulta, capturas extraídas da reprodução do Jam e a cronologia; não contém cópia do vídeo, e nenhum hash de vídeo foi gerado. As capturas mostram o botão de reprodução do Jam sobreposto. A mesma gravação é a fonte de vários casos.

O conteúdo não foi comparado com o módulo Contas a Receber; a opção Detalhado, outros status e o conteúdo da resposta da requisição não foram exercitados ou capturados.

Não houve execução da aplicação, inspeção de código, acesso ao banco ou reteste nesta revisão.
