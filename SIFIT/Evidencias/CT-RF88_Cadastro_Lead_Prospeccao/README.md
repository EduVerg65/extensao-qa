# Evidência — CT-RF88: Cadastro de lead com duas requisições de criação

- **Fonte:** [Jam original](https://jam.dev/c/308607ff-8abc-40af-8c7c-429ce506ed64).
- **Autor exibido:** Gustavo Pelissari Oenning.
- **Gravação:** 15/11/2026, 21:52 BRT; duração de 1 min 2 s.
- **Revisão:** 15/11/2026.
- **Caso:** [CT-RF88](../../Cenario_Teste/CT-RF88_Cadastro_Lead_Prospeccao.md).
- **Defeito:** nenhum confirmado; ponto a validar.
- **Ambiente:** https://sifit.centrion.com.br/prospeccao; Chrome 157.0.8103.78, Windows 11 (x86), janela 1920 × 911.

## Resultado e origem

Um clique em Salvar Lead gerou dois POST salvar-lead/1 com HTTP 200; a primeira resposta devolveu o id 10 e a listagem apresentou um único lead novo (Leads 7 → 8; Interessados 2 → 3). Corpo e resposta da segunda chamada estão indisponíveis; não há duplicidade confirmada.

**Status:** A validar — regra ou contexto pendente.

## Arquivos

| Arquivo | Conteúdo | SHA-256 |
| --- | --- | --- |
| [modal_adicionar_00-24.png](modal_adicionar_00-24.png) | estágio Novo Contato e código Novo. | `858d44d0f9f6cb793513d4fd6881e932678e9b48c1234fdd7983b3f919535a10` |
| [lista_apos_cadastro_00-39.png](lista_apos_cadastro_00-39.png) | 8 leads, com o código 10 e os cartões Leads 8 e Interessados 3. | `763b7881da16e86442fe344b4957de5dd1f8e0ab9a73466bde0ee2964ccb22f2` |
| [requisicao_salvar.png](requisicao_salvar.png) | Corpo da requisição salvar-lead (e-mail mascarado pelo Jam). | `286064037f65110b9e494066e518c8e0bc53ab9aec18dd0c4028716b9f3b604f` |
| [resposta_salvar.png](resposta_salvar.png) | id 10. | `f63d2eab342cec2021883a851f4cf7ddcd0fd09c63c9d80aea99a6ab67f1c919` |
| [rede_lista.jpg](rede_lista.jpg) | 16 entradas, com salvar-lead, OPTIONS e o segundo POST. | `086e2ef346f296db2a43a6e695d9ae73ca4e84b7afb12f71364230da20f4bc52` |
| [linha_do_tempo.txt](linha_do_tempo.txt) | Cronologia de ações, digitação e rede do Jam. | — |
| [origem.url](origem.url) | Endereço original do Jam. | — |

## Limites

Esta pasta contém documentação da consulta, capturas extraídas da reprodução do Jam e a cronologia; não contém cópia do vídeo, e nenhum hash de vídeo foi gerado. As capturas mostram o botão de reprodução do Jam sobreposto. A mesma gravação é a fonte de vários casos.

Não foram confirmados o conteúdo da segunda requisição, a ausência de duplicidade após recarga e a validação dos campos obrigatórios. O e-mail digitado foi mascarado pelo Jam e não é reproduzido.

Não houve execução da aplicação, inspeção de código, acesso ao banco ou reteste nesta revisão.
