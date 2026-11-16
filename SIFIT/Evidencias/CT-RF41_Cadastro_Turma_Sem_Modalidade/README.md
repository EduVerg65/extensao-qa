# Evidência — CT-RF41: Cadastro de turma sem modalidade selecionada em SifitBox – Turmas

- **Fonte:** [Jam original](https://jam.dev/c/ee9a133b-d6b1-442d-b4b0-dd87595b7e70).
- **Autor exibido:** Gustavo Pelissari Oenning.
- **Gravação:** 15/11/2026, 18:51 BRT; duração de 1 min 39 s.
- **Revisão:** 15/11/2026.
- **Caso:** [CT-RF41](../../Cenario_Teste/CT-RF41_Cadastro_Turma_Sem_Modalidade.md).
- **Defeito:** [BUG-020](../../Relatorio-de-Bugs.md#bug-020), em triagem.
- **Ambiente:** https://sifit.centrion.com.br/sifitbox/turmas; Chrome 157.0.8103.78, Windows 11 (x86), janela 1920 × 911.

## Resultado e origem

Com os formulários vazios (0:17–0:20) e depois com o formulário de Turma preenchido (nome "teste", horários 18:51 a 19:51, dias Dom/Seg/Ter, 12 vagas, status Ativo) mas sem modalidade selecionada (1:21–1:34), os cliques de envio não geram requisição de criação de turma e não apresentam mensagem de validação visível; o formulário permanece preenchido e a listagem mantém as quatro turmas. Em 1:34, o envio do formulário de Modalidade cria a modalidade "teste" (ver CT-RF39).

A edição da turma de id 4 (0:57–1:06) gera `POST /api/sifitbox/turmas/atualizar/1` com HTTP 200; a resposta retorna a turma com `updated_at` 2026-11-15 21:51:03 e status "inativo".

Nas 35 entradas da aba Network não há requisição de criação de turma; há um POST de atualização de turma (278 B) e um de criação de modalidade (HTTP 201).

**Status:** Reprovado nas evidências — sem feedback de validação visível; BUG-020 em triagem.

## Arquivos

| Arquivo | Conteúdo | SHA-256 |
| --- | --- | --- |
| [formulario_turma_01-29.png](formulario_turma_01-29.png) | Formulário de Turma com nome "teste", modalidade em branco e nenhum dia marcado, em 1:29. | `6ccec6f845c121e9c0c9a90c4a8cccbe160bd9d238a5002682527e81e2bfd76c` |
| [formulario_turma_01-33.png](formulario_turma_01-33.png) | Formulário de Turma com os dias Dom/Seg/Ter marcados e o cursor sobre o botão Turma, em 1:33. | `adc38c053694e3e61668135a5617c96c71c6ace11035f8b4db3bbb36bf9e8bb5` |
| [lista_apos_tentativa_01-35.png](lista_apos_tentativa_01-35.png) | Listagens após as tentativas, em 1:35: quatro turmas e a modalidade "teste". | `a2ef7fe69183e496c95545a85c66972e19b7fbe5c35000383d7c0dc90124b9a2` |
| [edicao_turma_00-58.png](edicao_turma_00-58.png) | Formulário de Turma carregado pela edição da turma de id 4, em 0:58. | `28447367472860a10d6d055da8e71ed7cd16cfac1242abe09b11ce5ded4f1682` |
| [requisicao_atualizar.png](requisicao_atualizar.png) | Corpo da requisição de atualização da turma de id 4. | `a96d0eace9f37a0b836942502849e24ce74cba53e6e583a7e18901726b39d176` |
| [resposta_atualizar.png](resposta_atualizar.png) | Resposta de atualização: turma id 4, status "inativo", updated_at 2026-11-15 21:51:03. | `9c30da5afeaaf9be13f9b3a26d989a5c77ea5e84d43a7500ba39b40bd56d271d` |
| [linha_do_tempo.txt](linha_do_tempo.txt) | Cronologia de ações, digitação e rede do Jam. | — |
| [origem.url](origem.url) | Endereço original do Jam. | — |

## Limites

Esta pasta contém documentação da consulta, capturas extraídas da reprodução do Jam e a cronologia; não contém cópia do vídeo, e nenhum hash de vídeo foi gerado. As capturas mostram o botão de reprodução do Jam sobreposto. A mesma gravação é a fonte de CT-RF39, CT-RF40 e CT-RF41.

Não foi confirmado se a modalidade é obrigatória nem se há validação nativa do navegador (balões de validação normalmente não aparecem em gravações de tela). O botão acionado em 1:17 e em 1:28 não foi identificado nos quadros; o cursor sobre o botão Turma é visível em 0:19 e em 1:33. A causa técnica e a persistência não foram confirmadas.

Não houve execução da aplicação, inspeção de código, acesso ao banco ou reteste nesta revisão.
