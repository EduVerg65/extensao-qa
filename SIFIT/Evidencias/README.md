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
## Inclusão de 15/11/2026 — CT-RF85 a CT-RF90

| Caso | Evidência | Resultado |
| --- | --- | --- |
| [CT-RF85](../Cenario_Teste/CT-RF85_Tema_Notificacoes_Prospeccao.md) | [Alternância de tema e painel de notificações em Prospecção](CT-RF85_Tema_Notificacoes_Prospeccao/README.md) | Aprovado conforme a gravação |
| [CT-RF86](../Cenario_Teste/CT-RF86_Busca_Leads_Prospeccao.md) | [Busca de leads por texto na tela Prospecção](CT-RF86_Busca_Leads_Prospeccao/README.md) | Aprovado conforme a gravação |
| [CT-RF87](../Cenario_Teste/CT-RF87_Filtro_Estagio_Leads.md) | [Filtro de leads por estágio e limpeza dos filtros](CT-RF87_Filtro_Estagio_Leads/README.md) | Aprovado conforme a gravação |
| [CT-RF88](../Cenario_Teste/CT-RF88_Cadastro_Lead_Prospeccao.md) | [Cadastro de lead com duas requisições de criação](CT-RF88_Cadastro_Lead_Prospeccao/README.md) | A validar — regra ou contexto pendente |
| [CT-RF89](../Cenario_Teste/CT-RF89_Telefone_Lead_Sem_Validacao.md) | [Telefone do lead aceita 30 dígitos sem validação](CT-RF89_Telefone_Lead_Sem_Validacao/README.md) | Reprovado nas evidências; BUG-038 em triagem |
| [CT-RF90](../Cenario_Teste/CT-RF90_Edicao_Lead_Prospeccao.md) | [Visualização e edição de lead na tela Prospecção](CT-RF90_Edicao_Lead_Prospeccao/README.md) | Aprovado conforme a gravação |

