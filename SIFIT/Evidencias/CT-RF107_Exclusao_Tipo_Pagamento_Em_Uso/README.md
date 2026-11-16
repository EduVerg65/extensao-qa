# Evidência — CT-RF107: Exclusão de tipo de pagamento em uso retorna HTTP 404 com erro SQL

- **Fonte:** [Jam original](https://jam.dev/c/e8734e3d-3f8e-458b-8c7d-e85eea882e50).
- **Autor exibido:** Gustavo Pelissari Oenning.
- **Gravação:** 15/11/2026, 22:03 BRT; duração de 1 min.
- **Revisão:** 15/11/2026.
- **Caso:** [CT-RF107](../../Cenario_Teste/CT-RF107_Exclusao_Tipo_Pagamento_Em_Uso.md).
- **Defeito:** [BUG-043](../../Relatorio-de-Bugs.md#bug-043), em triagem.
- **Ambiente:** https://sifit.centrion.com.br/tipos-pagamento; Chrome 157.0.8103.78, Windows 11 (x86), janela 1920 × 855.

## Resultado e origem

As duas exclusões (códigos 1 e 3) retornaram HTTP 404 com o erro SQL de violação de chave estrangeira e a tela exibiu apenas "Erro ao deletar tipo de pagamento", mantendo a listagem com 17 tipos.

**Status:** Reprovado nas evidências — exclusão de tipo em uso retorna HTTP 404 com erro SQL; defeito em triagem.

## Arquivos

| Arquivo | Conteúdo | SHA-256 |
| --- | --- | --- |
| [dialogo_confirmar_00-37.jpg](dialogo_confirmar_00-37.jpg) | Deseja deletar o Tipo de Pagamento? | `3e47797de2b7a00e512723f598e8ec1b2cf983fcc40a384803b32bddcd0ffab8` |
| [erro_exclusao_00-40.jpg](erro_exclusao_00-40.jpg) | Erro ao deletar tipo de pagamento. | `f9281f458d3b279e76ffdc1623d96dbd15ea33f8b37f41ed2cc2abf7b6fc47af` |
| [dialogo_segundo_00-43.jpg](dialogo_segundo_00-43.jpg) | segundo tipo (código 3). | `badac121b250ea29daad673db0bf07fbd67416b8db2fd61aa531f4e976f595b5` |
| [lista_apos_erro_00-45.jpg](lista_apos_erro_00-45.jpg) | Total 17 inalterado após as duas falhas. | `1e546b356818774a720bd800dc89e46096c14278b493e8b1a345033f90e966ea` |
| [rede_lista.jpg](rede_lista.jpg) | 18 entradas da gravação (POST, OPTIONS, GET e temas), com os dois POST deleta em HTTP 404. | `b38c881654bd91b7766e435bfc261119bb28f40499de148cf2ec0b156fbcad6d` |
| [linha_do_tempo.txt](linha_do_tempo.txt) | Cronologia de ações, digitação e rede do Jam. | — |
| [origem.url](origem.url) | Endereço original do Jam. | — |

## Limites

Esta pasta contém documentação da consulta, capturas extraídas da reprodução do Jam e a cronologia; não contém cópia do vídeo, e nenhum hash de vídeo foi gerado. As capturas são quadros do vídeo e incluem a barra de gravação do Jam. A mesma gravação é a fonte de vários casos.

Não foram confirmados a regra de exclusão, a exclusão de um tipo sem uso e o vínculo efetivo com contas a receber.

Não houve execução da aplicação, inspeção de código, acesso ao banco ou reteste nesta revisão.
