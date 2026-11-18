# Evidência — CT-RF164: Persistir a alteração da porta do aparelho de Biometria

- **Fonte:** [Jam 8 — Persistência da porta do aparelho](https://jam.dev/c/7d7bf60a-d8a8-4b7e-80da-1e73b45819cb).
- **Autor exibido:** Pedro Figueiredo.
- **Gravação:** 16/11/2026, 23:05:55 BRT, com duração de 20,40 s.
- **Revisão:** 18/11/2026.
- **Caso:** [CT-RF164](../../Cenario_Teste/CT-RF164_Configuracoes_Biometria_Persistir_Porta.md).
- **Defeito:** Nenhum no fluxo avaliado.
- **Ambiente:** https://sifit.centrion.com.br/configuracoes · Chrome 157.0.8103.79 / Windows 10 (x86) · vídeo de 1918 × 998.

## Resultado e origem

O POST retornou HTTP 200 com `verifica_erro: false`. Após recarregar, `porta_aparelho` no GET correspondia ao valor enviado e o campo Porta mostrava o novo valor. A gravação termina após o POST de restauração, também com sucesso.

**Status:** Aprovado conforme a gravação.

## Arquivos

| Arquivo | Conteúdo | SHA-256 |
| --- | --- | --- |
| [salvar_porta_00-06.jpg](salvar_porta_00-06.jpg) | Campo Porta editado antes do salvamento, com dados de conexão ocultos. | `f8ced4555ee7d12d14f96b1430a3d1490d3551fbbb0132f1df1a7ca7df5806c8` |
| [porta_apos_recarregar_00-14.jpg](porta_apos_recarregar_00-14.jpg) | Campo Porta ao reabrir Biometria, com dados de conexão ocultos. | `aa9b57919cd9b8d922ae8bc72354f92805f7994f71697a46cdcab91c95ec2bc8` |
| [linha_do_tempo.txt](linha_do_tempo.txt) | Cronologia de ações, rede e quadros consultados no Jam. | — |
| [origem.url](origem.url) | Endereço original do Jam. | — |

## Limites

Os recortes e a cronologia omitem credenciais, valores de conexão e conteúdo que identifica terceiros. A gravação integral fica no Jam.

A gravação cobre a persistência da primeira alteração. A conectividade e a nova leitura após a restauração ficaram fora do trecho.
