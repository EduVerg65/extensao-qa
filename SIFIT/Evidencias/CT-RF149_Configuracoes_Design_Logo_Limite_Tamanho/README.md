# Evidência — CT-RF149: Informar o limite de tamanho ao rejeitar o logo

- **Fonte:** [Jam 5 — Rejeição de logo pelo limite de tamanho](https://jam.dev/c/7aaeac50-8269-4cd6-b7f6-4c8c3740b0e5).
- **Autor exibido:** Pedro Figueiredo.
- **Gravação:** 16/11/2026, 23:27:58 BRT, com duração de 18,41 s.
- **Revisão:** 17/11/2026.
- **Caso:** [CT-RF149](../../Cenario_Teste/CT-RF149_Configuracoes_Design_Logo_Limite_Tamanho.md).
- **Defeito:** [BUG-052](../../Relatorio-de-Bugs.md#bug-052), em triagem.
- **Ambiente:** https://sifit.centrion.com.br/configuracoes · Chrome 157.0.8103.79 / Windows 10 (x86) · vídeo de 1918 × 998.

## Resultado e origem

A imagem selecionada apareceu na prévia. No salvamento, a API retornou HTTP 400 com “O arquivo deve ter no máximo 6 MB.” O diálogo mostrou apenas “Erro ao salvar configurações”. A prévia permaneceu na tela após fechar o diálogo.

**Status:** Reprovado nas evidências.

## Arquivos

| Arquivo | Conteúdo | SHA-256 |
| --- | --- | --- |
| [previa_logo_00-08.jpg](previa_logo_00-08.jpg) | Prévia da imagem selecionada no cartão Logo. | `34f61a3e9ccbdcefcdb193ef912b60a5b0db7a85cb4f7d51bdd47bc548fea195` |
| [erro_generico_ao_salvar_00-12.jpg](erro_generico_ao_salvar_00-12.jpg) | Diálogo genérico após a rejeição pela API. | `dc7ced449e04850fb2c2edcaaefe4238667197d302083332d0f32539022a77ac` |
| [linha_do_tempo.txt](linha_do_tempo.txt) | Cronologia de ações, rede e quadros consultados no Jam. | — |
| [origem.url](origem.url) | Endereço original do Jam. | — |

## Limites

Os recortes e a cronologia omitem valores dos campos de integração, identificadores de conta e dados de autenticação. A gravação integral fica no Jam.

O total em bytes corresponde à requisição inteira. O tamanho exato do arquivo e o logo armazenado após recarregar não ficaram demonstrados.
