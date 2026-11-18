# Evidência — CT-RF137: Executar Risco de Evasão manualmente pela Central

- **Fonte:** Jam — PED-04 — Executar Risco de Evasão (gravação restrita por conter dados individuais da avaliação de risco).
- **Autor exibido:** Pedro Figueiredo.
- **Gravação:** 16/11/2026, 21:33:26 BRT, com duração de 30,21 s.
- **Revisão:** 17/11/2026.
- **Caso:** [CT-RF137](../../Cenario_Teste/CT-RF137_Central_Risco_Evasao_Executar_Agora.md).
- **Defeito:** Nenhum no fluxo avaliado.
- **Ambiente:** https://sifit.centrion.com.br/inteligencia-automacao · Chrome 157.0.8103.79 / Windows 10 (x86) · vídeo de 1918 × 998.

## Resultado e origem

O POST retornou HTTP 200 e `verifica_erro: false`. O resumo da execução e o relatório indicaram 23 registros em risco médio e zero em risco alto e baixo. A Central apresentou a nova execução às 00:32 e o resumo continuou mostrando esse horário após Atualizar.

**Status:** Aprovado conforme a gravação.

## Arquivos

| Arquivo | Conteúdo | SHA-256 |
| --- | --- | --- |
| [central_antes_executar_00-08.jpg](central_antes_executar_00-08.jpg) | Resumo da Central antes da execução manual. | `1e2140a48c8084681f0d8a065b0254941485364c64d3a6e311c8376aa76c1cec` |
| [central_apos_executar_00-23.jpg](central_apos_executar_00-23.jpg) | Resumo e atividade recente depois da execução e da atualização. | `cdeab08dbc2bad53ae2ad0c1ceddb68ed63fdd6298217bf4289ae5c31d31b03e` |
| [linha_do_tempo.txt](linha_do_tempo.txt) | Cronologia de ações, rede e quadros consultados no Jam. | — |
| [origem.url](origem.url) | Página testada. O link da gravação fica restrito. | — |

## Limites

Esta pasta contém a cronologia e os recortes dos quadros consultados. A gravação integral fica no Jam.

A aprovação se limita à execução e à exibição do resultado na Central. O horário é a referência exibida no SIFIT. A entrega pelo canal de notificação não foi verificada. Os recortes mostram apenas informações agregadas.
