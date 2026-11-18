# Evidência — CT-RF119: Conferir a configuração Academia marcada como Box?

- **Fonte:** [Jam original](https://jam.dev/c/16dc862d-c3f9-4392-9037-526818e86cd6).
- **Autor exibido:** Pedro Figueiredo.
- **Gravação:** 16/11/2026, 22:08:35 BRT, com duração de 33,63 s.
- **Revisão:** 17/11/2026.
- **Caso:** [CT-RF119](../../Cenario_Teste/CT-RF119_Configuracoes_Academia_Marcada_Box.md).
- **Defeito:** Nenhum no fluxo avaliado.
- **Ambiente:** https://sifit.centrion.com.br/configuracoes · Chrome 157.0.8103.79 / Windows 10 (x86) · vídeo de 1918 × 998.

## Resultado e origem

Após salvar Sim e recarregar, o seletor e o cartão exibiram Sim e SifitBox apareceu no menu Principal. Depois de salvar Não e recarregar, seletor e cartão voltaram a Não e o item deixou de aparecer. A API retornou os mesmos estados de `sifitbox`.

**Status:** Aprovado conforme a gravação.

## Arquivos

| Arquivo | Conteúdo | SHA-256 |
| --- | --- | --- |
| [sifitbox_sim_00-17.jpg](sifitbox_sim_00-17.jpg) | Box em Sim após a recarga, com cartão e item no menu. | `87eed95f0a9f5fa1bf03c3d79f8d33e2d49290977ccb3b53798e4941522d1653` |
| [sifitbox_nao_00-29.jpg](sifitbox_nao_00-29.jpg) | Box em Não após a recarga, com cartão e menu atualizados. | `8d7d9b1506143bf8a078a179023c7e31de7c61e1243402d05b265374c67d99f6` |
| [linha_do_tempo.txt](linha_do_tempo.txt) | Cronologia de ações, rede e quadros consultados no Jam. | — |
| [origem.url](origem.url) | Endereço original do Jam. | — |

## Limites

Esta pasta contém a cronologia, a origem e os recortes dos quadros consultados. O vídeo permanece no Jam.

Foram verificadas persistência e visibilidade do item no menu. Operações e permissões internas do SifitBox não foram exercitadas.
