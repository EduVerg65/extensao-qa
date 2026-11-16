# 📦 Análise de Requisitos — SIFIT

**Módulos:** Autenticação, Perfil, Clientes / Filtros, Financeiro, Página inicial / Personais, SifitBox / Modalidades e Turmas, Categorias Crossfit, Avaliações, Exercícios, Grupos Musculares, Dashboard, Objetivos de Treino, Fichas de Anamnese, Colaboradores, Prospecção e Bandeiras de Cartão.

**Atualização:** 16/11/2026 — RF01 a RF35, RF38 a RF62 e RF65 a RF108 consolidados, com inclusão de Categorias Crossfit (CT-RF38), SifitBox – Turmas (CT-RF39 a CT-RF41), Pagar.me, Configurações, Despesas Fixas e Relatórios (CT-RF42 a CT-RF56), Grupos (treino) (CT-RF57 e CT-RF58), Fichas de Anamnese (CT-RF59), Modelos de Anamnese (CT-RF60), Categorias de Anamnese (CT-RF61), Perguntas Anamnese (CT-RF62), Colaboradores (CT-RF65 a CT-RF73), Prospecção e Bandeiras de Cartão (CT-RF74 a CT-RF90), Contas a Pagar / Modelos de Contrato / Planos (CT-RF91 a CT-RF103) e Tipos de Pagamento (CT-RF104 a CT-RF108); BUG-011–BUG-044 em triagem.

**Padronização documental:** 13/11/2026, sem alteração dos resultados registrados.

