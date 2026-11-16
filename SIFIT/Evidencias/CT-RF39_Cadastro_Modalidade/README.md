# Evidência — CT-RF39: Cadastro de modalidade em SifitBox – Turmas

- **Fonte:** [Jam original](https://jam.dev/c/ee9a133b-d6b1-442d-b4b0-dd87595b7e70).
- **Autor exibido:** Gustavo Pelissari Oenning.
- **Gravação:** 15/11/2026, 18:51 BRT; duração de 1 min 39 s.
- **Revisão:** 15/11/2026.
- **Caso:** [CT-RF39](../../Cenario_Teste/CT-RF39_Cadastro_Modalidade.md).
- **Defeito:** nenhum no fluxo avaliado.
- **Ambiente:** https://sifit.centrion.com.br/sifitbox/turmas; Chrome 157.0.8103.78, Windows 11 (x86), janela 1920 × 911.

## Resultado e origem

Em 1:33–1:34, o envio do formulário de Modalidade (Nome "teste", Descrição "teste", status Ativo) gera `POST https://backendsifit.centrion.com.br/api/sifitbox/modalidades/salvar/1` com HTTP 201 e o corpo `{"id": {}, "nome": "teste", "descricao": "teste", "status": "ativo"}`. A resposta retorna a modalidade de id 4, com `created_at` 2026-11-15 21:51:31. Em 1:35 a listagem passa de três para quatro modalidades, com "teste" como "ativo", e o formulário de Modalidade fica vazio.

A aba Network da gravação tem 35 entradas, todas com HTTP 200, 201 ou 204. Os GET de listas (535 B e 1341 B) atualizam as tabelas após cada operação.

**Status:** Aprovado conforme a gravação.

## Arquivos

| Arquivo | Conteúdo | SHA-256 |
| --- | --- | --- |
| [formulario_modalidade_01-17.png](formulario_modalidade_01-17.png) | Formulário de Modalidade com Nome e Descrição "teste", em 1:17. | `68332f2089c2be7bd8e9c1d1e7b00df5ab7c3799160e1fb5fe7da8ffcf93289e` |
| [lista_apos_cadastro_01-35.png](lista_apos_cadastro_01-35.png) | Listagem com quatro modalidades, incluindo "teste" (ativo), em 1:35. | `a2ef7fe69183e496c95545a85c66972e19b7fbe5c35000383d7c0dc90124b9a2` |
| [requisicao_salvar.png](requisicao_salvar.png) | Corpo da requisição de criação da modalidade. | `96fb39692f0cae4409d24ab82cda601f495c0e3f0dbeb0eeb8edcced72f37bf6` |
| [resposta_salvar.png](resposta_salvar.png) | Resposta de criação: id 4, status "ativo", created_at 2026-11-15 21:51:31. | `2e90976133aa36df994ef7535c385437fc737c0c91cb7eccc492ac73271a86bb` |
| [linha_do_tempo.txt](linha_do_tempo.txt) | Cronologia de ações, digitação e rede do Jam. | — |
| [origem.url](origem.url) | Endereço original do Jam. | — |

## Limites

Esta pasta contém documentação da consulta, capturas extraídas da reprodução do Jam e a cronologia; não contém cópia do vídeo, e nenhum hash de vídeo foi gerado. As capturas mostram o botão de reprodução do Jam sobreposto. A mesma gravação é a fonte de CT-RF39, CT-RF40 e CT-RF41.

Não foram confirmados a persistência após recarga, a mensagem de confirmação, a regra do status e o contrato da API. O botão exato acionado em 1:33 e em 1:34 não foi identificado com certeza nos quadros; a associação do envio à modalidade apoia-se no corpo da requisição.

Não houve execução da aplicação, inspeção de código, acesso ao banco ou reteste nesta revisão.
