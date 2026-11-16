# 🧪 Índice dos cenários de teste — SIFIT

**Atualização:** 15/11/2026. 73 casos (CT-RF01–CT-RF35, CT-RF38–CT-RF56 e CT-RF58–CT-RF76): 29 aprovados, 31 reprovados e 13 a validar; 27 defeitos registrados (10 abertos e 17 em triagem).

| Caso | Funcionalidade | Resultado | Defeito | Jam |
| --- | --- | --- | --- | --- |
| [CT-RF01](CT-RF01_Esqueci-senha.md) | Início da recuperação de senha | Reprovado conforme as evidências | [BUG-001](../../SIFIT/Relatorio-de-Bugs.md#bug-001--link-esqueci-minha-senha-não-executa-nenhuma-ação) | [Jam](https://jam.dev/c/0273b203-b999-493d-9919-2d143bc13301) |
| [CT-RF02_ERRO](CT-RF02_ERRO.md) | Dados, campos e layout do perfil | Reprovado conforme as evidências | [BUG-002](../../SIFIT/Relatorio-de-Bugs.md#bug-002--perfil-com-dados-fictícios-campos-ausentes-e-layout-desconfigurado) | [Jam](https://jam.dev/c/c61241d5-bff5-4a0a-9684-991318f9b51c) |
| [CT-RF03](CT-RF03_FILTRO_TelaClientes.md) | Filtros combinados de Clientes | Reprovado conforme o relato | [BUG-003](../../SIFIT/Relatorio-de-Bugs.md#bug-003--filtros-combinados-da-página-clientes-não-restringem-a-listagem) | [Jam](https://jam.dev/c/657627ec-e7e2-455d-a505-9b2a26f44bf1) |
| [CT-RF04_loginComSucesso](CT-RF04_loginComSucesso.md) | Login com credenciais válidas | Aprovado conforme a gravação | — | [Jam](https://jam.dev/c/5e4a28be-4e80-43d3-9587-1b113723cc38) |
| [CT-RF05](CT-RF05_Login_SenhaIncorreta.md) | Login com senha incorreta | Aprovado conforme a gravação | — | [Jam](https://jam.dev/c/75f16436-7201-4de0-b191-1c4d0d63bfe8) |
| [CT-RF06](CT-RF06_Login_UsuarioInexistente.md) | Login com usuário inexistente | Aprovado conforme a gravação | — | [Jam](https://jam.dev/c/b184e875-2cb1-4a01-b4dd-bc85b3741ff6) |
| [CT-RF07](CT-RF07_Exportacao_Financeiro.md) | Exportação financeira sem retorno visível | Reprovado nas evidências | [BUG-004](../../SIFIT/Relatorio-de-Bugs.md#bug-004) | [Jam](https://jam.dev/c/1084cb18-cb3d-4b85-9c2f-ee431b59a06b) |
| [CT-RF08](CT-RF08_Calculo_Cobranca.md) | Total atualizado da cobrança e valor da mensagem | A validar — regra ou contexto pendente | — | [Jam](https://jam.dev/c/79b712ae-d9e0-4600-862f-fd3a278285ff) |
| [CT-RF09](CT-RF09_Contagem_Mensalidades.md) | Contagem de mensalidades diverge da lista | Reprovado nas evidências | [BUG-005](../../SIFIT/Relatorio-de-Bugs.md#bug-005) | [Jam](https://jam.dev/c/1874d0b3-5c7c-4f28-85be-91750e20cbe1) |
| [CT-RF10](CT-RF10_Filtro_Mensalidades.md) | Filtro Até 7 dias conta uma mensalidade e mostra lista vazia | Reprovado nas evidências | [BUG-005](../../SIFIT/Relatorio-de-Bugs.md#bug-005) | [Jam](https://jam.dev/c/3f78cf16-2c3b-48bc-8622-23b829debbec) |
| [CT-RF11](CT-RF11_Metricas_Financeiro.md) | Escopo das métricas financeiras durante a filtragem | A validar — regra ou contexto pendente | — | [Jam](https://jam.dev/c/4491c9e7-7e00-4063-91ce-8683e316df06) |
| [CT-RF12](CT-RF12_Periodo_Dashboard.md) | Período invertido e atualização de indicadores pouco clara | Reprovado nas evidências | [BUG-006](../../SIFIT/Relatorio-de-Bugs.md#bug-006) | [Jam](https://jam.dev/c/93165ba3-3bfe-4dd5-9379-ab8db2d686ba) |
| [CT-RF13](CT-RF13_Codigos_Personais.md) | Códigos não sequenciais na lista de personais | A validar — regra ou contexto pendente | — | [Jam](https://jam.dev/c/69330ca9-ef19-4ece-918f-31a460628016) |
| [CT-RF14](CT-RF14_Contraste_TemaEscuro.md) | Baixa legibilidade no tema escuro de Box – Turmas | Reprovado nas evidências | [BUG-007](../../SIFIT/Relatorio-de-Bugs.md#bug-007) | [Jam](https://jam.dev/c/6889db07-bed1-472b-8ec2-00402919cd65) |
| [CT-RF15](CT-RF15_Edicao_Modalidade.md) | Edição de modalidade sem ação de salvar visível | Reprovado nas evidências | [BUG-008](../../SIFIT/Relatorio-de-Bugs.md#bug-008) | [Jam](https://jam.dev/c/951efaf8-bf32-44b0-b640-a2935a6b554a) |
| [CT-RF16](CT-RF16_Exclusao_Modalidade.md) | Ação de lixeira inativa modalidades e mantém registros na lista | A validar — regra ou contexto pendente | — | [Jam](https://jam.dev/c/0f55f76a-cd31-4cee-93da-23c13b1ba637) |
| [CT-RF17](CT-RF17_Filtros_Categorias.md) | Filtros de categorias por código e nome | Aprovado conforme a gravação | — | [Jam](https://jam.dev/c/5e75e423-9c7e-43d7-aade-9b1a32c5e559) |
| [CT-RF18](CT-RF18_Atualizacao_Categoria.md) | Atualização de categoria | Aprovado conforme a gravação | — | [Jam](https://jam.dev/c/67664a98-2a4a-4134-91a9-7ca9b8aa9dbd) |
| [CT-RF19](CT-RF19_Exclusao_Categoria.md) | Exclusão de categoria retorna erro HTTP 500 | Reprovado nas evidências | [BUG-009](../../SIFIT/Relatorio-de-Bugs.md#bug-009) | [Jam](https://jam.dev/c/c5c78b3b-2865-4226-836f-bcb0a8fc612f) |
| [CT-RF20](CT-RF20_Criacao_Categoria.md) | Criação de categoria | Aprovado conforme a gravação | — | [Jam](https://jam.dev/c/b48ab94e-517d-48d6-8e46-70b18c033b8b) |
| [CT-RF21](CT-RF21_Cadastro_Avaliacao.md) | Cadastro de avaliação retorna HTTP 500 | Reprovado nas evidências | [BUG-010](../Relatorio-de-Bugs.md#bug-010) | [Jam](https://jam.dev/c/2e5eca1f-7cd2-4ee3-854b-02ef4635955a) |

Os resultados são documentais; nenhuma nova execução ou reteste foi realizada nesta inclusão. No conjunto CT-RF01–CT-RF21, onze casos reprovados estão relacionados a dez defeitos, pois CT-RF09 e CT-RF10 compartilham BUG-005.

## Inclusão de 15/11/2026

A tabela anterior reúne CT-RF01–CT-RF21. Os quatro casos abaixo completam CT-RF01–CT-RF25 e estão integrados aos requisitos, plano e relatórios. As evidências documentais de CT-RF23–CT-RF25 estão em [Evidências](../Evidencias/README.md).

| Caso | Funcionalidade | Resultado | Defeito | Jam |
| --- | --- | --- | --- | --- |
| [CT-RF22](CT-RF22_Digitacao_Codigo_Exercicio.md) | Digitação do código no formulário Exercício | Reprovado conforme o relato; reprodução independente pendente | [BUG-011](../Relatorio-de-Bugs.md#bug-011), em triagem | [Jam](https://jam.dev/c/2696db03-0a18-4c39-a75d-4987a43c04f0) |
| [CT-RF23](CT-RF23_Exclusao_Exercicio.md) | Exclusão de exercício | Aprovado no trecho consultado | Sem defeito confirmado | [Jam](https://jam.dev/c/32adfca3-489f-4a4b-a08d-933c1d1a3c32) |
| [CT-RF24](CT-RF24_Edicao_Exercicio.md) | Edição de exercício aumenta o total e mantém duas entradas | Reprovado no trecho consultado; confirmar operação e identidade dos registros na reprodução | [BUG-012](../Relatorio-de-Bugs.md#bug-012), em triagem | [Jam](https://jam.dev/c/073f70d6-4052-4e0f-a4bb-e9f37305d618) |
| [CT-RF25](CT-RF25_Envio_Exercicio_Imagem.md) | Envio de exercício com imagem | A validar — criação visível; persistência e associação da imagem não confirmadas | Sem defeito confirmado | [Jam](https://jam.dev/c/25c37a9b-e9bd-4e0c-adf1-4da528ae1d58) |

## Inclusão complementar de 15/11/2026

| Caso | Funcionalidade | Resultado | Defeito | Jam |
| --- | --- | --- | --- | --- |
| [CT-RF26](CT-RF26_Exercicio_Campos_Vazios.md) | Envio de exercício com campos obrigatórios vazios | Reprovado — sem mensagem de validação visível | [BUG-013](../Relatorio-de-Bugs.md#bug-013), em triagem | [Jam](https://jam.dev/c/bc07ca5f-d3a9-45f6-84cb-12c0b562a211) |
| [CT-RF27](CT-RF27_Video_Campo_Imagem.md) | Vídeo selecionado no campo de imagem | Reprovado — arquivo não anexado e sem feedback visível | [BUG-014](../Relatorio-de-Bugs.md#bug-014), em triagem | [Jam](https://jam.dev/c/00740108-9a7d-4151-8723-171c89635567) |
| [CT-RF28](CT-RF28_Imagem_Campo_Video.md) | Imagem selecionada no campo de vídeo | Reprovado — arquivo não anexado e sem feedback visível | [BUG-015](../Relatorio-de-Bugs.md#bug-015), em triagem | [Jam](https://jam.dev/c/be9437a4-4fe9-4756-a2af-6777d3f43e25) |

## Inclusão RF34 — 15/11/2026

| Caso | Funcionalidade | Resultado | Defeito | Jam |
| --- | --- | --- | --- | --- |
| [CT-RF34](CT-RF34_Erro_Servidor_Excesso_Requisicoes.md) | Carregamento do dashboard e tratamento de falhas do servidor | Reprovado — múltiplas requisições retornam HTTP 500 | [BUG-018](../Relatorio-de-Bugs.md#bug-018), em triagem | [Jam](https://jam.dev/c/eea58e17-b62f-432b-97b2-b14c14bed555) |

## Inclusão RF29–RF33 — 15/11/2026

| Caso | Funcionalidade | Resultado | Defeito | Jam |
| --- | --- | --- | --- | --- |
| [CT-RF29](CT-RF29_Exclusao_GrupoMuscular.md) | Exclusão de grupo muscular | Reprovado — HTTP 500 e mensagem genérica | [BUG-016](../Relatorio-de-Bugs.md#bug-016), em triagem | [Jam](https://jam.dev/c/98008390-0040-475e-ba7b-7f1e72cc0b2e) |
| [CT-RF30](CT-RF30_Imagens_GruposMusculares.md) | Exibição das imagens dos grupos musculares | Reprovado — imagens quebradas e HTTP 422 | [BUG-017](../Relatorio-de-Bugs.md#bug-017), em triagem | [Jam](https://jam.dev/c/98008390-0040-475e-ba7b-7f1e72cc0b2e) |
| [CT-RF31](CT-RF31_Cadastro_GrupoMuscular.md) | Cadastro de grupo muscular | Aprovado conforme a gravação | — | [Jam](https://jam.dev/c/98008390-0040-475e-ba7b-7f1e72cc0b2e) |
| [CT-RF32](CT-RF32_Edicao_TipoMembro.md) | Edição do tipo de membro | Aprovado conforme a gravação | — | [Jam](https://jam.dev/c/98008390-0040-475e-ba7b-7f1e72cc0b2e) |
| [CT-RF33](CT-RF33_Filtros_GruposMusculares.md) | Filtros de grupos musculares | Aprovado conforme a gravação | — | [Jam](https://jam.dev/c/98008390-0040-475e-ba7b-7f1e72cc0b2e) |

Os casos abaixo têm como fonte uma única gravação da tela Grupos Musculares, de 15/11/2026 às 15h56 BRT, com 2 min 3 s. Os painéis de informações, rede e console do Jam foram lidos diretamente; não houve nova execução. As pastas locais de evidências desses casos ainda não foram criadas.

As três aprovações se limitam aos exemplos gravados. A cronologia não registra as requisições de criação, de atualização e de consulta com código de status; essas conclusões apoiam-se nos quadros e nos contadores da tela. A lógica de combinação dos filtros não ficou demonstrada, pois o único registro do código consultado também atendia ao tipo selecionado.

## Inclusão de 15/11/2026 — Objetivos de Treino

| Caso | Funcionalidade | Resultado | Defeito | Jam |
| --- | --- | --- | --- | --- |
| [CT-RF35](CT-RF35_Cadastro_Objetivo_Treino.md) | Cadastro de objetivo de treino retorna HTTP 500 | Reprovado nas evidências | [BUG-019](../Relatorio-de-Bugs.md#bug-019), em triagem | [Jam](https://jam.dev/c/1d474477-2411-4a81-b85c-74207402b783) |

O resultado é documental, com base em uma gravação; não houve nova execução ou reteste. A evidência local está em [Evidências](../Evidencias/CT-RF35_Cadastro_Objetivo_Treino/README.md).

## Inclusão de 15/11/2026 — Categorias Crossfit

| Caso | Funcionalidade | Resultado | Defeito | Jam |
| --- | --- | --- | --- | --- |
| [CT-RF38](CT-RF38_Cadastro_Categoria_Codigo_Automatico.md) | Cadastro de categoria com código automático e consulta pelo código | Aprovado conforme a gravação | — | [Jam](https://jam.dev/c/be1dbd05-217d-44c3-8a3d-240b7f6344e1) |

O resultado é documental, com base em uma gravação; não houve nova execução ou reteste. A evidência local está em [Evidências](../Evidencias/CT-RF38_Cadastro_Categoria_Codigo_Automatico/README.md).

## Inclusão de 15/11/2026 — SifitBox – Turmas

| Caso | Funcionalidade | Resultado | Defeito | Jam |
| --- | --- | --- | --- | --- |
| [CT-RF39](CT-RF39_Cadastro_Modalidade.md) | Cadastro de modalidade | Aprovado conforme a gravação | — | [Jam](https://jam.dev/c/ee9a133b-d6b1-442d-b4b0-dd87595b7e70) |
| [CT-RF40](CT-RF40_Exclusao_Turmas_Modalidades.md) | Exclusão de turmas e modalidades pela lixeira | A validar — regra ou contexto pendente | — | [Jam](https://jam.dev/c/ee9a133b-d6b1-442d-b4b0-dd87595b7e70) |
| [CT-RF41](CT-RF41_Cadastro_Turma_Sem_Modalidade.md) | Cadastro de turma sem modalidade, sem retorno visível | Reprovado nas evidências | [BUG-020](../Relatorio-de-Bugs.md#bug-020), em triagem | [Jam](https://jam.dev/c/ee9a133b-d6b1-442d-b4b0-dd87595b7e70) |

CT-RF39–CT-RF41 têm como fonte uma única gravação. Os resultados são documentais; nenhuma nova execução ou reteste foi realizada.

## Inclusão de 15/11/2026 — Pagar.me e Configurações

| Caso | Funcionalidade | Resultado | Defeito | Jam |
| --- | --- | --- | --- | --- |
| [CT-RF42](CT-RF42_Solicitacao_Saque_PagarMe.md) | Solicitação de saque no painel Pagar.me | A validar — regra ou contexto pendente | — | [Jam](https://jam.dev/c/e6e551ef-9196-4c79-b6a2-89747b1e8b33) |
| [CT-RF43](CT-RF43_Criacao_Cobranca_PagarMe.md) | Criação de cobrança no painel Pagar.me | Aprovado conforme a gravação | — | [Jam](https://jam.dev/c/e6e551ef-9196-4c79-b6a2-89747b1e8b33) |
| [CT-RF44](CT-RF44_Configuracoes_Home_Salvamento.md) | Alteração e salvamento das Configurações (Home) | A validar — regra ou contexto pendente | — | [Jam](https://jam.dev/c/e6e551ef-9196-4c79-b6a2-89747b1e8b33) |
| [CT-RF45](CT-RF45_Painel_PagarMe_Periodo.md) | Painel Pagar.me mantém Recebimentos e gráfico ao trocar o período | Reprovado nas evidências | [BUG-021](../Relatorio-de-Bugs.md#bug-021), em triagem | [Jam](https://jam.dev/c/e6e551ef-9196-4c79-b6a2-89747b1e8b33) |

Cada grupo tem como fonte uma única gravação. Os resultados são documentais; nenhuma nova execução ou reteste foi realizada.

## Inclusão de 15/11/2026 — Despesas Fixas

| Caso | Funcionalidade | Resultado | Defeito | Jam |
| --- | --- | --- | --- | --- |
| [CT-RF46](CT-RF46_Filtros_Despesas_Fixas.md) | Filtros da tela Despesas Fixas por código e por nome | Aprovado conforme a gravação | — | [Jam](https://jam.dev/c/a4bac99d-e436-4792-831e-8c3a875272bb) |
| [CT-RF47](CT-RF47_Cadastro_Despesa_Fixa.md) | Cadastro de despesa fixa com duas requisições de criação | A validar — regra ou contexto pendente | — | [Jam](https://jam.dev/c/a4bac99d-e436-4792-831e-8c3a875272bb) |
| [CT-RF48](CT-RF48_Exclusao_Despesa_Fixa.md) | Exclusão de despesa fixa com confirmação | Aprovado conforme a gravação | — | [Jam](https://jam.dev/c/a4bac99d-e436-4792-831e-8c3a875272bb) |
| [CT-RF49](CT-RF49_Edicao_Despesa_Fixa.md) | Edição de despesa fixa | Aprovado conforme a gravação | — | [Jam](https://jam.dev/c/a4bac99d-e436-4792-831e-8c3a875272bb) |

Cada grupo tem como fonte uma única gravação. Os resultados são documentais; nenhuma nova execução ou reteste foi realizada.

## Inclusão de 15/11/2026 — Relatórios

| Caso | Funcionalidade | Resultado | Defeito | Jam |
| --- | --- | --- | --- | --- |
| [CT-RF50](CT-RF50_Relatorio_Matriculas.md) | Relatório de Matrículas em PDF | Aprovado conforme a gravação | — | [Jam](https://jam.dev/c/3b4777a4-e1b0-4038-9b06-26c73669d7d1) |
| [CT-RF51](CT-RF51_Relatorio_Contas_Receber.md) | Relatório de Contas a Receber sem Valor a Receber | Reprovado nas evidências | [BUG-022](../Relatorio-de-Bugs.md#bug-022), em triagem | [Jam](https://jam.dev/c/3b4777a4-e1b0-4038-9b06-26c73669d7d1) |
| [CT-RF52](CT-RF52_Relatorio_Contas_Pagar_Pagas.md) | Relatório de Contas a Pagar (Pagas) sem registros | A validar — regra ou contexto pendente | — | [Jam](https://jam.dev/c/3b4777a4-e1b0-4038-9b06-26c73669d7d1) |
| [CT-RF53](CT-RF53_Relatorio_Avaliacoes_Vazio.md) | Relatório de Avaliações gera arquivo vazio | Reprovado nas evidências | [BUG-023](../Relatorio-de-Bugs.md#bug-023), em triagem | [Jam](https://jam.dev/c/3b4777a4-e1b0-4038-9b06-26c73669d7d1) |
| [CT-RF54](CT-RF54_Relatorio_Clientes_Vazio.md) | Relatório de Clientes gera arquivo vazio | Reprovado nas evidências | [BUG-023](../Relatorio-de-Bugs.md#bug-023), em triagem | [Jam](https://jam.dev/c/3b4777a4-e1b0-4038-9b06-26c73669d7d1) |
| [CT-RF55](CT-RF55_Relatorio_Colaboradores_Vazio.md) | Relatório de Colaboradores gera arquivo vazio | Reprovado nas evidências | [BUG-023](../Relatorio-de-Bugs.md#bug-023), em triagem | [Jam](https://jam.dev/c/3b4777a4-e1b0-4038-9b06-26c73669d7d1) |
| [CT-RF56](CT-RF56_Relatorio_Caixas_Vazio.md) | Relatório de Caixas gera arquivo vazio | Reprovado nas evidências | [BUG-023](../Relatorio-de-Bugs.md#bug-023), em triagem | [Jam](https://jam.dev/c/3b4777a4-e1b0-4038-9b06-26c73669d7d1) |

Cada grupo tem como fonte uma única gravação. Os resultados são documentais; nenhuma nova execução ou reteste foi realizada. Os PDFs baixados estão nas pastas de evidências de CT-RF50 a CT-RF56.

## Inclusão de 15/11/2026 — Prospecção

| Caso | Funcionalidade | Resultado | Defeito | Jam |
| --- | --- | --- | --- | --- |
| [CT-RF58](CT-RF58_Tema_Notificacoes_Prospeccao.md) | Alternância de tema e painel de notificações em Prospecção | Aprovado conforme a gravação | — | [Jam](https://jam.dev/c/308607ff-8abc-40af-8c7c-429ce506ed64) |
| [CT-RF59](CT-RF59_Busca_Leads_Prospeccao.md) | Busca de leads por texto na tela Prospecção | Aprovado conforme a gravação | — | [Jam](https://jam.dev/c/308607ff-8abc-40af-8c7c-429ce506ed64) |
| [CT-RF60](CT-RF60_Filtro_Estagio_Leads.md) | Filtro de leads por estágio e limpeza dos filtros | Aprovado conforme a gravação | — | [Jam](https://jam.dev/c/308607ff-8abc-40af-8c7c-429ce506ed64) |
| [CT-RF61](CT-RF61_Cadastro_Lead_Prospeccao.md) | Cadastro de lead com duas requisições de criação | A validar — regra ou contexto pendente | — | [Jam](https://jam.dev/c/308607ff-8abc-40af-8c7c-429ce506ed64) |
| [CT-RF62](CT-RF62_Telefone_Lead_Sem_Validacao.md) | Telefone do lead aceita 30 dígitos sem validação | Reprovado nas evidências | [BUG-024](../Relatorio-de-Bugs.md#bug-024), em triagem | [Jam](https://jam.dev/c/308607ff-8abc-40af-8c7c-429ce506ed64) |
| [CT-RF63](CT-RF63_Edicao_Lead_Prospeccao.md) | Visualização e edição de lead na tela Prospecção | Aprovado conforme a gravação | — | [Jam](https://jam.dev/c/308607ff-8abc-40af-8c7c-429ce506ed64) |

O grupo tem como fonte uma única gravação. Os resultados são documentais; nenhuma nova execução ou reteste foi realizada.

## Inclusão de 15/11/2026 — Contas a Pagar

| Caso | Funcionalidade | Resultado | Defeito | Jam |
| --- | --- | --- | --- | --- |
| [CT-RF64](CT-RF64_Filtros_Contas_Pagar.md) | Filtros da tela Contas a Pagar por nome, data e status | A validar — regra ou contexto pendente | — | [Jam](https://jam.dev/c/5d0afaf4-5abd-4e85-923f-27448304a9ef) |
| [CT-RF65](CT-RF65_Cadastro_Conta_Colaborador_Sem_Colaborador.md) | Conta a pagar a colaborador é cadastrada sem colaborador informado | Reprovado nas evidências | [BUG-025](../Relatorio-de-Bugs.md#bug-025), em triagem | [Jam](https://jam.dev/c/5d0afaf4-5abd-4e85-923f-27448304a9ef) |
| [CT-RF66](CT-RF66_Busca_Colaborador_Conta_Pagar.md) | Busca de colaborador no cadastro de conta a pagar | A validar — regra ou contexto pendente | — | [Jam](https://jam.dev/c/5d0afaf4-5abd-4e85-923f-27448304a9ef) |
| [CT-RF67](CT-RF67_Visualizacao_Conta_Pagar.md) | Visualização dos dados de uma conta a pagar | Aprovado conforme a gravação | — | [Jam](https://jam.dev/c/5d0afaf4-5abd-4e85-923f-27448304a9ef) |
| [CT-RF68](CT-RF68_Exclusao_Conta_Pagar.md) | Exclusão de conta a pagar com confirmação | Aprovado conforme a gravação | — | [Jam](https://jam.dev/c/5d0afaf4-5abd-4e85-923f-27448304a9ef) |

Cada grupo tem como fonte uma única gravação. Os resultados são documentais; nenhuma nova execução ou reteste foi realizada.

## Inclusão de 15/11/2026 — Modelos de Contrato

| Caso | Funcionalidade | Resultado | Defeito | Jam |
| --- | --- | --- | --- | --- |
| [CT-RF69](CT-RF69_Variaveis_Preview_Modelo_Contrato.md) | Variáveis e pré-visualização do texto do modelo de contrato | Aprovado conforme a gravação | — | [Jam](https://jam.dev/c/44dbbd39-6915-45d6-8dd1-5f30c1432ca0) |
| [CT-RF70](CT-RF70_Cadastro_Modelo_Contrato.md) | Cadastro de modelo de contrato | Aprovado conforme a gravação | — | [Jam](https://jam.dev/c/44dbbd39-6915-45d6-8dd1-5f30c1432ca0) |
| [CT-RF71](CT-RF71_Listagem_Modelos_Contrato_Vazia.md) | Listagem de modelos de contrato aparece vazia com 15 modelos retornados | Reprovado nas evidências | [BUG-026](../Relatorio-de-Bugs.md#bug-026), em triagem | [Jam](https://jam.dev/c/44dbbd39-6915-45d6-8dd1-5f30c1432ca0) |

Cada grupo tem como fonte uma única gravação. Os resultados são documentais; nenhuma nova execução ou reteste foi realizada.

## Inclusão de 15/11/2026 — Planos

| Caso | Funcionalidade | Resultado | Defeito | Jam |
| --- | --- | --- | --- | --- |
| [CT-RF72](CT-RF72_Filtros_Planos.md) | Filtros da tela Planos por código e nome | Aprovado conforme a gravação | — | [Jam](https://jam.dev/c/233c5d21-e108-4a55-b6f6-8738cb3fc6a6) |
| [CT-RF73](CT-RF73_Tema_Notificacoes_Planos.md) | Alternância de tema e painel de notificações em Planos | Aprovado conforme a gravação | — | [Jam](https://jam.dev/c/233c5d21-e108-4a55-b6f6-8738cb3fc6a6) |
| [CT-RF74](CT-RF74_Cadastro_Plano.md) | Cadastro de plano pelo modal Novo Plano | Aprovado conforme a gravação | — | [Jam](https://jam.dev/c/233c5d21-e108-4a55-b6f6-8738cb3fc6a6) |
| [CT-RF75](CT-RF75_Contador_Ativos_Planos.md) | Cartão Ativos de Planos aumenta ao cadastrar e editar planos inativos | Reprovado nas evidências | [BUG-027](../Relatorio-de-Bugs.md#bug-027), em triagem | [Jam](https://jam.dev/c/233c5d21-e108-4a55-b6f6-8738cb3fc6a6) |
| [CT-RF76](CT-RF76_Edicao_Plano.md) | Edição de plano pelo modal Editar Plano | Aprovado conforme a gravação | — | [Jam](https://jam.dev/c/233c5d21-e108-4a55-b6f6-8738cb3fc6a6) |

Cada grupo tem como fonte uma única gravação. Os resultados são documentais; nenhuma nova execução ou reteste foi realizada.

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md) · [Plano](../Plano%20de%20testes.md) · [Evidências](../Evidencias/README.md)
