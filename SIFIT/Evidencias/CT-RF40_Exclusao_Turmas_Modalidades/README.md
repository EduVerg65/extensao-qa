# Evidência — CT-RF40: Exclusão (lixeira) de turmas e modalidades em SifitBox – Turmas

- **Fonte:** [Jam original](https://jam.dev/c/ee9a133b-d6b1-442d-b4b0-dd87595b7e70).
- **Autor exibido:** Gustavo Pelissari Oenning.
- **Gravação:** 15/11/2026, 18:51 BRT; duração de 1 min 39 s.
- **Revisão:** 15/11/2026.
- **Caso:** [CT-RF40](../../Cenario_Teste/CT-RF40_Exclusao_Turmas_Modalidades.md).
- **Defeito:** nenhum confirmado; ponto a validar.
- **Ambiente:** https://sifit.centrion.com.br/sifitbox/turmas; Chrome 157.0.8103.78, Windows 11 (x86), janela 1920 × 911.

## Resultado e origem

Entre 1:00 e 1:05, os cliques na lixeira geram quatro `POST /api/sifitbox/turmas/excluir/1` e cinco `POST /api/sifitbox/modalidades/excluir/1`, todos com HTTP 200 e resposta `{"erro": false}`. Nos quadros de 1:00 e 1:05 não há diálogo de confirmação e as quatro turmas e as três modalidades continuam na listagem. As listas retornadas apresentam todas as turmas e modalidades com `"status": "inativo"`; a turma de id 4 tem `updated_at` 2026-11-15 21:50:58 e as modalidades 2026-11-15 21:51:00 e 21:51:01.

A aba Network tem 35 entradas, todas com HTTP 200, 201 ou 204. Após cada exclusão há `GET` de modalidades (535 B) e de turmas (1341 B), com tamanho constante, compatível com listas de mesmo número de registros.

**Status:** A validar — regra ou contexto pendente.

## Arquivos

| Arquivo | Conteúdo | SHA-256 |
| --- | --- | --- |
| [lixeira_01-00.png](lixeira_01-00.png) | Cursor sobre a lixeira da primeira turma, sem diálogo de confirmação, em 1:00. | `3e42029e41364f78dcbf0cf8955d9da7b84febe338294abb6351396c1b7d8478` |
| [lista_apos_exclusoes_01-05.png](lista_apos_exclusoes_01-05.png) | Listagens de modalidades e turmas após as exclusões, em 1:05. | `48d03242a63bfd883625fd59348f9521a41ce8a07d46b7662e13ababf26d3f7f` |
| [requisicao_excluir_turma.png](requisicao_excluir_turma.png) | Cabeçalhos de uma exclusão de turma: POST turmas/excluir/1, HTTP 200. | `68c61928d425439acd43b6d3fe32cfa470aab1742faab8631d9e67cb181fbad4` |
| [requisicao_excluir_modalidade.png](requisicao_excluir_modalidade.png) | Cabeçalhos de uma exclusão de modalidade: POST modalidades/excluir/1, HTTP 200. | `64f70709dc43c78fb97cba9450922d799f3ef8f398b81c3f1f0d35fae4d0728b` |
| [resposta_excluir.png](resposta_excluir.png) | Resposta de uma exclusão: {"erro": false}. | `8c9528074345376f0ecd23244bc115552712201e21ba0bde01bec1298b148bf6` |
| [linha_do_tempo.txt](linha_do_tempo.txt) | Cronologia de ações, digitação e rede do Jam. | — |
| [origem.url](origem.url) | Endereço original do Jam. | — |

## Limites

Esta pasta contém documentação da consulta, capturas extraídas da reprodução do Jam e a cronologia; não contém cópia do vídeo, e nenhum hash de vídeo foi gerado. As capturas mostram o botão de reprodução do Jam sobreposto. A mesma gravação é a fonte de CT-RF39, CT-RF40 e CT-RF41.

Não foram confirmados a regra de exclusão lógica, a necessidade de confirmação prévia, o efeito sobre turmas vinculadas a uma modalidade inativada, a correspondência exata entre cada clique e cada requisição e a persistência após recarga. Os corpos das requisições de exclusão não foram inspecionados.

Não houve execução da aplicação, inspeção de código, acesso ao banco ou reteste nesta revisão.
