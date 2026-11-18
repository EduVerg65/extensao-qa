# Evidência — CT-RF120: Conferir a configuração de acesso ao sistema desktop

- **Fonte:** [Jam original](https://jam.dev/c/466be253-ad9a-4856-b567-fb17e1fdd479).
- **Autor exibido:** Pedro Figueiredo.
- **Gravação:** 16/11/2026, 22:10:20 BRT, com duração de 28,54 s.
- **Revisão:** 17/11/2026.
- **Caso:** [CT-RF120](../../Cenario_Teste/CT-RF120_Configuracoes_Acesso_Desktop.md).
- **Defeito:** Nenhum no fluxo avaliado.
- **Ambiente:** https://sifit.centrion.com.br/configuracoes · Chrome 157.0.8103.79 / Windows 10 (x86) · vídeo de 1918 × 998.

## Resultado e origem

Sim e Não foram salvos em sequência com HTTP 200 e `verifica_erro: false`. Após cada recarga, seletor, cartão Desktop e GET apresentaram o mesmo valor.

**Status:** Aprovado conforme a gravação.

## Arquivos

| Arquivo | Conteúdo | SHA-256 |
| --- | --- | --- |
| [desktop_sim_00-12.jpg](desktop_sim_00-12.jpg) | Campo e cartão Desktop em Sim após a recarga. | `bb0fff57afd2b355c6cf849ac974ceeba3854ea30b40175f2f201ebf284fd299` |
| [desktop_nao_00-24.jpg](desktop_nao_00-24.jpg) | Campo e cartão Desktop em Não após a segunda recarga. | `9a035aa7e2babba87b4e93ebb8d6568897f4cb251260b3b6dba9d88aef9f8595` |
| [linha_do_tempo.txt](linha_do_tempo.txt) | Cronologia de ações, rede e quadros consultados no Jam. | — |
| [origem.url](origem.url) | Endereço original do Jam. | — |

## Limites

Esta pasta contém a cronologia, a origem e os recortes dos quadros consultados. O vídeo permanece no Jam.

A aprovação cobre Configurações no navegador. A autenticação e o uso efetivo do cliente desktop não foram exercitados.
