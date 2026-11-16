# Evidência — CT-RF60: Filtro de leads por estágio e limpeza dos filtros

- **Fonte:** [Jam original](https://jam.dev/c/308607ff-8abc-40af-8c7c-429ce506ed64).
- **Autor exibido:** Gustavo Pelissari Oenning.
- **Gravação:** 15/11/2026, 21:52 BRT; duração de 1 min 2 s.
- **Revisão:** 15/11/2026.
- **Caso:** [CT-RF60](../../Cenario_Teste/CT-RF60_Filtro_Estagio_Leads.md).
- **Defeito:** nenhum no fluxo avaliado.
- **Ambiente:** https://sifit.centrion.com.br/prospeccao; Chrome 157.0.8103.78, Windows 11 (x86), janela 1920 × 911.

## Resultado e origem

O filtro por estágio apresenta os leads de Novo Contato (códigos 7 e 8, coerente com o indicador Novos Contatos = 2) e de Proposta (código 4), e o botão Limpar restaura o seletor em Todos e a listagem completa; o filtro não gera requisição de rede.

**Status:** Aprovado conforme a gravação.

## Arquivos

| Arquivo | Conteúdo | SHA-256 |
| --- | --- | --- |
| [filtro_novo_contato_00-16.png](filtro_novo_contato_00-16.png) | leads de códigos 7 e 8. | `fdcdaee8a6b55e317d8502efedb289c1057ab7d10fcd3f3fa00cce101224edf1` |
| [filtro_proposta_00-19.png](filtro_proposta_00-19.png) | um lead (código 4). | `d6ca3245f7bbfa6fccbf0cf55bcc212c4bb1773928a32f211037dc845160cd91` |
| [lista_apos_limpar_00-21.png](lista_apos_limpar_00-21.png) | 7 leads, seletor em Todos. | `68d41d0f3e34072296c55b92b52c8a48035f55b3fdca0b4d3b4a0f5731a3f4e6` |
| [rede_lista.jpg](rede_lista.jpg) | 16 entradas da gravação, sem requisição de filtro. | `086e2ef346f296db2a43a6e695d9ae73ca4e84b7afb12f71364230da20f4bc52` |
| [linha_do_tempo.txt](linha_do_tempo.txt) | Cronologia de ações, digitação e rede do Jam. | — |
| [origem.url](origem.url) | Endereço original do Jam. | — |

## Limites

Esta pasta contém documentação da consulta, capturas extraídas da reprodução do Jam e a cronologia; não contém cópia do vídeo, e nenhum hash de vídeo foi gerado. As capturas mostram o botão de reprodução do Jam sobreposto. A mesma gravação é a fonte de vários casos.

Não foram confirmados os demais estágios, a combinação com a busca por texto, o estágio sem leads e a filtragem local.

Não houve execução da aplicação, inspeção de código, acesso ao banco ou reteste nesta revisão.
