# Evidência — CT-RF105: Cadastro de tipo de pagamento com status Ativo não é refletido

- **Fonte:** [Jam original](https://jam.dev/c/e8734e3d-3f8e-458b-8c7d-e85eea882e50).
- **Autor exibido:** Gustavo Pelissari Oenning.
- **Gravação:** 15/11/2026, 22:03 BRT; duração de 1 min.
- **Revisão:** 15/11/2026.
- **Caso:** [CT-RF105](../../Cenario_Teste/CT-RF105_Cadastro_Tipo_Pagamento_Status.md).
- **Defeito:** [BUG-042](../../Relatorio-de-Bugs.md#bug-042), em triagem.
- **Ambiente:** https://sifit.centrion.com.br/tipos-pagamento; Chrome 157.0.8103.78, Windows 11 (x86), janela 1920 × 855.

## Resultado e origem

O cadastro retornou HTTP 201 e elevou Total e Inativos para 17, mas o status Ativo escolhido não foi enviado e o cartão Ativos permaneceu em 0, com todos os tipos exibidos como Inativo.

**Status:** Reprovado nas evidências — status Ativo escolhido não é enviado nem refletido; defeito em triagem.

## Arquivos

| Arquivo | Conteúdo | SHA-256 |
| --- | --- | --- |
| [cartoes_antes_00-00.jpg](cartoes_antes_00-00.jpg) | Total 16, Ativos 0, Inativos 16 e Via gateway 5. | `4248e9f1669c77bff6507bbeff8ef63df748e48f459f683039ba144359bb80f3` |
| [modal_cadastro_00-19.jpg](modal_cadastro_00-19.jpg) | Nome 44444, Status Ativo, Tipo Débito. | `e07fa570fcf2346dc4ebbd2a2c4d23f7e44dd8d4f33a4650ecbe2577b5d3ffbc` |
| [modal_selecoes_00-24.jpg](modal_selecoes_00-24.jpg) | Escolher Bandeira Sim e Pagamento Pelo Sistema Não ainda exibidos. | `23dccd54ccf9e02ae83a00fa73e4c0d16a341ac80061736524f0f83385021238` |
| [lista_apos_cadastro_00-27.jpg](lista_apos_cadastro_00-27.jpg) | Total 17, Ativos 0, Inativos 17 e Via gateway 6. | `f18cc60b187013e0d39e4b8662bbd8be577a429ab2cd86b0e9f4677f3b23efe0` |
| [rede_lista.jpg](rede_lista.jpg) | 18 entradas da gravação (POST, OPTIONS, GET e temas), com os dois POST deleta em HTTP 404. | `b38c881654bd91b7766e435bfc261119bb28f40499de148cf2ec0b156fbcad6d` |
| [linha_do_tempo.txt](linha_do_tempo.txt) | Cronologia de ações, digitação e rede do Jam. | — |
| [origem.url](origem.url) | Endereço original do Jam. | — |

## Limites

Esta pasta contém documentação da consulta, capturas extraídas da reprodução do Jam e a cronologia; não contém cópia do vídeo, e nenhum hash de vídeo foi gerado. As capturas são quadros do vídeo e incluem a barra de gravação do Jam. A mesma gravação é a fonte de vários casos.

Não foram confirmados a regra do status, o status do novo tipo na listagem e a persistência após recarga.

Não houve execução da aplicação, inspeção de código, acesso ao banco ou reteste nesta revisão.
