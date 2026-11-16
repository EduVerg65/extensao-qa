# Evidência — CT-RF93: Busca de colaborador no cadastro de conta a pagar

- **Fonte:** [Jam original](https://jam.dev/c/5d0afaf4-5abd-4e85-923f-27448304a9ef).
- **Autor exibido:** Gustavo Pelissari Oenning.
- **Gravação:** 15/11/2026, 21:58 BRT; duração de 1 min.
- **Revisão:** 15/11/2026.
- **Caso:** [CT-RF93](../../Cenario_Teste/CT-RF93_Busca_Colaborador_Conta_Pagar.md).
- **Defeito:** nenhum confirmado; ponto a validar.
- **Ambiente:** https://sifit.centrion.com.br/contas-pagar; Chrome 157.0.8103.78, Windows 11 (x86), janela 1920 × 911.

## Resultado e origem

A busca de colaborador com o termo "sds" devolveu lista vazia e o modal não apresentou mensagem de resultado vazio; a busca com resultado e a seleção não foram exercitadas.

**Status:** A validar — regra ou contexto pendente.

## Arquivos

| Arquivo | Conteúdo | SHA-256 |
| --- | --- | --- |
| [modal_buscar_colaborador_00-26.png](modal_buscar_colaborador_00-26.png) | tabela sem linhas nem mensagem de resultado vazio. | `5cc54f056fedaa181c66af93180590b8436c392b6515a284a60acfd3e7226695` |
| [rede_lista.jpg](rede_lista.jpg) | primeiras 31 entradas da gravação. | `b80601de3e09b18c93ee63df32a0b2dd01269fbc1b86a85f60904fca406fc507` |
| [linha_do_tempo.txt](linha_do_tempo.txt) | Cronologia de ações, digitação e rede do Jam. | — |
| [origem.url](origem.url) | Endereço original do Jam. | — |

## Limites

Esta pasta contém documentação da consulta, capturas extraídas da reprodução do Jam e a cronologia; não contém cópia do vídeo, e nenhum hash de vídeo foi gerado. As capturas mostram o botão de reprodução do Jam sobreposto. A mesma gravação é a fonte de vários casos.

Não foram confirmados a busca com resultado, a seleção do colaborador e a mensagem de resultado vazio esperada.

Não houve execução da aplicação, inspeção de código, acesso ao banco ou reteste nesta revisão.