Esta análise documenta 104 requisitos de QA para os cenários relacionados abaixo, com base nos relatos e nas evidências fornecidas. RF01–RF04 e suas análises históricas foram preservados; RF05–RF20 ampliam a cobertura em 14/11/2026; RF21 acrescenta Avaliações; RF22–RF28 acrescentam Exercícios; RF29–RF33 acrescentam Grupos Musculares; RF34 acrescenta o carregamento do dashboard RF35 acrescenta o cadastro de objetivos de treino e RF38 acrescenta o cadastro de categorias com código automático em 15/11/2026. RF39 acrescenta o cadastro de modalidade em SifitBox – Turmas. RF40 acrescenta a exclusão de turmas e modalidades. RF41 acrescenta o cadastro de turma. RF42 a RF56 acrescentam Pagar.me, Configurações, Despesas Fixas e Relatórios em 15/11/2026. RF57 acrescenta a exclusão de grupo (treino) e RF58 acrescenta a edição de grupo (treino), ambos também em 15/11/2026. RF59 acrescenta o cadastro de anamnese, também em 15/11/2026. RF60 acrescenta a gestão de modelos de anamnese (busca, cadastro, edição e exclusão), em 16/11/2026. RF61 acrescenta a gestão de categorias de anamnese (filtro, busca, cadastro, edição, cancelamento de edição e exclusão), também em 16/11/2026. RF62 acrescenta a edição de pergunta de anamnese, reprovada por HTTP 500, também em 16/11/2026. RF65–RF73 cobrem validações, operações e buscas de Colaboradores, também em 15/11/2026. RF74–RF84 acrescentam Prospecção e Bandeiras de Cartão a partir de resumos fornecidos, em 16/11/2026. RF85 a RF90 acrescentam Prospecção (leads) em 15/11/2026. RF91 a RF103 acrescentam Contas a Pagar, Modelos de Contrato e Planos em 15/11/2026. RF104 a RF108 acrescentam Tipos de Pagamento em 15/11/2026. Os critérios abaixo constituem a referência de QA para esses fluxos; não representam validação de uma especificação formal pelo responsável pelo produto.

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
| [RF34](#rf34) | Carregar o dashboard sem falhas de servidor ou requisições redundantes | Alta, proposta | [CT-RF34](Cenario_Teste/CT-RF34_Erro_Servidor_Excesso_Requisicoes.md) |
| [RF35](#rf35) | Cadastrar objetivo de treino ou informar validação específica | Alta, proposta | [CT-RF35](Cenario_Teste/CT-RF35_Cadastro_Objetivo_Treino.md) |
| [RF38](#rf38) | Cadastrar categoria com código automático e localizá-la pelos filtros | Média, proposta | [CT-RF38](Cenario_Teste/CT-RF38_Cadastro_Categoria_Codigo_Automatico.md) |
| [RF39](#rf39) | Cadastrar modalidade e apresentá-la na listagem | Média, proposta | [CT-RF39](Cenario_Teste/CT-RF39_Cadastro_Modalidade.md) |
| [RF40](#rf40) | Aplicar e comunicar a regra de exclusão de turmas e modalidades | Média, proposta | [CT-RF40](Cenario_Teste/CT-RF40_Exclusao_Turmas_Modalidades.md) |
| [RF41](#rf41) | Cadastrar turma ou informar visivelmente o dado que impede o envio | Média, proposta | [CT-RF41](Cenario_Teste/CT-RF41_Cadastro_Turma_Sem_Modalidade.md) |
| [RF42](#rf42) | Solicitar saque e informar o resultado | Alta, proposta | [CT-RF42](Cenario_Teste/CT-RF42_Solicitacao_Saque_PagarMe.md) |
| [RF43](#rf43) | Criar cobrança pelo painel Pagar.me | Média, proposta | [CT-RF43](Cenario_Teste/CT-RF43_Criacao_Cobranca_PagarMe.md) |
| [RF44](#rf44) | Salvar as configurações gerais de acesso e presença | Média, proposta | [CT-RF44](Cenario_Teste/CT-RF44_Configuracoes_Home_Salvamento.md) |
| [RF45](#rf45) | Atualizar Recebimentos e gráfico conforme o período | Média, proposta | [CT-RF45](Cenario_Teste/CT-RF45_Painel_PagarMe_Periodo.md) |
| [RF46](#rf46) | Filtrar despesas fixas por código e por nome | Média, proposta | [CT-RF46](Cenario_Teste/CT-RF46_Filtros_Despesas_Fixas.md) |
| [RF47](#rf47) | Cadastrar despesa fixa com uma única gravação | Média, proposta | [CT-RF47](Cenario_Teste/CT-RF47_Cadastro_Despesa_Fixa.md) |
| [RF48](#rf48) | Excluir despesa fixa com confirmação | Média, proposta | [CT-RF48](Cenario_Teste/CT-RF48_Exclusao_Despesa_Fixa.md) |
| [RF49](#rf49) | Editar despesa fixa preservando o registro | Média, proposta | [CT-RF49](Cenario_Teste/CT-RF49_Edicao_Despesa_Fixa.md) |
| [RF50](#rf50) | Gerar o relatório de Matrículas em PDF | Média, proposta | [CT-RF50](Cenario_Teste/CT-RF50_Relatorio_Matriculas.md) |
| [RF51](#rf51) | Apresentar o valor a receber no relatório de Contas a Receber | Alta, proposta | [CT-RF51](Cenario_Teste/CT-RF51_Relatorio_Contas_Receber.md) |
| [RF52](#rf52) | Gerar o relatório de Contas a Pagar (Pagas) | Média, proposta | [CT-RF52](Cenario_Teste/CT-RF52_Relatorio_Contas_Pagar_Pagas.md) |
| [RF53](#rf53) | Gerar o relatório de Avaliações em PDF | Alta, proposta | [CT-RF53](Cenario_Teste/CT-RF53_Relatorio_Avaliacoes_Vazio.md) |
| [RF54](#rf54) | Gerar o relatório de Clientes em PDF | Alta, proposta | [CT-RF54](Cenario_Teste/CT-RF54_Relatorio_Clientes_Vazio.md) |
| [RF55](#rf55) | Gerar o relatório de Colaboradores em PDF | Alta, proposta | [CT-RF55](Cenario_Teste/CT-RF55_Relatorio_Colaboradores_Vazio.md) |
| [RF56](#rf56) | Gerar o relatório de Caixas em PDF | Alta, proposta | [CT-RF56](Cenario_Teste/CT-RF56_Relatorio_Caixas_Vazio.md) |
| [RF57](#rf57) | Excluir grupo ou explicar o impedimento | Alta, proposta | [CT-RF57](Cenario_Teste/CT-RF57_Exclusao_Grupo.md) |
| [RF58](#rf58) | Persistir todos os campos editados de um grupo | Alta, proposta | [CT-RF58](Cenario_Teste/CT-RF58_Edicao_Grupo.md) |
| [RF59](#rf59) | Cadastrar anamnese sem erro de servidor | Alta, proposta para triagem | [CT-RF59](Cenario_Teste/CT-RF59_Cadastro_Anamnese.md) |
| [RF60](#rf60--gerenciar-modelos-de-anamnese-sem-erro-de-servidor) | Gerenciar modelos de anamnese sem erro de servidor | Média | [CT-RF60](Cenario_Teste/CT-RF60_Gestao_Modelos_Anamnese.md) |
| [RF61](#rf61--gerenciar-categorias-de-anamnese-sem-erro-de-servidor) | Gerenciar categorias de anamnese sem erro de servidor | Média | [CT-RF61](Cenario_Teste/CT-RF61_Gestao_Categorias_Anamnese.md) |
| [RF62](#rf62--editar-pergunta-de-anamnese-sem-erro-de-servidor) | Editar pergunta de anamnese sem erro de servidor | Alta, proposta para triagem | [CT-RF62](Cenario_Teste/CT-RF62_Edicao_Pergunta_Anamnese.md) |
| [RF65](#rf65) | Recusar data de nascimento futura na edição de colaborador | Alta, proposta | [CT-RF65](Cenario_Teste/CT-RF65_Data_Nascimento_Futura_Colaborador.md) |
| [RF66](#rf66) | Exigir data de nascimento obrigatória do colaborador | Alta, proposta | [CT-RF66](Cenario_Teste/CT-RF66_Data_Nascimento_Obrigatoria_Colaborador.md) |
| [RF67](#rf67) | Validar o formato do CREF do colaborador | Média, proposta | [CT-RF67](Cenario_Teste/CT-RF67_CREF_Formato_Colaborador.md) |
| [RF68](#rf68) | Bloquear edição de colaborador com campo obrigatório vazio | Alta, proposta | [CT-RF68](Cenario_Teste/CT-RF68_Edicao_Colaborador_Campo_Obrigatorio_Vazio.md) |
| [RF69](#rf69) | Impedir função duplicada para o mesmo colaborador | Média, proposta | [CT-RF69](Cenario_Teste/CT-RF69_Funcao_Duplicada_Colaborador.md) |
| [RF70](#rf70) | Excluir colaborador sem erro de servidor | Alta, proposta | [CT-RF70](Cenario_Teste/CT-RF70_Exclusao_Colaborador_Erro_500.md) |
| [RF71](#rf71) | Manter o filtro por nome durante a paginação | Alta, proposta | [CT-RF71](Cenario_Teste/CT-RF71_Busca_Nome_Colaborador_Paginacao.md) |
| [RF72](#rf72) | Buscar colaborador por código existente | Média, proposta | [CT-RF72](Cenario_Teste/CT-RF72_Busca_Codigo_Existente_Colaborador.md) |
| [RF73](#rf73) | Exibir estado vazio para código inexistente | Alta, proposta | [CT-RF73](Cenario_Teste/CT-RF73_Busca_Codigo_Inexistente_Colaborador.md) |
| [RF74](#rf74) | Alternar entre os temas claro e escuro na Prospecção | Média, proposta | [CT-RF74](Cenario_Teste/CT-RF74_Temas_Prospeccao.md) |
| [RF75](#rf75) | Consultar os detalhes de um lead e cancelar a edição | Média, proposta | [CT-RF75](Cenario_Teste/CT-RF75_Detalhes_Lead_Cancelamento.md) |
| [RF76](#rf76) | Excluir leads com confirmação | Média, proposta | [CT-RF76](Cenario_Teste/CT-RF76_Exclusao_Leads_Confirmacao.md) |
| [RF77](#rf77) | Cadastrar lead no estágio Novo Contato | Média, proposta | [CT-RF77](Cenario_Teste/CT-RF77_Cadastro_Lead_Novo_Contato.md) |
| [RF78](#rf78) | Cadastrar lead no estágio Interessado | Média, proposta | [CT-RF78](Cenario_Teste/CT-RF78_Cadastro_Lead_Interessado.md) |
| [RF79](#rf79) | Cadastrar lead no estágio Fez Aula Experimental | Média, proposta | [CT-RF79](Cenario_Teste/CT-RF79_Cadastro_Lead_Aula_Experimental.md) |
| [RF80](#rf80) | Cadastrar lead no estágio Proposta | Média, proposta | [CT-RF80](Cenario_Teste/CT-RF80_Cadastro_Lead_Proposta.md) |
| [RF81](#rf81) | Cadastrar bandeira com parcela e conferir a listagem | Alta, proposta | [CT-RF81](Cenario_Teste/CT-RF81_Cadastro_Bandeira_Parcela_Listagem.md) |
| [RF82](#rf82) | Verificar aplicação dos temas na tela de Bandeiras | Média, proposta | [CT-RF82](Cenario_Teste/CT-RF82_Tema_Escuro_Bandeiras.md) |
| [RF83](#rf83) | Validar cadastro de lead preenchendo apenas o nome | Alta, proposta | [CT-RF83](Cenario_Teste/CT-RF83_Cadastro_Lead_Apenas_Nome.md) |
| [RF84](#rf84) | Cadastrar lead no estágio Fechado | Média, proposta | [CT-RF84](Cenario_Teste/CT-RF84_Cadastro_Lead_Fechado.md) |
| [RF85](#rf85) | Alternar o tema e consultar as notificações no cabeçalho | Baixa, proposta | [CT-RF85](Cenario_Teste/CT-RF85_Tema_Notificacoes_Prospeccao.md) |
| [RF86](#rf86) | Buscar leads por texto na listagem de Prospecção | Média, proposta | [CT-RF86](Cenario_Teste/CT-RF86_Busca_Leads_Prospeccao.md) |
| [RF87](#rf87) | Filtrar leads por estágio e restaurar a listagem | Média, proposta | [CT-RF87](Cenario_Teste/CT-RF87_Filtro_Estagio_Leads.md) |
| [RF88](#rf88) | Cadastrar um lead com uma única gravação | Média, proposta | [CT-RF88](Cenario_Teste/CT-RF88_Cadastro_Lead_Prospeccao.md) |
| [RF89](#rf89) | Validar o telefone do lead | Média, proposta | [CT-RF89](Cenario_Teste/CT-RF89_Telefone_Lead_Sem_Validacao.md) |
| [RF90](#rf90) | Visualizar e editar um lead | Média, proposta | [CT-RF90](Cenario_Teste/CT-RF90_Edicao_Lead_Prospeccao.md) |
| [RF91](#rf91) | Filtrar contas a pagar por nome, data e status | Média, proposta | [CT-RF91](Cenario_Teste/CT-RF91_Filtros_Contas_Pagar.md) |
| [RF92](#rf92) | Exigir o colaborador no cadastro de conta a pagar a colaborador | Alta, proposta | [CT-RF92](Cenario_Teste/CT-RF92_Cadastro_Conta_Colaborador_Sem_Colaborador.md) |
| [RF93](#rf93) | Buscar e selecionar colaborador no cadastro de conta | Média, proposta | [CT-RF93](Cenario_Teste/CT-RF93_Busca_Colaborador_Conta_Pagar.md) |
| [RF94](#rf94) | Visualizar os dados de uma conta a pagar | Baixa, proposta | [CT-RF94](Cenario_Teste/CT-RF94_Visualizacao_Conta_Pagar.md) |
| [RF95](#rf95) | Excluir uma conta a pagar com confirmação | Média, proposta | [CT-RF95](Cenario_Teste/CT-RF95_Exclusao_Conta_Pagar.md) |
| [RF96](#rf96) | Inserir variáveis e pré-visualizar o contrato | Média, proposta | [CT-RF96](Cenario_Teste/CT-RF96_Variaveis_Preview_Modelo_Contrato.md) |
| [RF97](#rf97) | Cadastrar um modelo de contrato | Média, proposta | [CT-RF97](Cenario_Teste/CT-RF97_Cadastro_Modelo_Contrato.md) |
| [RF98](#rf98) | Apresentar na listagem os modelos de contrato retornados pelo servidor | Alta, proposta | [CT-RF98](Cenario_Teste/CT-RF98_Listagem_Modelos_Contrato_Vazia.md) |
| [RF99](#rf99) | Filtrar planos por código e por nome | Média, proposta | [CT-RF99](Cenario_Teste/CT-RF99_Filtros_Planos.md) |
| [RF100](#rf100) | Alternar o tema e consultar as notificações na tela Planos | Baixa, proposta | [CT-RF100](Cenario_Teste/CT-RF100_Tema_Notificacoes_Planos.md) |
| [RF101](#rf101) | Cadastrar um plano | Alta, proposta | [CT-RF101](Cenario_Teste/CT-RF101_Cadastro_Plano.md) |
| [RF102](#rf102) | Manter o cartão Ativos coerente com o status dos planos | Média, proposta | [CT-RF102](Cenario_Teste/CT-RF102_Contador_Ativos_Planos.md) |
| [RF103](#rf103) | Editar um plano | Média, proposta | [CT-RF103](Cenario_Teste/CT-RF103_Edicao_Plano.md) |
| [RF104](#rf104) | Filtrar tipos de pagamento por código, nome, status e tipo | Média, proposta | [CT-RF104](Cenario_Teste/CT-RF104_Filtros_Tipos_Pagamento.md) |
| [RF105](#rf105) | Gravar e refletir o status do tipo de pagamento no cadastro | Média, proposta | [CT-RF105](Cenario_Teste/CT-RF105_Cadastro_Tipo_Pagamento_Status.md) |
| [RF106](#rf106) | Editar um tipo de pagamento | Média, proposta | [CT-RF106](Cenario_Teste/CT-RF106_Edicao_Tipo_Pagamento.md) |
| [RF107](#rf107) | Impedir a exclusão de tipo de pagamento em uso com mensagem clara | Média, proposta | [CT-RF107](Cenario_Teste/CT-RF107_Exclusao_Tipo_Pagamento_Em_Uso.md) |
| [RF108](#rf108) | Alternar tema Claro/Escuro e abrir as notificações em Tipos de Pagamento | Baixa, proposta | [CT-RF108](Cenario_Teste/CT-RF108_Tema_Notificacoes_Tipos_Pagamento.md) |

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

<a id="rf34"></a>

## RF34 — Carregar o dashboard sem falhas de servidor ou requisições redundantes

| Campo | Descrição |
| --- | --- |
| Requisito de QA | O dashboard deve solicitar somente os dados necessários, receber respostas tratáveis e carregar seus componentes sem erro HTTP 500. Uma falha parcial deve identificar o componente afetado sem inutilizar todo o painel. |
| Ator | Usuário autenticado com acesso ao dashboard. |
| Pré-condições | Sessão válida, conta de teste com dados conhecidos e captura de rede ativa. |
| Gatilho | Acessar ou recarregar controladamente o dashboard. |
| Caso | [CT-RF34](Cenario_Teste/CT-RF34_Erro_Servidor_Excesso_Requisicoes.md) |
| Situação observada | Reprovado nas evidências. O dashboard apresenta um diálogo de erro; a listagem visível contém 23 eventos, com verificação de token HTTP 200, diversas chamadas GET/POST HTTP 500 e OPTIONS HTTP 204. |
| Defeito | [BUG-018](Relatorio-de-Bugs.md#bug-018), em triagem |
| Evidências | [Jam](https://jam.dev/c/eea58e17-b62f-432b-97b2-b14c14bed555) e [Evidências](Evidencias/CT-RF34_Erro_Servidor_Excesso_Requisicoes/README.md). |

### Critérios de aceitação do RF34

1. Cada componente executa apenas as chamadas previstas pelo contrato.
2. Nenhuma requisição necessária ao dashboard retorna HTTP 500.
3. Falhas parciais são identificadas e não inutilizam componentes independentes.
4. A quantidade e a sequência das chamadas permanecem estáveis após recarga controlada.
5. Logs e identificadores permitem correlacionar qualquer resposta não bem-sucedida.

### Pontos a confirmar e limites do RF34

Os caminhos completos, parâmetros, corpos, logs e componentes de origem não foram confirmados. O título do Jam atribui o problema ao excesso de requisições, mas a relação causal não foi demonstrada. Correlacionar cada HTTP 500 ao endpoint e ao componente antes de concluir se há repetição indevida, retentativa descontrolada ou indisponibilidade simultânea do backend.
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
| Defeito | [BUG-019](Relatorio-de-Bugs.md#bug-019), em triagem |
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

O campo Código permaneceu vazio nos quadros apesar da digitação registrada; a evidência não distingue um código atribuído automaticamente (como se interpretou no [RF31](#rf31)) do impedimento relatado no [RF22](#rf22). A base estava vazia, de modo que os filtros por código e nome não puderam ser avaliados, e a mensagem "Nenhum objetivo cadastrado" também aparece com filtro aplicado; a distinção entre "nenhum cadastrado" e "nenhum encontrado" depende de confirmação do produto, como no [RF33](#rf33). O padrão de HTTP 500 em operação de escrita repete o de [RF19](#rf19), [RF21](#rf21) e [RF29](#rf29), em módulos distintos.

---

<a id="rf38"></a>

## RF38 — Cadastrar categoria com código automático e localizá-la pelos filtros

| Campo | Descrição |
| --- | --- |
| Requisito de QA | O cadastro de uma categoria deve exigir apenas o nome, com o código atribuído pelo sistema, e o novo registro deve constar na listagem e ser localizado pelos filtros de código e de nome, com o cartão Exibidas coerente. |
| Ator | Usuário autenticado com permissão em Categorias Crossfit. |
| Pré-condições | Base conhecida (quantidade de categorias e códigos registrados); nome de categoria de teste disponível; regra do campo Código confirmada com o produto. |
| Gatilho | Clicar em Nova Categoria, informar o nome e clicar em Salvar; depois informar o código atribuído no filtro Código. |
| Caso | [CT-RF38](Cenario_Teste/CT-RF38_Cadastro_Categoria_Codigo_Automatico.md) |
| Situação observada | Aprovado conforme a gravação. `POST /api/categoria-exercicio-cross/criar` retorna HTTP 201 com o corpo `{"nome": "teste"}` e "Categoria criada com sucesso!"; a listagem passa de oito para nove categorias, com o código 9, e o filtro Código "9" retorna apenas esse registro. O campo Código não retém o texto digitado. |
| Defeito | Nenhum no fluxo avaliado |
| Evidências | [Jam](https://jam.dev/c/be1dbd05-217d-44c3-8a3d-240b7f6344e1) e [Evidências](Evidencias/CT-RF38_Cadastro_Categoria_Codigo_Automatico/README.md). |

### Critérios de aceitação do RF38

1. O formulário permite informar o nome e cria a categoria ao salvar, com mensagem de sucesso.
2. O código é atribuído pelo sistema, sem depender de valor digitado pelo usuário, e não duplica um código existente.
3. A listagem e os cartões de resumo refletem a inclusão.
4. O filtro por nome e o filtro por código retornam apenas os registros correspondentes.
5. A limpeza dos filtros restaura a listagem completa.
6. O registro permanece após recarga da página.

### Pontos a confirmar e limites do RF38

A regra do campo Código não foi fornecida: o campo não retém o texto digitado e o código não consta no corpo da requisição, o que é compatível com um código automático (como nos [RF31](#rf31) e [RF35](#rf35)), mas também com um campo bloqueado à digitação, relacionado ao relato do [RF22](#rf22). Os filtros não geram requisição de rede, compatível com filtragem local, sem confirmação; o comportamento com bases maiores ou paginadas não foi avaliado. O contrato dos cartões de resumo, em especial Atualizadas, não foi fornecido, do mesmo modo que no [RF11](#rf11).

Permanecem fora do cenário gravado: nome vazio, nome duplicado, limites de tamanho, caracteres especiais, código inexistente ou não numérico no filtro, combinação contraditória de código e nome, resultado vazio, paginação e persistência após recarga. O RF38 complementa o [RF17](#rf17) (filtros) e o [RF20](#rf20) (criação), sem substituí-los.

---

<a id="rf39"></a>

## RF39 — Cadastrar modalidade em SifitBox – Turmas

| Campo | Descrição |
| --- | --- |
| Requisito de QA | O cadastro de uma modalidade deve criar o registro com o nome, a descrição e o status informados, apresentá-lo na listagem de Modalidades e limpar o formulário. |
| Ator | Usuário autenticado com permissão em SifitBox – Turmas. |
| Pré-condições | Listagem de Modalidades conhecida; nome de modalidade de teste disponível. |
| Gatilho | Preencher nome e descrição da modalidade, manter o status Ativo e acionar o botão de envio de Modalidade. |
| Caso | [CT-RF39](Cenario_Teste/CT-RF39_Cadastro_Modalidade.md) |
| Situação observada | Aprovado conforme a gravação. `POST /api/sifitbox/modalidades/salvar/1` retorna HTTP 201 com a modalidade de id 4 e status "ativo"; a listagem passa de três para quatro modalidades e o formulário é limpo. |
| Defeito | Nenhum no fluxo avaliado |
| Evidências | [Jam](https://jam.dev/c/ee9a133b-d6b1-442d-b4b0-dd87595b7e70) e [Evidências](Evidencias/CT-RF39_Cadastro_Modalidade/README.md). |

### Critérios de aceitação do RF39

1. O formulário permite informar nome, descrição e status e cria a modalidade ao confirmar.
2. A resposta retorna sucesso e o registro com os dados informados e o status escolhido.
3. A listagem passa a exibir a nova modalidade e o formulário é limpo.
4. A modalidade permanece após recarga da página.
5. Dados inválidos ou ausentes recebem validação específica, sem HTTP 500.

### Pontos a confirmar e limites do RF39

Não foram verificados a persistência após recarga, a mensagem de confirmação, o nome vazio, o nome duplicado e os limites de tamanho. O corpo enviado traz `"id": {}` (objeto vazio), aceito pelo sistema; o contrato da API não foi fornecido. As modalidades anteriores aparecem como "inativo" sob o filtro "Ativo", ponto tratado no [RF40](#rf40) e relacionado ao [RF16](#rf16).

---

<a id="rf40"></a>

## RF40 — Excluir turmas e modalidades conforme a regra de exclusão

| Campo | Descrição |
| --- | --- |
| Requisito de QA | A lixeira de turmas e de modalidades deve aplicar a regra de exclusão definida pelo produto (lógica ou física), com confirmação prévia quando exigida, informar o resultado ao usuário e refletir o resultado na listagem conforme o filtro de status selecionado. |
| Ator | Usuário autenticado com permissão em SifitBox – Turmas. |
| Pré-condições | Turmas e modalidades de teste com status e vínculos conhecidos; regra de exclusão e de confirmação definida com o produto. |
| Gatilho | Acionar a lixeira de uma turma ou de uma modalidade na listagem. |
| Caso | [CT-RF40](Cenario_Teste/CT-RF40_Exclusao_Turmas_Modalidades.md) |
| Situação observada | A validar — regra ou contexto pendente. Os cliques na lixeira geram `POST turmas/excluir` e `POST modalidades/excluir` com HTTP 200 e `{"erro": false}`; os registros permanecem na listagem com o status "inativo", sem diálogo de confirmação nos quadros consultados. |
| Defeito | Sem defeito confirmado |
| Evidências | [Jam](https://jam.dev/c/ee9a133b-d6b1-442d-b4b0-dd87595b7e70) e [Evidências](Evidencias/CT-RF40_Exclusao_Turmas_Modalidades/README.md). |

### Critérios de aceitação do RF40

1. A lixeira aplica a regra de exclusão definida pelo produto, com confirmação prévia quando exigida.
2. A resposta e a interface informam o resultado de forma compreensível.
3. A listagem apresenta apenas registros compatíveis com o filtro de status selecionado.
4. Turmas vinculadas a uma modalidade excluída ou inativada recebem tratamento definido e comunicado.
5. A ação sobre um registro já inativo tem retorno coerente.
6. O resultado se mantém após recarga da página.

### Pontos a confirmar e limites do RF40

Não foram confirmados a regra de exclusão lógica, a necessidade de confirmação, a exibição de registros inativos sob o filtro "Ativo", o efeito sobre turmas vinculadas e a persistência após recarga. Os corpos das requisições de exclusão e o filtro "Inativo" não foram inspecionados. O comportamento repete o ponto a validar do [RF16](#rf16). Registrar defeito apenas se houver divergência com a regra definida.

---

<a id="rf41"></a>

## RF41 — Cadastrar turma ou informar o dado que impede o envio

| Campo | Descrição |
| --- | --- |
| Requisito de QA | O cadastro de turma deve criar a turma quando todos os dados obrigatórios forem informados; com dado obrigatório ausente (como a modalidade), deve bloquear o envio, indicar de forma visível o campo pendente e não criar registro. |
| Ator | Usuário autenticado com permissão em SifitBox – Turmas. |
| Pré-condições | Ao menos uma modalidade ativa; turmas existentes registradas; regra de obrigatoriedade dos campos definida com o produto. |
| Gatilho | Preencher o formulário de Turma, sem selecionar a modalidade, e acionar o botão de envio de Turma. |
| Caso | [CT-RF41](Cenario_Teste/CT-RF41_Cadastro_Turma_Sem_Modalidade.md) |
| Situação observada | Reprovado nas evidências — sem feedback de validação visível. Nas tentativas com formulário vazio e com a modalidade em branco, o envio não gera requisição de criação de turma nem apresenta mensagem; o formulário permanece preenchido e a listagem não muda. |
| Defeito | [BUG-020](Relatorio-de-Bugs.md#bug-020), em triagem |
| Evidências | [Jam](https://jam.dev/c/ee9a133b-d6b1-442d-b4b0-dd87595b7e70) e [Evidências](Evidencias/CT-RF41_Cadastro_Turma_Sem_Modalidade/README.md). |

### Critérios de aceitação do RF41

1. O envio de Turma com campo obrigatório vazio é bloqueado e cada campo pendente recebe indicação compreensível.
2. Nenhum registro vazio ou incompleto é criado.
3. Com todos os dados válidos, a turma é criada, apresentada na listagem e mantida após recarga.
4. A ação de envio informa o resultado (sucesso ou impedimento) ao usuário.
5. O horário de término anterior ou igual ao de início recebe validação específica, conforme a regra do produto.

### Pontos a confirmar e limites do RF41

Não foi confirmado se a modalidade é obrigatória nem se existe validação nativa do navegador, cujo balão normalmente não aparece em gravações de tela. O envio válido, o horário de término igual ou anterior ao de início, o nome vazio e a persistência não foram exercitados. A edição da turma de id 4 gerou `POST turmas/atualizar` com HTTP 200, sem mensagem de confirmação observada. O padrão de ausência de feedback repete o do [RF26](#rf26).

---

<a id="rf42"></a>

## RF42 — Solicitar saque e informar o resultado

| Campo | Descrição |
| --- | --- |
| Requisito de QA | A solicitação de saque pelo painel Pagar.me deve registrar o pedido e informar ao usuário o resultado (sucesso ou impedimento), atualizando o saldo quando aplicável. |
| Ator | Usuário autenticado com acesso ao módulo Pagar.me. |
| Pré-condições | Conta de pagamento configurada; saldo disponível conhecido; regra de saque definida com o produto. |
| Gatilho | Acionar Solicitar saque, informar o valor e confirmar. |
| Caso | [CT-RF42](Cenario_Teste/CT-RF42_Solicitacao_Saque_PagarMe.md) |
| Situação observada | A validar — regra ou contexto pendente. A confirmação do saque (valor 1000, saldo "R$ --") gera `POST sacar-saldo` com HTTP 200, mas a interface não apresenta mensagem de resultado. |
| Defeito | Sem defeito confirmado |
| Evidências | [Jam](https://jam.dev/c/e6e551ef-9196-4c79-b6a2-89747b1e8b33) e [Evidências](Evidencias/CT-RF42_Solicitacao_Saque_PagarMe/README.md). |

### Critérios de aceitação do RF42

1. A solicitação de saque informa o resultado (sucesso ou impedimento) de forma compreensível.
2. Com saldo indisponível ou insuficiente, o sistema apresenta o impedimento antes ou depois do envio, sem aceitar silenciosamente.
3. O valor informado é validado (mínimo, máximo e formato).
4. O saldo e os indicadores são atualizados após uma solicitação bem-sucedida.
5. A solicitação não é duplicada por cliques repetidos.

### Pontos a confirmar e limites do RF42

O corpo e a resposta da solicitação não foram capturados; não foram confirmados o registro do saque, a regra de saldo e a mensagem de retorno. O saldo indisponível ("R$ --") e a diferença em relação ao cartão Recebimentos são tratados no [RF45](#rf45).

---

<a id="rf43"></a>

## RF43 — Criar cobrança pelo painel Pagar.me

| Campo | Descrição |
| --- | --- |
| Requisito de QA | A criação de cobrança pelo painel Pagar.me deve aceitar descrição, valor e método de pagamento, criar a cobrança e informar o sucesso ao usuário. |
| Ator | Usuário autenticado com acesso ao módulo Pagar.me. |
| Pré-condições | Conta de pagamento configurada; descrição e valor de teste autorizados. |
| Gatilho | Acionar Nova cobrança, informar descrição, valor e método e acionar Criar Cobrança. |
| Caso | [CT-RF43](Cenario_Teste/CT-RF43_Criacao_Cobranca_PagarMe.md) |
| Situação observada | Aprovado conforme a gravação. `POST criar-cobranca` retorna HTTP 200 e o sistema apresenta "Cobrança criada com sucesso!". |
| Defeito | Nenhum no fluxo avaliado |
| Evidências | [Jam](https://jam.dev/c/e6e551ef-9196-4c79-b6a2-89747b1e8b33) e [Evidências](Evidencias/CT-RF43_Criacao_Cobranca_PagarMe/README.md). |

### Critérios de aceitação do RF43

1. O formulário permite informar descrição, valor e método de pagamento.
2. A criação retorna sucesso e a interface apresenta mensagem compreensível.
3. A cobrança passa a constar nos registros do módulo (por exemplo, Transações recentes) conforme a regra do produto.
4. Dados inválidos ou ausentes recebem validação específica.
5. A cobrança não é duplicada por cliques repetidos.

### Pontos a confirmar e limites do RF43

Não foram verificados a presença da cobrança nos registros, o link gerado, outros métodos, valores inválidos e duplicidade; corpo e resposta da requisição não foram capturados.

---

<a id="rf44"></a>

## RF44 — Salvar as configurações gerais de acesso e presença

| Campo | Descrição |
| --- | --- |
| Requisito de QA | As alterações da aba Home de Configurações devem ser salvas com confirmação ao usuário, persistir após recarga, respeitar a faixa válida de cada campo e refletir-se nos cartões de resumo e no menu lateral. |
| Ator | Usuário autenticado com permissão para alterar as Configurações. |
| Pré-condições | Valores iniciais registrados; regra de cada opção e do campo de dias definida com o produto. |
| Gatilho | Alterar as opções e o campo de dias da aba Home e acionar Salvar Configurações. |
| Caso | [CT-RF44](Cenario_Teste/CT-RF44_Configuracoes_Home_Salvamento.md) |
| Situação observada | A validar — regra ou contexto pendente. As alterações são refletidas nos cartões e no menu lateral após o envio, sem mensagem de confirmação visível; o campo de dias vai de -120 para 1100 sem validação visível. |
| Defeito | Sem defeito confirmado |
| Evidências | [Jam](https://jam.dev/c/e6e551ef-9196-4c79-b6a2-89747b1e8b33) e [Evidências](Evidencias/CT-RF44_Configuracoes_Home_Salvamento/README.md). |

### Critérios de aceitação do RF44

1. O salvamento informa o resultado (sucesso ou erro) de forma compreensível.
2. As configurações salvas persistem após recarga da página.
3. O campo "Dias para contar cliente como ausente" rejeita valores fora da faixa definida (incluindo negativos).
4. O menu lateral e os cartões de resumo refletem as opções salvas.
5. Cancelar descarta as alterações não salvas.

### Pontos a confirmar e limites do RF44

A mensagem de salvamento, a persistência após recarga, a faixa válida do campo de dias (valor inicial -120 e valor informado 1100) e os corpos das requisições não foram confirmados. As demais abas (Biometria, Avaliação, Aniversário, Pagamento, Integrações e Design) não foram avaliadas.

---

<a id="rf45"></a>

## RF45 — Atualizar Recebimentos e gráfico conforme o período

| Campo | Descrição |
| --- | --- |
| Requisito de QA | O painel Pagar.me deve apresentar Recebimentos, variação, gráfico e meios de pagamento correspondentes ao período selecionado, com indicadores de saldo coerentes ou com indicação explícita de indisponibilidade. |
| Ator | Usuário autenticado com acesso ao módulo Pagar.me. |
| Pré-condições | Conta de pagamento com movimentação conhecida; regra de apuração dos indicadores definida com o produto. |
| Gatilho | Selecionar outro período no cartão Recebimentos. |
| Caso | [CT-RF45](Cenario_Teste/CT-RF45_Painel_PagarMe_Periodo.md) |
| Situação observada | Reprovado nas evidências. Com "Últimos 7 dias", Recebimentos permanece R$ 38.420,00 e o gráfico é idêntico ao de "Últimos 30 dias"; os indicadores de saldo permanecem "R$ --". |
| Defeito | [BUG-021](Relatorio-de-Bugs.md#bug-021), em triagem |
| Evidências | [Jam](https://jam.dev/c/e6e551ef-9196-4c79-b6a2-89747b1e8b33) e [Evidências](Evidencias/CT-RF45_Painel_PagarMe_Periodo/README.md). |

### Critérios de aceitação do RF45

1. O seletor de período atualiza o valor de Recebimentos, a variação, o gráfico e o eixo de datas.
2. O eixo do gráfico apresenta datas compatíveis com o período selecionado e com a data atual.
3. Os meios de pagamento correspondem ao período e ao total apresentado.
4. Os indicadores de saldo apresentam valores quando a conta tem saldo, ou mensagem explícita de indisponibilidade.
5. Valores de demonstração, se existirem, são identificados como tal.

### Pontos a confirmar e limites do RF45

Não foi confirmado se o painel usa dados reais ou de demonstração; o clique no seletor não consta na cronologia e a leitura do eixo de datas é aproximada. Os corpos das requisições não foram capturados.

---

<a id="rf46"></a>

## RF46 — Filtrar despesas fixas por código e por nome

| Campo | Descrição |
| --- | --- |
| Requisito de QA | A busca da tela Despesas Fixas deve apresentar apenas as despesas que atendam aos critérios de código e de nome informados, com o Valor Listado correspondente ao conjunto exibido e restauração da listagem completa ao limpar os critérios. |
| Ator | Usuário autenticado com acesso a Despesas Fixas. |
| Pré-condições | Base conhecida, com códigos, nomes, status e recorrências registrados. |
| Gatilho | Informar código ou nome e, depois, limpar os critérios. |
| Caso | [CT-RF46](Cenario_Teste/CT-RF46_Filtros_Despesas_Fixas.md) |
| Situação observada | Aprovado conforme a gravação. O filtro por código "1" lista os códigos 10 a 19 e o filtro por nome "Teste" retorna #5 e #7, com Valor Listado acompanhando o conjunto; os campos limpos restauram a listagem completa. |
| Defeito | Nenhum no fluxo avaliado |
| Evidências | [Jam](https://jam.dev/c/a4bac99d-e436-4792-831e-8c3a875272bb) e [Evidências](Evidencias/CT-RF46_Filtros_Despesas_Fixas/README.md). |

### Critérios de aceitação do RF46

1. O filtro por código retorna as despesas cujo código corresponde ao critério.
2. O filtro por nome retorna as despesas cujo nome contém o critério, sem diferenciar maiúsculas de minúsculas.
3. O cartão Valor Listado e o rodapé acompanham o conjunto exibido.
4. A limpeza dos critérios restaura a listagem completa.
5. Combinações sem correspondência apresentam mensagem explícita de resultado vazio.

### Pontos a confirmar e limites do RF46

A combinação de critérios, o resultado vazio, o filtro por Status e Recorrência com valores específicos e a regra de correspondência do código não foram exercitados. Os filtros não geram requisição de rede, compatível com filtragem local, sem confirmação. O contrato dos cartões não foi fornecido, como no [RF11](#rf11) e no [RF33](#rf33).

---

<a id="rf47"></a>

## RF47 — Cadastrar despesa fixa com uma única gravação

| Campo | Descrição |
| --- | --- |
| Requisito de QA | O cadastro de despesa fixa deve criar uma única despesa com os dados informados, atribuir o código, apresentá-la na listagem e atualizar os cartões, sem requisições de criação duplicadas. |
| Ator | Usuário autenticado com acesso a Despesas Fixas. |
| Pré-condições | Quantidade de despesas e códigos registrados; nome de teste disponível. |
| Gatilho | Preencher Nova Despesa e acionar Salvar Despesa. |
| Caso | [CT-RF47](Cenario_Teste/CT-RF47_Cadastro_Despesa_Fixa.md) |
| Situação observada | A validar — regra ou contexto pendente. A despesa de código 23 é criada e a listagem passa de 16 para 17 registros, mas um único clique em Salvar Despesa gera dois `POST cria/despesa-fixa` com HTTP 201. |
| Defeito | Sem defeito confirmado |
| Evidências | [Jam](https://jam.dev/c/a4bac99d-e436-4792-831e-8c3a875272bb) e [Evidências](Evidencias/CT-RF47_Cadastro_Despesa_Fixa/README.md). |

### Critérios de aceitação do RF47

1. Um único clique em Salvar Despesa gera uma única requisição de criação e um único registro.
2. O código é atribuído pelo sistema e não duplica um código existente.
3. A listagem e os cartões de resumo refletem a inclusão.
4. A mensagem de sucesso ou de erro é apresentada ao usuário.
5. A despesa permanece após recarga da página.

### Pontos a confirmar e limites do RF47

O corpo e a resposta da segunda requisição não foram capturados; não foi confirmado se houve registro adicional. A persistência após recarga, a mensagem de confirmação e a regra do código não foram verificadas.

---

<a id="rf48"></a>

## RF48 — Excluir despesa fixa com confirmação

| Campo | Descrição |
| --- | --- |
| Requisito de QA | A exclusão de despesa fixa deve pedir confirmação, excluir a despesa permitida, remover o registro da listagem e atualizar os cartões de resumo. |
| Ator | Usuário autenticado com permissão para excluir despesas fixas. |
| Pré-condições | Despesa de teste e cartões registrados antes da exclusão. |
| Gatilho | Acionar a lixeira da despesa e confirmar no diálogo. |
| Caso | [CT-RF48](Cenario_Teste/CT-RF48_Exclusao_Despesa_Fixa.md) |
| Situação observada | Aprovado conforme a gravação. O diálogo "Deseja excluir a despesa fixa?" é confirmado, `POST deleta/despesa-fixa` retorna HTTP 200 e a listagem passa de 17 para 16 despesas. |
| Defeito | Nenhum no fluxo avaliado |
| Evidências | [Jam](https://jam.dev/c/a4bac99d-e436-4792-831e-8c3a875272bb) e [Evidências](Evidencias/CT-RF48_Exclusao_Despesa_Fixa/README.md). |

### Critérios de aceitação do RF48

1. A ação de exclusão apresenta confirmação explícita antes de efetivar a operação.
2. A exclusão permitida remove o registro da listagem e atualiza os cartões.
3. A resposta informa sucesso e o resultado se mantém após recarga da página.
4. Cancelar no diálogo preserva o registro.
5. Despesas com vínculo impeditivo recebem mensagem específica, sem erro interno.

### Pontos a confirmar e limites do RF48

A persistência após recarga, a natureza da exclusão (física ou lógica), Cancelar e a exclusão com vínculos não foram exercitados.

---

<a id="rf49"></a>

## RF49 — Editar despesa fixa preservando o registro

| Campo | Descrição |
| --- | --- |
| Requisito de QA | A edição de despesa fixa deve abrir o formulário com os dados da despesa, atualizar a mesma despesa ao salvar, apresentar a alteração na listagem e não criar registro adicional. |
| Ator | Usuário autenticado com permissão para editar despesas fixas. |
| Pré-condições | Despesa de teste com todos os campos registrados antes da edição. |
| Gatilho | Abrir a despesa, alterar a recorrência e acionar Salvar Despesa. |
| Caso | [CT-RF49](Cenario_Teste/CT-RF49_Edicao_Despesa_Fixa.md) |
| Situação observada | Aprovado conforme a gravação. `POST edita/despesa-fixa` (despesa 7, recorrência "7 dias") retorna HTTP 200 e a listagem apresenta "7 Dias" sem alterar a quantidade de despesas. |
| Defeito | Nenhum no fluxo avaliado |
| Evidências | [Jam](https://jam.dev/c/a4bac99d-e436-4792-831e-8c3a875272bb) e [Evidências](Evidencias/CT-RF49_Edicao_Despesa_Fixa/README.md). |

### Critérios de aceitação do RF49

1. O formulário de edição é preenchido com todos os dados da despesa, incluindo a recorrência.
2. Salvar atualiza a mesma despesa, sem criar registro adicional.
3. A listagem apresenta a nova recorrência e os cartões permanecem coerentes.
4. A alteração permanece após recarga da página.
5. Cancelar descarta as alterações.

### Pontos a confirmar e limites do RF49

A persistência após recarga, o pré-preenchimento da recorrência (o quadro de 0:48 mostra o seletor sem valor visível, enquanto a resposta traz "1 Mês"), a mensagem de confirmação e a edição de outros campos não foram verificados.

---

<a id="rf50"></a>

## RF50 — Gerar o relatório de Matrículas em PDF

| Campo | Descrição |
| --- | --- |
| Requisito de QA | A geração do relatório de Matrículas deve produzir um PDF válido com as matrículas do período e dos filtros informados, com valor e quantidade de registros coerentes. |
| Ator | Usuário autenticado com permissão para gerar relatórios. |
| Pré-condições | Matrículas do período conhecidas. |
| Gatilho | Selecionar "Matrículas", informar o período e acionar Gerar Relatório. |
| Caso | [CT-RF50](Cenario_Teste/CT-RF50_Relatorio_Matriculas.md) |
| Situação observada | Aprovado conforme o PDF. O relatório abre e apresenta uma matrícula (Plano Diário, R$ 20,00) com "Quantidade de registros: 1". |
| Defeito | Nenhum no fluxo avaliado |
| Evidências | [Jam](https://jam.dev/c/3b4777a4-e1b0-4038-9b06-26c73669d7d1) e [Evidências](Evidencias/CT-RF50_Relatorio_Matriculas/README.md). |

### Critérios de aceitação do RF50

1. O PDF abre e apresenta cabeçalho, período e colunas do relatório.
2. Os registros correspondem às matrículas do período e aos filtros informados.
3. O valor e a quantidade de registros são coerentes com as linhas.
4. Sem matrículas no período, o relatório apresenta a estrutura vazia explícita.
5. Os filtros de Plano e de Tipo de Pagto restringem o conteúdo.

### Pontos a confirmar e limites do RF50

O conteúdo não foi conferido com a lista de matrículas do módulo; filtros de plano e de pagamento, mais de um registro e período sem matrículas não foram exercitados.

---

<a id="rf51"></a>

## RF51 — Apresentar o valor a receber no relatório de Contas a Receber

| Campo | Descrição |
| --- | --- |
| Requisito de QA | O relatório de Contas a Receber deve apresentar o valor a receber de cada conta do período e dos filtros informados, com totais coerentes com as linhas. |
| Ator | Usuário autenticado com permissão para gerar relatórios. |
| Pré-condições | Contas a receber pendentes do período conhecidas, com valores. |
| Gatilho | Selecionar "Contas a Receber", Status "Pendente", informar o período e acionar Gerar Relatório. |
| Caso | [CT-RF51](Cenario_Teste/CT-RF51_Relatorio_Contas_Receber.md) |
| Situação observada | Reprovado nas evidências. O PDF lista três contas pendentes, mas a coluna Valor a Receber apresenta "----" em todas as linhas. |
| Defeito | [BUG-022](Relatorio-de-Bugs.md#bug-022), em triagem |
| Evidências | [Jam](https://jam.dev/c/3b4777a4-e1b0-4038-9b06-26c73669d7d1) e [Evidências](Evidencias/CT-RF51_Relatorio_Contas_Receber/README.md). |

### Critérios de aceitação do RF51

1. Cada conta pendente apresenta o valor a receber no relatório.
2. Os totais do relatório correspondem às linhas apresentadas.
3. Os valores coincidem com os do módulo Contas a Receber para as mesmas contas.
4. Rótulos e colunas são legíveis e sem duplicação (por exemplo, "D Vencimento" e "Plano Plano Diário").
5. Sem valor disponível, o relatório apresenta indicação explícita e não um marcador.

### Pontos a confirmar e limites do RF51

Os valores não foram comparados com o módulo Contas a Receber; a opção Detalhado, outros status e o conteúdo da resposta da requisição não foram exercitados. O rótulo "D Vencimento" e a repetição em "Plano Plano Diário" foram observados sem classificação própria.

---

<a id="rf52"></a>

## RF52 — Gerar o relatório de Contas a Pagar (Pagas)

| Campo | Descrição |
| --- | --- |
| Requisito de QA | O relatório de Contas a Pagar (Pagas) deve apresentar as contas pagas do período, com valores bruto e líquido e totalizadores coerentes, ou a estrutura vazia explícita quando não houver pagamentos. |
| Ator | Usuário autenticado com permissão para gerar relatórios. |
| Pré-condições | Contas a pagar pagas do período conhecidas. |
| Gatilho | Selecionar "Contas a Pagar", informar o período e acionar Gerar Relatório. |
| Caso | [CT-RF52](Cenario_Teste/CT-RF52_Relatorio_Contas_Pagar_Pagas.md) |
| Situação observada | A validar — regra ou contexto pendente. O PDF abre com a estrutura do relatório, sem linhas e com totalizadores R$ 0,00, coerente com um período sem contas pagas, a confirmar. |
| Defeito | Sem defeito confirmado |
| Evidências | [Jam](https://jam.dev/c/3b4777a4-e1b0-4038-9b06-26c73669d7d1) e [Evidências](Evidencias/CT-RF52_Relatorio_Contas_Pagar_Pagas/README.md). |

### Critérios de aceitação do RF52

1. O PDF abre e apresenta cabeçalho, período e colunas do relatório.
2. As contas pagas do período aparecem com valores bruto e líquido coerentes com o módulo.
3. Sem contas pagas, o relatório apresenta a estrutura vazia com totalizadores zerados ou mensagem explícita.
4. Os totalizadores correspondem às linhas apresentadas.
5. O título do relatório identifica o filtro aplicado (Pagas).

### Pontos a confirmar e limites do RF52

As contas a pagar do período no módulo não foram conferidas; o comportamento com pagamentos e a regra do escopo do filtro "Pagas" não foram exercitados.

---

<a id="rf53"></a>

## RF53 — Gerar o relatório de Avaliações em PDF

| Campo | Descrição |
| --- | --- |
| Requisito de QA | A geração do relatório de Avaliações deve produzir um PDF válido para o período e os filtros informados, com os registros do período ou a estrutura vazia explícita, e informar falhas ao usuário. |
| Ator | Usuário autenticado com permissão para gerar relatórios. |
| Pré-condições | Período e filtros registrados; base com e sem registros no período conhecida. |
| Gatilho | Selecionar o tipo "Avaliações", informar o período e acionar Gerar Relatório. |
| Caso | [CT-RF53](Cenario_Teste/CT-RF53_Relatorio_Avaliacoes_Vazio.md) |
| Situação observada | Reprovado nas evidências. A requisição retorna HTTP 200, mas o arquivo baixado tem 0 bytes e não abre; nenhuma mensagem de erro foi observada. O defeito é compartilhado com os relatórios de Avaliações, Clientes, Colaboradores e Caixas. |
| Defeito | [BUG-023](Relatorio-de-Bugs.md#bug-023), em triagem |
| Evidências | [Jam](https://jam.dev/c/3b4777a4-e1b0-4038-9b06-26c73669d7d1) e [Evidências](Evidencias/CT-RF53_Relatorio_Avaliacoes_Vazio/README.md). |

### Critérios de aceitação do RF53

1. O arquivo gerado é um PDF válido, com tamanho maior que zero, que abre no visualizador.
2. O relatório apresenta cabeçalho, período, filtros e registros do período.
3. Sem registros, o relatório apresenta a estrutura com totais zerados ou mensagem explícita, sem arquivo vazio.
4. Falhas de geração são informadas ao usuário, sem resposta HTTP 200 com arquivo vazio.
5. O nome e o tipo do arquivo correspondem ao relatório solicitado.

### Pontos a confirmar e limites do RF53

O conteúdo das respostas e a causa não foram capturados. A correspondência entre o arquivo e o tipo é inferida pela ordem dos downloads e dos tipos selecionados no vídeo.

---

<a id="rf54"></a>

## RF54 — Gerar o relatório de Clientes em PDF

| Campo | Descrição |
| --- | --- |
| Requisito de QA | A geração do relatório de Clientes deve produzir um PDF válido para o período e os filtros informados, com os registros do período ou a estrutura vazia explícita, e informar falhas ao usuário. |
| Ator | Usuário autenticado com permissão para gerar relatórios. |
| Pré-condições | Período e filtros registrados; base com e sem registros no período conhecida. |
| Gatilho | Selecionar o tipo "Clientes", informar o período e acionar Gerar Relatório. |
| Caso | [CT-RF54](Cenario_Teste/CT-RF54_Relatorio_Clientes_Vazio.md) |
| Situação observada | Reprovado nas evidências. A requisição retorna HTTP 200, mas o arquivo baixado tem 0 bytes e não abre; nenhuma mensagem de erro foi observada. O defeito é compartilhado com os relatórios de Avaliações, Clientes, Colaboradores e Caixas. |
| Defeito | [BUG-023](Relatorio-de-Bugs.md#bug-023), em triagem |
| Evidências | [Jam](https://jam.dev/c/3b4777a4-e1b0-4038-9b06-26c73669d7d1) e [Evidências](Evidencias/CT-RF54_Relatorio_Clientes_Vazio/README.md). |

### Critérios de aceitação do RF54

1. O arquivo gerado é um PDF válido, com tamanho maior que zero, que abre no visualizador.
2. O relatório apresenta cabeçalho, período, filtros e registros do período.
3. Sem registros, o relatório apresenta a estrutura com totais zerados ou mensagem explícita, sem arquivo vazio.
4. Falhas de geração são informadas ao usuário, sem resposta HTTP 200 com arquivo vazio.
5. O nome e o tipo do arquivo correspondem ao relatório solicitado.

### Pontos a confirmar e limites do RF54

O conteúdo das respostas e a causa não foram capturados. A correspondência entre o arquivo e o tipo é inferida pela ordem dos downloads e dos tipos selecionados no vídeo.

---

<a id="rf55"></a>

## RF55 — Gerar o relatório de Colaboradores em PDF

| Campo | Descrição |
| --- | --- |
| Requisito de QA | A geração do relatório de Colaboradores deve produzir um PDF válido para o período e os filtros informados, com os registros do período ou a estrutura vazia explícita, e informar falhas ao usuário. |
| Ator | Usuário autenticado com permissão para gerar relatórios. |
| Pré-condições | Período e filtros registrados; base com e sem registros no período conhecida. |
| Gatilho | Selecionar o tipo "Colaboradores", informar o período e acionar Gerar Relatório. |
| Caso | [CT-RF55](Cenario_Teste/CT-RF55_Relatorio_Colaboradores_Vazio.md) |
| Situação observada | Reprovado nas evidências. A requisição retorna HTTP 200, mas o arquivo baixado tem 0 bytes e não abre; nenhuma mensagem de erro foi observada. O defeito é compartilhado com os relatórios de Avaliações, Clientes, Colaboradores e Caixas. |
| Defeito | [BUG-023](Relatorio-de-Bugs.md#bug-023), em triagem |
| Evidências | [Jam](https://jam.dev/c/3b4777a4-e1b0-4038-9b06-26c73669d7d1) e [Evidências](Evidencias/CT-RF55_Relatorio_Colaboradores_Vazio/README.md). |

### Critérios de aceitação do RF55

1. O arquivo gerado é um PDF válido, com tamanho maior que zero, que abre no visualizador.
2. O relatório apresenta cabeçalho, período, filtros e registros do período.
3. Sem registros, o relatório apresenta a estrutura com totais zerados ou mensagem explícita, sem arquivo vazio.
4. Falhas de geração são informadas ao usuário, sem resposta HTTP 200 com arquivo vazio.
5. O nome e o tipo do arquivo correspondem ao relatório solicitado.

### Pontos a confirmar e limites do RF55

O conteúdo das respostas e a causa não foram capturados. A correspondência entre o arquivo e o tipo é inferida pela ordem dos downloads e dos tipos selecionados no vídeo.

---

<a id="rf56"></a>

## RF56 — Gerar o relatório de Caixas em PDF

| Campo | Descrição |
| --- | --- |
| Requisito de QA | A geração do relatório de Caixas deve produzir um PDF válido para o período e os filtros informados, com os registros do período ou a estrutura vazia explícita, e informar falhas ao usuário. |
| Ator | Usuário autenticado com permissão para gerar relatórios. |
| Pré-condições | Período e filtros registrados; base com e sem registros no período conhecida. |
| Gatilho | Selecionar o tipo "Caixas", informar o período e acionar Gerar Relatório. |
| Caso | [CT-RF56](Cenario_Teste/CT-RF56_Relatorio_Caixas_Vazio.md) |
| Situação observada | Reprovado nas evidências. A requisição retorna HTTP 200, mas o arquivo baixado tem 0 bytes e não abre; nenhuma mensagem de erro foi observada. O defeito é compartilhado com os relatórios de Avaliações, Clientes, Colaboradores e Caixas. |
| Defeito | [BUG-023](Relatorio-de-Bugs.md#bug-023), em triagem |
| Evidências | [Jam](https://jam.dev/c/3b4777a4-e1b0-4038-9b06-26c73669d7d1) e [Evidências](Evidencias/CT-RF56_Relatorio_Caixas_Vazio/README.md). |

### Critérios de aceitação do RF56

1. O arquivo gerado é um PDF válido, com tamanho maior que zero, que abre no visualizador.
2. O relatório apresenta cabeçalho, período, filtros e registros do período.
3. Sem registros, o relatório apresenta a estrutura com totais zerados ou mensagem explícita, sem arquivo vazio.
4. Falhas de geração são informadas ao usuário, sem resposta HTTP 200 com arquivo vazio.
5. O nome e o tipo do arquivo correspondem ao relatório solicitado.

### Pontos a confirmar e limites do RF56

O conteúdo das respostas e a causa não foram capturados. A correspondência entre o arquivo e o tipo é inferida pela ordem dos downloads e dos tipos selecionados no vídeo.

---

## RF57 — Excluir grupo ou explicar o impedimento

| Campo | Descrição |
| --- | --- |
| Requisito de QA | A exclusão de um grupo deve ser concluída quando permitida, removendo o registro da listagem e atualizando os contadores; quando houver impedimento de regra, o sistema deve informá-lo de forma específica e tratável, sem erro interno do servidor. |
| Ator | Usuário autenticado com permissão em Grupos. |
| Pré-condições | Listagem carregada, registro de teste conhecido e vínculos desse registro identificados antes da execução. |
| Gatilho | Acionar a ação de exclusão na linha do registro e confirmar no diálogo "Deseja deletar o Grupo?". |
| Caso | [CT-RF57](Cenario_Teste/CT-RF57_Exclusao_Grupo.md) |
| Situação observada | Reprovado nas evidências. Duas tentativas de exclusão retornam HTTP 500 com o corpo "Erro interno inesperado."; o registro permanece na listagem e os contadores não se alteram. A mensagem e o padrão do erro coincidem com os já registrados no RF29 para grupos musculares. |
| Defeito | [BUG-024](Relatorio-de-Bugs.md#bug-024), em triagem |
| Evidências | [Jam](https://jam.dev/c/b1231a75-1a65-4bf0-b795-f52a8c7d3365). |

### Critérios de aceitação do RF57

1. A ação de exclusão apresenta confirmação explícita antes de efetivar a operação.
2. A exclusão permitida remove o registro da listagem e atualiza os contadores do resumo.
3. O impedimento de regra é comunicado com mensagem específica, sem erro interno do servidor.
4. Nenhum cenário de exclusão retorna HTTP 500.
5. O resultado se mantém após recarga da página.

### Pontos a confirmar e limites do RF57

Não foram consultados logs do servidor, corpo completo da resposta além dos 64 bytes retornados nem o banco de dados; a causa do HTTP 500 permanece indeterminada. Não foi possível confirmar visualmente o texto do diálogo de erro apresentado após a falha, pois o componente de alerta é fechado em menos de um segundo na gravação. Não foi confirmado se o registro permanece íntegro após as duas tentativas enviadas para o mesmo recurso. O cenário de exclusão com impedimento de regra não foi exercitado.

---

## RF58 — Persistir todos os campos editados de um grupo

| Campo | Descrição |
| --- | --- |
| Requisito de QA | Ao salvar a edição de um grupo, todo campo alterado deve ser persistido pelo backend; uma resposta de sucesso não deve ser retornada para uma alteração que não foi efetivamente salva. |
| Ator | Usuário autenticado com permissão em Grupos. |
| Pré-condições | Grupo de teste conhecido, com todos os campos atuais registrados antes da edição. |
| Gatilho | Abrir a edição do grupo, alterar um campo isoladamente (por exemplo, Status) e acionar Salvar. |
| Caso | [CT-RF58](Cenario_Teste/CT-RF58_Edicao_Grupo.md) |
| Situação observada | Reprovado nas evidências. A alteração do campo Status de "Ativo" para "Inativo" retorna sucesso (`verifica_erro: false`), mas a consulta imediatamente seguinte mostra o registro ainda com status "Ativo". Na mesma sessão e no mesmo registro, a alteração do campo Descrição é persistida corretamente, descartando falha geral de salvamento, sessão ou rede. |
| Defeito | [BUG-025](Relatorio-de-Bugs.md#bug-025), em triagem |
| Evidências | [Jam](https://jam.dev/c/b1231a75-1a65-4bf0-b795-f52a8c7d3365). |

### Critérios de aceitação do RF58

1. A edição de qualquer campo do grupo retorna sucesso somente quando o valor é efetivamente persistido.
2. O campo Status, especificamente, é persistido ao ser alterado e confirmado por consulta subsequente.
3. Uma resposta de sucesso nunca é retornada para uma alteração que não foi salva.
4. O resultado se mantém após recarga da página e nova consulta ao registro.
5. O comportamento é validado também para outros grupos e, se aplicável, para a entidade grupo muscular.

### Pontos a confirmar e limites do RF58

Não houve acesso a logs do servidor, ao código da rotina de edição nem ao banco de dados para confirmar o valor realmente gravado. A causa da falha isolada no campo `status` não foi determinada: pode ser uma whitelist de campos editáveis que exclui esse campo, uma rotina de atualização que o ignora silenciosamente, ou outra causa não identificada. Foi observado também um descompasso de cerca de 4 horas entre o cabeçalho HTTP `data` e o campo `updated_at` da resposta, sem relação confirmada com o defeito.

---

## RF59 — Cadastrar anamnese sem erro de servidor

| Campo | Descrição |
| --- | --- |
| Requisito de QA | Ao preencher as respostas de um modelo de anamnese e acionar "Salvar rascunho" ou a aplicação definitiva, o backend deve gravar o registro e retornar sucesso, sem erro genérico de servidor. |
| Ator | Usuário autenticado com permissão em Fichas de Anamnese. |
| Pré-condições | Aluno cadastrado e selecionável; modelo de anamnese com ao menos uma pergunta cadastrada. |
| Gatilho | Selecionar aluno e modelo, responder à(s) pergunta(s) e acionar "Salvar rascunho" ou a aplicação definitiva da anamnese. |
| Caso | [CT-RF59](Cenario_Teste/CT-RF59_Cadastro_Anamnese.md) |
| Situação observada | Reprovado nas evidências. As sete tentativas registradas na gravação (quatro em `/api/anamnese/aplicar/{id}` e três em `/api/anamnese/rascunho/{id}`) retornam HTTP 500 com a mesma mensagem genérica, independentemente do modelo de anamnese ou da resposta informada; nenhuma anamnese é cadastrada com sucesso. |
| Defeito | [BUG-032](Relatorio-de-Bugs.md#bug-032), em triagem |
| Evidências | [Jam](https://jam.dev/c/7be0fe71-3419-4050-b63f-473d943fa08e). |

### Critérios de aceitação do RF59

1. Ao preencher corretamente as respostas de um modelo e acionar "Salvar rascunho", o backend grava o rascunho e retorna sucesso.
2. Ao preencher corretamente as respostas e acionar a aplicação definitiva, o backend grava a anamnese com `status: "concluida"` e retorna sucesso.
3. O comportamento é validado para mais de um modelo de anamnese e mais de um aluno.
4. Uma anamnese salva com sucesso fica disponível para consulta na listagem.
5. Um erro de validação específico (por exemplo, pergunta sem resposta) não deve ser reportado como "Erro interno inesperado.".

### Pontos a confirmar e limites do RF59

Não houve acesso a logs do servidor, ao código das rotinas de aplicar/rascunho nem ao banco de dados; a causa real do HTTP 500 não foi determinada. O padrão de resposta é idêntico ao já registrado em [BUG-016](Relatorio-de-Bugs.md#bug-016) e [BUG-024](Relatorio-de-Bugs.md#bug-024), o que sugere tratamento de erro genérico no backend, mas não foi confirmado se a causa de fundo é a mesma. Não foi confirmado se as tentativas de rascunho afetaram o mesmo registro ou criaram registros distintos.
<a id="rf85"></a>

## RF85 — Alternar o tema e consultar as notificações no cabeçalho

| Campo | Descrição |
| --- | --- |
| Requisito de QA | O cabeçalho da tela Prospecção deve permitir alternar o tema claro e escuro, gravando a escolha do usuário, e abrir o painel de notificações com o estado correspondente às pendências. |
| Ator | Usuário autenticado com acesso a Prospecção. |
| Pré-condições | Sessão autenticada; tema inicial e notificações conhecidos. |
| Gatilho | Acionar o alternador de tema e o sino do cabeçalho. |
| Caso | [CT-RF85](Cenario_Teste/CT-RF85_Tema_Notificacoes_Prospeccao.md) |
| Situação observada | Aprovado conforme a gravação. O tema escuro é aplicado e o claro restaurado, com POST usuario/tema (HTTP 200) a cada troca; o painel de Notificações abre sem pendências. |
| Defeito | Nenhum no fluxo avaliado |
| Evidências | [Jam](https://jam.dev/c/308607ff-8abc-40af-8c7c-429ce506ed64) e [Evidências](Evidencias/CT-RF85_Tema_Notificacoes_Prospeccao/README.md). |

### Critérios de aceitação do RF85

1. Cada acionamento do alternador troca o tema da interface sem perda de legibilidade.
2. Cada troca de tema é gravada no servidor e permanece após recarregar a página.
3. O sino abre o painel de Notificações com as abas Tudo e Não lidas.
4. Sem pendências, o painel apresenta mensagem explícita de estado vazio.
5. Com pendências, o painel lista os itens e permite marcá-los como lidos.

### Pontos a confirmar e limites do RF85

A persistência do tema após recarga, as notificações pendentes e a ação Marcar como lidas não foram exercitadas; o contraste do tema escuro é tratado no [RF14](#rf14).

---

<a id="rf86"></a>

## RF86 — Buscar leads por texto na listagem de Prospecção

| Campo | Descrição |
| --- | --- |
| Requisito de QA | O campo Buscar lead deve filtrar a listagem por nome, e-mail, telefone ou código, apresentando apenas os leads correspondentes e restaurando a listagem completa ao limpar o termo. |
| Ator | Usuário autenticado com acesso a Prospecção. |
| Pré-condições | Base de leads conhecida, com nomes, contatos e códigos registrados. |
| Gatilho | Digitar um termo no campo Buscar lead e, depois, apagá-lo. |
| Caso | [CT-RF86](Cenario_Teste/CT-RF86_Busca_Leads_Prospeccao.md) |
| Situação observada | Aprovado conforme a gravação. A busca retorna os leads de códigos 3 e 7 em 0:12 e os leads 4 e 10 para "tes" em 0:44; o campo vazio restaura a listagem completa. |
| Defeito | Nenhum no fluxo avaliado |
| Evidências | [Jam](https://jam.dev/c/308607ff-8abc-40af-8c7c-429ce506ed64) e [Evidências](Evidencias/CT-RF86_Busca_Leads_Prospeccao/README.md). |

### Critérios de aceitação do RF86

1. O campo Buscar lead filtra por nome, e-mail, telefone e código conforme o rótulo do campo.
2. A busca não diferencia maiúsculas de minúsculas.
3. Os cartões acompanham ou não o filtro de acordo com o contrato definido.
4. Ao apagar o termo, a listagem completa é restaurada.
5. Um termo sem correspondência apresenta mensagem explícita de resultado vazio.

### Pontos a confirmar e limites do RF86

O termo vigente em 0:12 não foi identificado com certeza; a regra de correspondência, a busca por e-mail, telefone e código e o resultado vazio não foram exercitados. A busca não gera requisição de rede, compatível com filtragem local, sem confirmação. O contrato dos cartões não foi fornecido, como no [RF11](#rf11).

---

<a id="rf87"></a>

## RF87 — Filtrar leads por estágio e restaurar a listagem

| Campo | Descrição |
| --- | --- |
| Requisito de QA | O seletor Estágio deve apresentar apenas os leads do estágio escolhido e o botão Limpar deve restaurar o seletor e a listagem completa. |
| Ator | Usuário autenticado com acesso a Prospecção. |
| Pré-condições | Base de leads conhecida, com estágios registrados. |
| Gatilho | Selecionar um estágio e, depois, acionar Limpar. |
| Caso | [CT-RF87](Cenario_Teste/CT-RF87_Filtro_Estagio_Leads.md) |
| Situação observada | Aprovado conforme a gravação. "Novo Contato" apresenta os leads 7 e 8 e "Proposta" o lead 4; Limpar restaura a listagem completa. |
| Defeito | Nenhum no fluxo avaliado |
| Evidências | [Jam](https://jam.dev/c/308607ff-8abc-40af-8c7c-429ce506ed64) e [Evidências](Evidencias/CT-RF87_Filtro_Estagio_Leads/README.md). |

### Critérios de aceitação do RF87

1. Cada estágio apresenta apenas os leads desse estágio.
2. O número de linhas de um estágio coincide com o indicador correspondente, quando existir.
3. O botão Limpar restaura o seletor para Todos e a listagem completa.
4. Um estágio sem leads apresenta mensagem explícita de resultado vazio.
5. O filtro combina corretamente com a busca por texto.

### Pontos a confirmar e limites do RF87

Os demais estágios, a combinação com a busca por texto, o estágio sem leads e a lista completa de estágios do seletor não foram exercitados. O filtro não gera requisição de rede, compatível com filtragem local, sem confirmação.

---

<a id="rf88"></a>

## RF88 — Cadastrar um lead com uma única gravação

| Campo | Descrição |
| --- | --- |
| Requisito de QA | O formulário Adicionar Lead deve criar o lead informado uma única vez, apresentá-lo na listagem com o estágio escolhido e atualizar os cartões de resumo. |
| Ator | Usuário autenticado com acesso a Prospecção. |
| Pré-condições | Base de leads conhecida; dados de teste descartáveis. |
| Gatilho | Preencher o formulário Adicionar Lead e acionar Salvar Lead. |
| Caso | [CT-RF88](Cenario_Teste/CT-RF88_Cadastro_Lead_Prospeccao.md) |
| Situação observada | A validar — regra ou contexto pendente. O lead de código 10 é criado e listado (Leads 7 → 8), mas um clique gera dois POST salvar-lead/1 com HTTP 200. |
| Defeito | Sem defeito confirmado |
| Evidências | [Jam](https://jam.dev/c/308607ff-8abc-40af-8c7c-429ce506ed64) e [Evidências](Evidencias/CT-RF88_Cadastro_Lead_Prospeccao/README.md). |

### Critérios de aceitação do RF88

1. Um clique em Salvar Lead gera uma única requisição de criação.
2. O lead é gravado uma única vez e aparece na listagem com o estágio informado.
3. Os cartões Leads e do estágio acompanham o novo registro.
4. O botão é protegido contra segundo envio enquanto a requisição está em andamento.
5. Após recarga, a listagem contém um único lead com os dados informados.

### Pontos a confirmar e limites do RF88

O corpo e a resposta da segunda requisição, a persistência após recarga, os campos obrigatórios e as validações de formato não foram verificados. O mesmo padrão ocorre no [RF47](#rf47); a duplicidade não está confirmada.

---

<a id="rf89"></a>

## RF89 — Validar o telefone do lead

| Campo | Descrição |
| --- | --- |
| Requisito de QA | O campo Telefone do formulário de lead deve aceitar apenas valores no formato definido pelo produto (por exemplo, (00) 00000-0000) e rejeitar tamanhos e caracteres inválidos com mensagem clara. |
| Ator | Usuário autenticado com acesso a Prospecção. |
| Pré-condições | Formulário Adicionar Lead aberto; regra do campo definida com o produto. |
| Gatilho | Informar um telefone com 30 dígitos e acionar Salvar Lead. |
| Caso | [CT-RF89](Cenario_Teste/CT-RF89_Telefone_Lead_Sem_Validacao.md) |
| Situação observada | Reprovado nas evidências. O telefone de 30 dígitos é aceito, gravado (lead 10) e devolvido na consulta, sem máscara nem mensagem de validação. |
| Defeito | [BUG-038](Relatorio-de-Bugs.md#bug-038), em triagem |
| Evidências | [Jam](https://jam.dev/c/308607ff-8abc-40af-8c7c-429ce506ed64) e [Evidências](Evidencias/CT-RF89_Telefone_Lead_Sem_Validacao/README.md). |

### Critérios de aceitação do RF89

1. O campo Telefone limita o tamanho e os caracteres ao formato definido pelo produto.
2. Um telefone com tamanho ou caracteres inválidos é rejeitado antes da gravação, com mensagem clara.
3. A máscara exibida no placeholder é aplicada durante a digitação.
4. O servidor valida o telefone independentemente da interface.
5. O telefone válido é gravado e exibido no formato definido.

### Pontos a confirmar e limites do RF89

A regra do campo e a validação no servidor não foram informadas ou verificadas; se o campo for livre, o placeholder "(00) 00000-0000" deve ser revisto. Telefones de outros tamanhos e valores com letras não foram exercitados.

---

<a id="rf90"></a>

## RF90 — Visualizar e editar um lead

| Campo | Descrição |
| --- | --- |
| Requisito de QA | A lupa da listagem deve abrir os dados do lead e permitir a alteração dos campos, gravando a alteração sem erro e refletindo-a na listagem. |
| Ator | Usuário autenticado com acesso a Prospecção. |
| Pré-condições | Lead descartável cadastrado e visível na listagem. |
| Gatilho | Acionar a lupa do lead, alterar o nome e acionar Salvar Lead. |
| Caso | [CT-RF90](Cenario_Teste/CT-RF90_Edicao_Lead_Prospeccao.md) |
| Situação observada | Aprovado conforme a gravação. O modal abre com os dados do lead 10, o nome é atualizado para "testetete" com HTTP 200 e a listagem apresenta o novo nome. |
| Defeito | Nenhum no fluxo avaliado |
| Evidências | [Jam](https://jam.dev/c/308607ff-8abc-40af-8c7c-429ce506ed64) e [Evidências](Evidencias/CT-RF90_Edicao_Lead_Prospeccao/README.md). |

### Critérios de aceitação do RF90

1. A lupa abre o modal com os dados do lead selecionado.
2. A alteração de qualquer campo é enviada ao servidor e gravada sem erro.
3. A listagem reflete o novo valor sem recarga manual.
4. O valor permanece após recarregar a página.
5. O título do modal corresponde à ação disponível (visualizar ou editar).

### Pontos a confirmar e limites do RF90

A edição dos demais campos, a persistência após recarga, os campos obrigatórios e a revisão do título "Visualizar Lead" em um modal editável não foram exercitadas.

---

<a id="rf91"></a>

## RF91 — Filtrar contas a pagar por nome, data e status

| Campo | Descrição |
| --- | --- |
| Requisito de QA | A listagem de Contas a Pagar deve apresentar apenas as contas que atendam aos critérios de código, nome, tipo de data, período e status informados, com cartões coerentes e mensagem explícita de resultado vazio. |
| Ator | Usuário autenticado com acesso ao módulo. |
| Pré-condições | Base de contas conhecida, com nomes, datas e status registrados. |
| Gatilho | Informar critérios e acionar Buscar. |
| Caso | [CT-RF91](Cenario_Teste/CT-RF91_Filtros_Contas_Pagar.md) |
| Situação observada | A validar — regra ou contexto pendente. A combinação Nome "teste", Pagamento, 06/11/2026 e Pago deixa a listagem vazia, compatível com os critérios, sem dado de controle. |
| Defeito | Sem defeito confirmado |
| Evidências | [Jam](https://jam.dev/c/5d0afaf4-5abd-4e85-923f-27448304a9ef) e [Evidências](Evidencias/CT-RF91_Filtros_Contas_Pagar/README.md). |

### Critérios de aceitação do RF91

1. Cada critério isolado (nome, tipo de data, período e status) filtra corretamente a listagem.
2. A combinação de critérios aplica todos eles simultaneamente.
3. Os cartões acompanham o conjunto exibido conforme o contrato definido.
4. O resultado vazio apresenta mensagem explícita.
5. Limpar os critérios restaura a listagem do período.

### Pontos a confirmar e limites do RF91

Cada critério isolado, a troca de Tipo de Data e o resultado vazio contra a base não foram verificados; o corpo da busca principal não foi capturado.

---

<a id="rf92"></a>

## RF92 — Exigir o colaborador no cadastro de conta a pagar a colaborador

| Campo | Descrição |
| --- | --- |
| Requisito de QA | O formulário Cadastrar Conta a Pagar deve exigir o colaborador favorecido quando o tipo for Pagto. Colaborador, com mensagem clara e rejeição também no servidor. |
| Ator | Usuário autenticado com acesso ao módulo. |
| Pré-condições | Formulário aberto com o tipo Pagto. Colaborador; regra de obrigatoriedade definida com o produto. |
| Gatilho | Preencher o formulário sem colaborador e acionar Salvar. |
| Caso | [CT-RF92](Cenario_Teste/CT-RF92_Cadastro_Conta_Colaborador_Sem_Colaborador.md) |
| Situação observada | Reprovado nas evidências. A conta é gravada (HTTP 201) com colaborador vazio e listada com "-" no colaborador, sem mensagem de validação. |
| Defeito | [BUG-039](Relatorio-de-Bugs.md#bug-039), em triagem |
| Evidências | [Jam](https://jam.dev/c/5d0afaf4-5abd-4e85-923f-27448304a9ef) e [Evidências](Evidencias/CT-RF92_Cadastro_Conta_Colaborador_Sem_Colaborador/README.md). |

### Critérios de aceitação do RF92

1. Conta do tipo Pagto. Colaborador exige o colaborador antes da gravação.
2. A ausência do colaborador gera mensagem de validação junto ao campo.
3. O servidor rejeita a criação sem colaborador, independentemente da interface.
4. A listagem apresenta o colaborador na coluna Fornecedor / Colaborador.
5. Conta com colaborador informado é gravada e listada corretamente.

### Pontos a confirmar e limites do RF92

A regra de obrigatoriedade e a validação no servidor não foram verificadas; o tipo fornecedor sem fornecedor não foi exercitado.

---

<a id="rf93"></a>

## RF93 — Buscar e selecionar colaborador no cadastro de conta

| Campo | Descrição |
| --- | --- |
| Requisito de QA | O modal Buscar Colaborador deve listar os colaboradores correspondentes ao nome informado, permitir a seleção e informar explicitamente quando não houver resultado. |
| Ator | Usuário autenticado com acesso ao módulo. |
| Pré-condições | Colaboradores cadastrados; modal aberto a partir do tipo Pagto. Colaborador. |
| Gatilho | Informar um nome no modal e acionar Pesquisar. |
| Caso | [CT-RF93](Cenario_Teste/CT-RF93_Busca_Colaborador_Conta_Pagar.md) |
| Situação observada | A validar — regra ou contexto pendente. O termo "sds" devolve lista vazia, sem mensagem visível; a busca com resultado e a seleção não foram exercitadas. |
| Defeito | Sem defeito confirmado |
| Evidências | [Jam](https://jam.dev/c/5d0afaf4-5abd-4e85-923f-27448304a9ef) e [Evidências](Evidencias/CT-RF93_Busca_Colaborador_Conta_Pagar/README.md). |

### Critérios de aceitação do RF93

1. A busca lista os colaboradores cujo nome contenha o termo.
2. A seleção preenche Código e Colaborador no formulário.
3. Sem correspondência, o modal apresenta mensagem explícita.
4. O modal pode ser fechado sem alterar o formulário.
5. O colaborador selecionado é gravado na conta.

### Pontos a confirmar e limites do RF93

A busca com resultado, a seleção e a mensagem de resultado vazio esperada não foram verificadas.

---

<a id="rf94"></a>

## RF94 — Visualizar os dados de uma conta a pagar

| Campo | Descrição |
| --- | --- |
| Requisito de QA | A lupa da listagem deve abrir os dados da conta selecionada, com informações gerais, dados da conta, do colaborador ou fornecedor e do documento, em rótulos legíveis. |
| Ator | Usuário autenticado com acesso ao módulo. |
| Pré-condições | Conta a pagar cadastrada e visível na listagem. |
| Gatilho | Acionar a lupa da linha da conta. |
| Caso | [CT-RF94](Cenario_Teste/CT-RF94_Visualizacao_Conta_Pagar.md) |
| Situação observada | Aprovado conforme a gravação. O modal apresenta os dados da conta 29 e fecha corretamente; o tipo aparece como "PAG_COLABORADOR". |
| Defeito | Nenhum no fluxo avaliado |
| Evidências | [Jam](https://jam.dev/c/5d0afaf4-5abd-4e85-923f-27448304a9ef) e [Evidências](Evidencias/CT-RF94_Visualizacao_Conta_Pagar/README.md). |

### Critérios de aceitação do RF94

1. O modal apresenta os dados da conta selecionada conforme gravados.
2. Os rótulos exibidos ao usuário são legíveis (sem códigos internos).
3. As seções do colaborador ou do fornecedor apresentam o favorecido quando informado.
4. O botão Fechar retorna à listagem sem alterações.
5. A consulta não altera a conta.

### Pontos a confirmar e limites do RF94

Contas de fornecedor, pagas e atrasadas e o rótulo esperado do tipo não foram exercitados.

---

<a id="rf95"></a>

## RF95 — Excluir uma conta a pagar com confirmação

| Campo | Descrição |
| --- | --- |
| Requisito de QA | A lixeira da listagem deve exigir confirmação e, confirmada, remover a conta sem erro, atualizando a listagem e os cartões. |
| Ator | Usuário autenticado com acesso ao módulo. |
| Pré-condições | Conta a pagar descartável cadastrada. |
| Gatilho | Acionar a lixeira da conta e confirmar o diálogo. |
| Caso | [CT-RF95](Cenario_Teste/CT-RF95_Exclusao_Conta_Pagar.md) |
| Situação observada | Aprovado conforme a gravação. O diálogo pede confirmação e `deletar-conta-pagar` retorna HTTP 200 sem erro; a conta 29 deixa a listagem. |
| Defeito | Nenhum no fluxo avaliado |
| Evidências | [Jam](https://jam.dev/c/5d0afaf4-5abd-4e85-923f-27448304a9ef) e [Evidências](Evidencias/CT-RF95_Exclusao_Conta_Pagar/README.md). |

### Critérios de aceitação do RF95

1. A exclusão exige confirmação do usuário.
2. Cancelar preserva a conta.
3. Confirmar remove a conta sem erro e atualiza a listagem e os cartões.
4. A conta excluída não reaparece após recarga.
5. Contas vinculadas a pagamentos ou ao caixa têm tratamento explícito.

### Pontos a confirmar e limites do RF95

Cancelar, recarga após a exclusão e contas pagas ou vinculadas não foram exercitados.

---

<a id="rf96"></a>

## RF96 — Inserir variáveis e pré-visualizar o contrato

| Campo | Descrição |
| --- | --- |
| Requisito de QA | O editor do modelo de contrato deve inserir as variáveis clicadas e a pré-visualização deve substituí-las por dados de exemplo, preservando a formatação. |
| Ator | Usuário autenticado com acesso ao módulo. |
| Pré-condições | Editor de modelo de contrato aberto; variáveis disponíveis. |
| Gatilho | Clicar em variáveis e acionar Atualizar preview. |
| Caso | [CT-RF96](Cenario_Teste/CT-RF96_Variaveis_Preview_Modelo_Contrato.md) |
| Situação observada | Aprovado conforme a gravação. As variáveis {numero_contrato}, {nome_aluno} e {cpf_aluno} são inseridas e a pré-visualização apresenta "2024/001 João da Silva 123.456.789-00". |
| Defeito | Nenhum no fluxo avaliado |
| Evidências | [Jam](https://jam.dev/c/44dbbd39-6915-45d6-8dd1-5f30c1432ca0) e [Evidências](Evidencias/CT-RF96_Variaveis_Preview_Modelo_Contrato/README.md). |

### Critérios de aceitação do RF96

1. Cada variável clicada é inserida no ponto do cursor do editor.
2. A pré-visualização substitui as variáveis por dados de exemplo coerentes.
3. A formatação do texto é preservada na pré-visualização.
4. Todas as variáveis dos quatro grupos funcionam.
5. As variáveis permanecem no texto após salvar.

### Pontos a confirmar e limites do RF96

As demais variáveis, a formatação complexa e o texto gravado não foram exercitados.

---

<a id="rf97"></a>

## RF97 — Cadastrar um modelo de contrato

| Campo | Descrição |
| --- | --- |
| Requisito de QA | O formulário Adicionar Modelo Contrato deve criar o modelo com título, status e texto informados e devolvê-lo na lista de modelos. |
| Ator | Usuário autenticado com acesso ao módulo. |
| Pré-condições | Formulário preenchido; modelos existentes conhecidos. |
| Gatilho | Preencher título, status e texto e acionar Salvar modelo. |
| Caso | [CT-RF97](Cenario_Teste/CT-RF97_Cadastro_Modelo_Contrato.md) |
| Situação observada | Aprovado conforme a gravação. `modelo-contrato/salvar` retorna HTTP 201 e o servidor passa a listar o modelo de id 15 ("teste eduardo", Ativo). |
| Defeito | Nenhum no fluxo avaliado |
| Evidências | [Jam](https://jam.dev/c/44dbbd39-6915-45d6-8dd1-5f30c1432ca0) e [Evidências](Evidencias/CT-RF97_Cadastro_Modelo_Contrato/README.md). |

### Critérios de aceitação do RF97

1. Salvar com dados válidos cria o modelo e retorna sucesso.
2. O modelo criado é devolvido pelo servidor na lista de modelos.
3. A listagem na tela apresenta o modelo criado.
4. Título e texto obrigatórios são validados antes da gravação.
5. O texto e as variáveis são gravados sem perda.

### Pontos a confirmar e limites do RF97

O corpo da criação, o texto gravado, os campos obrigatórios e a apresentação na listagem não foram verificados.

---

<a id="rf98"></a>

## RF98 — Apresentar na listagem os modelos de contrato retornados pelo servidor

| Campo | Descrição |
| --- | --- |
| Requisito de QA | A tela Modelos Contrato deve apresentar uma linha com código, nome e status para cada modelo retornado pelo servidor, inclusive o recém-criado, ou uma mensagem explícita quando não houver modelos. |
| Ator | Usuário autenticado com acesso ao módulo. |
| Pré-condições | Modelos de contrato existentes no servidor. |
| Gatilho | Acessar Modelos Contrato e, depois, criar um modelo. |
| Caso | [CT-RF98](Cenario_Teste/CT-RF98_Listagem_Modelos_Contrato_Vazia.md) |
| Situação observada | Reprovado nas evidências. O servidor devolve 15 modelos, mas a tabela permanece com apenas o cabeçalho, sem linhas e sem mensagem. |
| Defeito | [BUG-040](Relatorio-de-Bugs.md#bug-040), em triagem |
| Evidências | [Jam](https://jam.dev/c/44dbbd39-6915-45d6-8dd1-5f30c1432ca0) e [Evidências](Evidencias/CT-RF98_Listagem_Modelos_Contrato_Vazia/README.md). |

### Critérios de aceitação do RF98

1. A tabela apresenta uma linha para cada modelo retornado pelo servidor.
2. O modelo recém-criado aparece na listagem sem recarregar manualmente.
3. Código, nome e status são exibidos corretamente.
4. Sem modelos, a tela apresenta mensagem explícita de estado vazio.
5. A listagem permanece correta após recarregar a página.

### Pontos a confirmar e limites do RF98

A causa e o comportamento após recarga não foram confirmados; a lista completa foi lida por texto.

---

<a id="rf99"></a>

## RF99 — Filtrar planos por código e por nome

| Campo | Descrição |
| --- | --- |
| Requisito de QA | A listagem de Planos deve apresentar apenas os planos que atendam aos critérios de código, nome e status e restaurar a listagem completa ao limpar os campos. |
| Ator | Usuário autenticado com acesso ao módulo. |
| Pré-condições | Base de planos conhecida, com códigos, nomes e status registrados. |
| Gatilho | Informar código ou nome e, depois, limpar os campos. |
| Caso | [CT-RF99](Cenario_Teste/CT-RF99_Filtros_Planos.md) |
| Situação observada | Aprovado conforme a gravação. O código "7" lista os planos 37, 7 e 67 e o nome "a" lista planos de nomes aba e Aba; Buscar recarrega a listagem. |
| Defeito | Nenhum no fluxo avaliado |
| Evidências | [Jam](https://jam.dev/c/233c5d21-e108-4a55-b6f6-8738cb3fc6a6) e [Evidências](Evidencias/CT-RF99_Filtros_Planos/README.md). |

### Critérios de aceitação do RF99

1. O filtro por código retorna os planos cujo código contenha o critério.
2. O filtro por nome retorna os planos cujo nome contenha o critério, sem diferenciar maiúsculas.
3. O seletor Status filtra a listagem conforme a opção.
4. Limpar os campos restaura a listagem completa.
5. Critérios sem correspondência apresentam mensagem explícita.

### Pontos a confirmar e limites do RF99

O filtro por Status, a combinação de critérios, o resultado vazio e o contrato dos cartões não foram exercitados.

---

<a id="rf100"></a>

## RF100 — Alternar o tema e consultar as notificações na tela Planos

| Campo | Descrição |
| --- | --- |
| Requisito de QA | O cabeçalho da tela Planos deve permitir alternar o tema, gravando a escolha, e abrir o painel de notificações com o estado correspondente. |
| Ator | Usuário autenticado com acesso ao módulo. |
| Pré-condições | Sessão autenticada; tema inicial e notificações conhecidos. |
| Gatilho | Acionar o alternador de tema e o sino. |
| Caso | [CT-RF100](Cenario_Teste/CT-RF100_Tema_Notificacoes_Planos.md) |
| Situação observada | Aprovado conforme a gravação. O tema escuro é aplicado e o claro restaurado, com POST usuario/tema (HTTP 200) a cada troca; o painel de Notificações abre sem pendências. |
| Defeito | Nenhum no fluxo avaliado |
| Evidências | [Jam](https://jam.dev/c/233c5d21-e108-4a55-b6f6-8738cb3fc6a6) e [Evidências](Evidencias/CT-RF100_Tema_Notificacoes_Planos/README.md). |

### Critérios de aceitação do RF100

1. Cada acionamento troca o tema sem perda de legibilidade.
2. Cada troca é gravada no servidor e permanece após recarregar.
3. O sino abre o painel de Notificações com as abas Tudo e Não lidas.
4. Sem pendências, o painel apresenta mensagem explícita.
5. Com pendências, o painel lista os itens.

### Pontos a confirmar e limites do RF100

A persistência após recarga e as notificações pendentes não foram exercitadas.

---

<a id="rf101"></a>

## RF101 — Cadastrar um plano

| Campo | Descrição |
| --- | --- |
| Requisito de QA | O modal Novo Plano deve criar o plano com os dados informados, devolver o identificador e atualizar o contador de planos e a listagem. |
| Ator | Usuário autenticado com acesso ao módulo. |
| Pré-condições | Modal Novo Plano preenchido; base de planos conhecida. |
| Gatilho | Preencher o modal e acionar Salvar Plano. |
| Caso | [CT-RF101](Cenario_Teste/CT-RF101_Cadastro_Plano.md) |
| Situação observada | Aprovado conforme a gravação. `plano/salvar` retorna HTTP 200 com o id 66 e o cartão Planos passa de 40 para 41. |
| Defeito | Nenhum no fluxo avaliado |
| Evidências | [Jam](https://jam.dev/c/233c5d21-e108-4a55-b6f6-8738cb3fc6a6) e [Evidências](Evidencias/CT-RF101_Cadastro_Plano/README.md). |

### Critérios de aceitação do RF101

1. Salvar com dados válidos cria o plano e retorna o identificador.
2. O contador de planos acompanha o cadastro.
3. A listagem apresenta o plano criado com os dados informados.
4. Campos obrigatórios em branco são validados antes da gravação.
5. Os benefícios informados são gravados com o plano.

### Pontos a confirmar e limites do RF101

A linha do plano na listagem, os campos obrigatórios e os benefícios não foram verificados; o cartão Ativos é tratado no RF102.

---

<a id="rf102"></a>

## RF102 — Manter o cartão Ativos coerente com o status dos planos

| Campo | Descrição |
| --- | --- |
| Requisito de QA | O cartão Ativos da tela Planos deve contar apenas planos com status ativo e não aumentar ao cadastrar ou editar planos inativos, enquanto o cartão Planos acompanha o total de registros. |
| Ator | Usuário autenticado com acesso ao módulo. |
| Pré-condições | Base de planos conhecida, com a regra do cartão definida com o produto. |
| Gatilho | Cadastrar um plano inativo e editar um plano inativo. |
| Caso | [CT-RF102](Cenario_Teste/CT-RF102_Contador_Ativos_Planos.md) |
| Situação observada | Reprovado nas evidências. O cartão Ativos sobe de 29 para 31 após cadastrar e editar planos inativos. |
| Defeito | [BUG-041](Relatorio-de-Bugs.md#bug-041), em triagem |
| Evidências | [Jam](https://jam.dev/c/233c5d21-e108-4a55-b6f6-8738cb3fc6a6) e [Evidências](Evidencias/CT-RF102_Contador_Ativos_Planos/README.md). |

### Critérios de aceitação do RF102

1. O cartão Ativos conta apenas planos com status ativo.
2. Cadastrar um plano inativo não altera o cartão Ativos.
3. Editar um plano sem alterar o status não altera o cartão Ativos.
4. O cartão Planos acompanha o total de registros.
5. O cartão é recalculado de forma consistente após recarregar a página.

### Pontos a confirmar e limites do RF102

A regra de cálculo do cartão e a contagem da listagem não foram verificadas.

---

<a id="rf103"></a>

## RF103 — Editar um plano

| Campo | Descrição |
| --- | --- |
| Requisito de QA | O botão de ação da listagem deve abrir o plano com os dados atuais e permitir a alteração dos campos, gravando sem erro e atualizando a listagem. |
| Ator | Usuário autenticado com acesso ao módulo. |
| Pré-condições | Plano descartável cadastrado e visível na listagem. |
| Gatilho | Acionar o botão de ação do plano, alterar os benefícios e acionar Salvar Plano. |
| Caso | [CT-RF103](Cenario_Teste/CT-RF103_Edicao_Plano.md) |
| Situação observada | Aprovado conforme a gravação. O modal abre com os dados do plano 41 e plano/update retorna HTTP 200 sem erro. |
| Defeito | Nenhum no fluxo avaliado |
| Evidências | [Jam](https://jam.dev/c/233c5d21-e108-4a55-b6f6-8738cb3fc6a6) e [Evidências](Evidencias/CT-RF103_Edicao_Plano/README.md). |

### Critérios de aceitação do RF103

1. O botão de ação abre o plano com os dados atuais.
2. A alteração de qualquer campo é enviada e gravada sem erro.
3. A listagem reflete a alteração.
4. A alteração permanece após recarregar.
5. O cartão Ativos não é alterado por edição sem mudança de status (CT-RF102).

### Pontos a confirmar e limites do RF103

A persistência após recarga, a edição dos demais campos e o efeito no cartão Ativos não foram exercitados.

---

<a id="rf104"></a>

## RF104 — Filtrar tipos de pagamento por código, nome, status e tipo

| Campo | Descrição |
| --- | --- |
| Requisito de QA | A listagem de Tipos de Pagamento deve apresentar apenas os tipos que atendam aos critérios de código, nome, status e tipo informados, com cartões coerentes e mensagem explícita de resultado vazio. |
| Ator | Usuário autenticado com acesso ao módulo. |
| Pré-condições | Base de tipos conhecida, com nomes, tipos e status registrados. |
| Gatilho | Informar critérios e acionar Buscar. |
| Caso | [CT-RF104](Cenario_Teste/CT-RF104_Filtros_Tipos_Pagamento.md) |
| Situação observada | A validar — regra ou contexto pendente. Os seletores e Buscar foram acionados sem requisição de listagem e a listagem permaneceu com 16 tipos; o valor escolhido não foi registrado. |
| Defeito | Sem defeito confirmado |
| Evidências | [Jam](https://jam.dev/c/e8734e3d-3f8e-458b-8c7d-e85eea882e50) e [Evidências](Evidencias/CT-RF104_Filtros_Tipos_Pagamento/README.md). |

### Critérios de aceitação do RF104

1. Cada critério isolado (código, nome, status e tipo) filtra corretamente a listagem.
2. A combinação de critérios aplica todos eles simultaneamente.
3. Os cartões acompanham o conjunto exibido conforme o contrato definido.
4. O resultado vazio apresenta mensagem explícita.
5. Limpar os critérios restaura a listagem completa.

### Pontos a confirmar e limites do RF104

Cada critério isolado, a filtragem local ou no servidor e o resultado vazio não foram verificados.

---

<a id="rf105"></a>

## RF105 — Gravar e refletir o status do tipo de pagamento no cadastro

| Campo | Descrição |
| --- | --- |
| Requisito de QA | O cadastro de tipo de pagamento deve gravar os valores informados, inclusive o status, e a listagem e os cartões Ativos e Inativos devem refletir o status real de cada tipo. |
| Ator | Usuário autenticado com acesso ao módulo. |
| Pré-condições | Modal Tipo de Pagamento aberto; regra do status definida com o produto. |
| Gatilho | Informar os campos, manter o Status Ativo e acionar Salvar. |
| Caso | [CT-RF105](Cenario_Teste/CT-RF105_Cadastro_Tipo_Pagamento_Status.md) |
| Situação observada | Reprovado nas evidências. A criação retorna HTTP 201, mas o status Ativo não é enviado, a API não o devolve, todos os tipos aparecem como Inativo e o cartão Ativos permanece em 0. |
| Defeito | [BUG-042](Relatorio-de-Bugs.md#bug-042), em triagem |
| Evidências | [Jam](https://jam.dev/c/e8734e3d-3f8e-458b-8c7d-e85eea882e50) e [Evidências](Evidencias/CT-RF105_Cadastro_Tipo_Pagamento_Status/README.md). |

### Critérios de aceitação do RF105

1. O status escolhido no modal é enviado ao servidor e gravado.
2. A listagem apresenta o status real de cada tipo, e não um valor fixo.
3. O cartão Ativos conta os tipos ativos e Inativos os demais.
4. O novo tipo aparece na listagem com nome, tipo, via gateway e status informados.
5. Reabrir o tipo mostra os valores gravados.

### Pontos a confirmar e limites do RF105

A regra do status e a persistência após recarga não foram verificadas; o novo tipo não está visível nos quadros.

---

<a id="rf106"></a>

## RF106 — Editar um tipo de pagamento

| Campo | Descrição |
| --- | --- |
| Requisito de QA | A lupa da listagem deve abrir o tipo com os dados gravados e permitir alterá-los, gravando sem erro e atualizando a listagem e os cartões. |
| Ator | Usuário autenticado com acesso ao módulo. |
| Pré-condições | Listagem de tipos aberta e tipo existente. |
| Gatilho | Abrir o tipo pela lupa, alterar um campo e acionar Salvar. |
| Caso | [CT-RF106](Cenario_Teste/CT-RF106_Edicao_Tipo_Pagamento.md) |
| Situação observada | Aprovado conforme a gravação. A edição do tipo Dinheiro retorna HTTP 200 sem erro e a listagem reflete Pagamento Pelo Sistema Não; Via gateway passa de 6 para 5. |
| Defeito | Nenhum no fluxo avaliado |
| Evidências | [Jam](https://jam.dev/c/e8734e3d-3f8e-458b-8c7d-e85eea882e50) e [Evidências](Evidencias/CT-RF106_Edicao_Tipo_Pagamento/README.md). |

### Critérios de aceitação do RF106

1. O tipo selecionado é aberto com os valores gravados.
2. A alteração é gravada sem mensagem de erro.
3. A listagem e o cartão Via gateway refletem a alteração.
4. A alteração persiste após recarregar a página.
5. A edição de nome e de tipo também é gravada.

### Pontos a confirmar e limites do RF106

A persistência após recarga e a edição de nome e tipo não foram verificadas.

---

<a id="rf107"></a>

## RF107 — Impedir a exclusão de tipo de pagamento em uso com mensagem clara

| Campo | Descrição |
| --- | --- |
| Requisito de QA | A exclusão de um tipo de pagamento em uso deve ser impedida com mensagem clara ao usuário, código HTTP compatível e sem expor detalhes internos do banco na resposta. |
| Ator | Usuário autenticado com acesso ao módulo. |
| Pré-condições | Tipo de pagamento referenciado por contas a receber; regra de exclusão definida com o produto. |
| Gatilho | Acionar o ícone de exclusão e confirmar o diálogo. |
| Caso | [CT-RF107](Cenario_Teste/CT-RF107_Exclusao_Tipo_Pagamento_Em_Uso.md) |
| Situação observada | Reprovado nas evidências. Dois tipos em uso retornam HTTP 404 com o erro SQL completo na resposta; a tela mostra só "Erro ao deletar tipo de pagamento". |
| Defeito | [BUG-043](Relatorio-de-Bugs.md#bug-043), em triagem |
| Evidências | [Jam](https://jam.dev/c/e8734e3d-3f8e-458b-8c7d-e85eea882e50) e [Evidências](Evidencias/CT-RF107_Exclusao_Tipo_Pagamento_Em_Uso/README.md). |

### Critérios de aceitação do RF107

1. A exclusão de um tipo em uso é impedida com mensagem clara que informe o uso.
2. A resposta do servidor não expõe nomes de esquema, tabela ou restrição do banco.
3. O código HTTP é compatível com o conflito (por exemplo 409) e não 404.
4. A listagem e os cartões permanecem íntegros após a falha.
5. Um tipo sem uso é excluído e removido da listagem.

### Pontos a confirmar e limites do RF107

A regra de exclusão e a exclusão de um tipo sem uso não foram verificadas.

---

<a id="rf108"></a>

## RF108 — Alternar tema Claro/Escuro e abrir as notificações em Tipos de Pagamento

| Campo | Descrição |
| --- | --- |
| Requisito de QA | A tela de Tipos de Pagamento deve aplicar o tema escolhido a todos os elementos e o painel de notificações deve apresentar o estado das notificações. |
| Ator | Usuário autenticado com acesso ao módulo. |
| Pré-condições | Tela aberta com o controle de tema e o sino disponíveis. |
| Gatilho | Alternar o tema e acionar o sino. |
| Caso | [CT-RF108](Cenario_Teste/CT-RF108_Tema_Notificacoes_Tipos_Pagamento.md) |
| Situação observada | Aprovado conforme a gravação. O tema Escuro foi aplicado de forma consistente, as notificações exibiram o estado vazio e o retorno a Claro restaurou a tela; seis chamadas de tema com HTTP 200. |
| Defeito | Nenhum no fluxo avaliado |
| Evidências | [Jam](https://jam.dev/c/e8734e3d-3f8e-458b-8c7d-e85eea882e50) e [Evidências](Evidencias/CT-RF108_Tema_Notificacoes_Tipos_Pagamento/README.md). |

### Critérios de aceitação do RF108

1. O tema Escuro é aplicado ao fundo, aos painéis, aos cartões e à listagem.
2. O painel de notificações apresenta o estado das notificações.
3. O retorno a Claro restaura a tela.
4. O tema escolhido persiste após recarregar a página.
5. Diálogos e modais acompanham o tema.

### Pontos a confirmar e limites do RF108

Contraste, persistência após recarga e modais no tema Escuro não foram verificados.

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
| RF34 | [CT-RF34](Cenario_Teste/CT-RF34_Erro_Servidor_Excesso_Requisicoes.md) | [BUG-018](Relatorio-de-Bugs.md#bug-018), em triagem | Reprovado — múltiplas requisições retornam HTTP 500. | [Jam](https://jam.dev/c/eea58e17-b62f-432b-97b2-b14c14bed555) e [Evidências](Evidencias/CT-RF34_Erro_Servidor_Excesso_Requisicoes/README.md) |
| RF35 | [CT-RF35](Cenario_Teste/CT-RF35_Cadastro_Objetivo_Treino.md) | [BUG-019](Relatorio-de-Bugs.md#bug-019), em triagem | Reprovado nas evidências; reteste pendente. | [Evidências](Evidencias/CT-RF35_Cadastro_Objetivo_Treino/README.md) e [Jam](https://jam.dev/c/1d474477-2411-4a81-b85c-74207402b783) |
| RF38 | [CT-RF38](Cenario_Teste/CT-RF38_Cadastro_Categoria_Codigo_Automatico.md) | Nenhum no fluxo avaliado | Aprovado conforme a gravação | [Evidências](Evidencias/CT-RF38_Cadastro_Categoria_Codigo_Automatico/README.md) e [Jam](https://jam.dev/c/be1dbd05-217d-44c3-8a3d-240b7f6344e1) |
| RF39 | [CT-RF39](Cenario_Teste/CT-RF39_Cadastro_Modalidade.md) | Nenhum no fluxo avaliado | Aprovado conforme a gravação | [Evidências](Evidencias/CT-RF39_Cadastro_Modalidade/README.md) e [Jam](https://jam.dev/c/ee9a133b-d6b1-442d-b4b0-dd87595b7e70) |
| RF40 | [CT-RF40](Cenario_Teste/CT-RF40_Exclusao_Turmas_Modalidades.md) | Sem defeito confirmado | A validar — regra ou contexto pendente | [Evidências](Evidencias/CT-RF40_Exclusao_Turmas_Modalidades/README.md) e [Jam](https://jam.dev/c/ee9a133b-d6b1-442d-b4b0-dd87595b7e70) |
| RF41 | [CT-RF41](Cenario_Teste/CT-RF41_Cadastro_Turma_Sem_Modalidade.md) | [BUG-020](Relatorio-de-Bugs.md#bug-020), em triagem | Reprovado nas evidências; reteste pendente. | [Evidências](Evidencias/CT-RF41_Cadastro_Turma_Sem_Modalidade/README.md) e [Jam](https://jam.dev/c/ee9a133b-d6b1-442d-b4b0-dd87595b7e70) |
| RF42 | [CT-RF42](Cenario_Teste/CT-RF42_Solicitacao_Saque_PagarMe.md) | Sem defeito confirmado | A validar — regra ou contexto pendente | [Evidências](Evidencias/CT-RF42_Solicitacao_Saque_PagarMe/README.md) e [Jam](https://jam.dev/c/e6e551ef-9196-4c79-b6a2-89747b1e8b33) |
| RF43 | [CT-RF43](Cenario_Teste/CT-RF43_Criacao_Cobranca_PagarMe.md) | Nenhum no fluxo avaliado | Aprovado conforme a gravação | [Evidências](Evidencias/CT-RF43_Criacao_Cobranca_PagarMe/README.md) e [Jam](https://jam.dev/c/e6e551ef-9196-4c79-b6a2-89747b1e8b33) |
| RF44 | [CT-RF44](Cenario_Teste/CT-RF44_Configuracoes_Home_Salvamento.md) | Sem defeito confirmado | A validar — regra ou contexto pendente | [Evidências](Evidencias/CT-RF44_Configuracoes_Home_Salvamento/README.md) e [Jam](https://jam.dev/c/e6e551ef-9196-4c79-b6a2-89747b1e8b33) |
| RF45 | [CT-RF45](Cenario_Teste/CT-RF45_Painel_PagarMe_Periodo.md) | [BUG-021](Relatorio-de-Bugs.md#bug-021), em triagem | Reprovado nas evidências; reteste pendente. | [Evidências](Evidencias/CT-RF45_Painel_PagarMe_Periodo/README.md) e [Jam](https://jam.dev/c/e6e551ef-9196-4c79-b6a2-89747b1e8b33) |
| RF46 | [CT-RF46](Cenario_Teste/CT-RF46_Filtros_Despesas_Fixas.md) | Nenhum no fluxo avaliado | Aprovado conforme a gravação | [Evidências](Evidencias/CT-RF46_Filtros_Despesas_Fixas/README.md) e [Jam](https://jam.dev/c/a4bac99d-e436-4792-831e-8c3a875272bb) |
| RF47 | [CT-RF47](Cenario_Teste/CT-RF47_Cadastro_Despesa_Fixa.md) | Sem defeito confirmado | A validar — regra ou contexto pendente | [Evidências](Evidencias/CT-RF47_Cadastro_Despesa_Fixa/README.md) e [Jam](https://jam.dev/c/a4bac99d-e436-4792-831e-8c3a875272bb) |
| RF48 | [CT-RF48](Cenario_Teste/CT-RF48_Exclusao_Despesa_Fixa.md) | Nenhum no fluxo avaliado | Aprovado conforme a gravação | [Evidências](Evidencias/CT-RF48_Exclusao_Despesa_Fixa/README.md) e [Jam](https://jam.dev/c/a4bac99d-e436-4792-831e-8c3a875272bb) |
| RF49 | [CT-RF49](Cenario_Teste/CT-RF49_Edicao_Despesa_Fixa.md) | Nenhum no fluxo avaliado | Aprovado conforme a gravação | [Evidências](Evidencias/CT-RF49_Edicao_Despesa_Fixa/README.md) e [Jam](https://jam.dev/c/a4bac99d-e436-4792-831e-8c3a875272bb) |
| RF50 | [CT-RF50](Cenario_Teste/CT-RF50_Relatorio_Matriculas.md) | Nenhum no fluxo avaliado | Aprovado conforme a gravação | [Evidências](Evidencias/CT-RF50_Relatorio_Matriculas/README.md) e [Jam](https://jam.dev/c/3b4777a4-e1b0-4038-9b06-26c73669d7d1) |
| RF51 | [CT-RF51](Cenario_Teste/CT-RF51_Relatorio_Contas_Receber.md) | [BUG-022](Relatorio-de-Bugs.md#bug-022), em triagem | Reprovado nas evidências; reteste pendente. | [Evidências](Evidencias/CT-RF51_Relatorio_Contas_Receber/README.md) e [Jam](https://jam.dev/c/3b4777a4-e1b0-4038-9b06-26c73669d7d1) |
| RF52 | [CT-RF52](Cenario_Teste/CT-RF52_Relatorio_Contas_Pagar_Pagas.md) | Sem defeito confirmado | A validar — regra ou contexto pendente | [Evidências](Evidencias/CT-RF52_Relatorio_Contas_Pagar_Pagas/README.md) e [Jam](https://jam.dev/c/3b4777a4-e1b0-4038-9b06-26c73669d7d1) |
| RF53 | [CT-RF53](Cenario_Teste/CT-RF53_Relatorio_Avaliacoes_Vazio.md) | [BUG-023](Relatorio-de-Bugs.md#bug-023), em triagem | Reprovado nas evidências; reteste pendente. | [Evidências](Evidencias/CT-RF53_Relatorio_Avaliacoes_Vazio/README.md) e [Jam](https://jam.dev/c/3b4777a4-e1b0-4038-9b06-26c73669d7d1) |
| RF54 | [CT-RF54](Cenario_Teste/CT-RF54_Relatorio_Clientes_Vazio.md) | [BUG-023](Relatorio-de-Bugs.md#bug-023), em triagem | Reprovado nas evidências; reteste pendente. | [Evidências](Evidencias/CT-RF54_Relatorio_Clientes_Vazio/README.md) e [Jam](https://jam.dev/c/3b4777a4-e1b0-4038-9b06-26c73669d7d1) |
| RF55 | [CT-RF55](Cenario_Teste/CT-RF55_Relatorio_Colaboradores_Vazio.md) | [BUG-023](Relatorio-de-Bugs.md#bug-023), em triagem | Reprovado nas evidências; reteste pendente. | [Evidências](Evidencias/CT-RF55_Relatorio_Colaboradores_Vazio/README.md) e [Jam](https://jam.dev/c/3b4777a4-e1b0-4038-9b06-26c73669d7d1) |
| RF56 | [CT-RF56](Cenario_Teste/CT-RF56_Relatorio_Caixas_Vazio.md) | [BUG-023](Relatorio-de-Bugs.md#bug-023), em triagem | Reprovado nas evidências; reteste pendente. | [Evidências](Evidencias/CT-RF56_Relatorio_Caixas_Vazio/README.md) e [Jam](https://jam.dev/c/3b4777a4-e1b0-4038-9b06-26c73669d7d1) |
| RF57 | [CT-RF57](Cenario_Teste/CT-RF57_Exclusao_Grupo.md) | [BUG-024](Relatorio-de-Bugs.md#bug-024), em triagem | Reprovado nas evidências; reteste pendente. | [Jam](https://jam.dev/c/b1231a75-1a65-4bf0-b795-f52a8c7d3365) |
| RF58 | [CT-RF58](Cenario_Teste/CT-RF58_Edicao_Grupo.md) | [BUG-025](Relatorio-de-Bugs.md#bug-025), em triagem | Reprovado nas evidências; reteste pendente. | [Jam](https://jam.dev/c/b1231a75-1a65-4bf0-b795-f52a8c7d3365) |
| RF59 | [CT-RF59](Cenario_Teste/CT-RF59_Cadastro_Anamnese.md) | [BUG-032](Relatorio-de-Bugs.md#bug-032), em triagem | Reprovado nas evidências; reteste pendente. | [Jam](https://jam.dev/c/7be0fe71-3419-4050-b63f-473d943fa08e) |
| RF60 | [CT-RF60](Cenario_Teste/CT-RF60_Gestao_Modelos_Anamnese.md) | Nenhum identificado no fluxo avaliado | Aprovado conforme a gravação | [Jam](https://jam.dev/c/4c1e9deb-20ca-417f-ad09-48749857266e) |
| RF61 | [CT-RF61](Cenario_Teste/CT-RF61_Gestao_Categorias_Anamnese.md) | Nenhum identificado no fluxo avaliado | Aprovado conforme a gravação | [Jam](https://jam.dev/c/fdb1c9f8-c428-4726-9742-617800325d09) |
| RF62 | [CT-RF62](Cenario_Teste/CT-RF62_Edicao_Pergunta_Anamnese.md) | [BUG-044](Relatorio-de-Bugs.md#bug-044), em triagem | Reprovado nas evidências | [Jam](https://jam.dev/c/84b116fb-4640-4b1e-9148-9a169b8aa2b0) |
| RF65 | [CT-RF65](Cenario_Teste/CT-RF65_Data_Nascimento_Futura_Colaborador.md) | [BUG-026](Relatorio-de-Bugs.md#bug-026), em triagem | Reprovado nas evidências; reteste pendente. | [Jam](https://jam.dev/c/6dd75961-8e8f-4c8e-939a-19595a1f8a32) |
| RF66 | [CT-RF66](Cenario_Teste/CT-RF66_Data_Nascimento_Obrigatoria_Colaborador.md) | [BUG-027](Relatorio-de-Bugs.md#bug-027), em triagem | Reprovado nas evidências; reteste pendente. | [Jam](https://jam.dev/c/04aa5ba0-ac7e-43b6-a7f3-91ae82417a85) |
| RF67 | [CT-RF67](Cenario_Teste/CT-RF67_CREF_Formato_Colaborador.md) | [BUG-028](Relatorio-de-Bugs.md#bug-028), em triagem | Reprovado nas evidências; formato a confirmar. | [Jam](https://jam.dev/c/243d9699-4bee-495d-ae65-9a02e42813b3) |
| RF68 | [CT-RF68](Cenario_Teste/CT-RF68_Edicao_Colaborador_Campo_Obrigatorio_Vazio.md) | [BUG-029](Relatorio-de-Bugs.md#bug-029), em triagem | Reprovado nas evidências; campo exato pendente. | [Jam](https://jam.dev/c/4219c1b3-085e-4218-b181-5cf448d64cea) |
| RF69 | [CT-RF69](Cenario_Teste/CT-RF69_Funcao_Duplicada_Colaborador.md) | [BUG-030](Relatorio-de-Bugs.md#bug-030), em triagem | Reprovado nas evidências; reteste pendente. | [Jam](https://jam.dev/c/ba2400f9-dbb0-45bc-a509-187249dbe9da) |
| RF70 | [CT-RF70](Cenario_Teste/CT-RF70_Exclusao_Colaborador_Erro_500.md) | [BUG-031](Relatorio-de-Bugs.md#bug-031), em triagem | Reprovado nas evidências; reteste pendente. | [Jam](https://jam.dev/c/05be297b-22d9-4d26-beff-937526bcd816) |
| RF74 | [CT-RF74](Cenario_Teste/CT-RF74_Temas_Prospeccao.md) | — | Aprovado conforme o resumo da gravação | [Evidências](Evidencias/CT-RF74_Temas_Prospeccao/README.md) e [Jam](https://jam.dev/c/5dc9fc15-8e13-4f90-b21f-a49aedc6731e) |
| RF75 | [CT-RF75](Cenario_Teste/CT-RF75_Detalhes_Lead_Cancelamento.md) | — | Aprovado conforme o resumo da gravação | [Evidências](Evidencias/CT-RF75_Detalhes_Lead_Cancelamento/README.md) e [Jam](https://jam.dev/c/7ef0ee0b-497e-48b8-a57d-cd914558d303) |
| RF76 | [CT-RF76](Cenario_Teste/CT-RF76_Exclusao_Leads_Confirmacao.md) | — | Aprovado conforme o resumo da gravação | [Evidências](Evidencias/CT-RF76_Exclusao_Leads_Confirmacao/README.md) e [Jam](https://jam.dev/c/2ac5e5ed-b10f-4cc9-9f97-7ba65ca560f8) |
| RF77 | [CT-RF77](Cenario_Teste/CT-RF77_Cadastro_Lead_Novo_Contato.md) | — | Aprovado conforme o resumo da gravação | [Evidências](Evidencias/CT-RF77_Cadastro_Lead_Novo_Contato/README.md) e [Jam](https://jam.dev/c/29447c6a-90f5-48b2-ac5d-d43cad44a782) |
| RF78 | [CT-RF78](Cenario_Teste/CT-RF78_Cadastro_Lead_Interessado.md) | — | Aprovado conforme o resumo da gravação | [Evidências](Evidencias/CT-RF78_Cadastro_Lead_Interessado/README.md) e [Jam](https://jam.dev/c/f8735cbf-4043-4467-b43f-3cad7eff0da8) |
| RF79 | [CT-RF79](Cenario_Teste/CT-RF79_Cadastro_Lead_Aula_Experimental.md) | — | Aprovado conforme o resumo da gravação | [Evidências](Evidencias/CT-RF79_Cadastro_Lead_Aula_Experimental/README.md) e [Jam](https://jam.dev/c/bef3d877-056b-4274-87c3-da37869c54fd) |
| RF80 | [CT-RF80](Cenario_Teste/CT-RF80_Cadastro_Lead_Proposta.md) | — | Aprovado conforme o resumo da gravação | [Evidências](Evidencias/CT-RF80_Cadastro_Lead_Proposta/README.md) e [Jam](https://jam.dev/c/84f94285-ae5f-4f95-b640-a9b107565aa6) |
| RF81 | [CT-RF81](Cenario_Teste/CT-RF81_Cadastro_Bandeira_Parcela_Listagem.md) | [BUG-035](Relatorio-de-Bugs.md#bug-035) | Reprovado nas evidências resumidas | [Evidências](Evidencias/CT-RF81_Cadastro_Bandeira_Parcela_Listagem/README.md) e [Jam](https://jam.dev/c/2f0280fb-6b7f-4cf0-a45c-02f8c16b6c5e) |
| RF82 | [CT-RF82](Cenario_Teste/CT-RF82_Tema_Escuro_Bandeiras.md) | [BUG-036](Relatorio-de-Bugs.md#bug-036) | Reprovado nas evidências resumidas | [Evidências](Evidencias/CT-RF82_Tema_Escuro_Bandeiras/README.md) e [Jam](https://jam.dev/c/ae4dc198-8a42-4451-898a-fb376596c744) |
| RF83 | [CT-RF83](Cenario_Teste/CT-RF83_Cadastro_Lead_Apenas_Nome.md) | [BUG-037](Relatorio-de-Bugs.md#bug-037) | Reprovado conforme o relato; regra de obrigatoriedade a confirmar | [Evidências](Evidencias/CT-RF83_Cadastro_Lead_Apenas_Nome/README.md) e [Jam](https://jam.dev/c/ef3df03c-16ce-4cb6-b0c7-d04514cab4f6) |
| RF84 | [CT-RF84](Cenario_Teste/CT-RF84_Cadastro_Lead_Fechado.md) | — | Aprovado conforme o resumo da gravação | [Evidências](Evidencias/CT-RF84_Cadastro_Lead_Fechado/README.md) e [Jam](https://jam.dev/c/775b9003-fdf7-4ad5-8882-15ba606b6674) |
| RF85 | [CT-RF85](Cenario_Teste/CT-RF85_Tema_Notificacoes_Prospeccao.md) | Nenhum no fluxo avaliado | Aprovado conforme a gravação | [Evidências](Evidencias/CT-RF85_Tema_Notificacoes_Prospeccao/README.md) e [Jam](https://jam.dev/c/308607ff-8abc-40af-8c7c-429ce506ed64) |
| RF86 | [CT-RF86](Cenario_Teste/CT-RF86_Busca_Leads_Prospeccao.md) | Nenhum no fluxo avaliado | Aprovado conforme a gravação | [Evidências](Evidencias/CT-RF86_Busca_Leads_Prospeccao/README.md) e [Jam](https://jam.dev/c/308607ff-8abc-40af-8c7c-429ce506ed64) |
| RF87 | [CT-RF87](Cenario_Teste/CT-RF87_Filtro_Estagio_Leads.md) | Nenhum no fluxo avaliado | Aprovado conforme a gravação | [Evidências](Evidencias/CT-RF87_Filtro_Estagio_Leads/README.md) e [Jam](https://jam.dev/c/308607ff-8abc-40af-8c7c-429ce506ed64) |
| RF88 | [CT-RF88](Cenario_Teste/CT-RF88_Cadastro_Lead_Prospeccao.md) | Sem defeito confirmado | A validar — regra ou contexto pendente | [Evidências](Evidencias/CT-RF88_Cadastro_Lead_Prospeccao/README.md) e [Jam](https://jam.dev/c/308607ff-8abc-40af-8c7c-429ce506ed64) |
| RF89 | [CT-RF89](Cenario_Teste/CT-RF89_Telefone_Lead_Sem_Validacao.md) | [BUG-038](Relatorio-de-Bugs.md#bug-038), em triagem | Reprovado nas evidências; reteste pendente. | [Evidências](Evidencias/CT-RF89_Telefone_Lead_Sem_Validacao/README.md) e [Jam](https://jam.dev/c/308607ff-8abc-40af-8c7c-429ce506ed64) |
| RF90 | [CT-RF90](Cenario_Teste/CT-RF90_Edicao_Lead_Prospeccao.md) | Nenhum no fluxo avaliado | Aprovado conforme a gravação | [Evidências](Evidencias/CT-RF90_Edicao_Lead_Prospeccao/README.md) e [Jam](https://jam.dev/c/308607ff-8abc-40af-8c7c-429ce506ed64) |
| RF91 | [CT-RF91](Cenario_Teste/CT-RF91_Filtros_Contas_Pagar.md) | Sem defeito confirmado | A validar — regra ou contexto pendente | [Evidências](Evidencias/CT-RF91_Filtros_Contas_Pagar/README.md) e [Jam](https://jam.dev/c/5d0afaf4-5abd-4e85-923f-27448304a9ef) |
| RF92 | [CT-RF92](Cenario_Teste/CT-RF92_Cadastro_Conta_Colaborador_Sem_Colaborador.md) | [BUG-039](Relatorio-de-Bugs.md#bug-039), em triagem | Reprovado nas evidências; reteste pendente. | [Evidências](Evidencias/CT-RF92_Cadastro_Conta_Colaborador_Sem_Colaborador/README.md) e [Jam](https://jam.dev/c/5d0afaf4-5abd-4e85-923f-27448304a9ef) |
| RF93 | [CT-RF93](Cenario_Teste/CT-RF93_Busca_Colaborador_Conta_Pagar.md) | Sem defeito confirmado | A validar — regra ou contexto pendente | [Evidências](Evidencias/CT-RF93_Busca_Colaborador_Conta_Pagar/README.md) e [Jam](https://jam.dev/c/5d0afaf4-5abd-4e85-923f-27448304a9ef) |
| RF94 | [CT-RF94](Cenario_Teste/CT-RF94_Visualizacao_Conta_Pagar.md) | Nenhum no fluxo avaliado | Aprovado conforme a gravação | [Evidências](Evidencias/CT-RF94_Visualizacao_Conta_Pagar/README.md) e [Jam](https://jam.dev/c/5d0afaf4-5abd-4e85-923f-27448304a9ef) |
| RF95 | [CT-RF95](Cenario_Teste/CT-RF95_Exclusao_Conta_Pagar.md) | Nenhum no fluxo avaliado | Aprovado conforme a gravação | [Evidências](Evidencias/CT-RF95_Exclusao_Conta_Pagar/README.md) e [Jam](https://jam.dev/c/5d0afaf4-5abd-4e85-923f-27448304a9ef) |
| RF96 | [CT-RF96](Cenario_Teste/CT-RF96_Variaveis_Preview_Modelo_Contrato.md) | Nenhum no fluxo avaliado | Aprovado conforme a gravação | [Evidências](Evidencias/CT-RF96_Variaveis_Preview_Modelo_Contrato/README.md) e [Jam](https://jam.dev/c/44dbbd39-6915-45d6-8dd1-5f30c1432ca0) |
| RF97 | [CT-RF97](Cenario_Teste/CT-RF97_Cadastro_Modelo_Contrato.md) | Nenhum no fluxo avaliado | Aprovado conforme a gravação | [Evidências](Evidencias/CT-RF97_Cadastro_Modelo_Contrato/README.md) e [Jam](https://jam.dev/c/44dbbd39-6915-45d6-8dd1-5f30c1432ca0) |
| RF98 | [CT-RF98](Cenario_Teste/CT-RF98_Listagem_Modelos_Contrato_Vazia.md) | [BUG-040](Relatorio-de-Bugs.md#bug-040), em triagem | Reprovado nas evidências; reteste pendente. | [Evidências](Evidencias/CT-RF98_Listagem_Modelos_Contrato_Vazia/README.md) e [Jam](https://jam.dev/c/44dbbd39-6915-45d6-8dd1-5f30c1432ca0) |
| RF99 | [CT-RF99](Cenario_Teste/CT-RF99_Filtros_Planos.md) | Nenhum no fluxo avaliado | Aprovado conforme a gravação | [Evidências](Evidencias/CT-RF99_Filtros_Planos/README.md) e [Jam](https://jam.dev/c/233c5d21-e108-4a55-b6f6-8738cb3fc6a6) |
| RF100 | [CT-RF100](Cenario_Teste/CT-RF100_Tema_Notificacoes_Planos.md) | Nenhum no fluxo avaliado | Aprovado conforme a gravação | [Evidências](Evidencias/CT-RF100_Tema_Notificacoes_Planos/README.md) e [Jam](https://jam.dev/c/233c5d21-e108-4a55-b6f6-8738cb3fc6a6) |
| RF101 | [CT-RF101](Cenario_Teste/CT-RF101_Cadastro_Plano.md) | Nenhum no fluxo avaliado | Aprovado conforme a gravação | [Evidências](Evidencias/CT-RF101_Cadastro_Plano/README.md) e [Jam](https://jam.dev/c/233c5d21-e108-4a55-b6f6-8738cb3fc6a6) |
| RF102 | [CT-RF102](Cenario_Teste/CT-RF102_Contador_Ativos_Planos.md) | [BUG-041](Relatorio-de-Bugs.md#bug-041), em triagem | Reprovado nas evidências; reteste pendente. | [Evidências](Evidencias/CT-RF102_Contador_Ativos_Planos/README.md) e [Jam](https://jam.dev/c/233c5d21-e108-4a55-b6f6-8738cb3fc6a6) |
| RF103 | [CT-RF103](Cenario_Teste/CT-RF103_Edicao_Plano.md) | Nenhum no fluxo avaliado | Aprovado conforme a gravação | [Evidências](Evidencias/CT-RF103_Edicao_Plano/README.md) e [Jam](https://jam.dev/c/233c5d21-e108-4a55-b6f6-8738cb3fc6a6) |
| RF104 | [CT-RF104](Cenario_Teste/CT-RF104_Filtros_Tipos_Pagamento.md) | Sem defeito confirmado | A validar — regra ou contexto pendente | [Evidências](Evidencias/CT-RF104_Filtros_Tipos_Pagamento/README.md) e [Jam](https://jam.dev/c/e8734e3d-3f8e-458b-8c7d-e85eea882e50) |
| RF105 | [CT-RF105](Cenario_Teste/CT-RF105_Cadastro_Tipo_Pagamento_Status.md) | [BUG-042](Relatorio-de-Bugs.md#bug-042), em triagem | Reprovado nas evidências; reteste pendente. | [Evidências](Evidencias/CT-RF105_Cadastro_Tipo_Pagamento_Status/README.md) e [Jam](https://jam.dev/c/e8734e3d-3f8e-458b-8c7d-e85eea882e50) |
| RF106 | [CT-RF106](Cenario_Teste/CT-RF106_Edicao_Tipo_Pagamento.md) | Nenhum no fluxo avaliado | Aprovado conforme a gravação | [Evidências](Evidencias/CT-RF106_Edicao_Tipo_Pagamento/README.md) e [Jam](https://jam.dev/c/e8734e3d-3f8e-458b-8c7d-e85eea882e50) |
| RF107 | [CT-RF107](Cenario_Teste/CT-RF107_Exclusao_Tipo_Pagamento_Em_Uso.md) | [BUG-043](Relatorio-de-Bugs.md#bug-043), em triagem | Reprovado nas evidências; reteste pendente. | [Evidências](Evidencias/CT-RF107_Exclusao_Tipo_Pagamento_Em_Uso/README.md) e [Jam](https://jam.dev/c/e8734e3d-3f8e-458b-8c7d-e85eea882e50) |
| RF108 | [CT-RF108](Cenario_Teste/CT-RF108_Tema_Notificacoes_Tipos_Pagamento.md) | Nenhum no fluxo avaliado | Aprovado conforme a gravação | [Evidências](Evidencias/CT-RF108_Tema_Notificacoes_Tipos_Pagamento/README.md) e [Jam](https://jam.dev/c/e8734e3d-3f8e-458b-8c7d-e85eea882e50) |

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

### Base da análise do RF34 — revisão de 15/11/2026

RF34 utiliza quadros, Info e a listagem Network do Jam. A evidência mostra 23 eventos visíveis, múltiplos HTTP 500 e um diálogo de erro, mas os endpoints aparecem truncados e não foram inspecionados corpos ou logs. BUG-018 permanece em triagem. Não houve nova execução, reteste ou diagnóstico de causa raiz.

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

Com RF29 a RF34, a análise passa a cobrir 34 requisitos. A tela Grupos Musculares acrescenta duas reprovações, com BUG-016 e BUG-017 em triagem, e três aprovações limitadas aos exemplos gravados. O dashboard acrescenta uma reprovação vinculada ao BUG-018, também em triagem.

### Base da análise do RF35 — revisão de 15/11/2026

RF35 utiliza os painéis Info, Console (atividade do usuário e erros de rede), Network e Actions do Jam "Objetivos Treino", lidos diretamente, os cabeçalhos de resposta da última requisição de gravação e os quadros de 0:04, 0:21, 0:41, 0:46, 0:52, 0:58, 1:00, 1:04, 1:06 e 1:11. Foram registrados o endpoint, as duas ocorrências de HTTP 500, o preflight HTTP 204, os tempos e o texto do diálogo de erro; o corpo da requisição e da resposta aparece como indisponível no Jam. As capturas e a cronologia estão na [pasta local de evidências](Evidencias/CT-RF35_Cadastro_Objetivo_Treino/README.md). Não houve nova execução, acesso ao código ou ao banco, nem reteste. BUG-019 está em triagem.

Com RF35, a análise passa a cobrir 35 requisitos. A tela Objetivos Treino acrescenta uma reprovação, vinculada ao BUG-019, também em triagem.

### Base da análise do RF38 — revisão de 15/11/2026

RF38 utiliza os painéis Info, Console (atividade do usuário), Network e Actions do Jam "Categorias Crossfit", lidos diretamente, o corpo da requisição e da resposta de criação, os cabeçalhos de resposta e os quadros de 0:02, 0:08, 0:14, 0:27, 0:28, 0:32 e 0:36. Foram registrados o filtro por nome e por código, a tentativa de digitar no campo Código, a criação com HTTP 201, o código 9 atribuído e a localização do registro pelo filtro. As capturas e a cronologia estão na [pasta local de evidências](Evidencias/CT-RF38_Cadastro_Categoria_Codigo_Automatico/README.md). Não houve nova execução, acesso ao código ou ao banco, nem reteste.

Com RF38, a análise passa a cobrir 36 requisitos documentados (RF01–RF35 e RF38). A tela Categorias Crossfit acrescenta uma aprovação limitada aos exemplos gravados.

### Base da análise do RF39 — revisão de 15/11/2026

RF39 utiliza os painéis Info, Console (atividade do usuário), Network e Actions do Jam "SifitBox – Turmas", o corpo da requisição e da resposta de criação e os quadros de 1:17, 1:28 e 1:35. Foram registrados o `POST modalidades/salvar` com HTTP 201, a modalidade de id 4 e a atualização da listagem. As capturas e a cronologia estão na [pasta local de evidências](Evidencias/CT-RF39_Cadastro_Modalidade/README.md). Não houve nova execução, acesso ao código ou ao banco, nem reteste.

Com RF39, a análise passa a cobrir 37 requisitos documentados. A tela SifitBox – Turmas acrescenta uma aprovação limitada ao exemplo gravado.

### Base da análise do RF40 — revisão de 15/11/2026

RF40 utiliza os painéis Info, Console, Network e Actions do Jam "SifitBox – Turmas", os cabeçalhos e a resposta das exclusões, as listas retornadas (todas as turmas e modalidades com status "inativo") e os quadros de 1:00 e 1:05. Foram registrados quatro `POST turmas/excluir` e cinco `POST modalidades/excluir`, todos com HTTP 200. Não houve nova execução, acesso ao código ou ao banco, nem reteste. A regra permanece a confirmar.

Com RF40, a análise passa a cobrir 38 requisitos documentados. SifitBox – Turmas acrescenta um ponto a validar, sem defeito confirmado.

### Base da análise do RF41 — revisão de 15/11/2026

RF41 utiliza os painéis Info, Console (atividade do usuário), Network e Actions do Jam "SifitBox – Turmas", o corpo da requisição e da resposta de atualização e os quadros de 0:19, 0:58, 1:29, 1:33 e 1:35. Nas 35 entradas de rede não há requisição de criação de turma. A classificação não confirma que a modalidade seja obrigatória nem que a validação esteja ausente. Não houve nova execução, acesso ao código ou ao banco, nem reteste. BUG-020 está em triagem.

Com RF41, a análise passa a cobrir 39 requisitos documentados. SifitBox – Turmas acrescenta uma reprovação, vinculada ao BUG-020, em triagem.

### Base da análise do RF42 — revisão de 15/11/2026

RF42 utiliza os painéis Info, Console, Network e Actions do Jam "Pagar.me" e os quadros de 0:00, 0:04 e 0:05. Foram registrados a requisição de saque com HTTP 200 e a ausência de mensagem de resultado. Corpos de requisição e de resposta indisponíveis. Não houve nova execução, acesso ao código ou ao banco, nem reteste.

Com RF42, a análise passa a cobrir 40 requisitos documentados. O CT-RF42 acrescenta um ponto a validar, sem defeito confirmado.

### Base da análise do RF43 — revisão de 15/11/2026

RF43 utiliza os painéis Info, Console, Network e Actions do Jam "Pagar.me" e os quadros de 0:29 e 0:31. Foram registrados o formulário preenchido, a requisição de criação com HTTP 200 e a mensagem de sucesso. Corpos de requisição e de resposta indisponíveis. Não houve nova execução, acesso ao código ou ao banco, nem reteste.

Com RF43, a análise passa a cobrir 41 requisitos documentados. O CT-RF43 acrescenta uma aprovação limitada ao exemplo gravado.

### Base da análise do RF44 — revisão de 15/11/2026

RF44 utiliza os painéis Info, Console, Network e Actions do Jam "Pagar.me" (trecho de Configurações) e os quadros de 0:33, 0:41, 0:46 e 0:56. Foram registrados as alterações, o valor 1100 no campo de dias, a mudança do menu lateral e a ausência de mensagem de confirmação. Não houve nova execução, acesso ao código ou ao banco, nem reteste.

Com RF44, a análise passa a cobrir 42 requisitos documentados. O CT-RF44 acrescenta um ponto a validar, sem defeito confirmado.

### Base da análise do RF45 — revisão de 15/11/2026

RF45 utiliza os painéis Info, Console, Network e Actions do Jam "Pagar.me" e os quadros de 0:00 e 0:25. A comparação entre os dois quadros mostra o mesmo valor e o mesmo gráfico com períodos diferentes. A leitura do eixo de datas é aproximada. Não houve nova execução, acesso ao código ou ao banco, nem reteste. BUG-021 está em triagem.

Com RF45, a análise passa a cobrir 43 requisitos documentados. O CT-RF45 acrescenta uma reprovação, vinculada ao BUG-021, em triagem.

### Base da análise do RF46 — revisão de 15/11/2026

RF46 utiliza os painéis Info, Console, Network e Actions do Jam "Despesas Fixas" e os quadros de 0:03, 0:11, 0:19 e 0:42. Foram registrados os filtros por código e por nome, o cartão Valor Listado e a ausência de requisição nos filtros. Não houve nova execução, acesso ao código ou ao banco, nem reteste.

Com RF46, a análise passa a cobrir 44 requisitos documentados. O CT-RF46 acrescenta uma aprovação limitada ao exemplo gravado.

### Base da análise do RF47 — revisão de 15/11/2026

RF47 utiliza os painéis Info, Console, Network e Actions do Jam "Despesas Fixas", o corpo e a resposta da primeira requisição de criação e os quadros de 0:34, 0:36 e 0:42. Foram registrados duas requisições de criação com HTTP 201 e um único registro novo visível. A segunda requisição não teve corpo nem resposta capturados. Não houve nova execução, acesso ao código ou ao banco, nem reteste.

Com RF47, a análise passa a cobrir 45 requisitos documentados. O CT-RF47 acrescenta um ponto a validar, sem defeito confirmado.

### Base da análise do RF48 — revisão de 15/11/2026

RF48 utiliza os painéis Info, Console, Network e Actions do Jam "Despesas Fixas", o corpo e a resposta da exclusão e os quadros de 0:42, 0:44 e 0:51. Foram registrados o diálogo de confirmação, a requisição de exclusão com HTTP 200 e a atualização da listagem. Não houve nova execução, acesso ao código ou ao banco, nem reteste.

Com RF48, a análise passa a cobrir 46 requisitos documentados. O CT-RF48 acrescenta uma aprovação limitada ao exemplo gravado.

### Base da análise do RF49 — revisão de 15/11/2026

RF49 utiliza os painéis Info, Console, Network e Actions do Jam "Despesas Fixas", o corpo e a resposta de seleção e de edição e os quadros de 0:48 e 0:51. Foram registrados a requisição de edição com HTTP 200 e a nova recorrência na listagem. Não houve nova execução, acesso ao código ou ao banco, nem reteste.

Com RF49, a análise passa a cobrir 47 requisitos documentados. O CT-RF49 acrescenta uma aprovação limitada ao exemplo gravado.

### Base da análise do RF50 — revisão de 15/11/2026

RF50 utiliza os painéis Info, Console e Network do Jam "Relatórios", o quadro de 0:38 e o conteúdo do PDF baixado. O PDF foi identificado pelo conteúdo. Não houve nova execução, acesso ao código ou ao banco, nem reteste.

Com RF50, a análise passa a cobrir 48 requisitos documentados. O CT-RF50 acrescenta uma aprovação limitada ao exemplo gravado.

### Base da análise do RF51 — revisão de 15/11/2026

RF51 utiliza os painéis Info, Console e Network do Jam "Relatórios", o quadro de 0:43 e o conteúdo do PDF baixado, com três contas e o valor a receber ausente. Não houve nova execução, acesso ao código ou ao banco, nem reteste. BUG-022 está em triagem.

Com RF51, a análise passa a cobrir 49 requisitos documentados. O CT-RF51 acrescenta uma reprovação, vinculada ao BUG-022, em triagem.

### Base da análise do RF52 — revisão de 15/11/2026

RF52 utiliza os painéis Info, Console e Network do Jam "Relatórios", o quadro de 0:48 e o conteúdo do PDF baixado, sem linhas e com totalizadores zerados. Não houve nova execução, acesso ao código ou ao banco, nem reteste.

Com RF52, a análise passa a cobrir 50 requisitos documentados. O CT-RF52 acrescenta um ponto a validar, sem defeito confirmado.

### Base da análise do RF53 — revisão de 15/11/2026

RF53 utiliza os painéis Info, Console e Network do Jam "Relatórios", os quadros do vídeo e os arquivos baixados (tamanho zero e carimbos de hora). A atividade do usuário não foi registrada no Console do Jam. A correspondência do arquivo com o tipo é inferida. Não houve nova execução, acesso ao código ou ao banco, nem reteste. BUG-023 está em triagem.

Com RF53, a análise passa a cobrir 51 requisitos documentados. O CT-RF53 acrescenta uma reprovação, vinculada ao BUG-023, em triagem.

### Base da análise do RF54 — revisão de 15/11/2026

RF54 utiliza os painéis Info, Console e Network do Jam "Relatórios", os quadros do vídeo e os arquivos baixados (tamanho zero e carimbos de hora). A atividade do usuário não foi registrada no Console do Jam. A correspondência do arquivo com o tipo é inferida. Não houve nova execução, acesso ao código ou ao banco, nem reteste. BUG-023 está em triagem.

Com RF54, a análise passa a cobrir 52 requisitos documentados. O CT-RF54 acrescenta uma reprovação, vinculada ao BUG-023, em triagem.

### Base da análise do RF55 — revisão de 15/11/2026

RF55 utiliza os painéis Info, Console e Network do Jam "Relatórios", os quadros do vídeo e os arquivos baixados (tamanho zero e carimbos de hora). A atividade do usuário não foi registrada no Console do Jam. A correspondência do arquivo com o tipo é inferida. Não houve nova execução, acesso ao código ou ao banco, nem reteste. BUG-023 está em triagem.

Com RF55, a análise passa a cobrir 53 requisitos documentados. O CT-RF55 acrescenta uma reprovação, vinculada ao BUG-023, em triagem.

### Base da análise do RF56 — revisão de 15/11/2026

RF56 utiliza os painéis Info, Console e Network do Jam "Relatórios", os quadros do vídeo e os arquivos baixados (tamanho zero e carimbos de hora). A atividade do usuário não foi registrada no Console do Jam. A correspondência do arquivo com o tipo é inferida. Não houve nova execução, acesso ao código ou ao banco, nem reteste. BUG-023 está em triagem.

Com RF56, a análise passa a cobrir 54 requisitos documentados. O CT-RF56 acrescenta uma reprovação, vinculada ao BUG-023, em triagem.

### Base da análise do RF57 — revisão de 15/11/2026

RF57 utiliza os painéis Informações, Console e Rede do Jam "Tela de Grupos", os quadros do vídeo entre 0:00 e 1:38 e as duas requisições de exclusão com HTTP 500. Não houve nova execução, acesso ao código ou ao banco, nem reteste.

Com RF57, a análise passa a cobrir 55 requisitos documentados. O CT-RF57 acrescenta uma reprovação, vinculada ao BUG-024, em triagem.

### Base da análise do RF58 — revisão de 15/11/2026

RF58 utiliza os painéis Informações, Console e Rede do mesmo Jam "Tela de Grupos" do RF57, os eventos de clique entre 0:57 e 1:16 e as requisições `POST /api/edita/grupo/1`, `GET /api/grupos/1` e `POST /api/seleciona/grupo/1` correspondentes às duas edições do grupo "Treino sla" (código 11). Foram registrados os corpos de requisição e resposta das duas edições e das consultas imediatamente seguintes. Não houve nova execução, acesso ao código ou ao banco, nem reteste.

Com RF58, a análise passa a cobrir 56 requisitos documentados. O CT-RF58 acrescenta uma reprovação, vinculada ao BUG-025, em triagem.

### Base da análise do RF59 — revisão de 15/11/2026

RF59 utiliza os painéis Informações, Console e Rede do Jam "Fichas de Anamnese", os eventos de clique e digitação entre 0:00 e 1:28 e as sete requisições com HTTP 500 (quatro em `POST /api/anamnese/aplicar/1` e três em `POST /api/anamnese/rascunho/1`), registradas com dois modelos de anamnese e três respostas distintas. Foram registrados os corpos de requisição e resposta de duas dessas tentativas, representativas das demais. Não houve nova execução, acesso a logs, ao código ou ao banco, nem reteste.

Com RF59, a análise passava a cobrir 57 requisitos documentados (antes da inclusão de RF60 e da integração de RF65 a RF70). O CT-RF59 acrescenta uma reprovação, vinculada ao BUG-032, em triagem.

---

## RF60 — Gerenciar modelos de anamnese sem erro de servidor

| Campo | Descrição |
| --- | --- |
| Requisito de QA | Ao buscar, filtrar, cadastrar, editar e excluir modelos de anamnese, o backend deve processar cada operação e retornar sucesso, sem erro de servidor. |
| Ator | Usuário autenticado com permissão em Modelos de Anamnese. |
| Pré-condições | Ao menos um modelo de anamnese já cadastrado; banco de perguntas com itens cadastrados e pesquisáveis. |
| Gatilho | Buscar/filtrar a listagem, cadastrar um modelo com perguntas do banco, editar um modelo cadastrado e excluir modelos pela ação do cartão. |
| Caso | [CT-RF60](Cenario_Teste/CT-RF60_Gestao_Modelos_Anamnese.md) |
| Situação observada | Aprovado conforme a gravação. As quinze requisições identificadas aos endpoints `/api/modelos-anamnese/*` (busca/filtro, cadastro, duas edições e duas exclusões) retornam HTTP 200 ou 201; nenhuma requisição ao backend do SIFIT retorna erro 4xx ou 5xx na gravação. |
| Defeito | Nenhum identificado no fluxo avaliado. |
| Evidências | [Jam](https://jam.dev/c/4c1e9deb-20ca-417f-ad09-48749857266e). |

### Critérios de aceitação do RF60

1. A busca e o filtro de status na listagem de modelos retornam resultados consistentes com o termo e o status informados.
2. Um novo modelo é cadastrado com nome, descrição e perguntas do banco, e passa a constar na listagem.
3. Um modelo cadastrado pode ser editado mais de uma vez, preservando as alterações salvas.
4. Um modelo pode ser excluído e deixa de constar na listagem após a exclusão.
5. Nenhuma das operações acima deve retornar erro HTTP 4xx ou 5xx em uso normal.

### Pontos a confirmar e limites do RF60

Os endpoints de escrita (`salvar/1`, `alterar/1` e `deletar/1`) e o de leitura (`GET /api/modelos-anamnese/1`) usam o mesmo sufixo numérico `1`, independentemente do modelo manipulado — compatível com a hipótese já registrada em RF59 de que esse identificador corresponde ao `empresa_id` da conta, e não ao id do modelo. A leitura da listagem retorna HTTP 201 em vez do código 200 mais usual para esse tipo de operação; como permanece na faixa de sucesso, isso não é tratado como defeito, mas fica registrado para confirmação com a equipe de desenvolvimento. Os corpos de solicitação e de resposta das chamadas de API não foram capturados pelo Jam, uma limitação da ferramenta. Não houve nova execução, acesso a logs, ao código ou ao banco, nem reteste.

### Base da análise do RF60 — revisão de 16/11/2026

RF60 utiliza os painéis Informações, Console e Rede do Jam "Modelos de Anamnese", os eventos de clique e digitação entre 0:00 e 2:32 e as quinze requisições aos endpoints `/api/modelos-anamnese/*`, todas com HTTP 200 ou 201. A única requisição com código de erro em toda a gravação é um *beacon* de analytics do Google (HTTP 499), sem relação com o backend do SIFIT. Os corpos de requisição e de resposta não foram capturados pelo Jam. Não houve nova execução, acesso a logs, ao código ou ao banco, nem reteste.

Com RF60, a análise passa a cobrir 58 requisitos documentados (antes da integração de RF65 a RF70).

---

## RF61 — Gerenciar categorias de anamnese sem erro de servidor

| Campo | Descrição |
| --- | --- |
| Requisito de QA | Ao filtrar por status, pesquisar, cadastrar, editar, cancelar uma edição e excluir categorias de anamnese, o backend deve processar cada operação e retornar sucesso, sem erro de servidor, e não enviar requisição alguma quando a edição é cancelada. |
| Ator | Usuário autenticado com permissão em Categorias de Anamnese. |
| Pré-condições | Ao menos uma categoria de anamnese já cadastrada, para exercitar o filtro por status e a busca. |
| Gatilho | Filtrar/pesquisar a listagem, cadastrar uma categoria, editá-la (ícone, nome e status), cancelar uma edição em andamento e excluí-la pelo ícone do cartão. |
| Caso | [CT-RF61](Cenario_Teste/CT-RF61_Gestao_Categorias_Anamnese.md) |
| Situação observada | Aprovado conforme a gravação. As sete requisições identificadas aos endpoints `/api/categorias-anamnese/*` (cadastro, três edições e exclusão) retornam HTTP 200 ou 201; a quarta tentativa de edição é cancelada e não gera requisição; nenhuma requisição ao backend do SIFIT retorna erro 4xx ou 5xx na gravação. |
| Defeito | Nenhum identificado no fluxo avaliado. |
| Evidências | [Jam](https://jam.dev/c/fdb1c9f8-c428-4726-9742-617800325d09). |

### Critérios de aceitação do RF61

1. O filtro de status e a busca por texto na listagem de categorias aplicam-se de forma consistente, sem gerar erro.
2. Uma nova categoria é cadastrada com nome, cor, ícone e status, e passa a constar na listagem.
3. Uma categoria cadastrada pode ser editada mais de uma vez (ícone, nome e status, isoladamente ou em conjunto), preservando as alterações salvas.
4. Ao cancelar uma edição em andamento, nenhuma alteração é enviada ao backend e os valores salvos anteriormente são mantidos.
5. Uma categoria pode ser excluída e deixa de constar na listagem após a exclusão.
6. Nenhuma das operações acima deve retornar erro HTTP 4xx ou 5xx em uso normal.

### Pontos a confirmar e limites do RF61

Os endpoints de escrita (`salvar/1`, `alterar/1` e `deletar/1`) e o de leitura (`GET /api/categorias-anamnese/1`) usam o mesmo sufixo numérico `1`, independentemente da categoria manipulada — reforçando a hipótese já registrada em RF59 e RF60 de que esse identificador corresponde ao `empresa_id` da conta, e não ao id da categoria. Diferentemente de RF60, aqui o cadastro retorna HTTP 201 e as edições e a exclusão retornam HTTP 200, um padrão mais previsível entre operações semelhantes, registrado para confirmação com a equipe de desenvolvimento. A ferramenta de gravação (Jam) apresentou instabilidade ao exibir os cabeçalhos de detalhe de algumas requisições com o mesmo identificador e horário repetidos entre linhas diferentes — tratado como limitação da ferramenta de captura, já que URL, método e código de status de cada requisição permaneceram corretos ao serem reconferidos. Não houve nova execução, acesso a logs, ao código ou ao banco, nem reteste.

### Base da análise do RF61 — revisão de 16/11/2026

RF61 utiliza os painéis Informações, Console, Rede e Ações do Jam "Categorias de Anamnese", os eventos de clique e digitação entre 0:00 e 1:35 e as sete requisições aos endpoints `/api/categorias-anamnese/*`, todas com HTTP 200 ou 201. A única requisição não relacionada ao backend do SIFIT é um *beacon* de telemetria de uma extensão de antivírus do navegador, também com retorno de sucesso. Não foram registradas mensagens de erro no console. Não houve nova execução, acesso a logs, ao código ou ao banco, nem reteste.

Com RF61, a análise passa a cobrir 59 requisitos documentados (antes da integração de RF65 a RF70).

---

## RF62 — Editar pergunta de anamnese sem erro de servidor

| Campo | Descrição |
| --- | --- |
| Requisito de QA | Ao editar o tipo de resposta ou o status de uma pergunta de anamnese cadastrada, o backend deve processar a alteração e retornar sucesso, sem erro de servidor. |
| Ator | Usuário autenticado com permissão em Perguntas Anamnese. |
| Pré-condições | Ao menos uma pergunta de anamnese já cadastrada, com um tipo de resposta definido. |
| Gatilho | Reabrir uma pergunta cadastrada pela ação de editar, alterar o tipo de resposta ou o status e acionar "Salvar". |
| Caso | [CT-RF62](Cenario_Teste/CT-RF62_Edicao_Pergunta_Anamnese.md) |
| Situação observada | Reprovado nas evidências. As quatro tentativas de editar o tipo de resposta e/ou o status de uma pergunta recém-criada retornam HTTP 500, com o mesmo corpo genérico de erro, impedindo qualquer atualização da pergunta. |
| Defeito | [BUG-044](Relatorio-de-Bugs.md#bug-044), em triagem. |
| Evidências | [Jam](https://jam.dev/c/84b116fb-4640-4b1e-9148-9a169b8aa2b0). |

### Critérios de aceitação do RF62

1. O filtro de código, nome e status na listagem de perguntas aplica-se de forma consistente, sem gerar erro.
2. Uma nova pergunta é cadastrada com nome, texto, tipo de resposta e status, e passa a constar na listagem.
3. Uma pergunta cadastrada pode ter o tipo de resposta alterado e salvo, sem erro de servidor, preservando a alteração.
4. Uma pergunta cadastrada pode ter o status alterado e salvo, isoladamente ou em conjunto com o tipo de resposta, sem erro de servidor.
5. Nenhuma das operações acima deve retornar erro HTTP 4xx ou 5xx em uso normal.

### Pontos a confirmar e limites do RF62

As quatro tentativas de edição falham com o mesmo erro genérico independentemente do valor de `resposta` (`"3opcoes"` ou `"2opcoes"`) ou do `status`, o que sugere uma falha na própria rotina de alteração — possivelmente ao ajustar ou remover as opções/complementos do tipo de resposta anterior (`"2opcoes_complemento"`, definido na criação) — e não em um valor específico enviado; isso não foi confirmado com acesso a logs, ao código ou ao banco. O cadastro da pergunta (`salvar/1`) foi registrado em duplicidade para uma única ação de "Salvar" (HTTP 200 e HTTP 201), no mesmo padrão de duplicação por clique já observado em outros módulos (por exemplo, CT-RF47). Não houve nova execução, acesso a logs, ao código ou ao banco, nem reteste.

### Base da análise do RF62 — revisão de 16/11/2026

RF62 utiliza os painéis Informações, Console, Rede e Ações do Jam "Perguntas Anamnese", os eventos de clique e digitação entre 0:00 e 1:30 e as dezenove requisições identificadas, incluindo as quatro requisições `POST /api/pergunta-anamnese/alterar/1`, todas com HTTP 500. As quatro requisições de erro aparecem também na visão "Erros de rede" do painel Console do Jam, nos mesmos instantes observados no painel Rede. Não houve nova execução, acesso a logs, ao código ou ao banco, nem reteste.

Com RF62, a análise passa a cobrir 60 requisitos documentados (antes da integração de RF65 a RF70).

---

## RF65 a RF73 — Validações, operações e buscas de Colaboradores

| Requisito | Comportamento esperado | Caso | Defeito | Resultado observado |
| --- | --- | --- | --- | --- |
| <a id="rf65"></a>RF65 | Recusar data de nascimento posterior à data atual. | [CT-RF65](Cenario_Teste/CT-RF65_Data_Nascimento_Futura_Colaborador.md) | [BUG-026](Relatorio-de-Bugs.md#bug-026) | `18/05/2222` aceito; atualização HTTP 200. |
| <a id="rf66"></a>RF66 | Exigir a data de nascimento definida como obrigatória. | [CT-RF66](Cenario_Teste/CT-RF66_Data_Nascimento_Obrigatoria_Colaborador.md) | [BUG-027](Relatorio-de-Bugs.md#bug-027) | Campo vazio aceito; atualização HTTP 200. |
| <a id="rf67"></a>RF67 | Validar o CREF conforme o formato confirmado pelo produto. | [CT-RF67](Cenario_Teste/CT-RF67_CREF_Formato_Colaborador.md) | [BUG-028](Relatorio-de-Bugs.md#bug-028) | Texto `TESTEE` aceito; atualização HTTP 200. |
| <a id="rf68"></a>RF68 | Bloquear edição com qualquer campo obrigatório vazio. | [CT-RF68](Cenario_Teste/CT-RF68_Edicao_Colaborador_Campo_Obrigatorio_Vazio.md) | [BUG-029](Relatorio-de-Bugs.md#bug-029) | Edição aceita sem validação visível; HTTP 200. |
| <a id="rf69"></a>RF69 | Manter uma única associação por colaborador e função. | [CT-RF69](Cenario_Teste/CT-RF69_Funcao_Duplicada_Colaborador.md) | [BUG-030](Relatorio-de-Bugs.md#bug-030) | Mesma função associada três vezes; dois POST HTTP 201. |
| <a id="rf70"></a>RF70 | Excluir colaborador permitido ou explicar o vínculo impeditivo sem HTTP 500. | [CT-RF70](Cenario_Teste/CT-RF70_Exclusao_Colaborador_Erro_500.md) | [BUG-031](Relatorio-de-Bugs.md#bug-031) | Exclusão retorna HTTP 500 e erro interno genérico. |
| <a id="rf71"></a>RF71 | Manter o filtro por nome aplicado em todas as páginas do resultado. | [CT-RF71](Cenario_Teste/CT-RF71_Busca_Nome_Colaborador_Paginacao.md) | [BUG-033](Relatorio-de-Bugs.md#bug-033) | A página seguinte exibe nomes fora do filtro. |
| <a id="rf72"></a>RF72 | Retornar somente o colaborador associado a um código existente. | [CT-RF72](Cenario_Teste/CT-RF72_Busca_Codigo_Existente_Colaborador.md) | — | Usuário correto retornado no exemplo gravado. |
| <a id="rf73"></a>RF73 | Exibir estado vazio para código inexistente, sem linha residual. | [CT-RF73](Cenario_Teste/CT-RF73_Busca_Codigo_Inexistente_Colaborador.md) | [BUG-034](Relatorio-de-Bugs.md#bug-034) | A tabela apresenta uma linha vazia. |

### Critérios gerais de aceitação

1. Regras de obrigatoriedade e formato devem ser aplicadas no cliente e no servidor.
2. Tentativas inválidas não podem persistir dados parcial ou integralmente.
3. A associação colaborador/função deve ser única e resistente a repetição ou concorrência.
4. Impedimentos de exclusão devem ser tratados como regra de negócio, com mensagem específica.
5. Todos os fluxos devem preservar os dados anteriores após falha e permitir correção.
6. Filtros devem permanecer ativos durante a paginação e representar o mesmo conjunto nos totais.
7. Consultas sem correspondência devem apresentar estado vazio sem linhas ou ações residuais.

### Base da análise — revisão de 15/11/2026

RF59 registra HTTP 500 no cadastro de anamnese. Os seis Jams de RF65–RF70 foram lidos por metadados, eventos de interação e registros de rede: RF65–RF68 possuem POST de atualização HTTP 200 sem corpo capturado, por isso a aceitação do endpoint está comprovada, mas a persistência final deve ser reconfirmada; RF69 registra payloads, HTTP 201 e respostas subsequentes com três associações iguais; RF70 registra payload, HTTP 500 e `Erro interno inesperado`. Com a inclusão de RF60 (Modelos de Anamnese), a gravação foi lida por metadados, eventos de interação e registros de rede, confirmando a aprovação sem erro de servidor. RF71–RF73 foram analisados visualmente: falha do filtro na paginação, busca válida por código e linha vazia para código inexistente. Não houve nova execução, acesso ao banco, logs ou código. A análise passa a cobrir 69 requisitos documentados; RF36–RF37 e RF63–RF64 permanecem fora do conjunto fornecido.

---

## Inclusão de 16/11/2026 — RF74 a RF84

Integração documental dos arquivos RESUMO.txt fornecidos em `C:\Users\Leonardo\Desktop\evidencias`, com data de gravação e análise informada de 16/11/2026. Os Jams não foram reabertos nesta integração; eventos de rede, horários e quadros abaixo são transcritos dos resumos, sem verificação independente. Não houve nova execução do SIFIT, reteste, consulta ao banco, logs ou código.

CT-RF74–CT-RF84 acrescentam oito aprovações e três reprovações conforme os resumos fornecidos, com BUG-035–BUG-037 em triagem. CT-RF83 mantém a classificação do relato, condicionada à confirmação da regra de obrigatoriedade. Os dez casos anteriores a validar permanecem inalterados.

<a id="rf74"></a>

### RF74 — Alternar entre os temas claro e escuro na Prospecção

| Campo | Descrição |
| --- | --- |
| Requisito funcional | A tela deve acompanhar a seleção de tema, mantendo os dados da listagem. |
| Ator | Usuário autenticado com acesso a Prospecção. |
| Pré-condição | Sessão autenticada com acesso à Prospecção e controle de tema disponível. Listagem de leads carregada antes da alternância. |
| Comportamento esperado | A tela deve acompanhar a seleção de tema, mantendo os dados da listagem. |
| Situação observada | A gravação mostra a tela passando de escura para clara e retornando ao tema escuro. A listagem permanece visível. |
| Prioridade | Média, proposta. |
| Rastreabilidade | [CT-RF74](Cenario_Teste/CT-RF74_Temas_Prospeccao.md) · — · [Evidências](Evidencias/CT-RF74_Temas_Prospeccao/README.md) · [Jam](https://jam.dev/c/5dc9fc15-8e13-4f90-b21f-a49aedc6731e) |

#### Critérios de aceitação

1. Claro e Escuro são aplicados na sequência escolhida.
2. A listagem mantém os mesmos leads e dados durante a alternância.
3. No reteste, recarregar a página para avaliar separadamente a persistência da preferência.

#### Base da análise e limites

Aprovado conforme o resumo da gravação. Classificação restrita à alternância visível nesta tela; a gravação não demonstra persistência após recarregar nem uma auditoria de contraste.
Análise da gravação e dos eventos capturados no Jam; não foi executado um novo teste no sistema.

Encaminhamento: Repetir a alternância com listagem conhecida; verificar persistência após recarga em execução complementar.

<a id="rf75"></a>

### RF75 — Consultar os detalhes de um lead e cancelar a edição

| Campo | Descrição |
| --- | --- |
| Requisito funcional | O sistema deve carregar os dados do lead e fechar a janela ao cancelar, sem enviar uma gravação da alteração. |
| Ator | Usuário autenticado com acesso a Prospecção. |
| Pré-condição | Sessão autenticada com acesso à Prospecção. Lead existente com dados conhecidos; na evidência, código 3. |
| Comportamento esperado | O sistema deve carregar os dados do lead e fechar a janela ao cancelar, sem enviar uma gravação da alteração. |
| Situação observada | Os dados do lead de código 3 são carregados, incluindo estágio Fechado, contato e observação. Após a alteração no telefone, Cancelar fecha a janela e retorna à listagem. Não há chamada de salvamento na linha do tempo. |
| Prioridade | Média, proposta. |
| Rastreabilidade | [CT-RF75](Cenario_Teste/CT-RF75_Detalhes_Lead_Cancelamento.md) · — · [Evidências](Evidencias/CT-RF75_Detalhes_Lead_Cancelamento/README.md) · [Jam](https://jam.dev/c/7ef0ee0b-497e-48b8-a57d-cd914558d303) |

#### Critérios de aceitação

1. A consulta carrega os dados do lead selecionado.
2. Cancelar fecha a janela e retorna à listagem.
3. Cancelar não envia requisição de salvamento.
4. Em execução complementar, reabrir o lead e conferir que o telefone original foi preservado.

#### Base da análise e limites

Aprovado conforme o resumo da gravação. Não houve reabertura do registro para confirmar o valor persistido do telefone. O sucesso se refere à consulta e ao cancelamento observados.
Análise da gravação e dos eventos capturados no Jam; não foi executado um novo teste no sistema.

Encaminhamento: Reabrir o lead após cancelar e comparar o telefone com o valor original.

<a id="rf76"></a>

### RF76 — Excluir leads com confirmação

| Campo | Descrição |
| --- | --- |
| Requisito funcional | Cada confirmação deve excluir o lead selecionado e atualizar a listagem e o total de registros. |
| Ator | Usuário autenticado com acesso a Prospecção. |
| Pré-condição | Sessão autenticada com permissão de exclusão em Prospecção. Dois leads de teste disponíveis para remoção; na evidência, códigos 3 e 4. |
| Comportamento esperado | Cada confirmação deve excluir o lead selecionado e atualizar a listagem e o total de registros. |
| Situação observada | Os leads de códigos 3 e 4 deixam de aparecer após as confirmações. O total exibido diminui de 8 para 7 e depois para 6. |
| Prioridade | Média, proposta. |
| Rastreabilidade | [CT-RF76](Cenario_Teste/CT-RF76_Exclusao_Leads_Confirmacao.md) · — · [Evidências](Evidencias/CT-RF76_Exclusao_Leads_Confirmacao/README.md) · [Jam](https://jam.dev/c/2ac5e5ed-b10f-4cc9-9f97-7ba65ca560f8) |

#### Critérios de aceitação

1. Cada exclusão depende da confirmação do usuário.
2. Cada confirmação remove somente o lead selecionado.
3. A listagem e o total são atualizados após cada exclusão.
4. Em execução complementar, cancelar a confirmação deve preservar o registro.

#### Base da análise e limites

Aprovado conforme o resumo da gravação. As duas exclusões foram agrupadas no mesmo caso porque pertencem ao mesmo cenário na gravação. O cancelamento da confirmação de exclusão não foi testado.
Análise da gravação e dos eventos capturados no Jam; não foi executado um novo teste no sistema.

Encaminhamento: Repetir com registros descartáveis e testar também o cancelamento da confirmação.

<a id="rf77"></a>

### RF77 — Cadastrar lead no estágio Novo Contato

| Campo | Descrição |
| --- | --- |
| Requisito funcional | O lead deve ser criado no estágio Novo Contato e aparecer na listagem. |
| Ator | Usuário autenticado com acesso a Prospecção. |
| Pré-condição | Sessão autenticada com permissão para adicionar leads. Dados de contato de teste disponíveis e estágio Novo Contato selecionável. |
| Comportamento esperado | O lead deve ser criado no estágio Novo Contato e aparecer na listagem. |
| Situação observada | O lead de teste é criado com o estágio NOVO_CONTATO, recebe código 11 e aparece na listagem. O total passa de 6 para 7, e o indicador Novo Contato passa de 2 para 3. |
| Prioridade | Média, proposta. |
| Rastreabilidade | [CT-RF77](Cenario_Teste/CT-RF77_Cadastro_Lead_Novo_Contato.md) · — · [Evidências](Evidencias/CT-RF77_Cadastro_Lead_Novo_Contato/README.md) · [Jam](https://jam.dev/c/29447c6a-90f5-48b2-ac5d-d43cad44a782) |

#### Critérios de aceitação

1. A seleção final envia o estágio NOVO_CONTATO.
2. O cadastro retorna um código e inclui o lead na listagem.
3. O total e o indicador Novo Contato aumentam em um.
4. Em execução complementar, reabrir o cadastro para conferir todos os campos.

#### Base da análise e limites

Aprovado conforme o resumo da gravação. A classificação considera o cadastro mostrado; não houve reabertura do registro para revisar todos os campos.
Análise da gravação e dos eventos capturados no Jam; não foi executado um novo teste no sistema.

Encaminhamento: Repetir o cadastro e conferir campos e estágio após reabertura.

<a id="rf78"></a>

### RF78 — Cadastrar lead no estágio Interessado

| Campo | Descrição |
| --- | --- |
| Requisito funcional | O lead deve ser criado no estágio Interessado e aparecer na listagem. |
| Ator | Usuário autenticado com acesso a Prospecção. |
| Pré-condição | Sessão autenticada com permissão para adicionar leads. Dados de contato de teste disponíveis e estágio Interessado selecionável. |
| Comportamento esperado | O lead deve ser criado no estágio Interessado e aparecer na listagem. |
| Situação observada | O cadastro retorna código 12 e o lead aparece na listagem com a identificação Interessado. |
| Prioridade | Média, proposta. |
| Rastreabilidade | [CT-RF78](Cenario_Teste/CT-RF78_Cadastro_Lead_Interessado.md) · — · [Evidências](Evidencias/CT-RF78_Cadastro_Lead_Interessado/README.md) · [Jam](https://jam.dev/c/f8735cbf-4043-4467-b43f-3cad7eff0da8) |

#### Critérios de aceitação

1. O envio utiliza o estágio INTERESSADO.
2. O cadastro retorna um código e o lead é listado como Interessado.
3. Em execução complementar, reabrir o registro para conferir os campos salvos.

#### Base da análise e limites

Aprovado conforme o resumo da gravação. A gravação não demonstra reabertura ou alteração posterior do registro.
Análise da gravação e dos eventos capturados no Jam; não foi executado um novo teste no sistema.

Encaminhamento: Repetir o cadastro e conferir os dados após reabertura.

<a id="rf79"></a>

### RF79 — Cadastrar lead no estágio Fez Aula Experimental

| Campo | Descrição |
| --- | --- |
| Requisito funcional | O lead deve ser criado com o estágio Fez Aula Experimental e aparecer na listagem. |
| Ator | Usuário autenticado com acesso a Prospecção. |
| Pré-condição | Sessão autenticada com permissão para adicionar leads. Dados de contato de teste disponíveis e estágio Fez Aula Experimental selecionável. |
| Comportamento esperado | O lead deve ser criado com o estágio Fez Aula Experimental e aparecer na listagem. |
| Situação observada | O lead é criado com código 14 e estágio FEZ_AULA_EXP. A linha correspondente aparece ao final, e o total de leads passa de 9 para 10. |
| Prioridade | Média, proposta. |
| Rastreabilidade | [CT-RF79](Cenario_Teste/CT-RF79_Cadastro_Lead_Aula_Experimental.md) · — · [Evidências](Evidencias/CT-RF79_Cadastro_Lead_Aula_Experimental/README.md) · [Jam](https://jam.dev/c/bef3d877-056b-4274-87c3-da37869c54fd) |

#### Critérios de aceitação

1. O cadastro utiliza o estágio FEZ_AULA_EXP.
2. O novo lead aparece na listagem com o estágio escolhido.
3. O total de leads aumenta em um.
4. Em execução complementar, reabrir o registro para conferir os campos salvos.

#### Base da análise e limites

Aprovado conforme o resumo da gravação. A gravação valida o cadastro no estágio indicado; não demonstra agendamento ou realização de uma aula.
Análise da gravação e dos eventos capturados no Jam; não foi executado um novo teste no sistema.

Encaminhamento: Repetir o cadastro e conferir estágio, total e dados após reabertura.

<a id="rf80"></a>

### RF80 — Cadastrar lead no estágio Proposta

| Campo | Descrição |
| --- | --- |
| Requisito funcional | O lead deve ser criado no estágio Proposta e aparecer na listagem. |
| Ator | Usuário autenticado com acesso a Prospecção. |
| Pré-condição | Sessão autenticada com permissão para adicionar leads. Dados de contato de teste disponíveis e estágio Proposta selecionável. |
| Comportamento esperado | O lead deve ser criado no estágio Proposta e aparecer na listagem. |
| Situação observada | O cadastro retorna código 15 e o registro aparece na listagem com estágio Proposta. O total de leads passa de 10 para 11. |
| Prioridade | Média, proposta. |
| Rastreabilidade | [CT-RF80](Cenario_Teste/CT-RF80_Cadastro_Lead_Proposta.md) · — · [Evidências](Evidencias/CT-RF80_Cadastro_Lead_Proposta/README.md) · [Jam](https://jam.dev/c/84f94285-ae5f-4f95-b640-a9b107565aa6) |

#### Critérios de aceitação

1. O envio utiliza o estágio PROPOSTA.
2. O cadastro retorna um código e o lead é listado como Proposta.
3. O total de leads aumenta em um.
4. Em execução complementar, reabrir o registro para conferir os campos salvos.

#### Base da análise e limites

Aprovado conforme o resumo da gravação. O teste demonstra a classificação do lead no estágio Proposta; não demonstra emissão de proposta comercial.
Análise da gravação e dos eventos capturados no Jam; não foi executado um novo teste no sistema.

Encaminhamento: Repetir o cadastro e conferir estágio e dados após reabertura.

<a id="rf81"></a>

### RF81 — Cadastrar bandeira com parcela e conferir a listagem

| Campo | Descrição |
| --- | --- |
| Requisito funcional | A bandeira deve ser criada com a configuração de parcela e aparecer na listagem após o salvamento. |
| Ator | Usuário autenticado com acesso a Bandeiras de Cartão. |
| Pré-condição | Sessão autenticada com permissão para cadastrar Bandeiras de Cartão. Ambiente de teste com possibilidade de cadastrar uma bandeira e sua configuração de parcela. |
| Comportamento esperado | A bandeira deve ser criada com a configuração de parcela e aparecer na listagem após o salvamento. |
| Situação observada | A API confirma a criação da bandeira de código 34 e da parcela, mas a consulta seguinte retorna [] e a interface continua exibindo Nenhuma bandeira encontrada. A criação da parcela tem retorno de sucesso; o fluxo completo apresenta erro na recuperação/exibição do cadastro. |
| Prioridade | Alta, proposta. |
| Rastreabilidade | [CT-RF81](Cenario_Teste/CT-RF81_Cadastro_Bandeira_Parcela_Listagem.md) · [BUG-035](Relatorio-de-Bugs.md#bug-035) · [Evidências](Evidencias/CT-RF81_Cadastro_Bandeira_Parcela_Listagem/README.md) · [Jam](https://jam.dev/c/2f0280fb-6b7f-4cf0-a45c-02f8c16b6c5e) |

#### Critérios de aceitação

1. A criação da bandeira e da parcela é concluída de forma coerente.
2. A consulta posterior inclui a bandeira confirmada pela criação.
3. A listagem exibe o novo registro sem exigir um novo cadastro.
4. Reabrir e recarregar a bandeira permite conferir taxas e configuração de parcela.
5. Uma falha parcial deve produzir mensagem clara e permitir recuperação sem duplicidade.

#### Base da análise e limites

Reprovado nas evidências resumidas. A causa da divergência e a persistência efetiva no banco não foram verificadas. A gravação comprova a diferença entre os retornos de criação e de listagem, sem permitir atribuir a causa ao frontend ou ao backend.
Análise da gravação e dos eventos capturados no Jam; não foi executado um novo teste no sistema.

Encaminhamento: Investigar a divergência criação/consulta; retestar listagem, reabertura e recarga com e sem parcela.

<a id="rf82"></a>

### RF82 — Verificar aplicação dos temas na tela de Bandeiras

| Campo | Descrição |
| --- | --- |
| Requisito funcional | O tema selecionado deve ser aplicado de forma consistente ao fundo, aos painéis e aos textos da tela. |
| Ator | Usuário autenticado com acesso a Bandeiras de Cartão. |
| Pré-condição | Sessão autenticada com acesso à tela Bandeiras de Cartão. Controle de tema disponível e listagem no estado vazio observado. |
| Comportamento esperado | O tema selecionado deve ser aplicado de forma consistente ao fundo, aos painéis e aos textos da tela. |
| Situação observada | No tema Escuro, os painéis ficam escuros, mas o fundo principal continua claro. Os textos da área vazia da listagem apresentam baixa legibilidade visual. A descrição do Jam relata: Fundo com falta de cores e modo escuro incompleto. |
| Prioridade | Média, proposta. |
| Rastreabilidade | [CT-RF82](Cenario_Teste/CT-RF82_Tema_Escuro_Bandeiras.md) · [BUG-036](Relatorio-de-Bugs.md#bug-036) · [Evidências](Evidencias/CT-RF82_Tema_Escuro_Bandeiras/README.md) · [Jam](https://jam.dev/c/ae4dc198-8a42-4451-898a-fb376596c744) |

#### Critérios de aceitação

1. O tema Escuro é aplicado ao fundo principal e aos painéis.
2. Os textos do estado vazio permanecem visualmente legíveis.
3. Alternar os temas mantém a consistência entre fundo, painéis e textos.
4. No reteste, conferir também a listagem preenchida.
5. Medições de contraste, se realizadas, devem registrar valores e o critério adotado separadamente.

#### Base da análise e limites

Reprovado nas evidências resumidas. O erro visual é observado na gravação. Não foram medidos índices de contraste nem feita auditoria formal de acessibilidade; a causa técnica não foi determinada.
Análise da gravação e dos eventos capturados no Jam; não foi executado um novo teste no sistema.

Encaminhamento: Revisar os estilos da página e retestar Claro/Escuro com lista vazia e preenchida; medir contraste separadamente.

<a id="rf83"></a>

### RF83 — Validar cadastro de lead preenchendo apenas o nome

| Campo | Descrição |
| --- | --- |
| Requisito funcional | Segundo o cenário identificado como bug pelo autor, o cadastro incompleto deveria ser bloqueado e os campos obrigatórios deveriam ser indicados. |
| Ator | Usuário autenticado com acesso a Prospecção. |
| Pré-condição | Sessão autenticada com permissão para adicionar leads. Para concluir o reteste, confirmar com o produto quais campos são obrigatórios além do nome; essa regra não acompanha a evidência. |
| Comportamento esperado | Segundo o cenário identificado como bug pelo autor, o cadastro incompleto deveria ser bloqueado e os campos obrigatórios deveriam ser indicados. |
| Situação observada | O sistema aceita o envio sem bloqueio visível, cria o lead de código 19 e atualiza a listagem. O total de leads passa de 14 para 15. |
| Prioridade | Alta, proposta. |
| Rastreabilidade | [CT-RF83](Cenario_Teste/CT-RF83_Cadastro_Lead_Apenas_Nome.md) · [BUG-037](Relatorio-de-Bugs.md#bug-037) · [Evidências](Evidencias/CT-RF83_Cadastro_Lead_Apenas_Nome/README.md) · [Jam](https://jam.dev/c/ef3df03c-16ce-4cb6-b0c7-d04514cab4f6) |

#### Critérios de aceitação

1. Produto confirma e documenta os campos obrigatórios para o cadastro.
2. Se a regra exigir dados além do nome, o envio incompleto é bloqueado e cada campo faltante é indicado.
3. A validação confirmada é aplicada também no servidor, sem criar registro inválido.
4. Um envio completo conforme a regra permite cadastrar o lead.
5. Se apenas o nome for suficiente pela regra aprovada, reclassificar o caso e encerrar o relato como comportamento esperado.

#### Base da análise e limites

Reprovado conforme o relato; regra de obrigatoriedade a confirmar. A classificação de erro acompanha o título do Jam. A regra formal dos campos obrigatórios não foi fornecida; é necessário validá-la para definir exatamente quais campos devem impedir o cadastro. O e-mail está mascarado nos dados de rede, e sua ausência foi avaliada visualmente.
Análise da gravação e dos eventos capturados no Jam; não foi executado um novo teste no sistema.

Encaminhamento: Confirmar obrigatoriedade com produto antes de definir correção; testar campos isolados, envio completo e ausência de criação inválida.

<a id="rf84"></a>

### RF84 — Cadastrar lead no estágio Fechado

| Campo | Descrição |
| --- | --- |
| Requisito funcional | O lead deve ser criado no estágio Fechado e aparecer na listagem. |
| Ator | Usuário autenticado com acesso a Prospecção. |
| Pré-condição | Sessão autenticada com permissão para adicionar leads. Dados de contato de teste disponíveis e estágio Fechado selecionável. |
| Comportamento esperado | O lead deve ser criado no estágio Fechado e aparecer na listagem. |
| Situação observada | A janela fecha após salvar, o total de leads passa de 12 para 13 e o registro testeFechado aparece com código 17 e identificação Fechado. |
| Prioridade | Média, proposta. |
| Rastreabilidade | [CT-RF84](Cenario_Teste/CT-RF84_Cadastro_Lead_Fechado.md) · — · [Evidências](Evidencias/CT-RF84_Cadastro_Lead_Fechado/README.md) · [Jam](https://jam.dev/c/775b9003-fdf7-4ad5-8882-15ba606b6674) |

#### Critérios de aceitação

1. O estágio selecionado é FECHADO.
2. Salvar fecha a janela e inclui o lead com identificação Fechado.
3. O total de leads aumenta em um.
4. Em execução complementar, reabrir o cadastro para conferir todos os campos.

#### Base da análise e limites

Aprovado conforme o resumo da gravação. O corpo da resposta de salvamento não está disponível no evento consultado; o resultado é sustentado pelo retorno HTTP e pelo registro visível na listagem.
Análise da gravação e dos eventos capturados no Jam; não foi executado um novo teste no sistema.

Encaminhamento: Repetir o cadastro e conferir os dados após reabertura; capturar o corpo da resposta de salvamento.

A análise passa a cobrir 80 requisitos documentados. RF36–RF37 e RF63–RF64 permanecem fora do conjunto fornecido.
### Base da análise do RF85 — revisão de 15/11/2026

RF85 utiliza os painéis Info, Console, Network e Actions do Jam "Prospecção" e os quadros de 0:01 e 0:03. Foram registrados a troca de tema, os POST usuario/tema e o painel de Notificações. Não houve nova execução, acesso ao código ou ao banco, nem reteste.

Com RF85, a análise passa a cobrir 55 requisitos documentados. O CT-RF85 acrescenta uma aprovação limitada ao exemplo gravado.

### Base da análise do RF86 — revisão de 15/11/2026

RF86 utiliza os painéis Info, Console, Network e Actions do Jam "Prospecção" e os quadros de 0:12, 0:13 e 0:44. Foram registrados a busca por texto, os cartões e a ausência de requisição na busca. Não houve nova execução, acesso ao código ou ao banco, nem reteste.

Com RF86, a análise passa a cobrir 56 requisitos documentados. O CT-RF86 acrescenta uma aprovação limitada ao exemplo gravado.

### Base da análise do RF87 — revisão de 15/11/2026

RF87 utiliza os painéis Info, Console, Network e Actions do Jam "Prospecção" e os quadros de 0:16, 0:19 e 0:21. Foram registrados o filtro por estágio, o indicador Novos Contatos, o botão Limpar e a ausência de requisição. Não houve nova execução, acesso ao código ou ao banco, nem reteste.

Com RF87, a análise passa a cobrir 57 requisitos documentados. O CT-RF87 acrescenta uma aprovação limitada ao exemplo gravado.

### Base da análise do RF88 — revisão de 15/11/2026

RF88 utiliza os painéis Info, Console, Network e Actions do Jam "Prospecção", os corpos da primeira requisição e os quadros de 0:24 e 0:39. Foram registrados o cadastro, os dois POST de criação e a atualização dos cartões. Não houve nova execução, acesso ao código ou ao banco, nem reteste.

Com RF88, a análise passa a cobrir 58 requisitos documentados. O CT-RF88 acrescenta um ponto a validar, sem defeito confirmado.

### Base da análise do RF89 — revisão de 15/11/2026

RF89 utiliza os painéis Info, Console, Network e Actions do Jam "Prospecção", o corpo do salvar-lead, a resposta do buscar-lead e os quadros de 0:47. Foram registrados o telefone de 30 dígitos, a ausência de validação e a gravação do valor. Não houve nova execução, acesso ao código ou ao banco, nem reteste.

Com RF89, a análise passa a cobrir 59 requisitos documentados. O CT-RF89 acrescenta uma reprovação, vinculada ao BUG-038, em triagem.

### Base da análise do RF90 — revisão de 15/11/2026

RF90 utiliza os painéis Info, Console, Network e Actions do Jam "Prospecção", os corpos de buscar-lead e atualizar-lead e os quadros de 0:47, 0:57 e 1:01. Foram registrados a abertura do lead, a atualização do nome e a listagem atualizada. Não houve nova execução, acesso ao código ou ao banco, nem reteste.

Com RF90, a análise passa a cobrir 60 requisitos documentados. O CT-RF90 acrescenta uma aprovação limitada ao exemplo gravado.

### Base da análise do RF91 — revisão de 15/11/2026

RF91 utiliza os painéis Info, Console, Network e Actions do Jam "Contas a Pagar" e os quadros de 0:03 e 0:12. Foram registrados os filtros por nome, tipo de data, período e status e o resultado vazio. Não houve nova execução, acesso ao código ou ao banco, nem reteste.

Com RF91, a análise passa a cobrir 61 requisitos documentados. O CT-RF91 acrescenta um ponto a validar, sem defeito confirmado.

### Base da análise do RF92 — revisão de 15/11/2026

RF92 utiliza os painéis Info, Console, Network e Actions do Jam "Contas a Pagar", o corpo e a resposta da criação e os quadros de 0:15, 0:41 e 0:50. Foram registrados o cadastro sem colaborador, o HTTP 201 e a listagem com "-". Não houve nova execução, acesso ao código ou ao banco, nem reteste.

Com RF92, a análise passa a cobrir 62 requisitos documentados. O CT-RF92 acrescenta uma reprovação, vinculada ao BUG-039, em triagem.

### Base da análise do RF93 — revisão de 15/11/2026

RF93 utiliza os painéis Info, Console, Network e Actions do Jam "Contas a Pagar" e o quadro de 0:26. Foram registrados a abertura do modal, a busca sem resultado e a resposta de 2 B. Não houve nova execução, acesso ao código ou ao banco, nem reteste.

Com RF93, a análise passa a cobrir 63 requisitos documentados. O CT-RF93 acrescenta um ponto a validar, sem defeito confirmado.

### Base da análise do RF94 — revisão de 15/11/2026

RF94 utiliza os painéis Info, Console, Network e Actions do Jam "Contas a Pagar" e o quadro de 0:52. Foram registrados a abertura do modal e os dados apresentados. Não houve nova execução, acesso ao código ou ao banco, nem reteste.

Com RF94, a análise passa a cobrir 64 requisitos documentados. O CT-RF94 acrescenta uma aprovação limitada ao exemplo gravado.

### Base da análise do RF95 — revisão de 15/11/2026

RF95 utiliza os painéis Info, Console, Network e Actions do Jam "Contas a Pagar", o corpo e a resposta da exclusão e os quadros de 0:54 e 0:59. Foram registrados o diálogo, a exclusão e a listagem. Não houve nova execução, acesso ao código ou ao banco, nem reteste.

Com RF95, a análise passa a cobrir 65 requisitos documentados. O CT-RF95 acrescenta uma aprovação limitada ao exemplo gravado.

### Base da análise do RF96 — revisão de 15/11/2026

RF96 utiliza os painéis Info, Console, Network e Actions do Jam "Modelos de Contrato" e os quadros de 0:09, 0:21, 0:33 e 0:36. Foram registrados a inserção das variáveis e a pré-visualização. Não houve nova execução, acesso ao código ou ao banco, nem reteste.

Com RF96, a análise passa a cobrir 66 requisitos documentados. O CT-RF96 acrescenta uma aprovação limitada ao exemplo gravado.

### Base da análise do RF97 — revisão de 15/11/2026

RF97 utiliza os painéis Info, Console, Network e Actions do Jam "Modelos de Contrato" e a resposta da lista de modelos. Foram registrados a criação (HTTP 201) e o modelo de id 15 na lista do servidor. Não houve nova execução, acesso ao código ou ao banco, nem reteste.

Com RF97, a análise passa a cobrir 67 requisitos documentados. O CT-RF97 acrescenta uma aprovação limitada ao exemplo gravado.

### Base da análise do RF98 — revisão de 15/11/2026

RF98 utiliza os painéis Info, Console, Network e Actions do Jam "Modelos de Contrato", a resposta de modelos-contrato e os quadros de 0:00, 0:39, 0:45 e 0:49. Foram registrados a lista de 15 modelos e a tabela sem linhas. Não houve nova execução, acesso ao código ou ao banco, nem reteste.

Com RF98, a análise passa a cobrir 68 requisitos documentados. O CT-RF98 acrescenta uma reprovação, vinculada ao BUG-040, em triagem.

### Base da análise do RF99 — revisão de 15/11/2026

RF99 utiliza os painéis Info, Console, Network e Actions do Jam "Planos" e os quadros de 0:03, 0:06 e 0:13. Foram registrados os filtros por código e nome e o botão Buscar. Não houve nova execução, acesso ao código ou ao banco, nem reteste.

Com RF99, a análise passa a cobrir 69 requisitos documentados. O CT-RF99 acrescenta uma aprovação limitada ao exemplo gravado.

### Base da análise do RF100 — revisão de 15/11/2026

RF100 utiliza os painéis Info, Console, Network e Actions do Jam "Planos" e os quadros de 0:16 e 0:19. Foram registrados a troca de tema, os POST usuario/tema e o painel de Notificações. Não houve nova execução, acesso ao código ou ao banco, nem reteste.

Com RF100, a análise passa a cobrir 70 requisitos documentados. O CT-RF100 acrescenta uma aprovação limitada ao exemplo gravado.

### Base da análise do RF101 — revisão de 15/11/2026

RF101 utiliza os painéis Info, Console, Network e Actions do Jam "Planos", o corpo e a resposta da criação e os quadros de 0:24, 0:46 e 0:53. Foram registrados o cadastro e o contador de planos. Não houve nova execução, acesso ao código ou ao banco, nem reteste.

Com RF101, a análise passa a cobrir 71 requisitos documentados. O CT-RF101 acrescenta uma aprovação limitada ao exemplo gravado.

### Base da análise do RF102 — revisão de 15/11/2026

RF102 utiliza os painéis Info, Console, Network e Actions do Jam "Planos", os corpos das requisições de criação e atualização e os quadros de 0:03, 0:53 e 1:08. Foram registrados os cartões Planos e Ativos e o status dos planos nas requisições. Não houve nova execução, acesso ao código ou ao banco, nem reteste.

Com RF102, a análise passa a cobrir 72 requisitos documentados. O CT-RF102 acrescenta uma reprovação, vinculada ao BUG-041, em triagem.

### Base da análise do RF103 — revisão de 15/11/2026

RF103 utiliza os painéis Info, Console, Network e Actions do Jam "Planos", os corpos das requisições e respostas de seleção e atualização e o quadro de 1:02. Foram registrados a abertura do plano e a atualização. Não houve nova execução, acesso ao código ou ao banco, nem reteste.

Com RF103, a análise passa a cobrir 73 requisitos documentados. O CT-RF103 acrescenta uma aprovação limitada ao exemplo gravado.

### Base da análise do RF104 — revisão de 16/11/2026

RF104 utiliza os painéis Info, Console, Network e Actions do Jam "Tipos de Pagamento" e os quadros de 0:00 e 0:14. Foram registrados o preenchimento do nome, o acionamento dos seletores e de Buscar e a ausência de requisição de listagem. Não houve nova execução, acesso ao código ou ao banco, nem reteste.

Com RF104, a análise passa a cobrir 97 requisitos documentados. O CT-RF104 acrescenta um ponto a validar, sem defeito confirmado.

### Base da análise do RF105 — revisão de 16/11/2026

RF105 utiliza os painéis Info, Console, Network e Actions do Jam "Tipos de Pagamento", o corpo e a resposta da criação, a resposta da lista e os quadros de 0:00, 0:19, 0:24 e 0:27. Foram registrados o cadastro com HTTP 201, a ausência de status no corpo e na resposta e os cartões. Não houve nova execução, acesso ao código ou ao banco, nem reteste.

Com RF105, a análise passa a cobrir 98 requisitos documentados. O CT-RF105 acrescenta uma reprovação, vinculada ao BUG-042, em triagem.

### Base da análise do RF106 — revisão de 16/11/2026

RF106 utiliza os painéis Info, Console, Network e Actions do Jam "Tipos de Pagamento", o corpo e a resposta da seleção e da edição e os quadros de 0:34 e 0:45. Foram registrados a abertura do tipo, a edição e a atualização da listagem. Não houve nova execução, acesso ao código ou ao banco, nem reteste.

Com RF106, a análise passa a cobrir 99 requisitos documentados. O CT-RF106 acrescenta uma aprovação limitada ao exemplo gravado.

### Base da análise do RF107 — revisão de 16/11/2026

RF107 utiliza os painéis Info, Console, Network e Actions do Jam "Tipos de Pagamento", os corpos e as respostas das duas exclusões e os quadros de 0:37, 0:40, 0:43 e 0:45. Foram registrados o HTTP 404, o erro de integridade referencial e a mensagem genérica da tela. Não houve nova execução, acesso ao código ou ao banco, nem reteste.

Com RF107, a análise passa a cobrir 100 requisitos documentados. O CT-RF107 acrescenta uma reprovação, vinculada ao BUG-043, em triagem.

### Base da análise do RF108 — revisão de 16/11/2026

RF108 utiliza os painéis Info, Console, Network e Actions do Jam "Tipos de Pagamento" e os quadros de 0:41, 0:45, 0:50 e 0:57. Foram registrados a alternância de tema e o painel de notificações. Não houve nova execução, acesso ao código ou ao banco, nem reteste.

Com RF108, a análise passa a cobrir 101 requisitos documentados. O CT-RF108 acrescenta uma aprovação limitada ao exemplo gravado.

---

[← Início](../README.md) · [Cenários de teste](Cenario_Teste/) · [Evidências de Clientes](Evidencias/CT-RF03_Filtros_Clientes/README.md)
