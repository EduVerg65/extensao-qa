# Evidência — CT-RF114: Limpar os filtros de Modelos de Ficha

- **Fonte:** [Jam original](https://jam.dev/c/297eec2b-7be4-498b-a0e6-e962ed93cc00).
- **Autor exibido:** Pedro Figueiredo.
- **Gravação:** 16/11/2026, 22:29:07 BRT, com duração de 14,95 s.
- **Revisão:** 17/11/2026.
- **Caso:** [CT-RF114](../../Cenario_Teste/CT-RF114_Limpeza_Filtros_Modelos_Ficha.md).
- **Defeito:** nenhum no fluxo avaliado.
- **Ambiente:** https://sifit.centrion.com.br/fichas-treino-modelo · Chrome 157.0.8103.79, Windows 10 (x86), vídeo de 1918 × 998.

## Resultado e origem

O usuário apagou manualmente Criador, Título e Código. Os três campos voltaram a mostrar suas indicações de preenchimento e o botão de busca permaneceu disponível. Não houve requisição capturada durante a limpeza. Os cliques posteriores iniciaram a consulta com todos os filtros vazios.

**Status:** Aprovado conforme a gravação.

## Arquivos

| Arquivo | Conteúdo | SHA-256 |
| --- | --- | --- |
| [filtros_preenchidos_00-03.jpg](filtros_preenchidos_00-03.jpg) | Valores inicialmente preenchidos. | `3d214b31d4a8e96e5f0588eea4c20926af3d7d86c05124869227ac5cae44a4c1` |
| [filtros_limpos_00-11.jpg](filtros_limpos_00-11.jpg) | Campos vazios antes de acionar Buscar. | `5a29fbd7aad17894710f303691381fcdd3e701ef10fcfdd0786c561f4d448a12` |
| [linha_do_tempo.txt](linha_do_tempo.txt) | Cronologia de ações, rede e quadros consultados no Jam. | — |
| [origem.url](origem.url) | Endereço do Jam original. | — |

## Limites

Esta pasta contém a cronologia, a origem e os recortes dos quadros consultados. O vídeo permanece no Jam. A mesma gravação é a fonte dos CT-RF114 e CT-RF115.

Este cenário cobre a limpeza dos campos. A recuperação dos resultados em uma base populada faz parte do cenário de nova busca.

A revisão se limita ao material gravado. A execução do sistema para as verificações complementares está prevista no caso de teste.
