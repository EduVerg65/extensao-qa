# Evidência — CT-RF38: Cadastro de categoria com código automático e consulta pelo código

- **Fonte:** [Jam original](https://jam.dev/c/be1dbd05-217d-44c3-8a3d-240b7f6344e1).
- **Autor exibido:** Gustavo Pelissari Oenning.
- **Gravação:** 15/11/2026, 18:41 BRT; duração de 37 s.
- **Revisão:** 15/11/2026.
- **Caso:** [CT-RF38](../../Cenario_Teste/CT-RF38_Cadastro_Categoria_Codigo_Automatico.md).
- **Defeito:** nenhum no fluxo avaliado.
- **Ambiente:** https://sifit.centrion.com.br/categorias-exercicios-crossfit; Chrome 157.0.8103.78, Windows 11 (x86), janela 1920 × 911.

## Resultado e origem

Em 0:27, o formulário "Cadastrar Categoria" é salvo com o nome "teste" e o campo Código vazio, mesmo após a digitação de "qwdas" em 0:25. `POST https://backendsifit.centrion.com.br/api/categoria-exercicio-cross/criar` retorna HTTP 201 com o corpo `{"nome": "teste"}` e a resposta "Categoria criada com sucesso!". Em 0:28 a listagem passa de oito para nove categorias, com o código 9 "teste", e em 0:32 o filtro Código "9" retorna apenas esse registro. Os filtros por nome ("bar", em 0:02) e por código ("8", em 0:08) retornam uma linha cada.

A aba Network apresenta cinco entradas: dois POST `tema` com HTTP 200, `OPTIONS` com HTTP 204, `POST criar` com HTTP 201 e `GET listar` com HTTP 200 (910 B). Os filtros não geram entrada de rede.

**Status:** Aprovado conforme a gravação.

## Arquivos

| Arquivo | Conteúdo | SHA-256 |
| --- | --- | --- |
| [filtro_nome_00-02.png](filtro_nome_00-02.png) | Filtro Nome "bar" em 0:02: código 1 "Barbell novo", Exibidas 1. | `08b25c6d317056e92f15d80eaf0b24083d9bb7fb35a17f39fe6dbb48ed694d82` |
| [filtro_codigo_00-08.png](filtro_codigo_00-08.png) | Filtro Código "8" em 0:08: código 8 "cardio leve", Exibidas 1. | `c0e45bd5fb3b8531a88d399a4e49f8a060b53f6e3548c83cc35765892748ae0c` |
| [formulario_codigo_vazio_00-27.png](formulario_codigo_vazio_00-27.png) | Formulário "Cadastrar Categoria" em 0:27, com Nome "teste" e Código vazio. | `5a627dd5b36e23d43843daadaf824babf07f8c84a215e982888a334e68ce3563` |
| [lista_apos_cadastro_00-28.png](lista_apos_cadastro_00-28.png) | Listagem com nove categorias e o código 9 "teste" em 0:28. | `758d66495554f83794d36852757e6b201e1e589cb792ed8aacec7456b31cb4ae` |
| [filtro_codigo_9_00-32.png](filtro_codigo_9_00-32.png) | Filtro Código "9" em 0:32: apenas o código 9 "teste". | `821627247fce5157fbad52675741fb2b896240955a25147fa02a4d8f48fbed4b` |
| [rede_lista.png](rede_lista.png) | Lista de rede do Jam com as cinco entradas. | `ee4761332d6d3373ea9ff002ad15e6e9e5f547e848f8b737edc86df472021cad` |
| [requisicao_criar.png](requisicao_criar.png) | Corpo da requisição de criação: `{"nome": "teste"}`. | `f39efbf7189817ecbf6990e6c8d4ffd0a4646659053584c3d5b4746be5e2059a` |
| [resposta_criar.png](resposta_criar.png) | Resposta de criação: `verifica_erro: false`, "Categoria criada com sucesso!". | `565900b970a39caedcb00ff992bb7a08e5f25743452c4a5e5f3b8493f8a5dbd9` |
| [linha_do_tempo.txt](linha_do_tempo.txt) | Cronologia de ações, digitação e rede do Jam. | — |
| [origem.url](origem.url) | Endereço original do Jam. | — |

## Limites

Esta pasta contém documentação da consulta, capturas extraídas da reprodução do Jam e a cronologia; não contém cópia do vídeo, e nenhum hash de vídeo foi gerado. As capturas mostram o botão de reprodução do Jam sobreposto.

Não foram confirmados a persistência após recarga, a regra do campo Código (automático ou bloqueado) e o contrato dos cartões de resumo. A ausência de requisição nos filtros é compatível com filtragem local, sem confirmação; a captura pode não incluir o carregamento inicial da página.

Não houve execução da aplicação, inspeção de código, acesso ao banco ou reteste nesta revisão.
