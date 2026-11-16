# Evidência — CT-RF74: Alternar entre os temas claro e escuro na Prospecção

- **Fonte fornecida:** [Jam](https://jam.dev/c/5dc9fc15-8e13-4f90-b21f-a49aedc6731e) — TemaEscuroClaro.
- **Gravação / análise original:** 16/11/2026, conforme o resumo; horário e fuso não informados.
- **Integração documental:** 16/11/2026.
- **Tela:** Prospecção.
- **Caso:** [CT-RF74](../../Cenario_Teste/CT-RF74_Temas_Prospeccao.md).
- **Defeito:** nenhum identificado no fluxo resumido.
- **Ambiente:** URL da tela, navegador, sistema operacional, versão e zoom não informados no resumo.

## Resultado e origem

A gravação mostra a tela passando de escura para clara e retornando ao tema escuro. A listagem permanece visível.

**Status:** Aprovado conforme o resumo da gravação.

## Cronologia informada no resumo

- 00:00–00:01: alternância nos controles de tema.
- POST /api/usuario/tema retorna HTTP 200 nas duas alterações. A resposta consultada contém verifica_erro=false.
- Quadros de 00:00.813 e 00:01.354 mostram, respectivamente, os temas claro e escuro.

## Arquivos

| Arquivo | Conteúdo | SHA-256 |
| --- | --- | --- |
| [RESUMO.txt](RESUMO.txt) | Cópia integral do resumo fornecido em CT-RF74, sem alterações. | `73a814ec7687ac980af231eca4bfd12f658220563359c02b9d0926a52ec8cda9` |

## Limites

Classificação restrita à alternância visível nesta tela; a gravação não demonstra persistência após recarregar nem uma auditoria de contraste.
Análise da gravação e dos eventos capturados no Jam; não foi executado um novo teste no sistema.

Integração documental dos arquivos RESUMO.txt fornecidos em `C:\Users\Leonardo\Desktop\evidencias`, com data de gravação e análise informada de 16/11/2026. Os Jams não foram reabertos nesta integração; eventos de rede, horários e quadros abaixo são transcritos dos resumos, sem verificação independente. Não houve nova execução do SIFIT, reteste, consulta ao banco, logs ou código.

Esta pasta contém o resumo e sua documentação; não foram fornecidos vídeos ou capturas locais. O hash identifica o arquivo de texto copiado, sem certificar o conteúdo remoto do Jam.

---

[← Evidências](../README.md) · [CT-RF74](../../Cenario_Teste/CT-RF74_Temas_Prospeccao.md)
