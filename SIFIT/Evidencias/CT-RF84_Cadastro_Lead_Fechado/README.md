# Evidência — CT-RF84: Cadastrar lead no estágio Fechado

- **Fonte fornecida:** [Jam](https://jam.dev/c/775b9003-fdf7-4ad5-8882-15ba606b6674) — TesteFechado.
- **Gravação / análise original:** 16/11/2026, conforme o resumo; horário e fuso não informados.
- **Integração documental:** 16/11/2026.
- **Tela:** Prospecção.
- **Caso:** [CT-RF84](../../Cenario_Teste/CT-RF84_Cadastro_Lead_Fechado.md).
- **Defeito:** nenhum identificado no fluxo resumido.
- **Ambiente:** URL da tela, navegador, sistema operacional, versão e zoom não informados no resumo.

## Resultado e origem

A janela fecha após salvar, o total de leads passa de 12 para 13 e o registro testeFechado aparece com código 17 e identificação Fechado.

**Status:** Aprovado conforme o resumo da gravação.

## Cronologia informada no resumo

- 00:01: seleção de FECHADO.
- 00:20: POST /api/salvar-lead/1 retorna HTTP 200, seguido de GET /api/leads/1 com HTTP 200.
- Quadro de 00:22.648 mostra o registro de código 17 no estágio Fechado.

## Arquivos

| Arquivo | Conteúdo | SHA-256 |
| --- | --- | --- |
| [RESUMO.txt](RESUMO.txt) | Cópia integral do resumo fornecido em CT-RF84, sem alterações. | `3e76c142ba50411f7a32d659d130cf5a248adee959396f3eedab16d47177411e` |

## Limites

O corpo da resposta de salvamento não está disponível no evento consultado; o resultado é sustentado pelo retorno HTTP e pelo registro visível na listagem.
Análise da gravação e dos eventos capturados no Jam; não foi executado um novo teste no sistema.

Integração documental dos arquivos RESUMO.txt fornecidos em `C:\Users\Leonardo\Desktop\evidencias`, com data de gravação e análise informada de 16/11/2026. Os Jams não foram reabertos nesta integração; eventos de rede, horários e quadros abaixo são transcritos dos resumos, sem verificação independente. Não houve nova execução do SIFIT, reteste, consulta ao banco, logs ou código.

Esta pasta contém o resumo e sua documentação; não foram fornecidos vídeos ou capturas locais. O hash identifica o arquivo de texto copiado, sem certificar o conteúdo remoto do Jam.

---

[← Evidências](../README.md) · [CT-RF84](../../Cenario_Teste/CT-RF84_Cadastro_Lead_Fechado.md)
