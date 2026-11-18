# 🧪 Testes Manuais — SIFIT

Repositório de documentação de QA manual do **SIFIT**, sistema de gestão de academias. Reúne requisitos, plano, cenários BDD, resultados, defeitos e evidências com links do Jam.

**Atualização documental:** 18/11/2026. Integrados CT-RF157–CT-RF165 e RF157–RF165 para Aplicativo e Configurações / Biometria. A revisão utiliza gravações e eventos do Jam.

## 📊 Situação consolidada

| Cenários documentados | Aprovados | Reprovados | A validar | Defeitos registrados | Casos com reteste corretivo pendente |
| :---: | :---: | :---: | :---: | :---: | :---: |
| 161 | 81 | 59 | 21 | 54 (10 abertos + 44 em triagem) | 59 |

As classificações se baseiam nas fontes indicadas em cada cenário. CT-RF09/10 compartilham BUG-005 e CT-RF53–CT-RF56 compartilham BUG-023. CT-RF135 e CT-RF136 compartilham o BUG-049. As 59 reprovações correspondem a 54 defeitos registrados. BUG-011–BUG-054 aguardam triagem.

## 📚 Documentos do projeto

| Documento | Conteúdo |
| --- | --- |
| [Análise de requisitos](SIFIT/Analise%20de%20requisitos.md) | RF01–RF35, RF38–RF62 e RF65–RF165, critérios de aceitação, dúvidas de regra e rastreabilidade. |
| [Plano de testes](SIFIT/Plano%20de%20testes.md) | Escopo, ambientes, preparação, critérios, regressão e retestes. |
| [Índice dos cenários](SIFIT/Cenario_Teste/README.md) | 161 cenários com pré-condições, BDD, passos, esperado, obtido e encaminhamento. |
| [Relatório de bugs](SIFIT/Relatorio-de-Bugs.md) | BUG-001–BUG-054: reprodução, impacto, evidências, severidade/prioridade propostas e reteste. |
| [Relatório dos testes](SIFIT/Relatorio%20dos%20testes.md) | Resultados consolidados, cobertura, limites e pendências. |
| [Índice das evidências](SIFIT/Evidencias/README.md) | Jam por cenário e arquivos locais dos novos casos. |

## 🧱 Estrutura

```text
extensao-qa/
├── README.md
└── SIFIT/
    ├── Analise de requisitos.md
    ├── Plano de testes.md
    ├── Relatorio-de-Bugs.md
    ├── Relatorio dos testes.md
    ├── Cenario_Teste/
    │   ├── README.md
    │   ├── CT-RF01_Esqueci-senha.md
    │   ├── ... CT-RF02 a CT-RF35
    │   ├── CT-RF38_Cadastro_Categoria_Codigo_Automatico.md
    │   ├── CT-RF39 a CT-RF41 (SifitBox – Turmas)
    │   ├── CT-RF42 a CT-RF56 (Pagar.me, Despesas Fixas e Relatórios)
    │   ├── CT-RF57 a CT-RF59 e CT-RF65 a CT-RF73 (Grupos, Anamnese e Colaboradores)
    │   ├── CT-RF74 a CT-RF84 (Prospecção e Bandeiras de Cartão)
    │   ├── CT-RF85 a CT-RF103 (Prospecção, Contas a Pagar, Modelos de Contrato e Planos)
    │   └── CT-RF104 a CT-RF108 (Tipos de Pagamento)
    └── Evidencias/
        ├── README.md
        ├── CT-RF23_Exclusao_Exercicio/ ... CT-RF25_Envio_Exercicio_Imagem/
        ├── CT-RF35_Cadastro_Objetivo_Treino/
        ├── CT-RF38_Cadastro_Categoria_Codigo_Automatico/
        ├── CT-RF39 a CT-RF41 (uma pasta por caso)
        ├── CT-RF42 a CT-RF56 (uma pasta por caso, com os PDFs de CT-RF50 a CT-RF56)
        ├── CT-RF74 a CT-RF84 (uma pasta por caso, com RESUMO.txt e README.md)
        ├── CT-RF85 a CT-RF103 (uma pasta por caso)
        └── CT-RF104 a CT-RF108 (uma pasta por caso)
```

## 📋 Cenários e resultados

