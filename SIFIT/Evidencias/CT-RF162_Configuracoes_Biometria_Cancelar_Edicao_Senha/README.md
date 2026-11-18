# Evidência — CT-RF162: Cancelar a edição da senha de Biometria

- **Fonte:** [Jam 6 — Cancelamento da edição no formulário de Biometria](https://jam.dev/c/ccac55df-d2c8-4b11-898b-d12d87aced72).
- **Autor exibido:** Pedro Figueiredo.
- **Gravação:** 16/11/2026, 23:02:14 BRT, com duração de 22,59 s.
- **Revisão:** 18/11/2026.
- **Caso:** [CT-RF162](../../Cenario_Teste/CT-RF162_Configuracoes_Biometria_Cancelar_Edicao_Senha.md).
- **Defeito:** Nenhum no fluxo avaliado.
- **Ambiente:** https://sifit.centrion.com.br/configuracoes · Chrome 157.0.8103.79 / Windows 10 (x86) · vídeo de 1918 × 998.

## Resultado e origem

Após editar Senha e sair pelo botão Cancelar, a Página Inicial foi exibida. A captura não registrou POST de configuração. Ao voltar a Biometria, o valor anterior estava no campo.

**Status:** Aprovado conforme a gravação.

## Arquivos

| Arquivo | Conteúdo | SHA-256 |
| --- | --- | --- |
| [formulario_senha_antes_cancelar_00-08.jpg](formulario_senha_antes_cancelar_00-08.jpg) | Formulário antes de Cancelar, com os dados de conexão ocultos. | `378c1e5e20b4986035661aeba0b89ae629f792bdb467976233debf195bf3174e` |
| [biometria_reaberta_00-20.jpg](biometria_reaberta_00-20.jpg) | Aba Biometria reaberta após o cancelamento, com os mesmos campos ocultos. | `96ae1cfe1117df34cc729f0e659680a2bf0aaed37a887321e8ce88f942f2eee1` |
| [linha_do_tempo.txt](linha_do_tempo.txt) | Cronologia de ações, rede e quadros consultados no Jam. | — |
| [origem.url](origem.url) | Endereço original do Jam. | — |

## Limites

Os recortes e a cronologia omitem credenciais, valores de conexão e conteúdo que identifica terceiros. A gravação integral fica no Jam.

A aprovação cobre o cancelamento. O comportamento de mascaramento de Senha está documentado no BUG-046.
