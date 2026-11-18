# Evidência — CT-RF115: Pesquisar novamente modelos de ficha sem filtros

- **Fonte:** [Jam original](https://jam.dev/c/297eec2b-7be4-498b-a0e6-e962ed93cc00).
- **Autor exibido:** Pedro Figueiredo.
- **Gravação:** 16/11/2026, 22:29:07 BRT, com duração de 14,95 s.
- **Revisão:** 17/11/2026.
- **Caso:** [CT-RF115](../../Cenario_Teste/CT-RF115_Nova_Busca_Modelos_Ficha_Sem_Filtros.md).
- **Defeito:** nenhum confirmado. Ponto a validar.
- **Ambiente:** https://sifit.centrion.com.br/fichas-treino-modelo · Chrome 157.0.8103.79, Windows 10 (x86), vídeo de 1918 × 998.

## Resultado e origem

Com os três campos vazios, Buscar foi acionado duas vezes. As duas consultas retornaram HTTP 200 com `[]`. A interface exibiu o carregamento durante a busca e terminou com “Nenhum modelo de ficha encontrado” e 0 registros.

**Status:** A validar — regra ou contexto pendente.

## Arquivos

| Arquivo | Conteúdo | SHA-256 |
| --- | --- | --- |
| [busca_sem_filtros_carregando_00-11.jpg](busca_sem_filtros_carregando_00-11.jpg) | Busca sem filtros com indicação de carregamento. | `3871c93c2f21dd08e569da9ecf25ff6406606f2af4216278c01ff37242bc08b5` |
| [busca_sem_filtros_resultado_00-14.jpg](busca_sem_filtros_resultado_00-14.jpg) | Busca sem filtros concluída com mensagem de estado vazio. | `3b096c4de6ed942fe8aeb076d0c178edb883622eccadbc981dca5984768a922c` |
| [linha_do_tempo.txt](linha_do_tempo.txt) | Cronologia de ações, rede e quadros consultados no Jam. | — |
| [origem.url](origem.url) | Endereço do Jam original. | — |

## Limites

Esta pasta contém a cronologia, a origem e os recortes dos quadros consultados. O vídeo permanece no Jam. A mesma gravação é a fonte dos CT-RF114 e CT-RF115.

A gravação não mostra uma listagem padrão populada. O estado vazio é compatível com os retornos, mas a recuperação de registros ocultados por uma pesquisa anterior ficou a validar.

A revisão se limita ao material gravado. A execução do sistema para as verificações complementares está prevista no caso de teste.
