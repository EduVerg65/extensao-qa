# Evidência — CT-RF76: Excluir leads com confirmação

- **Fonte fornecida:** [Jam](https://jam.dev/c/2ac5e5ed-b10f-4cc9-9f97-7ba65ca560f8) — TesteExcluindoLeads.
- **Gravação / análise original:** 16/11/2026, conforme o resumo; horário e fuso não informados.
- **Integração documental:** 16/11/2026.
- **Tela:** Prospecção.
- **Caso:** [CT-RF76](../../Cenario_Teste/CT-RF76_Exclusao_Leads_Confirmacao.md).
- **Defeito:** nenhum identificado no fluxo resumido.
- **Ambiente:** URL da tela, navegador, sistema operacional, versão e zoom não informados no resumo.

## Resultado e origem

Os leads de códigos 3 e 4 deixam de aparecer após as confirmações. O total exibido diminui de 8 para 7 e depois para 6.

**Status:** Aprovado conforme o resumo da gravação.

## Cronologia informada no resumo

- 00:01 e 00:04: POST /api/deletar-lead/1 retorna HTTP 200, seguido de GET /api/leads/1 com HTTP 200.
- A segunda exclusão envia id=4 e recebe verifica_erro=false.
- Quadros de 00:03.179 e 00:05.723 mostram os totais 7 e 6.

## Arquivos

| Arquivo | Conteúdo | SHA-256 |
| --- | --- | --- |
| [RESUMO.txt](RESUMO.txt) | Cópia integral do resumo fornecido em CT-RF76, sem alterações. | `80126600e88d13a494dcf137121c652fa0d1dfa36a1e081bac28e6d38d681f17` |

## Limites

As duas exclusões foram agrupadas no mesmo caso porque pertencem ao mesmo cenário na gravação. O cancelamento da confirmação de exclusão não foi testado.
Análise da gravação e dos eventos capturados no Jam; não foi executado um novo teste no sistema.

Integração documental dos arquivos RESUMO.txt fornecidos em `C:\Users\Leonardo\Desktop\evidencias`, com data de gravação e análise informada de 16/11/2026. Os Jams não foram reabertos nesta integração; eventos de rede, horários e quadros abaixo são transcritos dos resumos, sem verificação independente. Não houve nova execução do SIFIT, reteste, consulta ao banco, logs ou código.

Esta pasta contém o resumo e sua documentação; não foram fornecidos vídeos ou capturas locais. O hash identifica o arquivo de texto copiado, sem certificar o conteúdo remoto do Jam.

---

[← Evidências](../README.md) · [CT-RF76](../../Cenario_Teste/CT-RF76_Exclusao_Leads_Confirmacao.md)
