# Evidência — CT-RF104: Filtros de busca da tela Tipos de Pagamento

- **Fonte:** [Jam original](https://jam.dev/c/e8734e3d-3f8e-458b-8c7d-e85eea882e50).
- **Autor exibido:** Gustavo Pelissari Oenning.
- **Gravação:** 15/11/2026, 22:03 BRT; duração de 1 min.
- **Revisão:** 15/11/2026.
- **Caso:** [CT-RF104](../../Cenario_Teste/CT-RF104_Filtros_Tipos_Pagamento.md).
- **Defeito:** nenhum confirmado; ponto a validar.
- **Ambiente:** https://sifit.centrion.com.br/tipos-pagamento; Chrome 157.0.8103.78, Windows 11 (x86), janela 1920 × 855.

## Resultado e origem

Os cliques em Buscar e nos seletores Status e Tipo não emitiram requisição de listagem e a listagem permaneceu com os 16 tipos; não há resultado filtrado para avaliar a regra.

**Status:** A validar — regra ou contexto pendente.

## Arquivos

| Arquivo | Conteúdo | SHA-256 |
| --- | --- | --- |
| [lista_inicial_00-00.jpg](lista_inicial_00-00.jpg) | 16 tipos, todos Inativo, cartões Total 16, Ativos 0, Inativos 16 e Via gateway 5. | `4248e9f1669c77bff6507bbeff8ef63df748e48f459f683039ba144359bb80f3` |
| [filtros_buscar_00-14.jpg](filtros_buscar_00-14.jpg) | Buscar acionado com Status e Tipo em Todos; listagem inalterada. | `e96b49a23a8201cb944217ef2a3516e0544be13c96d4ad8e63ca8486400d54a3` |
| [rede_lista.jpg](rede_lista.jpg) | 18 entradas da gravação (POST, OPTIONS, GET e temas), com os dois POST deleta em HTTP 404. | `b38c881654bd91b7766e435bfc261119bb28f40499de148cf2ec0b156fbcad6d` |
| [linha_do_tempo.txt](linha_do_tempo.txt) | Cronologia de ações, digitação e rede do Jam. | — |
| [origem.url](origem.url) | Endereço original do Jam. | — |

## Limites

Esta pasta contém documentação da consulta, capturas extraídas da reprodução do Jam e a cronologia; não contém cópia do vídeo, e nenhum hash de vídeo foi gerado. As capturas são quadros do vídeo e incluem a barra de gravação do Jam. A mesma gravação é a fonte de vários casos.

Não foram confirmados o valor escolhido nos seletores, a filtragem local ou no servidor, o resultado vazio e cada critério isolado.

Não houve execução da aplicação, inspeção de código, acesso ao banco ou reteste nesta revisão.
