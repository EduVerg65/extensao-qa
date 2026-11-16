# Evidência — CT-RF89: Telefone do lead aceita 30 dígitos sem validação

- **Fonte:** [Jam original](https://jam.dev/c/308607ff-8abc-40af-8c7c-429ce506ed64).
- **Autor exibido:** Gustavo Pelissari Oenning.
- **Gravação:** 15/11/2026, 21:52 BRT; duração de 1 min 2 s.
- **Revisão:** 15/11/2026.
- **Caso:** [CT-RF89](../../Cenario_Teste/CT-RF89_Telefone_Lead_Sem_Validacao.md).
- **Defeito:** [BUG-038](../../Relatorio-de-Bugs.md#bug-038), em triagem.
- **Ambiente:** https://sifit.centrion.com.br/prospeccao; Chrome 157.0.8103.78, Windows 11 (x86), janela 1920 × 911.

## Resultado e origem

O campo Telefone aceitou 30 dígitos sem máscara nem mensagem, o lead foi criado (id 10) e o valor de 30 dígitos retornou na consulta do lead.

**Status:** Reprovado nas evidências — telefone de 30 dígitos aceito e gravado; defeito em triagem.

## Arquivos

| Arquivo | Conteúdo | SHA-256 |
| --- | --- | --- |
| [telefone_30_digitos_00-47.png](telefone_30_digitos_00-47.png) | valor longo sem máscara (recorte do quadro; demais campos omitidos). | `3b7ca3334edfbf6e29085fb88f3bb883c4524e3f0e26acb2187eb6c63c88297d` |
| [requisicao_salvar.png](requisicao_salvar.png) | Corpo da requisição salvar-lead com o telefone de 30 dígitos (e-mail mascarado pelo Jam). | `286064037f65110b9e494066e518c8e0bc53ab9aec18dd0c4028716b9f3b604f` |
| [resposta_buscar.png](resposta_buscar.png) | telefone de 30 dígitos gravado no lead 10. | `fad9d17f7746837a5b2393b2464b8d9b78b5325250a1d0679642b450daa75d5c` |
| [rede_lista.jpg](rede_lista.jpg) | 16 entradas da gravação. | `086e2ef346f296db2a43a6e695d9ae73ca4e84b7afb12f71364230da20f4bc52` |
| [linha_do_tempo.txt](linha_do_tempo.txt) | Cronologia de ações, digitação e rede do Jam. | — |
| [origem.url](origem.url) | Endereço original do Jam. | — |

## Limites

Esta pasta contém documentação da consulta, capturas extraídas da reprodução do Jam e a cronologia; não contém cópia do vídeo, e nenhum hash de vídeo foi gerado. As capturas mostram o botão de reprodução do Jam sobreposto. A mesma gravação é a fonte de vários casos.

Não foram confirmados a regra do campo, a validação no servidor e o comportamento com outros tamanhos e caracteres. O recorte do campo omite o e-mail e os demais dados do formulário.

Não houve execução da aplicação, inspeção de código, acesso ao banco ou reteste nesta revisão.
