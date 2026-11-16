# Evidência — CT-RF82: Verificar aplicação dos temas na tela de Bandeiras

- **Fonte fornecida:** [Jam](https://jam.dev/c/ae4dc198-8a42-4451-898a-fb376596c744) — Erro na acessibilidade!.
- **Gravação / análise original:** 16/11/2026, conforme o resumo; horário e fuso não informados.
- **Integração documental:** 16/11/2026.
- **Tela:** Bandeiras de Cartão.
- **Caso:** [CT-RF82](../../Cenario_Teste/CT-RF82_Tema_Escuro_Bandeiras.md).
- **Defeito:** [BUG-036](../../Relatorio-de-Bugs.md#bug-036), em triagem.
- **Ambiente:** URL da tela, navegador, sistema operacional, versão e zoom não informados no resumo.

## Resultado e origem

No tema Escuro, os painéis ficam escuros, mas o fundo principal continua claro. Os textos da área vazia da listagem apresentam baixa legibilidade visual. A descrição do Jam relata: Fundo com falta de cores e modo escuro incompleto.

**Status:** Reprovado nas evidências resumidas.

## Cronologia informada no resumo

- Quadro de 00:03.800 mostra o tema Escuro selecionado, painéis escuros e fundo principal claro.
- Quadros de 00:05.320 e 00:06.840 permitem comparar os temas Claro e Escuro.
- 00:04–00:07: alterações de tema chamam POST /api/usuario/tema e recebem HTTP 200.

## Arquivos

| Arquivo | Conteúdo | SHA-256 |
| --- | --- | --- |
| [RESUMO.txt](RESUMO.txt) | Cópia integral do resumo fornecido em CT-RF82, sem alterações. | `7d30fd773cd8ce965ed0b25e33bcb98799065b0850fd75763d631e770486dd35` |

## Limites

O erro visual é observado na gravação. Não foram medidos índices de contraste nem feita auditoria formal de acessibilidade; a causa técnica não foi determinada.
Análise da gravação e dos eventos capturados no Jam; não foi executado um novo teste no sistema.

Integração documental dos arquivos RESUMO.txt fornecidos em `C:\Users\Leonardo\Desktop\evidencias`, com data de gravação e análise informada de 16/11/2026. Os Jams não foram reabertos nesta integração; eventos de rede, horários e quadros abaixo são transcritos dos resumos, sem verificação independente. Não houve nova execução do SIFIT, reteste, consulta ao banco, logs ou código.

Esta pasta contém o resumo e sua documentação; não foram fornecidos vídeos ou capturas locais. O hash identifica o arquivo de texto copiado, sem certificar o conteúdo remoto do Jam.

---

[← Evidências](../README.md) · [CT-RF82](../../Cenario_Teste/CT-RF82_Tema_Escuro_Bandeiras.md)
