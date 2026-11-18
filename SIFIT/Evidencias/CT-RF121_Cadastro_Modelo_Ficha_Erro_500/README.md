# Evidência — CT-RF121: Cadastrar um modelo de ficha com nome e personal

- **Fonte:** [Jam original](https://jam.dev/c/04e2cae2-f3f2-43ff-8361-b3b9d9f50d35).
- **Autor exibido:** Pedro Figueiredo.
- **Gravação:** 16/11/2026, 22:18:52 BRT, com duração de 21,55 s.
- **Revisão:** 17/11/2026.
- **Caso:** [CT-RF121](../../Cenario_Teste/CT-RF121_Cadastro_Modelo_Ficha_Erro_500.md).
- **Defeito:** [BUG-045](../../Relatorio-de-Bugs.md#bug-045), em triagem.
- **Ambiente:** https://sifit.centrion.com.br/fichas-treino-modelo · Chrome 157.0.8103.79 / Windows 10 (x86) · vídeo de 1918 × 998.

## Resultado e origem

O envio com Pedro-01 e um personal selecionado produziu HTTP 500 em `POST /api/adicionar-ficha/1`. O servidor retornou `verifica_erro: true` e “Erro interno inesperado.” A interface exibiu “Erro ao salvar modelo.” e a gravação não mostrou confirmação de criação.

**Status:** Reprovado nas evidências.

## Arquivos

| Arquivo | Conteúdo | SHA-256 |
| --- | --- | --- |
| [modelo_preenchido_00-16.jpg](modelo_preenchido_00-16.jpg) | Formulário preenchido antes de Criar Modelo. | `981d2f69d5c6e8be4315bca29134aaee201807d5317dd6b6e5de22a6b4424614` |
| [erro_salvar_modelo_00-19.jpg](erro_salvar_modelo_00-19.jpg) | Aviso Erro ao salvar modelo após o HTTP 500. | `0c8d905b9025fef1e4b4ef31eba02503db12f923d9b95bb1d228c1e633a0e36b` |
| [linha_do_tempo.txt](linha_do_tempo.txt) | Cronologia de ações, rede e quadros consultados no Jam. | — |
| [origem.url](origem.url) | Endereço original do Jam. | — |

## Limites

Esta pasta contém a cronologia, a origem e os recortes dos quadros consultados. O vídeo permanece no Jam.

Uma tentativa foi registrada. A gravação não confirma causa técnica, persistência parcial ou abrangência para outros nomes e personais. Os CT-RF109 e CT-RF110 cobrem, respectivamente, a validação de nome vazio e o cancelamento.
