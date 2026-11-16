# Evidência — CT-RF64: Filtros da tela Contas a Pagar por nome, data e status

- **Fonte:** [Jam original](https://jam.dev/c/5d0afaf4-5abd-4e85-923f-27448304a9ef).
- **Autor exibido:** Gustavo Pelissari Oenning.
- **Gravação:** 15/11/2026, 21:58 BRT; duração de 1 min.
- **Revisão:** 15/11/2026.
- **Caso:** [CT-RF64](../../Cenario_Teste/CT-RF64_Filtros_Contas_Pagar.md).
- **Defeito:** nenhum confirmado; ponto a validar.
- **Ambiente:** https://sifit.centrion.com.br/contas-pagar; Chrome 157.0.8103.78, Windows 11 (x86), janela 1920 × 911.

## Resultado e origem

Com os critérios Nome "teste", Pagamento, 06/11/2026 e Pago, a listagem ficou vazia e os cartões foram a 0; o resultado é compatível com os critérios, mas sem dados de controle.

**Status:** A validar — regra ou contexto pendente.

## Arquivos

| Arquivo | Conteúdo | SHA-256 |
| --- | --- | --- |
| [filtro_nome_00-03.png](filtro_nome_00-03.png) | listagem inicial com as contas 27 e 28. | `c12a7d0df456b9037b970b512da14743d1fbaac0b2cefcf884b9dbf6e5240aaf` |
| [filtros_vazio_00-12.png](filtros_vazio_00-12.png) | nenhuma conta listada e cartões em 0. | `9d32b941d401fb3b61c67fd933c635c23eafd3889bcb00db6a9103fc0d000eb5` |
| [rede_lista.jpg](rede_lista.jpg) | primeiras 31 entradas da gravação. | `b80601de3e09b18c93ee63df32a0b2dd01269fbc1b86a85f60904fca406fc507` |
| [linha_do_tempo.txt](linha_do_tempo.txt) | Cronologia de ações, digitação e rede do Jam. | — |
| [origem.url](origem.url) | Endereço original do Jam. | — |

## Limites

Esta pasta contém documentação da consulta, capturas extraídas da reprodução do Jam e a cronologia; não contém cópia do vídeo, e nenhum hash de vídeo foi gerado. As capturas mostram o botão de reprodução do Jam sobreposto. A mesma gravação é a fonte de vários casos.

Não foram confirmados o resultado vazio contra a base, cada critério isolado e o corpo da busca principal.

Não houve execução da aplicação, inspeção de código, acesso ao banco ou reteste nesta revisão.