| Caso | Funcionalidade | Resultado nas evidências | Defeito | Fonte |
| --- | --- | --- | --- | --- |
| [CT-RF01](SIFIT/Cenario_Teste/CT-RF01_Esqueci-senha.md) | Início da recuperação de senha | Reprovado conforme as evidências | [BUG-001](SIFIT/Relatorio-de-Bugs.md#bug-001--link-esqueci-minha-senha-não-executa-nenhuma-ação) | [Jam](https://jam.dev/c/0273b203-b999-493d-9919-2d143bc13301) |
| [CT-RF02_ERRO](SIFIT/Cenario_Teste/CT-RF02_ERRO.md) | Dados, campos e layout do perfil | Reprovado conforme as evidências | [BUG-002](SIFIT/Relatorio-de-Bugs.md#bug-002--perfil-com-dados-fictícios-campos-ausentes-e-layout-desconfigurado) | [Jam](https://jam.dev/c/c61241d5-bff5-4a0a-9684-991318f9b51c) |
| [CT-RF03](SIFIT/Cenario_Teste/CT-RF03_FILTRO_TelaClientes.md) | Filtros combinados de Clientes | Reprovado conforme o relato | [BUG-003](SIFIT/Relatorio-de-Bugs.md#bug-003--filtros-combinados-da-página-clientes-não-restringem-a-listagem) | [Jam](https://jam.dev/c/657627ec-e7e2-455d-a505-9b2a26f44bf1) |
| [CT-RF04_loginComSucesso](SIFIT/Cenario_Teste/CT-RF04_loginComSucesso.md) | Login com credenciais válidas | Aprovado conforme a gravação | — | [Jam](https://jam.dev/c/5e4a28be-4e80-43d3-9587-1b113723cc38) |
| [CT-RF05](SIFIT/Cenario_Teste/CT-RF05_Login_SenhaIncorreta.md) | Login com senha incorreta | Aprovado conforme a gravação | — | [Jam](https://jam.dev/c/75f16436-7201-4de0-b191-1c4d0d63bfe8) |
| [CT-RF06](SIFIT/Cenario_Teste/CT-RF06_Login_UsuarioInexistente.md) | Login com usuário inexistente | Aprovado conforme a gravação | — | [Jam](https://jam.dev/c/b184e875-2cb1-4a01-b4dd-bc85b3741ff6) |
| [CT-RF07](SIFIT/Cenario_Teste/CT-RF07_Exportacao_Financeiro.md) | Exportação financeira sem retorno visível | Reprovado nas evidências | [BUG-004](SIFIT/Relatorio-de-Bugs.md#bug-004) | [Jam](https://jam.dev/c/1084cb18-cb3d-4b85-9c2f-ee431b59a06b) |
| [CT-RF08](SIFIT/Cenario_Teste/CT-RF08_Calculo_Cobranca.md) | Total atualizado da cobrança e valor da mensagem | A validar — regra ou contexto pendente | — | [Jam](https://jam.dev/c/79b712ae-d9e0-4600-862f-fd3a278285ff) |
| [CT-RF09](SIFIT/Cenario_Teste/CT-RF09_Contagem_Mensalidades.md) | Contagem de mensalidades diverge da lista | Reprovado nas evidências | [BUG-005](SIFIT/Relatorio-de-Bugs.md#bug-005) | [Jam](https://jam.dev/c/1874d0b3-5c7c-4f28-85be-91750e20cbe1) |
| [CT-RF10](SIFIT/Cenario_Teste/CT-RF10_Filtro_Mensalidades.md) | Filtro Até 7 dias conta uma mensalidade e mostra lista vazia | Reprovado nas evidências | [BUG-005](SIFIT/Relatorio-de-Bugs.md#bug-005) | [Jam](https://jam.dev/c/3f78cf16-2c3b-48bc-8622-23b829debbec) |
| [CT-RF11](SIFIT/Cenario_Teste/CT-RF11_Metricas_Financeiro.md) | Escopo das métricas financeiras durante a filtragem | A validar — regra ou contexto pendente | — | [Jam](https://jam.dev/c/4491c9e7-7e00-4063-91ce-8683e316df06) |
| [CT-RF12](SIFIT/Cenario_Teste/CT-RF12_Periodo_Dashboard.md) | Período invertido e atualização de indicadores pouco clara | Reprovado nas evidências | [BUG-006](SIFIT/Relatorio-de-Bugs.md#bug-006) | [Jam](https://jam.dev/c/93165ba3-3bfe-4dd5-9379-ab8db2d686ba) |
| [CT-RF13](SIFIT/Cenario_Teste/CT-RF13_Codigos_Personais.md) | Códigos não sequenciais na lista de personais | A validar — regra ou contexto pendente | — | [Jam](https://jam.dev/c/69330ca9-ef19-4ece-918f-31a460628016) |
| [CT-RF14](SIFIT/Cenario_Teste/CT-RF14_Contraste_TemaEscuro.md) | Baixa legibilidade no tema escuro de Box – Turmas | Reprovado nas evidências | [BUG-007](SIFIT/Relatorio-de-Bugs.md#bug-007) | [Jam](https://jam.dev/c/6889db07-bed1-472b-8ec2-00402919cd65) |
| [CT-RF15](SIFIT/Cenario_Teste/CT-RF15_Edicao_Modalidade.md) | Edição de modalidade sem ação de salvar visível | Reprovado nas evidências | [BUG-008](SIFIT/Relatorio-de-Bugs.md#bug-008) | [Jam](https://jam.dev/c/951efaf8-bf32-44b0-b640-a2935a6b554a) |
| [CT-RF16](SIFIT/Cenario_Teste/CT-RF16_Exclusao_Modalidade.md) | Ação de lixeira inativa modalidades e mantém registros na lista | A validar — regra ou contexto pendente | — | [Jam](https://jam.dev/c/0f55f76a-cd31-4cee-93da-23c13b1ba637) |
| [CT-RF17](SIFIT/Cenario_Teste/CT-RF17_Filtros_Categorias.md) | Filtros de categorias por código e nome | Aprovado conforme a gravação | — | [Jam](https://jam.dev/c/5e75e423-9c7e-43d7-aade-9b1a32c5e559) |
| [CT-RF18](SIFIT/Cenario_Teste/CT-RF18_Atualizacao_Categoria.md) | Atualização de categoria | Aprovado conforme a gravação | — | [Jam](https://jam.dev/c/67664a98-2a4a-4134-91a9-7ca9b8aa9dbd) |
| [CT-RF19](SIFIT/Cenario_Teste/CT-RF19_Exclusao_Categoria.md) | Exclusão de categoria retorna erro HTTP 500 | Reprovado nas evidências | [BUG-009](SIFIT/Relatorio-de-Bugs.md#bug-009) | [Jam](https://jam.dev/c/c5c78b3b-2865-4226-836f-bcb0a8fc612f) |
| [CT-RF20](SIFIT/Cenario_Teste/CT-RF20_Criacao_Categoria.md) | Criação de categoria | Aprovado conforme a gravação | — | [Jam](https://jam.dev/c/b48ab94e-517d-48d6-8e46-70b18c033b8b) |
| [CT-RF21](SIFIT/Cenario_Teste/CT-RF21_Cadastro_Avaliacao.md) | Cadastro de avaliação retorna HTTP 500 | Reprovado nas evidências | [BUG-010](SIFIT/Relatorio-de-Bugs.md#bug-010) | [Jam](https://jam.dev/c/2e5eca1f-7cd2-4ee3-854b-02ef4635955a) |
| [CT-RF22](SIFIT/Cenario_Teste/CT-RF22_Digitacao_Codigo_Exercicio.md) | Permitir informar o código do exercício conforme a regra | Reprovado conforme o relato; reprodução independente pendente. | [BUG-011](SIFIT/Relatorio-de-Bugs.md#bug-011), em triagem | [Jam](https://jam.dev/c/2696db03-0a18-4c39-a75d-4987a43c04f0) |
| [CT-RF23](SIFIT/Cenario_Teste/CT-RF23_Exclusao_Exercicio.md) | Exclusão de exercício | Aprovado no trecho consultado. | Sem defeito confirmado | [Jam](https://jam.dev/c/32adfca3-489f-4a4b-a08d-933c1d1a3c32) |
| [CT-RF24](SIFIT/Cenario_Teste/CT-RF24_Edicao_Exercicio.md) | Edição de exercício aumenta o total e mantém duas entradas | Reprovado no trecho consultado; confirmar operação e identidade dos registros na reprodução. | [BUG-012](SIFIT/Relatorio-de-Bugs.md#bug-012), em triagem | [Jam](https://jam.dev/c/073f70d6-4052-4e0f-a4bb-e9f37305d618) |
| [CT-RF25](SIFIT/Cenario_Teste/CT-RF25_Envio_Exercicio_Imagem.md) | Envio de exercício com imagem | A validar — criação visível; persistência e associação da imagem não confirmadas. | Sem defeito confirmado | [Jam](https://jam.dev/c/25c37a9b-e9bd-4e0c-adf1-4da528ae1d58) |
| [CT-RF26](SIFIT/Cenario_Teste/CT-RF26_Exercicio_Campos_Vazios.md) | Envio de exercício com campos obrigatórios vazios | Reprovado — sem feedback de validação visível. | [BUG-013](SIFIT/Relatorio-de-Bugs.md#bug-013), em triagem | [Jam](https://jam.dev/c/bc07ca5f-d3a9-45f6-84cb-12c0b562a211) |
| [CT-RF27](SIFIT/Cenario_Teste/CT-RF27_Video_Campo_Imagem.md) | Vídeo selecionado no campo de imagem | Reprovado — arquivo rejeitado sem feedback visível. | [BUG-014](SIFIT/Relatorio-de-Bugs.md#bug-014), em triagem | [Jam](https://jam.dev/c/00740108-9a7d-4151-8723-171c89635567) |
| [CT-RF28](SIFIT/Cenario_Teste/CT-RF28_Imagem_Campo_Video.md) | Imagem selecionada no campo de vídeo | Reprovado — arquivo rejeitado sem feedback visível. | [BUG-015](SIFIT/Relatorio-de-Bugs.md#bug-015), em triagem | [Jam](https://jam.dev/c/be9437a4-4fe9-4756-a2af-6777d3f43e25) |
| [CT-RF29](SIFIT/Cenario_Teste/CT-RF29_Exclusao_GrupoMuscular.md) | Exclusão de grupo muscular retorna HTTP 500 | Reprovado nas evidências | [BUG-016](SIFIT/Relatorio-de-Bugs.md#bug-016), em triagem | [Jam](https://jam.dev/c/98008390-0040-475e-ba7b-7f1e72cc0b2e) |
| [CT-RF30](SIFIT/Cenario_Teste/CT-RF30_Imagens_GruposMusculares.md) | Imagens dos grupos musculares retornam HTTP 422 | Reprovado nas evidências | [BUG-017](SIFIT/Relatorio-de-Bugs.md#bug-017), em triagem | [Jam](https://jam.dev/c/98008390-0040-475e-ba7b-7f1e72cc0b2e) |
| [CT-RF31](SIFIT/Cenario_Teste/CT-RF31_Cadastro_GrupoMuscular.md) | Cadastro de grupo muscular | Aprovado conforme a gravação | — | [Jam](https://jam.dev/c/98008390-0040-475e-ba7b-7f1e72cc0b2e) |
| [CT-RF32](SIFIT/Cenario_Teste/CT-RF32_Edicao_TipoMembro.md) | Edição do tipo de membro | Aprovado conforme a gravação | — | [Jam](https://jam.dev/c/98008390-0040-475e-ba7b-7f1e72cc0b2e) |
| [CT-RF33](SIFIT/Cenario_Teste/CT-RF33_Filtros_GruposMusculares.md) | Filtros de grupos musculares por código e tipo | Aprovado conforme a gravação | — | [Jam](https://jam.dev/c/98008390-0040-475e-ba7b-7f1e72cc0b2e) |
| [CT-RF35](SIFIT/Cenario_Teste/CT-RF35_Cadastro_Objetivo_Treino.md) | Cadastro de objetivo de treino retorna HTTP 500 | Reprovado nas evidências | [BUG-019](SIFIT/Relatorio-de-Bugs.md#bug-019), em triagem | [Jam](https://jam.dev/c/1d474477-2411-4a81-b85c-74207402b783) |
| [CT-RF38](SIFIT/Cenario_Teste/CT-RF38_Cadastro_Categoria_Codigo_Automatico.md) | Cadastro de categoria com código automático e consulta pelo código | Aprovado conforme a gravação | — | [Jam](https://jam.dev/c/be1dbd05-217d-44c3-8a3d-240b7f6344e1) |
| [CT-RF39](SIFIT/Cenario_Teste/CT-RF39_Cadastro_Modalidade.md) | Cadastro de modalidade em SifitBox – Turmas | Aprovado conforme a gravação | — | [Jam](https://jam.dev/c/ee9a133b-d6b1-442d-b4b0-dd87595b7e70) |
| [CT-RF40](SIFIT/Cenario_Teste/CT-RF40_Exclusao_Turmas_Modalidades.md) | Exclusão de turmas e modalidades pela lixeira | A validar — regra ou contexto pendente | — | [Jam](https://jam.dev/c/ee9a133b-d6b1-442d-b4b0-dd87595b7e70) |
| [CT-RF41](SIFIT/Cenario_Teste/CT-RF41_Cadastro_Turma_Sem_Modalidade.md) | Cadastro de turma sem modalidade, sem retorno visível | Reprovado nas evidências | [BUG-020](SIFIT/Relatorio-de-Bugs.md#bug-020), em triagem | [Jam](https://jam.dev/c/ee9a133b-d6b1-442d-b4b0-dd87595b7e70) |
| [CT-RF42](SIFIT/Cenario_Teste/CT-RF42_Solicitacao_Saque_PagarMe.md) | Solicitação de saque no painel Pagar.me | A validar — regra ou contexto pendente | — | [Jam](https://jam.dev/c/e6e551ef-9196-4c79-b6a2-89747b1e8b33) |
| [CT-RF43](SIFIT/Cenario_Teste/CT-RF43_Criacao_Cobranca_PagarMe.md) | Criação de cobrança no painel Pagar.me | Aprovado conforme a gravação | — | [Jam](https://jam.dev/c/e6e551ef-9196-4c79-b6a2-89747b1e8b33) |
| [CT-RF44](SIFIT/Cenario_Teste/CT-RF44_Configuracoes_Home_Salvamento.md) | Alteração e salvamento das Configurações (Home) | A validar — regra ou contexto pendente | — | [Jam](https://jam.dev/c/e6e551ef-9196-4c79-b6a2-89747b1e8b33) |
| [CT-RF45](SIFIT/Cenario_Teste/CT-RF45_Painel_PagarMe_Periodo.md) | Painel Pagar.me mantém Recebimentos e gráfico ao trocar o período | Reprovado nas evidências | [BUG-021](SIFIT/Relatorio-de-Bugs.md#bug-021), em triagem | [Jam](https://jam.dev/c/e6e551ef-9196-4c79-b6a2-89747b1e8b33) |
| [CT-RF46](SIFIT/Cenario_Teste/CT-RF46_Filtros_Despesas_Fixas.md) | Filtros da tela Despesas Fixas por código e por nome | Aprovado conforme a gravação | — | [Jam](https://jam.dev/c/a4bac99d-e436-4792-831e-8c3a875272bb) |
| [CT-RF47](SIFIT/Cenario_Teste/CT-RF47_Cadastro_Despesa_Fixa.md) | Cadastro de despesa fixa com duas requisições de criação | A validar — regra ou contexto pendente | — | [Jam](https://jam.dev/c/a4bac99d-e436-4792-831e-8c3a875272bb) |
| [CT-RF48](SIFIT/Cenario_Teste/CT-RF48_Exclusao_Despesa_Fixa.md) | Exclusão de despesa fixa com confirmação | Aprovado conforme a gravação | — | [Jam](https://jam.dev/c/a4bac99d-e436-4792-831e-8c3a875272bb) |
| [CT-RF49](SIFIT/Cenario_Teste/CT-RF49_Edicao_Despesa_Fixa.md) | Edição de despesa fixa | Aprovado conforme a gravação | — | [Jam](https://jam.dev/c/a4bac99d-e436-4792-831e-8c3a875272bb) |
| [CT-RF50](SIFIT/Cenario_Teste/CT-RF50_Relatorio_Matriculas.md) | Relatório de Matrículas em PDF | Aprovado conforme a gravação | — | [Jam](https://jam.dev/c/3b4777a4-e1b0-4038-9b06-26c73669d7d1) |
| [CT-RF51](SIFIT/Cenario_Teste/CT-RF51_Relatorio_Contas_Receber.md) | Relatório de Contas a Receber sem Valor a Receber | Reprovado nas evidências | [BUG-022](SIFIT/Relatorio-de-Bugs.md#bug-022), em triagem | [Jam](https://jam.dev/c/3b4777a4-e1b0-4038-9b06-26c73669d7d1) |
| [CT-RF52](SIFIT/Cenario_Teste/CT-RF52_Relatorio_Contas_Pagar_Pagas.md) | Relatório de Contas a Pagar (Pagas) sem registros | A validar — regra ou contexto pendente | — | [Jam](https://jam.dev/c/3b4777a4-e1b0-4038-9b06-26c73669d7d1) |
| [CT-RF53](SIFIT/Cenario_Teste/CT-RF53_Relatorio_Avaliacoes_Vazio.md) | Relatório de Avaliações gera arquivo vazio | Reprovado nas evidências | [BUG-023](SIFIT/Relatorio-de-Bugs.md#bug-023), em triagem | [Jam](https://jam.dev/c/3b4777a4-e1b0-4038-9b06-26c73669d7d1) |
| [CT-RF54](SIFIT/Cenario_Teste/CT-RF54_Relatorio_Clientes_Vazio.md) | Relatório de Clientes gera arquivo vazio | Reprovado nas evidências | [BUG-023](SIFIT/Relatorio-de-Bugs.md#bug-023), em triagem | [Jam](https://jam.dev/c/3b4777a4-e1b0-4038-9b06-26c73669d7d1) |
| [CT-RF55](SIFIT/Cenario_Teste/CT-RF55_Relatorio_Colaboradores_Vazio.md) | Relatório de Colaboradores gera arquivo vazio | Reprovado nas evidências | [BUG-023](SIFIT/Relatorio-de-Bugs.md#bug-023), em triagem | [Jam](https://jam.dev/c/3b4777a4-e1b0-4038-9b06-26c73669d7d1) |
| [CT-RF56](SIFIT/Cenario_Teste/CT-RF56_Relatorio_Caixas_Vazio.md) | Relatório de Caixas gera arquivo vazio | Reprovado nas evidências | [BUG-023](SIFIT/Relatorio-de-Bugs.md#bug-023), em triagem | [Jam](https://jam.dev/c/3b4777a4-e1b0-4038-9b06-26c73669d7d1) |
| [CT-RF85](SIFIT/Cenario_Teste/CT-RF85_Tema_Notificacoes_Prospeccao.md) | Alternância de tema e painel de notificações em Prospecção | Aprovado conforme a gravação | — | [Jam](https://jam.dev/c/308607ff-8abc-40af-8c7c-429ce506ed64) |
| [CT-RF86](SIFIT/Cenario_Teste/CT-RF86_Busca_Leads_Prospeccao.md) | Busca de leads por texto na tela Prospecção | Aprovado conforme a gravação | — | [Jam](https://jam.dev/c/308607ff-8abc-40af-8c7c-429ce506ed64) |
| [CT-RF87](SIFIT/Cenario_Teste/CT-RF87_Filtro_Estagio_Leads.md) | Filtro de leads por estágio e limpeza dos filtros | Aprovado conforme a gravação | — | [Jam](https://jam.dev/c/308607ff-8abc-40af-8c7c-429ce506ed64) |
| [CT-RF88](SIFIT/Cenario_Teste/CT-RF88_Cadastro_Lead_Prospeccao.md) | Cadastro de lead com duas requisições de criação | A validar — regra ou contexto pendente | — | [Jam](https://jam.dev/c/308607ff-8abc-40af-8c7c-429ce506ed64) |
| [CT-RF89](SIFIT/Cenario_Teste/CT-RF89_Telefone_Lead_Sem_Validacao.md) | Telefone do lead aceita 30 dígitos sem validação | Reprovado nas evidências | [BUG-038](SIFIT/Relatorio-de-Bugs.md#bug-038), em triagem | [Jam](https://jam.dev/c/308607ff-8abc-40af-8c7c-429ce506ed64) |
| [CT-RF90](SIFIT/Cenario_Teste/CT-RF90_Edicao_Lead_Prospeccao.md) | Visualização e edição de lead na tela Prospecção | Aprovado conforme a gravação | — | [Jam](https://jam.dev/c/308607ff-8abc-40af-8c7c-429ce506ed64) |
| [CT-RF91](SIFIT/Cenario_Teste/CT-RF91_Filtros_Contas_Pagar.md) | Filtros da tela Contas a Pagar por nome, data e status | A validar — regra ou contexto pendente | — | [Jam](https://jam.dev/c/5d0afaf4-5abd-4e85-923f-27448304a9ef) |
| [CT-RF92](SIFIT/Cenario_Teste/CT-RF92_Cadastro_Conta_Colaborador_Sem_Colaborador.md) | Conta a pagar a colaborador é cadastrada sem colaborador informado | Reprovado nas evidências | [BUG-039](SIFIT/Relatorio-de-Bugs.md#bug-039), em triagem | [Jam](https://jam.dev/c/5d0afaf4-5abd-4e85-923f-27448304a9ef) |
| [CT-RF93](SIFIT/Cenario_Teste/CT-RF93_Busca_Colaborador_Conta_Pagar.md) | Busca de colaborador no cadastro de conta a pagar | A validar — regra ou contexto pendente | — | [Jam](https://jam.dev/c/5d0afaf4-5abd-4e85-923f-27448304a9ef) |
| [CT-RF94](SIFIT/Cenario_Teste/CT-RF94_Visualizacao_Conta_Pagar.md) | Visualização dos dados de uma conta a pagar | Aprovado conforme a gravação | — | [Jam](https://jam.dev/c/5d0afaf4-5abd-4e85-923f-27448304a9ef) |
| [CT-RF95](SIFIT/Cenario_Teste/CT-RF95_Exclusao_Conta_Pagar.md) | Exclusão de conta a pagar com confirmação | Aprovado conforme a gravação | — | [Jam](https://jam.dev/c/5d0afaf4-5abd-4e85-923f-27448304a9ef) |
| [CT-RF96](SIFIT/Cenario_Teste/CT-RF96_Variaveis_Preview_Modelo_Contrato.md) | Variáveis e pré-visualização do texto do modelo de contrato | Aprovado conforme a gravação | — | [Jam](https://jam.dev/c/44dbbd39-6915-45d6-8dd1-5f30c1432ca0) |
| [CT-RF97](SIFIT/Cenario_Teste/CT-RF97_Cadastro_Modelo_Contrato.md) | Cadastro de modelo de contrato | Aprovado conforme a gravação | — | [Jam](https://jam.dev/c/44dbbd39-6915-45d6-8dd1-5f30c1432ca0) |
| [CT-RF98](SIFIT/Cenario_Teste/CT-RF98_Listagem_Modelos_Contrato_Vazia.md) | Listagem de modelos de contrato aparece vazia com 15 modelos retornados | Reprovado nas evidências | [BUG-040](SIFIT/Relatorio-de-Bugs.md#bug-040), em triagem | [Jam](https://jam.dev/c/44dbbd39-6915-45d6-8dd1-5f30c1432ca0) |
| [CT-RF99](SIFIT/Cenario_Teste/CT-RF99_Filtros_Planos.md) | Filtros da tela Planos por código e nome | Aprovado conforme a gravação | — | [Jam](https://jam.dev/c/233c5d21-e108-4a55-b6f6-8738cb3fc6a6) |
| [CT-RF100](SIFIT/Cenario_Teste/CT-RF100_Tema_Notificacoes_Planos.md) | Alternância de tema e painel de notificações em Planos | Aprovado conforme a gravação | — | [Jam](https://jam.dev/c/233c5d21-e108-4a55-b6f6-8738cb3fc6a6) |
| [CT-RF101](SIFIT/Cenario_Teste/CT-RF101_Cadastro_Plano.md) | Cadastro de plano pelo modal Novo Plano | Aprovado conforme a gravação | — | [Jam](https://jam.dev/c/233c5d21-e108-4a55-b6f6-8738cb3fc6a6) |
| [CT-RF102](SIFIT/Cenario_Teste/CT-RF102_Contador_Ativos_Planos.md) | Cartão Ativos de Planos aumenta ao cadastrar e editar planos inativos | Reprovado nas evidências | [BUG-041](SIFIT/Relatorio-de-Bugs.md#bug-041), em triagem | [Jam](https://jam.dev/c/233c5d21-e108-4a55-b6f6-8738cb3fc6a6) |
| [CT-RF103](SIFIT/Cenario_Teste/CT-RF103_Edicao_Plano.md) | Edição de plano pelo modal Editar Plano | Aprovado conforme a gravação | — | [Jam](https://jam.dev/c/233c5d21-e108-4a55-b6f6-8738cb3fc6a6) |
| [CT-RF104](SIFIT/Cenario_Teste/CT-RF104_Filtros_Tipos_Pagamento.md) | Filtros de busca da tela Tipos de Pagamento | A validar — regra ou contexto pendente | — | [Jam](https://jam.dev/c/e8734e3d-3f8e-458b-8c7d-e85eea882e50) |
| [CT-RF105](SIFIT/Cenario_Teste/CT-RF105_Cadastro_Tipo_Pagamento_Status.md) | Cadastro de tipo de pagamento com status Ativo não é refletido | Reprovado nas evidências | [BUG-042](SIFIT/Relatorio-de-Bugs.md#bug-042), em triagem | [Jam](https://jam.dev/c/e8734e3d-3f8e-458b-8c7d-e85eea882e50) |
| [CT-RF106](SIFIT/Cenario_Teste/CT-RF106_Edicao_Tipo_Pagamento.md) | Edição de tipo de pagamento pela lupa da listagem | Aprovado conforme a gravação | — | [Jam](https://jam.dev/c/e8734e3d-3f8e-458b-8c7d-e85eea882e50) |
| [CT-RF107](SIFIT/Cenario_Teste/CT-RF107_Exclusao_Tipo_Pagamento_Em_Uso.md) | Exclusão de tipo de pagamento em uso retorna HTTP 404 com erro SQL | Reprovado nas evidências | [BUG-043](SIFIT/Relatorio-de-Bugs.md#bug-043), em triagem | [Jam](https://jam.dev/c/e8734e3d-3f8e-458b-8c7d-e85eea882e50) |
| [CT-RF108](SIFIT/Cenario_Teste/CT-RF108_Tema_Notificacoes_Tipos_Pagamento.md) | Tema Claro/Escuro e notificações na tela Tipos de Pagamento | Aprovado conforme a gravação | — | [Jam](https://jam.dev/c/e8734e3d-3f8e-458b-8c7d-e85eea882e50) |
| [CT-RF109](SIFIT/Cenario_Teste/CT-RF109_Modelo_Ficha_Sem_Nome.md) | Bloquear cadastro de modelo de ficha sem nome | Aprovado conforme a gravação | — | [Jam — PED-25](https://jam.dev/c/fb5673c9-3cd1-46c4-88f4-d5fb32574a8e) |
| [CT-RF110](SIFIT/Cenario_Teste/CT-RF110_Cancelar_Cadastro_Modelo_Ficha.md) | Cancelar cadastro de modelo de ficha preenchido | Aprovado conforme a gravação | — | [Jam — PED-26](https://jam.dev/c/a2a39e11-04f4-40aa-a97e-75a57a5f1b0f) |
| [CT-RF111](SIFIT/Cenario_Teste/CT-RF111_Busca_Modelo_Ficha_Codigo_Inexistente.md) | Buscar modelo de ficha por código inexistente | A validar — regra ou contexto pendente | — | [Jam — PED-27](https://jam.dev/c/c1aecaa8-39c7-49b0-89af-9de47a68ba40) |
| [CT-RF112](SIFIT/Cenario_Teste/CT-RF112_Busca_Modelo_Ficha_Titulo_Inexistente.md) | Buscar modelo de ficha por título inexistente | A validar — regra ou contexto pendente | — | [Jam — PED-28](https://jam.dev/c/0c385452-2aeb-427f-8159-79549fe7371d) |
| [CT-RF113](SIFIT/Cenario_Teste/CT-RF113_Busca_Modelo_Ficha_Filtros_Combinados.md) | Buscar modelos de ficha com filtros combinados | A validar — regra ou contexto pendente | — | [Jam — PED-29](https://jam.dev/c/006f9722-e643-4b65-904a-25471a7b90ed) |
| [CT-RF114](SIFIT/Cenario_Teste/CT-RF114_Limpeza_Filtros_Modelos_Ficha.md) | Limpar os filtros de Modelos de Ficha | Aprovado conforme a gravação | — | [Jam — PED-30](https://jam.dev/c/297eec2b-7be4-498b-a0e6-e962ed93cc00) |
| [CT-RF115](SIFIT/Cenario_Teste/CT-RF115_Nova_Busca_Modelos_Ficha_Sem_Filtros.md) | Pesquisar novamente modelos de ficha sem filtros | A validar — regra ou contexto pendente | — | [Jam — PED-30](https://jam.dev/c/297eec2b-7be4-498b-a0e6-e962ed93cc00) |
| [CT-RF116](SIFIT/Cenario_Teste/CT-RF116_Configuracoes_Dias_Ausencia_Vazio.md) | Validar o salvamento com o campo de dias de ausência vazio | A validar — regra ou contexto pendente | — | [Jam — PED-20 — Dias de ausência vazio](https://jam.dev/c/4e96d4fa-65b5-459b-a795-854496e5753c) |
| [CT-RF117](SIFIT/Cenario_Teste/CT-RF117_Configuracoes_Cancelar_Alteracao.md) | Cancelar uma alteração nas Configurações sem salvar | Aprovado conforme a gravação | — | [Jam — PED-20 — Cancelar alteração](https://jam.dev/c/e8faa199-1177-4563-8b00-590606669a1d) |
| [CT-RF118](SIFIT/Cenario_Teste/CT-RF118_Configuracoes_Trabalha_Com_Turmas.md) | Alterar e persistir a opção Trabalha com turmas? | Aprovado conforme a gravação | — | [Jam — PED-21 — Trabalha com turmas](https://jam.dev/c/a51c33a5-537a-40fd-a55d-990b70ac0696) |
| [CT-RF119](SIFIT/Cenario_Teste/CT-RF119_Configuracoes_Academia_Marcada_Box.md) | Conferir a configuração Academia marcada como Box? | Aprovado conforme a gravação | — | [Jam — PED-22 — Academia marcada como Box](https://jam.dev/c/16dc862d-c3f9-4392-9037-526818e86cd6) |
| [CT-RF120](SIFIT/Cenario_Teste/CT-RF120_Configuracoes_Acesso_Desktop.md) | Conferir a configuração de acesso ao sistema desktop | Aprovado conforme a gravação | — | [Jam — PED-23 — Acesso desktop](https://jam.dev/c/466be253-ad9a-4856-b567-fb17e1fdd479) |
| [CT-RF121](SIFIT/Cenario_Teste/CT-RF121_Cadastro_Modelo_Ficha_Erro_500.md) | Cadastrar um modelo de ficha com nome e personal | Reprovado nas evidências | [BUG-045](SIFIT/Relatorio-de-Bugs.md#bug-045), em triagem | [Jam — PED-24 — Cadastro de modelo de ficha](https://jam.dev/c/04e2cae2-f3f2-43ff-8361-b3b9d9f50d35) |
| [CT-RF122](SIFIT/Cenario_Teste/CT-RF122_Resultados_IA_Filtro_90_Dias.md) | Filtrar Resultados da Inteligência pelos últimos 90 dias | Aprovado conforme a gravação | — | [Jam — PED-12 — Últimos 90 dias](https://jam.dev/c/1728cfc2-1d36-4ea4-ab68-68a84458c359) |
| [CT-RF123](SIFIT/Cenario_Teste/CT-RF123_Central_Resultados_IA_Execucao_Evasao.md) | Conferir a execução de Risco de Evasão na Central e em Resultados IA | Aprovado conforme a gravação | — | [Jam — PED-14 — Execução de Risco de Evasão](https://jam.dev/c/efe26a44-458a-4802-bd48-8e23c5ac5fd9) |
| [CT-RF124](SIFIT/Cenario_Teste/CT-RF124_Configuracoes_Abas_Biometria_Senha.md) | Navegar pelas abas de Configurações com a senha da biometria protegida | Reprovado nas evidências | [BUG-046](SIFIT/Relatorio-de-Bugs.md#bug-046), em triagem | Jam — PED-15 (gravação restrita por conter dados de integração) |
| [CT-RF125](SIFIT/Cenario_Teste/CT-RF125_Configuracoes_Salvar_Dias_Ausencia_Valido.md) | Salvar um valor válido de dias de ausência | Aprovado conforme a gravação | — | [Jam — PED-16 — Salvar dias de ausência](https://jam.dev/c/12d6bba7-a67e-4882-86a5-4dd08d194af2) |
| [CT-RF126](SIFIT/Cenario_Teste/CT-RF126_Configuracoes_Dias_Ausencia_Negativo.md) | Bloquear número negativo no campo de dias de ausência | Reprovado nas evidências | [BUG-047](SIFIT/Relatorio-de-Bugs.md#bug-047), em triagem | [Jam — PED-17 — Dias de ausência negativos](https://jam.dev/c/d5786f67-6e5f-44f5-bbba-fbd763a88740) |
| [CT-RF127](SIFIT/Cenario_Teste/CT-RF127_Configuracoes_Dias_Ausencia_Texto.md) | Validar letras no campo de dias de ausência | A validar — regra ou contexto pendente | — | [Jam — PED-18 — Dias de ausência com texto](https://jam.dev/c/c578ed7a-c11c-4cef-8a6c-84d0244f21a5) |
| [CT-RF128](SIFIT/Cenario_Teste/CT-RF128_Central_Configuracao_Risco_Evasao_Cancelar.md) | Abrir e fechar a configuração de Risco de Evasão | Aprovado conforme a gravação | — | [Jam — PED-06 — Configuração de Risco de Evasão](https://jam.dev/c/d49b8ffc-a6e2-4e37-a618-c280b5e807db) |
| [CT-RF129](SIFIT/Cenario_Teste/CT-RF129_Central_Aniversariantes_Previa_Risco.md) | Abrir Aniversariantes e conferir a prévia da automação | Reprovado nas evidências | [BUG-048](SIFIT/Relatorio-de-Bugs.md#bug-048), em triagem | [Jam — PED-07 — Configuração de Aniversariantes](https://jam.dev/c/c66d4d01-aee2-4037-a8fd-858da21a0a14) |
| [CT-RF130](SIFIT/Cenario_Teste/CT-RF130_Central_Recursos_Em_Desenvolvimento.md) | Verificar recursos marcados como Em desenvolvimento | Aprovado conforme a gravação | — | [Jam — PED-08 — Recursos em desenvolvimento](https://jam.dev/c/0a7ae8fb-980d-4df2-8ef8-de78d6b11b8f) |
| [CT-RF131](SIFIT/Cenario_Teste/CT-RF131_Resultados_IA_Filtro_Hoje.md) | Filtrar Resultados da Inteligência por Hoje | Aprovado conforme a gravação | — | [Jam — PED-09 — Hoje](https://jam.dev/c/a83c4c74-0b8e-4242-9612-0202c9063d56) |
| [CT-RF132](SIFIT/Cenario_Teste/CT-RF132_Resultados_IA_Filtro_7_Dias.md) | Filtrar Resultados da Inteligência pelos últimos 7 dias | Aprovado conforme a gravação | — | [Jam — PED-10 — Últimos 7 dias](https://jam.dev/c/cbf45b87-b7b6-4314-a359-c5e706aa755e) |
| [CT-RF133](SIFIT/Cenario_Teste/CT-RF133_Resultados_IA_Filtro_30_Dias.md) | Filtrar Resultados da Inteligência pelos últimos 30 dias | Aprovado conforme a gravação | — | [Jam — PED-11 — Últimos 30 dias](https://jam.dev/c/2756d5c1-a823-482b-bf8d-878357b8b087) |
| [CT-RF134](SIFIT/Cenario_Teste/CT-RF134_Central_Automacoes_Atualizar.md) | Atualizar a Central de Automações | Aprovado conforme a gravação | — | [Jam — PED-01 — Atualizar Central de Automações](https://jam.dev/c/efe35b08-8733-434c-a6fa-32c45e248ae1) |
| [CT-RF135](SIFIT/Cenario_Teste/CT-RF135_Central_Desativar_Risco_Evasao_Contador.md) | Desativar Risco de Evasão e conferir a persistência e o contador | Reprovado nas evidências | [BUG-049](SIFIT/Relatorio-de-Bugs.md#bug-049), em triagem | [Jam — PED-02 — Desativar Risco de Evasão](https://jam.dev/c/b63ec55f-f8b6-41aa-af4c-d4cdd4515de8) |
| [CT-RF136](SIFIT/Cenario_Teste/CT-RF136_Central_Ativar_Aniversariantes_Contador.md) | Ativar Aniversariantes e conferir a persistência e o contador | Reprovado nas evidências | [BUG-049](SIFIT/Relatorio-de-Bugs.md#bug-049), em triagem | [Jam — PED-03 — Ativar Aniversariantes](https://jam.dev/c/60c724da-6760-4238-91f5-2ddad8f42bb3) |
| [CT-RF137](SIFIT/Cenario_Teste/CT-RF137_Central_Risco_Evasao_Executar_Agora.md) | Executar Risco de Evasão manualmente pela Central | Aprovado conforme a gravação | — | Jam — PED-04 — Executar Risco de Evasão (gravação restrita por conter dados individuais da avaliação de risco) |
| [CT-RF138](SIFIT/Cenario_Teste/CT-RF138_Central_Abrir_Resultados_Risco_Evasao.md) | Abrir os resultados de Risco de Evasão pela Central | Aprovado conforme a gravação | — | Jam — PED-05 — Ver resultados de Risco de Evasão (gravação restrita por conter dados individuais da avaliação de risco) |
| [CT-RF139](SIFIT/Cenario_Teste/CT-RF139_Integracoes_WhatsApp_Mascarar_API_Key.md) | Mascarar a API Key no formulário de WhatsApp | Aprovado conforme a gravação | — | Jam 1 — Mascaramento da API Key (gravação restrita por conter dados de integração) |
| [CT-RF140](SIFIT/Cenario_Teste/CT-RF140_Integracoes_WhatsApp_Validar_URL_API.md) | Validar uma URL da API sem formato de endereço | A validar — regra ou contexto pendente | — | Jam 2 — Validação da URL da API (gravação restrita por conter dados de integração) |
| [CT-RF141](SIFIT/Cenario_Teste/CT-RF141_Integracoes_WhatsApp_Instancia_Obrigatoria.md) | Bloquear o salvamento com Nome da Instância vazio | Aprovado conforme a gravação | — | Jam 3 — Obrigatoriedade do Nome da Instância (gravação restrita por conter dados de integração) |
| [CT-RF142](SIFIT/Cenario_Teste/CT-RF142_Integracoes_WhatsApp_Persistir_Ativo.md) | Persistir a opção Ativo da integração de WhatsApp | Aprovado conforme a gravação | — | Jam 4 — Persistência da opção Ativo (gravação restrita por conter dados de integração) |
| [CT-RF143](SIFIT/Cenario_Teste/CT-RF143_Integracoes_WhatsApp_Conectar_Evolution.md) | Tratar falha ao conectar WhatsApp via Evolution API | Reprovado nas evidências | [BUG-050](SIFIT/Relatorio-de-Bugs.md#bug-050), em triagem | Jam 5 — Tentativas de conexão pela Evolution API (gravação restrita por conter dados de integração) |
| [CT-RF144](SIFIT/Cenario_Teste/CT-RF144_Integracoes_WhatsApp_Atualizar_Status.md) | Consultar novamente o status da integração de WhatsApp | Aprovado conforme a gravação | [BUG-050](SIFIT/Relatorio-de-Bugs.md#bug-050) na tentativa posterior de conexão | Jam 6 — Atualização manual de status (gravação restrita por conter dados de integração) |
| [CT-RF145](SIFIT/Cenario_Teste/CT-RF145_Configuracoes_Aniversario_Salvar_WhatsApp_SMS.md) | Salvar mensagens de aniversário para WhatsApp e SMS | Aprovado conforme a gravação | — | Jam 1 — Mensagens de aniversário por WhatsApp e SMS (gravação restrita por conter dados de integração) |
| [CT-RF146](SIFIT/Cenario_Teste/CT-RF146_Configuracoes_Pagamento_Online_Desativar.md) | Persistir a desativação do Pagamento Online | Aprovado conforme a gravação | — | Jam 2 — Desativação do Pagamento Online (gravação restrita por conter dados de integração) |
| [CT-RF147](SIFIT/Cenario_Teste/CT-RF147_Configuracoes_Design_Salvar_Cor_Principal.md) | Salvar uma Cor Principal hexadecimal válida | Aprovado conforme a gravação | — | Jam 3 — Persistência da Cor Principal (gravação restrita por conter dados de integração) |
| [CT-RF148](SIFIT/Cenario_Teste/CT-RF148_Configuracoes_Design_Validar_Cor_Secundaria.md) | Rejeitar código hexadecimal inválido na Cor Secundária | Reprovado nas evidências | [BUG-051](SIFIT/Relatorio-de-Bugs.md#bug-051), em triagem | Jam 4 — Validação da Cor Secundária (gravação restrita por conter dados de integração) |
| [CT-RF149](SIFIT/Cenario_Teste/CT-RF149_Configuracoes_Design_Logo_Limite_Tamanho.md) | Informar o limite de tamanho ao rejeitar o logo | Reprovado nas evidências | [BUG-052](SIFIT/Relatorio-de-Bugs.md#bug-052), em triagem | Jam 5 — Rejeição de logo pelo limite de tamanho (gravação restrita por conter dados de integração) |
| [CT-RF150](SIFIT/Cenario_Teste/CT-RF150_Integracoes_WhatsApp_Atualizar_Status_Aguardando_QR.md) | Atualizar a verificação do WhatsApp enquanto aguarda QR Code | Aprovado conforme a gravação | — | Jam 6 — Atualização de status enquanto aguarda QR Code (gravação restrita por conter dados de integração) |
| [CT-RF151](SIFIT/Cenario_Teste/CT-RF151_Configuracoes_Avaliacao_Desativar_Cobranca.md) | Desativar a cobrança da avaliação do cliente | Aprovado conforme a gravação | — | Jam 1 — Desativação da cobrança da avaliação (gravação restrita por conter dados de integração) |
| [CT-RF152](SIFIT/Cenario_Teste/CT-RF152_Configuracoes_Avaliacao_Tipo_Bioimpedancia.md) | Alterar o tipo de avaliação para Bioimpedância | Aprovado conforme a gravação | — | Jam 2 — Alteração do tipo para Bioimpedância (gravação restrita por conter dados de integração) |
| [CT-RF153](SIFIT/Cenario_Teste/CT-RF153_Configuracoes_Avaliacao_Habilitar_Teste_Fisico.md) | Habilitar Teste Físico nas configurações de avaliação | Aprovado conforme a gravação | — | Jam 3 — Habilitação de Teste Físico (gravação restrita por conter dados de integração) |
| [CT-RF154](SIFIT/Cenario_Teste/CT-RF154_Configuracoes_Aniversario_Desabilitar_Envio_Automatico.md) | Desabilitar o envio automático de aniversário | Aprovado conforme a gravação | — | Jam 4 — Desativação do envio automático de aniversário (gravação restrita por conter dados de integração) |
| [CT-RF155](SIFIT/Cenario_Teste/CT-RF155_Configuracoes_Aniversario_Cancelar_Mensagem_WhatsApp.md) | Cancelar a edição da mensagem de aniversário do WhatsApp | Aprovado conforme a gravação | — | Jam 5 — Cancelamento da edição da mensagem de WhatsApp (gravação restrita por conter dados de integração) |
| [CT-RF156](SIFIT/Cenario_Teste/CT-RF156_Configuracoes_Aniversario_Inserir_Variaveis_WhatsApp.md) | Inserir variáveis na mensagem de aniversário do WhatsApp | Aprovado conforme a gravação | — | Jam 6 — Inserção de variáveis na mensagem de WhatsApp (gravação restrita por conter dados de integração) |
| [CT-RF157](SIFIT/Cenario_Teste/CT-RF157_Aplicativo_Consultar_Notificacao.md) | Consultar os detalhes de uma notificação | Aprovado conforme a gravação | — | Jam 1 — Consulta de notificação existente (gravação restrita por conter dados de integração ou dados de alunos) |
| [CT-RF158](SIFIT/Cenario_Teste/CT-RF158_Aplicativo_Bloquear_Notificacao_Vazia.md) | Impedir o envio de uma notificação sem mensagem | Aprovado conforme a gravação | — | Jam 2 — Validação de mensagem obrigatória (gravação restrita por conter dados de integração ou dados de alunos) |
| [CT-RF159](SIFIT/Cenario_Teste/CT-RF159_Aplicativo_Criar_Notificacao_Preview.md) | Criar uma notificação e conferir a prévia e a listagem | Aprovado conforme a gravação | — | Jam 3 — Criação de notificação com prévia (gravação restrita por conter dados de integração ou dados de alunos) |
| [CT-RF160](SIFIT/Cenario_Teste/CT-RF160_Aplicativo_Postagens_Filtros_Estados_Vazios.md) | Alternar o filtro de postagens e abrir a lista completa | Aprovado conforme a gravação | — | Jam 4 — Filtros e lista completa de postagens (gravação restrita por conter dados de integração ou dados de alunos) |
| [CT-RF161](SIFIT/Cenario_Teste/CT-RF161_Aplicativo_Denuncias_Filtros_Estados_Vazios.md) | Alternar o filtro de denúncias com a lista vazia | Aprovado conforme a gravação | — | Jam 5 — Filtros de denúncias sem registros (gravação restrita por conter dados de integração ou dados de alunos) |
| [CT-RF162](SIFIT/Cenario_Teste/CT-RF162_Configuracoes_Biometria_Cancelar_Edicao_Senha.md) | Cancelar a edição da senha de Biometria | Aprovado conforme a gravação | — | Jam 6 — Cancelamento da edição no formulário de Biometria (gravação restrita por conter dados de integração ou dados de alunos) |
| [CT-RF163](SIFIT/Cenario_Teste/CT-RF163_Configuracoes_Biometria_Rejeitar_IP_Invalido.md) | Rejeitar um valor sem formato de IP em Biometria | Reprovado nas evidências | [BUG-053](SIFIT/Relatorio-de-Bugs.md#bug-053), em triagem | Jam 7 — Validação de IP do aparelho (gravação restrita por conter dados de integração ou dados de alunos) |
| [CT-RF164](SIFIT/Cenario_Teste/CT-RF164_Configuracoes_Biometria_Persistir_Porta.md) | Persistir a alteração da porta do aparelho de Biometria | Aprovado conforme a gravação | — | Jam 8 — Persistência da porta do aparelho (gravação restrita por conter dados de integração ou dados de alunos) |
| [CT-RF165](SIFIT/Cenario_Teste/CT-RF165_Configuracoes_Biometria_Validar_Dias_Bloqueio.md) | Validar dias negativos para travar a catraca | Reprovado nas evidências | [BUG-054](SIFIT/Relatorio-de-Bugs.md#bug-054), em triagem | Jam 9 — Validação de dias de bloqueio da catraca (gravação restrita por conter dados de integração ou dados de alunos) |

## 🔬 Como este projeto funciona

1. Registrar o comportamento esperado e os critérios na análise de requisitos.
2. Preparar ambiente e dados conforme o plano de testes.
3. Executar e gravar o cenário; documentar o resultado obtido em separado do BDD esperado.
4. Vincular cenário, requisito, Jam, arquivos e defeito. Agrupar manifestações do mesmo defeito, preservando os cenários de reteste.
5. Após correção, repetir os cenários em uma versão identificada e atualizar caso, relatórios e defeito com nova evidência.

Esta atualização organiza gravações existentes e **não é uma nova execução ou reteste da aplicação**. Os critérios são referências de QA; as decisões de produto pendentes estão explícitas. As variações propostas ainda não executadas não entram nas contagens de testes realizados. Não há suíte automatizada ou código da aplicação neste repositório.

## 🎥 Consultar os vídeos e a origem

Cada cenário contém o link do Jam. A evidência local de CT-RF21 inclui o relato original, o link fornecido, dois quadros extraídos da gravação, cronologia, requisição/resposta sem autenticação e metadados. O vídeo de CT-RF21 permanece no Jam.

A documentação de 14/11/2026 menciona 16 vídeos de CT-RF05–CT-RF20 (39.490.598 bytes), mas esses arquivos e as evidências locais de CT-RF02–CT-RF04 **não estavam nesta cópia do repositório** na revisão de 15/11/2026. O [índice de evidências](SIFIT/Evidencias/README.md) identifica os links disponíveis e essa pendência; o [manifesto](SIFIT/Evidencias/manifesto_sha256.json) cobre somente os arquivos locais incluídos agora.

## 🔐 Ambientes e limites

CT-RF01 usa `sifitalfa.centrion.com.br`; CT-RF02 aponta para `/profile`, com divergência de rota na aba Info; o frontend de CT-RF03 permanece não confirmado. CT-RF04 e os 16 novos casos usam `sifit.centrion.com.br`. Os novos vídeos foram gravados em 14/11/2026 com Chrome 157.0.8103.51 / Windows 11. A versão da aplicação e o zoom não foram identificados; conferir antes de nova execução.

CT-RF21 usa a página de Avaliações no mesmo domínio, com gravação de 15/11/2026 às 15:07:51 BRT, Chrome 157.0.8103.51 / Windows 11 e captura 1536 × 742. A causa do HTTP 500 e a persistência não foram confirmadas.

As quatro decisões pendentes são: composição da cobrança (CT-RF08), escopo das métricas (CT-RF11), significado dos códigos de personais (CT-RF13) e exclusão lógica de modalidades (CT-RF16). Os vídeos de login negativo têm senha mascarada; os documentos não reproduzem senhas, tokens ou corpos de autenticação.

## Inclusão de 16/11/2026 — Prospecção e Bandeiras de Cartão

| Caso | Funcionalidade | Resultado | Defeito | Fonte |
| --- | --- | --- | --- | --- |
| [CT-RF74](SIFIT/Cenario_Teste/CT-RF74_Temas_Prospeccao.md) | Alternar entre os temas claro e escuro na Prospecção | Aprovado conforme o resumo da gravação | — | [Jam](https://jam.dev/c/5dc9fc15-8e13-4f90-b21f-a49aedc6731e) |
| [CT-RF75](SIFIT/Cenario_Teste/CT-RF75_Detalhes_Lead_Cancelamento.md) | Consultar os detalhes de um lead e cancelar a edição | Aprovado conforme o resumo da gravação | — | [Jam](https://jam.dev/c/7ef0ee0b-497e-48b8-a57d-cd914558d303) |
| [CT-RF76](SIFIT/Cenario_Teste/CT-RF76_Exclusao_Leads_Confirmacao.md) | Excluir leads com confirmação | Aprovado conforme o resumo da gravação | — | [Jam](https://jam.dev/c/2ac5e5ed-b10f-4cc9-9f97-7ba65ca560f8) |
| [CT-RF77](SIFIT/Cenario_Teste/CT-RF77_Cadastro_Lead_Novo_Contato.md) | Cadastrar lead no estágio Novo Contato | Aprovado conforme o resumo da gravação | — | [Jam](https://jam.dev/c/29447c6a-90f5-48b2-ac5d-d43cad44a782) |
| [CT-RF78](SIFIT/Cenario_Teste/CT-RF78_Cadastro_Lead_Interessado.md) | Cadastrar lead no estágio Interessado | Aprovado conforme o resumo da gravação | — | [Jam](https://jam.dev/c/f8735cbf-4043-4467-b43f-3cad7eff0da8) |
| [CT-RF79](SIFIT/Cenario_Teste/CT-RF79_Cadastro_Lead_Aula_Experimental.md) | Cadastrar lead no estágio Fez Aula Experimental | Aprovado conforme o resumo da gravação | — | [Jam](https://jam.dev/c/bef3d877-056b-4274-87c3-da37869c54fd) |
| [CT-RF80](SIFIT/Cenario_Teste/CT-RF80_Cadastro_Lead_Proposta.md) | Cadastrar lead no estágio Proposta | Aprovado conforme o resumo da gravação | — | [Jam](https://jam.dev/c/84f94285-ae5f-4f95-b640-a9b107565aa6) |
| [CT-RF81](SIFIT/Cenario_Teste/CT-RF81_Cadastro_Bandeira_Parcela_Listagem.md) | Cadastrar bandeira com parcela e conferir a listagem | Reprovado nas evidências resumidas | [BUG-035](SIFIT/Relatorio-de-Bugs.md#bug-035) | [Jam](https://jam.dev/c/2f0280fb-6b7f-4cf0-a45c-02f8c16b6c5e) |
| [CT-RF82](SIFIT/Cenario_Teste/CT-RF82_Tema_Escuro_Bandeiras.md) | Verificar aplicação dos temas na tela de Bandeiras | Reprovado nas evidências resumidas | [BUG-036](SIFIT/Relatorio-de-Bugs.md#bug-036) | [Jam](https://jam.dev/c/ae4dc198-8a42-4451-898a-fb376596c744) |
| [CT-RF83](SIFIT/Cenario_Teste/CT-RF83_Cadastro_Lead_Apenas_Nome.md) | Validar cadastro de lead preenchendo apenas o nome | Reprovado conforme o relato; regra de obrigatoriedade a confirmar | [BUG-037](SIFIT/Relatorio-de-Bugs.md#bug-037) | [Jam](https://jam.dev/c/ef3df03c-16ce-4cb6-b0c7-d04514cab4f6) |
| [CT-RF84](SIFIT/Cenario_Teste/CT-RF84_Cadastro_Lead_Fechado.md) | Cadastrar lead no estágio Fechado | Aprovado conforme o resumo da gravação | — | [Jam](https://jam.dev/c/775b9003-fdf7-4ad5-8882-15ba606b6674) |

Integração documental dos arquivos RESUMO.txt fornecidos em `C:\Users\Leonardo\Desktop\evidencias`, com data de gravação e análise informada de 16/11/2026. Os Jams não foram reabertos nesta integração; eventos de rede, horários e quadros abaixo são transcritos dos resumos, sem verificação independente. Não houve nova execução do SIFIT, reteste, consulta ao banco, logs ou código.

CT-RF74–CT-RF84 acrescentam oito aprovações e três reprovações conforme os resumos fornecidos, com BUG-035–BUG-037 em triagem. CT-RF83 mantém a classificação do relato, condicionada à confirmação da regra de obrigatoriedade. Os dez casos anteriores a validar permanecem inalterados.

[Resumos e rastreabilidade local](SIFIT/Evidencias/README.md).

## 📎 Referência de organização

A apresentação foi adaptada do [repositório de referência de testes manuais](https://github.com/Adnyslougansilva/extensao-qa), com conteúdo e rastreabilidade próprios do SIFIT.

CT-RF22–CT-RF25 estão integrados aos requisitos, plano e relatórios. A imagem persistida em CT-RF25 permanece a validar. As evidências locais de CT-RF23–25 contêm resumos e cronologias; os vídeos permanecem no Jam. Não houve nova execução ou reteste.

CT-RF35 (Objetivos Treino, gravação de 15/11/2026 às 18:13 BRT, Chrome 157.0.8103.78 / Windows 11) tem pasta local com capturas extraídas do Jam, cronologia, origem e hashes; o vídeo permanece no Jam, e o Jam não capturou o corpo da requisição nem da resposta.
