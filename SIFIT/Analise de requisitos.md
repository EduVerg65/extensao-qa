# Análise de requisitos — SIFIT

**Módulos:** Autenticação / Recuperação de senha e Perfil

**Atualização:** 12/11/2026

Esta análise documenta o comportamento esperado para as opções "Esqueci minha senha" e "Perfil", com base nos relatos e nas evidências fornecidas. Os critérios abaixo constituem a referência de QA para esses fluxos; não representam validação de uma especificação formal pelo responsável pelo produto.

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

## Rastreabilidade

| Requisito | Cenário / caso | Defeito | Resultado | Evidências |
| --- | --- | --- | --- | --- |
| RF01 | [Cenário 1 / CT-RF01](Cenario_Teste/CT-RF01_Esqueci-senha.md) | [BUG-001](Relatorio-de-Bugs.md#bug-001--link-esqueci-minha-senha-não-executa-nenhuma-ação) | Reprovado nas evidências; reteste pendente | [Drive](https://drive.google.com/file/d/1f6AqYunchDH4R9Yw1JpbyX9x28UQGcbo/view?usp=sharing) e [Jam](https://jam.dev/c/0273b203-b999-493d-9919-2d143bc13301) |
| RF02 | [Cenário 2 / CT-RF02_ERRO](Cenario_Teste/CT-RF02_ERRO.md) | [BUG-002](Relatorio-de-Bugs.md#bug-002--perfil-com-dados-fictícios-campos-ausentes-e-layout-desconfigurado) | Reprovado nas evidências; reteste pendente | [Captura](Evidencias/CT-RF02_ERRO/erro-na-tela.png), [HTML](Evidencias/CT-RF02_ERRO/recorte-dom.html) e [Jam](https://jam.dev/c/c61241d5-bff5-4a0a-9684-991318f9b51c) |

## Base da análise

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
