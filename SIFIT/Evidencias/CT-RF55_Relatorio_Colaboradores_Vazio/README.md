# Evidência — CT-RF55: Relatório de Colaboradores gera arquivo vazio

- **Fonte:** [Jam original](https://jam.dev/c/3b4777a4-e1b0-4038-9b06-26c73669d7d1).
- **Autor exibido:** Gustavo Pelissari Oenning.
- **Gravação:** 15/11/2026, 19:09 BRT; duração de 58 s.
- **Revisão:** 15/11/2026.
- **Caso:** [CT-RF55](../../Cenario_Teste/CT-RF55_Relatorio_Colaboradores_Vazio.md).
- **Defeito:** [BUG-023](../../Relatorio-de-Bugs.md#bug-023), em triagem.
- **Ambiente:** https://sifit.centrion.com.br/relatorios; Chrome 157.0.8103.78, Windows 11 (x86), janela 1920 × 911.

## Resultado e origem

O relatório de Colaboradores é gerado com HTTP 200, mas o arquivo baixado tem 0 bytes (SHA-256 de arquivo vazio). A atividade do usuário não consta no Console do Jam; a seleção do tipo é confirmada pelo quadro do vídeo.

**Status:** Reprovado nas evidências — arquivo gerado vazio (0 bytes); defeito em triagem.

## Arquivos

| Arquivo | Conteúdo | SHA-256 |
| --- | --- | --- |
| [relatorio_4_vazio.pdf](relatorio_4_vazio.pdf) | Arquivo vazio — PDF de 0 bytes (SHA-256 de arquivo vazio). | `e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855` |
| [formulario_colaboradores_00-28.png](formulario_colaboradores_00-28.png) | tipo Colaboradores com o período. | `e1964c1f680999c39ce17e2401426ea922f7994fbb040d9de06de3d21b15cfa3` |
| [rede_lista.png](rede_lista.png) | oito POST relatorio (HTTP 200) e um OPTIONS. | `ecd2414b90cbba8bf93464a4691473a1881f9089b4d3a45cd6d145f309dba798` |
| [linha_do_tempo.txt](linha_do_tempo.txt) | Cronologia de ações, digitação e rede do Jam. | — |
| [origem.url](origem.url) | Endereço original do Jam. | — |

## Limites

Esta pasta contém documentação da consulta, capturas extraídas da reprodução do Jam e a cronologia; não contém cópia do vídeo, e nenhum hash de vídeo foi gerado. As capturas mostram o botão de reprodução do Jam sobreposto. A mesma gravação é a fonte de vários casos.

O conteúdo da resposta das requisições não foi capturado. A correspondência entre este arquivo e o tipo de relatório é inferida pela ordem dos downloads e pela ordem de seleção dos tipos no vídeo (os arquivos 5 a 7 foram identificados pelo conteúdo e seguem a mesma ordem); o corpo da requisição não foi capturado pelo Jam.

Não houve execução da aplicação, inspeção de código, acesso ao banco ou reteste nesta revisão.
