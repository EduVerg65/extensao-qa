# Evidência — CT-RF80: Cadastrar lead no estágio Proposta

- **Fonte fornecida:** [Jam](https://jam.dev/c/84f94285-ae5f-4f95-b640-a9b107565aa6) — testeProposta.
- **Gravação / análise original:** 16/11/2026, conforme o resumo; horário e fuso não informados.
- **Integração documental:** 16/11/2026.
- **Tela:** Prospecção.
- **Caso:** [CT-RF80](../../Cenario_Teste/CT-RF80_Cadastro_Lead_Proposta.md).
- **Defeito:** nenhum identificado no fluxo resumido.
- **Ambiente:** URL da tela, navegador, sistema operacional, versão e zoom não informados no resumo.

## Resultado e origem

O cadastro retorna código 15 e o registro aparece na listagem com estágio Proposta. O total de leads passa de 10 para 11.

**Status:** Aprovado conforme o resumo da gravação.

## Cronologia informada no resumo

- 00:14: seleção de PROPOSTA.
- 00:25: POST /api/salvar-lead/1 envia estagio=PROPOSTA e retorna HTTP 200, verifica_erro=false e id=15.
- 00:25: GET /api/leads/1 retorna HTTP 200; quadro de 00:27.559 mostra o registro de código 15.

## Arquivos

| Arquivo | Conteúdo | SHA-256 |
| --- | --- | --- |
| [RESUMO.txt](RESUMO.txt) | Cópia integral do resumo fornecido em CT-RF80, sem alterações. | `c361bed38e76bdf1848478af7d257068e718072627316563328ea6a1a2523d5e` |

## Limites

O teste demonstra a classificação do lead no estágio Proposta; não demonstra emissão de proposta comercial.
Análise da gravação e dos eventos capturados no Jam; não foi executado um novo teste no sistema.

Integração documental dos arquivos RESUMO.txt fornecidos em `C:\Users\Leonardo\Desktop\evidencias`, com data de gravação e análise informada de 16/11/2026. Os Jams não foram reabertos nesta integração; eventos de rede, horários e quadros abaixo são transcritos dos resumos, sem verificação independente. Não houve nova execução do SIFIT, reteste, consulta ao banco, logs ou código.

Esta pasta contém o resumo e sua documentação; não foram fornecidos vídeos ou capturas locais. O hash identifica o arquivo de texto copiado, sem certificar o conteúdo remoto do Jam.

---

[← Evidências](../README.md) · [CT-RF80](../../Cenario_Teste/CT-RF80_Cadastro_Lead_Proposta.md)
