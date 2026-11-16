# Evidência — CT-RF83: Validar cadastro de lead preenchendo apenas o nome

- **Fonte fornecida:** [Jam](https://jam.dev/c/ef3df03c-16ce-4cb6-b0c7-d04514cab4f6) — Bug - Criando propecção apenas com nome.
- **Gravação / análise original:** 16/11/2026, conforme o resumo; horário e fuso não informados.
- **Integração documental:** 16/11/2026.
- **Tela:** Prospecção.
- **Caso:** [CT-RF83](../../Cenario_Teste/CT-RF83_Cadastro_Lead_Apenas_Nome.md).
- **Defeito:** [BUG-037](../../Relatorio-de-Bugs.md#bug-037), em triagem.
- **Ambiente:** URL da tela, navegador, sistema operacional, versão e zoom não informados no resumo.

## Resultado e origem

O sistema aceita o envio sem bloqueio visível, cria o lead de código 19 e atualiza a listagem. O total de leads passa de 14 para 15.

**Status:** Reprovado conforme o relato; regra de obrigatoriedade a confirmar.

## Cronologia informada no resumo

- 00:02: nome Leo preenchido; os demais campos de contato permanecem visualmente vazios.
- 00:03: POST /api/salvar-lead/1 retorna HTTP 200, verifica_erro=false e id=19. O corpo enviado confirma telefone e observacao vazios.
- 00:03: GET /api/leads/1 retorna HTTP 200; quadro de 00:08.223 mostra o registro de código 19.

## Arquivos

| Arquivo | Conteúdo | SHA-256 |
| --- | --- | --- |
| [RESUMO.txt](RESUMO.txt) | Cópia integral do resumo fornecido em CT-RF83, sem alterações. | `ac7de6881a4e405d59465e6af9ae8eda0a6dbdb72bb030ad1d27e0104e020e52` |

## Limites

A classificação de erro acompanha o título do Jam. A regra formal dos campos obrigatórios não foi fornecida; é necessário validá-la para definir exatamente quais campos devem impedir o cadastro. O e-mail está mascarado nos dados de rede, e sua ausência foi avaliada visualmente.
Análise da gravação e dos eventos capturados no Jam; não foi executado um novo teste no sistema.

Integração documental dos arquivos RESUMO.txt fornecidos em `C:\Users\Leonardo\Desktop\evidencias`, com data de gravação e análise informada de 16/11/2026. Os Jams não foram reabertos nesta integração; eventos de rede, horários e quadros abaixo são transcritos dos resumos, sem verificação independente. Não houve nova execução do SIFIT, reteste, consulta ao banco, logs ou código.

Esta pasta contém o resumo e sua documentação; não foram fornecidos vídeos ou capturas locais. O hash identifica o arquivo de texto copiado, sem certificar o conteúdo remoto do Jam.

---

[← Evidências](../README.md) · [CT-RF83](../../Cenario_Teste/CT-RF83_Cadastro_Lead_Apenas_Nome.md)
