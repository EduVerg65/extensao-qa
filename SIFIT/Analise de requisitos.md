# 📦 Análise de Requisitos — SIFIT

**Módulos:** Autenticação, Perfil, Clientes / Filtros, Financeiro, Página inicial / Personais, SifitBox / Modalidades e Turmas, Categorias Crossfit, Avaliações, Exercícios, Grupos Musculares e Objetivos de Treino.

**Atualização:** 15/11/2026 — RF01 a RF33 e RF35, com inclusão de Objetivos de Treino (CT-RF35 / BUG-018 em triagem). A numeração RF34 / CT-RF34 permanece reservada e sem cenário integrado nesta revisão.

**Padronização documental:** 13/11/2026, sem alteração dos resultados registrados.

Esta análise documenta os 34 requisitos de QA para os cenários relacionados abaixo, com base nos relatos e nas evidências fornecidas. RF01–RF04 e suas análises históricas foram preservados; RF05–RF20 ampliam a cobertura em 14/11/2026; RF21 acrescenta Avaliações, RF22–RF28 acrescentam Exercícios, RF29–RF33 acrescentam Grupos Musculares e RF35 acrescenta Objetivos de Treino em 15/11/2026. Os critérios abaixo constituem a referência de QA para esses fluxos; não representam validação de uma especificação formal pelo responsável pelo produto.

## 📋 Visão geral dos requisitos

