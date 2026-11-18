# Evidência — CT-RF133: Filtrar Resultados da Inteligência pelos últimos 30 dias

- **Fonte:** [Jam original](https://jam.dev/c/2756d5c1-a823-482b-bf8d-878357b8b087).
- **Autor exibido:** Pedro Figueiredo.
- **Gravação:** 16/11/2026, 21:49:48 BRT, com duração de 20,07 s.
- **Revisão:** 17/11/2026.
- **Caso:** [CT-RF133](../../Cenario_Teste/CT-RF133_Resultados_IA_Filtro_30_Dias.md).
- **Defeito:** Nenhum no fluxo avaliado.
- **Ambiente:** https://sifit.centrion.com.br/inteligencia/resultados · Chrome 157.0.8103.79 / Windows 10 (x86) · vídeo de 1918 × 998.

## Resultado e origem

Ao selecionar 30 dias, automações e relatórios passaram de 3 para 12 e aniversariantes de 2 para 6. O GET retornou `dias: 30` e 12 itens na linha do tempo, frente a 3 em 7 dias. O retorno a 7 dias e a seleção seguinte de 30 repetiram os estados observados.

**Status:** Aprovado conforme a gravação.

## Arquivos

| Arquivo | Conteúdo | SHA-256 |
| --- | --- | --- |
| [resultados_7_dias_00-08.jpg](resultados_7_dias_00-08.jpg) | Últimos 7 dias com três automações e dois aniversariantes. | `a636d4285abdcce845096fd992810d6aaae098ed5c23658a05906e3738eba25e` |
| [resultados_30_dias_00-18.jpg](resultados_30_dias_00-18.jpg) | Últimos 30 dias com doze automações e seis aniversariantes. | `53d78886012977495e74c2eadf6aac3ad3d678dfb6cc0bff7c846b7de7ff7125` |
| [linha_do_tempo.txt](linha_do_tempo.txt) | Cronologia de ações, rede e quadros consultados no Jam. | — |
| [origem.url](origem.url) | Endereço original do Jam. | — |

## Limites

Esta pasta contém a cronologia e os recortes dos quadros consultados. A gravação integral fica no Jam.

O teste confirma troca de filtro e consistência com a API. Os limites de data e a regra dos cartões que ficaram constantes exigem dados de controle.
