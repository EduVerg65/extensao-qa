# Evidência — CT-RF163: Rejeitar um valor sem formato de IP em Biometria

- **Fonte:** Jam 7 — Validação de IP do aparelho (gravação restrita por conter dados de integração ou dados de alunos).
- **Autor exibido:** Pedro Figueiredo.
- **Gravação:** 16/11/2026, 23:03:49 BRT, com duração de 27,52 s.
- **Revisão:** 18/11/2026.
- **Caso:** [CT-RF163](../../Cenario_Teste/CT-RF163_Configuracoes_Biometria_Rejeitar_IP_Invalido.md).
- **Defeito:** [BUG-053](../../Relatorio-de-Bugs.md#bug-053), em triagem.
- **Ambiente:** https://sifit.centrion.com.br/configuracoes · Chrome 157.0.8103.79 / Windows 10 (x86) · vídeo de 1918 × 998.

## Resultado e origem

O salvamento retornou HTTP 200. Depois de recarregar, o GET devolveu a sequência numérica sem separadores em `ip_aparelho`. O formulário reaberto manteve essa entrada.

**Status:** Reprovado nas evidências.

## Arquivos

| Arquivo | Conteúdo | SHA-256 |
| --- | --- | --- |
| [campo_ip_antes_de_salvar_00-14.jpg](campo_ip_antes_de_salvar_00-14.jpg) | Campo IP em edição antes de salvar, com dados de conexão ocultos. | `0373b61d3ba443988584eb669f1a5abec089c26cfd04ebe8aa7c4cd617baa734` |
| [campo_ip_apos_recarregar_00-22.jpg](campo_ip_apos_recarregar_00-22.jpg) | Campo IP após recarregar, com os valores de integração ocultos. | `de9aac61f5a2f51543d126c25fe97ecc0cb575688d2e70e39a07d6c8da38351b` |
| [linha_do_tempo.txt](linha_do_tempo.txt) | Cronologia de ações, rede e quadros consultados no Jam. | — |
| [origem.url](origem.url) | Página testada. O link da gravação fica restrito. | — |

## Limites

Os recortes e a cronologia omitem credenciais, valores de conexão e conteúdo que identifica terceiros. A gravação integral fica no Jam.

A leitura posterior comprova o valor armazenado. A gravação não verifica a tentativa de conexão ao aparelho.
