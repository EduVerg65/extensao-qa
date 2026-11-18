# 🧪 Índice dos cenários de teste — SIFIT

**Atualização:** 17/11/2026. 146 casos documentados: 68 aprovados, 57 reprovados e 21 a validar. 52 defeitos registrados (10 abertos e 42 em triagem) e 57 casos com reteste corretivo pendente. Escopo: CT-RF01–CT-RF35, CT-RF38–CT-RF62 e CT-RF65–CT-RF150.

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

## Inclusão de 15/11/2026 — Colaboradores

| Caso | Funcionalidade | Resultado | Defeito | Jam |
| --- | --- | --- | --- | --- |
| [CT-RF65](CT-RF65_Data_Nascimento_Futura_Colaborador.md) | Data de nascimento futura | Reprovado — atualização aceita com HTTP 200 | [BUG-026](../Relatorio-de-Bugs.md#bug-026) | [Jam](https://jam.dev/c/6dd75961-8e8f-4c8e-939a-19595a1f8a32) |
| [CT-RF66](CT-RF66_Data_Nascimento_Obrigatoria_Colaborador.md) | Data de nascimento obrigatória vazia | Reprovado — atualização aceita com HTTP 200 | [BUG-027](../Relatorio-de-Bugs.md#bug-027) | [Jam](https://jam.dev/c/04aa5ba0-ac7e-43b6-a7f3-91ae82417a85) |
| [CT-RF67](CT-RF67_CREF_Formato_Colaborador.md) | Formato do CREF | Reprovado — texto livre aceito com HTTP 200 | [BUG-028](../Relatorio-de-Bugs.md#bug-028) | [Jam](https://jam.dev/c/243d9699-4bee-495d-ae65-9a02e42813b3) |
| [CT-RF68](CT-RF68_Edicao_Colaborador_Campo_Obrigatorio_Vazio.md) | Edição com campo obrigatório vazio | Reprovado — atualização aceita com HTTP 200 | [BUG-029](../Relatorio-de-Bugs.md#bug-029) | [Jam](https://jam.dev/c/4219c1b3-085e-4218-b181-5cf448d64cea) |
| [CT-RF69](CT-RF69_Funcao_Duplicada_Colaborador.md) | Função duplicada para o colaborador | Reprovado — três associações iguais | [BUG-030](../Relatorio-de-Bugs.md#bug-030) | [Jam](https://jam.dev/c/ba2400f9-dbb0-45bc-a509-187249dbe9da) |
| [CT-RF70](CT-RF70_Exclusao_Colaborador_Erro_500.md) | Exclusão de colaborador | Reprovado — HTTP 500 e erro interno | [BUG-031](../Relatorio-de-Bugs.md#bug-031) | [Jam](https://jam.dev/c/05be297b-22d9-4d26-beff-937526bcd816) |
| [CT-RF71](CT-RF71_Busca_Nome_Colaborador_Paginacao.md) | Busca por nome durante a paginação | Reprovado — próxima página exibe nomes fora do filtro | [BUG-033](../Relatorio-de-Bugs.md#bug-033) | [Jam](https://jam.dev/c/b35516e3-c571-47ea-b233-28f00d1fca4c) |
| [CT-RF72](CT-RF72_Busca_Codigo_Existente_Colaborador.md) | Busca por código existente | Aprovado conforme a gravação | — | [Jam](https://jam.dev/c/415a6ea3-273b-40f7-b3e4-f2b767dc7dfd) |
| [CT-RF73](CT-RF73_Busca_Codigo_Inexistente_Colaborador.md) | Busca por código inexistente | Reprovado — retorna uma linha vazia | [BUG-034](../Relatorio-de-Bugs.md#bug-034) | [Jam](https://jam.dev/c/cdbb3d76-3d6a-4d36-adf9-edd935b5a449) |

## Inclusão de 15/11/2026 — Grupos (treino)

| Caso | Funcionalidade | Resultado | Defeito | Jam |
| --- | --- | --- | --- | --- |
| [CT-RF57](CT-RF57_Exclusao_Grupo.md) | Exclusão de grupo retorna HTTP 500 | Reprovado nas evidências | [BUG-024](../Relatorio-de-Bugs.md#bug-024), em triagem | [Jam](https://jam.dev/c/b1231a75-1a65-4bf0-b795-f52a8c7d3365) |
| [CT-RF58](CT-RF58_Edicao_Grupo.md) | Edição de grupo não persiste o campo status | Reprovado nas evidências | [BUG-025](../Relatorio-de-Bugs.md#bug-025), em triagem | [Jam](https://jam.dev/c/b1231a75-1a65-4bf0-b795-f52a8c7d3365) |

A mesma gravação mostra o cadastro bem-sucedido de um novo grupo ("Treino sla", código 11) antes das duas edições e da tentativa de exclusão aqui reprovadas. No CT-RF57, o endpoint e a mensagem genérica retornada coincidem com os já registrados no BUG-016 para a exclusão de grupo muscular. No CT-RF58, a alteração do campo Status para "Inativo" retorna sucesso sem persistir o valor, enquanto a alteração do campo Descrição é persistida corretamente. O resultado é documental; não houve nova execução ou reteste.

## Inclusão de 15/11/2026 — Fichas de Anamnese

| Caso | Funcionalidade | Resultado | Defeito | Jam |
| --- | --- | --- | --- | --- |
| [CT-RF59](CT-RF59_Cadastro_Anamnese.md) | Cadastro de anamnese retorna HTTP 500 ao salvar ou aplicar | Reprovado nas evidências | [BUG-032](../Relatorio-de-Bugs.md#bug-032), em triagem | [Jam](https://jam.dev/c/7be0fe71-3419-4050-b63f-473d943fa08e) |

Na mesma gravação, sete tentativas de cadastrar uma anamnese para o aluno "Jorge" — quatro pela rota de aplicar e três pela de salvar rascunho, com dois modelos de anamnese e três respostas diferentes — retornam todas HTTP 500 com a mesma mensagem genérica, coincidindo com o padrão já registrado nos BUG-016 e BUG-024. Nenhuma anamnese é cadastrada com sucesso ao longo da gravação. O resultado é documental; não houve nova execução ou reteste.

## Inclusão de 16/11/2026 — Modelos de Anamnese

| Caso | Funcionalidade | Resultado | Defeito | Jam |
| --- | --- | --- | --- | --- |
| [CT-RF60](CT-RF60_Gestao_Modelos_Anamnese.md) | Busca, cadastro, edição e exclusão de modelos de anamnese | Aprovado conforme a gravação | — | [Jam](https://jam.dev/c/4c1e9deb-20ca-417f-ad09-48749857266e) |

Na mesma gravação, busca e filtro da listagem, cadastro de um modelo com três perguntas do banco, duas edições e duas exclusões de modelos retornam HTTP 200 ou 201 em todas as quinze requisições identificadas aos endpoints `/api/modelos-anamnese/*`, sem nenhuma ocorrência de erro 4xx ou 5xx. Nenhum defeito foi identificado no fluxo avaliado. O resultado é documental; não houve nova execução ou reteste.

---

## Inclusão de 16/11/2026 — Categorias de Anamnese

| Caso | Funcionalidade | Resultado | Defeito | Jam |
| --- | --- | --- | --- | --- |
| [CT-RF61](CT-RF61_Gestao_Categorias_Anamnese.md) | Filtro, busca, cadastro, edição e exclusão de categorias de anamnese | Aprovado conforme a gravação | — | [Jam](https://jam.dev/c/fdb1c9f8-c428-4726-9742-617800325d09) |

Na mesma gravação, filtro por status, busca por texto, cadastro de uma categoria, três edições sucessivas (ícone, nome e status), o cancelamento correto de uma quarta edição sem salvar e a exclusão da categoria retornam HTTP 200 ou 201 em todas as sete requisições identificadas aos endpoints `/api/categorias-anamnese/*`, sem nenhuma ocorrência de erro 4xx ou 5xx. Nenhum defeito foi identificado no fluxo avaliado. O resultado é documental; não houve nova execução ou reteste.

---

## Inclusão de 16/11/2026 — Perguntas Anamnese

| Caso | Funcionalidade | Resultado | Defeito | Jam |
| --- | --- | --- | --- | --- |
| [CT-RF62](CT-RF62_Edicao_Pergunta_Anamnese.md) | Edição do tipo de resposta e do status de pergunta de anamnese | Reprovado nas evidências | [BUG-044](../Relatorio-de-Bugs.md#bug-044), em triagem | [Jam](https://jam.dev/c/84b116fb-4640-4b1e-9148-9a169b8aa2b0) |

Na mesma gravação, o cadastro de uma nova pergunta de anamnese é concluído com sucesso, mas as quatro tentativas seguintes de editar o tipo de resposta e/ou o status dessa mesma pergunta retornam HTTP 500 em todas as ocorrências, com o mesmo corpo genérico de erro já observado em outros módulos; nenhuma alteração é persistida. O resultado é documental; não houve nova execução ou reteste.

---

## Inclusão de 16/11/2026 — Prospecção e Bandeiras de Cartão

| Caso | Funcionalidade | Resultado | Defeito | Jam |
| --- | --- | --- | --- | --- |
| [CT-RF74](CT-RF74_Temas_Prospeccao.md) | Alternar entre os temas claro e escuro na Prospecção | Aprovado conforme o resumo da gravação | — | [Jam](https://jam.dev/c/5dc9fc15-8e13-4f90-b21f-a49aedc6731e) |
| [CT-RF75](CT-RF75_Detalhes_Lead_Cancelamento.md) | Consultar os detalhes de um lead e cancelar a edição | Aprovado conforme o resumo da gravação | — | [Jam](https://jam.dev/c/7ef0ee0b-497e-48b8-a57d-cd914558d303) |
| [CT-RF76](CT-RF76_Exclusao_Leads_Confirmacao.md) | Excluir leads com confirmação | Aprovado conforme o resumo da gravação | — | [Jam](https://jam.dev/c/2ac5e5ed-b10f-4cc9-9f97-7ba65ca560f8) |
| [CT-RF77](CT-RF77_Cadastro_Lead_Novo_Contato.md) | Cadastrar lead no estágio Novo Contato | Aprovado conforme o resumo da gravação | — | [Jam](https://jam.dev/c/29447c6a-90f5-48b2-ac5d-d43cad44a782) |
| [CT-RF78](CT-RF78_Cadastro_Lead_Interessado.md) | Cadastrar lead no estágio Interessado | Aprovado conforme o resumo da gravação | — | [Jam](https://jam.dev/c/f8735cbf-4043-4467-b43f-3cad7eff0da8) |
| [CT-RF79](CT-RF79_Cadastro_Lead_Aula_Experimental.md) | Cadastrar lead no estágio Fez Aula Experimental | Aprovado conforme o resumo da gravação | — | [Jam](https://jam.dev/c/bef3d877-056b-4274-87c3-da37869c54fd) |
| [CT-RF80](CT-RF80_Cadastro_Lead_Proposta.md) | Cadastrar lead no estágio Proposta | Aprovado conforme o resumo da gravação | — | [Jam](https://jam.dev/c/84f94285-ae5f-4f95-b640-a9b107565aa6) |
| [CT-RF81](CT-RF81_Cadastro_Bandeira_Parcela_Listagem.md) | Cadastrar bandeira com parcela e conferir a listagem | Reprovado nas evidências resumidas | [BUG-035](../Relatorio-de-Bugs.md#bug-035) | [Jam](https://jam.dev/c/2f0280fb-6b7f-4cf0-a45c-02f8c16b6c5e) |
| [CT-RF82](CT-RF82_Tema_Escuro_Bandeiras.md) | Verificar aplicação dos temas na tela de Bandeiras | Reprovado nas evidências resumidas | [BUG-036](../Relatorio-de-Bugs.md#bug-036) | [Jam](https://jam.dev/c/ae4dc198-8a42-4451-898a-fb376596c744) |
| [CT-RF83](CT-RF83_Cadastro_Lead_Apenas_Nome.md) | Validar cadastro de lead preenchendo apenas o nome | Reprovado conforme o relato; regra de obrigatoriedade a confirmar | [BUG-037](../Relatorio-de-Bugs.md#bug-037) | [Jam](https://jam.dev/c/ef3df03c-16ce-4cb6-b0c7-d04514cab4f6) |
| [CT-RF84](CT-RF84_Cadastro_Lead_Fechado.md) | Cadastrar lead no estágio Fechado | Aprovado conforme o resumo da gravação | — | [Jam](https://jam.dev/c/775b9003-fdf7-4ad5-8882-15ba606b6674) |

Integração documental dos arquivos RESUMO.txt fornecidos em `C:\Users\Leonardo\Desktop\evidencias`, com data de gravação e análise informada de 16/11/2026. Os Jams não foram reabertos nesta integração; eventos de rede, horários e quadros abaixo são transcritos dos resumos, sem verificação independente. Não houve nova execução do SIFIT, reteste, consulta ao banco, logs ou código.

CT-RF74–CT-RF84 acrescentam oito aprovações e três reprovações conforme os resumos fornecidos, com BUG-035–BUG-037 em triagem. CT-RF83 mantém a classificação do relato, condicionada à confirmação da regra de obrigatoriedade. Os dez casos anteriores a validar permanecem inalterados.

Os resumos originais estão no [índice das evidências](../Evidencias/README.md).

---
## Inclusão de 15/11/2026 — Prospecção

| Caso | Funcionalidade | Resultado | Defeito | Jam |
| --- | --- | --- | --- | --- |
| [CT-RF85](CT-RF85_Tema_Notificacoes_Prospeccao.md) | Alternância de tema e painel de notificações em Prospecção | Aprovado conforme a gravação | — | [Jam](https://jam.dev/c/308607ff-8abc-40af-8c7c-429ce506ed64) |
| [CT-RF86](CT-RF86_Busca_Leads_Prospeccao.md) | Busca de leads por texto na tela Prospecção | Aprovado conforme a gravação | — | [Jam](https://jam.dev/c/308607ff-8abc-40af-8c7c-429ce506ed64) |
| [CT-RF87](CT-RF87_Filtro_Estagio_Leads.md) | Filtro de leads por estágio e limpeza dos filtros | Aprovado conforme a gravação | — | [Jam](https://jam.dev/c/308607ff-8abc-40af-8c7c-429ce506ed64) |
| [CT-RF88](CT-RF88_Cadastro_Lead_Prospeccao.md) | Cadastro de lead com duas requisições de criação | A validar — regra ou contexto pendente | — | [Jam](https://jam.dev/c/308607ff-8abc-40af-8c7c-429ce506ed64) |
| [CT-RF89](CT-RF89_Telefone_Lead_Sem_Validacao.md) | Telefone do lead aceita 30 dígitos sem validação | Reprovado nas evidências | [BUG-038](../Relatorio-de-Bugs.md#bug-038), em triagem | [Jam](https://jam.dev/c/308607ff-8abc-40af-8c7c-429ce506ed64) |
| [CT-RF90](CT-RF90_Edicao_Lead_Prospeccao.md) | Visualização e edição de lead na tela Prospecção | Aprovado conforme a gravação | — | [Jam](https://jam.dev/c/308607ff-8abc-40af-8c7c-429ce506ed64) |

O grupo tem como fonte uma única gravação. Os resultados são documentais; nenhuma nova execução ou reteste foi realizada.

## Inclusão de 15/11/2026 — Contas a Pagar

| Caso | Funcionalidade | Resultado | Defeito | Jam |
| --- | --- | --- | --- | --- |
| [CT-RF91](CT-RF91_Filtros_Contas_Pagar.md) | Filtros da tela Contas a Pagar por nome, data e status | A validar — regra ou contexto pendente | — | [Jam](https://jam.dev/c/5d0afaf4-5abd-4e85-923f-27448304a9ef) |
| [CT-RF92](CT-RF92_Cadastro_Conta_Colaborador_Sem_Colaborador.md) | Conta a pagar a colaborador é cadastrada sem colaborador informado | Reprovado nas evidências | [BUG-039](../Relatorio-de-Bugs.md#bug-039), em triagem | [Jam](https://jam.dev/c/5d0afaf4-5abd-4e85-923f-27448304a9ef) |
| [CT-RF93](CT-RF93_Busca_Colaborador_Conta_Pagar.md) | Busca de colaborador no cadastro de conta a pagar | A validar — regra ou contexto pendente | — | [Jam](https://jam.dev/c/5d0afaf4-5abd-4e85-923f-27448304a9ef) |
| [CT-RF94](CT-RF94_Visualizacao_Conta_Pagar.md) | Visualização dos dados de uma conta a pagar | Aprovado conforme a gravação | — | [Jam](https://jam.dev/c/5d0afaf4-5abd-4e85-923f-27448304a9ef) |
| [CT-RF95](CT-RF95_Exclusao_Conta_Pagar.md) | Exclusão de conta a pagar com confirmação | Aprovado conforme a gravação | — | [Jam](https://jam.dev/c/5d0afaf4-5abd-4e85-923f-27448304a9ef) |

Cada grupo tem como fonte uma única gravação. Os resultados são documentais; nenhuma nova execução ou reteste foi realizada.

## Inclusão de 15/11/2026 — Modelos de Contrato

| Caso | Funcionalidade | Resultado | Defeito | Jam |
| --- | --- | --- | --- | --- |
| [CT-RF96](CT-RF96_Variaveis_Preview_Modelo_Contrato.md) | Variáveis e pré-visualização do texto do modelo de contrato | Aprovado conforme a gravação | — | [Jam](https://jam.dev/c/44dbbd39-6915-45d6-8dd1-5f30c1432ca0) |
| [CT-RF97](CT-RF97_Cadastro_Modelo_Contrato.md) | Cadastro de modelo de contrato | Aprovado conforme a gravação | — | [Jam](https://jam.dev/c/44dbbd39-6915-45d6-8dd1-5f30c1432ca0) |
| [CT-RF98](CT-RF98_Listagem_Modelos_Contrato_Vazia.md) | Listagem de modelos de contrato aparece vazia com 15 modelos retornados | Reprovado nas evidências | [BUG-040](../Relatorio-de-Bugs.md#bug-040), em triagem | [Jam](https://jam.dev/c/44dbbd39-6915-45d6-8dd1-5f30c1432ca0) |

Cada grupo tem como fonte uma única gravação. Os resultados são documentais; nenhuma nova execução ou reteste foi realizada.

## Inclusão de 15/11/2026 — Planos

| Caso | Funcionalidade | Resultado | Defeito | Jam |
| --- | --- | --- | --- | --- |
| [CT-RF99](CT-RF99_Filtros_Planos.md) | Filtros da tela Planos por código e nome | Aprovado conforme a gravação | — | [Jam](https://jam.dev/c/233c5d21-e108-4a55-b6f6-8738cb3fc6a6) |
| [CT-RF100](CT-RF100_Tema_Notificacoes_Planos.md) | Alternância de tema e painel de notificações em Planos | Aprovado conforme a gravação | — | [Jam](https://jam.dev/c/233c5d21-e108-4a55-b6f6-8738cb3fc6a6) |
| [CT-RF101](CT-RF101_Cadastro_Plano.md) | Cadastro de plano pelo modal Novo Plano | Aprovado conforme a gravação | — | [Jam](https://jam.dev/c/233c5d21-e108-4a55-b6f6-8738cb3fc6a6) |
| [CT-RF102](CT-RF102_Contador_Ativos_Planos.md) | Cartão Ativos de Planos aumenta ao cadastrar e editar planos inativos | Reprovado nas evidências | [BUG-041](../Relatorio-de-Bugs.md#bug-041), em triagem | [Jam](https://jam.dev/c/233c5d21-e108-4a55-b6f6-8738cb3fc6a6) |
| [CT-RF103](CT-RF103_Edicao_Plano.md) | Edição de plano pelo modal Editar Plano | Aprovado conforme a gravação | — | [Jam](https://jam.dev/c/233c5d21-e108-4a55-b6f6-8738cb3fc6a6) |

Cada grupo tem como fonte uma única gravação. Os resultados são documentais; nenhuma nova execução ou reteste foi realizada.

## Inclusão de 16/11/2026 — Tipos de Pagamento

| Caso | Funcionalidade | Resultado | Defeito | Jam |
| --- | --- | --- | --- | --- |
| [CT-RF104](CT-RF104_Filtros_Tipos_Pagamento.md) | Filtros de busca da tela Tipos de Pagamento | A validar — regra ou contexto pendente | — | [Jam](https://jam.dev/c/e8734e3d-3f8e-458b-8c7d-e85eea882e50) |
| [CT-RF105](CT-RF105_Cadastro_Tipo_Pagamento_Status.md) | Cadastro de tipo de pagamento com status Ativo não é refletido | Reprovado nas evidências | [BUG-042](../Relatorio-de-Bugs.md#bug-042), em triagem | [Jam](https://jam.dev/c/e8734e3d-3f8e-458b-8c7d-e85eea882e50) |
| [CT-RF106](CT-RF106_Edicao_Tipo_Pagamento.md) | Edição de tipo de pagamento pela lupa da listagem | Aprovado conforme a gravação | — | [Jam](https://jam.dev/c/e8734e3d-3f8e-458b-8c7d-e85eea882e50) |
| [CT-RF107](CT-RF107_Exclusao_Tipo_Pagamento_Em_Uso.md) | Exclusão de tipo de pagamento em uso retorna HTTP 404 com erro SQL | Reprovado nas evidências | [BUG-043](../Relatorio-de-Bugs.md#bug-043), em triagem | [Jam](https://jam.dev/c/e8734e3d-3f8e-458b-8c7d-e85eea882e50) |
| [CT-RF108](CT-RF108_Tema_Notificacoes_Tipos_Pagamento.md) | Tema Claro/Escuro e notificações na tela Tipos de Pagamento | Aprovado conforme a gravação | — | [Jam](https://jam.dev/c/e8734e3d-3f8e-458b-8c7d-e85eea882e50) |

Os cinco casos têm como fonte uma única gravação. Os resultados são documentais; nenhuma nova execução ou reteste foi realizada.

## Inclusão de 17/11/2026 — Modelos de Ficha

| Caso | Funcionalidade | Resultado | Defeito | Jam |
| --- | --- | --- | --- | --- |
| [CT-RF109](CT-RF109_Modelo_Ficha_Sem_Nome.md) | Bloquear cadastro de modelo de ficha sem nome | Aprovado conforme a gravação | — | [Jam — PED-25](https://jam.dev/c/fb5673c9-3cd1-46c4-88f4-d5fb32574a8e) |
| [CT-RF110](CT-RF110_Cancelar_Cadastro_Modelo_Ficha.md) | Cancelar cadastro de modelo de ficha preenchido | Aprovado conforme a gravação | — | [Jam — PED-26](https://jam.dev/c/a2a39e11-04f4-40aa-a97e-75a57a5f1b0f) |
| [CT-RF111](CT-RF111_Busca_Modelo_Ficha_Codigo_Inexistente.md) | Buscar modelo de ficha por código inexistente | A validar — regra ou contexto pendente | — | [Jam — PED-27](https://jam.dev/c/c1aecaa8-39c7-49b0-89af-9de47a68ba40) |
| [CT-RF112](CT-RF112_Busca_Modelo_Ficha_Titulo_Inexistente.md) | Buscar modelo de ficha por título inexistente | A validar — regra ou contexto pendente | — | [Jam — PED-28](https://jam.dev/c/0c385452-2aeb-427f-8159-79549fe7371d) |
| [CT-RF113](CT-RF113_Busca_Modelo_Ficha_Filtros_Combinados.md) | Buscar modelos de ficha com filtros combinados | A validar — regra ou contexto pendente | — | [Jam — PED-29](https://jam.dev/c/006f9722-e643-4b65-904a-25471a7b90ed) |
| [CT-RF114](CT-RF114_Limpeza_Filtros_Modelos_Ficha.md) | Limpar os filtros de Modelos de Ficha | Aprovado conforme a gravação | — | [Jam — PED-30](https://jam.dev/c/297eec2b-7be4-498b-a0e6-e962ed93cc00) |
| [CT-RF115](CT-RF115_Nova_Busca_Modelos_Ficha_Sem_Filtros.md) | Pesquisar novamente modelos de ficha sem filtros | A validar — regra ou contexto pendente | — | [Jam — PED-30](https://jam.dev/c/297eec2b-7be4-498b-a0e6-e962ed93cc00) |

A revisão de Modelos de Ficha inclui CT-RF109–CT-RF115 com base em 6 gravações do Jam de 16/11/2026. A revisão documental foi feita em 17/11/2026.

## Inclusão de 17/11/2026 — Configurações e Modelos de Ficha (CT-RF116–CT-RF121)

| Caso | Funcionalidade | Resultado | Defeito | Jam |
| --- | --- | --- | --- | --- |
| [CT-RF116](CT-RF116_Configuracoes_Dias_Ausencia_Vazio.md) | Validar o salvamento com o campo de dias de ausência vazio | A validar — regra ou contexto pendente | — | [Jam — PED-20 — Dias de ausência vazio](https://jam.dev/c/4e96d4fa-65b5-459b-a795-854496e5753c) |
| [CT-RF117](CT-RF117_Configuracoes_Cancelar_Alteracao.md) | Cancelar uma alteração nas Configurações sem salvar | Aprovado conforme a gravação | — | [Jam — PED-20 — Cancelar alteração](https://jam.dev/c/e8faa199-1177-4563-8b00-590606669a1d) |
| [CT-RF118](CT-RF118_Configuracoes_Trabalha_Com_Turmas.md) | Alterar e persistir a opção Trabalha com turmas? | Aprovado conforme a gravação | — | [Jam — PED-21 — Trabalha com turmas](https://jam.dev/c/a51c33a5-537a-40fd-a55d-990b70ac0696) |
| [CT-RF119](CT-RF119_Configuracoes_Academia_Marcada_Box.md) | Conferir a configuração Academia marcada como Box? | Aprovado conforme a gravação | — | [Jam — PED-22 — Academia marcada como Box](https://jam.dev/c/16dc862d-c3f9-4392-9037-526818e86cd6) |
| [CT-RF120](CT-RF120_Configuracoes_Acesso_Desktop.md) | Conferir a configuração de acesso ao sistema desktop | Aprovado conforme a gravação | — | [Jam — PED-23 — Acesso desktop](https://jam.dev/c/466be253-ad9a-4856-b567-fb17e1fdd479) |
| [CT-RF121](CT-RF121_Cadastro_Modelo_Ficha_Erro_500.md) | Cadastrar um modelo de ficha com nome e personal | Reprovado nas evidências | [BUG-045](../Relatorio-de-Bugs.md#bug-045), em triagem | [Jam — PED-24 — Cadastro de modelo de ficha](https://jam.dev/c/04e2cae2-f3f2-43ff-8361-b3b9d9f50d35) |

CT-RF116–CT-RF121 amplia a cobertura de Configurações e Modelos de Ficha com gravações de 16/11/2026 entre 22:03:53 e 22:18:52 BRT. A revisão é documental.

## Inclusão de 17/11/2026 — Inteligência e Configurações (CT-RF122–CT-RF127)

| Caso | Funcionalidade | Resultado | Defeito | Jam |
| --- | --- | --- | --- | --- |
| [CT-RF122](CT-RF122_Resultados_IA_Filtro_90_Dias.md) | Filtrar Resultados da Inteligência pelos últimos 90 dias | Aprovado conforme a gravação | — | [Jam — PED-12 — Últimos 90 dias](https://jam.dev/c/1728cfc2-1d36-4ea4-ab68-68a84458c359) |
| [CT-RF123](CT-RF123_Central_Resultados_IA_Execucao_Evasao.md) | Conferir a execução de Risco de Evasão na Central e em Resultados IA | Aprovado conforme a gravação | — | [Jam — PED-14 — Execução de Risco de Evasão](https://jam.dev/c/efe26a44-458a-4802-bd48-8e23c5ac5fd9) |
| [CT-RF124](CT-RF124_Configuracoes_Abas_Biometria_Senha.md) | Navegar pelas abas de Configurações com a senha da biometria protegida | Reprovado nas evidências | [BUG-046](../Relatorio-de-Bugs.md#bug-046), em triagem | Jam — PED-15 (gravação restrita por conter dados de integração) |
| [CT-RF125](CT-RF125_Configuracoes_Salvar_Dias_Ausencia_Valido.md) | Salvar um valor válido de dias de ausência | Aprovado conforme a gravação | — | [Jam — PED-16 — Salvar dias de ausência](https://jam.dev/c/12d6bba7-a67e-4882-86a5-4dd08d194af2) |
| [CT-RF126](CT-RF126_Configuracoes_Dias_Ausencia_Negativo.md) | Bloquear número negativo no campo de dias de ausência | Reprovado nas evidências | [BUG-047](../Relatorio-de-Bugs.md#bug-047), em triagem | [Jam — PED-17 — Dias de ausência negativos](https://jam.dev/c/d5786f67-6e5f-44f5-bbba-fbd763a88740) |
| [CT-RF127](CT-RF127_Configuracoes_Dias_Ausencia_Texto.md) | Validar letras no campo de dias de ausência | A validar — regra ou contexto pendente | — | [Jam — PED-18 — Dias de ausência com texto](https://jam.dev/c/c578ed7a-c11c-4cef-8a6c-84d0244f21a5) |

CT-RF122–CT-RF127 cobre Inteligência e Configurações com gravações de 16/11/2026 entre 21:50:51 e 22:02:16 BRT. A revisão é documental.

## Inclusão de 17/11/2026 — Inteligência e Automação (CT-RF128–CT-RF133)

| Caso | Funcionalidade | Resultado | Defeito | Jam |
| --- | --- | --- | --- | --- |
| [CT-RF128](CT-RF128_Central_Configuracao_Risco_Evasao_Cancelar.md) | Abrir e fechar a configuração de Risco de Evasão | Aprovado conforme a gravação | — | [Jam — PED-06 — Configuração de Risco de Evasão](https://jam.dev/c/d49b8ffc-a6e2-4e37-a618-c280b5e807db) |
| [CT-RF129](CT-RF129_Central_Aniversariantes_Previa_Risco.md) | Abrir Aniversariantes e conferir a prévia da automação | Reprovado nas evidências | [BUG-048](../Relatorio-de-Bugs.md#bug-048), em triagem | [Jam — PED-07 — Configuração de Aniversariantes](https://jam.dev/c/c66d4d01-aee2-4037-a8fd-858da21a0a14) |
| [CT-RF130](CT-RF130_Central_Recursos_Em_Desenvolvimento.md) | Verificar recursos marcados como Em desenvolvimento | Aprovado conforme a gravação | — | [Jam — PED-08 — Recursos em desenvolvimento](https://jam.dev/c/0a7ae8fb-980d-4df2-8ef8-de78d6b11b8f) |
| [CT-RF131](CT-RF131_Resultados_IA_Filtro_Hoje.md) | Filtrar Resultados da Inteligência por Hoje | Aprovado conforme a gravação | — | [Jam — PED-09 — Hoje](https://jam.dev/c/a83c4c74-0b8e-4242-9612-0202c9063d56) |
| [CT-RF132](CT-RF132_Resultados_IA_Filtro_7_Dias.md) | Filtrar Resultados da Inteligência pelos últimos 7 dias | Aprovado conforme a gravação | — | [Jam — PED-10 — Últimos 7 dias](https://jam.dev/c/cbf45b87-b7b6-4314-a359-c5e706aa755e) |
| [CT-RF133](CT-RF133_Resultados_IA_Filtro_30_Dias.md) | Filtrar Resultados da Inteligência pelos últimos 30 dias | Aprovado conforme a gravação | — | [Jam — PED-11 — Últimos 30 dias](https://jam.dev/c/2756d5c1-a823-482b-bf8d-878357b8b087) |

CT-RF128–CT-RF133 cobre Inteligência e Automação com gravações de 16/11/2026 entre 21:40:31 e 21:49:48 BRT. A revisão é documental.

## Inclusão de 17/11/2026 — Inteligência e Automação / Central de Automações (CT-RF134–CT-RF138)

| Caso | Funcionalidade | Resultado | Defeito | Jam |
| --- | --- | --- | --- | --- |
| [CT-RF134](CT-RF134_Central_Automacoes_Atualizar.md) | Atualizar a Central de Automações | Aprovado conforme a gravação | — | [Jam — PED-01 — Atualizar Central de Automações](https://jam.dev/c/efe35b08-8733-434c-a6fa-32c45e248ae1) |
| [CT-RF135](CT-RF135_Central_Desativar_Risco_Evasao_Contador.md) | Desativar Risco de Evasão e conferir a persistência e o contador | Reprovado nas evidências | [BUG-049](../Relatorio-de-Bugs.md#bug-049), em triagem | [Jam — PED-02 — Desativar Risco de Evasão](https://jam.dev/c/b63ec55f-f8b6-41aa-af4c-d4cdd4515de8) |
| [CT-RF136](CT-RF136_Central_Ativar_Aniversariantes_Contador.md) | Ativar Aniversariantes e conferir a persistência e o contador | Reprovado nas evidências | [BUG-049](../Relatorio-de-Bugs.md#bug-049), em triagem | [Jam — PED-03 — Ativar Aniversariantes](https://jam.dev/c/60c724da-6760-4238-91f5-2ddad8f42bb3) |
| [CT-RF137](CT-RF137_Central_Risco_Evasao_Executar_Agora.md) | Executar Risco de Evasão manualmente pela Central | Aprovado conforme a gravação | — | Jam — PED-04 — Executar Risco de Evasão (gravação restrita por conter dados individuais da avaliação de risco) |
| [CT-RF138](CT-RF138_Central_Abrir_Resultados_Risco_Evasao.md) | Abrir os resultados de Risco de Evasão pela Central | Aprovado conforme a gravação | — | Jam — PED-05 — Ver resultados de Risco de Evasão (gravação restrita por conter dados individuais da avaliação de risco) |

CT-RF134–CT-RF138 cobrem a Central de Automações com gravações de 16/11/2026 entre 21:25:26 e 21:38:29 BRT. A revisão é documental.

## Inclusão de 17/11/2026 — Configurações / Integrações / WhatsApp (CT-RF139–CT-RF144)

| Caso | Funcionalidade | Resultado | Defeito | Jam |
| --- | --- | --- | --- | --- |
| [CT-RF139](CT-RF139_Integracoes_WhatsApp_Mascarar_API_Key.md) | Mascarar a API Key no formulário de WhatsApp | Aprovado conforme a gravação | — | Jam 1 — Mascaramento da API Key (gravação restrita por conter dados de integração) |
| [CT-RF140](CT-RF140_Integracoes_WhatsApp_Validar_URL_API.md) | Validar uma URL da API sem formato de endereço | A validar — regra ou contexto pendente | — | Jam 2 — Validação da URL da API (gravação restrita por conter dados de integração) |
| [CT-RF141](CT-RF141_Integracoes_WhatsApp_Instancia_Obrigatoria.md) | Bloquear o salvamento com Nome da Instância vazio | Aprovado conforme a gravação | — | Jam 3 — Obrigatoriedade do Nome da Instância (gravação restrita por conter dados de integração) |
| [CT-RF142](CT-RF142_Integracoes_WhatsApp_Persistir_Ativo.md) | Persistir a opção Ativo da integração de WhatsApp | Aprovado conforme a gravação | — | Jam 4 — Persistência da opção Ativo (gravação restrita por conter dados de integração) |
| [CT-RF143](CT-RF143_Integracoes_WhatsApp_Conectar_Evolution.md) | Tratar falha ao conectar WhatsApp via Evolution API | Reprovado nas evidências | [BUG-050](../Relatorio-de-Bugs.md#bug-050), em triagem | Jam 5 — Tentativas de conexão pela Evolution API (gravação restrita por conter dados de integração) |
| [CT-RF144](CT-RF144_Integracoes_WhatsApp_Atualizar_Status.md) | Consultar novamente o status da integração de WhatsApp | Aprovado conforme a gravação | [BUG-050](../Relatorio-de-Bugs.md#bug-050) na tentativa posterior de conexão | Jam 6 — Atualização manual de status (gravação restrita por conter dados de integração) |

CT-RF139–CT-RF144 cobrem a integração do WhatsApp com gravações de 16/11/2026 entre 23:37:22 e 23:45:52 BRT. A revisão é documental.

## Inclusão de 17/11/2026 — Configurações (CT-RF145–CT-RF150)

| Caso | Funcionalidade | Resultado | Defeito | Jam |
| --- | --- | --- | --- | --- |
| [CT-RF145](CT-RF145_Configuracoes_Aniversario_Salvar_WhatsApp_SMS.md) | Salvar mensagens de aniversário para WhatsApp e SMS | Aprovado conforme a gravação | — | Jam 1 — Mensagens de aniversário por WhatsApp e SMS (gravação restrita por conter dados de integração) |
| [CT-RF146](CT-RF146_Configuracoes_Pagamento_Online_Desativar.md) | Persistir a desativação do Pagamento Online | Aprovado conforme a gravação | — | Jam 2 — Desativação do Pagamento Online (gravação restrita por conter dados de integração) |
| [CT-RF147](CT-RF147_Configuracoes_Design_Salvar_Cor_Principal.md) | Salvar uma Cor Principal hexadecimal válida | Aprovado conforme a gravação | — | Jam 3 — Persistência da Cor Principal (gravação restrita por conter dados de integração) |
| [CT-RF148](CT-RF148_Configuracoes_Design_Validar_Cor_Secundaria.md) | Rejeitar código hexadecimal inválido na Cor Secundária | Reprovado nas evidências | [BUG-051](../Relatorio-de-Bugs.md#bug-051), em triagem | Jam 4 — Validação da Cor Secundária (gravação restrita por conter dados de integração) |
| [CT-RF149](CT-RF149_Configuracoes_Design_Logo_Limite_Tamanho.md) | Informar o limite de tamanho ao rejeitar o logo | Reprovado nas evidências | [BUG-052](../Relatorio-de-Bugs.md#bug-052), em triagem | Jam 5 — Rejeição de logo pelo limite de tamanho (gravação restrita por conter dados de integração) |
| [CT-RF150](CT-RF150_Integracoes_WhatsApp_Atualizar_Status_Aguardando_QR.md) | Atualizar a verificação do WhatsApp enquanto aguarda QR Code | Aprovado conforme a gravação | — | Jam 6 — Atualização de status enquanto aguarda QR Code (gravação restrita por conter dados de integração) |

CT-RF145–CT-RF150 cobrem funcionalidades de Configurações com gravações de 16/11/2026 entre 23:21:59 e 23:36:13 BRT. A revisão é documental.

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md) · [Plano](../Plano%20de%20testes.md) · [Evidências](../Evidencias/README.md)
