# Evidência — CT-RF81: Cadastrar bandeira com parcela e conferir a listagem

- **Fonte fornecida:** [Jam](https://jam.dev/c/2f0280fb-6b7f-4cf0-a45c-02f8c16b6c5e) — TesteParcela.
- **Gravação / análise original:** 16/11/2026, conforme o resumo; horário e fuso não informados.
- **Integração documental:** 16/11/2026.
- **Tela:** Bandeiras de Cartão.
- **Caso:** [CT-RF81](../../Cenario_Teste/CT-RF81_Cadastro_Bandeira_Parcela_Listagem.md).
- **Defeito:** [BUG-035](../../Relatorio-de-Bugs.md#bug-035), em triagem.
- **Ambiente:** URL da tela, navegador, sistema operacional, versão e zoom não informados no resumo.

## Resultado e origem

A API confirma a criação da bandeira de código 34 e da parcela, mas a consulta seguinte retorna [] e a interface continua exibindo Nenhuma bandeira encontrada. A criação da parcela tem retorno de sucesso; o fluxo completo apresenta erro na recuperação/exibição do cadastro.

**Status:** Reprovado nas evidências resumidas.

## Cronologia informada no resumo

- 00:11: POST /api/cria/bandeira/1 retorna HTTP 201, verifica_erro=false e id=34.
- 00:11: POST /api/cria/parcela-bandeira/1 envia bandeira_id=34, n_parcela=2 e taxa=3,33; retorna HTTP 201 e verifica_erro=false.
- 00:11: POST /api/bandeiras/1 retorna HTTP 200 com corpo [].
- Quadro de 00:13.191 mostra a listagem vazia após fechar a janela.

## Arquivos

| Arquivo | Conteúdo | SHA-256 |
| --- | --- | --- |
| [RESUMO.txt](RESUMO.txt) | Cópia integral do resumo fornecido em CT-RF81, sem alterações. | `7fa2517b5ddf775c1d7d7b25ea650a605dda336724f584a353f7272b6030d8de` |

## Limites

A causa da divergência e a persistência efetiva no banco não foram verificadas. A gravação comprova a diferença entre os retornos de criação e de listagem, sem permitir atribuir a causa ao frontend ou ao backend.
Análise da gravação e dos eventos capturados no Jam; não foi executado um novo teste no sistema.

Integração documental dos arquivos RESUMO.txt fornecidos em `C:\Users\Leonardo\Desktop\evidencias`, com data de gravação e análise informada de 16/11/2026. Os Jams não foram reabertos nesta integração; eventos de rede, horários e quadros abaixo são transcritos dos resumos, sem verificação independente. Não houve nova execução do SIFIT, reteste, consulta ao banco, logs ou código.

Esta pasta contém o resumo e sua documentação; não foram fornecidos vídeos ou capturas locais. O hash identifica o arquivo de texto copiado, sem certificar o conteúdo remoto do Jam.

---

[← Evidências](../README.md) · [CT-RF81](../../Cenario_Teste/CT-RF81_Cadastro_Bandeira_Parcela_Listagem.md)
