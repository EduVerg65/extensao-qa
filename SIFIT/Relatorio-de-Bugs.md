# Relatório de Bugs — SIFIT

**Escopo:** CT-RF01 — Recuperação de senha; CT-RF02_ERRO — Perfil

**Ambientes:** CT-RF01 em https://sifitalfa.centrion.com.br/login; CT-RF02_ERRO em https://sifit.centrion.com.br/profile.

**Datas das gravações do Jam:** CT-RF01 em 23/10/2026; CT-RF02_ERRO em 22/10/2026 às 21:45 BRT.

**Atualização documental:** 12/11/2026

### BUG-001 — Link "Esqueci minha senha" não executa nenhuma ação

| Campo | Descrição |
| --- | --- |
| **Status** | Aberto — reteste pendente após a correção. |
| **Módulo** | Autenticação / Recuperação de senha. |
| **Severidade** | Alta — impede o início da recuperação autônoma de acesso. |
| **Prioridade** | Alta. |
| **Requisito** | [RF01 — Iniciar recuperação de senha](Analise%20de%20requisitos.md#rf01--iniciar-recuperação-de-senha). |
| **Caso de teste** | [CT-RF01](Cenario_Teste/CT-RF01_Esqueci-senha.md). |

**Pré-condições:** Acessar a tela de login sem estar autenticado, com a opção "Esqueci minha senha" visível. Não é necessário informar credenciais para iniciar esse fluxo.

**Passos para reprodução:**

1. Acessar https://sifitalfa.centrion.com.br/login.
2. Abrir Network (Rede) e Console nas ferramentas de desenvolvedor, habilitar a captura de todas as requisições e limpar os registros.
3. Clicar no link "Esqueci minha senha".
4. Observar se o fluxo de recuperação abre e se há requisição ou erro correspondente ao clique.

**Resultado esperado:** Exibição de formulário ou página para iniciar a solicitação de redefinição de senha, com os campos e as orientações necessários para prosseguir. Requisições ao servidor devem ocorrer nas etapas que dependam dele; uma abertura local de formulário pode ocorrer sem requisição.

**Resultado obtido:** O clique não produz abertura de formulário nem navegação para o fluxo de recuperação. O Jam registra cliques repetidos entre aproximadamente 00:02 e 00:12 e a interface permanece na tela de login. A consulta aos registros de rede da gravação retorna **0 requisições**; a consulta aos erros de console retorna **0 mensagens**.

**Impacto:** O usuário não consegue iniciar a recuperação de senha pela opção disponibilizada na tela de login.

**Análise técnica:** A causa ainda não foi confirmada no código. As evidências mostram a falha de abertura do fluxo e a ausência de requisições registradas. A ausência de requisição isoladamente não caracteriza defeito quando o formulário é aberto localmente; neste caso, o fluxo não abre.

**Encaminhamento:** Inspecionar o tratamento do clique e o destino do fluxo, corrigir a abertura e executar o reteste CT-RF01 conforme o [plano de testes](Plano%20de%20testes.md). Não houve alteração nem validação do código da aplicação nesta revisão documental.

**Evidências:**

- [Vídeo no Google Drive — CT-RF01_Esqueci-senha](https://drive.google.com/file/d/1f6AqYunchDH4R9Yw1JpbyX9x28UQGcbo/view?usp=sharing) — evidência complementar fornecida; metadados consultados, conteúdo não inspecionado nesta revisão.
- [Jam — Erro no esqueci a senhas](https://jam.dev/c/0273b203-b999-493d-9919-2d143bc13301) — eventos, quadros do vídeo, rede e erros de console consultados.

### BUG-002 — Perfil com dados fictícios, campos ausentes e layout desconfigurado

| Campo | Descrição |
| --- | --- |
| **Status** | Aberto — reteste pendente após a correção. |
| **Módulo** | Perfil do usuário. |
| **Severidade** | Alta — compromete a visualização e a edição das informações do perfil. |
| **Prioridade** | Alta, proposta para triagem. |
| **Requisito** | [RF02 — Exibir perfil do usuário autenticado](Analise%20de%20requisitos.md#rf02--exibir-perfil-do-usuário-autenticado). |
| **Caso de teste** | [CT-RF02_ERRO](Cenario_Teste/CT-RF02_ERRO.md). |
| **URL afetada** | https://sifit.centrion.com.br/profile, conforme Actions do Jam. A aba Info registra `/configuracoes`. |
| **Ambiente da gravação** | Chrome 155.0.8059.85 / Windows 11 (x86) / janela 1536 × 742; versão da aplicação e zoom não confirmados. |
| **Data da gravação** | 22/10/2026 às 21:45 BRT, aproximadamente 15 segundos. |
| **Origem do registro** | Relato, captura e HTML fornecidos; metadados, navegações e quadro do vídeo do Jam consultados em 12/11/2026. |

**Pré-condições:** Estar autenticado no SIFIT com acesso à opção Perfil. Para o reteste, usar conta de teste com dados conhecidos e permissões de edição identificadas.

**Passos para reprodução:**

1. Acessar o SIFIT e autenticar-se com uma conta de teste.
2. Abrir o menu do usuário e selecionar **Perfil**.
3. Conferir os dados e textos apresentados, incluindo o cabeçalho e o cartão de perfil.
4. Verificar se as seções **Usuário**, **Documentos** e **Endereço** exibem os campos e seus valores.
5. Observar o dimensionamento das imagens, o alinhamento e a presença de rolagem horizontal.
6. Inspecionar o DOM e registrar as condições de navegador, resolução e zoom para comparação após a correção.

**Resultado esperado:** Exibição dos dados da conta autenticada, com campos carregados corretamente, textos em português e layout organizado conforme o padrão do sistema, sem imagens desproporcionais ou rolagem horizontal indevida. Os campos editáveis devem permitir interação conforme as permissões da conta.

**Resultado obtido:** A página apresenta conteúdo fictício e textos em inglês, como “Hello Jesse”, “Jessica Jones”, “Edit profile” e “About me”. A captura mostra as seções Usuário, Documentos e Endereço sem campos visíveis e uma imagem fora de proporção. O quadro do Jam consultado em 00:05 também mostra seções vazias e uma barra horizontal. Os eventos registram acessos a `/profile` em aproximadamente 00:02 e 00:12.

**Impacto:** O usuário não consegue visualizar adequadamente seus dados nem utilizar os campos de edição ausentes. A navegação fica prejudicada pelo layout desconfigurado. A persistência de alterações não foi testada.

**Análise técnica do HTML:** O conteúdo fornecido mantém `<base-input>`, `<base-header>`, `<base-button>` e `<card>` no DOM. Os campos de cadastro aparecem como `<base-input ... modelvalue=""></base-input>`, sem controles `<input>` internos; o `<textarea>` nativo de About me é exibido com texto de demonstração. Isso sugere componentes não resolvidos ou tratados como elementos personalizados, mas não confirma a causa. Investigar registro/importação de componentes, configuração do compilador, vínculo com a conta autenticada e estilos de imagens/contêineres. Não há evidência suficiente para atribuir o defeito à API ou confirmar um erro específico no console.

**Encaminhamento:** Corrigir o carregamento e a apresentação do perfil no código da aplicação e executar o reteste do [CT-RF02_ERRO](Cenario_Teste/CT-RF02_ERRO.md), conforme o [plano](Plano%20de%20testes.md). O repositório atual contém documentação de QA; esta revisão não corrige o sistema nem fecha o defeito.

**Evidências:**

- [Captura — erro na tela](Evidencias/CT-RF02_ERRO/erro-na-tela.png) — arquivo fornecido, copiado sem alterações e inspecionado visualmente; não mostra toda a página.
- [HTML — recorte do DOM fornecido](Evidencias/CT-RF02_ERRO/recorte-dom.html) — trechos selecionados, com omissões sinalizadas; não é o HTML integral.
- [Jam — Tela de perfil do usuário com erro](https://jam.dev/c/c61241d5-bff5-4a0a-9684-991318f9b51c) — Info, Actions e quadro em 00:05 consultados. Não foi estabelecido diagnóstico de rede ou console nesta revisão.
