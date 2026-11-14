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

## 🔗 Rastreabilidade

| Requisito | Cenário / caso | Defeito | Resultado | Evidências |
| --- | --- | --- | --- | --- |
| RF01 | [Cenário 1 / CT-RF01](Cenario_Teste/CT-RF01_Esqueci-senha.md) | [BUG-001](Relatorio-de-Bugs.md#bug-001--link-esqueci-minha-senha-não-executa-nenhuma-ação) | Reprovado nas evidências; reteste pendente | [Drive](https://drive.google.com/file/d/1f6AqYunchDH4R9Yw1JpbyX9x28UQGcbo/view?usp=sharing) e [Jam](https://jam.dev/c/0273b203-b999-493d-9919-2d143bc13301) |
| RF02 | [Cenário 2 / CT-RF02_ERRO](Cenario_Teste/CT-RF02_ERRO.md) | [BUG-002](Relatorio-de-Bugs.md#bug-002--perfil-com-dados-fictícios-campos-ausentes-e-layout-desconfigurado) | Reprovado nas evidências; reteste pendente | [Captura](Evidencias/CT-RF02_ERRO/erro-na-tela.png), [HTML](Evidencias/CT-RF02_ERRO/recorte-dom.html) e [Jam](https://jam.dev/c/c61241d5-bff5-4a0a-9684-991318f9b51c) |
| RF03 | [Cenário 3 / CT-RF03](Cenario_Teste/CT-RF03_FILTRO_TelaClientes.md) | [BUG-003](Relatorio-de-Bugs.md#bug-003--filtros-combinados-da-página-clientes-não-restringem-a-listagem) | Reprovado conforme o relato; reteste pendente | [Índice e limites](Evidencias/CT-RF03_Filtros_Clientes/README.md), [captura 1](Evidencias/CT-RF03_Filtros_Clientes/filtros-clientes-01.png), [captura 2](Evidencias/CT-RF03_Filtros_Clientes/filtros-clientes-02.png) e [Jam](https://jam.dev/c/657627ec-e7e2-455d-a505-9b2a26f44bf1) |
| RF04 | [Cenário 4 / CT-RF04_loginComSucesso](Cenario_Teste/CT-RF04_loginComSucesso.md) | Nenhum identificado no fluxo avaliado | Aprovado conforme a gravação | [Resumo das evidências](Evidencias/CT-RF04_loginComSucesso/README.md) e [Jam](https://jam.dev/c/5e4a28be-4e80-43d3-9587-1b113723cc38) |
| RF05 | [CT-RF05](Cenario_Teste/CT-RF05_Login_SenhaIncorreta.md) | Nenhum no fluxo avaliado | Aprovado conforme a gravação | [Evidências](Evidencias/CT-RF05_Login_SenhaIncorreta/README.md) e [Jam](https://jam.dev/c/75f16436-7201-4de0-b191-1c4d0d63bfe8) |

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
