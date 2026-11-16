# Evidência — CT-RF63: Visualização e edição de lead na tela Prospecção

- **Fonte:** [Jam original](https://jam.dev/c/308607ff-8abc-40af-8c7c-429ce506ed64).
- **Autor exibido:** Gustavo Pelissari Oenning.
- **Gravação:** 15/11/2026, 21:52 BRT; duração de 1 min 2 s.
- **Revisão:** 15/11/2026.
- **Caso:** [CT-RF63](../../Cenario_Teste/CT-RF63_Edicao_Lead_Prospeccao.md).
- **Defeito:** nenhum no fluxo avaliado.
- **Ambiente:** https://sifit.centrion.com.br/prospeccao; Chrome 157.0.8103.78, Windows 11 (x86), janela 1920 × 911.

## Resultado e origem

A lupa abre o modal com os dados do lead 10; o nome é alterado para "testetete", `POST atualizar-lead/1` retorna HTTP 200 sem erro e a listagem apresenta o novo nome.

**Status:** Aprovado conforme a gravação.

## Arquivos

| Arquivo | Conteúdo | SHA-256 |
| --- | --- | --- |
| [visualizar_lead_00-47.png](visualizar_lead_00-47.png) | código 10, estágio Interessado e nome (recorte do quadro; e-mail e telefone omitidos). | `6fc2ee548d7eb9cfe62376058df69429055e4d74605f4772d3b4f58fa022b44e` |
| [nome_editado_00-57.png](nome_editado_00-57.png) | Nome em edição em 0:57 (recorte do quadro; e-mail e telefone omitidos). | `54e21365d3a1370581ba49f1d1e50e8195e61a19f0d489b06e6a4444ee12f505` |
| [lista_apos_edicao_01-01.png](lista_apos_edicao_01-01.png) | lead 10 com o nome "testetete". | `8cc791c4147a781c3c86215b05e92e3c43102e73ded0b157922ced09050b23d1` |
| [requisicao_buscar.png](requisicao_buscar.png) | id 10. | `36828f65e0882b4dec67a3dcf278369470564da41103a28c776ca0fb00809425` |
| [resposta_buscar.png](resposta_buscar.png) | dados do lead 10. | `fad9d17f7746837a5b2393b2464b8d9b78b5325250a1d0679642b450daa75d5c` |
| [requisicao_atualizar.png](requisicao_atualizar.png) | id 10 e nome testetete (e-mail mascarado pelo Jam). | `35d6d2cf8e18458fc35b251e13083f2d66338c54ac7d66e11a132bacbb085997` |
| [resposta_atualizar.png](resposta_atualizar.png) | verifica_erro false. | `85ee94fc089da0321509851a74944b48dec652fc474cd329ee69c591eea7a41e` |
| [linha_do_tempo.txt](linha_do_tempo.txt) | Cronologia de ações, digitação e rede do Jam. | — |
| [origem.url](origem.url) | Endereço original do Jam. | — |

## Limites

Esta pasta contém documentação da consulta, capturas extraídas da reprodução do Jam e a cronologia; não contém cópia do vídeo, e nenhum hash de vídeo foi gerado. As capturas mostram o botão de reprodução do Jam sobreposto. A mesma gravação é a fonte de vários casos.

Não foram confirmados a persistência após recarga, a edição dos demais campos e a validação de campos obrigatórios. Os recortes do modal omitem o e-mail e o telefone.

Não houve execução da aplicação, inspeção de código, acesso ao banco ou reteste nesta revisão.
