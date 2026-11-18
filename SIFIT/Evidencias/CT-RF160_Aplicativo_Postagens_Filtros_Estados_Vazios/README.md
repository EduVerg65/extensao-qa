# Evidência — CT-RF160: Alternar o filtro de postagens e abrir a lista completa

- **Fonte:** Jam 4 — Filtros e lista completa de postagens (gravação restrita por conter dados de integração ou dados de alunos).
- **Autor exibido:** Pedro Figueiredo.
- **Gravação:** 16/11/2026, 22:43:07 BRT, com duração de 20,67 s.
- **Revisão:** 18/11/2026.
- **Caso:** [CT-RF160](../../Cenario_Teste/CT-RF160_Aplicativo_Postagens_Filtros_Estados_Vazios.md).
- **Defeito:** Nenhum no fluxo avaliado.
- **Ambiente:** https://sifit.centrion.com.br/aplicativo · Chrome 157.0.8103.79 / Windows 10 (x86) · vídeo de 1918 × 998.

## Resultado e origem

A lista alternou entre os dois avisos e o diálogo abriu com o filtro ativo nas duas tentativas. Em ambas, o total exibido no diálogo era zero. Fechar retornou ao painel.

**Status:** Aprovado conforme a gravação.

## Arquivos

| Arquivo | Conteúdo | SHA-256 |
| --- | --- | --- |
| [postagens_todas_00-12.jpg](postagens_todas_00-12.jpg) | Diálogo em todas as postagens com o aviso de lista vazia. | `71ac1fedf80851416bce266959c838cbd9c483060358c4cf9ee56596f5a9ecf0` |
| [postagens_pendentes_00-18.jpg](postagens_pendentes_00-18.jpg) | Diálogo filtrado pelas pendentes e sem postagens aguardando aprovação. | `4e389b988c9607a86716a7fe69796b85512055d12d6f6162cef42764f5869172` |
| [linha_do_tempo.txt](linha_do_tempo.txt) | Cronologia de ações, rede e quadros consultados no Jam. | — |
| [origem.url](origem.url) | Página testada. O link da gravação fica restrito. | — |

## Limites

Os recortes e a cronologia omitem credenciais, valores de conexão e conteúdo que identifica terceiros. A gravação integral fica no Jam.

A aprovação se limita à base vazia e à troca dos avisos. A filtragem de registros com estados diferentes exige massa de teste.
