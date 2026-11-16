# Evidência — CT-RF59: Busca de leads por texto na tela Prospecção

- **Fonte:** [Jam original](https://jam.dev/c/308607ff-8abc-40af-8c7c-429ce506ed64).
- **Autor exibido:** Gustavo Pelissari Oenning.
- **Gravação:** 15/11/2026, 21:52 BRT; duração de 1 min 2 s.
- **Revisão:** 15/11/2026.
- **Caso:** [CT-RF59](../../Cenario_Teste/CT-RF59_Busca_Leads_Prospeccao.md).
- **Defeito:** nenhum no fluxo avaliado.
- **Ambiente:** https://sifit.centrion.com.br/prospeccao; Chrome 157.0.8103.78, Windows 11 (x86), janela 1920 × 911.

## Resultado e origem

A busca por texto reduz a listagem a subconjuntos coerentes com o termo (códigos 3 e 7 em 0:12; códigos 4 e 10 com "tes" em 0:44) e a listagem completa volta com o campo vazio; a busca não gera requisição de rede.

**Status:** Aprovado conforme a gravação.

## Arquivos

| Arquivo | Conteúdo | SHA-256 |
| --- | --- | --- |
| [busca_texto_00-12.png](busca_texto_00-12.png) | dois leads (códigos 3 e 7) de 7. | `3aa632fa464c7f6d0422f976e713ff49a382884f4eb17e07d001fb474b86a34c` |
| [busca_tes_00-44.png](busca_tes_00-44.png) | leads 4 e 10, com os cartões Leads 8 e Interessados 3. | `53e5132c18f69c7a1f2476aa21d1b773e3fa823178f49f64f032fd64d75b9af0` |
| [rede_lista.jpg](rede_lista.jpg) | 16 entradas da gravação, sem requisição de busca. | `086e2ef346f296db2a43a6e695d9ae73ca4e84b7afb12f71364230da20f4bc52` |
| [linha_do_tempo.txt](linha_do_tempo.txt) | Cronologia de ações, digitação e rede do Jam. | — |
| [origem.url](origem.url) | Endereço original do Jam. | — |

## Limites

Esta pasta contém documentação da consulta, capturas extraídas da reprodução do Jam e a cronologia; não contém cópia do vídeo, e nenhum hash de vídeo foi gerado. As capturas mostram o botão de reprodução do Jam sobreposto. A mesma gravação é a fonte de vários casos.

Não foram confirmados o termo vigente em 0:12, a regra de correspondência, a busca por e-mail, telefone e código e o resultado vazio. A filtragem local não foi confirmada.

Não houve execução da aplicação, inspeção de código, acesso ao banco ou reteste nesta revisão.
