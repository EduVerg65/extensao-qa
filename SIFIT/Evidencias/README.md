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

## Inclusão de 15/11/2026 — CT-RF39 a CT-RF41

| Caso | Evidência | Resultado |
| --- | --- | --- |
| [CT-RF39](../Cenario_Teste/CT-RF39_Cadastro_Modalidade.md) | [Cadastro de modalidade](CT-RF39_Cadastro_Modalidade/README.md) | Aprovado conforme a gravação. |
| [CT-RF40](../Cenario_Teste/CT-RF40_Exclusao_Turmas_Modalidades.md) | [Exclusão de turmas e modalidades](CT-RF40_Exclusao_Turmas_Modalidades/README.md) | A validar — regra ou contexto pendente. |
| [CT-RF41](../Cenario_Teste/CT-RF41_Cadastro_Turma_Sem_Modalidade.md) | [Cadastro de turma sem modalidade](CT-RF41_Cadastro_Turma_Sem_Modalidade/README.md) | Reprovado nas evidências; BUG-020 em triagem. |

Uma única gravação do Jam ([SifitBox – Turmas](https://jam.dev/c/ee9a133b-d6b1-442d-b4b0-dd87595b7e70)) é a fonte dos três casos; cada pasta contém resumo, cronologia, origem, capturas extraídas da reprodução do Jam e seus hashes SHA-256. O vídeo permanece no Jam.

## Inclusão de 15/11/2026 — CT-RF42 a CT-RF56

| Caso | Evidência | Resultado |
| --- | --- | --- |
| [CT-RF42](../Cenario_Teste/CT-RF42_Solicitacao_Saque_PagarMe.md) | [Solicitação de saque no painel Pagar.me](CT-RF42_Solicitacao_Saque_PagarMe/README.md) | A validar — regra ou contexto pendente |
| [CT-RF43](../Cenario_Teste/CT-RF43_Criacao_Cobranca_PagarMe.md) | [Criação de cobrança no painel Pagar.me](CT-RF43_Criacao_Cobranca_PagarMe/README.md) | Aprovado conforme a gravação |
| [CT-RF44](../Cenario_Teste/CT-RF44_Configuracoes_Home_Salvamento.md) | [Alteração e salvamento das Configurações (Home)](CT-RF44_Configuracoes_Home_Salvamento/README.md) | A validar — regra ou contexto pendente |
| [CT-RF45](../Cenario_Teste/CT-RF45_Painel_PagarMe_Periodo.md) | [Painel Pagar.me mantém Recebimentos e gráfico ao trocar o período](CT-RF45_Painel_PagarMe_Periodo/README.md) | Reprovado nas evidências; BUG-021 em triagem |
| [CT-RF46](../Cenario_Teste/CT-RF46_Filtros_Despesas_Fixas.md) | [Filtros da tela Despesas Fixas por código e por nome](CT-RF46_Filtros_Despesas_Fixas/README.md) | Aprovado conforme a gravação |
| [CT-RF47](../Cenario_Teste/CT-RF47_Cadastro_Despesa_Fixa.md) | [Cadastro de despesa fixa com duas requisições de criação](CT-RF47_Cadastro_Despesa_Fixa/README.md) | A validar — regra ou contexto pendente |
| [CT-RF48](../Cenario_Teste/CT-RF48_Exclusao_Despesa_Fixa.md) | [Exclusão de despesa fixa com confirmação](CT-RF48_Exclusao_Despesa_Fixa/README.md) | Aprovado conforme a gravação |
| [CT-RF49](../Cenario_Teste/CT-RF49_Edicao_Despesa_Fixa.md) | [Edição de despesa fixa](CT-RF49_Edicao_Despesa_Fixa/README.md) | Aprovado conforme a gravação |
| [CT-RF50](../Cenario_Teste/CT-RF50_Relatorio_Matriculas.md) | [Relatório de Matrículas em PDF](CT-RF50_Relatorio_Matriculas/README.md) | Aprovado conforme a gravação |
| [CT-RF51](../Cenario_Teste/CT-RF51_Relatorio_Contas_Receber.md) | [Relatório de Contas a Receber sem Valor a Receber](CT-RF51_Relatorio_Contas_Receber/README.md) | Reprovado nas evidências; BUG-022 em triagem |
| [CT-RF52](../Cenario_Teste/CT-RF52_Relatorio_Contas_Pagar_Pagas.md) | [Relatório de Contas a Pagar (Pagas) sem registros](CT-RF52_Relatorio_Contas_Pagar_Pagas/README.md) | A validar — regra ou contexto pendente |
| [CT-RF53](../Cenario_Teste/CT-RF53_Relatorio_Avaliacoes_Vazio.md) | [Relatório de Avaliações gera arquivo vazio](CT-RF53_Relatorio_Avaliacoes_Vazio/README.md) | Reprovado nas evidências; BUG-023 em triagem |
| [CT-RF54](../Cenario_Teste/CT-RF54_Relatorio_Clientes_Vazio.md) | [Relatório de Clientes gera arquivo vazio](CT-RF54_Relatorio_Clientes_Vazio/README.md) | Reprovado nas evidências; BUG-023 em triagem |
| [CT-RF55](../Cenario_Teste/CT-RF55_Relatorio_Colaboradores_Vazio.md) | [Relatório de Colaboradores gera arquivo vazio](CT-RF55_Relatorio_Colaboradores_Vazio/README.md) | Reprovado nas evidências; BUG-023 em triagem |
| [CT-RF56](../Cenario_Teste/CT-RF56_Relatorio_Caixas_Vazio.md) | [Relatório de Caixas gera arquivo vazio](CT-RF56_Relatorio_Caixas_Vazio/README.md) | Reprovado nas evidências; BUG-023 em triagem |

Três gravações do Jam ([Pagar.me e Configurações](https://jam.dev/c/e6e551ef-9196-4c79-b6a2-89747b1e8b33), [Despesas Fixas](https://jam.dev/c/a4bac99d-e436-4792-831e-8c3a875272bb) e [Relatórios](https://jam.dev/c/3b4777a4-e1b0-4038-9b06-26c73669d7d1)) são a fonte dos quinze casos; cada pasta contém resumo, cronologia, origem, capturas extraídas da reprodução do Jam e seus hashes SHA-256, e as pastas de CT-RF50 a CT-RF56 incluem os PDFs baixados (os arquivos vazios têm 0 bytes). Os vídeos permanecem no Jam.


## Inclusão de 16/11/2026 — CT-RF74 a CT-RF84

Integração documental dos arquivos RESUMO.txt fornecidos em `C:\Users\Leonardo\Desktop\evidencias`, com data de gravação e análise informada de 16/11/2026. Os Jams não foram reabertos nesta integração; eventos de rede, horários e quadros abaixo são transcritos dos resumos, sem verificação independente. Não houve nova execução do SIFIT, reteste, consulta ao banco, logs ou código.

| Caso | Evidência local | Resultado | Defeito | Jam |
| --- | --- | --- | --- | --- |
| [CT-RF74](../Cenario_Teste/CT-RF74_Temas_Prospeccao.md) | [Evidências](CT-RF74_Temas_Prospeccao/README.md) | Aprovado conforme o resumo da gravação | — | [Jam](https://jam.dev/c/5dc9fc15-8e13-4f90-b21f-a49aedc6731e) |
| [CT-RF75](../Cenario_Teste/CT-RF75_Detalhes_Lead_Cancelamento.md) | [Evidências](CT-RF75_Detalhes_Lead_Cancelamento/README.md) | Aprovado conforme o resumo da gravação | — | [Jam](https://jam.dev/c/7ef0ee0b-497e-48b8-a57d-cd914558d303) |
| [CT-RF76](../Cenario_Teste/CT-RF76_Exclusao_Leads_Confirmacao.md) | [Evidências](CT-RF76_Exclusao_Leads_Confirmacao/README.md) | Aprovado conforme o resumo da gravação | — | [Jam](https://jam.dev/c/2ac5e5ed-b10f-4cc9-9f97-7ba65ca560f8) |
| [CT-RF77](../Cenario_Teste/CT-RF77_Cadastro_Lead_Novo_Contato.md) | [Evidências](CT-RF77_Cadastro_Lead_Novo_Contato/README.md) | Aprovado conforme o resumo da gravação | — | [Jam](https://jam.dev/c/29447c6a-90f5-48b2-ac5d-d43cad44a782) |
| [CT-RF78](../Cenario_Teste/CT-RF78_Cadastro_Lead_Interessado.md) | [Evidências](CT-RF78_Cadastro_Lead_Interessado/README.md) | Aprovado conforme o resumo da gravação | — | [Jam](https://jam.dev/c/f8735cbf-4043-4467-b43f-3cad7eff0da8) |
| [CT-RF79](../Cenario_Teste/CT-RF79_Cadastro_Lead_Aula_Experimental.md) | [Evidências](CT-RF79_Cadastro_Lead_Aula_Experimental/README.md) | Aprovado conforme o resumo da gravação | — | [Jam](https://jam.dev/c/bef3d877-056b-4274-87c3-da37869c54fd) |
| [CT-RF80](../Cenario_Teste/CT-RF80_Cadastro_Lead_Proposta.md) | [Evidências](CT-RF80_Cadastro_Lead_Proposta/README.md) | Aprovado conforme o resumo da gravação | — | [Jam](https://jam.dev/c/84f94285-ae5f-4f95-b640-a9b107565aa6) |
| [CT-RF81](../Cenario_Teste/CT-RF81_Cadastro_Bandeira_Parcela_Listagem.md) | [Evidências](CT-RF81_Cadastro_Bandeira_Parcela_Listagem/README.md) | Reprovado nas evidências resumidas | [BUG-035](../Relatorio-de-Bugs.md#bug-035) | [Jam](https://jam.dev/c/2f0280fb-6b7f-4cf0-a45c-02f8c16b6c5e) |
| [CT-RF82](../Cenario_Teste/CT-RF82_Tema_Escuro_Bandeiras.md) | [Evidências](CT-RF82_Tema_Escuro_Bandeiras/README.md) | Reprovado nas evidências resumidas | [BUG-036](../Relatorio-de-Bugs.md#bug-036) | [Jam](https://jam.dev/c/ae4dc198-8a42-4451-898a-fb376596c744) |
| [CT-RF83](../Cenario_Teste/CT-RF83_Cadastro_Lead_Apenas_Nome.md) | [Evidências](CT-RF83_Cadastro_Lead_Apenas_Nome/README.md) | Reprovado conforme o relato; regra de obrigatoriedade a confirmar | [BUG-037](../Relatorio-de-Bugs.md#bug-037) | [Jam](https://jam.dev/c/ef3df03c-16ce-4cb6-b0c7-d04514cab4f6) |
| [CT-RF84](../Cenario_Teste/CT-RF84_Cadastro_Lead_Fechado.md) | [Evidências](CT-RF84_Cadastro_Lead_Fechado/README.md) | Aprovado conforme o resumo da gravação | — | [Jam](https://jam.dev/c/775b9003-fdf7-4ad5-8882-15ba606b6674) |

As onze pastas contêm uma cópia integral de RESUMO.txt e um README.md no padrão do projeto, com cronologia e hash SHA-256 do texto original. Não foram fornecidos vídeos ou capturas locais neste lote. CT-RF74–CT-RF84 acrescentam oito aprovações e três reprovações conforme os resumos fornecidos, com BUG-035–BUG-037 em triagem. CT-RF83 mantém a classificação do relato, condicionada à confirmação da regra de obrigatoriedade. Os dez casos anteriores a validar permanecem inalterados.
