# Evidência — CT-RF46: Filtros da tela Despesas Fixas por código e por nome

- **Fonte:** [Jam original](https://jam.dev/c/a4bac99d-e436-4792-831e-8c3a875272bb).
- **Autor exibido:** Gustavo Pelissari Oenning.
- **Gravação:** 15/11/2026, 19:07 BRT; duração de 52 s.
- **Revisão:** 15/11/2026.
- **Caso:** [CT-RF46](../../Cenario_Teste/CT-RF46_Filtros_Despesas_Fixas.md).
- **Defeito:** nenhum no fluxo avaliado.
- **Ambiente:** https://sifit.centrion.com.br/despesas-fixas; Chrome 157.0.8103.78, Windows 11 (x86), janela 1920 × 911.

## Resultado e origem

Os filtros por código ("1") e por nome ("Teste") retornam conjuntos coerentes, com o cartão Valor Listado acompanhando o conjunto exibido (R$ 7.626,00 e R$ 100,00) e a listagem completa restaurada ao limpar os campos (R$ 8.060,00). Os filtros não geram requisição de rede.

**Status:** Aprovado conforme a gravação.

## Arquivos

| Arquivo | Conteúdo | SHA-256 |
| --- | --- | --- |
| [filtro_codigo_00-03.png](filtro_codigo_00-03.png) | códigos 10 a 19 com Valor Listado R$ 7.626,00. | `65c559d19e0ac5e783e2a90e2913f0689e185656e36925d53a5446a4ce1705ca` |
| [filtro_nome_00-11.png](filtro_nome_00-11.png) | duas linhas (#5 e #7) com Valor Listado R$ 100,00. | `2aa82d9df7c63d6e9e040692de8bfa71a437126da39e5f730b98fc33b8fdafff` |
| [lista_completa_00-19.png](lista_completa_00-19.png) | 16 despesas e Valor Listado R$ 8.060,00. | `7fff932cc3a62eb08cc388ac9e446f1f5679585e750d1a5695e3709055b8e652` |
| [filtro_teste_00-42.png](filtro_teste_00-42.png) | três linhas (#5, #7 e #23) com Valor Listado R$ 250,00. | `4dfb1e79d948bc3b57d68f201faa67e23f49eb52ee5c84baea13a14613d9e536` |
| [rede_lista.png](rede_lista.png) | 16 entradas da gravação, sem requisições de filtro. | `e6bc25d7469c63b56e9171d9a355d8b2a98eaf7b46c4b441a6b87c5340ae84f8` |
| [linha_do_tempo.txt](linha_do_tempo.txt) | Cronologia de ações, digitação e rede do Jam. | — |
| [origem.url](origem.url) | Endereço original do Jam. | — |

## Limites

Esta pasta contém documentação da consulta, capturas extraídas da reprodução do Jam e a cronologia; não contém cópia do vídeo, e nenhum hash de vídeo foi gerado. As capturas mostram o botão de reprodução do Jam sobreposto. A mesma gravação é a fonte de vários casos.

Não foram confirmados o contrato dos cartões, a regra de correspondência do código, a combinação de critérios e o resultado vazio. A filtragem local não foi confirmada.

Não houve execução da aplicação, inspeção de código, acesso ao banco ou reteste nesta revisão.
