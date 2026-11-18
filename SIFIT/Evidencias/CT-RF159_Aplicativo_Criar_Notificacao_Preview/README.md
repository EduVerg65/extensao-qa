# Evidência — CT-RF159: Criar uma notificação e conferir a prévia e a listagem

- **Fonte:** [Jam 3 — Criação de notificação com prévia](https://jam.dev/c/6720f25a-45e9-4e8d-9c5f-c48b0bfec5c0).
- **Autor exibido:** Pedro Figueiredo.
- **Gravação:** 16/11/2026, 22:41:22 BRT, com duração de 32,86 s.
- **Revisão:** 18/11/2026.
- **Caso:** [CT-RF159](../../Cenario_Teste/CT-RF159_Aplicativo_Criar_Notificacao_Preview.md).
- **Defeito:** Nenhum no fluxo avaliado.
- **Ambiente:** https://sifit.centrion.com.br/aplicativo · Chrome 157.0.8103.79 / Windows 10 (x86) · vídeo de 1918 × 998.

## Resultado e origem

A prévia mostrou TESTE DE MENSAGEM. Ao acionar Enviar aviso, a API retornou HTTP 201 com `verifica_erro: false`. A lista foi consultada novamente e exibiu o aviso de teste no topo.

**Status:** Aprovado conforme a gravação.

## Arquivos

| Arquivo | Conteúdo | SHA-256 |
| --- | --- | --- |
| [mensagem_e_previa_00-18.jpg](mensagem_e_previa_00-18.jpg) | Mensagem de teste no formulário e na prévia para celular. | `f7e8518d671b811a574b52e6ab82c4cb37e267aaaf0a42e8dbe74668ef021563` |
| [notificacao_criada_00-26.jpg](notificacao_criada_00-26.jpg) | Novo aviso de teste no início da listagem. | `464d83e2cfc6e62981dbeda6202394f0d14598e2eecc965056cdbc0d3f5e8b49` |
| [linha_do_tempo.txt](linha_do_tempo.txt) | Cronologia de ações, rede e quadros consultados no Jam. | — |
| [origem.url](origem.url) | Endereço original do Jam. | — |

## Limites

Os recortes e a cronologia omitem credenciais, valores de conexão e conteúdo que identifica terceiros. A gravação integral fica no Jam.

O resultado cobre a criação, a prévia e a listagem. A entrega efetiva no aplicativo dos alunos não foi verificada.
