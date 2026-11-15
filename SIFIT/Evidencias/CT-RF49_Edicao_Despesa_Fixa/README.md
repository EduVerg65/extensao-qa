# Evidência — CT-RF49: Edição de despesa fixa

- **Fonte:** [Jam original](https://jam.dev/c/a4bac99d-e436-4792-831e-8c3a875272bb).
- **Autor exibido:** Gustavo Pelissari Oenning.
- **Gravação:** 15/11/2026, 19:07 BRT; duração de 52 s.
- **Revisão:** 15/11/2026.
- **Caso:** [CT-RF49](../../Cenario_Teste/CT-RF49_Edicao_Despesa_Fixa.md).
- **Defeito:** nenhum no fluxo avaliado.
- **Ambiente:** https://sifit.centrion.com.br/despesas-fixas; Chrome 157.0.8103.78, Windows 11 (x86), janela 1920 × 911.

## Resultado e origem

Em 0:46, a ação sobre a despesa 7 gera `POST /api/seleciona/despesa-fixa/1` e abre o formulário Editar Despesa; em 0:49, Salvar Despesa envia `POST /api/edita/despesa-fixa/1` com a recorrência "7 dias" e HTTP 200. Em 0:51 a listagem exibe a despesa 7 com a recorrência "7 Dias" e a contagem de despesas permanece 16.

**Status:** Aprovado conforme a gravação.

## Arquivos

| Arquivo | Conteúdo | SHA-256 |
| --- | --- | --- |
| [editar_despesa_00-48.png](editar_despesa_00-48.png) | formulário Editar Despesa da despesa 7. | `c01d82f016d1a9aac6de00e3a869f289de634c567cd2ae0c5a0f24ebf638609d` |
| [lista_final_00-51.png](lista_final_00-51.png) | #7 "teste 323" com recorrência "7 Dias". | `530380c92c1ece208704aa855c1b4eb61ec950578d210f6179392b47fc45c2b6` |
| [resposta_seleciona.png](resposta_seleciona.png) | dados da despesa 7 retornados para o formulário. | `9f865959777aa556a337340e13f00eef656ff58c83c117dff3f3b2942812aa15` |
| [requisicao_editar.png](requisicao_editar.png) | corpo com recorrência "7 dias". | `e30579a2b2981d1f41c6b8c61304f34fb18a2bb982a9e394e1beba5fc42dfdf8` |
| [resposta_editar.png](resposta_editar.png) | verifica_erro false. | `ba9774992f9f7977cad09bd07a9280f575eda8ee775b149ce3660f75449aa3da` |
| [linha_do_tempo.txt](linha_do_tempo.txt) | Cronologia de ações, digitação e rede do Jam. | — |
| [origem.url](origem.url) | Endereço original do Jam. | — |

## Limites

Esta pasta contém documentação da consulta, capturas extraídas da reprodução do Jam e a cronologia; não contém cópia do vídeo, e nenhum hash de vídeo foi gerado. As capturas mostram o botão de reprodução do Jam sobreposto. A mesma gravação é a fonte de vários casos.

Não foram confirmados a persistência após recarga, o pré-preenchimento da recorrência, a mensagem de confirmação e a edição de outros campos.

Não houve execução da aplicação, inspeção de código, acesso ao banco ou reteste nesta revisão.