| Código | Funcionalidade | Prioridade | Caso relacionado |
| --- | --- | --- | --- |
| [RF01](#rf01--iniciar-recuperação-de-senha) | Recuperação de senha | Alta | [CT-RF01](Cenario_Teste/CT-RF01_Esqueci-senha.md) |
| [RF02](#rf02--exibir-perfil-do-usuário-autenticado) | Perfil do usuário | Alta | [CT-RF02_ERRO](Cenario_Teste/CT-RF02_ERRO.md) |
| [RF03](#rf03--pesquisar-clientes-com-filtros-combinados) | Filtros da página Clientes | Alta, proposta para triagem | [CT-RF03](Cenario_Teste/CT-RF03_FILTRO_TelaClientes.md) |
| [RF04](#rf04--autenticar-usuário-com-credenciais-válidas) | Login com sucesso | Alta | [CT-RF04_loginComSucesso](Cenario_Teste/CT-RF04_loginComSucesso.md) |
| [RF05](#rf05) | Recusar autenticação com senha incorreta | Alta, proposta | [CT-RF05](Cenario_Teste/CT-RF05_Login_SenhaIncorreta.md) |
| [RF06](#rf06) | Recusar autenticação com usuário inexistente | Alta, proposta | [CT-RF06](Cenario_Teste/CT-RF06_Login_UsuarioInexistente.md) |
| [RF07](#rf07) | Oferecer retorno ao solicitar exportação financeira | Média, proposta | [CT-RF07](Cenario_Teste/CT-RF07_Exportacao_Financeiro.md) |
| [RF08](#rf08) | Apresentar a composição e o valor comunicado na cobrança | Alta, proposta | [CT-RF08](Cenario_Teste/CT-RF08_Calculo_Cobranca.md) |
| [RF09](#rf09) | Manter contagem e paginação coerentes com as mensalidades | Alta, proposta | [CT-RF09](Cenario_Teste/CT-RF09_Contagem_Mensalidades.md) |
| [RF10](#rf10) | Aplicar o filtro Até 7 dias com contagem consistente | Alta, proposta | [CT-RF10](Cenario_Teste/CT-RF10_Filtro_Mensalidades.md) |
| [RF11](#rf11) | Explicitar o escopo dos indicadores financeiros | Média, proposta | [CT-RF11](Cenario_Teste/CT-RF11_Metricas_Financeiro.md) |
| [RF12](#rf12) | Validar a ordem das datas do período | Média, proposta | [CT-RF12](Cenario_Teste/CT-RF12_Periodo_Dashboard.md) |
| [RF13](#rf13) | Identificar personais sem confundir códigos com contagem | Média, proposta | [CT-RF13](Cenario_Teste/CT-RF13_Codigos_Personais.md) |
| [RF14](#rf14) | Preservar a legibilidade das tabelas no tema escuro | Média, proposta | [CT-RF14](Cenario_Teste/CT-RF14_Contraste_TemaEscuro.md) |
| [RF15](#rf15) | Permitir concluir e cancelar a edição de modalidade | Média, proposta | [CT-RF15](Cenario_Teste/CT-RF15_Edicao_Modalidade.md) |
| [RF16](#rf16) | Comunicar e aplicar a regra de remoção de modalidade | Média, proposta | [CT-RF16](Cenario_Teste/CT-RF16_Exclusao_Modalidade.md) |
| [RF17](#rf17) | Filtrar categorias por código e nome | Média, proposta | [CT-RF17](Cenario_Teste/CT-RF17_Filtros_Categorias.md) |
| [RF18](#rf18) | Salvar a atualização do nome de categoria | Média, proposta | [CT-RF18](Cenario_Teste/CT-RF18_Atualizacao_Categoria.md) |
| [RF19](#rf19) | Excluir categoria permitida ou explicar o impedimento | Média, proposta | [CT-RF19](Cenario_Teste/CT-RF19_Exclusao_Categoria.md) |
| [RF20](#rf20) | Cadastrar e listar uma nova categoria | Média, proposta | [CT-RF20](Cenario_Teste/CT-RF20_Criacao_Categoria.md) |
| [RF21](#rf21) | Cadastrar avaliação ou informar validação específica | Alta, proposta | [CT-RF21](Cenario_Teste/CT-RF21_Cadastro_Avaliacao.md) |
| [RF22](#rf22) | Permitir informar o código do exercício conforme a regra | Média, proposta | [CT-RF22](Cenario_Teste/CT-RF22_Digitacao_Codigo_Exercicio.md) |
| [RF23](#rf23) | Exclusão de exercício | Média, proposta | [CT-RF23](Cenario_Teste/CT-RF23_Exclusao_Exercicio.md) |
| [RF24](#rf24) | Edição de exercício aumenta o total e mantém duas entradas | Média, proposta | [CT-RF24](Cenario_Teste/CT-RF24_Edicao_Exercicio.md) |
| [RF25](#rf25) | Envio de exercício com imagem | Média, proposta | [CT-RF25](Cenario_Teste/CT-RF25_Envio_Exercicio_Imagem.md) |
| [RF26](#rf26) | Validar campos obrigatórios do exercício | Alta, proposta | [CT-RF26](Cenario_Teste/CT-RF26_Exercicio_Campos_Vazios.md) |
| [RF27](#rf27) | Rejeitar vídeo no campo de imagem com feedback | Média, proposta | [CT-RF27](Cenario_Teste/CT-RF27_Video_Campo_Imagem.md) |
| [RF28](#rf28) | Rejeitar imagem no campo de vídeo com feedback | Média, proposta | [CT-RF28](Cenario_Teste/CT-RF28_Imagem_Campo_Video.md) |
| [RF29](#rf29) | Excluir grupo muscular ou explicar o impedimento | Alta, proposta | [CT-RF29](Cenario_Teste/CT-RF29_Exclusao_GrupoMuscular.md) |
| [RF30](#rf30) | Exibir as imagens cadastradas dos grupos musculares | Média, proposta | [CT-RF30](Cenario_Teste/CT-RF30_Imagens_GruposMusculares.md) |
| [RF31](#rf31) | Cadastrar e listar um grupo muscular | Média, proposta | [CT-RF31](Cenario_Teste/CT-RF31_Cadastro_GrupoMuscular.md) |
| [RF32](#rf32) | Alterar o tipo de membro de um grupo muscular | Média, proposta | [CT-RF32](Cenario_Teste/CT-RF32_Edicao_TipoMembro.md) |
| [RF33](#rf33) | Filtrar a listagem de grupos musculares por código e tipo | Média, proposta | [CT-RF33](Cenario_Teste/CT-RF33_Filtros_GruposMusculares.md) |
| [RF35](#rf35) | Cadastrar objetivo de treino ou informar validação específica | Alta, proposta | [CT-RF35](Cenario_Teste/CT-RF35_Cadastro_Objetivo_Treino.md) |

---

## RF01 — Iniciar recuperação de senha

| Campo | Descrição |
| --- | --- |
| **Requisito funcional** | O sistema deve permitir que um usuário não autenticado inicie a recuperação de senha pela opção "Esqueci minha senha" na tela de login. |
| **Ator** | Usuário sem acesso à sua senha. |
| **Pré-condição** | Página de login acessível e opção de recuperação visível. |
| **Gatilho** | Clique em "Esqueci minha senha". |
| **Comportamento esperado** | Exibir formulário ou página com os campos e as orientações necessários para iniciar a solicitação de redefinição. |
| **Pós-condição esperada** | Usuário consegue prosseguir com a identificação da conta e a solicitação de recuperação. |
| **Prioridade** | Alta, pois a falha impede o início da recuperação autônoma de acesso. |
| **Situação observada** | Não atendido na gravação: cliques sem abertura do fluxo e nenhum registro de requisição no Jam. |

### Critérios de aceitação

1. A opção deve estar disponível antes da autenticação.
2. O clique deve iniciar o fluxo de recuperação por formulário ou página própria.
3. Os campos e as orientações para a próxima etapa devem ser apresentados ao usuário.
4. Quando uma etapa depender do servidor, a interface deve realizar a requisição correspondente e apresentar o retorno ou a falha ao usuário.

A abertura de um formulário local pode ocorrer sem requisição de rede. Neste defeito, a ausência de requisições acompanha a ausência de qualquer abertura do fluxo; não comprova, por si só, uma falha no servidor.

### Pontos a definir para a recuperação completa

O identificador da conta, o canal de recuperação, o contrato da API, as mensagens de retorno, a validade de eventual token e as regras de redefinição precisam ser confirmados com o responsável pelo sistema antes de detalhar os testes das etapas seguintes. Não há comprovação de envio de e-mail, geração de token ou alteração de senha nas evidências analisadas.

---

## RF02 — Exibir perfil do usuário autenticado

| Campo | Descrição |
| --- | --- |
| **Requisito funcional** | Ao acessar Perfil, o sistema deve exibir os dados da conta autenticada e os campos de Usuário, Documentos e Endereço, organizados conforme o padrão visual do SIFIT. |
| **Ator** | Usuário autenticado com acesso ao perfil. |
| **Pré-condição** | Sessão válida, opção Perfil disponível e dados da conta conhecidos para comparação no reteste. |
| **Gatilho** | Acesso à opção Perfil no menu do usuário. |
| **Comportamento esperado** | Exibir dados reais, campos renderizados e textos em português, com imagens e conteúdo dentro dos limites da tela. |
| **Pós-condição esperada** | Usuário consegue visualizar suas informações e interagir com os campos editáveis conforme suas permissões. |
| **Prioridade** | Alta, pelo comprometimento da visualização e da edição dos dados do perfil. |
| **Situação observada** | Não atendido nas evidências: conteúdo fictício, campos ausentes visualmente e layout desconfigurado. |

### Critérios de aceitação do RF02

1. Os valores apresentados devem corresponder à conta autenticada; textos e imagens de demonstração não devem substituir o cadastro.
2. As seções Usuário, Documentos e Endereço devem apresentar todos os campos previstos, seus rótulos e os valores cadastrados, quando existentes.
3. Campos editáveis devem permitir interação de acordo com as permissões da conta.
4. A interface deve usar português e o padrão visual do sistema.
5. Imagens e demais elementos devem respeitar seus contêineres, sem desalinhamento ou rolagem horizontal indevida nas resoluções definidas para o reteste.

### Pontos a definir para o perfil

Confirmar campos obrigatórios e opcionais, permissões de edição, resoluções suportadas, comportamento para dados ausentes e regras de validação e salvamento. A evidência atual avalia o carregamento e a apresentação; não comprova persistência de alterações nem contém os dados reais da conta para comparação individual.

---

## RF03 — Pesquisar clientes com filtros combinados

| Campo | Descrição |
| --- | --- |
| **Requisito funcional** | A página Clientes deve permitir a pesquisa por Código, Nome, Status, Situação Financeira, Plano e Personal, retornando exclusivamente os clientes que atendam simultaneamente a todos os critérios selecionados. |
| **Ator** | Usuário autenticado com acesso à consulta de clientes da empresa. |
| **Pré-condição** | Sessão válida, acesso à página Clientes e opções de filtros disponíveis. Para validação, utilizar base conhecida com os atributos e vínculos de cada cliente. |
| **Gatilho** | Clique em Buscar após definir ou alterar os filtros. |
| **Comportamento esperado** | Aplicar lógica AND entre os critérios ativos e atualizar a tabela com o conjunto correspondente; apresentar "Nenhum cliente encontrado" quando o conjunto estiver vazio. |
| **Pós-condição esperada** | A tabela corresponde à seleção da busca atual, respeitando a empresa e as permissões da conta. |
| **Prioridade** | Alta, proposta para triagem pelo impacto na confiabilidade da consulta. |
| **Situação observada** | Não atendido conforme o relato: clientes incompatíveis com os filtros e resultados praticamente iguais ao alternar a situação financeira. Não houve reprodução independente nesta revisão. |

### Critérios de aceitação do RF03

1. Todos os clientes retornados devem satisfazer todos os filtros selecionados. Atender apenas a parte dos critérios não permite incluir um registro.
2. Todos os clientes esperados na base de teste devem ser encontrados, considerando outras páginas, caso exista paginação.
3. Alterar um filtro e executar Buscar deve atualizar o resultado conforme a nova seleção, mantendo as demais restrições.
4. Código e Nome devem restringir a busca quando preenchidos, conforme as regras de correspondência acordadas. Campos sem restrição não devem excluir clientes; limpar uma seleção deve remover a respectiva restrição.
5. Uma pesquisa sem correspondências deve apresentar **"Nenhum cliente encontrado"**, sem manter linhas da pesquisa anterior.
6. A aplicação efetiva dos filtros deve ser verificável conforme a arquitetura: parâmetros de acordo com o contrato na busca no servidor ou aplicação das condições sobre dados suficientes na busca local. HTTP 200, isoladamente, não comprova atendimento ao requisito.

### Pontos a definir para a pesquisa de clientes

Confirmar as regras de correspondência de Código e Nome, os valores e padrões dos filtros, o cálculo da situação financeira, a regra de vínculo com Plano e Personal e o tratamento da paginação. Confirmar também o contrato do endpoint e onde a filtragem deve ocorrer, sem impor uma implementação somente pela ausência de parâmetros no corpo informado.

Os IDs exemplificativos `plano_id: 60` e `personal_id: 36` não têm correspondência validada com Plano Hendreu e Marcelo Longo Zandonadi. O relato informa `empresa_id: 1`; esse valor não deve ser presumido para outros ambientes ou contas.

---

## RF04 — Autenticar usuário com credenciais válidas

| Campo | Descrição |
| --- | --- |
| **Requisito funcional** | O sistema deve autenticar o usuário com Login e Senha válidos e permitir acesso ao dashboard. |
| **Ator** | Usuário com conta ativa e permissão de acesso ao painel. |
| **Pré-condição** | Página de login acessível e credenciais válidas disponíveis. |
| **Gatilho** | Clique em Entrar após preencher Login e Senha. |
| **Comportamento esperado** | Concluir a autenticação, navegar para `/dashboard` e apresentar menu e resumo da academia. |
| **Pós-condição esperada** | Usuário acessa a página inicial autenticada. |
| **Prioridade** | Alta, por validar o acesso ao sistema. |
| **Situação observada** | Atendido na gravação de 13/11/2026: chamadas de autenticação HTTP 200, navegação para `/dashboard` e painel visível. |

### Critérios de aceitação do RF04

1. O formulário deve permitir preencher Login e Senha, com senha mascarada na interface.
2. Credenciais válidas devem permitir concluir a autenticação ao clicar em **Entrar**.
3. O navegador deve acessar `https://sifit.centrion.com.br/dashboard`.
4. O menu de navegação e o resumo da academia devem ser apresentados após a autenticação. HTTP 200 isoladamente não aprova o caso.

### Limites da validação do login

O caso cobre o fluxo positivo gravado. Credenciais inválidas, campos vazios, logout, expiração, persistência de **Manter conectado**, outras permissões e correspondência dos dados exibidos com o cadastro exigem validações próprias. A versão da aplicação não foi informada.

---

## Ampliação de cobertura — 14/11/2026

Os requisitos abaixo são referências de QA propostas a partir das evidências. Cálculo de encargos (RF08), escopo dos cartões (RF11), significado dos códigos de personais (RF13) e remoção lógica de modalidades (RF16) dependem da confirmação do produto; seus cenários estão a validar e não geraram defeitos confirmados. Os casos RF09 e RF10 compartilham o BUG-005.

<a id="rf05"></a>

## RF05 — Recusar autenticação com senha incorreta

| Campo | Descrição |
| --- | --- |
| Requisito de QA | Recusar a autenticação e informar a falha sem abrir a área autenticada. |
| Ator | Usuário sem sessão autenticada. |
| Pré-condições | Iniciar sem sessão autenticada na página de login. Dispor de conta de teste existente e senha propositalmente incorreta. |
| Gatilho | Preencher Login com a conta de teste existente. Informar uma senha incorreta, mantendo o valor mascarado. Clicar em Entrar e observar a mensagem, a URL e a ausência de acesso ao painel. |
| Caso | [CT-RF05](Cenario_Teste/CT-RF05_Login_SenhaIncorreta.md) |
| Situação observada | Aprovado conforme a gravação. Após o envio, a tela permanece no login e apresenta “O nome de usuário e senha não correspondem.” |
| Defeito | Nenhum no fluxo avaliado |
| Evidências | [Evidências](Evidencias/CT-RF05_Login_SenhaIncorreta/README.md) e [Jam](https://jam.dev/c/75f16436-7201-4de0-b191-1c4d0d63bfe8). |

### Critérios de aceitação do RF05

1. Senha incorreta não permite acesso ao dashboard.
2. A interface apresenta mensagem compreensível de credenciais inválidas.
3. A conclusão considera mensagem e permanência no login, além do status HTTP.

### Pontos a confirmar e limites do RF05

HTTP 200 é o status da resposta da API; a recusa é demonstrada pela interface. O vídeo não valida bloqueio por tentativas ou outras regras de segurança. Usar como regressão de autenticação negativa; preparar conta conhecida e repetir após alterações no login.

---

<a id="rf06"></a>

## RF06 — Recusar autenticação com usuário inexistente

| Campo | Descrição |
| --- | --- |
| Requisito de QA | Recusar o acesso para credenciais inválidas. |
| Ator | Usuário sem sessão autenticada. |
| Pré-condições | Iniciar sem sessão autenticada. Preparar um identificador cuja inexistência seja conhecida na base de teste. |
| Gatilho | Preencher Login com identificador inexistente na base de referência. Informar uma senha de teste, sem expor seu valor. Clicar em Entrar e verificar que não há acesso à área autenticada. |
| Caso | [CT-RF06](Cenario_Teste/CT-RF06_Login_UsuarioInexistente.md) |
| Situação observada | Aprovado conforme a gravação. A gravação termina na página de login com a mensagem genérica de credenciais inválidas, sem acesso ao painel. |
| Defeito | Nenhum no fluxo avaliado |
| Evidências | [Evidências](Evidencias/CT-RF06_Login_UsuarioInexistente/README.md) e [Jam](https://jam.dev/c/b184e875-2cb1-4a01-b4dd-bc85b3741ff6). |

### Critérios de aceitação do RF06

1. Identificador inexistente não permite abrir a área autenticada.
2. A tentativa recebe retorno compreensível sem revelar se a conta existe.
3. Em nova execução, a inexistência do identificador é conferida na base de referência.

### Pontos a confirmar e limites do RF06

A inexistência do usuário é o cenário declarado no título; não foi conferida no banco. A mensagem já está visível no início do vídeo e permanece após a nova tentativa. Repetir com identificador de inexistência comprovada; a classificação atual refere-se à recusa visível do cenário declarado pelo autor.

---

<a id="rf07"></a>

## RF07 — Oferecer retorno ao solicitar exportação financeira

| Campo | Descrição |
| --- | --- |
| Requisito de QA | Iniciar a exportação e apresentar um retorno claro ao usuário. |
| Ator | Usuário autenticado com permissão no módulo. |
| Pré-condições | Sessão autenticada com permissão para consultar e exportar o financeiro. Modal Financeiro em Aberto aberto e registros disponíveis. |
| Gatilho | Abrir Financeiro em Aberto a partir da página inicial. Clicar uma vez em Exportar e aguardar a conclusão. Verificar retorno visual e o arquivo no histórico de downloads; repetir somente para conferir comportamento. |
| Caso | [CT-RF07](Cenario_Teste/CT-RF07_Exportacao_Financeiro.md) |
| Situação observada | Reprovado nas evidências. Vários cliques em Exportar não produzem mudança ou confirmação visível durante a gravação. |
| Defeito | [BUG-004](Relatorio-de-Bugs.md#bug-004) |
| Evidências | [Evidências](Evidencias/CT-RF07_Exportacao_Financeiro/README.md) e [Jam](https://jam.dev/c/1084cb18-cb3d-4b85-9c2f-ee431b59a06b). |

### Critérios de aceitação do RF07

1. O clique oferece retorno perceptível de processamento, conclusão ou falha.
2. O arquivo disponibilizado corresponde ao escopo de exportação definido pelo produto.
3. A validação do download inclui o histórico e a abertura do arquivo, ainda pendentes na evidência atual.

### Pontos a confirmar e limites do RF07

O vídeo não mostra o diretório de downloads; portanto, não comprova sozinho que nenhum arquivo foi gerado. A ausência de requisição também não exclui uma exportação feita no próprio navegador. Investigar o retorno do botão; no reteste capturar o histórico de downloads e abrir o arquivo antes de concluir se a exportação foi gerada.

---

<a id="rf08"></a>

## RF08 — Apresentar a composição e o valor comunicado na cobrança

| Campo | Descrição |
| --- | --- |
| Requisito de QA | Exibir a composição do total, incluindo eventuais juros, e deixar claro qual valor será comunicado. |
| Ator | Usuário autenticado com permissão no módulo. |
| Pré-condições | Sessão autenticada e mensalidade de teste com valor, vencimento e encargos conhecidos. Confirmar com o produto multa, juros, arredondamento e valor que deve constar na mensagem. |
| Gatilho | Abrir Cobrar via WhatsApp para uma mensalidade de referência. Comparar valor original, multa, total atualizado e texto inicial da mensagem. Calcular o total conforme a regra confirmada e registrar a composição, sem enviar mensagem. |
| Caso | [CT-RF08](Cenario_Teste/CT-RF08_Calculo_Cobranca.md) |
| Situação observada | A validar — regra ou contexto pendente. O modal mostra valor original de R$ 350,00, multa de R$ 7,00 e total atualizado de R$ 377,83. A mensagem inicial cita R$ 350,00; o autor escreve que o valor deveria ser R$ 357,00. |
| Defeito | Sem defeito confirmado |
| Evidências | [Evidências](Evidencias/CT-RF08_Calculo_Cobranca/README.md) e [Jam](https://jam.dev/c/79b712ae-d9e0-4600-862f-fd3a278285ff). |

### Critérios de aceitação do RF08

1. Valor original, multa e eventuais juros são identificáveis.
2. Total confere com a fórmula e o arredondamento definidos.
3. O valor na mensagem segue uma regra explícita.

### Pontos a confirmar e limites do RF08

R$ 350,00 + R$ 7,00 = R$ 357,00, mas os R$ 20,83 restantes podem corresponder a juros. A regra de cálculo e as configurações não foram fornecidas; não é possível afirmar que o total está incorreto. Confirmar a origem dos R$ 20,83 além de principal e multa e a regra da mensagem; não registrar cálculo incorreto antes dessa validação.

---

<a id="rf09"></a>

## RF09 — Manter contagem e paginação coerentes com as mensalidades

| Campo | Descrição |
| --- | --- |
| Requisito de QA | Manter a contagem, a listagem e a paginação coerentes e permitir consultar todos os registros contabilizados. |
| Ator | Usuário autenticado com permissão no módulo. |
| Pré-condições | Sessão autenticada com acesso ao financeiro. Base de referência com mensalidades conhecidas e distribuídas entre as faixas de vencimento. |
| Gatilho | Abrir Financeiro em Aberto e selecionar Todos. Comparar o contador com as linhas e o total do rodapé; percorrer páginas quando disponíveis. Selecionar +30 dias e repetir a conferência da quantidade e dos registros acessíveis. |
| Caso | [CT-RF09](Cenario_Teste/CT-RF09_Contagem_Mensalidades.md) |
| Situação observada | Reprovado nas evidências. Todos informa três mensalidades, mas aparece uma linha. No filtro +30 dias, o contador indica dois registros e apenas uma linha permanece disponível. |
| Defeito | [BUG-005](Relatorio-de-Bugs.md#bug-005) |
| Evidências | [Evidências](Evidencias/CT-RF09_Contagem_Mensalidades/README.md) e [Jam](https://jam.dev/c/1874d0b3-5c7c-4f28-85be-91750e20cbe1). |

### Critérios de aceitação do RF09

1. Contador, total do rodapé e conjunto listado são consistentes.
2. Todos os registros contados podem ser consultados, considerando a paginação.
3. A troca de filtro recalcula a contagem e os registros com os mesmos critérios.

### Pontos a confirmar e limites do RF09

Não foram inspecionados os corpos das respostas ou o banco. Os casos CT-RF09, CT-RF10 e CT-RF11 tratam de aspectos relacionados do mesmo modal. Retestar com o CT-RF10; os dois cenários documentam manifestações do BUG-005, sem criar um defeito duplicado.

---

<a id="rf10"></a>

## RF10 — Aplicar o filtro Até 7 dias com contagem consistente

| Campo | Descrição |
| --- | --- |
| Requisito de QA | O contador do filtro e os registros exibidos devem representar o mesmo conjunto. |
| Ator | Usuário autenticado com permissão no módulo. |
| Pré-condições | Sessão autenticada e modal Financeiro em Aberto disponível. Mensalidade conhecida que pertença à faixa Até 7 dias conforme a regra do produto. |
| Gatilho | Selecionar Até 7 dias no modal financeiro. Aguardar o carregamento e comparar contador, linhas e estado vazio. Conferir que os registros esperados estão acessíveis e que a mensagem vazia só aparece para conjunto vazio. |
| Caso | [CT-RF10](Cenario_Teste/CT-RF10_Filtro_Mensalidades.md) |
| Situação observada | Reprovado nas evidências. O filtro mantém o contador 1, enquanto a lista informa “Nenhuma mensalidade encontrada para o filtro atual”. |
| Defeito | [BUG-005](Relatorio-de-Bugs.md#bug-005) |
| Evidências | [Evidências](Evidencias/CT-RF10_Filtro_Mensalidades/README.md) e [Jam](https://jam.dev/c/3f78cf16-2c3b-48bc-8622-23b829debbec). |

### Critérios de aceitação do RF10

1. Contador e lista usam o mesmo critério de período.
2. Uma mensalidade contabilizada no filtro pode ser consultada.
3. Conjunto vazio apresenta mensagem e contagem coerentes.

### Pontos a confirmar e limites do RF10

A evidência confirma a divergência visual. A causa técnica não foi investigada. Relacionado ao CT-RF09. Retestar em conjunto com CT-RF09 e conferir o contrato da faixa Até 7 dias antes de preparar a base.

---

<a id="rf11"></a>

## RF11 — Explicitar o escopo dos indicadores financeiros

| Campo | Descrição |
| --- | --- |
| Requisito de QA | Indicar claramente quais métricas seguem o filtro e quais representam o total geral ou o mês. |
| Ator | Usuário autenticado com permissão no módulo. |
| Pré-condições | Sessão autenticada e base com valores conhecidos por faixa e mês. Definir quais cartões são globais, mensais ou dependentes do filtro selecionado. |
| Gatilho | Abrir Financeiro em Aberto e registrar os cartões e a lista em Todos. Alternar Até 7 dias e +30 dias. Comparar cada cartão com seu escopo definido e verificar se a interface identifica esse escopo. |
| Caso | [CT-RF11](Cenario_Teste/CT-RF11_Metricas_Financeiro.md) |
| Situação observada | A validar — regra ou contexto pendente. A lista alterna entre uma linha e estado vazio. O cartão de atraso muda de dois para zero alunos; outros totais, como Total em aberto de R$ 470,00 e Recuperado no mês de R$ 45,00, permanecem. |
| Defeito | Sem defeito confirmado |
| Evidências | [Evidências](Evidencias/CT-RF11_Metricas_Financeiro/README.md) e [Jam](https://jam.dev/c/4491c9e7-7e00-4063-91ce-8683e316df06). |

### Critérios de aceitação do RF11

1. Cada indicador possui escopo e período identificados.
2. Indicadores filtrados acompanham a seleção.
3. Indicadores globais ou mensais podem permanecer constantes quando isso corresponde à regra definida.

### Pontos a confirmar e limites do RF11

Totais globais podem permanecer constantes por definição. Sem a regra de cada indicador, não é possível classificar toda permanência de valor como erro. A divergência de contagens está documentada nos itens 05 e 06. Confirmar os contratos dos cartões; a constância de totais globais não é suficiente para abrir outro defeito financeiro.

---

<a id="rf12"></a>

## RF12 — Validar a ordem das datas do período

| Campo | Descrição |
| --- | --- |
| Requisito de QA | Validar a ordem das datas, orientar o usuário e aplicar um período válido com retorno perceptível. |
| Ator | Usuário autenticado com permissão no módulo. |
| Pré-condições | Sessão autenticada com acesso ao seletor de período da página inicial. Registrar as regras de aplicação do filtro e preparar um intervalo válido de controle. |
| Gatilho | Alterar a data final para 10/11/2026 na base de referência da gravação. Alterar a inicial para 19/11/2026, posterior à data final. Verificar a validação e tentar aplicar; depois selecionar um período válido e conferir os dados de referência. |
| Caso | [CT-RF12](Cenario_Teste/CT-RF12_Periodo_Dashboard.md) |
| Situação observada | Reprovado nas evidências. O seletor chega a exibir 19/11/2026–10/11/2026, com início posterior ao fim, sem uma validação visível. Os indicadores permanecem com os mesmos valores nos quadros conferidos. |
| Defeito | [BUG-006](Relatorio-de-Bugs.md#bug-006) |
| Evidências | [Evidências](Evidencias/CT-RF12_Periodo_Dashboard/README.md) e [Jam](https://jam.dev/c/93165ba3-3bfe-4dd5-9379-ab8db2d686ba). |

### Critérios de aceitação do RF12

1. Data inicial posterior à final recebe validação clara.
2. Somente intervalos válidos são aplicados.
3. O efeito de um período válido é conferido com dados conhecidos; valores constantes não provam erro de cálculo.

### Pontos a confirmar e limites do RF12

A captura comprova o intervalo invertido. Indicadores constantes, isoladamente, não demonstram falha no cálculo; os botões de seta geraram requisições, portanto não se pode dizer que todos estavam sem função. Corrigir e retestar a validação do intervalo; avaliar a atualização dos indicadores em base controlada como verificação complementar.

---

<a id="rf13"></a>

## RF13 — Identificar personais sem confundir códigos com contagem

| Campo | Descrição |
| --- | --- |
| Requisito de QA | Se a coluna for um identificador de cadastro, lacunas são aceitáveis. Se deveria numerar linhas, a regra precisa ser esclarecida. |
| Ator | Usuário autenticado com permissão no módulo. |
| Pré-condições | Sessão autenticada e acesso à listagem Personais. Confirmar se Código representa ID de cadastro ou posição na listagem. |
| Gatilho | Abrir Personais pelo indicador da página inicial. Contar as linhas e comparar com o total informado. Conferir o significado e a unicidade dos códigos com o cadastro de referência. |
| Caso | [CT-RF13](Cenario_Teste/CT-RF13_Codigos_Personais.md) |
| Situação observada | A validar — regra ou contexto pendente. A lista contém quatro personais e o total informado é quatro. A coluna Código apresenta identificadores não sequenciais, como #1, #2, #4 e #11. |
| Defeito | Sem defeito confirmado |
| Evidências | [Evidências](Evidencias/CT-RF13_Codigos_Personais/README.md) e [Jam](https://jam.dev/c/69330ca9-ef19-4ece-918f-31a460628016). |

### Critérios de aceitação do RF13

1. Total confere com o número de registros considerando a paginação.
2. Identificadores são interpretados conforme sua regra, sem exigir sequência de IDs por suposição.
3. Se a intenção for numerar posições, o rótulo e a numeração deixam isso claro.

### Pontos a confirmar e limites do RF13

Não foi demonstrada uma divergência entre o total e a quantidade listada. A numeração não sequencial por si só não confirma defeito. Confirmar a semântica da coluna Código; quatro linhas e total quatro não sustentam um defeito de quantidade.

---

<a id="rf14"></a>

## RF14 — Preservar a legibilidade das tabelas no tema escuro

| Campo | Descrição |
| --- | --- |
| Requisito de QA | Aplicar cores de texto e de fundo que preservem a legibilidade em ambos os temas. |
| Ator | Usuário autenticado com permissão no módulo. |
| Pré-condições | Sessão autenticada com acesso a SifitBox – Turmas. Página com modalidades e turmas recorrentes cadastradas. |
| Gatilho | Registrar a apresentação das tabelas no tema Claro. Selecionar Escuro. Conferir títulos, nomes, status e ações sobre os fundos das duas tabelas. |
| Caso | [CT-RF14](Cenario_Teste/CT-RF14_Contraste_TemaEscuro.md) |
| Situação observada | Reprovado nas evidências. As áreas de Modalidades e Turmas recorrentes permanecem brancas enquanto diversos textos ficam muito claros, dificultando sua leitura. |
| Defeito | [BUG-007](Relatorio-de-Bugs.md#bug-007) |
| Evidências | [Evidências](Evidencias/CT-RF14_Contraste_TemaEscuro/README.md) e [Jam](https://jam.dev/c/6889db07-bed1-472b-8ec2-00402919cd65). |

### Critérios de aceitação do RF14

1. Nomes e demais textos permanecem legíveis ao alternar o tema.
2. Títulos, filtros, status e ações podem ser identificados nas duas tabelas.
3. Uma conclusão formal de acessibilidade depende de medição de contraste e do padrão acordado.

### Pontos a confirmar e limites do RF14

A observação é visual. Não foi medida a razão de contraste nem realizada uma auditoria formal de acessibilidade. Ajustar as cores e retestar ambos os temas; medir contraste se houver critério formal de acessibilidade definido.

---

<a id="rf15"></a>

## RF15 — Permitir concluir e cancelar a edição de modalidade

| Campo | Descrição |
| --- | --- |
| Requisito de QA | Oferecer ações visíveis de salvar e cancelar e confirmar a atualização. |
| Ator | Usuário autenticado com permissão no módulo. |
| Pré-condições | Sessão autenticada com permissão para editar modalidades. Modalidade de teste com nome, descrição e status conhecidos. |
| Gatilho | Clicar no lápis de uma modalidade. Verificar o preenchimento dos campos e alterar um valor de teste. Localizar e usar a ação de salvar; conferir confirmação e recarregar a lista para validar persistência. |
| Caso | [CT-RF15](Cenario_Teste/CT-RF15_Edicao_Modalidade.md) |
| Situação observada | Reprovado nas evidências. Há ícones de lápis na lista. Ao clicar, os campos superiores são preenchidos para edição, mas não aparece uma ação clara para salvar ou concluir a alteração nos quadros analisados. |
| Defeito | [BUG-008](Relatorio-de-Bugs.md#bug-008) |
| Evidências | [Evidências](Evidencias/CT-RF15_Edicao_Modalidade/README.md) e [Jam](https://jam.dev/c/951efaf8-bf32-44b0-b640-a2935a6b554a). |

### Critérios de aceitação do RF15

1. O lápis carrega os dados do registro selecionado.
2. Salvar e cancelar são ações visíveis e compreensíveis.
3. Salvar persiste os dados; cancelar preserva os valores anteriores.

### Pontos a confirmar e limites do RF15

O título original diz “Sem botão para editar modalidades”, mas o lápis existe. A dificuldade demonstrada é concluir a edição; a gravação não prova ausência de toda alternativa de salvamento. Verificar o fluxo de conclusão da edição e retestar persistência. A evidência reprova a clareza da ação de salvar; não afirma que o ícone de editar inexiste.

---

<a id="rf16"></a>

## RF16 — Comunicar e aplicar a regra de remoção de modalidade

| Campo | Descrição |
| --- | --- |
| Requisito de QA | O nome, o ícone e a confirmação da ação devem informar se o efeito é desativar ou excluir definitivamente. |
| Ator | Usuário autenticado com permissão no módulo. |
| Pré-condições | Sessão autenticada e modalidade descartável na base de teste. Confirmar se a ação realiza exclusão lógica, inativação ou exclusão definitiva e como trata vínculos. |
| Gatilho | Registrar o status e os vínculos da modalidade de teste. Acionar a lixeira conforme a regra e eventual confirmação definida pelo produto. Verificar o estado final e os filtros da lista; não repetir a ação para exigir exclusão física sem regra confirmada. |
| Caso | [CT-RF16](Cenario_Teste/CT-RF16_Exclusao_Modalidade.md) |
| Situação observada | A validar — regra ou contexto pendente. As modalidades passam a aparecer como inativas e continuam na listagem, mesmo após novos cliques. A linha do tempo registra chamadas a /api/sifitbox/modalidades/excluir/1 e recargas das listas com HTTP 200. |
| Defeito | Sem defeito confirmado |
| Evidências | [Evidências](Evidencias/CT-RF16_Exclusao_Modalidade/README.md) e [Jam](https://jam.dev/c/0f55f76a-cd31-4cee-93da-23c13b1ba637). |

### Critérios de aceitação do RF16

1. Nome, ícone e confirmação da ação comunicam seu efeito.
2. O estado final corresponde à regra de inativação ou exclusão acordada.
3. Vínculos e filtros têm tratamento definido; manter registros inativos pode ser comportamento válido.

### Pontos a confirmar e limites do RF16

A inativação pode ser uma exclusão lógica prevista pelo sistema. É necessário confirmar a regra do produto antes de exigir exclusão definitiva. Nenhuma exclusão foi executada nesta revisão. Confirmar a exclusão lógica e a nomenclatura da ação; registrar defeito apenas se houver divergência com a regra definida.

---

<a id="rf17"></a>

## RF17 — Filtrar categorias por código e nome

| Campo | Descrição |
| --- | --- |
| Requisito de QA | Exibir apenas os registros correspondentes aos critérios e restaurar a lista ao limpar. |
| Ator | Usuário autenticado com permissão no módulo. |
| Pré-condições | Sessão autenticada e acesso a Categorias Crossfit. Categorias conhecidas por código e nome para comparação. |
| Gatilho | Pesquisar por códigos conhecidos e conferir o resultado exibido. Limpar a busca com a ação de recarregar/limpar e conferir a lista geral. Pesquisar barbell no campo Nome e comparar as linhas com a base. |
| Caso | [CT-RF17](Cenario_Teste/CT-RF17_Filtros_Categorias.md) |
| Situação observada | Aprovado conforme a gravação. A quantidade de linhas exibidas muda conforme o código informado; a limpeza retorna a lista e a busca por barbell mostra a categoria correspondente. |
| Defeito | Nenhum no fluxo avaliado |
| Evidências | [Evidências](Evidencias/CT-RF17_Filtros_Categorias/README.md) e [Jam](https://jam.dev/c/5e75e423-9c7e-43d7-aade-9b1a32c5e559). |

### Critérios de aceitação do RF17

1. Código restringe ao registro correspondente.
2. Nome restringe conforme a regra de correspondência definida.
3. Limpar a pesquisa restaura a listagem e a contagem.

### Pontos a confirmar e limites do RF17

Resultado válido para os exemplos gravados. Não cobre combinações de filtros, valores inválidos, caracteres especiais ou paginação. Usar como regressão; combinações, conjunto vazio, caracteres especiais e paginação exigem execuções adicionais.

---

<a id="rf18"></a>

## RF18 — Salvar a atualização do nome de categoria

| Campo | Descrição |
| --- | --- |
| Requisito de QA | Persistir a alteração e atualizar a listagem. |
| Ator | Usuário autenticado com permissão no módulo. |
| Pré-condições | Sessão autenticada com permissão de edição. Categoria de teste editável e nome inicial conhecido. |
| Gatilho | Abrir a edição da categoria Barbell teste da base de referência. Alterar o nome para Barbell novo. Clicar em Salvar e conferir o valor atualizado na lista; em nova execução, recarregar para conferir persistência. |
| Caso | [CT-RF18](Cenario_Teste/CT-RF18_Atualizacao_Categoria.md) |
| Situação observada | Aprovado conforme a gravação. O modal fecha e a lista exibe Barbell novo. |
| Defeito | Nenhum no fluxo avaliado |
| Evidências | [Evidências](Evidencias/CT-RF18_Atualizacao_Categoria/README.md) e [Jam](https://jam.dev/c/67664a98-2a4a-4134-91a9-7ca9b8aa9dbd). |

### Critérios de aceitação do RF18

1. O editor carrega a categoria selecionada.
2. Salvar conclui a atualização e retorna à lista com o novo nome.
3. Persistência após recarga ou nova sessão é uma extensão de validação ainda não executada.

### Pontos a confirmar e limites do RF18

A atualização está demonstrada na própria gravação. Não houve novo teste de persistência após outra sessão ou novo login. Usar como regressão; acrescentar recarga e nova consulta para ampliar a verificação de persistência.

---

<a id="rf19"></a>

## RF19 — Excluir categoria permitida ou explicar o impedimento

| Campo | Descrição |
| --- | --- |
| Requisito de QA | Concluir a exclusão permitida ou explicar de forma tratável por que o registro não pode ser excluído. |
| Ator | Usuário autenticado com permissão no módulo. |
| Pré-condições | Sessão autenticada com permissão para excluir categorias. Categoria descartável e vínculos conhecidos; confirmar os impedimentos de exclusão previstos. |
| Gatilho | Acionar a lixeira da categoria de teste. Confirmar a exclusão no diálogo. Conferir retorno visual, status da chamada e presença do registro após a operação. |
| Caso | [CT-RF19](Cenario_Teste/CT-RF19_Exclusao_Categoria.md) |
| Situação observada | Reprovado nas evidências. Após a confirmação, aparece o diálogo “Erro” / “Erro ao deletar categoria”. A categoria permanece na lista. |
| Defeito | [BUG-009](Relatorio-de-Bugs.md#bug-009) |
| Evidências | [Evidências](Evidencias/CT-RF19_Exclusao_Categoria/README.md) e [Jam](https://jam.dev/c/c5c78b3b-2865-4226-836f-bcb0a8fc612f). |

### Critérios de aceitação do RF19

1. Exclusão permitida remove ou altera o registro conforme a regra definida.
2. Impedimentos por vínculos são informados de forma compreensível e sem falha interna genérica.
3. A listagem e o retorno da operação refletem o resultado efetivo.

### Pontos a confirmar e limites do RF19

O erro e o endpoint estão registrados. Sem o corpo completo da resposta, logs do servidor ou banco, a causa do HTTP 500 não foi determinada. Investigar o HTTP 500 com logs do servidor e vínculos da categoria; corrigir e retestar cenários permitido e impedido.

---

<a id="rf20"></a>

## RF20 — Cadastrar e listar uma nova categoria

| Campo | Descrição |
| --- | --- |
| Requisito de QA | Criar a categoria e apresentar o novo registro na listagem. |
| Ator | Usuário autenticado com permissão no módulo. |
| Pré-condições | Sessão autenticada com permissão para cadastrar categorias. Nome de categoria de teste disponível segundo as regras do produto. |
| Gatilho | Clicar em Nova Categoria. Preencher o nome cardio leve na base de referência. Clicar em Salvar e conferir o novo registro e o contador da lista. |
| Caso | [CT-RF20](Cenario_Teste/CT-RF20_Criacao_Categoria.md) |
| Situação observada | Aprovado conforme a gravação. O modal fecha, o contador passa de sete para oito e a lista passa a incluir cardio leve. |
| Defeito | Nenhum no fluxo avaliado |
| Evidências | [Evidências](Evidencias/CT-RF20_Criacao_Categoria/README.md) e [Jam](https://jam.dev/c/b48ab94e-517d-48d6-8e46-70b18c033b8b). |

### Critérios de aceitação do RF20

1. O formulário permite informar um nome válido.
2. Salvar cria o registro e fecha o formulário com retorno de sucesso.
3. A lista exibe a nova categoria e o total atualizado.

### Pontos a confirmar e limites do RF20

O teste demonstra criação no cenário gravado. Não cobre campos vazios, duplicidade ou validações de tamanho. Usar como regressão; campos vazios, nomes duplicados e limites de tamanho permanecem fora do cenário gravado.

---

<a id="rf21"></a>

## RF21 — Cadastrar avaliação ou informar validação específica

| Campo | Descrição |
| --- | --- |
| Requisito de QA | Cadastrar uma avaliação com dados válidos e apresentar confirmação; tratar dados recusados sem erro interno genérico. |
| Ator / pré-condições | Usuário autenticado com permissão; aluno existente, personal habilitado e data/hora permitidas no fluxo válido. |
| Gatilho | Clicar em Salvar no formulário Cadastrar Avaliação. |
| Caso | [CT-RF21](Cenario_Teste/CT-RF21_Cadastro_Avaliacao.md) |
| Situação observada | Reprovado: POST /api/avaliacao/adicionar-agendamento/1 retorna HTTP 500 e a interface mostra “Erro ao cadastrar Avaliação.”. |
| Defeito | [BUG-010](Relatorio-de-Bugs.md#bug-010), aberto; reteste pendente. |
| Evidências | [Evidências](Evidencias/CT-RF21_Cadastro_Avaliacao/README.md) e [Jam](https://jam.dev/c/2e5eca1f-7cd2-4ee3-854b-02ef4635955a). |

### Critérios de aceitação do RF21

1. Dados válidos geram cadastro confirmado e avaliação consultável na listagem.
2. Aluno inválido, vínculo incompleto ou data/hora proibida recebem validação específica, sem HTTP 500.
3. Tentativas rejeitadas não deixam registros parciais; uma tentativa válida cria um agendamento.
4. A interface permite corrigir os dados após uma rejeição.

### Pontos a confirmar e limites do RF21

O aluno 3423 foi digitado manualmente sem confirmação pela busca. A avaliação foi solicitada para 15/11/2026 às 06:00, antes da tentativa de aproximadamente 15:08. Confirmar existência/elegibilidade do aluno, vínculos, contrato da data e regra de agendamento retroativo. Esses pontos não comprovam a causa do HTTP 500. A referência de QA foi elaborada a partir da evidência e depende de confirmação de produto; não foi fornecida especificação formal. Causa raiz e persistência não confirmadas; sem nova execução.

---

<a id="rf22"></a>

## RF22 — Permitir informar o código do exercício conforme a regra

| Campo | Descrição |
| --- | --- |
| Requisito de QA | Quando editável, o campo Código deve aceitar e manter um código válido e permitir sua correção. |
| Ator | Usuário autenticado com permissão em Exercícios. |
| Pré-condições | Confirmar se o código é manual ou automático e quais operações permitem edição. Preparar dados de teste autorizados. |
| Gatilho | Abrir o formulário Exercício com permissão adequada. |
| Caso | [CT-RF22](Cenario_Teste/CT-RF22_Digitacao_Codigo_Exercicio.md) |
| Situação observada | Reprovado conforme o relato; reprodução independente pendente. O testador relata não conseguir digitar o código. A imagem inicial confirma o campo Código no formulário Exercício; a reprodução integral, as teclas e o foco não foram confirmados. |
| Defeito | [BUG-011](Relatorio-de-Bugs.md#bug-011), em triagem |
| Evidências | [Jam](https://jam.dev/c/2696db03-0a18-4c39-a75d-4987a43c04f0) e relato do testador. |

### Critérios de aceitação do RF22

1. A regra de preenchimento manual ou geração automática está confirmada.
2. Quando editável, o campo recebe foco, aceita e mantém um código válido.
3. O usuário pode apagar e corrigir o valor; restrições são explicadas.

### Pontos a confirmar e limites do RF22

Não foram confirmadas a operação de criação/edição, a sequência de teclas ou a causa. A classificação se apoia no relato e na imagem inicial, sem análise de rede ou console. Confirmar a regra, reproduzir o impedimento e retestar o campo após correção. Os critérios são referências de QA, sem aprovação formal de produto ou nova execução.

---

<a id="rf23"></a>

## RF23 — Exclusão de exercício

| Campo | Descrição |
| --- | --- |
| Requisito de QA | O sistema deve remover o exercício permitido da biblioteca e atualizar os totais. Se houver impedimento, deve explicá-lo sem indicar sucesso indevido. |
| Ator | Usuário autenticado com permissão em Exercícios. |
| Pré-condições | Exercício de teste existente, sem impedimento conhecido para exclusão. Preparar dados de teste autorizados. |
| Gatilho | Identificar o exercício de teste e registrar o total da biblioteca e do grupo. |
| Caso | [CT-RF23](Cenario_Teste/CT-RF23_Exclusao_Exercicio.md) |
| Situação observada | Aprovado no trecho consultado. No quadro de aproximadamente 0:02, a biblioteca apresenta total 11 e o exercício Levantamento de Peso. No quadro final, em aproximadamente 0:06, esse registro não aparece e o total é 10. A lista continua contendo Levantamento de Peso 02, registro distinto. |
| Defeito | Sem defeito confirmado |
| Evidências | [Jam](https://jam.dev/c/32adfca3-489f-4a4b-a08d-933c1d1a3c32) e [Evidências](Evidencias/CT-RF23_Exclusao_Exercicio/README.md). |

### Critérios de aceitação do RF23

1. O registro selecionado deixa de aparecer na biblioteca.
2. O total diminui em uma unidade e os demais exercícios são preservados.
3. Uma restrição de exclusão, quando aplicável, é apresentada claramente.

### Pontos a confirmar e limites do RF23

Não foram confirmados o diálogo de confirmação, a persistência após recarregar ou os efeitos sobre fichas de treino vinculadas. Manter como regressão. Em nova execução, recarregar a página para conferir persistência e testar separadamente as regras para exercícios vinculados. Os critérios são referências de QA, sem aprovação formal de produto ou nova execução.

---

<a id="rf24"></a>

## RF24 — Edição de exercício aumenta o total e mantém duas entradas

| Campo | Descrição |
| --- | --- |
| Requisito de QA | Salvar a edição deve atualizar o mesmo exercício, sem criar um registro adicional e sem aumentar o total da biblioteca. |
| Ator | Usuário autenticado com permissão em Exercícios. |
| Pré-condições | Exercício de teste existente, com identificador e nome original registrados antes da edição. Preparar dados de teste autorizados. |
| Gatilho | Registrar identificador, nome e total do exercício de teste. |
| Caso | [CT-RF24](Cenario_Teste/CT-RF24_Edicao_Exercicio.md) |
| Situação observada | Reprovado no trecho consultado; confirmar operação e identidade dos registros na reprodução. O Jam está identificado como teste de edição. Nos quadros intermediários, o formulário Exercício está aberto com código 16, o nome é preenchido e a biblioteca ao fundo indica total 10. No quadro final, o formulário fecha, o total é 11 e a lista contém Levantamento de Peso e Levantamento de Peso 02. O aumento e a coexistência dos nomes divergem do resultado esperado para uma edição. |
| Defeito | [BUG-012](Relatorio-de-Bugs.md#bug-012), em triagem |
| Evidências | [Jam](https://jam.dev/c/073f70d6-4052-4e0f-a4bb-e9f37305d618) e [Evidências](Evidencias/CT-RF24_Edicao_Exercicio/README.md). |

### Critérios de aceitação do RF24

1. A ação de edição abre o exercício correto com seus dados atuais.
2. Salvar altera o nome do mesmo identificador.
3. O total permanece igual e não surge um registro adicional.
4. Os dados não alterados permanecem associados ao exercício.

### Pontos a confirmar e limites do RF24

O acionamento inicial da edição e os identificadores das duas entradas não foram confirmados. A classificação considera o propósito declarado do Jam e a divergência visual; se a operação tiver sido criação, reavaliar a conclusão. Reproduzir a partir da ação explícita de edição e comparar os identificadores antes e depois. Investigar eventual envio para criação como hipótese, sem atribuir causa técnica antes de verificar código e contrato da API. Os critérios são referências de QA, sem aprovação formal de produto ou nova execução.

---

<a id="rf25"></a>

## RF25 — Envio de exercício com imagem

| Campo | Descrição |
| --- | --- |
| Requisito de QA | O sistema deve cadastrar o exercício, atualizar a biblioteca e manter a imagem vinculada ao registro, disponível após reabrir o cadastro. |
| Ator | Usuário autenticado com permissão em Exercícios. |
| Pré-condições | Imagem de teste disponível, em formato e tamanho aceitos pela interface, sem dados pessoais. Preparar dados de teste autorizados. |
| Gatilho | Registrar o total inicial da biblioteca e abrir o formulário de novo exercício. |
| Caso | [CT-RF25](Cenario_Teste/CT-RF25_Envio_Exercicio_Imagem.md) |
| Situação observada | A validar — criação visível; persistência e associação da imagem não confirmadas. O quadro inicial consultado mostra o formulário Exercício preenchido com nome braço forte e uma miniatura na seção Imagem; a biblioteca ao fundo indica total 9. O quadro final mostra o formulário fechado, braço forte na lista e total 10. Esses quadros sustentam a criação com imagem selecionada, mas não demonstram a reabertura ou a visualização da imagem salva. |
| Defeito | Sem defeito confirmado |
| Evidências | [Jam](https://jam.dev/c/25c37a9b-e9bd-4e0c-adf1-4da528ae1d58) e [Evidências](Evidencias/CT-RF25_Envio_Exercicio_Imagem/README.md). |

### Critérios de aceitação do RF25

1. Uma imagem válida pode ser selecionada e sua prévia aparece.
2. Salvar cria um único exercício e atualiza o total.
3. Reabrir o cadastro exibe a imagem correspondente ao arquivo enviado.
4. A associação permanece após recarregar a página.

### Pontos a confirmar e limites do RF25

Não foram confirmados nome, formato, tamanho ou conteúdo integral do arquivo, nem a persistência da imagem, sua recuperação ou a ausência de duplicação após nova submissão. Reabrir o exercício criado e conferir a imagem salva. Testar formatos e tamanhos inválidos em casos separados; essas variações não recebem resultado nesta análise. Os critérios são referências de QA, sem aprovação formal de produto ou nova execução.

---

<a id="rf26"></a>

## RF26 — Validar campos obrigatórios do exercício

| Campo | Descrição |
| --- | --- |
| Requisito de QA | O sistema deve impedir o cadastro de exercício com campos obrigatórios vazios e indicar claramente quais dados precisam ser preenchidos. |
| Ator | Usuário autenticado com permissão em Exercícios. |
| Pré-condições | Formulário de novo exercício aberto, sem preenchimento dos campos obrigatórios. |
| Gatilho | Clicar em Salvar com os campos obrigatórios vazios. |
| Caso | [CT-RF26](Cenario_Teste/CT-RF26_Exercicio_Campos_Vazios.md) |
| Situação observada | Reprovado conforme a gravação. O formulário permanece aberto sem mensagem, destaque ou orientação de validação visível. A evidência não demonstra criação de registro vazio. |
| Defeito | [BUG-013](Relatorio-de-Bugs.md#bug-013), em triagem |
| Evidências | [Jam](https://jam.dev/c/bc07ca5f-d3a9-45f6-84cb-12c0b562a211). |

### Critérios de aceitação do RF26

1. O envio com campos obrigatórios vazios é bloqueado.
2. Cada campo inválido recebe indicação visual e textual compreensível.
3. O foco é direcionado ao primeiro campo que exige correção.
4. Nenhum registro vazio é criado, inclusive após recarregar a página.

### Pontos a confirmar e limites do RF26

A gravação não confirma resposta da API, persistência ou comportamento após recarregar a biblioteca. Reproduzir com total inicial conhecido, registrar as mensagens e confirmar que nenhum exercício vazio foi criado. A causa técnica não foi determinada.

---

<a id="rf27"></a>

## RF27 — Rejeitar vídeo no campo de imagem com feedback

| Campo | Descrição |
| --- | --- |
| Requisito de QA | O campo Imagem deve rejeitar arquivos de vídeo e informar os formatos e limites aceitos, sem descartar os demais dados do formulário. |
| Ator | Usuário autenticado com permissão em Exercícios. |
| Pré-condições | Formulário aberto e arquivo de vídeo de teste disponível, com extensão, MIME e tamanho conhecidos. |
| Gatilho | Selecionar o vídeo no campo Imagem. |
| Caso | [CT-RF27](Cenario_Teste/CT-RF27_Video_Campo_Imagem.md) |
| Situação observada | Reprovado conforme a gravação. O arquivo não aparece anexado, porém não há mensagem visível explicando a rejeição ou os formatos permitidos. |
| Defeito | [BUG-014](Relatorio-de-Bugs.md#bug-014), em triagem |
| Evidências | [Jam](https://jam.dev/c/00740108-9a7d-4151-8723-171c89635567). |

### Critérios de aceitação do RF27

1. Arquivos de vídeo não são aceitos como imagem.
2. A mensagem identifica o tipo incompatível e informa formatos e tamanho máximo aceitos.
3. O formulário conserva os demais dados e permanece utilizável.
4. Nenhum upload ou vínculo indevido é persistido.

### Pontos a confirmar e limites do RF27

Nome, extensão, MIME, tamanho do arquivo e resposta da API não ficaram confirmados. Repetir com arquivo controlado, observar cliente e rede e verificar ausência de vínculo após salvar e reabrir. A causa técnica não foi determinada.

---

<a id="rf28"></a>

## RF28 — Rejeitar imagem no campo de vídeo com feedback

| Campo | Descrição |
| --- | --- |
| Requisito de QA | O campo Vídeo deve rejeitar arquivos de imagem e informar os formatos e limites aceitos, sem descartar os demais dados do formulário. |
| Ator | Usuário autenticado com permissão em Exercícios. |
| Pré-condições | Formulário aberto e arquivo de imagem de teste disponível, com extensão, MIME e tamanho conhecidos. |
| Gatilho | Selecionar a imagem no campo Vídeo. |
| Caso | [CT-RF28](Cenario_Teste/CT-RF28_Imagem_Campo_Video.md) |
| Situação observada | Reprovado conforme a gravação. O arquivo não aparece anexado, porém não há mensagem visível explicando a rejeição ou os formatos permitidos. |
| Defeito | [BUG-015](Relatorio-de-Bugs.md#bug-015), em triagem |
| Evidências | [Jam](https://jam.dev/c/be9437a4-4fe9-4756-a2af-6777d3f43e25). |

### Critérios de aceitação do RF28

1. Arquivos de imagem não são aceitos como vídeo.
2. A mensagem identifica o tipo incompatível e informa formatos e tamanho máximo aceitos.
3. O formulário conserva os demais dados e permanece utilizável.
4. Nenhum upload ou vínculo indevido é persistido.

### Pontos a confirmar e limites do RF28

Nome, extensão, MIME, tamanho do arquivo e resposta da API não ficaram confirmados. Repetir com arquivo controlado, observar cliente e rede e verificar ausência de vínculo após salvar e reabrir. A causa técnica não foi determinada.

---

## RF29 — Excluir grupo muscular ou explicar o impedimento

| Campo | Descrição |
| --- | --- |
| Requisito de QA | A exclusão de um grupo muscular deve ser concluída quando permitida, removendo o registro da listagem e atualizando os contadores; quando houver impedimento de regra, o sistema deve informá-lo de forma específica e tratável, sem erro interno do servidor. |
| Ator | Usuário autenticado com permissão em Grupos Musculares. |
| Pré-condições | Listagem carregada, registro de teste conhecido e vínculos desse registro identificados antes da execução. |
| Gatilho | Acionar a ação de exclusão na linha do registro e confirmar no diálogo "Deseja deletar o Grupo?". |
| Caso | [CT-RF29](Cenario_Teste/CT-RF29_Exclusao_GrupoMuscular.md) |
| Situação observada | Reprovado nas evidências. Duas tentativas de exclusão retornam HTTP 500 com o corpo "Erro interno inesperado."; a interface apresenta o diálogo "Erro ao deletar Grupo" e o registro permanece na listagem. |
| Defeito | [BUG-016](Relatorio-de-Bugs.md#bug-016), em triagem |
| Evidências | [Jam](https://jam.dev/c/98008390-0040-475e-ba7b-7f1e72cc0b2e). |

### Critérios de aceitação do RF29

1. A ação de exclusão apresenta confirmação explícita antes de efetivar a operação.
2. A exclusão permitida remove o registro da listagem e atualiza os contadores do resumo.
3. O impedimento de regra é comunicado com mensagem específica, sem erro interno do servidor.
4. Nenhum cenário de exclusão retorna HTTP 500.
5. O resultado se mantém após recarga da página.

### Pontos a confirmar e limites do RF29

Não foram consultados logs do servidor, corpo completo da resposta além dos 64 bytes retornados nem o banco de dados; a causa do HTTP 500 permanece indeterminada. Não foi confirmado se o registro permanece íntegro após as duas tentativas enviadas para o mesmo recurso. O cenário de exclusão com impedimento de regra não foi exercitado, de modo que não se sabe se o sistema distingue impedimento de falha. A mensagem "Erro ao deletar Grupo" é genérica e não informa a causa ao usuário.

---

## RF30 — Exibir as imagens cadastradas dos grupos musculares

| Campo | Descrição |
| --- | --- |
| Requisito de QA | A listagem deve apresentar a imagem de cada grupo muscular que a possua, com as requisições dos arquivos concluídas com sucesso, e adotar um estado neutro definido para registros sem imagem. |
| Ator | Usuário autenticado com acesso a Grupos Musculares. |
| Pré-condições | Listagem carregada e caminho esperado dos arquivos de imagem conhecido. |
| Gatilho | Carregar a tela Grupos Musculares, aplicar filtros ou alternar o tema, situações em que a listagem é recarregada. |
| Caso | [CT-RF30](Cenario_Teste/CT-RF30_Imagens_GruposMusculares.md) |
| Situação observada | Reprovado nas evidências. As requisições dos quatro arquivos de imagem retornam HTTP 422 durante toda a gravação, com ocorrências de `net::ERR_ABORTED`, e a coluna IMAGEM apresenta o ícone de imagem quebrada em todas as linhas, nos dois temas e com ou sem filtro. |
| Defeito | [BUG-017](Relatorio-de-Bugs.md#bug-017), em triagem |
| Evidências | [Jam](https://jam.dev/c/98008390-0040-475e-ba7b-7f1e72cc0b2e). |

### Critérios de aceitação do RF30

1. Cada grupo muscular com imagem cadastrada apresenta a imagem na coluna IMAGEM.
2. As requisições dos arquivos de imagem são concluídas com sucesso.
3. Registros sem imagem apresentam um estado neutro definido pelo produto, e não um ícone de arquivo quebrado.
4. O comportamento se mantém após busca, troca de página e troca de tema.

### Pontos a confirmar e limites do RF30

Não foi verificada a existência dos arquivos em `/img/grupos_musculares/imagens/`, nem o conteúdo do campo de imagem de cada registro no banco, nem o resultado do acesso direto às URLs fora da página. O código 422 não é o retorno usual para arquivo ausente ou sem permissão, o que sugere tratamento por aplicação em vez de entrega direta de arquivo estático; essa é uma hipótese a confirmar. Os status foram lidos na coluna Status da lista de rede, porque o painel de detalhe da ferramenta repetiu cabeçalhos e identificadores entre linhas distintas. Resta confirmar também o comportamento para registros criados sem imagem informada, que passam a ter um arquivo requisitado.

---

## RF31 — Cadastrar e listar um grupo muscular

| Campo | Descrição |
| --- | --- |
| Requisito de QA | O sistema deve permitir cadastrar um grupo muscular, apresentá-lo na listagem e atualizar os contadores do resumo, mantendo a contagem do rodapé coerente com os registros exibidos. |
| Ator | Usuário autenticado com permissão em Grupos Musculares. |
| Pré-condições | Nome de grupo muscular de teste disponível e estado inicial da listagem e dos contadores registrado. |
| Gatilho | Abrir o formulário de inclusão, informar nome e tipo de membro e confirmar em "Salvar". |
| Caso | [CT-RF31](Cenario_Teste/CT-RF31_Cadastro_GrupoMuscular.md) |
| Situação observada | Aprovado conforme a gravação. O registro "Tríceps" foi criado com o código 6 e tipo "Superiores"; a listagem passou de três para quatro registros e os cartões de Grupos cadastrados e Superiores acompanharam a inclusão. |
| Defeito | Nenhum no fluxo avaliado |
| Evidências | [Jam](https://jam.dev/c/98008390-0040-475e-ba7b-7f1e72cc0b2e). |

### Critérios de aceitação do RF31

1. O formulário permite informar nome e tipo de membro.
2. O envio cria o registro e encerra o formulário.
3. A listagem passa a exibir o novo grupo muscular, com o rodapé de contagem coerente.
4. Os cartões de resumo refletem a inclusão, inclusive o cartão do tipo de membro escolhido.
5. O registro permanece após recarga da página.

### Pontos a confirmar e limites do RF31

A cronologia não registra uma requisição de criação com o respectivo código de status; a conclusão apoia-se na comparação entre os quadros de 0:48 e 0:55. A persistência após recarga não foi verificada, nem houve consulta ao banco. Permanecem fora do cenário gravado campos obrigatórios em branco, nomes duplicados, limites de tamanho, caracteres especiais e cancelamento do formulário. O campo Código estava em branco no envio e o sistema atribuiu o código 6; a atribuição automática é compatível com os códigos não sequenciais da listagem, mas a regra não foi confirmada, nem foi testado o envio com código informado manualmente. O formulário foi enviado sem imagem e, ainda assim, passou a existir um arquivo requisitado para o novo registro, situação tratada no [RF30](#rf30).

---

## RF32 — Alterar o tipo de membro de um grupo muscular

| Campo | Descrição |
| --- | --- |
| Requisito de QA | O sistema deve permitir alterar o tipo de membro de um grupo muscular existente, refletir a mudança na listagem e recalcular os cartões de resumo, mantendo a soma dos tipos igual ao total de registros. |
| Ator | Usuário autenticado com permissão em Grupos Musculares. |
| Pré-condições | Registro de teste com tipo de membro conhecido e estado inicial dos cartões de resumo registrado. |
| Gatilho | Abrir a edição do registro, selecionar outro tipo de membro e confirmar em "Salvar". |
| Caso | [CT-RF32](Cenario_Teste/CT-RF32_Edicao_TipoMembro.md) |
| Situação observada | Aprovado conforme a gravação. O registro de código 1 passou de "Superiores" para "Inferiores" e os cartões acompanharam, de Superiores 3 / Inferiores 1 para Superiores 2 / Inferiores 2, com o total constante em quatro. |
| Defeito | Nenhum no fluxo avaliado |
| Evidências | [Jam](https://jam.dev/c/98008390-0040-475e-ba7b-7f1e72cc0b2e). |

### Critérios de aceitação do RF32

1. O formulário de edição abre preenchido com os dados atuais do registro.
2. A alteração do tipo de membro é persistida e exibida na listagem.
3. Os cartões de resumo são recalculados e a soma dos tipos corresponde ao total de registros.
4. O resultado se mantém após recarga da página.

### Pontos a confirmar e limites do RF32

A cronologia não registra uma requisição de atualização com o respectivo código de status; a conclusão apoia-se na comparação entre os quadros de 1:02 e 1:08 e nos cartões de resumo. O controle que abre o formulário de edição não foi identificado com certeza na cronologia. A persistência após recarga não foi verificada, nem houve consulta ao banco. Permanecem fora do cenário gravado o cancelamento da edição, a alteração de nome, a alteração simultânea de vários campos e a validação de campos obrigatórios.

A edição recebeu um arquivo de imagem, com miniatura exibida corretamente na pré-visualização, mas após o envio o registro continua sem imagem na listagem e o arquivo requisitado mantém o mesmo nome anterior. Isso é compatível tanto com sobrescrita sob o mesmo nome quanto com não persistência do envio, e não distingue as duas hipóteses, já que todas as requisições de imagem retornam HTTP 422 conforme o [RF30](#rf30).

---

## RF33 — Filtrar a listagem de grupos musculares por código e tipo

| Campo | Descrição |
| --- | --- |
| Requisito de QA | A busca deve apresentar apenas os registros que atendam aos critérios informados, com a contagem do rodapé correspondente ao conjunto exibido, e informar explicitamente quando não houver correspondência. |
| Ator | Usuário autenticado com acesso a Grupos Musculares. |
| Pré-condições | Base conhecida, com a quantidade de registros por tipo de membro registrada e ao menos um tipo sem registros associados. |
| Gatilho | Informar código, selecionar tipo de membro e acionar a busca. |
| Caso | [CT-RF33](Cenario_Teste/CT-RF33_Filtros_GruposMusculares.md) |
| Situação observada | Aprovado conforme a gravação. O filtro por tipo sem registros apresenta "Nenhum grupo muscular encontrado" e rodapé "Mostrando 0 a 0 de 0 grupos"; os filtros por tipo e por código retornam o registro correspondente, com rodapé coerente. |
| Defeito | Nenhum no fluxo avaliado |
| Evidências | [Jam](https://jam.dev/c/98008390-0040-475e-ba7b-7f1e72cc0b2e). |

### Critérios de aceitação do RF33

1. A busca por tipo de membro retorna apenas registros daquele tipo.
2. A busca por código retorna o registro correspondente.
3. A contagem do rodapé corresponde aos registros apresentados.
4. A ausência de correspondência apresenta mensagem explícita, e não uma listagem vazia sem aviso.
5. A limpeza dos critérios restaura a listagem completa.

### Pontos a confirmar e limites do RF33

A lógica de combinação dos critérios não ficou demonstrada. No quadro de 2:00 o código e o tipo de membro estão preenchidos ao mesmo tempo e o resultado atende aos dois, porém o único registro daquele código também é daquele tipo, de modo que o mesmo resultado seria obtido com apenas um dos critérios. A verificação exige um caso em que os critérios se contradigam, cujo retorno esperado é o conjunto vazio; esse caso não foi exercitado. Esse ponto é relevante porque filtros combinados são o aspecto reprovado no [RF03](#rf03--pesquisar-clientes-com-filtros-combinados).

Permanecem fora do cenário gravado a busca por nome, código inexistente ou inválido, caracteres especiais, resultados com mais de uma linha, paginação do resultado filtrado e limpeza dos critérios. Os cartões de resumo não acompanham o filtro e mantêm o total da base, enquanto o rodapé acompanha o conjunto filtrado; o comportamento é coerente entre os quadros conferidos, mas o contrato de cada indicador não foi fornecido, do mesmo modo que no [RF11](#rf11).

---

<a id="rf35"></a>

## RF35 — Cadastrar objetivo de treino ou informar validação específica

| Campo | Descrição |
| --- | --- |
| Requisito de QA | O cadastro de um objetivo de treino deve ser confirmado e apresentado na listagem quando os dados forem válidos; quando algum dado for recusado, o sistema deve informar a validação específica e permitir a correção, sem erro interno do servidor. |
| Ator | Usuário autenticado com acesso a Objetivos Treino. |
| Pré-condições | Listagem carregada e estado inicial conhecido (registros e cartões Objetivos, Exibidos e Com Descrição); nome de teste disponível; regra do campo Código e da descrição confirmada com o produto. |
| Gatilho | Clicar em Novo Objetivo, informar nome e descrição e clicar em Salvar. |
| Caso | [CT-RF35](Cenario_Teste/CT-RF35_Cadastro_Objetivo_Treino.md) |
| Situação observada | Reprovado nas evidências. Duas ocorrências de `POST /api/objetivo-treino/salvar/1` retornam HTTP 500; a interface apresenta o diálogo "Erro ao salvar objetivo" e a listagem permanece sem registros. |
| Defeito | [BUG-018](Relatorio-de-Bugs.md#bug-018), em triagem |
| Evidências | [Jam](https://jam.dev/c/1d474477-2411-4a81-b85c-74207402b783) e [Evidências](Evidencias/CT-RF35_Cadastro_Objetivo_Treino/README.md). |

### Critérios de aceitação do RF35

1. O formulário permite informar nome e descrição e oferece as ações Salvar e Cancelar.
2. O envio válido cria o registro, encerra o formulário e confirma o resultado ao usuário.
3. A listagem passa a exibir o novo objetivo e os cartões de resumo refletem a inclusão.
4. Um dado recusado recebe mensagem específica, sem HTTP 500, e o formulário permite a correção.
5. Um único clique em Salvar gera uma única gravação, sem registros duplicados ou parciais.
6. O registro permanece após recarga da página.

### Pontos a confirmar e limites do RF35

Os corpos da requisição e da resposta não foram capturados pelo Jam; não é possível afirmar o payload enviado nem a mensagem retornada, e a causa do HTTP 500 permanece indeterminada. A descrição utilizada continha caracteres especiais (`#@`), o que orienta a verificação, sem comprovar a causa. Não foi confirmada a persistência de registros parciais nem a razão de duas ocorrências de HTTP 500 para uma única ação de salvar registrada.

O campo Código permaneceu vazio nos quadros apesar da digitação registrada; a evidência não distingue um código atribuído automaticamente (como se interpretou no [RF31](#rf31)) do impedimento relatado no [RF22](#rf22). A base estava vazia, de modo que os filtros por código e nome não puderam ser avaliados, e a mensagem "Nenhum objetivo cadastrado" também aparece com filtro aplicado; a distinção entre "nenhum cadastrado" e "nenhum encontrado" depende de confirmação do produto, como no [RF33](#rf33).

---

## 🔗 Rastreabilidade

| Requisito | Cenário / caso | Defeito | Resultado | Evidências |
| --- | --- | --- | --- | --- |
| RF01 | [Cenário 1 / CT-RF01](Cenario_Teste/CT-RF01_Esqueci-senha.md) | [BUG-001](Relatorio-de-Bugs.md#bug-001--link-esqueci-minha-senha-não-executa-nenhuma-ação) | Reprovado nas evidências; reteste pendente | [Drive](https://drive.google.com/file/d/1f6AqYunchDH4R9Yw1JpbyX9x28UQGcbo/view?usp=sharing) e [Jam](https://jam.dev/c/0273b203-b999-493d-9919-2d143bc13301) |
| RF02 | [Cenário 2 / CT-RF02_ERRO](Cenario_Teste/CT-RF02_ERRO.md) | [BUG-002](Relatorio-de-Bugs.md#bug-002--perfil-com-dados-fictícios-campos-ausentes-e-layout-desconfigurado) | Reprovado nas evidências; reteste pendente | [Captura](Evidencias/CT-RF02_ERRO/erro-na-tela.png), [HTML](Evidencias/CT-RF02_ERRO/recorte-dom.html) e [Jam](https://jam.dev/c/c61241d5-bff5-4a0a-9684-991318f9b51c) |
| RF03 | [Cenário 3 / CT-RF03](Cenario_Teste/CT-RF03_FILTRO_TelaClientes.md) | [BUG-003](Relatorio-de-Bugs.md#bug-003--filtros-combinados-da-página-clientes-não-restringem-a-listagem) | Reprovado conforme o relato; reteste pendente | [Índice e limites](Evidencias/CT-RF03_Filtros_Clientes/README.md), [captura 1](Evidencias/CT-RF03_Filtros_Clientes/filtros-clientes-01.png), [captura 2](Evidencias/CT-RF03_Filtros_Clientes/filtros-clientes-02.png) e [Jam](https://jam.dev/c/657627ec-e7e2-455d-a505-9b2a26f44bf1) |
| RF04 | [Cenário 4 / CT-RF04_loginComSucesso](Cenario_Teste/CT-RF04_loginComSucesso.md) | Nenhum identificado no fluxo avaliado | Aprovado conforme a gravação | [Resumo das evidências](Evidencias/CT-RF04_loginComSucesso/README.md) e [Jam](https://jam.dev/c/5e4a28be-4e80-43d3-9587-1b113723cc38) |
| RF05 | [CT-RF05](Cenario_Teste/CT-RF05_Login_SenhaIncorreta.md) | Nenhum no fluxo avaliado | Aprovado conforme a gravação | [Evidências](Evidencias/CT-RF05_Login_SenhaIncorreta/README.md) e [Jam](https://jam.dev/c/75f16436-7201-4de0-b191-1c4d0d63bfe8) |
| RF06 | [CT-RF06](Cenario_Teste/CT-RF06_Login_UsuarioInexistente.md) | Nenhum no fluxo avaliado | Aprovado conforme a gravação | [Evidências](Evidencias/CT-RF06_Login_UsuarioInexistente/README.md) e [Jam](https://jam.dev/c/b184e875-2cb1-4a01-b4dd-bc85b3741ff6) |
| RF07 | [CT-RF07](Cenario_Teste/CT-RF07_Exportacao_Financeiro.md) | [BUG-004](Relatorio-de-Bugs.md#bug-004) | Reprovado nas evidências | [Evidências](Evidencias/CT-RF07_Exportacao_Financeiro/README.md) e [Jam](https://jam.dev/c/1084cb18-cb3d-4b85-9c2f-ee431b59a06b) |
| RF08 | [CT-RF08](Cenario_Teste/CT-RF08_Calculo_Cobranca.md) | Sem defeito confirmado | A validar — regra ou contexto pendente | [Evidências](Evidencias/CT-RF08_Calculo_Cobranca/README.md) e [Jam](https://jam.dev/c/79b712ae-d9e0-4600-862f-fd3a278285ff) |
| RF09 | [CT-RF09](Cenario_Teste/CT-RF09_Contagem_Mensalidades.md) | [BUG-005](Relatorio-de-Bugs.md#bug-005) | Reprovado nas evidências | [Evidências](Evidencias/CT-RF09_Contagem_Mensalidades/README.md) e [Jam](https://jam.dev/c/1874d0b3-5c7c-4f28-85be-91750e20cbe1) |
| RF10 | [CT-RF10](Cenario_Teste/CT-RF10_Filtro_Mensalidades.md) | [BUG-005](Relatorio-de-Bugs.md#bug-005) | Reprovado nas evidências | [Evidências](Evidencias/CT-RF10_Filtro_Mensalidades/README.md) e [Jam](https://jam.dev/c/3f78cf16-2c3b-48bc-8622-23b829debbec) |
| RF11 | [CT-RF11](Cenario_Teste/CT-RF11_Metricas_Financeiro.md) | Sem defeito confirmado | A validar — regra ou contexto pendente | [Evidências](Evidencias/CT-RF11_Metricas_Financeiro/README.md) e [Jam](https://jam.dev/c/4491c9e7-7e00-4063-91ce-8683e316df06) |
| RF12 | [CT-RF12](Cenario_Teste/CT-RF12_Periodo_Dashboard.md) | [BUG-006](Relatorio-de-Bugs.md#bug-006) | Reprovado nas evidências | [Evidências](Evidencias/CT-RF12_Periodo_Dashboard/README.md) e [Jam](https://jam.dev/c/93165ba3-3bfe-4dd5-9379-ab8db2d686ba) |
| RF13 | [CT-RF13](Cenario_Teste/CT-RF13_Codigos_Personais.md) | Sem defeito confirmado | A validar — regra ou contexto pendente | [Evidências](Evidencias/CT-RF13_Codigos_Personais/README.md) e [Jam](https://jam.dev/c/69330ca9-ef19-4ece-918f-31a460628016) |
| RF14 | [CT-RF14](Cenario_Teste/CT-RF14_Contraste_TemaEscuro.md) | [BUG-007](Relatorio-de-Bugs.md#bug-007) | Reprovado nas evidências | [Evidências](Evidencias/CT-RF14_Contraste_TemaEscuro/README.md) e [Jam](https://jam.dev/c/6889db07-bed1-472b-8ec2-00402919cd65) |
| RF15 | [CT-RF15](Cenario_Teste/CT-RF15_Edicao_Modalidade.md) | [BUG-008](Relatorio-de-Bugs.md#bug-008) | Reprovado nas evidências | [Evidências](Evidencias/CT-RF15_Edicao_Modalidade/README.md) e [Jam](https://jam.dev/c/951efaf8-bf32-44b0-b640-a2935a6b554a) |
| RF16 | [CT-RF16](Cenario_Teste/CT-RF16_Exclusao_Modalidade.md) | Sem defeito confirmado | A validar — regra ou contexto pendente | [Evidências](Evidencias/CT-RF16_Exclusao_Modalidade/README.md) e [Jam](https://jam.dev/c/0f55f76a-cd31-4cee-93da-23c13b1ba637) |
| RF17 | [CT-RF17](Cenario_Teste/CT-RF17_Filtros_Categorias.md) | Nenhum no fluxo avaliado | Aprovado conforme a gravação | [Evidências](Evidencias/CT-RF17_Filtros_Categorias/README.md) e [Jam](https://jam.dev/c/5e75e423-9c7e-43d7-aade-9b1a32c5e559) |
| RF18 | [CT-RF18](Cenario_Teste/CT-RF18_Atualizacao_Categoria.md) | Nenhum no fluxo avaliado | Aprovado conforme a gravação | [Evidências](Evidencias/CT-RF18_Atualizacao_Categoria/README.md) e [Jam](https://jam.dev/c/67664a98-2a4a-4134-91a9-7ca9b8aa9dbd) |
| RF19 | [CT-RF19](Cenario_Teste/CT-RF19_Exclusao_Categoria.md) | [BUG-009](Relatorio-de-Bugs.md#bug-009) | Reprovado nas evidências | [Evidências](Evidencias/CT-RF19_Exclusao_Categoria/README.md) e [Jam](https://jam.dev/c/c5c78b3b-2865-4226-836f-bcb0a8fc612f) |
| RF20 | [CT-RF20](Cenario_Teste/CT-RF20_Criacao_Categoria.md) | Nenhum no fluxo avaliado | Aprovado conforme a gravação | [Evidências](Evidencias/CT-RF20_Criacao_Categoria/README.md) e [Jam](https://jam.dev/c/b48ab94e-517d-48d6-8e46-70b18c033b8b) |
| RF21 | [CT-RF21](Cenario_Teste/CT-RF21_Cadastro_Avaliacao.md) | [BUG-010](Relatorio-de-Bugs.md#bug-010) | Reprovado nas evidências | [Evidências](Evidencias/CT-RF21_Cadastro_Avaliacao/README.md) e [Jam](https://jam.dev/c/2e5eca1f-7cd2-4ee3-854b-02ef4635955a) |
| RF22 | [CT-RF22](Cenario_Teste/CT-RF22_Digitacao_Codigo_Exercicio.md) | [BUG-011](Relatorio-de-Bugs.md#bug-011), em triagem | Reprovado conforme o relato; reprodução independente pendente. | [Jam](https://jam.dev/c/2696db03-0a18-4c39-a75d-4987a43c04f0) e relato do testador |
| RF23 | [CT-RF23](Cenario_Teste/CT-RF23_Exclusao_Exercicio.md) | Sem defeito confirmado | Aprovado no trecho consultado. | [Jam](https://jam.dev/c/32adfca3-489f-4a4b-a08d-933c1d1a3c32) e [Evidências](Evidencias/CT-RF23_Exclusao_Exercicio/README.md) |
| RF24 | [CT-RF24](Cenario_Teste/CT-RF24_Edicao_Exercicio.md) | [BUG-012](Relatorio-de-Bugs.md#bug-012), em triagem | Reprovado no trecho consultado; confirmar operação e identidade dos registros na reprodução. | [Jam](https://jam.dev/c/073f70d6-4052-4e0f-a4bb-e9f37305d618) e [Evidências](Evidencias/CT-RF24_Edicao_Exercicio/README.md) |
| RF25 | [CT-RF25](Cenario_Teste/CT-RF25_Envio_Exercicio_Imagem.md) | Sem defeito confirmado | A validar — criação visível; persistência e associação da imagem não confirmadas. | [Jam](https://jam.dev/c/25c37a9b-e9bd-4e0c-adf1-4da528ae1d58) e [Evidências](Evidencias/CT-RF25_Envio_Exercicio_Imagem/README.md) |
| RF26 | [CT-RF26](Cenario_Teste/CT-RF26_Exercicio_Campos_Vazios.md) | [BUG-013](Relatorio-de-Bugs.md#bug-013), em triagem | Reprovado — sem feedback de validação visível. | [Jam](https://jam.dev/c/bc07ca5f-d3a9-45f6-84cb-12c0b562a211) |
| RF27 | [CT-RF27](Cenario_Teste/CT-RF27_Video_Campo_Imagem.md) | [BUG-014](Relatorio-de-Bugs.md#bug-014), em triagem | Reprovado — arquivo rejeitado sem feedback visível. | [Jam](https://jam.dev/c/00740108-9a7d-4151-8723-171c89635567) |
| RF28 | [CT-RF28](Cenario_Teste/CT-RF28_Imagem_Campo_Video.md) | [BUG-015](Relatorio-de-Bugs.md#bug-015), em triagem | Reprovado — arquivo rejeitado sem feedback visível. | [Jam](https://jam.dev/c/be9437a4-4fe9-4756-a2af-6777d3f43e25) |
| RF29 | [CT-RF29](Cenario_Teste/CT-RF29_Exclusao_GrupoMuscular.md) | [BUG-016](Relatorio-de-Bugs.md#bug-016), em triagem | Reprovado nas evidências; reteste pendente. | [Jam](https://jam.dev/c/98008390-0040-475e-ba7b-7f1e72cc0b2e) |
| RF30 | [CT-RF30](Cenario_Teste/CT-RF30_Imagens_GruposMusculares.md) | [BUG-017](Relatorio-de-Bugs.md#bug-017), em triagem | Reprovado nas evidências; reteste pendente. | [Jam](https://jam.dev/c/98008390-0040-475e-ba7b-7f1e72cc0b2e) |
| RF31 | [CT-RF31](Cenario_Teste/CT-RF31_Cadastro_GrupoMuscular.md) | Nenhum no fluxo avaliado | Aprovado conforme a gravação | [Jam](https://jam.dev/c/98008390-0040-475e-ba7b-7f1e72cc0b2e) |
| RF32 | [CT-RF32](Cenario_Teste/CT-RF32_Edicao_TipoMembro.md) | Nenhum no fluxo avaliado | Aprovado conforme a gravação | [Jam](https://jam.dev/c/98008390-0040-475e-ba7b-7f1e72cc0b2e) |
| RF33 | [CT-RF33](Cenario_Teste/CT-RF33_Filtros_GruposMusculares.md) | Nenhum no fluxo avaliado | Aprovado conforme a gravação | [Jam](https://jam.dev/c/98008390-0040-475e-ba7b-7f1e72cc0b2e) |
| RF35 | [CT-RF35](Cenario_Teste/CT-RF35_Cadastro_Objetivo_Treino.md) | [BUG-018](Relatorio-de-Bugs.md#bug-018), em triagem | Reprovado nas evidências; reteste pendente. | [Evidências](Evidencias/CT-RF35_Cadastro_Objetivo_Treino/README.md) e [Jam](https://jam.dev/c/1d474477-2411-4a81-b85c-74207402b783) |

---

## 🔎 Base da análise

- **Relato:** a opção "Esqueci minha senha" não funciona e não dispara requisição ao ser acionada.
- **Jam:** gravação criada em 23/10/2026, com 14 segundos, em https://sifitalfa.centrion.com.br/login; cliques repetidos, permanência na tela de login, 0 requisições registradas e 0 erros de console registrados.
- **Drive:** arquivo de vídeo identificado como `CT-RF01_Esqueci-senha`, mantido como evidência complementar; conteúdo não inspecionado nesta revisão.
- **Limite:** não houve inspeção do código da aplicação nem nova execução no sistema em 10/11/2026.

### Base da análise do RF02 — revisão de 12/11/2026

- **Relato:** perfil com dados fictícios, textos em inglês, campos não exibidos e rolagem horizontal.
- **Captura:** seções Usuário, Documentos e Endereço sem campos visíveis, imagem fora de proporção e textos em inglês.
- **HTML:** conteúdo de demonstração e tags de componentes preservadas no DOM; os trechos de cadastro não contêm elementos `<input>` internos. [Recorte preservado](Evidencias/CT-RF02_ERRO/recorte-dom.html).
- **Jam:** gravação de 22/10/2026 às 21:45 BRT, com aproximadamente 15 segundos; Info indica `/configuracoes`, enquanto Actions registra `/profile` em 00:02 e 00:12 no domínio `sifit.centrion.com.br`. Quadro em 00:05 consultado.
- **Limite:** hipótese de componentes não resolvidos requer inspeção do código. Não houve nova execução, reteste, diagnóstico de rede/console ou validação de salvamento nesta revisão. O ambiente do RF02 é distinto do domínio `sifitalfa.centrion.com.br` registrado no RF01.

### Base da análise do RF03 — revisão de 12/11/2026

- **Relato:** seleção de Ativo, Inadimplente, Plano Hendreu e Marcelo Longo Zandonadi sem restringir corretamente a listagem; alternar para Adimplente mantém resultados praticamente iguais.
- **Rede informada:** três chamadas a `POST https://backendsifit.centrion.com.br/api/clientesPorNome/1`, em aproximadamente 00:05, 00:20 e 00:28, com HTTP 200 e cerca de 180,9 KB por resposta. O corpo simplificado contém apenas `empresa_id: 1` e `nome: ""`, sem os outros quatro critérios; autenticação omitida.
- **Capturas:** mostram filtros selecionados com textos truncados e listagens semelhantes. A primeira mostra uma entrada XHR HTTP 200; a segunda não lista requisições naquele instante. Não permitem confirmar isoladamente os vínculos de cada cliente nem o corpo das chamadas.
- **Jam:** [link fornecido](https://jam.dev/c/657627ec-e7e2-455d-a505-9b2a26f44bf1), sem acesso direto pela ferramenta de consulta na revisão. Horários, endpoint, payload e volumes foram registrados conforme o relato. [Origem e limites das evidências](Evidencias/CT-RF03_Filtros_Clientes/README.md).
- **Limite:** código e contrato da API não analisados; causa não confirmada. Não houve nova execução ou reteste. URL do frontend, data da gravação e versão não confirmadas. As variações de Código, Nome e demais combinações são propostas de validação, sem resultado de execução nesta revisão.

---

### Base da análise do RF04 — revisão de 13/11/2026

- **Jam:** Login com sucesso, criado em 13/11/2026 por Leonardo Barbosa, com aproximadamente 12 segundos; metadados, cronologia e seis quadros consultados diretamente.
- **Ações e rede:** preenchimento de credenciais e clique em Entrar em aproximadamente 00:06; `POST /api/login` e `POST /api/verifica-token-logado` retornam HTTP 200, seguidos de navegação para `/dashboard`.
- **Visual:** menu e resumo da academia visíveis após o envio; cartões preenchidos nos quadros de aproximadamente 00:09 e 00:11.
- **Limite:** sem nova execução, inspeção do código ou validação de persistência da sessão e dos dados do painel. [Origem e cronologia](Evidencias/CT-RF04_loginComSucesso/README.md).

### Base da análise do RF05 ao RF20 — revisão de 14/11/2026

Foram incorporadas as 16 gravações do JAM.txt, na ordem definida pelo solicitante a partir de CT-RF05. A revisão anterior desta sessão consultou detalhes, cronologia e quadros de todas elas; os vídeos originais e seus resumos foram copiados com hash conferido para o repositório. O [índice de evidências](Evidencias/README.md) associa cada caso ao Jam, ao vídeo e aos metadados.

Os novos resultados são cinco aprovações, sete reprovações de manifestações observadas e quatro pontos a validar. As duas reprovações de contagem/filtro financeiro compartilham um defeito. Não houve nova execução, reteste ou análise do código da aplicação.

### Base da análise do RF21 — revisão de 15/11/2026

O relato original foi copiado integralmente. A consulta ao Jam confirmou os detalhes, a cronologia, o evento 16 (HTTP 500, 1363 ms, corpo “Erro interno inesperado.”) e os quadros do formulário em 00:12,479 e do alerta em 00:14,748. Foram preservados os dados de negócio sem autenticação. Não houve nova execução, acesso ao código/banco ou reteste. As referências históricas a evidências ausentes nesta cópia estão identificadas no índice de evidências.


### Base da análise do RF22 ao RF28 — revisão de 15/11/2026

RF22 utiliza relato, imagem inicial e Info do Jam. RF23–RF25 utilizam quadros, Info e listagem Network. RF26–RF28 utilizam quadros e Info dos Jams, sem confirmação de arquivo, MIME, persistência ou resposta detalhada da API. RF23 demonstra remoção e redução de 11 para 10; RF24 apresenta total de 10 para 11 no teste declarado como edição, exigindo confirmar operação e IDs; RF25 demonstra criação com imagem selecionada, sem conferir a imagem salva; RF26–RF28 demonstram ausência de feedback visual nos testes negativos. BUG-011–BUG-015 estão em triagem. Não houve revisão integral quadro a quadro, nova execução, reteste ou diagnóstico de causa raiz.

### Base da análise do RF29 — revisão de 15/11/2026

RF29 utiliza os painéis Informações, Rede e Console do Jam "Tela de Grupos Musculares", lidos diretamente, e os quadros de 1:18 e 1:21. As duas requisições de exclusão, seus horários, tempos de resposta, cabeçalhos e corpo de resposta foram registrados a partir do painel de rede. Não houve nova execução, acesso ao código ou ao banco, nem reteste. BUG-016 está em triagem.

### Base da análise do RF30 — revisão de 15/11/2026

RF30 utiliza a lista de rede do Jam filtrada por erros, a cronologia do painel Console e os quadros de 0:20, 0:55, 1:18, 1:21, 1:45 e 2:00. Foram registrados os quatro arquivos requisitados, doze ocorrências de HTTP 422 entre 0:06 e 1:59 e três ocorrências de `net::ERR_ABORTED`. Os cabeçalhos de resposta das imagens não foram utilizados por inconsistência do painel de detalhe. Não houve verificação no servidor de arquivos, acesso ao banco, nova execução ou reteste. BUG-017 está em triagem.

### Base da análise do RF31 — revisão de 15/11/2026

RF31 utiliza a cronologia do painel Console entre 0:17 e 0:53 e os quadros de 0:20, 0:48 e 0:55. O quadro de 0:48 mostra o formulário no momento do envio, com o campo Código em branco e o campo Imagem em "Nenhum arquivo escolhido". A comparação com o quadro de 0:55 sustenta a criação do registro e a atualização dos cartões. Não houve nova execução, acesso ao código ou ao banco, nem reteste.

### Base da análise do RF32 — revisão de 15/11/2026

RF32 utiliza a cronologia do painel Console entre 0:57 e 1:38 e os quadros de 0:55, 1:02, 1:08, 1:45 e 2:00. O quadro de 1:02 mostra o formulário aberto em edição com os dados do registro de código 1; o de 1:08 mostra a listagem já com o novo tipo de membro e os cartões recalculados. As alterações posteriores a 1:08 não têm quadro de antes e depois individual e sustentam-se no quadro de 1:45 e nos cartões de 2:00. Não houve nova execução, acesso ao código ou ao banco, nem reteste.

### Base da análise do RF33 — revisão de 15/11/2026

RF33 utiliza a cronologia do painel Console e os quadros de 0:15, 1:45 e 2:00. O quadro de 0:15 registra o estado sem resultados; os de 1:45 e 2:00 registram buscas por tipo de membro e por código, com o rodapé correspondente. O resultado da busca pelo código "1", acionada entre 1:53 e 1:55, não teve quadro consultado e está registrado apenas como ação. Não houve nova execução, acesso ao código ou ao banco, nem reteste.

Com RF29 a RF33 a análise passa a cobrir 33 requisitos. A tela Grupos Musculares acrescenta duas reprovações, com BUG-016 e BUG-017 em triagem, e três aprovações limitadas aos exemplos gravados.

### Base da análise do RF35 — revisão de 15/11/2026

RF35 utiliza os painéis Info, Console (atividade do usuário e erros de rede), Network e Actions do Jam "Objetivos Treino", lidos diretamente, os cabeçalhos da última requisição de gravação e os quadros de 0:04, 0:21, 0:41, 0:46, 0:52, 0:58, 1:00, 1:04, 1:06 e 1:11. Foram registrados o endpoint, as duas ocorrências de HTTP 500, o preflight HTTP 204, os tempos e o texto do diálogo de erro; o corpo da requisição e da resposta aparece como indisponível no Jam. As capturas e a cronologia estão na [pasta local de evidências](Evidencias/CT-RF35_Cadastro_Objetivo_Treino/README.md). Não houve nova execução, acesso ao código ou ao banco, nem reteste. BUG-018 está em triagem.

Com RF35 a análise passa a cobrir 34 requisitos documentados (RF01–RF33 e RF35). A tela Objetivos Treino acrescenta uma reprovação, com BUG-018 em triagem. A numeração RF34 / CT-RF34 permanece reservada, sem cenário integrado.

---

[← Início](../README.md) · [Cenários de teste](Cenario_Teste/) · [Evidências de Clientes](Evidencias/CT-RF03_Filtros_Clientes/README.md)
