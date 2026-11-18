# Evidência — CT-RF152: Alterar o tipo de avaliação para Bioimpedância

- **Fonte:** [Jam 2 — Alteração do tipo para Bioimpedância](https://jam.dev/c/8685a48a-ed9a-4169-a825-90036265b185).
- **Autor exibido:** Pedro Figueiredo.
- **Gravação:** 16/11/2026, 23:11:02 BRT, com duração de 18,94 s.
- **Revisão:** 18/11/2026.
- **Caso:** [CT-RF152](../../Cenario_Teste/CT-RF152_Configuracoes_Avaliacao_Tipo_Bioimpedancia.md).
- **Defeito:** Nenhum no fluxo avaliado.
- **Ambiente:** https://sifit.centrion.com.br/configuracoes · Chrome 157.0.8103.79 / Windows 10 (x86) · vídeo de 1918 × 998.

## Resultado e origem

O salvamento de Bioimpedância retornou HTTP 200 com `verifica_erro: false`. Após recarregar, a consulta devolveu `tipo_avaliacao: BIOIMPEDANCIA` e o seletor mostrou Bioimpedância. O cartão de resumo Avaliação também exibiu Bioimpedância. O POST de restauração para Dobras retornou sucesso.

**Status:** Aprovado conforme a gravação.

## Arquivos

| Arquivo | Conteúdo | SHA-256 |
| --- | --- | --- |
| [tipo_dobras_00-01.jpg](tipo_dobras_00-01.jpg) | Tipo Dobras no formulário e no cartão de resumo antes da alteração. | `ca6a747a4b1b2d1ead9fd3f5cfd1f0f96ae67b5bcbc5600578193acdd301b4c0` |
| [tipo_bioimpedancia_00-12.jpg](tipo_bioimpedancia_00-12.jpg) | Bioimpedância no formulário e no cartão após reabrir Avaliação. | `3bac1ad9dcd59d97e247ed3efe4204a7d45806fdd2902f65dcdcf074804383d1` |
| [linha_do_tempo.txt](linha_do_tempo.txt) | Cronologia de ações, rede e quadros consultados no Jam. | — |
| [origem.url](origem.url) | Endereço original do Jam. | — |

## Limites

Os recortes e a cronologia omitem valores dos campos de integração, identificadores de conta e dados de autenticação. A gravação integral fica no Jam.

O tipo foi conferido no formulário e no cartão de resumo de Configurações. A gravação não cobre a criação de uma avaliação nesse tipo.
