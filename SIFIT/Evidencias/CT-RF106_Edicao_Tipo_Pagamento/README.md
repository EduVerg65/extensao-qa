# Evidência — CT-RF106: Edição de tipo de pagamento pela lupa da listagem

- **Fonte:** [Jam original](https://jam.dev/c/e8734e3d-3f8e-458b-8c7d-e85eea882e50).
- **Autor exibido:** Gustavo Pelissari Oenning.
- **Gravação:** 15/11/2026, 22:03 BRT; duração de 1 min.
- **Revisão:** 15/11/2026.
- **Caso:** [CT-RF106](../../Cenario_Teste/CT-RF106_Edicao_Tipo_Pagamento.md).
- **Defeito:** nenhum no fluxo avaliado.
- **Ambiente:** https://sifit.centrion.com.br/tipos-pagamento; Chrome 157.0.8103.78, Windows 11 (x86), janela 1920 × 855.

## Resultado e origem

A edição do tipo Dinheiro retornou HTTP 200 sem erro e a listagem refletiu Pagamento Pelo Sistema Não, com Via gateway de 6 para 5.

**Status:** Aprovado conforme a gravação.

## Arquivos

| Arquivo | Conteúdo | SHA-256 |
| --- | --- | --- |
| [edicao_salvando_00-34.jpg](edicao_salvando_00-34.jpg) | Dinheiro, Pagamento Pelo Sistema Não, botão Salvando. | `326a8d9a00617dbf06abf7e61ddf6f487f72e597bf41dd761d426305dcc52a5f` |
| [lista_apos_edicao_00-45.jpg](lista_apos_edicao_00-45.jpg) | Dinheiro com Via gateway Não; Total 17 e Via gateway 5. | `1e546b356818774a720bd800dc89e46096c14278b493e8b1a345033f90e966ea` |
| [rede_lista.jpg](rede_lista.jpg) | 18 entradas da gravação (POST, OPTIONS, GET e temas), com os dois POST deleta em HTTP 404. | `b38c881654bd91b7766e435bfc261119bb28f40499de148cf2ec0b156fbcad6d` |
| [linha_do_tempo.txt](linha_do_tempo.txt) | Cronologia de ações, digitação e rede do Jam. | — |
| [origem.url](origem.url) | Endereço original do Jam. | — |

## Limites

Esta pasta contém documentação da consulta, capturas extraídas da reprodução do Jam e a cronologia; não contém cópia do vídeo, e nenhum hash de vídeo foi gerado. As capturas são quadros do vídeo e incluem a barra de gravação do Jam. A mesma gravação é a fonte de vários casos.

Não foram confirmados a persistência após recarga e a edição de outros campos.

Não houve execução da aplicação, inspeção de código, acesso ao banco ou reteste nesta revisão.
