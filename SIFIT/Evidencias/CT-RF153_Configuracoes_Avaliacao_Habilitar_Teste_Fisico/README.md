# Evidência — CT-RF153: Habilitar Teste Físico nas configurações de avaliação

- **Fonte:** [Jam 3 — Habilitação de Teste Físico](https://jam.dev/c/86466f6e-b180-439f-ab1d-dde2484595a3).
- **Autor exibido:** Pedro Figueiredo.
- **Gravação:** 16/11/2026, 23:12:07 BRT, com duração de 17,30 s.
- **Revisão:** 18/11/2026.
- **Caso:** [CT-RF153](../../Cenario_Teste/CT-RF153_Configuracoes_Avaliacao_Habilitar_Teste_Fisico.md).
- **Defeito:** Nenhum no fluxo avaliado.
- **Ambiente:** https://sifit.centrion.com.br/configuracoes · Chrome 157.0.8103.79 / Windows 10 (x86) · vídeo de 1918 × 998.

## Resultado e origem

O salvamento de Sim retornou HTTP 200 com `verifica_erro: false`. Após recarregar, a consulta devolveu `teste_fisico: SIM` e o seletor mostrou Sim. O POST de restauração para Não retornou sucesso.

**Status:** Aprovado conforme a gravação.

## Arquivos

| Arquivo | Conteúdo | SHA-256 |
| --- | --- | --- |
| [teste_fisico_nao_00-01.jpg](teste_fisico_nao_00-01.jpg) | Teste Físico em Não antes da alteração. | `58fe7ec14589766bf3cd1d737c09e77494bfef3db0e70b70c9e087e43bc6190d` |
| [teste_fisico_sim_00-12.jpg](teste_fisico_sim_00-12.jpg) | Teste Físico em Sim depois de reabrir Avaliação. | `d8c863528bdb547363c48521f957bd62dfaf19f210d71bd5fff5229bd0366b01` |
| [linha_do_tempo.txt](linha_do_tempo.txt) | Cronologia de ações, rede e quadros consultados no Jam. | — |
| [origem.url](origem.url) | Endereço original do Jam. | — |

## Limites

Os recortes e a cronologia omitem valores dos campos de integração, identificadores de conta e dados de autenticação. A gravação integral fica no Jam.

A gravação cobre a alteração e a leitura da preferência. A disponibilidade do teste no cadastro de avaliação fica para verificação separada.
