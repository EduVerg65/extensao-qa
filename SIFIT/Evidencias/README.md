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

## Inclusão de 15/11/2026 — CT-RF58 a CT-RF63

| Caso | Evidência | Resultado |
| --- | --- | --- |
| [CT-RF58](../Cenario_Teste/CT-RF58_Tema_Notificacoes_Prospeccao.md) | [Alternância de tema e painel de notificações em Prospecção](CT-RF58_Tema_Notificacoes_Prospeccao/README.md) | Aprovado conforme a gravação |
| [CT-RF59](../Cenario_Teste/CT-RF59_Busca_Leads_Prospeccao.md) | [Busca de leads por texto na tela Prospecção](CT-RF59_Busca_Leads_Prospeccao/README.md) | Aprovado conforme a gravação |
| [CT-RF60](../Cenario_Teste/CT-RF60_Filtro_Estagio_Leads.md) | [Filtro de leads por estágio e limpeza dos filtros](CT-RF60_Filtro_Estagio_Leads/README.md) | Aprovado conforme a gravação |
| [CT-RF61](../Cenario_Teste/CT-RF61_Cadastro_Lead_Prospeccao.md) | [Cadastro de lead com duas requisições de criação](CT-RF61_Cadastro_Lead_Prospeccao/README.md) | A validar — regra ou contexto pendente |
| [CT-RF62](../Cenario_Teste/CT-RF62_Telefone_Lead_Sem_Validacao.md) | [Telefone do lead aceita 30 dígitos sem validação](CT-RF62_Telefone_Lead_Sem_Validacao/README.md) | Reprovado nas evidências; BUG-024 em triagem |
| [CT-RF63](../Cenario_Teste/CT-RF63_Edicao_Lead_Prospeccao.md) | [Visualização e edição de lead na tela Prospecção](CT-RF63_Edicao_Lead_Prospeccao/README.md) | Aprovado conforme a gravação |

Uma gravação do Jam ([Prospecção](https://jam.dev/c/308607ff-8abc-40af-8c7c-429ce506ed64)) é a fonte dos seis casos; cada pasta contém resumo, cronologia, origem, capturas extraídas da reprodução do Jam e seus hashes SHA-256. Quadros que mostravam o e-mail digitado no formulário não foram incluídos; onde o modal de lead é mostrado, o recorte omite e-mail e telefone. O vídeo permanece no Jam.

## Inclusão de 15/11/2026 — CT-RF64 a CT-RF76

| Caso | Evidência | Resultado |
| --- | --- | --- |
| [CT-RF64](../Cenario_Teste/CT-RF64_Filtros_Contas_Pagar.md) | [Filtros da tela Contas a Pagar por nome, data e status](CT-RF64_Filtros_Contas_Pagar/README.md) | A validar — regra ou contexto pendente |
| [CT-RF65](../Cenario_Teste/CT-RF65_Cadastro_Conta_Colaborador_Sem_Colaborador.md) | [Conta a pagar a colaborador é cadastrada sem colaborador informado](CT-RF65_Cadastro_Conta_Colaborador_Sem_Colaborador/README.md) | Reprovado nas evidências; BUG-025 em triagem |
| [CT-RF66](../Cenario_Teste/CT-RF66_Busca_Colaborador_Conta_Pagar.md) | [Busca de colaborador no cadastro de conta a pagar](CT-RF66_Busca_Colaborador_Conta_Pagar/README.md) | A validar — regra ou contexto pendente |
| [CT-RF67](../Cenario_Teste/CT-RF67_Visualizacao_Conta_Pagar.md) | [Visualização dos dados de uma conta a pagar](CT-RF67_Visualizacao_Conta_Pagar/README.md) | Aprovado conforme a gravação |
| [CT-RF68](../Cenario_Teste/CT-RF68_Exclusao_Conta_Pagar.md) | [Exclusão de conta a pagar com confirmação](CT-RF68_Exclusao_Conta_Pagar/README.md) | Aprovado conforme a gravação |
| [CT-RF69](../Cenario_Teste/CT-RF69_Variaveis_Preview_Modelo_Contrato.md) | [Variáveis e pré-visualização do texto do modelo de contrato](CT-RF69_Variaveis_Preview_Modelo_Contrato/README.md) | Aprovado conforme a gravação |
| [CT-RF70](../Cenario_Teste/CT-RF70_Cadastro_Modelo_Contrato.md) | [Cadastro de modelo de contrato](CT-RF70_Cadastro_Modelo_Contrato/README.md) | Aprovado conforme a gravação |
| [CT-RF71](../Cenario_Teste/CT-RF71_Listagem_Modelos_Contrato_Vazia.md) | [Listagem de modelos de contrato aparece vazia com 15 modelos retornados](CT-RF71_Listagem_Modelos_Contrato_Vazia/README.md) | Reprovado nas evidências; BUG-026 em triagem |
| [CT-RF72](../Cenario_Teste/CT-RF72_Filtros_Planos.md) | [Filtros da tela Planos por código e nome](CT-RF72_Filtros_Planos/README.md) | Aprovado conforme a gravação |
| [CT-RF73](../Cenario_Teste/CT-RF73_Tema_Notificacoes_Planos.md) | [Alternância de tema e painel de notificações em Planos](CT-RF73_Tema_Notificacoes_Planos/README.md) | Aprovado conforme a gravação |
| [CT-RF74](../Cenario_Teste/CT-RF74_Cadastro_Plano.md) | [Cadastro de plano pelo modal Novo Plano](CT-RF74_Cadastro_Plano/README.md) | Aprovado conforme a gravação |
| [CT-RF75](../Cenario_Teste/CT-RF75_Contador_Ativos_Planos.md) | [Cartão Ativos de Planos aumenta ao cadastrar e editar planos inativos](CT-RF75_Contador_Ativos_Planos/README.md) | Reprovado nas evidências; BUG-027 em triagem |
| [CT-RF76](../Cenario_Teste/CT-RF76_Edicao_Plano.md) | [Edição de plano pelo modal Editar Plano](CT-RF76_Edicao_Plano/README.md) | Aprovado conforme a gravação |

Três gravações do Jam ([Contas a Pagar](https://jam.dev/c/5d0afaf4-5abd-4e85-923f-27448304a9ef), [Modelos de Contrato](https://jam.dev/c/44dbbd39-6915-45d6-8dd1-5f30c1432ca0) e [Planos](https://jam.dev/c/233c5d21-e108-4a55-b6f6-8738cb3fc6a6)) são a fonte dos treze casos; cada pasta contém resumo, cronologia, origem, capturas extraídas da reprodução do Jam e seus hashes SHA-256. Os vídeos permanecem no Jam.
