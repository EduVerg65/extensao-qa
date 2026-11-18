# Evidência — CT-RF116: Validar o salvamento com o campo de dias de ausência vazio

- **Fonte:** [Jam original](https://jam.dev/c/4e96d4fa-65b5-459b-a795-854496e5753c).
- **Autor exibido:** Pedro Figueiredo.
- **Gravação:** 16/11/2026, 22:03:53 BRT, com duração de 21,47 s.
- **Revisão:** 17/11/2026.
- **Caso:** [CT-RF116](../../Cenario_Teste/CT-RF116_Configuracoes_Dias_Ausencia_Vazio.md).
- **Defeito:** Sem defeito confirmado.
- **Ambiente:** https://sifit.centrion.com.br/configuracoes · Chrome 157.0.8103.79 / Windows 10 (x86) · vídeo de 1918 × 998.

## Resultado e origem

Com o campo vazio, Salvar Configurações enviou `dias_ausente=0` e recebeu HTTP 200 com `verifica_erro: false`. A recarga exibiu 0 e o GET confirmou `dias_ausente: 0`. No fim, foi reenviado 1100 com HTTP 200.

**Status:** A validar — regra ou contexto pendente.

## Arquivos

| Arquivo | Conteúdo | SHA-256 |
| --- | --- | --- |
| [dias_vazio_00-07.jpg](dias_vazio_00-07.jpg) | Campo de dias vazio antes do salvamento. | `eded01af7b1b3382f85e64fdfa3755c5d822f007dd15e193ac151ac71a999941` |
| [dias_apos_recarga_00-13.jpg](dias_apos_recarga_00-13.jpg) | Estado do campo de dias após a recarga. | `30a402ebef3fadb5ec0d2a9d124a4d2afa134f45ff93f8268e9164ba3ee34c92` |
| [linha_do_tempo.txt](linha_do_tempo.txt) | Cronologia de ações, rede e quadros consultados no Jam. | — |
| [origem.url](origem.url) | Endereço original do Jam. | — |

## Limites

Esta pasta contém a cronologia, a origem e os recortes dos quadros consultados. O vídeo permanece no Jam.

A conversão de vazio para zero e a persistência estão confirmadas. A obrigatoriedade do campo, o significado de zero e o efeito sobre a contagem de clientes ausentes dependem da regra de produto. O CT-RF44 já registra a necessidade de confirmar a faixa.