Uma gravação do Jam ([Prospecção](https://jam.dev/c/308607ff-8abc-40af-8c7c-429ce506ed64)) é a fonte dos seis casos; cada pasta contém resumo, cronologia, origem, capturas extraídas da reprodução do Jam e seus hashes SHA-256. Quadros que mostravam o e-mail digitado no formulário não foram incluídos; onde o modal de lead é mostrado, o recorte omite e-mail e telefone. O vídeo permanece no Jam.

## Inclusão de 15/11/2026 — CT-RF91 a CT-RF103

| Caso | Evidência | Resultado |
| --- | --- | --- |
| [CT-RF91](../Cenario_Teste/CT-RF91_Filtros_Contas_Pagar.md) | [Filtros da tela Contas a Pagar por nome, data e status](CT-RF91_Filtros_Contas_Pagar/README.md) | A validar — regra ou contexto pendente |
| [CT-RF92](../Cenario_Teste/CT-RF92_Cadastro_Conta_Colaborador_Sem_Colaborador.md) | [Conta a pagar a colaborador é cadastrada sem colaborador informado](CT-RF92_Cadastro_Conta_Colaborador_Sem_Colaborador/README.md) | Reprovado nas evidências; BUG-039 em triagem |
| [CT-RF93](../Cenario_Teste/CT-RF93_Busca_Colaborador_Conta_Pagar.md) | [Busca de colaborador no cadastro de conta a pagar](CT-RF93_Busca_Colaborador_Conta_Pagar/README.md) | A validar — regra ou contexto pendente |
| [CT-RF94](../Cenario_Teste/CT-RF94_Visualizacao_Conta_Pagar.md) | [Visualização dos dados de uma conta a pagar](CT-RF94_Visualizacao_Conta_Pagar/README.md) | Aprovado conforme a gravação |
| [CT-RF95](../Cenario_Teste/CT-RF95_Exclusao_Conta_Pagar.md) | [Exclusão de conta a pagar com confirmação](CT-RF95_Exclusao_Conta_Pagar/README.md) | Aprovado conforme a gravação |
| [CT-RF96](../Cenario_Teste/CT-RF96_Variaveis_Preview_Modelo_Contrato.md) | [Variáveis e pré-visualização do texto do modelo de contrato](CT-RF96_Variaveis_Preview_Modelo_Contrato/README.md) | Aprovado conforme a gravação |
| [CT-RF97](../Cenario_Teste/CT-RF97_Cadastro_Modelo_Contrato.md) | [Cadastro de modelo de contrato](CT-RF97_Cadastro_Modelo_Contrato/README.md) | Aprovado conforme a gravação |
| [CT-RF98](../Cenario_Teste/CT-RF98_Listagem_Modelos_Contrato_Vazia.md) | [Listagem de modelos de contrato aparece vazia com 15 modelos retornados](CT-RF98_Listagem_Modelos_Contrato_Vazia/README.md) | Reprovado nas evidências; BUG-040 em triagem |
| [CT-RF99](../Cenario_Teste/CT-RF99_Filtros_Planos.md) | [Filtros da tela Planos por código e nome](CT-RF99_Filtros_Planos/README.md) | Aprovado conforme a gravação |
| [CT-RF100](../Cenario_Teste/CT-RF100_Tema_Notificacoes_Planos.md) | [Alternância de tema e painel de notificações em Planos](CT-RF100_Tema_Notificacoes_Planos/README.md) | Aprovado conforme a gravação |
| [CT-RF101](../Cenario_Teste/CT-RF101_Cadastro_Plano.md) | [Cadastro de plano pelo modal Novo Plano](CT-RF101_Cadastro_Plano/README.md) | Aprovado conforme a gravação |
| [CT-RF102](../Cenario_Teste/CT-RF102_Contador_Ativos_Planos.md) | [Cartão Ativos de Planos aumenta ao cadastrar e editar planos inativos](CT-RF102_Contador_Ativos_Planos/README.md) | Reprovado nas evidências; BUG-041 em triagem |
| [CT-RF103](../Cenario_Teste/CT-RF103_Edicao_Plano.md) | [Edição de plano pelo modal Editar Plano](CT-RF103_Edicao_Plano/README.md) | Aprovado conforme a gravação |

Três gravações do Jam ([Contas a Pagar](https://jam.dev/c/5d0afaf4-5abd-4e85-923f-27448304a9ef), [Modelos de Contrato](https://jam.dev/c/44dbbd39-6915-45d6-8dd1-5f30c1432ca0) e [Planos](https://jam.dev/c/233c5d21-e108-4a55-b6f6-8738cb3fc6a6)) são a fonte dos treze casos; cada pasta contém resumo, cronologia, origem, capturas extraídas da reprodução do Jam e seus hashes SHA-256. Os vídeos permanecem no Jam.

## Inclusão de 16/11/2026 — CT-RF104 a CT-RF108

| Caso | Evidência | Resultado |
| --- | --- | --- |
| [CT-RF104](../Cenario_Teste/CT-RF104_Filtros_Tipos_Pagamento.md) | [Filtros de busca da tela Tipos de Pagamento](CT-RF104_Filtros_Tipos_Pagamento/README.md) | A validar — regra ou contexto pendente |
| [CT-RF105](../Cenario_Teste/CT-RF105_Cadastro_Tipo_Pagamento_Status.md) | [Cadastro de tipo de pagamento com status Ativo não é refletido](CT-RF105_Cadastro_Tipo_Pagamento_Status/README.md) | Reprovado nas evidências; BUG-042 em triagem |
| [CT-RF106](../Cenario_Teste/CT-RF106_Edicao_Tipo_Pagamento.md) | [Edição de tipo de pagamento pela lupa da listagem](CT-RF106_Edicao_Tipo_Pagamento/README.md) | Aprovado conforme a gravação |
| [CT-RF107](../Cenario_Teste/CT-RF107_Exclusao_Tipo_Pagamento_Em_Uso.md) | [Exclusão de tipo de pagamento em uso retorna HTTP 404 com erro SQL](CT-RF107_Exclusao_Tipo_Pagamento_Em_Uso/README.md) | Reprovado nas evidências; BUG-043 em triagem |
| [CT-RF108](../Cenario_Teste/CT-RF108_Tema_Notificacoes_Tipos_Pagamento.md) | [Tema Claro/Escuro e notificações na tela Tipos de Pagamento](CT-RF108_Tema_Notificacoes_Tipos_Pagamento/README.md) | Aprovado conforme a gravação |

Uma gravação do Jam ([Tipos de Pagamento](https://jam.dev/c/e8734e3d-3f8e-458b-8c7d-e85eea882e50)) é a fonte dos cinco casos; cada pasta contém resumo, cronologia, origem, capturas extraídas da reprodução do Jam e seus hashes SHA-256. O vídeo permanece no Jam.

## Inclusão de 17/11/2026 — Modelos de Ficha

| Caso | Evidência | Resultado |
| --- | --- | --- |
| [CT-RF109](../Cenario_Teste/CT-RF109_Modelo_Ficha_Sem_Nome.md) | [Bloquear cadastro de modelo de ficha sem nome](CT-RF109_Modelo_Ficha_Sem_Nome/README.md) | Aprovado conforme a gravação |
| [CT-RF110](../Cenario_Teste/CT-RF110_Cancelar_Cadastro_Modelo_Ficha.md) | [Cancelar cadastro de modelo de ficha preenchido](CT-RF110_Cancelar_Cadastro_Modelo_Ficha/README.md) | Aprovado conforme a gravação |
| [CT-RF111](../Cenario_Teste/CT-RF111_Busca_Modelo_Ficha_Codigo_Inexistente.md) | [Buscar modelo de ficha por código inexistente](CT-RF111_Busca_Modelo_Ficha_Codigo_Inexistente/README.md) | A validar — regra ou contexto pendente |
| [CT-RF112](../Cenario_Teste/CT-RF112_Busca_Modelo_Ficha_Titulo_Inexistente.md) | [Buscar modelo de ficha por título inexistente](CT-RF112_Busca_Modelo_Ficha_Titulo_Inexistente/README.md) | A validar — regra ou contexto pendente |
| [CT-RF113](../Cenario_Teste/CT-RF113_Busca_Modelo_Ficha_Filtros_Combinados.md) | [Buscar modelos de ficha com filtros combinados](CT-RF113_Busca_Modelo_Ficha_Filtros_Combinados/README.md) | A validar — regra ou contexto pendente |
| [CT-RF114](../Cenario_Teste/CT-RF114_Limpeza_Filtros_Modelos_Ficha.md) | [Limpar os filtros de Modelos de Ficha](CT-RF114_Limpeza_Filtros_Modelos_Ficha/README.md) | Aprovado conforme a gravação |
| [CT-RF115](../Cenario_Teste/CT-RF115_Nova_Busca_Modelos_Ficha_Sem_Filtros.md) | [Pesquisar novamente modelos de ficha sem filtros](CT-RF115_Nova_Busca_Modelos_Ficha_Sem_Filtros/README.md) | A validar — regra ou contexto pendente |

A revisão de Modelos de Ficha inclui CT-RF109–CT-RF115 com base em 6 gravações do Jam de 16/11/2026. A revisão documental foi feita em 17/11/2026. Cada pasta reúne a origem, a cronologia, os quadros do fluxo e os hashes SHA-256 das imagens. Os vídeos permanecem no Jam.

## Inclusão de 17/11/2026 — Configurações e Modelos de Ficha (CT-RF116–CT-RF121)

| Caso | Evidência | Resultado |
| --- | --- | --- |
| [CT-RF116](../Cenario_Teste/CT-RF116_Configuracoes_Dias_Ausencia_Vazio.md) | [Validar o salvamento com o campo de dias de ausência vazio](CT-RF116_Configuracoes_Dias_Ausencia_Vazio/README.md) | A validar — regra ou contexto pendente |
| [CT-RF117](../Cenario_Teste/CT-RF117_Configuracoes_Cancelar_Alteracao.md) | [Cancelar uma alteração nas Configurações sem salvar](CT-RF117_Configuracoes_Cancelar_Alteracao/README.md) | Aprovado conforme a gravação |
| [CT-RF118](../Cenario_Teste/CT-RF118_Configuracoes_Trabalha_Com_Turmas.md) | [Alterar e persistir a opção Trabalha com turmas?](CT-RF118_Configuracoes_Trabalha_Com_Turmas/README.md) | Aprovado conforme a gravação |
| [CT-RF119](../Cenario_Teste/CT-RF119_Configuracoes_Academia_Marcada_Box.md) | [Conferir a configuração Academia marcada como Box?](CT-RF119_Configuracoes_Academia_Marcada_Box/README.md) | Aprovado conforme a gravação |
| [CT-RF120](../Cenario_Teste/CT-RF120_Configuracoes_Acesso_Desktop.md) | [Conferir a configuração de acesso ao sistema desktop](CT-RF120_Configuracoes_Acesso_Desktop/README.md) | Aprovado conforme a gravação |
| [CT-RF121](../Cenario_Teste/CT-RF121_Cadastro_Modelo_Ficha_Erro_500.md) | [Cadastrar um modelo de ficha com nome e personal](CT-RF121_Cadastro_Modelo_Ficha_Erro_500/README.md) | Reprovado nas evidências |

CT-RF116–CT-RF121 amplia a cobertura de Configurações e Modelos de Ficha com gravações de 16/11/2026 entre 22:03:53 e 22:18:52 BRT. As pastas seguem o padrão de origem, cronologia e quadros com SHA-256.

## Inclusão de 17/11/2026 — Inteligência e Configurações (CT-RF122–CT-RF127)

| Caso | Evidência | Resultado |
| --- | --- | --- |
| [CT-RF122](../Cenario_Teste/CT-RF122_Resultados_IA_Filtro_90_Dias.md) | [Filtrar Resultados da Inteligência pelos últimos 90 dias](CT-RF122_Resultados_IA_Filtro_90_Dias/README.md) | Aprovado conforme a gravação |
| [CT-RF123](../Cenario_Teste/CT-RF123_Central_Resultados_IA_Execucao_Evasao.md) | [Conferir a execução de Risco de Evasão na Central e em Resultados IA](CT-RF123_Central_Resultados_IA_Execucao_Evasao/README.md) | Aprovado conforme a gravação |
| [CT-RF124](../Cenario_Teste/CT-RF124_Configuracoes_Abas_Biometria_Senha.md) | [Navegar pelas abas de Configurações com a senha da biometria protegida](CT-RF124_Configuracoes_Abas_Biometria_Senha/README.md) | Reprovado nas evidências |
| [CT-RF125](../Cenario_Teste/CT-RF125_Configuracoes_Salvar_Dias_Ausencia_Valido.md) | [Salvar um valor válido de dias de ausência](CT-RF125_Configuracoes_Salvar_Dias_Ausencia_Valido/README.md) | Aprovado conforme a gravação |
| [CT-RF126](../Cenario_Teste/CT-RF126_Configuracoes_Dias_Ausencia_Negativo.md) | [Bloquear número negativo no campo de dias de ausência](CT-RF126_Configuracoes_Dias_Ausencia_Negativo/README.md) | Reprovado nas evidências |
| [CT-RF127](../Cenario_Teste/CT-RF127_Configuracoes_Dias_Ausencia_Texto.md) | [Validar letras no campo de dias de ausência](CT-RF127_Configuracoes_Dias_Ausencia_Texto/README.md) | A validar — regra ou contexto pendente |

CT-RF122–CT-RF127 cobre Inteligência e Configurações com gravações de 16/11/2026 entre 21:50:51 e 22:02:16 BRT. As pastas reúnem origem, cronologia e recortes identificados com SHA-256.

## Inclusão de 17/11/2026 — Inteligência e Automação (CT-RF128–CT-RF133)

| Caso | Evidência | Resultado |
| --- | --- | --- |
| [CT-RF128](../Cenario_Teste/CT-RF128_Central_Configuracao_Risco_Evasao_Cancelar.md) | [Abrir e fechar a configuração de Risco de Evasão](CT-RF128_Central_Configuracao_Risco_Evasao_Cancelar/README.md) | Aprovado conforme a gravação |
| [CT-RF129](../Cenario_Teste/CT-RF129_Central_Aniversariantes_Previa_Risco.md) | [Abrir Aniversariantes e conferir a prévia da automação](CT-RF129_Central_Aniversariantes_Previa_Risco/README.md) | Reprovado nas evidências |
| [CT-RF130](../Cenario_Teste/CT-RF130_Central_Recursos_Em_Desenvolvimento.md) | [Verificar recursos marcados como Em desenvolvimento](CT-RF130_Central_Recursos_Em_Desenvolvimento/README.md) | Aprovado conforme a gravação |
| [CT-RF131](../Cenario_Teste/CT-RF131_Resultados_IA_Filtro_Hoje.md) | [Filtrar Resultados da Inteligência por Hoje](CT-RF131_Resultados_IA_Filtro_Hoje/README.md) | Aprovado conforme a gravação |
| [CT-RF132](../Cenario_Teste/CT-RF132_Resultados_IA_Filtro_7_Dias.md) | [Filtrar Resultados da Inteligência pelos últimos 7 dias](CT-RF132_Resultados_IA_Filtro_7_Dias/README.md) | Aprovado conforme a gravação |
| [CT-RF133](../Cenario_Teste/CT-RF133_Resultados_IA_Filtro_30_Dias.md) | [Filtrar Resultados da Inteligência pelos últimos 30 dias](CT-RF133_Resultados_IA_Filtro_30_Dias/README.md) | Aprovado conforme a gravação |

CT-RF128–CT-RF133 cobre Inteligência e Automação com gravações de 16/11/2026 entre 21:40:31 e 21:49:48 BRT. As pastas reúnem origem, cronologia e recortes identificados com SHA-256.

## Inclusão de 17/11/2026 — Inteligência e Automação / Central de Automações (CT-RF134–CT-RF138)

| Caso | Evidência | Resultado |
| --- | --- | --- |
| [CT-RF134](../Cenario_Teste/CT-RF134_Central_Automacoes_Atualizar.md) | [Atualizar a Central de Automações](CT-RF134_Central_Automacoes_Atualizar/README.md) | Aprovado conforme a gravação |
| [CT-RF135](../Cenario_Teste/CT-RF135_Central_Desativar_Risco_Evasao_Contador.md) | [Desativar Risco de Evasão e conferir a persistência e o contador](CT-RF135_Central_Desativar_Risco_Evasao_Contador/README.md) | Reprovado nas evidências |
| [CT-RF136](../Cenario_Teste/CT-RF136_Central_Ativar_Aniversariantes_Contador.md) | [Ativar Aniversariantes e conferir a persistência e o contador](CT-RF136_Central_Ativar_Aniversariantes_Contador/README.md) | Reprovado nas evidências |
| [CT-RF137](../Cenario_Teste/CT-RF137_Central_Risco_Evasao_Executar_Agora.md) | [Executar Risco de Evasão manualmente pela Central](CT-RF137_Central_Risco_Evasao_Executar_Agora/README.md) | Aprovado conforme a gravação |
| [CT-RF138](../Cenario_Teste/CT-RF138_Central_Abrir_Resultados_Risco_Evasao.md) | [Abrir os resultados de Risco de Evasão pela Central](CT-RF138_Central_Abrir_Resultados_Risco_Evasao/README.md) | Aprovado conforme a gravação |

CT-RF134–CT-RF138 cobrem a Central de Automações com gravações de 16/11/2026 entre 21:25:26 e 21:38:29 BRT. As pastas reúnem origem, cronologia e recortes identificados com SHA-256.

## Inclusão de 17/11/2026 — Configurações / Integrações / WhatsApp (CT-RF139–CT-RF144)

| Caso | Evidência | Resultado |
| --- | --- | --- |
| [CT-RF139](../Cenario_Teste/CT-RF139_Integracoes_WhatsApp_Mascarar_API_Key.md) | [Mascarar a API Key no formulário de WhatsApp](CT-RF139_Integracoes_WhatsApp_Mascarar_API_Key/README.md) | Aprovado conforme a gravação |
| [CT-RF140](../Cenario_Teste/CT-RF140_Integracoes_WhatsApp_Validar_URL_API.md) | [Validar uma URL da API sem formato de endereço](CT-RF140_Integracoes_WhatsApp_Validar_URL_API/README.md) | A validar — regra ou contexto pendente |
| [CT-RF141](../Cenario_Teste/CT-RF141_Integracoes_WhatsApp_Instancia_Obrigatoria.md) | [Bloquear o salvamento com Nome da Instância vazio](CT-RF141_Integracoes_WhatsApp_Instancia_Obrigatoria/README.md) | Aprovado conforme a gravação |
| [CT-RF142](../Cenario_Teste/CT-RF142_Integracoes_WhatsApp_Persistir_Ativo.md) | [Persistir a opção Ativo da integração de WhatsApp](CT-RF142_Integracoes_WhatsApp_Persistir_Ativo/README.md) | Aprovado conforme a gravação |
| [CT-RF143](../Cenario_Teste/CT-RF143_Integracoes_WhatsApp_Conectar_Evolution.md) | [Tratar falha ao conectar WhatsApp via Evolution API](CT-RF143_Integracoes_WhatsApp_Conectar_Evolution/README.md) | Reprovado nas evidências |
| [CT-RF144](../Cenario_Teste/CT-RF144_Integracoes_WhatsApp_Atualizar_Status.md) | [Consultar novamente o status da integração de WhatsApp](CT-RF144_Integracoes_WhatsApp_Atualizar_Status/README.md) | Aprovado conforme a gravação |

CT-RF139–CT-RF144 cobrem a integração do WhatsApp com gravações de 16/11/2026 entre 23:37:22 e 23:45:52 BRT. As pastas reúnem origem, cronologia e recortes identificados com SHA-256.

## Inclusão de 17/11/2026 — Configurações (CT-RF145–CT-RF148)

| Caso | Evidência | Resultado |
| --- | --- | --- |
| [CT-RF145](../Cenario_Teste/CT-RF145_Configuracoes_Aniversario_Salvar_WhatsApp_SMS.md) | [Salvar mensagens de aniversário para WhatsApp e SMS](CT-RF145_Configuracoes_Aniversario_Salvar_WhatsApp_SMS/README.md) | Aprovado conforme a gravação |
| [CT-RF146](../Cenario_Teste/CT-RF146_Configuracoes_Pagamento_Online_Desativar.md) | [Persistir a desativação do Pagamento Online](CT-RF146_Configuracoes_Pagamento_Online_Desativar/README.md) | Aprovado conforme a gravação |
| [CT-RF147](../Cenario_Teste/CT-RF147_Configuracoes_Design_Salvar_Cor_Principal.md) | [Salvar uma Cor Principal hexadecimal válida](CT-RF147_Configuracoes_Design_Salvar_Cor_Principal/README.md) | Aprovado conforme a gravação |
| [CT-RF148](../Cenario_Teste/CT-RF148_Configuracoes_Design_Validar_Cor_Secundaria.md) | [Rejeitar código hexadecimal inválido na Cor Secundária](CT-RF148_Configuracoes_Design_Validar_Cor_Secundaria/README.md) | Reprovado nas evidências |

CT-RF145–CT-RF148 cobrem funcionalidades de Configurações com gravações de 16/11/2026 entre 23:21:59 e 23:26:21 BRT. As pastas reúnem origem, cronologia e recortes identificados com SHA-256.
