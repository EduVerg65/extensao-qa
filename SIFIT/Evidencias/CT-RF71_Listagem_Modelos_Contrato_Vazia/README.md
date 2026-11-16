# Evidência — CT-RF71: Listagem de modelos de contrato aparece vazia com 15 modelos retornados

- **Fonte:** [Jam original](https://jam.dev/c/44dbbd39-6915-45d6-8dd1-5f30c1432ca0).
- **Autor exibido:** Gustavo Pelissari Oenning.
- **Gravação:** 15/11/2026, 21:55 BRT; duração de 50 s.
- **Revisão:** 15/11/2026.
- **Caso:** [CT-RF71](../../Cenario_Teste/CT-RF71_Listagem_Modelos_Contrato_Vazia.md).
- **Defeito:** [BUG-026](../../Relatorio-de-Bugs.md#bug-026), em triagem.
- **Ambiente:** https://sifit.centrion.com.br/modelos-contrato; Chrome 157.0.8103.78, Windows 11 (x86), janela 1920 × 855.

## Resultado e origem

A resposta de modelos-contrato traz 15 modelos, mas a tabela da tela permanece com apenas o cabeçalho antes e depois do cadastro, sem mensagem de estado vazio.

**Status:** Reprovado nas evidências — tabela vazia com 15 modelos retornados; defeito em triagem.

## Arquivos

| Arquivo | Conteúdo | SHA-256 |
| --- | --- | --- |
| [lista_vazia_00-39.png](lista_vazia_00-39.png) | tabela sem linhas após o cadastro. | `66980e7c28b0a520d49cfc8621eaac1837b18649318431e672e32a797d69c5bb` |
| [lista_vazia_00-45.png](lista_vazia_00-45.png) | tabela ainda sem linhas. | `1d755dbd533297013162b4756ce401a365699c33898764a0529677b84e7557ed` |
| [lista_vazia_00-49.png](lista_vazia_00-49.png) | tabela sem linhas e sem mensagem. | `279a317d42ddc50d26dfdc2272ee9b0f1675a845d48113afec2f42cc3ba3ed2a` |
| [lista_servidor_resposta.png](lista_servidor_resposta.png) | lista com modelos de ids 1 em diante (início da lista). | `c9741cfdfc4f7721f6a8eed0d389c0831c33a5ef2b2c87f2731ba817089ea6a1` |
| [rede_lista.jpg](rede_lista.jpg) | 28 entradas da gravação. | `46a7c120d2cc24837d370275468a35b863a46759a9610345422f77431da894c6` |
| [linha_do_tempo.txt](linha_do_tempo.txt) | Cronologia de ações, digitação e rede do Jam. | — |
| [origem.url](origem.url) | Endereço original do Jam. | — |

## Limites

Esta pasta contém documentação da consulta, capturas extraídas da reprodução do Jam e a cronologia; não contém cópia do vídeo, e nenhum hash de vídeo foi gerado. As capturas mostram o botão de reprodução do Jam sobreposto. A mesma gravação é a fonte de vários casos.

Não foram confirmados a causa, o comportamento após recarga e a leitura da tabela por tecnologia assistiva.

Não houve execução da aplicação, inspeção de código, acesso ao banco ou reteste nesta revisão.
