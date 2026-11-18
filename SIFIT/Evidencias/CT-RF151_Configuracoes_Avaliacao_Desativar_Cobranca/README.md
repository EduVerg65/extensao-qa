# Evidência — CT-RF151: Desativar a cobrança da avaliação do cliente

- **Fonte:** Jam 1 — Desativação da cobrança da avaliação (gravação restrita por conter dados de integração).
- **Autor exibido:** Pedro Figueiredo.
- **Gravação:** 16/11/2026, 23:10:04 BRT, com duração de 18,34 s.
- **Revisão:** 18/11/2026.
- **Caso:** [CT-RF151](../../Cenario_Teste/CT-RF151_Configuracoes_Avaliacao_Desativar_Cobranca.md).
- **Defeito:** Nenhum no fluxo avaliado.
- **Ambiente:** https://sifit.centrion.com.br/configuracoes · Chrome 157.0.8103.79 / Windows 10 (x86) · vídeo de 1918 × 998.

## Resultado e origem

O salvamento de Não retornou HTTP 200 com `verifica_erro: false`. Após recarregar, a consulta devolveu `cobrar_avaliacao: nao` e o seletor mostrou Não. O POST de restauração para Sim retornou sucesso.

**Status:** Aprovado conforme a gravação.

## Arquivos

| Arquivo | Conteúdo | SHA-256 |
| --- | --- | --- |
| [cobrar_avaliacao_sim_00-01.jpg](cobrar_avaliacao_sim_00-01.jpg) | Cobrar Avaliação do Cliente em Sim antes da alteração. | `7580667c26eeb26c2ccb430104782a229038d9938784c6d85fc5214516760ff0` |
| [cobrar_avaliacao_nao_00-12.jpg](cobrar_avaliacao_nao_00-12.jpg) | Cobrar Avaliação do Cliente em Não após reabrir a aba. | `5dde09530d4b0af66262884e4d2602bc37075c05e21862867745401095448b74` |
| [linha_do_tempo.txt](linha_do_tempo.txt) | Cronologia de ações, rede e quadros consultados no Jam. | — |
| [origem.url](origem.url) | Página testada. O link da gravação fica restrito. | — |

## Limites

Os recortes e a cronologia omitem valores dos campos de integração, identificadores de conta e dados de autenticação. A gravação integral fica no Jam.

A evidência cobre a preferência salva. A geração de cobranças e o reflexo no cadastro de avaliação ficam para nova execução.
