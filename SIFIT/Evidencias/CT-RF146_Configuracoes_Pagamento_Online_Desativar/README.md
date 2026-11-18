# Evidência — CT-RF146: Persistir a desativação do Pagamento Online

- **Fonte:** Jam 2 — Desativação do Pagamento Online (gravação restrita por conter dados de integração).
- **Autor exibido:** Pedro Figueiredo.
- **Gravação:** 16/11/2026, 23:23:27 BRT, com duração de 15,84 s.
- **Revisão:** 17/11/2026.
- **Caso:** [CT-RF146](../../Cenario_Teste/CT-RF146_Configuracoes_Pagamento_Online_Desativar.md).
- **Defeito:** Nenhum no fluxo avaliado.
- **Ambiente:** https://sifit.centrion.com.br/configuracoes · Chrome 157.0.8103.79 / Windows 10 (x86) · vídeo de 1918 × 998.

## Resultado e origem

A alteração para Não retornou sucesso. Após recarregar, a consulta devolveu `pagarme: nao` e a aba Pagamento exibiu Não. No fim, o usuário selecionou Sim e enviou a restauração, que retornou sucesso.

**Status:** Aprovado conforme a gravação.

## Arquivos

| Arquivo | Conteúdo | SHA-256 |
| --- | --- | --- |
| [pagamento_nao_apos_reabrir_00-11.jpg](pagamento_nao_apos_reabrir_00-11.jpg) | Pagamento Online retorna como Não após reabrir a aba. | `90cb7e9c49d94e92cc426d8b598cb8ebe1807ec8d2e4e168e787faffa7968901` |
| [pagamento_sim_na_restauracao_00-14.jpg](pagamento_sim_na_restauracao_00-14.jpg) | Pagamento Online alterado para Sim antes do salvamento de restauração. | `9e0c43d5833a850f788b3666f9b9199d5b96327891c995f1183c4bd6473c48d1` |
| [linha_do_tempo.txt](linha_do_tempo.txt) | Cronologia de ações, rede e quadros consultados no Jam. | — |
| [origem.url](origem.url) | Página testada. O link da gravação fica restrito. | — |

## Limites

Os recortes e a cronologia omitem valores dos campos de integração, identificadores de conta e dados de autenticação. A gravação integral fica no Jam.

A aprovação cobre a persistência de Não. A gravação termina após o POST de restauração, sem nova leitura de Sim. Cobrança e validação do token não foram exercitadas.
