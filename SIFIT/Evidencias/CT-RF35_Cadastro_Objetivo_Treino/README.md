# Evidência — CT-RF35: Cadastro de objetivo de treino retorna HTTP 500

- **Fonte:** [Jam original](https://jam.dev/c/1d474477-2411-4a81-b85c-74207402b783).
- **Autor exibido:** Gustavo Pelissari Oenning.
- **Gravação:** 15/11/2026, 18:13 BRT; duração de 1 min 12 s.
- **Revisão:** 15/11/2026.
- **Caso:** [CT-RF35](../../Cenario_Teste/CT-RF35_Cadastro_Objetivo_Treino.md).
- **Defeito:** [BUG-018](../../Relatorio-de-Bugs.md#bug-018), em triagem.
- **Ambiente:** https://sifit.centrion.com.br/objetivos-treino; Chrome 157.0.8103.78, Windows 11 (x86), janela 1920 × 911.

## Resultado e origem

Ao clicar em Salvar no formulário "Objetivo" (nome Gustavo, descrição Gustavo 45254#@v), `POST https://backendsifit.centrion.com.br/api/objetivo-treino/salvar/1` retorna HTTP 500. O sistema apresenta o diálogo "Erro" / "Erro ao salvar objetivo" e a listagem continua sem registros.

A aba Network apresenta nove entradas: quatro POST `tema` com HTTP 200, dois GET com HTTP 200 (2 B), um POST com HTTP 500 (1077 ms), um OPTIONS com HTTP 204 e um segundo POST com HTTP 500 (856 ms). O corpo da requisição e da resposta aparece como indisponível no Jam.

**Status:** Reprovado nas evidências.

## Arquivos

| Arquivo | Conteúdo | SHA-256 |
| --- | --- | --- |
| [formulario_codigo_vazio_00-46.png](formulario_codigo_vazio_00-46.png) | Formulário "Objetivo" em 0:46, com o campo Código focado e vazio. | `be7fb613152a958da6e9c9bf7cd66f1a3db1c55748a23cc44d49c637f25b3818` |
| [formulario_preenchido_01-00.png](formulario_preenchido_01-00.png) | Formulário com nome e descrição preenchidos, em aproximadamente 1:00. | `d3eae2099f471148b25d818a5bcf45318240e185fba09ed35b8991df6ba17002` |
| [erro_01-04.png](erro_01-04.png) | Recorte do diálogo "Erro" / "Erro ao salvar objetivo", em 1:04. | `a5c4de6375c7e37c9ce5815226fd0dc4592e97de83cf6bc58f79ae2b91813df5` |
| [lista_vazia_01-11.png](lista_vazia_01-11.png) | Listagem sem registros e cartões em 0, em 1:11. | `49c552999739f67ac113fc6579e5952e4f2ec8345a654612791ad7e131da9195` |
| [rede_lista.png](rede_lista.png) | Lista de rede do Jam com as nove entradas, status, tamanhos e tempos. | `79dd5d5038effa4f143c8c7a4cb34d9898d1d387c4480b9d97a8486f80589599` |
| [linha_do_tempo.txt](linha_do_tempo.txt) | Cronologia de ações, digitação e erros de rede do Jam. | — |
| [origem.url](origem.url) | Endereço original do Jam. | — |

## Limites

Esta pasta contém documentação da consulta, capturas extraídas da reprodução do Jam e a cronologia; não contém cópia do vídeo, e nenhum hash de vídeo foi gerado. As capturas mostram o botão de reprodução do Jam sobreposto e, no diálogo de erro, o texto parcialmente coberto; a leitura "Erro ao salvar objetivo" é aproximada.

O corpo da requisição e da resposta não foi capturado pelo Jam; não é possível afirmar o payload enviado nem a mensagem retornada pelo servidor. Não foram confirmados a persistência de registros parciais, a regra do campo Código nem a razão da segunda ocorrência de HTTP 500. O console do Jam não registra mensagens de JavaScript além dos erros de rede.

Não houve execução da aplicação, inspeção de código, acesso ao banco ou reteste nesta revisão.
