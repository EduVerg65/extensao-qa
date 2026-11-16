# Evidência — CT-RF78: Cadastrar lead no estágio Interessado

- **Fonte fornecida:** [Jam](https://jam.dev/c/f8735cbf-4043-4467-b43f-3cad7eff0da8) — testeInterresado.
- **Gravação / análise original:** 16/11/2026, conforme o resumo; horário e fuso não informados.
- **Integração documental:** 16/11/2026.
- **Tela:** Prospecção.
- **Caso:** [CT-RF78](../../Cenario_Teste/CT-RF78_Cadastro_Lead_Interessado.md).
- **Defeito:** nenhum identificado no fluxo resumido.
- **Ambiente:** URL da tela, navegador, sistema operacional, versão e zoom não informados no resumo.

## Resultado e origem

O cadastro retorna código 12 e o lead aparece na listagem com a identificação Interessado.

**Status:** Aprovado conforme o resumo da gravação.

## Cronologia informada no resumo

- 00:02: seleção de INTERESSADO.
- 00:17: POST /api/salvar-lead/1 envia estagio=INTERESSADO e retorna HTTP 200, verifica_erro=false e id=12.
- 00:17: GET /api/leads/1 retorna HTTP 200; quadro de 00:19.843 mostra o registro de código 12.

## Arquivos

| Arquivo | Conteúdo | SHA-256 |
| --- | --- | --- |
| [RESUMO.txt](RESUMO.txt) | Cópia integral do resumo fornecido em CT-RF78, sem alterações. | `991e2d35074c3ff783969ac87bf454cfe1dc057d1d61aa31b8cf70553aa98cdf` |

## Limites

A gravação não demonstra reabertura ou alteração posterior do registro.
Análise da gravação e dos eventos capturados no Jam; não foi executado um novo teste no sistema.

Integração documental dos arquivos RESUMO.txt fornecidos em `C:\Users\Leonardo\Desktop\evidencias`, com data de gravação e análise informada de 16/11/2026. Os Jams não foram reabertos nesta integração; eventos de rede, horários e quadros abaixo são transcritos dos resumos, sem verificação independente. Não houve nova execução do SIFIT, reteste, consulta ao banco, logs ou código.

Esta pasta contém o resumo e sua documentação; não foram fornecidos vídeos ou capturas locais. O hash identifica o arquivo de texto copiado, sem certificar o conteúdo remoto do Jam.

---

[← Evidências](../README.md) · [CT-RF78](../../Cenario_Teste/CT-RF78_Cadastro_Lead_Interessado.md)
