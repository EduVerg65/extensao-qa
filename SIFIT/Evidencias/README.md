# Evidências — SIFIT

## Inclusão de 15/11/2026

Documentação da consulta aos três links do Jam, na ordem solicitada. As pastas contêm resumo, cronologia e origem; os vídeos e as capturas permanecem no Jam e não foram copiados localmente.

| Caso | Evidência | Resultado |
| --- | --- | --- |
| [CT-RF23](../Cenario_Teste/CT-RF23_Exclusao_Exercicio.md) | [Exclusão de exercício](CT-RF23_Exclusao_Exercicio/README.md) | Aprovado no trecho consultado. |
| [CT-RF24](../Cenario_Teste/CT-RF24_Edicao_Exercicio.md) | [Edição de exercício aumenta o total e mantém duas entradas](CT-RF24_Edicao_Exercicio/README.md) | Reprovado no trecho consultado; confirmar operação e identidade dos registros na reprodução. |
| [CT-RF25](../Cenario_Teste/CT-RF25_Envio_Exercicio_Imagem.md) | [Envio de exercício com imagem](CT-RF25_Envio_Exercicio_Imagem/README.md) | A validar — criação visível; persistência e associação da imagem não confirmadas. |

## Inclusão de 15/11/2026 — CT-RF35

| Caso | Evidência | Resultado |
| --- | --- | --- |
| [CT-RF35](../Cenario_Teste/CT-RF35_Cadastro_Objetivo_Treino.md) | [Cadastro de objetivo de treino retorna HTTP 500](CT-RF35_Cadastro_Objetivo_Treino/README.md) | Reprovado nas evidências; BUG-019 em triagem. |

A pasta contém resumo, cronologia, origem, cinco capturas extraídas da reprodução do Jam e seus hashes SHA-256; o vídeo permanece no Jam. O Jam não capturou o corpo da requisição nem da resposta.

Não houve nova execução ou reteste do SIFIT. Os resultados se limitam aos quadros e registros consultados, conforme descrito em cada caso. Os documentos anteriores referenciam evidências de CT-RF01–CT-RF20 que não estão presentes nesta cópia local; esta inclusão não recria esses arquivos.

## Inclusão RF34 — 15/11/2026

| Caso | Evidência | Resultado |
| --- | --- | --- |
| CT-RF34 | [Erro no servidor por excesso de requisições](CT-RF34_Erro_Servidor_Excesso_Requisicoes/README.md) | Reprovado nas evidências — múltiplas requisições do dashboard retornam HTTP 500 e a interface apresenta um diálogo de erro. |

A evidência RF34 registra os fatos visíveis no Jam sem confirmar que o volume de requisições seja a causa dos erros. Caminhos completos, corpos, logs do servidor e causa raiz permanecem pendentes.

## Inclusão de 15/11/2026 — CT-RF38

| Caso | Evidência | Resultado |
| --- | --- | --- |
| [CT-RF38](../Cenario_Teste/CT-RF38_Cadastro_Categoria_Codigo_Automatico.md) | [Cadastro de categoria com código automático e consulta pelo código](CT-RF38_Cadastro_Categoria_Codigo_Automatico/README.md) | Aprovado conforme a gravação. |

A pasta contém resumo, cronologia, origem, oito capturas extraídas da reprodução do Jam (incluindo o corpo da requisição e da resposta de criação) e seus hashes SHA-256; o vídeo permanece no Jam.
