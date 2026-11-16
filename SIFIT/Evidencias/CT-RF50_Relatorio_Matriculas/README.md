# Evidência — CT-RF50: Relatório de Matrículas em PDF

- **Fonte:** [Jam original](https://jam.dev/c/3b4777a4-e1b0-4038-9b06-26c73669d7d1).
- **Autor exibido:** Gustavo Pelissari Oenning.
- **Gravação:** 15/11/2026, 19:09 BRT; duração de 58 s.
- **Revisão:** 15/11/2026.
- **Caso:** [CT-RF50](../../Cenario_Teste/CT-RF50_Relatorio_Matriculas.md).
- **Defeito:** nenhum no fluxo avaliado.
- **Ambiente:** https://sifit.centrion.com.br/relatorios; Chrome 157.0.8103.78, Windows 11 (x86), janela 1920 × 911.

## Resultado e origem

O PDF `relatorio (5).pdf` abre e apresenta "Relatório de Matrículas" com Data Inicial 01/11/2026 e Data Final 15/11/2026 e uma linha (Aluno Demonstracao Manual Sifit, Plano Diário, Treino Livre, 11/11/2026 a 11/11/2026, R$ 20,00), com "Quantidade de registros: 1".

**Status:** Aprovado conforme a gravação.

## Arquivos

| Arquivo | Conteúdo | SHA-256 |
| --- | --- | --- |
| [relatorio_5_matriculas.pdf](relatorio_5_matriculas.pdf) | PDF gerado com uma matrícula (R$ 20,00). | `ee1c647227b00798b3538233b9305a73fcec2f279ee7a4a48e6e83787bc3aeec` |
| [formulario_matriculas_00-38.png](formulario_matriculas_00-38.png) | tipo Matrículas com Plano e Tipo de Pagto "Todos". | `b15b2e29dfc9059cc47806dae93b75badd134f7da898c1fc7a1b500c4e3927fe` |
| [rede_lista.png](rede_lista.png) | oito POST relatorio (HTTP 200) e um OPTIONS. | `ecd2414b90cbba8bf93464a4691473a1881f9089b4d3a45cd6d145f309dba798` |
| [linha_do_tempo.txt](linha_do_tempo.txt) | Cronologia de ações, digitação e rede do Jam. | — |
| [origem.url](origem.url) | Endereço original do Jam. | — |

## Limites

Esta pasta contém documentação da consulta, capturas extraídas da reprodução do Jam e a cronologia; não contém cópia do vídeo, e nenhum hash de vídeo foi gerado. As capturas mostram o botão de reprodução do Jam sobreposto. A mesma gravação é a fonte de vários casos.

O conteúdo não foi conferido contra a lista de matrículas do módulo; filtros de plano e de pagamento e períodos sem registros não foram exercitados.

Não houve execução da aplicação, inspeção de código, acesso ao banco ou reteste nesta revisão.
