# Evidência — CT-RF47: Cadastro de despesa fixa com duas requisições de criação

- **Fonte:** [Jam original](https://jam.dev/c/a4bac99d-e436-4792-831e-8c3a875272bb).
- **Autor exibido:** Gustavo Pelissari Oenning.
- **Gravação:** 15/11/2026, 19:07 BRT; duração de 52 s.
- **Revisão:** 15/11/2026.
- **Caso:** [CT-RF47](../../Cenario_Teste/CT-RF47_Cadastro_Despesa_Fixa.md).
- **Defeito:** nenhum confirmado; ponto a validar.
- **Ambiente:** https://sifit.centrion.com.br/despesas-fixas; Chrome 157.0.8103.78, Windows 11 (x86), janela 1920 × 911.

## Resultado e origem

Em 0:35, um único clique em Salvar Despesa (Nome "teste gg", Status Inativo, Valor 150, Recorrência "1 Dia") gera dois `POST /api/cria/despesa-fixa/1` com HTTP 201; a primeira resposta retorna `id` 23. A listagem passa de 16 para 17 despesas, com a despesa 23 visível no filtro por nome.

**Status:** A validar — regra ou contexto pendente.

## Arquivos

| Arquivo | Conteúdo | SHA-256 |
| --- | --- | --- |
| [modal_nova_despesa_00-34.png](modal_nova_despesa_00-34.png) | formulário Nova Despesa preenchido (teste gg, Inativo, 150, 1 Dia). | `2abdd57e1f7ed22b4c365723fe1582c6e0e027fcfb9cfeb4fcf592a21997020f` |
| [lista_apos_cadastro_00-36.png](lista_apos_cadastro_00-36.png) | 17 despesas e Valor Listado R$ 8.210,00. | `7c4e1d0392cfd416f593cffcdebb49663e167934aecdd99f6012fdb312b6b2cd` |
| [filtro_teste_00-42.png](filtro_teste_00-42.png) | #5, #7 e #23 "teste gg" (inativo). | `4dfb1e79d948bc3b57d68f201faa67e23f49eb52ee5c84baea13a14613d9e536` |
| [requisicao_criar.png](requisicao_criar.png) | corpo da primeira requisição de criação. | `c517f011b6d84091a6180e3eecd9da9407c0040f6c1d41cfbf64ca656bd47a20` |
| [resposta_criar.png](resposta_criar.png) | verifica_erro false e id 23. | `536943dc7298355ed0f2cc037114a742ca12af9a2057646e1407f8affe7de3fe` |
| [rede_lista.png](rede_lista.png) | duas entradas POST 201 para a criação. | `e6bc25d7469c63b56e9171d9a355d8b2a98eaf7b46c4b441a6b87c5340ae84f8` |
| [linha_do_tempo.txt](linha_do_tempo.txt) | Cronologia de ações, digitação e rede do Jam. | — |
| [origem.url](origem.url) | Endereço original do Jam. | — |

## Limites

Esta pasta contém documentação da consulta, capturas extraídas da reprodução do Jam e a cronologia; não contém cópia do vídeo, e nenhum hash de vídeo foi gerado. As capturas mostram o botão de reprodução do Jam sobreposto. A mesma gravação é a fonte de vários casos.

O corpo e a resposta da segunda requisição de criação estão indisponíveis. Não foram confirmados registro adicional, persistência após recarga e a regra do código.

Não houve execução da aplicação, inspeção de código, acesso ao banco ou reteste nesta revisão.
