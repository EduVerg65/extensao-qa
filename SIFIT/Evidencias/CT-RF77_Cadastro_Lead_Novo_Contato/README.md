# Evidência — CT-RF77: Cadastrar lead no estágio Novo Contato

- **Fonte fornecida:** [Jam](https://jam.dev/c/29447c6a-90f5-48b2-ac5d-d43cad44a782) — CriandoLeadContato.
- **Gravação / análise original:** 16/11/2026, conforme o resumo; horário e fuso não informados.
- **Integração documental:** 16/11/2026.
- **Tela:** Prospecção.
- **Caso:** [CT-RF77](../../Cenario_Teste/CT-RF77_Cadastro_Lead_Novo_Contato.md).
- **Defeito:** nenhum identificado no fluxo resumido.
- **Ambiente:** URL da tela, navegador, sistema operacional, versão e zoom não informados no resumo.

## Resultado e origem

O lead de teste é criado com o estágio NOVO_CONTATO, recebe código 11 e aparece na listagem. O total passa de 6 para 7, e o indicador Novo Contato passa de 2 para 3.

**Status:** Aprovado conforme o resumo da gravação.

## Cronologia informada no resumo

- 00:14: seleção final de Novo Contato.
- 00:22: POST /api/salvar-lead/1 envia estagio=NOVO_CONTATO e retorna HTTP 200, verifica_erro=false e id=11.
- 00:23: GET /api/leads/1 retorna HTTP 200; quadro de 00:25.604 mostra o novo registro.

## Arquivos

| Arquivo | Conteúdo | SHA-256 |
| --- | --- | --- |
| [RESUMO.txt](RESUMO.txt) | Cópia integral do resumo fornecido em CT-RF77, sem alterações. | `e134285adbdd47f2e6d0161ac29f6d04c28a7fbd7b5fdae7a13ed92a834aea99` |

## Limites

A classificação considera o cadastro mostrado; não houve reabertura do registro para revisar todos os campos.
Análise da gravação e dos eventos capturados no Jam; não foi executado um novo teste no sistema.

Integração documental dos arquivos RESUMO.txt fornecidos em `C:\Users\Leonardo\Desktop\evidencias`, com data de gravação e análise informada de 16/11/2026. Os Jams não foram reabertos nesta integração; eventos de rede, horários e quadros abaixo são transcritos dos resumos, sem verificação independente. Não houve nova execução do SIFIT, reteste, consulta ao banco, logs ou código.

Esta pasta contém o resumo e sua documentação; não foram fornecidos vídeos ou capturas locais. O hash identifica o arquivo de texto copiado, sem certificar o conteúdo remoto do Jam.

---

[← Evidências](../README.md) · [CT-RF77](../../Cenario_Teste/CT-RF77_Cadastro_Lead_Novo_Contato.md)
