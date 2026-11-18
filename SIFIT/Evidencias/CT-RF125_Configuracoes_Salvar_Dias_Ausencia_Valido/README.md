# Evidência — CT-RF125: Salvar um valor válido de dias de ausência

- **Fonte:** [Jam original](https://jam.dev/c/12d6bba7-a67e-4882-86a5-4dd08d194af2).
- **Autor exibido:** Pedro Figueiredo.
- **Gravação:** 16/11/2026, 21:59:22 BRT, com duração de 29,34 s.
- **Revisão:** 17/11/2026.
- **Caso:** [CT-RF125](../../Cenario_Teste/CT-RF125_Configuracoes_Salvar_Dias_Ausencia_Valido.md).
- **Defeito:** Nenhum no fluxo avaliado.
- **Ambiente:** https://sifit.centrion.com.br/configuracoes · Chrome 157.0.8103.79 / Windows 10 (x86) · vídeo de 1918 × 998.

## Resultado e origem

O POST com 15 retornou HTTP 200 e `verifica_erro: false`. A recarga exibiu 15 e o GET devolveu `dias_ausente: 15`. O valor inicial 1100 foi reenviado e confirmado na recarga seguinte.

**Status:** Aprovado conforme a gravação.

## Arquivos

| Arquivo | Conteúdo | SHA-256 |
| --- | --- | --- |
| [dias_15_apos_recarga_00-16.jpg](dias_15_apos_recarga_00-16.jpg) | Valor 15 após a primeira recarga. | `55621d710a84d44980232e333abb2287a5cae54f1d89bb7d807c6a942f9e4b5b` |
| [dias_1100_apos_recarga_00-27.jpg](dias_1100_apos_recarga_00-27.jpg) | Valor original 1100 após a segunda recarga. | `6238492ce79de358cbf0f3348996a09063128ed367ec1a298a14384b5c24e48f` |
| [linha_do_tempo.txt](linha_do_tempo.txt) | Cronologia de ações, rede e quadros consultados no Jam. | — |
| [origem.url](origem.url) | Endereço original do Jam. | — |

## Limites

Esta pasta contém a cronologia e os recortes dos quadros consultados. A gravação integral fica no Jam.

A evidência confirma persistência para o valor testado e restauração do valor original observado. A faixa completa e o efeito na contagem de clientes ausentes exigem outros casos.
