# Evidência — CT-RF110: Cancelar cadastro de modelo de ficha preenchido

- **Fonte:** [Jam original](https://jam.dev/c/a2a39e11-04f4-40aa-a97e-75a57a5f1b0f).
- **Autor exibido:** Pedro Figueiredo.
- **Gravação:** 16/11/2026, 22:20:56 BRT, com duração de 20,18 s.
- **Revisão:** 17/11/2026.
- **Caso:** [CT-RF110](../../Cenario_Teste/CT-RF110_Cancelar_Cadastro_Modelo_Ficha.md).
- **Defeito:** nenhum no fluxo avaliado.
- **Ambiente:** https://sifit.centrion.com.br/fichas-treino-modelo · Chrome 157.0.8103.79, Windows 10 (x86), vídeo de 1918 × 998.

## Resultado e origem

O formulário continha o nome PEDRO-01 e um personal selecionado. O clique em Cancelar fechou o formulário e a tela voltou à listagem com 0 registros. A captura não registrou requisições de rede no fluxo.

**Status:** Aprovado conforme a gravação.

## Arquivos

| Arquivo | Conteúdo | SHA-256 |
| --- | --- | --- |
| [formulario_preenchido_00-14.jpg](formulario_preenchido_00-14.jpg) | Dados preenchidos imediatamente antes do cancelamento. | `edf6b9f7badc3264c06909b634182b8363022dfa169cf34661ae9eda5d753c98` |
| [listagem_apos_cancelar_00-17.jpg](listagem_apos_cancelar_00-17.jpg) | Listagem com 0 registros após cancelar. | `1e9a0436e7768af510173da2312eeffe71d055fd7cf6599e773d1163ef652e94` |
| [linha_do_tempo.txt](linha_do_tempo.txt) | Cronologia de ações, rede e quadros consultados no Jam. | — |
| [origem.url](origem.url) | Endereço do Jam original. | — |

## Limites

Esta pasta contém a cronologia, a origem e os recortes dos quadros consultados. O vídeo permanece no Jam.

O formulário não foi reaberto depois do cancelamento. A listagem inicial e a final mostram 0 registros.

A revisão se limita ao material gravado. A execução do sistema para as verificações complementares está prevista no caso de teste.
