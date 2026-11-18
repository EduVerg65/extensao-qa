# Evidência — CT-RF158: Impedir o envio de uma notificação sem mensagem

- **Fonte:** Jam 2 — Validação de mensagem obrigatória (gravação restrita por conter dados de integração ou dados de alunos).
- **Autor exibido:** Pedro Figueiredo.
- **Gravação:** 16/11/2026, 22:40:04 BRT, com duração de 13,11 s.
- **Revisão:** 18/11/2026.
- **Caso:** [CT-RF158](../../Cenario_Teste/CT-RF158_Aplicativo_Bloquear_Notificacao_Vazia.md).
- **Defeito:** Nenhum no fluxo avaliado.
- **Ambiente:** https://sifit.centrion.com.br/aplicativo · Chrome 157.0.8103.79 / Windows 10 (x86) · vídeo de 1918 × 998.

## Resultado e origem

O formulário abriu com contador em zero. Os cliques na região de Enviar aviso não iniciaram a criação. O botão permaneceu desabilitado e Cancelar fechou o formulário.

**Status:** Aprovado conforme a gravação.

## Arquivos

| Arquivo | Conteúdo | SHA-256 |
| --- | --- | --- |
| [notificacao_sem_mensagem_00-05.jpg](notificacao_sem_mensagem_00-05.jpg) | Formulário vazio, contador em zero e ação Enviar aviso desabilitada. | `e2d4ac9f9a05ee8d450a27cd2da67ddb8bbf706daff36c8c6d76f8b62392a8d4` |
| [acao_enviar_desabilitada_00-09.jpg](acao_enviar_desabilitada_00-09.jpg) | Ação Enviar aviso permanece desabilitada durante a tentativa. | `63a5485d58cad62c7978d5fc94b73ec7134791236b2ac2fabe0a9d850ce3f946` |
| [linha_do_tempo.txt](linha_do_tempo.txt) | Cronologia de ações, rede e quadros consultados no Jam. | — |
| [origem.url](origem.url) | Página testada. O link da gravação fica restrito. | — |

## Limites

Os recortes e a cronologia omitem credenciais, valores de conexão e conteúdo que identifica terceiros. A gravação integral fica no Jam.

A evidência cobre o campo totalmente vazio. Espaços em branco e limites de comprimento ficam para nova execução.
