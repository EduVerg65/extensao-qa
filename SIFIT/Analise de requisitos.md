# 📦 Análise de Requisitos — SIFIT

**Módulos:** Autenticação / Login e Recuperação de senha, Perfil e Clientes / Filtros

**Atualização:** 13/11/2026 — inclusão do RF04 e do caso de login com sucesso.

**Padronização documental:** 13/11/2026, sem alteração dos resultados registrados.

Esta análise documenta o comportamento esperado para login com credenciais válidas, "Esqueci minha senha", "Perfil" e pesquisa com filtros da página Clientes, com base nos relatos e nas evidências fornecidas. Os critérios abaixo constituem a referência de QA para esses fluxos; não representam validação de uma especificação formal pelo responsável pelo produto.

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

---

[← Início](../README.md) · [Cenários de teste](Cenario_Teste/) · [Evidências de Clientes](Evidencias/CT-RF03_Filtros_Clientes/README.md)
