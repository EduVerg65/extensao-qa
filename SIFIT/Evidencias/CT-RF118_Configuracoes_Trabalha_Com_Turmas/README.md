# Evidência — CT-RF118: Alterar e persistir a opção Trabalha com turmas?

- **Fonte:** [Jam original](https://jam.dev/c/a51c33a5-537a-40fd-a55d-990b70ac0696).
- **Autor exibido:** Pedro Figueiredo.
- **Gravação:** 16/11/2026, 22:06:12 BRT, com duração de 25,33 s.
- **Revisão:** 17/11/2026.
- **Caso:** [CT-RF118](../../Cenario_Teste/CT-RF118_Configuracoes_Trabalha_Com_Turmas.md).
- **Defeito:** Nenhum no fluxo avaliado.
- **Ambiente:** https://sifit.centrion.com.br/configuracoes · Chrome 157.0.8103.79 / Windows 10 (x86) · vídeo de 1918 × 998.

## Resultado e origem

O seletor mudou de Sim para Não e depois voltou a Sim. Os dois salvamentos retornaram HTTP 200 com `verifica_erro: false`. Após cada recarga, o seletor e o GET apresentaram o estado salvo.

**Status:** Aprovado conforme a gravação.

## Arquivos

| Arquivo | Conteúdo | SHA-256 |
| --- | --- | --- |
| [turmas_nao_00-12.jpg](turmas_nao_00-12.jpg) | Trabalha com turmas? em Não após a recarga. | `f36c8d09d908bb586b520cde1a97415dee87399481aa685a77b655456b878af0` |
| [turmas_sim_00-22.jpg](turmas_sim_00-22.jpg) | Trabalha com turmas? em Sim após a segunda recarga. | `e55d931c205e5f067d18490a2998dfeef0266833448a1d400c2d21feba39668e` |
| [linha_do_tempo.txt](linha_do_tempo.txt) | Cronologia de ações, rede e quadros consultados no Jam. | — |
| [origem.url](origem.url) | Endereço original do Jam. | — |

## Limites

Esta pasta contém a cronologia, a origem e os recortes dos quadros consultados. O vídeo permanece no Jam.

A evidência cobre o seletor nas Configurações e o valor retornado após recarga. Os efeitos sobre criação de turmas e sobre o menu Turmas exigem casos específicos.
