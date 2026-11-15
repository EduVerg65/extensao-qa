# Evidência — CT-RF48: Exclusão de despesa fixa com confirmação

- **Fonte:** [Jam original](https://jam.dev/c/a4bac99d-e436-4792-831e-8c3a875272bb).
- **Autor exibido:** Gustavo Pelissari Oenning.
- **Gravação:** 15/11/2026, 19:07 BRT; duração de 52 s.
- **Revisão:** 15/11/2026.
- **Caso:** [CT-RF48](../../Cenario_Teste/CT-RF48_Exclusao_Despesa_Fixa.md).
- **Defeito:** nenhum no fluxo avaliado.
- **Ambiente:** https://sifit.centrion.com.br/despesas-fixas; Chrome 157.0.8103.78, Windows 11 (x86), janela 1920 × 911.

## Resultado e origem

Em 0:44–0:45, a lixeira da despesa 23 abre o diálogo "Deseja excluir a despesa fixa?"; após Confirmar, `POST /api/deleta/despesa-fixa/1` (corpo `{"id": 23}`) retorna HTTP 200 com `{"verifica_erro": false}` e a listagem passa de 17 para 16 despesas, de 2 para 1 inativa.

**Status:** Aprovado conforme a gravação.

## Arquivos

| Arquivo | Conteúdo | SHA-256 |
| --- | --- | --- |
| [confirmar_exclusao_00-44.png](confirmar_exclusao_00-44.png) | diálogo de confirmação "Deseja excluir a despesa fixa?". | `8ca6a0978f522a612cff6e8f95f53a47cffff4ae016f0a1e752120292ced8c3c` |
| [lista_final_00-51.png](lista_final_00-51.png) | 16 despesas e Valor Listado R$ 100,00 após a exclusão. | `530380c92c1ece208704aa855c1b4eb61ec950578d210f6179392b47fc45c2b6` |
| [requisicao_deletar.png](requisicao_deletar.png) | corpo {"id": 23}. | `9b6905cb94c76dc526deecd39a4f2ab7567061a1c8470afb8020d68edcf54122` |
| [resposta_deletar.png](resposta_deletar.png) | verifica_erro false. | `02689f07f3147da763f8f1ffc557aded104069867fbecfa929fde2f1f09e778a` |
| [linha_do_tempo.txt](linha_do_tempo.txt) | Cronologia de ações, digitação e rede do Jam. | — |
| [origem.url](origem.url) | Endereço original do Jam. | — |

## Limites

Esta pasta contém documentação da consulta, capturas extraídas da reprodução do Jam e a cronologia; não contém cópia do vídeo, e nenhum hash de vídeo foi gerado. As capturas mostram o botão de reprodução do Jam sobreposto. A mesma gravação é a fonte de vários casos.

Não foram confirmados a persistência após recarga, a natureza da exclusão, o comportamento de Cancelar e a exclusão com vínculos.

Não houve execução da aplicação, inspeção de código, acesso ao banco ou reteste nesta revisão.
