# Evidência — CT-RF79: Cadastrar lead no estágio Fez Aula Experimental

- **Fonte fornecida:** [Jam](https://jam.dev/c/bef3d877-056b-4274-87c3-da37869c54fd) — TesteFezAula.
- **Gravação / análise original:** 16/11/2026, conforme o resumo; horário e fuso não informados.
- **Integração documental:** 16/11/2026.
- **Tela:** Prospecção.
- **Caso:** [CT-RF79](../../Cenario_Teste/CT-RF79_Cadastro_Lead_Aula_Experimental.md).
- **Defeito:** nenhum identificado no fluxo resumido.
- **Ambiente:** URL da tela, navegador, sistema operacional, versão e zoom não informados no resumo.

## Resultado e origem

O lead é criado com código 14 e estágio FEZ_AULA_EXP. A linha correspondente aparece ao final, e o total de leads passa de 9 para 10.

**Status:** Aprovado conforme o resumo da gravação.

## Cronologia informada no resumo

- 00:04: seleção de FEZ_AULA_EXP.
- 00:16: POST /api/salvar-lead/1 retorna HTTP 200, verifica_erro=false e id=14.
- 00:16: GET /api/leads/1 retorna HTTP 200; quadro de 00:17.747 mostra o lead no estágio escolhido.

## Arquivos

| Arquivo | Conteúdo | SHA-256 |
| --- | --- | --- |
| [RESUMO.txt](RESUMO.txt) | Cópia integral do resumo fornecido em CT-RF79, sem alterações. | `c6d92bb631fa4b1b0badf0550b775e5c70d62c4be4336f3d2e2f21fd28ec5dc0` |

## Limites

A gravação valida o cadastro no estágio indicado; não demonstra agendamento ou realização de uma aula.
Análise da gravação e dos eventos capturados no Jam; não foi executado um novo teste no sistema.

Integração documental dos arquivos RESUMO.txt fornecidos em `C:\Users\Leonardo\Desktop\evidencias`, com data de gravação e análise informada de 16/11/2026. Os Jams não foram reabertos nesta integração; eventos de rede, horários e quadros abaixo são transcritos dos resumos, sem verificação independente. Não houve nova execução do SIFIT, reteste, consulta ao banco, logs ou código.

Esta pasta contém o resumo e sua documentação; não foram fornecidos vídeos ou capturas locais. O hash identifica o arquivo de texto copiado, sem certificar o conteúdo remoto do Jam.

---

[← Evidências](../README.md) · [CT-RF79](../../Cenario_Teste/CT-RF79_Cadastro_Lead_Aula_Experimental.md)
