# 📦 Análise de Requisitos — SIFIT

**Módulos:** Autenticação, Perfil, Clientes / Filtros, Financeiro, Página inicial / Personais, SifitBox / Modalidades e Turmas, Categorias Crossfit, Avaliações, Exercícios, Grupos Musculares, Dashboard, Objetivos de Treino, Fichas de Anamnese, Colaboradores, Prospecção e Bandeiras de Cartão.

**Atualização:** 18/11/2026 — Renumeração completa de RF01 a RF161 (sem lacunas), seguindo a ordem de navegação do aplicativo (tela de login/recuperação de senha, depois o menu lateral de cima para baixo: Principal, Operação da Academia, Treinamento, Financeiro, Comercial, Gestão, Saúde, Inteligência e Configurações), conforme as capturas de tela fornecidas. O conteúdo técnico de cada requisito e caso de teste foi preservado; apenas a numeração e a posição no documento mudaram. BUG-001–BUG-054 em triagem ou já referenciados no relatório de bugs.

**Padronização documental:** 13/11/2026, sem alteração dos resultados registrados.

Esta análise documenta 161 requisitos de QA (RF01 a RF161, sem lacunas), numerados na ordem em que as telas correspondentes aparecem no aplicativo, com base nos relatos e nas evidências fornecidas. O histórico de quando cada requisito foi originalmente levantado (datas de 14 a 18/11/2026) está preservado dentro de cada seção, nas notas históricas e nas referências cruzadas. Os critérios abaixo constituem a referência de QA para esses fluxos; não representam validação de uma especificação formal pelo responsável pelo produto.

## 📋 Visão geral dos requisitos

| Código | Funcionalidade | Prioridade | Caso relacionado |
| --- | --- | --- | --- |
| [RF01](#rf01--autenticar-usuário-com-credenciais-válidas) | Login com sucesso | Alta | [CT-RF01_loginComSucesso](Cenario_Teste/CT-RF01_loginComSucesso.md) |
| [RF02](#rf02) | Recusar autenticação com senha incorreta | Alta, proposta | [CT-RF02](Cenario_Teste/CT-RF02_Login_SenhaIncorreta.md) |
| [RF03](#rf03) | Recusar autenticação com usuário inexistente | Alta, proposta | [CT-RF03](Cenario_Teste/CT-RF03_Login_UsuarioInexistente.md) |
| [RF04](#rf04--iniciar-recuperação-de-senha) | Recuperação de senha | Alta | [CT-RF04](Cenario_Teste/CT-RF04_Esqueci-senha.md) |
| [RF05](#rf05--exibir-perfil-do-usuário-autenticado) | Perfil do usuário | Alta | [CT-RF05_ERRO](Cenario_Teste/CT-RF05_ERRO.md) |
| [RF06](#rf06) | Validar a ordem das datas do período | Média, proposta | [CT-RF06](Cenario_Teste/CT-RF06_Periodo_Dashboard.md) |
| [RF07](#rf07) | Identificar personais sem confundir códigos com contagem | Média, proposta | [CT-RF07](Cenario_Teste/CT-RF07_Codigos_Personais.md) |
| [RF08](#rf08) | Carregar o dashboard sem falhas de servidor ou requisições redundantes | Alta, proposta | [CT-RF08](Cenario_Teste/CT-RF08_Erro_Servidor_Excesso_Requisicoes.md) |
| [RF09](#rf09--pesquisar-clientes-com-filtros-combinados) | Filtros da página Clientes | Alta, proposta para triagem | [CT-RF09](Cenario_Teste/CT-RF09_FILTRO_TelaClientes.md) |
| [RF10](#rf10) | Cadastrar avaliação ou informar validação específica | Alta, proposta | [CT-RF10](Cenario_Teste/CT-RF10_Cadastro_Avaliacao.md) |
| [RF11](#rf11) | Oferecer retorno ao solicitar exportação financeira | Média, proposta | [CT-RF11](Cenario_Teste/CT-RF11_Exportacao_Financeiro.md) |
| [RF12](#rf12) | Manter contagem e paginação coerentes com as mensalidades | Alta, proposta | [CT-RF12](Cenario_Teste/CT-RF12_Contagem_Mensalidades.md) |
| [RF13](#rf13) | Aplicar o filtro Até 7 dias com contagem consistente | Alta, proposta | [CT-RF13](Cenario_Teste/CT-RF13_Filtro_Mensalidades.md) |
| [RF14](#rf14) | Apresentar a composição e o valor comunicado na cobrança | Alta, proposta | [CT-RF14](Cenario_Teste/CT-RF14_Calculo_Cobranca.md) |
| [RF15](#rf15) | Explicitar o escopo dos indicadores financeiros | Média, proposta | [CT-RF15](Cenario_Teste/CT-RF15_Metricas_Financeiro.md) |
| [RF16](#rf16) | Filtrar contas a pagar por nome, data e status | Média, proposta | [CT-RF16](Cenario_Teste/CT-RF16_Filtros_Contas_Pagar.md) |
| [RF17](#rf17) | Exigir o colaborador no cadastro de conta a pagar a colaborador | Alta, proposta | [CT-RF17](Cenario_Teste/CT-RF17_Cadastro_Conta_Colaborador_Sem_Colaborador.md) |
| [RF18](#rf18) | Buscar e selecionar colaborador no cadastro de conta | Média, proposta | [CT-RF18](Cenario_Teste/CT-RF18_Busca_Colaborador_Conta_Pagar.md) |
| [RF19](#rf19) | Visualizar os dados de uma conta a pagar | Baixa, proposta | [CT-RF19](Cenario_Teste/CT-RF19_Visualizacao_Conta_Pagar.md) |
| [RF20](#rf20) | Excluir uma conta a pagar com confirmação | Média, proposta | [CT-RF20](Cenario_Teste/CT-RF20_Exclusao_Conta_Pagar.md) |
| [RF21](#rf21) | Permitir informar o código do exercício conforme a regra | Média, proposta | [CT-RF21](Cenario_Teste/CT-RF21_Digitacao_Codigo_Exercicio.md) |
| [RF22](#rf22) | Exclusão de exercício | Média, proposta | [CT-RF22](Cenario_Teste/CT-RF22_Exclusao_Exercicio.md) |
| [RF23](#rf23) | Edição de exercício aumenta o total e mantém duas entradas | Média, proposta | [CT-RF23](Cenario_Teste/CT-RF23_Edicao_Exercicio.md) |
| [RF24](#rf24) | Envio de exercício com imagem | Média, proposta | [CT-RF24](Cenario_Teste/CT-RF24_Envio_Exercicio_Imagem.md) |
| [RF25](#rf25) | Validar campos obrigatórios do exercício | Alta, proposta | [CT-RF25](Cenario_Teste/CT-RF25_Exercicio_Campos_Vazios.md) |
| [RF26](#rf26) | Rejeitar vídeo no campo de imagem com feedback | Média, proposta | [CT-RF26](Cenario_Teste/CT-RF26_Video_Campo_Imagem.md) |
| [RF27](#rf27) | Rejeitar imagem no campo de vídeo com feedback | Média, proposta | [CT-RF27](Cenario_Teste/CT-RF27_Imagem_Campo_Video.md) |
| [RF28](#rf28) | Excluir grupo muscular ou explicar o impedimento | Alta, proposta | [CT-RF28](Cenario_Teste/CT-RF28_Exclusao_GrupoMuscular.md) |
| [RF29](#rf29) | Exibir as imagens cadastradas dos grupos musculares | Média, proposta | [CT-RF29](Cenario_Teste/CT-RF29_Imagens_GruposMusculares.md) |
| [RF30](#rf30) | Cadastrar e listar um grupo muscular | Média, proposta | [CT-RF30](Cenario_Teste/CT-RF30_Cadastro_GrupoMuscular.md) |
| [RF31](#rf31) | Alterar o tipo de membro de um grupo muscular | Média, proposta | [CT-RF31](Cenario_Teste/CT-RF31_Edicao_TipoMembro.md) |
| [RF32](#rf32) | Filtrar a listagem de grupos musculares por código e tipo | Média, proposta | [CT-RF32](Cenario_Teste/CT-RF32_Filtros_GruposMusculares.md) |
| [RF33](#rf33) | Cadastrar objetivo de treino ou informar validação específica | Alta, proposta | [CT-RF33](Cenario_Teste/CT-RF33_Cadastro_Objetivo_Treino.md) |
| [RF34](#rf34) | Excluir grupo ou explicar o impedimento | Alta, proposta | [CT-RF34](Cenario_Teste/CT-RF34_Exclusao_Grupo.md) |
| [RF35](#rf35) | Persistir todos os campos editados de um grupo | Alta, proposta | [CT-RF35](Cenario_Teste/CT-RF35_Edicao_Grupo.md) |
| [RF36](#rf36) | Filtrar categorias por código e nome | Média, proposta | [CT-RF36](Cenario_Teste/CT-RF36_Filtros_Categorias.md) |
| [RF37](#rf37) | Salvar a atualização do nome de categoria | Média, proposta | [CT-RF37](Cenario_Teste/CT-RF37_Atualizacao_Categoria.md) |
| [RF38](#rf38) | Excluir categoria permitida ou explicar o impedimento | Média, proposta | [CT-RF38](Cenario_Teste/CT-RF38_Exclusao_Categoria.md) |
| [RF39](#rf39) | Cadastrar e listar uma nova categoria | Média, proposta | [CT-RF39](Cenario_Teste/CT-RF39_Criacao_Categoria.md) |
| [RF40](#rf40) | Cadastrar categoria com código automático e localizá-la pelos filtros | Média, proposta | [CT-RF40](Cenario_Teste/CT-RF40_Cadastro_Categoria_Codigo_Automatico.md) |
| [RF41](#rf41) | Preservar a legibilidade das tabelas no tema escuro | Média, proposta | [CT-RF41](Cenario_Teste/CT-RF41_Contraste_TemaEscuro.md) |
| [RF42](#rf42) | Permitir concluir e cancelar a edição de modalidade | Média, proposta | [CT-RF42](Cenario_Teste/CT-RF42_Edicao_Modalidade.md) |
| [RF43](#rf43) | Comunicar e aplicar a regra de remoção de modalidade | Média, proposta | [CT-RF43](Cenario_Teste/CT-RF43_Exclusao_Modalidade.md) |
| [RF44](#rf44) | Cadastrar modalidade e apresentá-la na listagem | Média, proposta | [CT-RF44](Cenario_Teste/CT-RF44_Cadastro_Modalidade.md) |
| [RF45](#rf45) | Aplicar e comunicar a regra de exclusão de turmas e modalidades | Média, proposta | [CT-RF45](Cenario_Teste/CT-RF45_Exclusao_Turmas_Modalidades.md) |
| [RF46](#rf46) | Cadastrar turma ou informar visivelmente o dado que impede o envio | Média, proposta | [CT-RF46](Cenario_Teste/CT-RF46_Cadastro_Turma_Sem_Modalidade.md) |
| [RF47](#rf47) | Solicitar saque e informar o resultado | Alta, proposta | [CT-RF47](Cenario_Teste/CT-RF47_Solicitacao_Saque_PagarMe.md) |
| [RF48](#rf48) | Criar cobrança pelo painel Pagar.me | Média, proposta | [CT-RF48](Cenario_Teste/CT-RF48_Criacao_Cobranca_PagarMe.md) |
| [RF49](#rf49) | Atualizar Recebimentos e gráfico conforme o período | Média, proposta | [CT-RF49](Cenario_Teste/CT-RF49_Painel_PagarMe_Periodo.md) |
| [RF50](#rf50) | Filtrar despesas fixas por código e por nome | Média, proposta | [CT-RF50](Cenario_Teste/CT-RF50_Filtros_Despesas_Fixas.md) |
| [RF51](#rf51) | Cadastrar despesa fixa com uma única gravação | Média, proposta | [CT-RF51](Cenario_Teste/CT-RF51_Cadastro_Despesa_Fixa.md) |
| [RF52](#rf52) | Excluir despesa fixa com confirmação | Média, proposta | [CT-RF52](Cenario_Teste/CT-RF52_Exclusao_Despesa_Fixa.md) |
| [RF53](#rf53) | Editar despesa fixa preservando o registro | Média, proposta | [CT-RF53](Cenario_Teste/CT-RF53_Edicao_Despesa_Fixa.md) |
| [RF54](#rf54) | Gerar o relatório de Matrículas em PDF | Média, proposta | [CT-RF54](Cenario_Teste/CT-RF54_Relatorio_Matriculas.md) |
| [RF55](#rf55) | Apresentar o valor a receber no relatório de Contas a Receber | Alta, proposta | [CT-RF55](Cenario_Teste/CT-RF55_Relatorio_Contas_Receber.md) |
| [RF56](#rf56) | Gerar o relatório de Contas a Pagar (Pagas) | Média, proposta | [CT-RF56](Cenario_Teste/CT-RF56_Relatorio_Contas_Pagar_Pagas.md) |
| [RF57](#rf57) | Gerar o relatório de Avaliações em PDF | Alta, proposta | [CT-RF57](Cenario_Teste/CT-RF57_Relatorio_Avaliacoes_Vazio.md) |
| [RF58](#rf58) | Gerar o relatório de Clientes em PDF | Alta, proposta | [CT-RF58](Cenario_Teste/CT-RF58_Relatorio_Clientes_Vazio.md) |
| [RF59](#rf59) | Gerar o relatório de Colaboradores em PDF | Alta, proposta | [CT-RF59](Cenario_Teste/CT-RF59_Relatorio_Colaboradores_Vazio.md) |
| [RF60](#rf60) | Gerar o relatório de Caixas em PDF | Alta, proposta | [CT-RF60](Cenario_Teste/CT-RF60_Relatorio_Caixas_Vazio.md) |
| [RF61](#rf61) | Alternar entre os temas claro e escuro na Prospecção | Média, proposta | [CT-RF61](Cenario_Teste/CT-RF61_Temas_Prospeccao.md) |
| [RF62](#rf62) | Alternar o tema e consultar as notificações no cabeçalho | Baixa, proposta | [CT-RF62](Cenario_Teste/CT-RF62_Tema_Notificacoes_Prospeccao.md) |
| [RF63](#rf63) | Buscar leads por texto na listagem de Prospecção | Média, proposta | [CT-RF63](Cenario_Teste/CT-RF63_Busca_Leads_Prospeccao.md) |
| [RF64](#rf64) | Filtrar leads por estágio e restaurar a listagem | Média, proposta | [CT-RF64](Cenario_Teste/CT-RF64_Filtro_Estagio_Leads.md) |
| [RF65](#rf65) | Cadastrar lead no estágio Novo Contato | Média, proposta | [CT-RF65](Cenario_Teste/CT-RF65_Cadastro_Lead_Novo_Contato.md) |
| [RF66](#rf66) | Cadastrar lead no estágio Interessado | Média, proposta | [CT-RF66](Cenario_Teste/CT-RF66_Cadastro_Lead_Interessado.md) |
| [RF67](#rf67) | Cadastrar lead no estágio Fez Aula Experimental | Média, proposta | [CT-RF67](Cenario_Teste/CT-RF67_Cadastro_Lead_Aula_Experimental.md) |
| [RF68](#rf68) | Cadastrar lead no estágio Proposta | Média, proposta | [CT-RF68](Cenario_Teste/CT-RF68_Cadastro_Lead_Proposta.md) |
| [RF69](#rf69) | Validar cadastro de lead preenchendo apenas o nome | Alta, proposta | [CT-RF69](Cenario_Teste/CT-RF69_Cadastro_Lead_Apenas_Nome.md) |
| [RF70](#rf70) | Cadastrar lead no estágio Fechado | Média, proposta | [CT-RF70](Cenario_Teste/CT-RF70_Cadastro_Lead_Fechado.md) |
| [RF71](#rf71) | Cadastrar um lead com uma única gravação | Média, proposta | [CT-RF71](Cenario_Teste/CT-RF71_Cadastro_Lead_Prospeccao.md) |
| [RF72](#rf72) | Validar o telefone do lead | Média, proposta | [CT-RF72](Cenario_Teste/CT-RF72_Telefone_Lead_Sem_Validacao.md) |
| [RF73](#rf73) | Consultar os detalhes de um lead e cancelar a edição | Média, proposta | [CT-RF73](Cenario_Teste/CT-RF73_Detalhes_Lead_Cancelamento.md) |
| [RF74](#rf74) | Excluir leads com confirmação | Média, proposta | [CT-RF74](Cenario_Teste/CT-RF74_Exclusao_Leads_Confirmacao.md) |
| [RF75](#rf75) | Visualizar e editar um lead | Média, proposta | [CT-RF75](Cenario_Teste/CT-RF75_Edicao_Lead_Prospeccao.md) |
| [RF76](#rf76) | Alternar o tema e consultar as notificações na tela Planos | Baixa, proposta | [CT-RF76](Cenario_Teste/CT-RF76_Tema_Notificacoes_Planos.md) |
| [RF77](#rf77) | Filtrar planos por código e por nome | Média, proposta | [CT-RF77](Cenario_Teste/CT-RF77_Filtros_Planos.md) |
| [RF78](#rf78) | Cadastrar um plano | Alta, proposta | [CT-RF78](Cenario_Teste/CT-RF78_Cadastro_Plano.md) |
| [RF79](#rf79) | Manter o cartão Ativos coerente com o status dos planos | Média, proposta | [CT-RF79](Cenario_Teste/CT-RF79_Contador_Ativos_Planos.md) |
| [RF80](#rf80) | Editar um plano | Média, proposta | [CT-RF80](Cenario_Teste/CT-RF80_Edicao_Plano.md) |
| [RF81](#rf81) | Cadastrar um modelo de contrato | Média, proposta | [CT-RF81](Cenario_Teste/CT-RF81_Cadastro_Modelo_Contrato.md) |
| [RF82](#rf82) | Inserir variáveis e pré-visualizar o contrato | Média, proposta | [CT-RF82](Cenario_Teste/CT-RF82_Variaveis_Preview_Modelo_Contrato.md) |
| [RF83](#rf83) | Apresentar na listagem os modelos de contrato retornados pelo servidor | Alta, proposta | [CT-RF83](Cenario_Teste/CT-RF83_Listagem_Modelos_Contrato_Vazia.md) |
| [RF84](#rf84) | Filtrar tipos de pagamento por código, nome, status e tipo | Média, proposta | [CT-RF84](Cenario_Teste/CT-RF84_Filtros_Tipos_Pagamento.md) |
| [RF85](#rf85) | Gravar e refletir o status do tipo de pagamento no cadastro | Média, proposta | [CT-RF85](Cenario_Teste/CT-RF85_Cadastro_Tipo_Pagamento_Status.md) |
| [RF86](#rf86) | Editar um tipo de pagamento | Média, proposta | [CT-RF86](Cenario_Teste/CT-RF86_Edicao_Tipo_Pagamento.md) |
| [RF87](#rf87) | Impedir a exclusão de tipo de pagamento em uso com mensagem clara | Média, proposta | [CT-RF87](Cenario_Teste/CT-RF87_Exclusao_Tipo_Pagamento_Em_Uso.md) |
| [RF88](#rf88) | Alternar tema Claro/Escuro e abrir as notificações em Tipos de Pagamento | Baixa, proposta | [CT-RF88](Cenario_Teste/CT-RF88_Tema_Notificacoes_Tipos_Pagamento.md) |
| [RF89](#rf89) | Cadastrar bandeira com parcela e conferir a listagem | Alta, proposta | [CT-RF89](Cenario_Teste/CT-RF89_Cadastro_Bandeira_Parcela_Listagem.md) |
| [RF90](#rf90) | Verificar aplicação dos temas na tela de Bandeiras | Média, proposta | [CT-RF90](Cenario_Teste/CT-RF90_Tema_Escuro_Bandeiras.md) |
| [RF91](#rf91) | Recusar data de nascimento futura na edição de colaborador | Alta, proposta | [CT-RF91](Cenario_Teste/CT-RF91_Data_Nascimento_Futura_Colaborador.md) |
| [RF92](#rf92) | Exigir data de nascimento obrigatória do colaborador | Alta, proposta | [CT-RF92](Cenario_Teste/CT-RF92_Data_Nascimento_Obrigatoria_Colaborador.md) |
| [RF93](#rf93) | Validar o formato do CREF do colaborador | Média, proposta | [CT-RF93](Cenario_Teste/CT-RF93_CREF_Formato_Colaborador.md) |
| [RF94](#rf94) | Bloquear edição de colaborador com campo obrigatório vazio | Alta, proposta | [CT-RF94](Cenario_Teste/CT-RF94_Edicao_Colaborador_Campo_Obrigatorio_Vazio.md) |
| [RF95](#rf95) | Impedir função duplicada para o mesmo colaborador | Média, proposta | [CT-RF95](Cenario_Teste/CT-RF95_Funcao_Duplicada_Colaborador.md) |
| [RF96](#rf96) | Excluir colaborador sem erro de servidor | Alta, proposta | [CT-RF96](Cenario_Teste/CT-RF96_Exclusao_Colaborador_Erro_500.md) |
| [RF97](#rf97) | Manter o filtro por nome durante a paginação | Alta, proposta | [CT-RF97](Cenario_Teste/CT-RF97_Busca_Nome_Colaborador_Paginacao.md) |
| [RF98](#rf98) | Buscar colaborador por código existente | Média, proposta | [CT-RF98](Cenario_Teste/CT-RF98_Busca_Codigo_Existente_Colaborador.md) |
| [RF99](#rf99) | Exibir estado vazio para código inexistente | Alta, proposta | [CT-RF99](Cenario_Teste/CT-RF99_Busca_Codigo_Inexistente_Colaborador.md) |
| [RF100](#rf100) | Cadastrar anamnese sem erro de servidor | Alta, proposta para triagem | [CT-RF100](Cenario_Teste/CT-RF100_Cadastro_Anamnese.md) |
| [RF101](#rf101--gerenciar-modelos-de-anamnese-sem-erro-de-servidor) | Gerenciar modelos de anamnese sem erro de servidor | Média | [CT-RF101](Cenario_Teste/CT-RF101_Gestao_Modelos_Anamnese.md) |
| [RF102](#rf102--gerenciar-categorias-de-anamnese-sem-erro-de-servidor) | Gerenciar categorias de anamnese sem erro de servidor | Média | [CT-RF102](Cenario_Teste/CT-RF102_Gestao_Categorias_Anamnese.md) |
| [RF103](#rf103--editar-pergunta-de-anamnese-sem-erro-de-servidor) | Editar pergunta de anamnese sem erro de servidor | Alta, proposta para triagem | [CT-RF103](Cenario_Teste/CT-RF103_Edicao_Pergunta_Anamnese.md) |
| [RF104](#rf104) | Abrir e fechar a configuração de Risco de Evasão | Média, proposta | [CT-RF104](Cenario_Teste/CT-RF104_Central_Configuracao_Risco_Evasao_Cancelar.md) |
| [RF105](#rf105) | Executar Risco de Evasão manualmente pela Central | Média, proposta | [CT-RF105](Cenario_Teste/CT-RF105_Central_Risco_Evasao_Executar_Agora.md) |
| [RF106](#rf106) | Abrir os resultados de Risco de Evasão pela Central | Média, proposta | [CT-RF106](Cenario_Teste/CT-RF106_Central_Abrir_Resultados_Risco_Evasao.md) |
| [RF107](#rf107) | Desativar Risco de Evasão e conferir a persistência e o contador | Média, proposta | [CT-RF107](Cenario_Teste/CT-RF107_Central_Desativar_Risco_Evasao_Contador.md) |
| [RF108](#rf108) | Conferir a execução de Risco de Evasão na Central e em Resultados IA | Média, proposta | [CT-RF108](Cenario_Teste/CT-RF108_Central_Resultados_IA_Execucao_Evasao.md) |
| [RF109](#rf109) | Abrir Aniversariantes e conferir a prévia da automação | Média, proposta | [CT-RF109](Cenario_Teste/CT-RF109_Central_Aniversariantes_Previa_Risco.md) |
| [RF110](#rf110) | Ativar Aniversariantes e conferir a persistência e o contador | Média, proposta | [CT-RF110](Cenario_Teste/CT-RF110_Central_Ativar_Aniversariantes_Contador.md) |
| [RF111](#rf111) | Verificar recursos marcados como Em desenvolvimento | Média, proposta | [CT-RF111](Cenario_Teste/CT-RF111_Central_Recursos_Em_Desenvolvimento.md) |
| [RF112](#rf112) | Atualizar a Central de Automações | Média, proposta | [CT-RF112](Cenario_Teste/CT-RF112_Central_Automacoes_Atualizar.md) |
| [RF113](#rf113) | Filtrar Resultados da Inteligência por Hoje | Média, proposta | [CT-RF113](Cenario_Teste/CT-RF113_Resultados_IA_Filtro_Hoje.md) |
| [RF114](#rf114) | Filtrar Resultados da Inteligência pelos últimos 7 dias | Média, proposta | [CT-RF114](Cenario_Teste/CT-RF114_Resultados_IA_Filtro_7_Dias.md) |
| [RF115](#rf115) | Filtrar Resultados da Inteligência pelos últimos 30 dias | Média, proposta | [CT-RF115](Cenario_Teste/CT-RF115_Resultados_IA_Filtro_30_Dias.md) |
| [RF116](#rf116) | Filtrar Resultados da Inteligência pelos últimos 90 dias | Média, proposta | [CT-RF116](Cenario_Teste/CT-RF116_Resultados_IA_Filtro_90_Dias.md) |
| [RF117](#rf117) | Salvar as configurações gerais de acesso e presença | Média, proposta | [CT-RF117](Cenario_Teste/CT-RF117_Configuracoes_Home_Salvamento.md) |
| [RF118](#rf118) | Validar o salvamento com o campo de dias de ausência vazio | Média, proposta | [CT-RF118](Cenario_Teste/CT-RF118_Configuracoes_Dias_Ausencia_Vazio.md) |
| [RF119](#rf119) | Salvar um valor válido de dias de ausência | Média, proposta | [CT-RF119](Cenario_Teste/CT-RF119_Configuracoes_Salvar_Dias_Ausencia_Valido.md) |
| [RF120](#rf120) | Bloquear número negativo no campo de dias de ausência | Média, proposta | [CT-RF120](Cenario_Teste/CT-RF120_Configuracoes_Dias_Ausencia_Negativo.md) |
| [RF121](#rf121) | Validar letras no campo de dias de ausência | Média, proposta | [CT-RF121](Cenario_Teste/CT-RF121_Configuracoes_Dias_Ausencia_Texto.md) |
| [RF122](#rf122) | Cancelar uma alteração nas Configurações sem salvar | Média, proposta | [CT-RF122](Cenario_Teste/CT-RF122_Configuracoes_Cancelar_Alteracao.md) |
| [RF123](#rf123) | Alterar e persistir a opção Trabalha com turmas? | Média, proposta | [CT-RF123](Cenario_Teste/CT-RF123_Configuracoes_Trabalha_Com_Turmas.md) |
| [RF124](#rf124) | Conferir a configuração Academia marcada como Box? | Média, proposta | [CT-RF124](Cenario_Teste/CT-RF124_Configuracoes_Academia_Marcada_Box.md) |
| [RF125](#rf125) | Conferir a configuração de acesso ao sistema desktop | Média, proposta | [CT-RF125](Cenario_Teste/CT-RF125_Configuracoes_Acesso_Desktop.md) |
| [RF126](#rf126) | Navegar pelas abas de Configurações com a senha da biometria protegida | Alta, proposta | [CT-RF126](Cenario_Teste/CT-RF126_Configuracoes_Abas_Biometria_Senha.md) |
| [RF127](#rf127) | Mascarar a API Key no formulário de WhatsApp | Média, proposta | [CT-RF127](Cenario_Teste/CT-RF127_Integracoes_WhatsApp_Mascarar_API_Key.md) |
| [RF128](#rf128) | Validar uma URL da API sem formato de endereço | Média, proposta | [CT-RF128](Cenario_Teste/CT-RF128_Integracoes_WhatsApp_Validar_URL_API.md) |
| [RF129](#rf129) | Bloquear o salvamento com Nome da Instância vazio | Média, proposta | [CT-RF129](Cenario_Teste/CT-RF129_Integracoes_WhatsApp_Instancia_Obrigatoria.md) |
| [RF130](#rf130) | Persistir a opção Ativo da integração de WhatsApp | Média, proposta | [CT-RF130](Cenario_Teste/CT-RF130_Integracoes_WhatsApp_Persistir_Ativo.md) |
| [RF131](#rf131) | Tratar falha ao conectar WhatsApp via Evolution API | Média, proposta | [CT-RF131](Cenario_Teste/CT-RF131_Integracoes_WhatsApp_Conectar_Evolution.md) |
| [RF132](#rf132) | Consultar novamente o status da integração de WhatsApp | Média, proposta | [CT-RF132](Cenario_Teste/CT-RF132_Integracoes_WhatsApp_Atualizar_Status.md) |
| [RF133](#rf133) | Atualizar a verificação do WhatsApp enquanto aguarda QR Code | Média, proposta | [CT-RF133](Cenario_Teste/CT-RF133_Integracoes_WhatsApp_Atualizar_Status_Aguardando_QR.md) |
| [RF134](#rf134) | Salvar mensagens de aniversário para WhatsApp e SMS | Média, proposta | [CT-RF134](Cenario_Teste/CT-RF134_Configuracoes_Aniversario_Salvar_WhatsApp_SMS.md) |
| [RF135](#rf135) | Desabilitar o envio automático de aniversário | Média, proposta | [CT-RF135](Cenario_Teste/CT-RF135_Configuracoes_Aniversario_Desabilitar_Envio_Automatico.md) |
| [RF136](#rf136) | Cancelar a edição da mensagem de aniversário do WhatsApp | Média, proposta | [CT-RF136](Cenario_Teste/CT-RF136_Configuracoes_Aniversario_Cancelar_Mensagem_WhatsApp.md) |
| [RF137](#rf137) | Inserir variáveis na mensagem de aniversário do WhatsApp | Média, proposta | [CT-RF137](Cenario_Teste/CT-RF137_Configuracoes_Aniversario_Inserir_Variaveis_WhatsApp.md) |
| [RF138](#rf138) | Persistir a desativação do Pagamento Online | Média, proposta | [CT-RF138](Cenario_Teste/CT-RF138_Configuracoes_Pagamento_Online_Desativar.md) |
| [RF139](#rf139) | Salvar uma Cor Principal hexadecimal válida | Média, proposta | [CT-RF139](Cenario_Teste/CT-RF139_Configuracoes_Design_Salvar_Cor_Principal.md) |
| [RF140](#rf140) | Rejeitar código hexadecimal inválido na Cor Secundária | Média, proposta | [CT-RF140](Cenario_Teste/CT-RF140_Configuracoes_Design_Validar_Cor_Secundaria.md) |
| [RF141](#rf141) | Informar o limite de tamanho ao rejeitar o logo | Baixa, proposta | [CT-RF141](Cenario_Teste/CT-RF141_Configuracoes_Design_Logo_Limite_Tamanho.md) |
| [RF142](#rf142) | Desativar a cobrança da avaliação do cliente | Média, proposta | [CT-RF142](Cenario_Teste/CT-RF142_Configuracoes_Avaliacao_Desativar_Cobranca.md) |
| [RF143](#rf143) | Alterar o tipo de avaliação para Bioimpedância | Média, proposta | [CT-RF143](Cenario_Teste/CT-RF143_Configuracoes_Avaliacao_Tipo_Bioimpedancia.md) |
| [RF144](#rf144) | Habilitar Teste Físico nas configurações de avaliação | Média, proposta | [CT-RF144](Cenario_Teste/CT-RF144_Configuracoes_Avaliacao_Habilitar_Teste_Fisico.md) |
| [RF145](#rf145) | Cancelar a edição da senha de Biometria | Média, proposta | [CT-RF145](Cenario_Teste/CT-RF145_Configuracoes_Biometria_Cancelar_Edicao_Senha.md) |
| [RF146](#rf146) | Rejeitar um valor sem formato de IP em Biometria | Média, proposta | [CT-RF146](Cenario_Teste/CT-RF146_Configuracoes_Biometria_Rejeitar_IP_Invalido.md) |
| [RF147](#rf147) | Persistir a alteração da porta do aparelho de Biometria | Média, proposta | [CT-RF147](Cenario_Teste/CT-RF147_Configuracoes_Biometria_Persistir_Porta.md) |
| [RF148](#rf148) | Validar dias negativos para travar a catraca | Baixa, proposta | [CT-RF148](Cenario_Teste/CT-RF148_Configuracoes_Biometria_Validar_Dias_Bloqueio.md) |
| [RF149](#rf149) | Bloquear cadastro de modelo de ficha sem nome | Média, proposta | [CT-RF149](Cenario_Teste/CT-RF149_Modelo_Ficha_Sem_Nome.md) |
| [RF150](#rf150) | Cancelar cadastro de modelo de ficha preenchido | Média, proposta | [CT-RF150](Cenario_Teste/CT-RF150_Cancelar_Cadastro_Modelo_Ficha.md) |
| [RF151](#rf151) | Buscar modelo de ficha por código inexistente | Média, proposta | [CT-RF151](Cenario_Teste/CT-RF151_Busca_Modelo_Ficha_Codigo_Inexistente.md) |
| [RF152](#rf152) | Buscar modelo de ficha por título inexistente | Média, proposta | [CT-RF152](Cenario_Teste/CT-RF152_Busca_Modelo_Ficha_Titulo_Inexistente.md) |
| [RF153](#rf153) | Buscar modelos de ficha com filtros combinados | Média, proposta | [CT-RF153](Cenario_Teste/CT-RF153_Busca_Modelo_Ficha_Filtros_Combinados.md) |
| [RF154](#rf154) | Limpar os filtros de Modelos de Ficha | Baixa, proposta | [CT-RF154](Cenario_Teste/CT-RF154_Limpeza_Filtros_Modelos_Ficha.md) |
| [RF155](#rf155) | Pesquisar novamente modelos de ficha sem filtros | Média, proposta | [CT-RF155](Cenario_Teste/CT-RF155_Nova_Busca_Modelos_Ficha_Sem_Filtros.md) |
| [RF156](#rf156) | Cadastrar um modelo de ficha com nome e personal | Alta, proposta | [CT-RF156](Cenario_Teste/CT-RF156_Cadastro_Modelo_Ficha_Erro_500.md) |
| [RF157](#rf157) | Consultar os detalhes de uma notificação | Média, proposta | [CT-RF157](Cenario_Teste/CT-RF157_Aplicativo_Consultar_Notificacao.md) |
| [RF158](#rf158) | Impedir o envio de uma notificação sem mensagem | Média, proposta | [CT-RF158](Cenario_Teste/CT-RF158_Aplicativo_Bloquear_Notificacao_Vazia.md) |
| [RF159](#rf159) | Criar uma notificação e conferir a prévia e a listagem | Média, proposta | [CT-RF159](Cenario_Teste/CT-RF159_Aplicativo_Criar_Notificacao_Preview.md) |
| [RF160](#rf160) | Alternar o filtro de postagens e abrir a lista completa | Média, proposta | [CT-RF160](Cenario_Teste/CT-RF160_Aplicativo_Postagens_Filtros_Estados_Vazios.md) |
| [RF161](#rf161) | Alternar o filtro de denúncias com a lista vazia | Média, proposta | [CT-RF161](Cenario_Teste/CT-RF161_Aplicativo_Denuncias_Filtros_Estados_Vazios.md) |

---


## RF01 — Autenticar usuário com credenciais válidas

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

### Critérios de aceitação do RF01

1. O formulário deve permitir preencher Login e Senha, com senha mascarada na interface.
2. Credenciais válidas devem permitir concluir a autenticação ao clicar em **Entrar**.
3. O navegador deve acessar `https://sifit.centrion.com.br/dashboard`.
4. O menu de navegação e o resumo da academia devem ser apresentados após a autenticação. HTTP 200 isoladamente não aprova o caso.

### Limites da validação do login

O caso cobre o fluxo positivo gravado. Credenciais inválidas, campos vazios, logout, expiração, persistência de **Manter conectado**, outras permissões e correspondência dos dados exibidos com o cadastro exigem validações próprias. A versão da aplicação não foi informada.

---


## RF02 — Recusar autenticação com senha incorreta

> **Nota histórica (marco de ampliação):** Os requisitos abaixo são referências de QA propostas a partir das evidências. Cálculo de encargos (RF14), escopo dos cartões (RF15), significado dos códigos de personais (RF07) e remoção lógica de modalidades (RF43) dependem da confirmação do produto; seus cenários estão a validar e não geraram defeitos confirmados. Os casos RF12 e RF13 compartilham o BUG-005.

<a id="rf02"></a>

| Campo | Descrição |
| --- | --- |
| Requisito de QA | Recusar a autenticação e informar a falha sem abrir a área autenticada. |
| Ator | Usuário sem sessão autenticada. |
| Pré-condições | Iniciar sem sessão autenticada na página de login. Dispor de conta de teste existente e senha propositalmente incorreta. |
| Gatilho | Preencher Login com a conta de teste existente. Informar uma senha incorreta, mantendo o valor mascarado. Clicar em Entrar e observar a mensagem, a URL e a ausência de acesso ao painel. |
| Caso | [CT-RF02](Cenario_Teste/CT-RF02_Login_SenhaIncorreta.md) |
| Situação observada | Aprovado conforme a gravação. Após o envio, a tela permanece no login e apresenta “O nome de usuário e senha não correspondem.” |
| Defeito | Nenhum no fluxo avaliado |
| Evidências | [Evidências](Evidencias/CT-RF05_Login_SenhaIncorreta/README.md) e [Jam](https://jam.dev/c/75f16436-7201-4de0-b191-1c4d0d63bfe8). |

### Critérios de aceitação do RF02

1. Senha incorreta não permite acesso ao dashboard.
2. A interface apresenta mensagem compreensível de credenciais inválidas.
3. A conclusão considera mensagem e permanência no login, além do status HTTP.

### Pontos a confirmar e limites do RF02

HTTP 200 é o status da resposta da API; a recusa é demonstrada pela interface. O vídeo não valida bloqueio por tentativas ou outras regras de segurança. Usar como regressão de autenticação negativa; preparar conta conhecida e repetir após alterações no login.

---

<a id="rf03"></a>


## RF03 — Recusar autenticação com usuário inexistente

| Campo | Descrição |
| --- | --- |
| Requisito de QA | Recusar o acesso para credenciais inválidas. |
| Ator | Usuário sem sessão autenticada. |
| Pré-condições | Iniciar sem sessão autenticada. Preparar um identificador cuja inexistência seja conhecida na base de teste. |
| Gatilho | Preencher Login com identificador inexistente na base de referência. Informar uma senha de teste, sem expor seu valor. Clicar em Entrar e verificar que não há acesso à área autenticada. |
| Caso | [CT-RF03](Cenario_Teste/CT-RF03_Login_UsuarioInexistente.md) |
| Situação observada | Aprovado conforme a gravação. A gravação termina na página de login com a mensagem genérica de credenciais inválidas, sem acesso ao painel. |
| Defeito | Nenhum no fluxo avaliado |
| Evidências | [Evidências](Evidencias/CT-RF06_Login_UsuarioInexistente/README.md) e [Jam](https://jam.dev/c/b184e875-2cb1-4a01-b4dd-bc85b3741ff6). |

### Critérios de aceitação do RF03

1. Identificador inexistente não permite abrir a área autenticada.
2. A tentativa recebe retorno compreensível sem revelar se a conta existe.
3. Em nova execução, a inexistência do identificador é conferida na base de referência.

### Pontos a confirmar e limites do RF03

A inexistência do usuário é o cenário declarado no título; não foi conferida no banco. A mensagem já está visível no início do vídeo e permanece após a nova tentativa. Repetir com identificador de inexistência comprovada; a classificação atual refere-se à recusa visível do cenário declarado pelo autor.

---

<a id="rf11"></a>


## RF04 — Iniciar recuperação de senha

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


## RF05 — Exibir perfil do usuário autenticado

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

### Critérios de aceitação do RF05

1. Os valores apresentados devem corresponder à conta autenticada; textos e imagens de demonstração não devem substituir o cadastro.
2. As seções Usuário, Documentos e Endereço devem apresentar todos os campos previstos, seus rótulos e os valores cadastrados, quando existentes.
3. Campos editáveis devem permitir interação de acordo com as permissões da conta.
4. A interface deve usar português e o padrão visual do sistema.
5. Imagens e demais elementos devem respeitar seus contêineres, sem desalinhamento ou rolagem horizontal indevida nas resoluções definidas para o reteste.

### Pontos a definir para o perfil

Confirmar campos obrigatórios e opcionais, permissões de edição, resoluções suportadas, comportamento para dados ausentes e regras de validação e salvamento. A evidência atual avalia o carregamento e a apresentação; não comprova persistência de alterações nem contém os dados reais da conta para comparação individual.

---


## RF06 — Validar a ordem das datas do período

| Campo | Descrição |
| --- | --- |
| Requisito de QA | Validar a ordem das datas, orientar o usuário e aplicar um período válido com retorno perceptível. |
| Ator | Usuário autenticado com permissão no módulo. |
| Pré-condições | Sessão autenticada com acesso ao seletor de período da página inicial. Registrar as regras de aplicação do filtro e preparar um intervalo válido de controle. |
| Gatilho | Alterar a data final para 10/11/2026 na base de referência da gravação. Alterar a inicial para 19/11/2026, posterior à data final. Verificar a validação e tentar aplicar; depois selecionar um período válido e conferir os dados de referência. |
| Caso | [CT-RF06](Cenario_Teste/CT-RF06_Periodo_Dashboard.md) |
| Situação observada | Reprovado nas evidências. O seletor chega a exibir 19/11/2026–10/11/2026, com início posterior ao fim, sem uma validação visível. Os indicadores permanecem com os mesmos valores nos quadros conferidos. |
| Defeito | [BUG-006](Relatorio-de-Bugs.md#bug-006) |
| Evidências | [Evidências](Evidencias/CT-RF12_Periodo_Dashboard/README.md) e [Jam](https://jam.dev/c/93165ba3-3bfe-4dd5-9379-ab8db2d686ba). |

### Critérios de aceitação do RF06

1. Data inicial posterior à final recebe validação clara.
2. Somente intervalos válidos são aplicados.
3. O efeito de um período válido é conferido com dados conhecidos; valores constantes não provam erro de cálculo.

### Pontos a confirmar e limites do RF06

A captura comprova o intervalo invertido. Indicadores constantes, isoladamente, não demonstram falha no cálculo; os botões de seta geraram requisições, portanto não se pode dizer que todos estavam sem função. Corrigir e retestar a validação do intervalo; avaliar a atualização dos indicadores em base controlada como verificação complementar.

---

<a id="rf07"></a>


## RF07 — Identificar personais sem confundir códigos com contagem

| Campo | Descrição |
| --- | --- |
| Requisito de QA | Se a coluna for um identificador de cadastro, lacunas são aceitáveis. Se deveria numerar linhas, a regra precisa ser esclarecida. |
| Ator | Usuário autenticado com permissão no módulo. |
| Pré-condições | Sessão autenticada e acesso à listagem Personais. Confirmar se Código representa ID de cadastro ou posição na listagem. |
| Gatilho | Abrir Personais pelo indicador da página inicial. Contar as linhas e comparar com o total informado. Conferir o significado e a unicidade dos códigos com o cadastro de referência. |
| Caso | [CT-RF07](Cenario_Teste/CT-RF07_Codigos_Personais.md) |
| Situação observada | A validar — regra ou contexto pendente. A lista contém quatro personais e o total informado é quatro. A coluna Código apresenta identificadores não sequenciais, como #1, #2, #4 e #11. |
| Defeito | Sem defeito confirmado |
| Evidências | [Evidências](Evidencias/CT-RF13_Codigos_Personais/README.md) e [Jam](https://jam.dev/c/69330ca9-ef19-4ece-918f-31a460628016). |

### Critérios de aceitação do RF07

1. Total confere com o número de registros considerando a paginação.
2. Identificadores são interpretados conforme sua regra, sem exigir sequência de IDs por suposição.
3. Se a intenção for numerar posições, o rótulo e a numeração deixam isso claro.

### Pontos a confirmar e limites do RF07

Não foi demonstrada uma divergência entre o total e a quantidade listada. A numeração não sequencial por si só não confirma defeito. Confirmar a semântica da coluna Código; quatro linhas e total quatro não sustentam um defeito de quantidade.

---

<a id="rf41"></a>


## RF08 — Carregar o dashboard sem falhas de servidor ou requisições redundantes

| Campo | Descrição |
| --- | --- |
| Requisito de QA | O dashboard deve solicitar somente os dados necessários, receber respostas tratáveis e carregar seus componentes sem erro HTTP 500. Uma falha parcial deve identificar o componente afetado sem inutilizar todo o painel. |
| Ator | Usuário autenticado com acesso ao dashboard. |
| Pré-condições | Sessão válida, conta de teste com dados conhecidos e captura de rede ativa. |
| Gatilho | Acessar ou recarregar controladamente o dashboard. |
| Caso | [CT-RF08](Cenario_Teste/CT-RF08_Erro_Servidor_Excesso_Requisicoes.md) |
| Situação observada | Reprovado nas evidências. O dashboard apresenta um diálogo de erro; a listagem visível contém 23 eventos, com verificação de token HTTP 200, diversas chamadas GET/POST HTTP 500 e OPTIONS HTTP 204. |
| Defeito | [BUG-018](Relatorio-de-Bugs.md#bug-018), em triagem |
| Evidências | [Jam](https://jam.dev/c/eea58e17-b62f-432b-97b2-b14c14bed555) e [Evidências](Evidencias/CT-RF34_Erro_Servidor_Excesso_Requisicoes/README.md). |

### Critérios de aceitação do RF08

1. Cada componente executa apenas as chamadas previstas pelo contrato.
2. Nenhuma requisição necessária ao dashboard retorna HTTP 500.
3. Falhas parciais são identificadas e não inutilizam componentes independentes.
4. A quantidade e a sequência das chamadas permanecem estáveis após recarga controlada.
5. Logs e identificadores permitem correlacionar qualquer resposta não bem-sucedida.

### Pontos a confirmar e limites do RF08

Os caminhos completos, parâmetros, corpos, logs e componentes de origem não foram confirmados. O título do Jam atribui o problema ao excesso de requisições, mas a relação causal não foi demonstrada. Correlacionar cada HTTP 500 ao endpoint e ao componente antes de concluir se há repetição indevida, retentativa descontrolada ou indisponibilidade simultânea do backend.

---

<a id="rf33"></a>


## RF09 — Pesquisar clientes com filtros combinados

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

### Critérios de aceitação do RF09

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


## RF10 — Cadastrar avaliação ou informar validação específica

| Campo | Descrição |
| --- | --- |
| Requisito de QA | Cadastrar uma avaliação com dados válidos e apresentar confirmação; tratar dados recusados sem erro interno genérico. |
| Ator / pré-condições | Usuário autenticado com permissão; aluno existente, personal habilitado e data/hora permitidas no fluxo válido. |
| Gatilho | Clicar em Salvar no formulário Cadastrar Avaliação. |
| Caso | [CT-RF10](Cenario_Teste/CT-RF10_Cadastro_Avaliacao.md) |
| Situação observada | Reprovado: POST /api/avaliacao/adicionar-agendamento/1 retorna HTTP 500 e a interface mostra “Erro ao cadastrar Avaliação.”. |
| Defeito | [BUG-010](Relatorio-de-Bugs.md#bug-010), aberto; reteste pendente. |
| Evidências | [Evidências](Evidencias/CT-RF21_Cadastro_Avaliacao/README.md) e [Jam](https://jam.dev/c/2e5eca1f-7cd2-4ee3-854b-02ef4635955a). |

### Critérios de aceitação do RF10

1. Dados válidos geram cadastro confirmado e avaliação consultável na listagem.
2. Aluno inválido, vínculo incompleto ou data/hora proibida recebem validação específica, sem HTTP 500.
3. Tentativas rejeitadas não deixam registros parciais; uma tentativa válida cria um agendamento.
4. A interface permite corrigir os dados após uma rejeição.

### Pontos a confirmar e limites do RF10

O aluno 3423 foi digitado manualmente sem confirmação pela busca. A avaliação foi solicitada para 15/11/2026 às 06:00, antes da tentativa de aproximadamente 15:08. Confirmar existência/elegibilidade do aluno, vínculos, contrato da data e regra de agendamento retroativo. Esses pontos não comprovam a causa do HTTP 500. A referência de QA foi elaborada a partir da evidência e depende de confirmação de produto; não foi fornecida especificação formal. Causa raiz e persistência não confirmadas; sem nova execução.

---

<a id="rf21"></a>


## RF11 — Oferecer retorno ao solicitar exportação financeira

| Campo | Descrição |
| --- | --- |
| Requisito de QA | Iniciar a exportação e apresentar um retorno claro ao usuário. |
| Ator | Usuário autenticado com permissão no módulo. |
| Pré-condições | Sessão autenticada com permissão para consultar e exportar o financeiro. Modal Financeiro em Aberto aberto e registros disponíveis. |
| Gatilho | Abrir Financeiro em Aberto a partir da página inicial. Clicar uma vez em Exportar e aguardar a conclusão. Verificar retorno visual e o arquivo no histórico de downloads; repetir somente para conferir comportamento. |
| Caso | [CT-RF11](Cenario_Teste/CT-RF11_Exportacao_Financeiro.md) |
| Situação observada | Reprovado nas evidências. Vários cliques em Exportar não produzem mudança ou confirmação visível durante a gravação. |
| Defeito | [BUG-004](Relatorio-de-Bugs.md#bug-004) |
| Evidências | [Evidências](Evidencias/CT-RF07_Exportacao_Financeiro/README.md) e [Jam](https://jam.dev/c/1084cb18-cb3d-4b85-9c2f-ee431b59a06b). |

### Critérios de aceitação do RF11

1. O clique oferece retorno perceptível de processamento, conclusão ou falha.
2. O arquivo disponibilizado corresponde ao escopo de exportação definido pelo produto.
3. A validação do download inclui o histórico e a abertura do arquivo, ainda pendentes na evidência atual.

### Pontos a confirmar e limites do RF11

O vídeo não mostra o diretório de downloads; portanto, não comprova sozinho que nenhum arquivo foi gerado. A ausência de requisição também não exclui uma exportação feita no próprio navegador. Investigar o retorno do botão; no reteste capturar o histórico de downloads e abrir o arquivo antes de concluir se a exportação foi gerada.

---

<a id="rf14"></a>


## RF12 — Manter contagem e paginação coerentes com as mensalidades

| Campo | Descrição |
| --- | --- |
| Requisito de QA | Manter a contagem, a listagem e a paginação coerentes e permitir consultar todos os registros contabilizados. |
| Ator | Usuário autenticado com permissão no módulo. |
| Pré-condições | Sessão autenticada com acesso ao financeiro. Base de referência com mensalidades conhecidas e distribuídas entre as faixas de vencimento. |
| Gatilho | Abrir Financeiro em Aberto e selecionar Todos. Comparar o contador com as linhas e o total do rodapé; percorrer páginas quando disponíveis. Selecionar +30 dias e repetir a conferência da quantidade e dos registros acessíveis. |
| Caso | [CT-RF12](Cenario_Teste/CT-RF12_Contagem_Mensalidades.md) |
| Situação observada | Reprovado nas evidências. Todos informa três mensalidades, mas aparece uma linha. No filtro +30 dias, o contador indica dois registros e apenas uma linha permanece disponível. |
| Defeito | [BUG-005](Relatorio-de-Bugs.md#bug-005) |
| Evidências | [Evidências](Evidencias/CT-RF09_Contagem_Mensalidades/README.md) e [Jam](https://jam.dev/c/1874d0b3-5c7c-4f28-85be-91750e20cbe1). |

### Critérios de aceitação do RF12

1. Contador, total do rodapé e conjunto listado são consistentes.
2. Todos os registros contados podem ser consultados, considerando a paginação.
3. A troca de filtro recalcula a contagem e os registros com os mesmos critérios.

### Pontos a confirmar e limites do RF12

Não foram inspecionados os corpos das respostas ou o banco. Os casos CT-RF12, CT-RF13 e CT-RF15 tratam de aspectos relacionados do mesmo modal. Retestar com o CT-RF13; os dois cenários documentam manifestações do BUG-005, sem criar um defeito duplicado.

---

<a id="rf13"></a>


## RF13 — Aplicar o filtro Até 7 dias com contagem consistente

| Campo | Descrição |
| --- | --- |
| Requisito de QA | O contador do filtro e os registros exibidos devem representar o mesmo conjunto. |
| Ator | Usuário autenticado com permissão no módulo. |
| Pré-condições | Sessão autenticada e modal Financeiro em Aberto disponível. Mensalidade conhecida que pertença à faixa Até 7 dias conforme a regra do produto. |
| Gatilho | Selecionar Até 7 dias no modal financeiro. Aguardar o carregamento e comparar contador, linhas e estado vazio. Conferir que os registros esperados estão acessíveis e que a mensagem vazia só aparece para conjunto vazio. |
| Caso | [CT-RF13](Cenario_Teste/CT-RF13_Filtro_Mensalidades.md) |
| Situação observada | Reprovado nas evidências. O filtro mantém o contador 1, enquanto a lista informa “Nenhuma mensalidade encontrada para o filtro atual”. |
| Defeito | [BUG-005](Relatorio-de-Bugs.md#bug-005) |
| Evidências | [Evidências](Evidencias/CT-RF10_Filtro_Mensalidades/README.md) e [Jam](https://jam.dev/c/3f78cf16-2c3b-48bc-8622-23b829debbec). |

### Critérios de aceitação do RF13

1. Contador e lista usam o mesmo critério de período.
2. Uma mensalidade contabilizada no filtro pode ser consultada.
3. Conjunto vazio apresenta mensagem e contagem coerentes.

### Pontos a confirmar e limites do RF13

A evidência confirma a divergência visual. A causa técnica não foi investigada. Relacionado ao CT-RF12. Retestar em conjunto com CT-RF12 e conferir o contrato da faixa Até 7 dias antes de preparar a base.

---

<a id="rf15"></a>


## RF14 — Apresentar a composição e o valor comunicado na cobrança

| Campo | Descrição |
| --- | --- |
| Requisito de QA | Exibir a composição do total, incluindo eventuais juros, e deixar claro qual valor será comunicado. |
| Ator | Usuário autenticado com permissão no módulo. |
| Pré-condições | Sessão autenticada e mensalidade de teste com valor, vencimento e encargos conhecidos. Confirmar com o produto multa, juros, arredondamento e valor que deve constar na mensagem. |
| Gatilho | Abrir Cobrar via WhatsApp para uma mensalidade de referência. Comparar valor original, multa, total atualizado e texto inicial da mensagem. Calcular o total conforme a regra confirmada e registrar a composição, sem enviar mensagem. |
| Caso | [CT-RF14](Cenario_Teste/CT-RF14_Calculo_Cobranca.md) |
| Situação observada | A validar — regra ou contexto pendente. O modal mostra valor original de R$ 350,00, multa de R$ 7,00 e total atualizado de R$ 377,83. A mensagem inicial cita R$ 350,00; o autor escreve que o valor deveria ser R$ 357,00. |
| Defeito | Sem defeito confirmado |
| Evidências | [Evidências](Evidencias/CT-RF08_Calculo_Cobranca/README.md) e [Jam](https://jam.dev/c/79b712ae-d9e0-4600-862f-fd3a278285ff). |

### Critérios de aceitação do RF14

1. Valor original, multa e eventuais juros são identificáveis.
2. Total confere com a fórmula e o arredondamento definidos.
3. O valor na mensagem segue uma regra explícita.

### Pontos a confirmar e limites do RF14

R$ 350,00 + R$ 7,00 = R$ 357,00, mas os R$ 20,83 restantes podem corresponder a juros. A regra de cálculo e as configurações não foram fornecidas; não é possível afirmar que o total está incorreto. Confirmar a origem dos R$ 20,83 além de principal e multa e a regra da mensagem; não registrar cálculo incorreto antes dessa validação.

---

<a id="rf12"></a>


## RF15 — Explicitar o escopo dos indicadores financeiros

| Campo | Descrição |
| --- | --- |
| Requisito de QA | Indicar claramente quais métricas seguem o filtro e quais representam o total geral ou o mês. |
| Ator | Usuário autenticado com permissão no módulo. |
| Pré-condições | Sessão autenticada e base com valores conhecidos por faixa e mês. Definir quais cartões são globais, mensais ou dependentes do filtro selecionado. |
| Gatilho | Abrir Financeiro em Aberto e registrar os cartões e a lista em Todos. Alternar Até 7 dias e +30 dias. Comparar cada cartão com seu escopo definido e verificar se a interface identifica esse escopo. |
| Caso | [CT-RF15](Cenario_Teste/CT-RF15_Metricas_Financeiro.md) |
| Situação observada | A validar — regra ou contexto pendente. A lista alterna entre uma linha e estado vazio. O cartão de atraso muda de dois para zero alunos; outros totais, como Total em aberto de R$ 470,00 e Recuperado no mês de R$ 45,00, permanecem. |
| Defeito | Sem defeito confirmado |
| Evidências | [Evidências](Evidencias/CT-RF11_Metricas_Financeiro/README.md) e [Jam](https://jam.dev/c/4491c9e7-7e00-4063-91ce-8683e316df06). |

### Critérios de aceitação do RF15

1. Cada indicador possui escopo e período identificados.
2. Indicadores filtrados acompanham a seleção.
3. Indicadores globais ou mensais podem permanecer constantes quando isso corresponde à regra definida.

### Pontos a confirmar e limites do RF15

Totais globais podem permanecer constantes por definição. Sem a regra de cada indicador, não é possível classificar toda permanência de valor como erro. A divergência de contagens está documentada nos itens 05 e 06. Confirmar os contratos dos cartões; a constância de totais globais não é suficiente para abrir outro defeito financeiro.

---

<a id="rf06"></a>


## RF16 — Filtrar contas a pagar por nome, data e status

| Campo | Descrição |
| --- | --- |
| Requisito de QA | A listagem de Contas a Pagar deve apresentar apenas as contas que atendam aos critérios de código, nome, tipo de data, período e status informados, com cartões coerentes e mensagem explícita de resultado vazio. |
| Ator | Usuário autenticado com acesso ao módulo. |
| Pré-condições | Base de contas conhecida, com nomes, datas e status registrados. |
| Gatilho | Informar critérios e acionar Buscar. |
| Caso | [CT-RF16](Cenario_Teste/CT-RF16_Filtros_Contas_Pagar.md) |
| Situação observada | A validar — regra ou contexto pendente. A combinação Nome "teste", Pagamento, 06/11/2026 e Pago deixa a listagem vazia, compatível com os critérios, sem dado de controle. |
| Defeito | Sem defeito confirmado |
| Evidências | [Jam](https://jam.dev/c/5d0afaf4-5abd-4e85-923f-27448304a9ef) e [Evidências](Evidencias/CT-RF91_Filtros_Contas_Pagar/README.md). |

### Critérios de aceitação do RF16

1. Cada critério isolado (nome, tipo de data, período e status) filtra corretamente a listagem.
2. A combinação de critérios aplica todos eles simultaneamente.
3. Os cartões acompanham o conjunto exibido conforme o contrato definido.
4. O resultado vazio apresenta mensagem explícita.
5. Limpar os critérios restaura a listagem do período.

### Pontos a confirmar e limites do RF16

Cada critério isolado, a troca de Tipo de Data e o resultado vazio contra a base não foram verificados; o corpo da busca principal não foi capturado.

---

<a id="rf17"></a>


## RF17 — Exigir o colaborador no cadastro de conta a pagar a colaborador

| Campo | Descrição |
| --- | --- |
| Requisito de QA | O formulário Cadastrar Conta a Pagar deve exigir o colaborador favorecido quando o tipo for Pagto. Colaborador, com mensagem clara e rejeição também no servidor. |
| Ator | Usuário autenticado com acesso ao módulo. |
| Pré-condições | Formulário aberto com o tipo Pagto. Colaborador; regra de obrigatoriedade definida com o produto. |
| Gatilho | Preencher o formulário sem colaborador e acionar Salvar. |
| Caso | [CT-RF17](Cenario_Teste/CT-RF17_Cadastro_Conta_Colaborador_Sem_Colaborador.md) |
| Situação observada | Reprovado nas evidências. A conta é gravada (HTTP 201) com colaborador vazio e listada com "-" no colaborador, sem mensagem de validação. |
| Defeito | [BUG-039](Relatorio-de-Bugs.md#bug-039), em triagem |
| Evidências | [Jam](https://jam.dev/c/5d0afaf4-5abd-4e85-923f-27448304a9ef) e [Evidências](Evidencias/CT-RF92_Cadastro_Conta_Colaborador_Sem_Colaborador/README.md). |

### Critérios de aceitação do RF17

1. Conta do tipo Pagto. Colaborador exige o colaborador antes da gravação.
2. A ausência do colaborador gera mensagem de validação junto ao campo.
3. O servidor rejeita a criação sem colaborador, independentemente da interface.
4. A listagem apresenta o colaborador na coluna Fornecedor / Colaborador.
5. Conta com colaborador informado é gravada e listada corretamente.

### Pontos a confirmar e limites do RF17

A regra de obrigatoriedade e a validação no servidor não foram verificadas; o tipo fornecedor sem fornecedor não foi exercitado.

---

<a id="rf18"></a>


## RF18 — Buscar e selecionar colaborador no cadastro de conta

| Campo | Descrição |
| --- | --- |
| Requisito de QA | O modal Buscar Colaborador deve listar os colaboradores correspondentes ao nome informado, permitir a seleção e informar explicitamente quando não houver resultado. |
| Ator | Usuário autenticado com acesso ao módulo. |
| Pré-condições | Colaboradores cadastrados; modal aberto a partir do tipo Pagto. Colaborador. |
| Gatilho | Informar um nome no modal e acionar Pesquisar. |
| Caso | [CT-RF18](Cenario_Teste/CT-RF18_Busca_Colaborador_Conta_Pagar.md) |
| Situação observada | A validar — regra ou contexto pendente. O termo "sds" devolve lista vazia, sem mensagem visível; a busca com resultado e a seleção não foram exercitadas. |
| Defeito | Sem defeito confirmado |
| Evidências | [Jam](https://jam.dev/c/5d0afaf4-5abd-4e85-923f-27448304a9ef) e [Evidências](Evidencias/CT-RF93_Busca_Colaborador_Conta_Pagar/README.md). |

### Critérios de aceitação do RF18

1. A busca lista os colaboradores cujo nome contenha o termo.
2. A seleção preenche Código e Colaborador no formulário.
3. Sem correspondência, o modal apresenta mensagem explícita.
4. O modal pode ser fechado sem alterar o formulário.
5. O colaborador selecionado é gravado na conta.

### Pontos a confirmar e limites do RF18

A busca com resultado, a seleção e a mensagem de resultado vazio esperada não foram verificadas.

---

<a id="rf19"></a>


## RF19 — Visualizar os dados de uma conta a pagar

| Campo | Descrição |
| --- | --- |
| Requisito de QA | A lupa da listagem deve abrir os dados da conta selecionada, com informações gerais, dados da conta, do colaborador ou fornecedor e do documento, em rótulos legíveis. |
| Ator | Usuário autenticado com acesso ao módulo. |
| Pré-condições | Conta a pagar cadastrada e visível na listagem. |
| Gatilho | Acionar a lupa da linha da conta. |
| Caso | [CT-RF19](Cenario_Teste/CT-RF19_Visualizacao_Conta_Pagar.md) |
| Situação observada | Aprovado conforme a gravação. O modal apresenta os dados da conta 29 e fecha corretamente; o tipo aparece como "PAG_COLABORADOR". |
| Defeito | Nenhum no fluxo avaliado |
| Evidências | [Jam](https://jam.dev/c/5d0afaf4-5abd-4e85-923f-27448304a9ef) e [Evidências](Evidencias/CT-RF94_Visualizacao_Conta_Pagar/README.md). |

### Critérios de aceitação do RF19

1. O modal apresenta os dados da conta selecionada conforme gravados.
2. Os rótulos exibidos ao usuário são legíveis (sem códigos internos).
3. As seções do colaborador ou do fornecedor apresentam o favorecido quando informado.
4. O botão Fechar retorna à listagem sem alterações.
5. A consulta não altera a conta.

### Pontos a confirmar e limites do RF19

Contas de fornecedor, pagas e atrasadas e o rótulo esperado do tipo não foram exercitados.

---

<a id="rf20"></a>


## RF20 — Excluir uma conta a pagar com confirmação

| Campo | Descrição |
| --- | --- |
| Requisito de QA | A lixeira da listagem deve exigir confirmação e, confirmada, remover a conta sem erro, atualizando a listagem e os cartões. |
| Ator | Usuário autenticado com acesso ao módulo. |
| Pré-condições | Conta a pagar descartável cadastrada. |
| Gatilho | Acionar a lixeira da conta e confirmar o diálogo. |
| Caso | [CT-RF20](Cenario_Teste/CT-RF20_Exclusao_Conta_Pagar.md) |
| Situação observada | Aprovado conforme a gravação. O diálogo pede confirmação e `deletar-conta-pagar` retorna HTTP 200 sem erro; a conta 29 deixa a listagem. |
| Defeito | Nenhum no fluxo avaliado |
| Evidências | [Jam](https://jam.dev/c/5d0afaf4-5abd-4e85-923f-27448304a9ef) e [Evidências](Evidencias/CT-RF95_Exclusao_Conta_Pagar/README.md). |

### Critérios de aceitação do RF20

1. A exclusão exige confirmação do usuário.
2. Cancelar preserva a conta.
3. Confirmar remove a conta sem erro e atualiza a listagem e os cartões.
4. A conta excluída não reaparece após recarga.
5. Contas vinculadas a pagamentos ou ao caixa têm tratamento explícito.

### Pontos a confirmar e limites do RF20

Cancelar, recarga após a exclusão e contas pagas ou vinculadas não foram exercitados.

---

<a id="rf82"></a>


## RF21 — Permitir informar o código do exercício conforme a regra

| Campo | Descrição |
| --- | --- |
| Requisito de QA | Quando editável, o campo Código deve aceitar e manter um código válido e permitir sua correção. |
| Ator | Usuário autenticado com permissão em Exercícios. |
| Pré-condições | Confirmar se o código é manual ou automático e quais operações permitem edição. Preparar dados de teste autorizados. |
| Gatilho | Abrir o formulário Exercício com permissão adequada. |
| Caso | [CT-RF21](Cenario_Teste/CT-RF21_Digitacao_Codigo_Exercicio.md) |
| Situação observada | Reprovado conforme o relato; reprodução independente pendente. O testador relata não conseguir digitar o código. A imagem inicial confirma o campo Código no formulário Exercício; a reprodução integral, as teclas e o foco não foram confirmados. |
| Defeito | [BUG-011](Relatorio-de-Bugs.md#bug-011), em triagem |
| Evidências | [Jam](https://jam.dev/c/2696db03-0a18-4c39-a75d-4987a43c04f0) e relato do testador. |

### Critérios de aceitação do RF21

1. A regra de preenchimento manual ou geração automática está confirmada.
2. Quando editável, o campo recebe foco, aceita e mantém um código válido.
3. O usuário pode apagar e corrigir o valor; restrições são explicadas.

### Pontos a confirmar e limites do RF21

Não foram confirmadas a operação de criação/edição, a sequência de teclas ou a causa. A classificação se apoia no relato e na imagem inicial, sem análise de rede ou console. Confirmar a regra, reproduzir o impedimento e retestar o campo após correção. Os critérios são referências de QA, sem aprovação formal de produto ou nova execução.

---

<a id="rf22"></a>


## RF22 — Exclusão de exercício

| Campo | Descrição |
| --- | --- |
| Requisito de QA | O sistema deve remover o exercício permitido da biblioteca e atualizar os totais. Se houver impedimento, deve explicá-lo sem indicar sucesso indevido. |
| Ator | Usuário autenticado com permissão em Exercícios. |
| Pré-condições | Exercício de teste existente, sem impedimento conhecido para exclusão. Preparar dados de teste autorizados. |
| Gatilho | Identificar o exercício de teste e registrar o total da biblioteca e do grupo. |
| Caso | [CT-RF22](Cenario_Teste/CT-RF22_Exclusao_Exercicio.md) |
| Situação observada | Aprovado no trecho consultado. No quadro de aproximadamente 0:02, a biblioteca apresenta total 11 e o exercício Levantamento de Peso. No quadro final, em aproximadamente 0:06, esse registro não aparece e o total é 10. A lista continua contendo Levantamento de Peso 02, registro distinto. |
| Defeito | Sem defeito confirmado |
| Evidências | [Jam](https://jam.dev/c/32adfca3-489f-4a4b-a08d-933c1d1a3c32) e [Evidências](Evidencias/CT-RF23_Exclusao_Exercicio/README.md). |

### Critérios de aceitação do RF22

1. O registro selecionado deixa de aparecer na biblioteca.
2. O total diminui em uma unidade e os demais exercícios são preservados.
3. Uma restrição de exclusão, quando aplicável, é apresentada claramente.

### Pontos a confirmar e limites do RF22

Não foram confirmados o diálogo de confirmação, a persistência após recarregar ou os efeitos sobre fichas de treino vinculadas. Manter como regressão. Em nova execução, recarregar a página para conferir persistência e testar separadamente as regras para exercícios vinculados. Os critérios são referências de QA, sem aprovação formal de produto ou nova execução.

---

<a id="rf23"></a>


## RF23 — Edição de exercício aumenta o total e mantém duas entradas

| Campo | Descrição |
| --- | --- |
| Requisito de QA | Salvar a edição deve atualizar o mesmo exercício, sem criar um registro adicional e sem aumentar o total da biblioteca. |
| Ator | Usuário autenticado com permissão em Exercícios. |
| Pré-condições | Exercício de teste existente, com identificador e nome original registrados antes da edição. Preparar dados de teste autorizados. |
| Gatilho | Registrar identificador, nome e total do exercício de teste. |
| Caso | [CT-RF23](Cenario_Teste/CT-RF23_Edicao_Exercicio.md) |
| Situação observada | Reprovado no trecho consultado; confirmar operação e identidade dos registros na reprodução. O Jam está identificado como teste de edição. Nos quadros intermediários, o formulário Exercício está aberto com código 16, o nome é preenchido e a biblioteca ao fundo indica total 10. No quadro final, o formulário fecha, o total é 11 e a lista contém Levantamento de Peso e Levantamento de Peso 02. O aumento e a coexistência dos nomes divergem do resultado esperado para uma edição. |
| Defeito | [BUG-012](Relatorio-de-Bugs.md#bug-012), em triagem |
| Evidências | [Jam](https://jam.dev/c/073f70d6-4052-4e0f-a4bb-e9f37305d618) e [Evidências](Evidencias/CT-RF24_Edicao_Exercicio/README.md). |

### Critérios de aceitação do RF23

1. A ação de edição abre o exercício correto com seus dados atuais.
2. Salvar altera o nome do mesmo identificador.
3. O total permanece igual e não surge um registro adicional.
4. Os dados não alterados permanecem associados ao exercício.

### Pontos a confirmar e limites do RF23

O acionamento inicial da edição e os identificadores das duas entradas não foram confirmados. A classificação considera o propósito declarado do Jam e a divergência visual; se a operação tiver sido criação, reavaliar a conclusão. Reproduzir a partir da ação explícita de edição e comparar os identificadores antes e depois. Investigar eventual envio para criação como hipótese, sem atribuir causa técnica antes de verificar código e contrato da API. Os critérios são referências de QA, sem aprovação formal de produto ou nova execução.

---

<a id="rf24"></a>


## RF24 — Envio de exercício com imagem

| Campo | Descrição |
| --- | --- |
| Requisito de QA | O sistema deve cadastrar o exercício, atualizar a biblioteca e manter a imagem vinculada ao registro, disponível após reabrir o cadastro. |
| Ator | Usuário autenticado com permissão em Exercícios. |
| Pré-condições | Imagem de teste disponível, em formato e tamanho aceitos pela interface, sem dados pessoais. Preparar dados de teste autorizados. |
| Gatilho | Registrar o total inicial da biblioteca e abrir o formulário de novo exercício. |
| Caso | [CT-RF24](Cenario_Teste/CT-RF24_Envio_Exercicio_Imagem.md) |
| Situação observada | A validar — criação visível; persistência e associação da imagem não confirmadas. O quadro inicial consultado mostra o formulário Exercício preenchido com nome braço forte e uma miniatura na seção Imagem; a biblioteca ao fundo indica total 9. O quadro final mostra o formulário fechado, braço forte na lista e total 10. Esses quadros sustentam a criação com imagem selecionada, mas não demonstram a reabertura ou a visualização da imagem salva. |
| Defeito | Sem defeito confirmado |
| Evidências | [Jam](https://jam.dev/c/25c37a9b-e9bd-4e0c-adf1-4da528ae1d58) e [Evidências](Evidencias/CT-RF25_Envio_Exercicio_Imagem/README.md). |

### Critérios de aceitação do RF24

1. Uma imagem válida pode ser selecionada e sua prévia aparece.
2. Salvar cria um único exercício e atualiza o total.
3. Reabrir o cadastro exibe a imagem correspondente ao arquivo enviado.
4. A associação permanece após recarregar a página.

### Pontos a confirmar e limites do RF24

Não foram confirmados nome, formato, tamanho ou conteúdo integral do arquivo, nem a persistência da imagem, sua recuperação ou a ausência de duplicação após nova submissão. Reabrir o exercício criado e conferir a imagem salva. Testar formatos e tamanhos inválidos em casos separados; essas variações não recebem resultado nesta análise. Os critérios são referências de QA, sem aprovação formal de produto ou nova execução.

---

<a id="rf25"></a>


## RF25 — Validar campos obrigatórios do exercício

| Campo | Descrição |
| --- | --- |
| Requisito de QA | O sistema deve impedir o cadastro de exercício com campos obrigatórios vazios e indicar claramente quais dados precisam ser preenchidos. |
| Ator | Usuário autenticado com permissão em Exercícios. |
| Pré-condições | Formulário de novo exercício aberto, sem preenchimento dos campos obrigatórios. |
| Gatilho | Clicar em Salvar com os campos obrigatórios vazios. |
| Caso | [CT-RF25](Cenario_Teste/CT-RF25_Exercicio_Campos_Vazios.md) |
| Situação observada | Reprovado conforme a gravação. O formulário permanece aberto sem mensagem, destaque ou orientação de validação visível. A evidência não demonstra criação de registro vazio. |
| Defeito | [BUG-013](Relatorio-de-Bugs.md#bug-013), em triagem |
| Evidências | [Jam](https://jam.dev/c/bc07ca5f-d3a9-45f6-84cb-12c0b562a211). |

### Critérios de aceitação do RF25

1. O envio com campos obrigatórios vazios é bloqueado.
2. Cada campo inválido recebe indicação visual e textual compreensível.
3. O foco é direcionado ao primeiro campo que exige correção.
4. Nenhum registro vazio é criado, inclusive após recarregar a página.

### Pontos a confirmar e limites do RF25

A gravação não confirma resposta da API, persistência ou comportamento após recarregar a biblioteca. Reproduzir com total inicial conhecido, registrar as mensagens e confirmar que nenhum exercício vazio foi criado. A causa técnica não foi determinada.

---

<a id="rf26"></a>


## RF26 — Rejeitar vídeo no campo de imagem com feedback

| Campo | Descrição |
| --- | --- |
| Requisito de QA | O campo Imagem deve rejeitar arquivos de vídeo e informar os formatos e limites aceitos, sem descartar os demais dados do formulário. |
| Ator | Usuário autenticado com permissão em Exercícios. |
| Pré-condições | Formulário aberto e arquivo de vídeo de teste disponível, com extensão, MIME e tamanho conhecidos. |
| Gatilho | Selecionar o vídeo no campo Imagem. |
| Caso | [CT-RF26](Cenario_Teste/CT-RF26_Video_Campo_Imagem.md) |
| Situação observada | Reprovado conforme a gravação. O arquivo não aparece anexado, porém não há mensagem visível explicando a rejeição ou os formatos permitidos. |
| Defeito | [BUG-014](Relatorio-de-Bugs.md#bug-014), em triagem |
| Evidências | [Jam](https://jam.dev/c/00740108-9a7d-4151-8723-171c89635567). |

### Critérios de aceitação do RF26

1. Arquivos de vídeo não são aceitos como imagem.
2. A mensagem identifica o tipo incompatível e informa formatos e tamanho máximo aceitos.
3. O formulário conserva os demais dados e permanece utilizável.
4. Nenhum upload ou vínculo indevido é persistido.

### Pontos a confirmar e limites do RF26

Nome, extensão, MIME, tamanho do arquivo e resposta da API não ficaram confirmados. Repetir com arquivo controlado, observar cliente e rede e verificar ausência de vínculo após salvar e reabrir. A causa técnica não foi determinada.

---

<a id="rf27"></a>


## RF27 — Rejeitar imagem no campo de vídeo com feedback

| Campo | Descrição |
| --- | --- |
| Requisito de QA | O campo Vídeo deve rejeitar arquivos de imagem e informar os formatos e limites aceitos, sem descartar os demais dados do formulário. |
| Ator | Usuário autenticado com permissão em Exercícios. |
| Pré-condições | Formulário aberto e arquivo de imagem de teste disponível, com extensão, MIME e tamanho conhecidos. |
| Gatilho | Selecionar a imagem no campo Vídeo. |
| Caso | [CT-RF27](Cenario_Teste/CT-RF27_Imagem_Campo_Video.md) |
| Situação observada | Reprovado conforme a gravação. O arquivo não aparece anexado, porém não há mensagem visível explicando a rejeição ou os formatos permitidos. |
| Defeito | [BUG-015](Relatorio-de-Bugs.md#bug-015), em triagem |
| Evidências | [Jam](https://jam.dev/c/be9437a4-4fe9-4756-a2af-6777d3f43e25). |

### Critérios de aceitação do RF27

1. Arquivos de imagem não são aceitos como vídeo.
2. A mensagem identifica o tipo incompatível e informa formatos e tamanho máximo aceitos.
3. O formulário conserva os demais dados e permanece utilizável.
4. Nenhum upload ou vínculo indevido é persistido.

### Pontos a confirmar e limites do RF27

Nome, extensão, MIME, tamanho do arquivo e resposta da API não ficaram confirmados. Repetir com arquivo controlado, observar cliente e rede e verificar ausência de vínculo após salvar e reabrir. A causa técnica não foi determinada.


## RF28 — Excluir grupo muscular ou explicar o impedimento

| Campo | Descrição |
| --- | --- |
| Requisito de QA | A exclusão de um grupo muscular deve ser concluída quando permitida, removendo o registro da listagem e atualizando os contadores; quando houver impedimento de regra, o sistema deve informá-lo de forma específica e tratável, sem erro interno do servidor. |
| Ator | Usuário autenticado com permissão em Grupos Musculares. |
| Pré-condições | Listagem carregada, registro de teste conhecido e vínculos desse registro identificados antes da execução. |
| Gatilho | Acionar a ação de exclusão na linha do registro e confirmar no diálogo "Deseja deletar o Grupo?". |
| Caso | [CT-RF28](Cenario_Teste/CT-RF28_Exclusao_GrupoMuscular.md) |
| Situação observada | Reprovado nas evidências. Duas tentativas de exclusão retornam HTTP 500 com o corpo "Erro interno inesperado."; a interface apresenta o diálogo "Erro ao deletar Grupo" e o registro permanece na listagem. |
| Defeito | [BUG-016](Relatorio-de-Bugs.md#bug-016), em triagem |
| Evidências | [Jam](https://jam.dev/c/98008390-0040-475e-ba7b-7f1e72cc0b2e). |

### Critérios de aceitação do RF28

1. A ação de exclusão apresenta confirmação explícita antes de efetivar a operação.
2. A exclusão permitida remove o registro da listagem e atualiza os contadores do resumo.
3. O impedimento de regra é comunicado com mensagem específica, sem erro interno do servidor.
4. Nenhum cenário de exclusão retorna HTTP 500.
5. O resultado se mantém após recarga da página.

### Pontos a confirmar e limites do RF28

Não foram consultados logs do servidor, corpo completo da resposta além dos 64 bytes retornados nem o banco de dados; a causa do HTTP 500 permanece indeterminada. Não foi confirmado se o registro permanece íntegro após as duas tentativas enviadas para o mesmo recurso. O cenário de exclusão com impedimento de regra não foi exercitado, de modo que não se sabe se o sistema distingue impedimento de falha. A mensagem "Erro ao deletar Grupo" é genérica e não informa a causa ao usuário.

---


## RF29 — Exibir as imagens cadastradas dos grupos musculares

| Campo | Descrição |
| --- | --- |
| Requisito de QA | A listagem deve apresentar a imagem de cada grupo muscular que a possua, com as requisições dos arquivos concluídas com sucesso, e adotar um estado neutro definido para registros sem imagem. |
| Ator | Usuário autenticado com acesso a Grupos Musculares. |
| Pré-condições | Listagem carregada e caminho esperado dos arquivos de imagem conhecido. |
| Gatilho | Carregar a tela Grupos Musculares, aplicar filtros ou alternar o tema, situações em que a listagem é recarregada. |
| Caso | [CT-RF29](Cenario_Teste/CT-RF29_Imagens_GruposMusculares.md) |
| Situação observada | Reprovado nas evidências. As requisições dos quatro arquivos de imagem retornam HTTP 422 durante toda a gravação, com ocorrências de `net::ERR_ABORTED`, e a coluna IMAGEM apresenta o ícone de imagem quebrada em todas as linhas, nos dois temas e com ou sem filtro. |
| Defeito | [BUG-017](Relatorio-de-Bugs.md#bug-017), em triagem |
| Evidências | [Jam](https://jam.dev/c/98008390-0040-475e-ba7b-7f1e72cc0b2e). |

### Critérios de aceitação do RF29

1. Cada grupo muscular com imagem cadastrada apresenta a imagem na coluna IMAGEM.
2. As requisições dos arquivos de imagem são concluídas com sucesso.
3. Registros sem imagem apresentam um estado neutro definido pelo produto, e não um ícone de arquivo quebrado.
4. O comportamento se mantém após busca, troca de página e troca de tema.

### Pontos a confirmar e limites do RF29

Não foi verificada a existência dos arquivos em `/img/grupos_musculares/imagens/`, nem o conteúdo do campo de imagem de cada registro no banco, nem o resultado do acesso direto às URLs fora da página. O código 422 não é o retorno usual para arquivo ausente ou sem permissão, o que sugere tratamento por aplicação em vez de entrega direta de arquivo estático; essa é uma hipótese a confirmar. Os status foram lidos na coluna Status da lista de rede, porque o painel de detalhe da ferramenta repetiu cabeçalhos e identificadores entre linhas distintas. Resta confirmar também o comportamento para registros criados sem imagem informada, que passam a ter um arquivo requisitado.

---


## RF30 — Cadastrar e listar um grupo muscular

| Campo | Descrição |
| --- | --- |
| Requisito de QA | O sistema deve permitir cadastrar um grupo muscular, apresentá-lo na listagem e atualizar os contadores do resumo, mantendo a contagem do rodapé coerente com os registros exibidos. |
| Ator | Usuário autenticado com permissão em Grupos Musculares. |
| Pré-condições | Nome de grupo muscular de teste disponível e estado inicial da listagem e dos contadores registrado. |
| Gatilho | Abrir o formulário de inclusão, informar nome e tipo de membro e confirmar em "Salvar". |
| Caso | [CT-RF30](Cenario_Teste/CT-RF30_Cadastro_GrupoMuscular.md) |
| Situação observada | Aprovado conforme a gravação. O registro "Tríceps" foi criado com o código 6 e tipo "Superiores"; a listagem passou de três para quatro registros e os cartões de Grupos cadastrados e Superiores acompanharam a inclusão. |
| Defeito | Nenhum no fluxo avaliado |
| Evidências | [Jam](https://jam.dev/c/98008390-0040-475e-ba7b-7f1e72cc0b2e). |

### Critérios de aceitação do RF30

1. O formulário permite informar nome e tipo de membro.
2. O envio cria o registro e encerra o formulário.
3. A listagem passa a exibir o novo grupo muscular, com o rodapé de contagem coerente.
4. Os cartões de resumo refletem a inclusão, inclusive o cartão do tipo de membro escolhido.
5. O registro permanece após recarga da página.

### Pontos a confirmar e limites do RF30

A cronologia não registra uma requisição de criação com o respectivo código de status; a conclusão apoia-se na comparação entre os quadros de 0:48 e 0:55. A persistência após recarga não foi verificada, nem houve consulta ao banco. Permanecem fora do cenário gravado campos obrigatórios em branco, nomes duplicados, limites de tamanho, caracteres especiais e cancelamento do formulário. O campo Código estava em branco no envio e o sistema atribuiu o código 6; a atribuição automática é compatível com os códigos não sequenciais da listagem, mas a regra não foi confirmada, nem foi testado o envio com código informado manualmente. O formulário foi enviado sem imagem e, ainda assim, passou a existir um arquivo requisitado para o novo registro, situação tratada no [RF29](#rf29).

---


## RF31 — Alterar o tipo de membro de um grupo muscular

| Campo | Descrição |
| --- | --- |
| Requisito de QA | O sistema deve permitir alterar o tipo de membro de um grupo muscular existente, refletir a mudança na listagem e recalcular os cartões de resumo, mantendo a soma dos tipos igual ao total de registros. |
| Ator | Usuário autenticado com permissão em Grupos Musculares. |
| Pré-condições | Registro de teste com tipo de membro conhecido e estado inicial dos cartões de resumo registrado. |
| Gatilho | Abrir a edição do registro, selecionar outro tipo de membro e confirmar em "Salvar". |
| Caso | [CT-RF31](Cenario_Teste/CT-RF31_Edicao_TipoMembro.md) |
| Situação observada | Aprovado conforme a gravação. O registro de código 1 passou de "Superiores" para "Inferiores" e os cartões acompanharam, de Superiores 3 / Inferiores 1 para Superiores 2 / Inferiores 2, com o total constante em quatro. |
| Defeito | Nenhum no fluxo avaliado |
| Evidências | [Jam](https://jam.dev/c/98008390-0040-475e-ba7b-7f1e72cc0b2e). |

### Critérios de aceitação do RF31

1. O formulário de edição abre preenchido com os dados atuais do registro.
2. A alteração do tipo de membro é persistida e exibida na listagem.
3. Os cartões de resumo são recalculados e a soma dos tipos corresponde ao total de registros.
4. O resultado se mantém após recarga da página.

### Pontos a confirmar e limites do RF31

A cronologia não registra uma requisição de atualização com o respectivo código de status; a conclusão apoia-se na comparação entre os quadros de 1:02 e 1:08 e nos cartões de resumo. O controle que abre o formulário de edição não foi identificado com certeza na cronologia. A persistência após recarga não foi verificada, nem houve consulta ao banco. Permanecem fora do cenário gravado o cancelamento da edição, a alteração de nome, a alteração simultânea de vários campos e a validação de campos obrigatórios.

A edição recebeu um arquivo de imagem, com miniatura exibida corretamente na pré-visualização, mas após o envio o registro continua sem imagem na listagem e o arquivo requisitado mantém o mesmo nome anterior. Isso é compatível tanto com sobrescrita sob o mesmo nome quanto com não persistência do envio, e não distingue as duas hipóteses, já que todas as requisições de imagem retornam HTTP 422 conforme o [RF29](#rf29).

---


## RF32 — Filtrar a listagem de grupos musculares por código e tipo

| Campo | Descrição |
| --- | --- |
| Requisito de QA | A busca deve apresentar apenas os registros que atendam aos critérios informados, com a contagem do rodapé correspondente ao conjunto exibido, e informar explicitamente quando não houver correspondência. |
| Ator | Usuário autenticado com acesso a Grupos Musculares. |
| Pré-condições | Base conhecida, com a quantidade de registros por tipo de membro registrada e ao menos um tipo sem registros associados. |
| Gatilho | Informar código, selecionar tipo de membro e acionar a busca. |
| Caso | [CT-RF32](Cenario_Teste/CT-RF32_Filtros_GruposMusculares.md) |
| Situação observada | Aprovado conforme a gravação. O filtro por tipo sem registros apresenta "Nenhum grupo muscular encontrado" e rodapé "Mostrando 0 a 0 de 0 grupos"; os filtros por tipo e por código retornam o registro correspondente, com rodapé coerente. |
| Defeito | Nenhum no fluxo avaliado |
| Evidências | [Jam](https://jam.dev/c/98008390-0040-475e-ba7b-7f1e72cc0b2e). |

### Critérios de aceitação do RF32

1. A busca por tipo de membro retorna apenas registros daquele tipo.
2. A busca por código retorna o registro correspondente.
3. A contagem do rodapé corresponde aos registros apresentados.
4. A ausência de correspondência apresenta mensagem explícita, e não uma listagem vazia sem aviso.
5. A limpeza dos critérios restaura a listagem completa.

### Pontos a confirmar e limites do RF32

A lógica de combinação dos critérios não ficou demonstrada. No quadro de 2:00 o código e o tipo de membro estão preenchidos ao mesmo tempo e o resultado atende aos dois, porém o único registro daquele código também é daquele tipo, de modo que o mesmo resultado seria obtido com apenas um dos critérios. A verificação exige um caso em que os critérios se contradigam, cujo retorno esperado é o conjunto vazio; esse caso não foi exercitado. Esse ponto é relevante porque filtros combinados são o aspecto reprovado no [RF09](#rf09--pesquisar-clientes-com-filtros-combinados).

Permanecem fora do cenário gravado a busca por nome, código inexistente ou inválido, caracteres especiais, resultados com mais de uma linha, paginação do resultado filtrado e limpeza dos critérios. Os cartões de resumo não acompanham o filtro e mantêm o total da base, enquanto o rodapé acompanha o conjunto filtrado; o comportamento é coerente entre os quadros conferidos, mas o contrato de cada indicador não foi fornecido, do mesmo modo que no [RF15](#rf15).

---

<a id="rf08"></a>


## RF33 — Cadastrar objetivo de treino ou informar validação específica

| Campo | Descrição |
| --- | --- |
| Requisito de QA | O cadastro de um objetivo de treino deve ser confirmado e apresentado na listagem quando os dados forem válidos; quando algum dado for recusado, o sistema deve informar a validação específica e permitir a correção, sem erro interno do servidor. |
| Ator | Usuário autenticado com acesso a Objetivos Treino. |
| Pré-condições | Listagem carregada e estado inicial conhecido (registros e cartões Objetivos, Exibidos e Com Descrição); nome de teste disponível; regra do campo Código e da descrição confirmada com o produto. |
| Gatilho | Clicar em Novo Objetivo, informar nome e descrição e clicar em Salvar. |
| Caso | [CT-RF33](Cenario_Teste/CT-RF33_Cadastro_Objetivo_Treino.md) |
| Situação observada | Reprovado nas evidências. Duas ocorrências de `POST /api/objetivo-treino/salvar/1` retornam HTTP 500; a interface apresenta o diálogo "Erro ao salvar objetivo" e a listagem permanece sem registros. |
| Defeito | [BUG-019](Relatorio-de-Bugs.md#bug-019), em triagem |
| Evidências | [Jam](https://jam.dev/c/1d474477-2411-4a81-b85c-74207402b783) e [Evidências](Evidencias/CT-RF35_Cadastro_Objetivo_Treino/README.md). |

### Critérios de aceitação do RF33

1. O formulário permite informar nome e descrição e oferece as ações Salvar e Cancelar.
2. O envio válido cria o registro, encerra o formulário e confirma o resultado ao usuário.
3. A listagem passa a exibir o novo objetivo e os cartões de resumo refletem a inclusão.
4. Um dado recusado recebe mensagem específica, sem HTTP 500, e o formulário permite a correção.
5. Um único clique em Salvar gera uma única gravação, sem registros duplicados ou parciais.
6. O registro permanece após recarga da página.

### Pontos a confirmar e limites do RF33

Os corpos da requisição e da resposta não foram capturados pelo Jam; não é possível afirmar o payload enviado nem a mensagem retornada, e a causa do HTTP 500 permanece indeterminada. A descrição utilizada continha caracteres especiais (`#@`), o que orienta a verificação, sem comprovar a causa. Não foi confirmada a persistência de registros parciais nem a razão de duas ocorrências de HTTP 500 para uma única ação de salvar registrada.

O campo Código permaneceu vazio nos quadros apesar da digitação registrada; a evidência não distingue um código atribuído automaticamente (como se interpretou no [RF30](#rf30)) do impedimento relatado no [RF21](#rf21). A base estava vazia, de modo que os filtros por código e nome não puderam ser avaliados, e a mensagem "Nenhum objetivo cadastrado" também aparece com filtro aplicado; a distinção entre "nenhum cadastrado" e "nenhum encontrado" depende de confirmação do produto, como no [RF32](#rf32). O padrão de HTTP 500 em operação de escrita repete o de [RF38](#rf38), [RF10](#rf10) e [RF28](#rf28), em módulos distintos.

---

<a id="rf40"></a>


## RF34 — Excluir grupo ou explicar o impedimento

| Campo | Descrição |
| --- | --- |
| Requisito de QA | A exclusão de um grupo deve ser concluída quando permitida, removendo o registro da listagem e atualizando os contadores; quando houver impedimento de regra, o sistema deve informá-lo de forma específica e tratável, sem erro interno do servidor. |
| Ator | Usuário autenticado com permissão em Grupos. |
| Pré-condições | Listagem carregada, registro de teste conhecido e vínculos desse registro identificados antes da execução. |
| Gatilho | Acionar a ação de exclusão na linha do registro e confirmar no diálogo "Deseja deletar o Grupo?". |
| Caso | [CT-RF34](Cenario_Teste/CT-RF34_Exclusao_Grupo.md) |
| Situação observada | Reprovado nas evidências. Duas tentativas de exclusão retornam HTTP 500 com o corpo "Erro interno inesperado."; o registro permanece na listagem e os contadores não se alteram. A mensagem e o padrão do erro coincidem com os já registrados no RF28 para grupos musculares. |
| Defeito | [BUG-024](Relatorio-de-Bugs.md#bug-024), em triagem |
| Evidências | [Jam](https://jam.dev/c/b1231a75-1a65-4bf0-b795-f52a8c7d3365). |

### Critérios de aceitação do RF34

1. A ação de exclusão apresenta confirmação explícita antes de efetivar a operação.
2. A exclusão permitida remove o registro da listagem e atualiza os contadores do resumo.
3. O impedimento de regra é comunicado com mensagem específica, sem erro interno do servidor.
4. Nenhum cenário de exclusão retorna HTTP 500.
5. O resultado se mantém após recarga da página.

### Pontos a confirmar e limites do RF34

Não foram consultados logs do servidor, corpo completo da resposta além dos 64 bytes retornados nem o banco de dados; a causa do HTTP 500 permanece indeterminada. Não foi possível confirmar visualmente o texto do diálogo de erro apresentado após a falha, pois o componente de alerta é fechado em menos de um segundo na gravação. Não foi confirmado se o registro permanece íntegro após as duas tentativas enviadas para o mesmo recurso. O cenário de exclusão com impedimento de regra não foi exercitado.

---


## RF35 — Persistir todos os campos editados de um grupo

| Campo | Descrição |
| --- | --- |
| Requisito de QA | Ao salvar a edição de um grupo, todo campo alterado deve ser persistido pelo backend; uma resposta de sucesso não deve ser retornada para uma alteração que não foi efetivamente salva. |
| Ator | Usuário autenticado com permissão em Grupos. |
| Pré-condições | Grupo de teste conhecido, com todos os campos atuais registrados antes da edição. |
| Gatilho | Abrir a edição do grupo, alterar um campo isoladamente (por exemplo, Status) e acionar Salvar. |
| Caso | [CT-RF35](Cenario_Teste/CT-RF35_Edicao_Grupo.md) |
| Situação observada | Reprovado nas evidências. A alteração do campo Status de "Ativo" para "Inativo" retorna sucesso (`verifica_erro: false`), mas a consulta imediatamente seguinte mostra o registro ainda com status "Ativo". Na mesma sessão e no mesmo registro, a alteração do campo Descrição é persistida corretamente, descartando falha geral de salvamento, sessão ou rede. |
| Defeito | [BUG-025](Relatorio-de-Bugs.md#bug-025), em triagem |
| Evidências | [Jam](https://jam.dev/c/b1231a75-1a65-4bf0-b795-f52a8c7d3365). |

### Critérios de aceitação do RF35

1. A edição de qualquer campo do grupo retorna sucesso somente quando o valor é efetivamente persistido.
2. O campo Status, especificamente, é persistido ao ser alterado e confirmado por consulta subsequente.
3. Uma resposta de sucesso nunca é retornada para uma alteração que não foi salva.
4. O resultado se mantém após recarga da página e nova consulta ao registro.
5. O comportamento é validado também para outros grupos e, se aplicável, para a entidade grupo muscular.

### Pontos a confirmar e limites do RF35

Não houve acesso a logs do servidor, ao código da rotina de edição nem ao banco de dados para confirmar o valor realmente gravado. A causa da falha isolada no campo `status` não foi determinada: pode ser uma whitelist de campos editáveis que exclui esse campo, uma rotina de atualização que o ignora silenciosamente, ou outra causa não identificada. Foi observado também um descompasso de cerca de 4 horas entre o cabeçalho HTTP `data` e o campo `updated_at` da resposta, sem relação confirmada com o defeito.

---


## RF36 — Filtrar categorias por código e nome

| Campo | Descrição |
| --- | --- |
| Requisito de QA | Exibir apenas os registros correspondentes aos critérios e restaurar a lista ao limpar. |
| Ator | Usuário autenticado com permissão no módulo. |
| Pré-condições | Sessão autenticada e acesso a Categorias Crossfit. Categorias conhecidas por código e nome para comparação. |
| Gatilho | Pesquisar por códigos conhecidos e conferir o resultado exibido. Limpar a busca com a ação de recarregar/limpar e conferir a lista geral. Pesquisar barbell no campo Nome e comparar as linhas com a base. |
| Caso | [CT-RF36](Cenario_Teste/CT-RF36_Filtros_Categorias.md) |
| Situação observada | Aprovado conforme a gravação. A quantidade de linhas exibidas muda conforme o código informado; a limpeza retorna a lista e a busca por barbell mostra a categoria correspondente. |
| Defeito | Nenhum no fluxo avaliado |
| Evidências | [Evidências](Evidencias/CT-RF17_Filtros_Categorias/README.md) e [Jam](https://jam.dev/c/5e75e423-9c7e-43d7-aade-9b1a32c5e559). |

### Critérios de aceitação do RF36

1. Código restringe ao registro correspondente.
2. Nome restringe conforme a regra de correspondência definida.
3. Limpar a pesquisa restaura a listagem e a contagem.

### Pontos a confirmar e limites do RF36

Resultado válido para os exemplos gravados. Não cobre combinações de filtros, valores inválidos, caracteres especiais ou paginação. Usar como regressão; combinações, conjunto vazio, caracteres especiais e paginação exigem execuções adicionais.

---

<a id="rf37"></a>


## RF37 — Salvar a atualização do nome de categoria

| Campo | Descrição |
| --- | --- |
| Requisito de QA | Persistir a alteração e atualizar a listagem. |
| Ator | Usuário autenticado com permissão no módulo. |
| Pré-condições | Sessão autenticada com permissão de edição. Categoria de teste editável e nome inicial conhecido. |
| Gatilho | Abrir a edição da categoria Barbell teste da base de referência. Alterar o nome para Barbell novo. Clicar em Salvar e conferir o valor atualizado na lista; em nova execução, recarregar para conferir persistência. |
| Caso | [CT-RF37](Cenario_Teste/CT-RF37_Atualizacao_Categoria.md) |
| Situação observada | Aprovado conforme a gravação. O modal fecha e a lista exibe Barbell novo. |
| Defeito | Nenhum no fluxo avaliado |
| Evidências | [Evidências](Evidencias/CT-RF18_Atualizacao_Categoria/README.md) e [Jam](https://jam.dev/c/67664a98-2a4a-4134-91a9-7ca9b8aa9dbd). |

### Critérios de aceitação do RF37

1. O editor carrega a categoria selecionada.
2. Salvar conclui a atualização e retorna à lista com o novo nome.
3. Persistência após recarga ou nova sessão é uma extensão de validação ainda não executada.

### Pontos a confirmar e limites do RF37

A atualização está demonstrada na própria gravação. Não houve novo teste de persistência após outra sessão ou novo login. Usar como regressão; acrescentar recarga e nova consulta para ampliar a verificação de persistência.

---

<a id="rf38"></a>


## RF38 — Excluir categoria permitida ou explicar o impedimento

| Campo | Descrição |
| --- | --- |
| Requisito de QA | Concluir a exclusão permitida ou explicar de forma tratável por que o registro não pode ser excluído. |
| Ator | Usuário autenticado com permissão no módulo. |
| Pré-condições | Sessão autenticada com permissão para excluir categorias. Categoria descartável e vínculos conhecidos; confirmar os impedimentos de exclusão previstos. |
| Gatilho | Acionar a lixeira da categoria de teste. Confirmar a exclusão no diálogo. Conferir retorno visual, status da chamada e presença do registro após a operação. |
| Caso | [CT-RF38](Cenario_Teste/CT-RF38_Exclusao_Categoria.md) |
| Situação observada | Reprovado nas evidências. Após a confirmação, aparece o diálogo “Erro” / “Erro ao deletar categoria”. A categoria permanece na lista. |
| Defeito | [BUG-009](Relatorio-de-Bugs.md#bug-009) |
| Evidências | [Evidências](Evidencias/CT-RF19_Exclusao_Categoria/README.md) e [Jam](https://jam.dev/c/c5c78b3b-2865-4226-836f-bcb0a8fc612f). |

### Critérios de aceitação do RF38

1. Exclusão permitida remove ou altera o registro conforme a regra definida.
2. Impedimentos por vínculos são informados de forma compreensível e sem falha interna genérica.
3. A listagem e o retorno da operação refletem o resultado efetivo.

### Pontos a confirmar e limites do RF38

O erro e o endpoint estão registrados. Sem o corpo completo da resposta, logs do servidor ou banco, a causa do HTTP 500 não foi determinada. Investigar o HTTP 500 com logs do servidor e vínculos da categoria; corrigir e retestar cenários permitido e impedido.

---

<a id="rf39"></a>


## RF39 — Cadastrar e listar uma nova categoria

| Campo | Descrição |
| --- | --- |
| Requisito de QA | Criar a categoria e apresentar o novo registro na listagem. |
| Ator | Usuário autenticado com permissão no módulo. |
| Pré-condições | Sessão autenticada com permissão para cadastrar categorias. Nome de categoria de teste disponível segundo as regras do produto. |
| Gatilho | Clicar em Nova Categoria. Preencher o nome cardio leve na base de referência. Clicar em Salvar e conferir o novo registro e o contador da lista. |
| Caso | [CT-RF39](Cenario_Teste/CT-RF39_Criacao_Categoria.md) |
| Situação observada | Aprovado conforme a gravação. O modal fecha, o contador passa de sete para oito e a lista passa a incluir cardio leve. |
| Defeito | Nenhum no fluxo avaliado |
| Evidências | [Evidências](Evidencias/CT-RF20_Criacao_Categoria/README.md) e [Jam](https://jam.dev/c/b48ab94e-517d-48d6-8e46-70b18c033b8b). |

### Critérios de aceitação do RF39

1. O formulário permite informar um nome válido.
2. Salvar cria o registro e fecha o formulário com retorno de sucesso.
3. A lista exibe a nova categoria e o total atualizado.

### Pontos a confirmar e limites do RF39

O teste demonstra criação no cenário gravado. Não cobre campos vazios, duplicidade ou validações de tamanho. Usar como regressão; campos vazios, nomes duplicados e limites de tamanho permanecem fora do cenário gravado.

---

<a id="rf10"></a>


## RF40 — Cadastrar categoria com código automático e localizá-la pelos filtros

| Campo | Descrição |
| --- | --- |
| Requisito de QA | O cadastro de uma categoria deve exigir apenas o nome, com o código atribuído pelo sistema, e o novo registro deve constar na listagem e ser localizado pelos filtros de código e de nome, com o cartão Exibidas coerente. |
| Ator | Usuário autenticado com permissão em Categorias Crossfit. |
| Pré-condições | Base conhecida (quantidade de categorias e códigos registrados); nome de categoria de teste disponível; regra do campo Código confirmada com o produto. |
| Gatilho | Clicar em Nova Categoria, informar o nome e clicar em Salvar; depois informar o código atribuído no filtro Código. |
| Caso | [CT-RF40](Cenario_Teste/CT-RF40_Cadastro_Categoria_Codigo_Automatico.md) |
| Situação observada | Aprovado conforme a gravação. `POST /api/categoria-exercicio-cross/criar` retorna HTTP 201 com o corpo `{"nome": "teste"}` e "Categoria criada com sucesso!"; a listagem passa de oito para nove categorias, com o código 9, e o filtro Código "9" retorna apenas esse registro. O campo Código não retém o texto digitado. |
| Defeito | Nenhum no fluxo avaliado |
| Evidências | [Jam](https://jam.dev/c/be1dbd05-217d-44c3-8a3d-240b7f6344e1) e [Evidências](Evidencias/CT-RF38_Cadastro_Categoria_Codigo_Automatico/README.md). |

### Critérios de aceitação do RF40

1. O formulário permite informar o nome e cria a categoria ao salvar, com mensagem de sucesso.
2. O código é atribuído pelo sistema, sem depender de valor digitado pelo usuário, e não duplica um código existente.
3. A listagem e os cartões de resumo refletem a inclusão.
4. O filtro por nome e o filtro por código retornam apenas os registros correspondentes.
5. A limpeza dos filtros restaura a listagem completa.
6. O registro permanece após recarga da página.

### Pontos a confirmar e limites do RF40

A regra do campo Código não foi fornecida: o campo não retém o texto digitado e o código não consta no corpo da requisição, o que é compatível com um código automático (como nos [RF30](#rf30) e [RF33](#rf33)), mas também com um campo bloqueado à digitação, relacionado ao relato do [RF21](#rf21). Os filtros não geram requisição de rede, compatível com filtragem local, sem confirmação; o comportamento com bases maiores ou paginadas não foi avaliado. O contrato dos cartões de resumo, em especial Atualizadas, não foi fornecido, do mesmo modo que no [RF15](#rf15).

Permanecem fora do cenário gravado: nome vazio, nome duplicado, limites de tamanho, caracteres especiais, código inexistente ou não numérico no filtro, combinação contraditória de código e nome, resultado vazio, paginação e persistência após recarga. O RF40 complementa o [RF36](#rf36) (filtros) e o [RF39](#rf39) (criação), sem substituí-los.

---

<a id="rf44"></a>


## RF41 — Preservar a legibilidade das tabelas no tema escuro

| Campo | Descrição |
| --- | --- |
| Requisito de QA | Aplicar cores de texto e de fundo que preservem a legibilidade em ambos os temas. |
| Ator | Usuário autenticado com permissão no módulo. |
| Pré-condições | Sessão autenticada com acesso a SifitBox – Turmas. Página com modalidades e turmas recorrentes cadastradas. |
| Gatilho | Registrar a apresentação das tabelas no tema Claro. Selecionar Escuro. Conferir títulos, nomes, status e ações sobre os fundos das duas tabelas. |
| Caso | [CT-RF41](Cenario_Teste/CT-RF41_Contraste_TemaEscuro.md) |
| Situação observada | Reprovado nas evidências. As áreas de Modalidades e Turmas recorrentes permanecem brancas enquanto diversos textos ficam muito claros, dificultando sua leitura. |
| Defeito | [BUG-007](Relatorio-de-Bugs.md#bug-007) |
| Evidências | [Evidências](Evidencias/CT-RF14_Contraste_TemaEscuro/README.md) e [Jam](https://jam.dev/c/6889db07-bed1-472b-8ec2-00402919cd65). |

### Critérios de aceitação do RF41

1. Nomes e demais textos permanecem legíveis ao alternar o tema.
2. Títulos, filtros, status e ações podem ser identificados nas duas tabelas.
3. Uma conclusão formal de acessibilidade depende de medição de contraste e do padrão acordado.

### Pontos a confirmar e limites do RF41

A observação é visual. Não foi medida a razão de contraste nem realizada uma auditoria formal de acessibilidade. Ajustar as cores e retestar ambos os temas; medir contraste se houver critério formal de acessibilidade definido.

---

<a id="rf42"></a>


## RF42 — Permitir concluir e cancelar a edição de modalidade

| Campo | Descrição |
| --- | --- |
| Requisito de QA | Oferecer ações visíveis de salvar e cancelar e confirmar a atualização. |
| Ator | Usuário autenticado com permissão no módulo. |
| Pré-condições | Sessão autenticada com permissão para editar modalidades. Modalidade de teste com nome, descrição e status conhecidos. |
| Gatilho | Clicar no lápis de uma modalidade. Verificar o preenchimento dos campos e alterar um valor de teste. Localizar e usar a ação de salvar; conferir confirmação e recarregar a lista para validar persistência. |
| Caso | [CT-RF42](Cenario_Teste/CT-RF42_Edicao_Modalidade.md) |
| Situação observada | Reprovado nas evidências. Há ícones de lápis na lista. Ao clicar, os campos superiores são preenchidos para edição, mas não aparece uma ação clara para salvar ou concluir a alteração nos quadros analisados. |
| Defeito | [BUG-008](Relatorio-de-Bugs.md#bug-008) |
| Evidências | [Evidências](Evidencias/CT-RF15_Edicao_Modalidade/README.md) e [Jam](https://jam.dev/c/951efaf8-bf32-44b0-b640-a2935a6b554a). |

### Critérios de aceitação do RF42

1. O lápis carrega os dados do registro selecionado.
2. Salvar e cancelar são ações visíveis e compreensíveis.
3. Salvar persiste os dados; cancelar preserva os valores anteriores.

### Pontos a confirmar e limites do RF42

O título original diz “Sem botão para editar modalidades”, mas o lápis existe. A dificuldade demonstrada é concluir a edição; a gravação não prova ausência de toda alternativa de salvamento. Verificar o fluxo de conclusão da edição e retestar persistência. A evidência reprova a clareza da ação de salvar; não afirma que o ícone de editar inexiste.

---

<a id="rf43"></a>


## RF43 — Comunicar e aplicar a regra de remoção de modalidade

| Campo | Descrição |
| --- | --- |
| Requisito de QA | O nome, o ícone e a confirmação da ação devem informar se o efeito é desativar ou excluir definitivamente. |
| Ator | Usuário autenticado com permissão no módulo. |
| Pré-condições | Sessão autenticada e modalidade descartável na base de teste. Confirmar se a ação realiza exclusão lógica, inativação ou exclusão definitiva e como trata vínculos. |
| Gatilho | Registrar o status e os vínculos da modalidade de teste. Acionar a lixeira conforme a regra e eventual confirmação definida pelo produto. Verificar o estado final e os filtros da lista; não repetir a ação para exigir exclusão física sem regra confirmada. |
| Caso | [CT-RF43](Cenario_Teste/CT-RF43_Exclusao_Modalidade.md) |
| Situação observada | A validar — regra ou contexto pendente. As modalidades passam a aparecer como inativas e continuam na listagem, mesmo após novos cliques. A linha do tempo registra chamadas a /api/sifitbox/modalidades/excluir/1 e recargas das listas com HTTP 200. |
| Defeito | Sem defeito confirmado |
| Evidências | [Evidências](Evidencias/CT-RF16_Exclusao_Modalidade/README.md) e [Jam](https://jam.dev/c/0f55f76a-cd31-4cee-93da-23c13b1ba637). |

### Critérios de aceitação do RF43

1. Nome, ícone e confirmação da ação comunicam seu efeito.
2. O estado final corresponde à regra de inativação ou exclusão acordada.
3. Vínculos e filtros têm tratamento definido; manter registros inativos pode ser comportamento válido.

### Pontos a confirmar e limites do RF43

A inativação pode ser uma exclusão lógica prevista pelo sistema. É necessário confirmar a regra do produto antes de exigir exclusão definitiva. Nenhuma exclusão foi executada nesta revisão. Confirmar a exclusão lógica e a nomenclatura da ação; registrar defeito apenas se houver divergência com a regra definida.

---

<a id="rf36"></a>


## RF44 — Cadastrar modalidade em SifitBox – Turmas

| Campo | Descrição |
| --- | --- |
| Requisito de QA | O cadastro de uma modalidade deve criar o registro com o nome, a descrição e o status informados, apresentá-lo na listagem de Modalidades e limpar o formulário. |
| Ator | Usuário autenticado com permissão em SifitBox – Turmas. |
| Pré-condições | Listagem de Modalidades conhecida; nome de modalidade de teste disponível. |
| Gatilho | Preencher nome e descrição da modalidade, manter o status Ativo e acionar o botão de envio de Modalidade. |
| Caso | [CT-RF44](Cenario_Teste/CT-RF44_Cadastro_Modalidade.md) |
| Situação observada | Aprovado conforme a gravação. `POST /api/sifitbox/modalidades/salvar/1` retorna HTTP 201 com a modalidade de id 4 e status "ativo"; a listagem passa de três para quatro modalidades e o formulário é limpo. |
| Defeito | Nenhum no fluxo avaliado |
| Evidências | [Jam](https://jam.dev/c/ee9a133b-d6b1-442d-b4b0-dd87595b7e70) e [Evidências](Evidencias/CT-RF39_Cadastro_Modalidade/README.md). |

### Critérios de aceitação do RF44

1. O formulário permite informar nome, descrição e status e cria a modalidade ao confirmar.
2. A resposta retorna sucesso e o registro com os dados informados e o status escolhido.
3. A listagem passa a exibir a nova modalidade e o formulário é limpo.
4. A modalidade permanece após recarga da página.
5. Dados inválidos ou ausentes recebem validação específica, sem HTTP 500.

### Pontos a confirmar e limites do RF44

Não foram verificados a persistência após recarga, a mensagem de confirmação, o nome vazio, o nome duplicado e os limites de tamanho. O corpo enviado traz `"id": {}` (objeto vazio), aceito pelo sistema; o contrato da API não foi fornecido. As modalidades anteriores aparecem como "inativo" sob o filtro "Ativo", ponto tratado no [RF45](#rf45) e relacionado ao [RF43](#rf43).

---

<a id="rf45"></a>


## RF45 — Excluir turmas e modalidades conforme a regra de exclusão

| Campo | Descrição |
| --- | --- |
| Requisito de QA | A lixeira de turmas e de modalidades deve aplicar a regra de exclusão definida pelo produto (lógica ou física), com confirmação prévia quando exigida, informar o resultado ao usuário e refletir o resultado na listagem conforme o filtro de status selecionado. |
| Ator | Usuário autenticado com permissão em SifitBox – Turmas. |
| Pré-condições | Turmas e modalidades de teste com status e vínculos conhecidos; regra de exclusão e de confirmação definida com o produto. |
| Gatilho | Acionar a lixeira de uma turma ou de uma modalidade na listagem. |
| Caso | [CT-RF45](Cenario_Teste/CT-RF45_Exclusao_Turmas_Modalidades.md) |
| Situação observada | A validar — regra ou contexto pendente. Os cliques na lixeira geram `POST turmas/excluir` e `POST modalidades/excluir` com HTTP 200 e `{"erro": false}`; os registros permanecem na listagem com o status "inativo", sem diálogo de confirmação nos quadros consultados. |
| Defeito | Sem defeito confirmado |
| Evidências | [Jam](https://jam.dev/c/ee9a133b-d6b1-442d-b4b0-dd87595b7e70) e [Evidências](Evidencias/CT-RF40_Exclusao_Turmas_Modalidades/README.md). |

### Critérios de aceitação do RF45

1. A lixeira aplica a regra de exclusão definida pelo produto, com confirmação prévia quando exigida.
2. A resposta e a interface informam o resultado de forma compreensível.
3. A listagem apresenta apenas registros compatíveis com o filtro de status selecionado.
4. Turmas vinculadas a uma modalidade excluída ou inativada recebem tratamento definido e comunicado.
5. A ação sobre um registro já inativo tem retorno coerente.
6. O resultado se mantém após recarga da página.

### Pontos a confirmar e limites do RF45

Não foram confirmados a regra de exclusão lógica, a necessidade de confirmação, a exibição de registros inativos sob o filtro "Ativo", o efeito sobre turmas vinculadas e a persistência após recarga. Os corpos das requisições de exclusão e o filtro "Inativo" não foram inspecionados. O comportamento repete o ponto a validar do [RF43](#rf43). Registrar defeito apenas se houver divergência com a regra definida.

---

<a id="rf46"></a>


## RF46 — Cadastrar turma ou informar o dado que impede o envio

| Campo | Descrição |
| --- | --- |
| Requisito de QA | O cadastro de turma deve criar a turma quando todos os dados obrigatórios forem informados; com dado obrigatório ausente (como a modalidade), deve bloquear o envio, indicar de forma visível o campo pendente e não criar registro. |
| Ator | Usuário autenticado com permissão em SifitBox – Turmas. |
| Pré-condições | Ao menos uma modalidade ativa; turmas existentes registradas; regra de obrigatoriedade dos campos definida com o produto. |
| Gatilho | Preencher o formulário de Turma, sem selecionar a modalidade, e acionar o botão de envio de Turma. |
| Caso | [CT-RF46](Cenario_Teste/CT-RF46_Cadastro_Turma_Sem_Modalidade.md) |
| Situação observada | Reprovado nas evidências — sem feedback de validação visível. Nas tentativas com formulário vazio e com a modalidade em branco, o envio não gera requisição de criação de turma nem apresenta mensagem; o formulário permanece preenchido e a listagem não muda. |
| Defeito | [BUG-020](Relatorio-de-Bugs.md#bug-020), em triagem |
| Evidências | [Jam](https://jam.dev/c/ee9a133b-d6b1-442d-b4b0-dd87595b7e70) e [Evidências](Evidencias/CT-RF41_Cadastro_Turma_Sem_Modalidade/README.md). |

### Critérios de aceitação do RF46

1. O envio de Turma com campo obrigatório vazio é bloqueado e cada campo pendente recebe indicação compreensível.
2. Nenhum registro vazio ou incompleto é criado.
3. Com todos os dados válidos, a turma é criada, apresentada na listagem e mantida após recarga.
4. A ação de envio informa o resultado (sucesso ou impedimento) ao usuário.
5. O horário de término anterior ou igual ao de início recebe validação específica, conforme a regra do produto.

### Pontos a confirmar e limites do RF46

Não foi confirmado se a modalidade é obrigatória nem se existe validação nativa do navegador, cujo balão normalmente não aparece em gravações de tela. O envio válido, o horário de término igual ou anterior ao de início, o nome vazio e a persistência não foram exercitados. A edição da turma de id 4 gerou `POST turmas/atualizar` com HTTP 200, sem mensagem de confirmação observada. O padrão de ausência de feedback repete o do [RF25](#rf25).

---

<a id="rf47"></a>


## RF47 — Solicitar saque e informar o resultado

| Campo | Descrição |
| --- | --- |
| Requisito de QA | A solicitação de saque pelo painel Pagar.me deve registrar o pedido e informar ao usuário o resultado (sucesso ou impedimento), atualizando o saldo quando aplicável. |
| Ator | Usuário autenticado com acesso ao módulo Pagar.me. |
| Pré-condições | Conta de pagamento configurada; saldo disponível conhecido; regra de saque definida com o produto. |
| Gatilho | Acionar Solicitar saque, informar o valor e confirmar. |
| Caso | [CT-RF47](Cenario_Teste/CT-RF47_Solicitacao_Saque_PagarMe.md) |
| Situação observada | A validar — regra ou contexto pendente. A confirmação do saque (valor 1000, saldo "R$ --") gera `POST sacar-saldo` com HTTP 200, mas a interface não apresenta mensagem de resultado. |
| Defeito | Sem defeito confirmado |
| Evidências | [Jam](https://jam.dev/c/e6e551ef-9196-4c79-b6a2-89747b1e8b33) e [Evidências](Evidencias/CT-RF42_Solicitacao_Saque_PagarMe/README.md). |

### Critérios de aceitação do RF47

1. A solicitação de saque informa o resultado (sucesso ou impedimento) de forma compreensível.
2. Com saldo indisponível ou insuficiente, o sistema apresenta o impedimento antes ou depois do envio, sem aceitar silenciosamente.
3. O valor informado é validado (mínimo, máximo e formato).
4. O saldo e os indicadores são atualizados após uma solicitação bem-sucedida.
5. A solicitação não é duplicada por cliques repetidos.

### Pontos a confirmar e limites do RF47

O corpo e a resposta da solicitação não foram capturados; não foram confirmados o registro do saque, a regra de saldo e a mensagem de retorno. O saldo indisponível ("R$ --") e a diferença em relação ao cartão Recebimentos são tratados no [RF49](#rf49).

---

<a id="rf48"></a>


## RF48 — Criar cobrança pelo painel Pagar.me

| Campo | Descrição |
| --- | --- |
| Requisito de QA | A criação de cobrança pelo painel Pagar.me deve aceitar descrição, valor e método de pagamento, criar a cobrança e informar o sucesso ao usuário. |
| Ator | Usuário autenticado com acesso ao módulo Pagar.me. |
| Pré-condições | Conta de pagamento configurada; descrição e valor de teste autorizados. |
| Gatilho | Acionar Nova cobrança, informar descrição, valor e método e acionar Criar Cobrança. |
| Caso | [CT-RF48](Cenario_Teste/CT-RF48_Criacao_Cobranca_PagarMe.md) |
| Situação observada | Aprovado conforme a gravação. `POST criar-cobranca` retorna HTTP 200 e o sistema apresenta "Cobrança criada com sucesso!". |
| Defeito | Nenhum no fluxo avaliado |
| Evidências | [Jam](https://jam.dev/c/e6e551ef-9196-4c79-b6a2-89747b1e8b33) e [Evidências](Evidencias/CT-RF43_Criacao_Cobranca_PagarMe/README.md). |

### Critérios de aceitação do RF48

1. O formulário permite informar descrição, valor e método de pagamento.
2. A criação retorna sucesso e a interface apresenta mensagem compreensível.
3. A cobrança passa a constar nos registros do módulo (por exemplo, Transações recentes) conforme a regra do produto.
4. Dados inválidos ou ausentes recebem validação específica.
5. A cobrança não é duplicada por cliques repetidos.

### Pontos a confirmar e limites do RF48

Não foram verificados a presença da cobrança nos registros, o link gerado, outros métodos, valores inválidos e duplicidade; corpo e resposta da requisição não foram capturados.

---

<a id="rf117"></a>


## RF49 — Atualizar Recebimentos e gráfico conforme o período

| Campo | Descrição |
| --- | --- |
| Requisito de QA | O painel Pagar.me deve apresentar Recebimentos, variação, gráfico e meios de pagamento correspondentes ao período selecionado, com indicadores de saldo coerentes ou com indicação explícita de indisponibilidade. |
| Ator | Usuário autenticado com acesso ao módulo Pagar.me. |
| Pré-condições | Conta de pagamento com movimentação conhecida; regra de apuração dos indicadores definida com o produto. |
| Gatilho | Selecionar outro período no cartão Recebimentos. |
| Caso | [CT-RF49](Cenario_Teste/CT-RF49_Painel_PagarMe_Periodo.md) |
| Situação observada | Reprovado nas evidências. Com "Últimos 7 dias", Recebimentos permanece R$ 38.420,00 e o gráfico é idêntico ao de "Últimos 30 dias"; os indicadores de saldo permanecem "R$ --". |
| Defeito | [BUG-021](Relatorio-de-Bugs.md#bug-021), em triagem |
| Evidências | [Jam](https://jam.dev/c/e6e551ef-9196-4c79-b6a2-89747b1e8b33) e [Evidências](Evidencias/CT-RF45_Painel_PagarMe_Periodo/README.md). |

### Critérios de aceitação do RF49

1. O seletor de período atualiza o valor de Recebimentos, a variação, o gráfico e o eixo de datas.
2. O eixo do gráfico apresenta datas compatíveis com o período selecionado e com a data atual.
3. Os meios de pagamento correspondem ao período e ao total apresentado.
4. Os indicadores de saldo apresentam valores quando a conta tem saldo, ou mensagem explícita de indisponibilidade.
5. Valores de demonstração, se existirem, são identificados como tal.

### Pontos a confirmar e limites do RF49

Não foi confirmado se o painel usa dados reais ou de demonstração; o clique no seletor não consta na cronologia e a leitura do eixo de datas é aproximada. Os corpos das requisições não foram capturados.

---

<a id="rf50"></a>


## RF50 — Filtrar despesas fixas por código e por nome

| Campo | Descrição |
| --- | --- |
| Requisito de QA | A busca da tela Despesas Fixas deve apresentar apenas as despesas que atendam aos critérios de código e de nome informados, com o Valor Listado correspondente ao conjunto exibido e restauração da listagem completa ao limpar os critérios. |
| Ator | Usuário autenticado com acesso a Despesas Fixas. |
| Pré-condições | Base conhecida, com códigos, nomes, status e recorrências registrados. |
| Gatilho | Informar código ou nome e, depois, limpar os critérios. |
| Caso | [CT-RF50](Cenario_Teste/CT-RF50_Filtros_Despesas_Fixas.md) |
| Situação observada | Aprovado conforme a gravação. O filtro por código "1" lista os códigos 10 a 19 e o filtro por nome "Teste" retorna #5 e #7, com Valor Listado acompanhando o conjunto; os campos limpos restauram a listagem completa. |
| Defeito | Nenhum no fluxo avaliado |
| Evidências | [Jam](https://jam.dev/c/a4bac99d-e436-4792-831e-8c3a875272bb) e [Evidências](Evidencias/CT-RF46_Filtros_Despesas_Fixas/README.md). |

### Critérios de aceitação do RF50

1. O filtro por código retorna as despesas cujo código corresponde ao critério.
2. O filtro por nome retorna as despesas cujo nome contém o critério, sem diferenciar maiúsculas de minúsculas.
3. O cartão Valor Listado e o rodapé acompanham o conjunto exibido.
4. A limpeza dos critérios restaura a listagem completa.
5. Combinações sem correspondência apresentam mensagem explícita de resultado vazio.

### Pontos a confirmar e limites do RF50

A combinação de critérios, o resultado vazio, o filtro por Status e Recorrência com valores específicos e a regra de correspondência do código não foram exercitados. Os filtros não geram requisição de rede, compatível com filtragem local, sem confirmação. O contrato dos cartões não foi fornecido, como no [RF15](#rf15) e no [RF32](#rf32).

---

<a id="rf51"></a>


## RF51 — Cadastrar despesa fixa com uma única gravação

| Campo | Descrição |
| --- | --- |
| Requisito de QA | O cadastro de despesa fixa deve criar uma única despesa com os dados informados, atribuir o código, apresentá-la na listagem e atualizar os cartões, sem requisições de criação duplicadas. |
| Ator | Usuário autenticado com acesso a Despesas Fixas. |
| Pré-condições | Quantidade de despesas e códigos registrados; nome de teste disponível. |
| Gatilho | Preencher Nova Despesa e acionar Salvar Despesa. |
| Caso | [CT-RF51](Cenario_Teste/CT-RF51_Cadastro_Despesa_Fixa.md) |
| Situação observada | A validar — regra ou contexto pendente. A despesa de código 23 é criada e a listagem passa de 16 para 17 registros, mas um único clique em Salvar Despesa gera dois `POST cria/despesa-fixa` com HTTP 201. |
| Defeito | Sem defeito confirmado |
| Evidências | [Jam](https://jam.dev/c/a4bac99d-e436-4792-831e-8c3a875272bb) e [Evidências](Evidencias/CT-RF47_Cadastro_Despesa_Fixa/README.md). |

### Critérios de aceitação do RF51

1. Um único clique em Salvar Despesa gera uma única requisição de criação e um único registro.
2. O código é atribuído pelo sistema e não duplica um código existente.
3. A listagem e os cartões de resumo refletem a inclusão.
4. A mensagem de sucesso ou de erro é apresentada ao usuário.
5. A despesa permanece após recarga da página.

### Pontos a confirmar e limites do RF51

O corpo e a resposta da segunda requisição não foram capturados; não foi confirmado se houve registro adicional. A persistência após recarga, a mensagem de confirmação e a regra do código não foram verificadas.

---

<a id="rf52"></a>


## RF52 — Excluir despesa fixa com confirmação

| Campo | Descrição |
| --- | --- |
| Requisito de QA | A exclusão de despesa fixa deve pedir confirmação, excluir a despesa permitida, remover o registro da listagem e atualizar os cartões de resumo. |
| Ator | Usuário autenticado com permissão para excluir despesas fixas. |
| Pré-condições | Despesa de teste e cartões registrados antes da exclusão. |
| Gatilho | Acionar a lixeira da despesa e confirmar no diálogo. |
| Caso | [CT-RF52](Cenario_Teste/CT-RF52_Exclusao_Despesa_Fixa.md) |
| Situação observada | Aprovado conforme a gravação. O diálogo "Deseja excluir a despesa fixa?" é confirmado, `POST deleta/despesa-fixa` retorna HTTP 200 e a listagem passa de 17 para 16 despesas. |
| Defeito | Nenhum no fluxo avaliado |
| Evidências | [Jam](https://jam.dev/c/a4bac99d-e436-4792-831e-8c3a875272bb) e [Evidências](Evidencias/CT-RF48_Exclusao_Despesa_Fixa/README.md). |

### Critérios de aceitação do RF52

1. A ação de exclusão apresenta confirmação explícita antes de efetivar a operação.
2. A exclusão permitida remove o registro da listagem e atualiza os cartões.
3. A resposta informa sucesso e o resultado se mantém após recarga da página.
4. Cancelar no diálogo preserva o registro.
5. Despesas com vínculo impeditivo recebem mensagem específica, sem erro interno.

### Pontos a confirmar e limites do RF52

A persistência após recarga, a natureza da exclusão (física ou lógica), Cancelar e a exclusão com vínculos não foram exercitados.

---

<a id="rf53"></a>


## RF53 — Editar despesa fixa preservando o registro

| Campo | Descrição |
| --- | --- |
| Requisito de QA | A edição de despesa fixa deve abrir o formulário com os dados da despesa, atualizar a mesma despesa ao salvar, apresentar a alteração na listagem e não criar registro adicional. |
| Ator | Usuário autenticado com permissão para editar despesas fixas. |
| Pré-condições | Despesa de teste com todos os campos registrados antes da edição. |
| Gatilho | Abrir a despesa, alterar a recorrência e acionar Salvar Despesa. |
| Caso | [CT-RF53](Cenario_Teste/CT-RF53_Edicao_Despesa_Fixa.md) |
| Situação observada | Aprovado conforme a gravação. `POST edita/despesa-fixa` (despesa 7, recorrência "7 dias") retorna HTTP 200 e a listagem apresenta "7 Dias" sem alterar a quantidade de despesas. |
| Defeito | Nenhum no fluxo avaliado |
| Evidências | [Jam](https://jam.dev/c/a4bac99d-e436-4792-831e-8c3a875272bb) e [Evidências](Evidencias/CT-RF49_Edicao_Despesa_Fixa/README.md). |

### Critérios de aceitação do RF53

1. O formulário de edição é preenchido com todos os dados da despesa, incluindo a recorrência.
2. Salvar atualiza a mesma despesa, sem criar registro adicional.
3. A listagem apresenta a nova recorrência e os cartões permanecem coerentes.
4. A alteração permanece após recarga da página.
5. Cancelar descarta as alterações.

### Pontos a confirmar e limites do RF53

A persistência após recarga, o pré-preenchimento da recorrência (o quadro de 0:48 mostra o seletor sem valor visível, enquanto a resposta traz "1 Mês"), a mensagem de confirmação e a edição de outros campos não foram verificados.

---

<a id="rf54"></a>


## RF54 — Gerar o relatório de Matrículas em PDF

| Campo | Descrição |
| --- | --- |
| Requisito de QA | A geração do relatório de Matrículas deve produzir um PDF válido com as matrículas do período e dos filtros informados, com valor e quantidade de registros coerentes. |
| Ator | Usuário autenticado com permissão para gerar relatórios. |
| Pré-condições | Matrículas do período conhecidas. |
| Gatilho | Selecionar "Matrículas", informar o período e acionar Gerar Relatório. |
| Caso | [CT-RF54](Cenario_Teste/CT-RF54_Relatorio_Matriculas.md) |
| Situação observada | Aprovado conforme o PDF. O relatório abre e apresenta uma matrícula (Plano Diário, R$ 20,00) com "Quantidade de registros: 1". |
| Defeito | Nenhum no fluxo avaliado |
| Evidências | [Jam](https://jam.dev/c/3b4777a4-e1b0-4038-9b06-26c73669d7d1) e [Evidências](Evidencias/CT-RF50_Relatorio_Matriculas/README.md). |

### Critérios de aceitação do RF54

1. O PDF abre e apresenta cabeçalho, período e colunas do relatório.
2. Os registros correspondem às matrículas do período e aos filtros informados.
3. O valor e a quantidade de registros são coerentes com as linhas.
4. Sem matrículas no período, o relatório apresenta a estrutura vazia explícita.
5. Os filtros de Plano e de Tipo de Pagto restringem o conteúdo.

### Pontos a confirmar e limites do RF54

O conteúdo não foi conferido com a lista de matrículas do módulo; filtros de plano e de pagamento, mais de um registro e período sem matrículas não foram exercitados.

---

<a id="rf55"></a>


## RF55 — Apresentar o valor a receber no relatório de Contas a Receber

| Campo | Descrição |
| --- | --- |
| Requisito de QA | O relatório de Contas a Receber deve apresentar o valor a receber de cada conta do período e dos filtros informados, com totais coerentes com as linhas. |
| Ator | Usuário autenticado com permissão para gerar relatórios. |
| Pré-condições | Contas a receber pendentes do período conhecidas, com valores. |
| Gatilho | Selecionar "Contas a Receber", Status "Pendente", informar o período e acionar Gerar Relatório. |
| Caso | [CT-RF55](Cenario_Teste/CT-RF55_Relatorio_Contas_Receber.md) |
| Situação observada | Reprovado nas evidências. O PDF lista três contas pendentes, mas a coluna Valor a Receber apresenta "----" em todas as linhas. |
| Defeito | [BUG-022](Relatorio-de-Bugs.md#bug-022), em triagem |
| Evidências | [Jam](https://jam.dev/c/3b4777a4-e1b0-4038-9b06-26c73669d7d1) e [Evidências](Evidencias/CT-RF51_Relatorio_Contas_Receber/README.md). |

### Critérios de aceitação do RF55

1. Cada conta pendente apresenta o valor a receber no relatório.
2. Os totais do relatório correspondem às linhas apresentadas.
3. Os valores coincidem com os do módulo Contas a Receber para as mesmas contas.
4. Rótulos e colunas são legíveis e sem duplicação (por exemplo, "D Vencimento" e "Plano Plano Diário").
5. Sem valor disponível, o relatório apresenta indicação explícita e não um marcador.

### Pontos a confirmar e limites do RF55

Os valores não foram comparados com o módulo Contas a Receber; a opção Detalhado, outros status e o conteúdo da resposta da requisição não foram exercitados. O rótulo "D Vencimento" e a repetição em "Plano Plano Diário" foram observados sem classificação própria.

---

<a id="rf56"></a>


## RF56 — Gerar o relatório de Contas a Pagar (Pagas)

| Campo | Descrição |
| --- | --- |
| Requisito de QA | O relatório de Contas a Pagar (Pagas) deve apresentar as contas pagas do período, com valores bruto e líquido e totalizadores coerentes, ou a estrutura vazia explícita quando não houver pagamentos. |
| Ator | Usuário autenticado com permissão para gerar relatórios. |
| Pré-condições | Contas a pagar pagas do período conhecidas. |
| Gatilho | Selecionar "Contas a Pagar", informar o período e acionar Gerar Relatório. |
| Caso | [CT-RF56](Cenario_Teste/CT-RF56_Relatorio_Contas_Pagar_Pagas.md) |
| Situação observada | A validar — regra ou contexto pendente. O PDF abre com a estrutura do relatório, sem linhas e com totalizadores R$ 0,00, coerente com um período sem contas pagas, a confirmar. |
| Defeito | Sem defeito confirmado |
| Evidências | [Jam](https://jam.dev/c/3b4777a4-e1b0-4038-9b06-26c73669d7d1) e [Evidências](Evidencias/CT-RF52_Relatorio_Contas_Pagar_Pagas/README.md). |

### Critérios de aceitação do RF56

1. O PDF abre e apresenta cabeçalho, período e colunas do relatório.
2. As contas pagas do período aparecem com valores bruto e líquido coerentes com o módulo.
3. Sem contas pagas, o relatório apresenta a estrutura vazia com totalizadores zerados ou mensagem explícita.
4. Os totalizadores correspondem às linhas apresentadas.
5. O título do relatório identifica o filtro aplicado (Pagas).

### Pontos a confirmar e limites do RF56

As contas a pagar do período no módulo não foram conferidas; o comportamento com pagamentos e a regra do escopo do filtro "Pagas" não foram exercitados.

---

<a id="rf57"></a>


## RF57 — Gerar o relatório de Avaliações em PDF

| Campo | Descrição |
| --- | --- |
| Requisito de QA | A geração do relatório de Avaliações deve produzir um PDF válido para o período e os filtros informados, com os registros do período ou a estrutura vazia explícita, e informar falhas ao usuário. |
| Ator | Usuário autenticado com permissão para gerar relatórios. |
| Pré-condições | Período e filtros registrados; base com e sem registros no período conhecida. |
| Gatilho | Selecionar o tipo "Avaliações", informar o período e acionar Gerar Relatório. |
| Caso | [CT-RF57](Cenario_Teste/CT-RF57_Relatorio_Avaliacoes_Vazio.md) |
| Situação observada | Reprovado nas evidências. A requisição retorna HTTP 200, mas o arquivo baixado tem 0 bytes e não abre; nenhuma mensagem de erro foi observada. O defeito é compartilhado com os relatórios de Avaliações, Clientes, Colaboradores e Caixas. |
| Defeito | [BUG-023](Relatorio-de-Bugs.md#bug-023), em triagem |
| Evidências | [Jam](https://jam.dev/c/3b4777a4-e1b0-4038-9b06-26c73669d7d1) e [Evidências](Evidencias/CT-RF53_Relatorio_Avaliacoes_Vazio/README.md). |

### Critérios de aceitação do RF57

1. O arquivo gerado é um PDF válido, com tamanho maior que zero, que abre no visualizador.
2. O relatório apresenta cabeçalho, período, filtros e registros do período.
3. Sem registros, o relatório apresenta a estrutura com totais zerados ou mensagem explícita, sem arquivo vazio.
4. Falhas de geração são informadas ao usuário, sem resposta HTTP 200 com arquivo vazio.
5. O nome e o tipo do arquivo correspondem ao relatório solicitado.

### Pontos a confirmar e limites do RF57

O conteúdo das respostas e a causa não foram capturados. A correspondência entre o arquivo e o tipo é inferida pela ordem dos downloads e dos tipos selecionados no vídeo.

---

<a id="rf58"></a>


## RF58 — Gerar o relatório de Clientes em PDF

| Campo | Descrição |
| --- | --- |
| Requisito de QA | A geração do relatório de Clientes deve produzir um PDF válido para o período e os filtros informados, com os registros do período ou a estrutura vazia explícita, e informar falhas ao usuário. |
| Ator | Usuário autenticado com permissão para gerar relatórios. |
| Pré-condições | Período e filtros registrados; base com e sem registros no período conhecida. |
| Gatilho | Selecionar o tipo "Clientes", informar o período e acionar Gerar Relatório. |
| Caso | [CT-RF58](Cenario_Teste/CT-RF58_Relatorio_Clientes_Vazio.md) |
| Situação observada | Reprovado nas evidências. A requisição retorna HTTP 200, mas o arquivo baixado tem 0 bytes e não abre; nenhuma mensagem de erro foi observada. O defeito é compartilhado com os relatórios de Avaliações, Clientes, Colaboradores e Caixas. |
| Defeito | [BUG-023](Relatorio-de-Bugs.md#bug-023), em triagem |
| Evidências | [Jam](https://jam.dev/c/3b4777a4-e1b0-4038-9b06-26c73669d7d1) e [Evidências](Evidencias/CT-RF54_Relatorio_Clientes_Vazio/README.md). |

### Critérios de aceitação do RF58

1. O arquivo gerado é um PDF válido, com tamanho maior que zero, que abre no visualizador.
2. O relatório apresenta cabeçalho, período, filtros e registros do período.
3. Sem registros, o relatório apresenta a estrutura com totais zerados ou mensagem explícita, sem arquivo vazio.
4. Falhas de geração são informadas ao usuário, sem resposta HTTP 200 com arquivo vazio.
5. O nome e o tipo do arquivo correspondem ao relatório solicitado.

### Pontos a confirmar e limites do RF58

O conteúdo das respostas e a causa não foram capturados. A correspondência entre o arquivo e o tipo é inferida pela ordem dos downloads e dos tipos selecionados no vídeo.

---

<a id="rf59"></a>


## RF59 — Gerar o relatório de Colaboradores em PDF

| Campo | Descrição |
| --- | --- |
| Requisito de QA | A geração do relatório de Colaboradores deve produzir um PDF válido para o período e os filtros informados, com os registros do período ou a estrutura vazia explícita, e informar falhas ao usuário. |
| Ator | Usuário autenticado com permissão para gerar relatórios. |
| Pré-condições | Período e filtros registrados; base com e sem registros no período conhecida. |
| Gatilho | Selecionar o tipo "Colaboradores", informar o período e acionar Gerar Relatório. |
| Caso | [CT-RF59](Cenario_Teste/CT-RF59_Relatorio_Colaboradores_Vazio.md) |
| Situação observada | Reprovado nas evidências. A requisição retorna HTTP 200, mas o arquivo baixado tem 0 bytes e não abre; nenhuma mensagem de erro foi observada. O defeito é compartilhado com os relatórios de Avaliações, Clientes, Colaboradores e Caixas. |
| Defeito | [BUG-023](Relatorio-de-Bugs.md#bug-023), em triagem |
| Evidências | [Jam](https://jam.dev/c/3b4777a4-e1b0-4038-9b06-26c73669d7d1) e [Evidências](Evidencias/CT-RF55_Relatorio_Colaboradores_Vazio/README.md). |

### Critérios de aceitação do RF59

1. O arquivo gerado é um PDF válido, com tamanho maior que zero, que abre no visualizador.
2. O relatório apresenta cabeçalho, período, filtros e registros do período.
3. Sem registros, o relatório apresenta a estrutura com totais zerados ou mensagem explícita, sem arquivo vazio.
4. Falhas de geração são informadas ao usuário, sem resposta HTTP 200 com arquivo vazio.
5. O nome e o tipo do arquivo correspondem ao relatório solicitado.

### Pontos a confirmar e limites do RF59

O conteúdo das respostas e a causa não foram capturados. A correspondência entre o arquivo e o tipo é inferida pela ordem dos downloads e dos tipos selecionados no vídeo.

---

<a id="rf60"></a>


## RF60 — Gerar o relatório de Caixas em PDF

| Campo | Descrição |
| --- | --- |
| Requisito de QA | A geração do relatório de Caixas deve produzir um PDF válido para o período e os filtros informados, com os registros do período ou a estrutura vazia explícita, e informar falhas ao usuário. |
| Ator | Usuário autenticado com permissão para gerar relatórios. |
| Pré-condições | Período e filtros registrados; base com e sem registros no período conhecida. |
| Gatilho | Selecionar o tipo "Caixas", informar o período e acionar Gerar Relatório. |
| Caso | [CT-RF60](Cenario_Teste/CT-RF60_Relatorio_Caixas_Vazio.md) |
| Situação observada | Reprovado nas evidências. A requisição retorna HTTP 200, mas o arquivo baixado tem 0 bytes e não abre; nenhuma mensagem de erro foi observada. O defeito é compartilhado com os relatórios de Avaliações, Clientes, Colaboradores e Caixas. |
| Defeito | [BUG-023](Relatorio-de-Bugs.md#bug-023), em triagem |
| Evidências | [Jam](https://jam.dev/c/3b4777a4-e1b0-4038-9b06-26c73669d7d1) e [Evidências](Evidencias/CT-RF56_Relatorio_Caixas_Vazio/README.md). |

### Critérios de aceitação do RF60

1. O arquivo gerado é um PDF válido, com tamanho maior que zero, que abre no visualizador.
2. O relatório apresenta cabeçalho, período, filtros e registros do período.
3. Sem registros, o relatório apresenta a estrutura com totais zerados ou mensagem explícita, sem arquivo vazio.
4. Falhas de geração são informadas ao usuário, sem resposta HTTP 200 com arquivo vazio.
5. O nome e o tipo do arquivo correspondem ao relatório solicitado.

### Pontos a confirmar e limites do RF60

O conteúdo das respostas e a causa não foram capturados. A correspondência entre o arquivo e o tipo é inferida pela ordem dos downloads e dos tipos selecionados no vídeo.

---


## RF61 — Alternar entre os temas claro e escuro na Prospecção

| Campo | Descrição |
| --- | --- |
| Requisito funcional | A tela deve acompanhar a seleção de tema, mantendo os dados da listagem. |
| Ator | Usuário autenticado com acesso a Prospecção. |
| Pré-condição | Sessão autenticada com acesso à Prospecção e controle de tema disponível. Listagem de leads carregada antes da alternância. |
| Comportamento esperado | A tela deve acompanhar a seleção de tema, mantendo os dados da listagem. |
| Situação observada | A gravação mostra a tela passando de escura para clara e retornando ao tema escuro. A listagem permanece visível. |
| Prioridade | Média, proposta. |
| Rastreabilidade | [CT-RF61](Cenario_Teste/CT-RF61_Temas_Prospeccao.md) · — · [Evidências](Evidencias/CT-RF74_Temas_Prospeccao/README.md) · [Jam](https://jam.dev/c/5dc9fc15-8e13-4f90-b21f-a49aedc6731e) |

### Critérios de aceitação do RF61

1. Claro e Escuro são aplicados na sequência escolhida.
2. A listagem mantém os mesmos leads e dados durante a alternância.
3. No reteste, recarregar a página para avaliar separadamente a persistência da preferência.

### Base da análise e limites do RF61

Aprovado conforme o resumo da gravação. Classificação restrita à alternância visível nesta tela; a gravação não demonstra persistência após recarregar nem uma auditoria de contraste.
Análise da gravação e dos eventos capturados no Jam; não foi executado um novo teste no sistema.

Encaminhamento: Repetir a alternância com listagem conhecida; verificar persistência após recarga em execução complementar.

<a id="rf73"></a>


## RF62 — Alternar o tema e consultar as notificações no cabeçalho

| Campo | Descrição |
| --- | --- |
| Requisito de QA | O cabeçalho da tela Prospecção deve permitir alternar o tema claro e escuro, gravando a escolha do usuário, e abrir o painel de notificações com o estado correspondente às pendências. |
| Ator | Usuário autenticado com acesso a Prospecção. |
| Pré-condições | Sessão autenticada; tema inicial e notificações conhecidos. |
| Gatilho | Acionar o alternador de tema e o sino do cabeçalho. |
| Caso | [CT-RF62](Cenario_Teste/CT-RF62_Tema_Notificacoes_Prospeccao.md) |
| Situação observada | Aprovado conforme a gravação. O tema escuro é aplicado e o claro restaurado, com POST usuario/tema (HTTP 200) a cada troca; o painel de Notificações abre sem pendências. |
| Defeito | Nenhum no fluxo avaliado |
| Evidências | [Jam](https://jam.dev/c/308607ff-8abc-40af-8c7c-429ce506ed64) e [Evidências](Evidencias/CT-RF85_Tema_Notificacoes_Prospeccao/README.md). |

### Critérios de aceitação do RF62

1. Cada acionamento do alternador troca o tema da interface sem perda de legibilidade.
2. Cada troca de tema é gravada no servidor e permanece após recarregar a página.
3. O sino abre o painel de Notificações com as abas Tudo e Não lidas.
4. Sem pendências, o painel apresenta mensagem explícita de estado vazio.
5. Com pendências, o painel lista os itens e permite marcá-los como lidos.

### Pontos a confirmar e limites do RF62

A persistência do tema após recarga, as notificações pendentes e a ação Marcar como lidas não foram exercitadas; o contraste do tema escuro é tratado no [RF41](#rf41).

---

<a id="rf63"></a>


## RF63 — Buscar leads por texto na listagem de Prospecção

| Campo | Descrição |
| --- | --- |
| Requisito de QA | O campo Buscar lead deve filtrar a listagem por nome, e-mail, telefone ou código, apresentando apenas os leads correspondentes e restaurando a listagem completa ao limpar o termo. |
| Ator | Usuário autenticado com acesso a Prospecção. |
| Pré-condições | Base de leads conhecida, com nomes, contatos e códigos registrados. |
| Gatilho | Digitar um termo no campo Buscar lead e, depois, apagá-lo. |
| Caso | [CT-RF63](Cenario_Teste/CT-RF63_Busca_Leads_Prospeccao.md) |
| Situação observada | Aprovado conforme a gravação. A busca retorna os leads de códigos 3 e 7 em 0:12 e os leads 4 e 10 para "tes" em 0:44; o campo vazio restaura a listagem completa. |
| Defeito | Nenhum no fluxo avaliado |
| Evidências | [Jam](https://jam.dev/c/308607ff-8abc-40af-8c7c-429ce506ed64) e [Evidências](Evidencias/CT-RF86_Busca_Leads_Prospeccao/README.md). |

### Critérios de aceitação do RF63

1. O campo Buscar lead filtra por nome, e-mail, telefone e código conforme o rótulo do campo.
2. A busca não diferencia maiúsculas de minúsculas.
3. Os cartões acompanham ou não o filtro de acordo com o contrato definido.
4. Ao apagar o termo, a listagem completa é restaurada.
5. Um termo sem correspondência apresenta mensagem explícita de resultado vazio.

### Pontos a confirmar e limites do RF63

O termo vigente em 0:12 não foi identificado com certeza; a regra de correspondência, a busca por e-mail, telefone e código e o resultado vazio não foram exercitados. A busca não gera requisição de rede, compatível com filtragem local, sem confirmação. O contrato dos cartões não foi fornecido, como no [RF15](#rf15).

---

<a id="rf64"></a>


## RF64 — Filtrar leads por estágio e restaurar a listagem

| Campo | Descrição |
| --- | --- |
| Requisito de QA | O seletor Estágio deve apresentar apenas os leads do estágio escolhido e o botão Limpar deve restaurar o seletor e a listagem completa. |
| Ator | Usuário autenticado com acesso a Prospecção. |
| Pré-condições | Base de leads conhecida, com estágios registrados. |
| Gatilho | Selecionar um estágio e, depois, acionar Limpar. |
| Caso | [CT-RF64](Cenario_Teste/CT-RF64_Filtro_Estagio_Leads.md) |
| Situação observada | Aprovado conforme a gravação. "Novo Contato" apresenta os leads 7 e 8 e "Proposta" o lead 4; Limpar restaura a listagem completa. |
| Defeito | Nenhum no fluxo avaliado |
| Evidências | [Jam](https://jam.dev/c/308607ff-8abc-40af-8c7c-429ce506ed64) e [Evidências](Evidencias/CT-RF87_Filtro_Estagio_Leads/README.md). |

### Critérios de aceitação do RF64

1. Cada estágio apresenta apenas os leads desse estágio.
2. O número de linhas de um estágio coincide com o indicador correspondente, quando existir.
3. O botão Limpar restaura o seletor para Todos e a listagem completa.
4. Um estágio sem leads apresenta mensagem explícita de resultado vazio.
5. O filtro combina corretamente com a busca por texto.

### Pontos a confirmar e limites do RF64

Os demais estágios, a combinação com a busca por texto, o estágio sem leads e a lista completa de estágios do seletor não foram exercitados. O filtro não gera requisição de rede, compatível com filtragem local, sem confirmação.

---

<a id="rf71"></a>


## RF65 — Cadastrar lead no estágio Novo Contato

| Campo | Descrição |
| --- | --- |
| Requisito funcional | O lead deve ser criado no estágio Novo Contato e aparecer na listagem. |
| Ator | Usuário autenticado com acesso a Prospecção. |
| Pré-condição | Sessão autenticada com permissão para adicionar leads. Dados de contato de teste disponíveis e estágio Novo Contato selecionável. |
| Comportamento esperado | O lead deve ser criado no estágio Novo Contato e aparecer na listagem. |
| Situação observada | O lead de teste é criado com o estágio NOVO_CONTATO, recebe código 11 e aparece na listagem. O total passa de 6 para 7, e o indicador Novo Contato passa de 2 para 3. |
| Prioridade | Média, proposta. |
| Rastreabilidade | [CT-RF65](Cenario_Teste/CT-RF65_Cadastro_Lead_Novo_Contato.md) · — · [Evidências](Evidencias/CT-RF77_Cadastro_Lead_Novo_Contato/README.md) · [Jam](https://jam.dev/c/29447c6a-90f5-48b2-ac5d-d43cad44a782) |

### Critérios de aceitação do RF65

1. A seleção final envia o estágio NOVO_CONTATO.
2. O cadastro retorna um código e inclui o lead na listagem.
3. O total e o indicador Novo Contato aumentam em um.
4. Em execução complementar, reabrir o cadastro para conferir todos os campos.

### Base da análise e limites do RF65

Aprovado conforme o resumo da gravação. A classificação considera o cadastro mostrado; não houve reabertura do registro para revisar todos os campos.
Análise da gravação e dos eventos capturados no Jam; não foi executado um novo teste no sistema.

Encaminhamento: Repetir o cadastro e conferir campos e estágio após reabertura.

<a id="rf66"></a>


## RF66 — Cadastrar lead no estágio Interessado

| Campo | Descrição |
| --- | --- |
| Requisito funcional | O lead deve ser criado no estágio Interessado e aparecer na listagem. |
| Ator | Usuário autenticado com acesso a Prospecção. |
| Pré-condição | Sessão autenticada com permissão para adicionar leads. Dados de contato de teste disponíveis e estágio Interessado selecionável. |
| Comportamento esperado | O lead deve ser criado no estágio Interessado e aparecer na listagem. |
| Situação observada | O cadastro retorna código 12 e o lead aparece na listagem com a identificação Interessado. |
| Prioridade | Média, proposta. |
| Rastreabilidade | [CT-RF66](Cenario_Teste/CT-RF66_Cadastro_Lead_Interessado.md) · — · [Evidências](Evidencias/CT-RF78_Cadastro_Lead_Interessado/README.md) · [Jam](https://jam.dev/c/f8735cbf-4043-4467-b43f-3cad7eff0da8) |

### Critérios de aceitação do RF66

1. O envio utiliza o estágio INTERESSADO.
2. O cadastro retorna um código e o lead é listado como Interessado.
3. Em execução complementar, reabrir o registro para conferir os campos salvos.

### Base da análise e limites do RF66

Aprovado conforme o resumo da gravação. A gravação não demonstra reabertura ou alteração posterior do registro.
Análise da gravação e dos eventos capturados no Jam; não foi executado um novo teste no sistema.

Encaminhamento: Repetir o cadastro e conferir os dados após reabertura.

<a id="rf67"></a>


## RF67 — Cadastrar lead no estágio Fez Aula Experimental

| Campo | Descrição |
| --- | --- |
| Requisito funcional | O lead deve ser criado com o estágio Fez Aula Experimental e aparecer na listagem. |
| Ator | Usuário autenticado com acesso a Prospecção. |
| Pré-condição | Sessão autenticada com permissão para adicionar leads. Dados de contato de teste disponíveis e estágio Fez Aula Experimental selecionável. |
| Comportamento esperado | O lead deve ser criado com o estágio Fez Aula Experimental e aparecer na listagem. |
| Situação observada | O lead é criado com código 14 e estágio FEZ_AULA_EXP. A linha correspondente aparece ao final, e o total de leads passa de 9 para 10. |
| Prioridade | Média, proposta. |
| Rastreabilidade | [CT-RF67](Cenario_Teste/CT-RF67_Cadastro_Lead_Aula_Experimental.md) · — · [Evidências](Evidencias/CT-RF79_Cadastro_Lead_Aula_Experimental/README.md) · [Jam](https://jam.dev/c/bef3d877-056b-4274-87c3-da37869c54fd) |

### Critérios de aceitação do RF67

1. O cadastro utiliza o estágio FEZ_AULA_EXP.
2. O novo lead aparece na listagem com o estágio escolhido.
3. O total de leads aumenta em um.
4. Em execução complementar, reabrir o registro para conferir os campos salvos.

### Base da análise e limites do RF67

Aprovado conforme o resumo da gravação. A gravação valida o cadastro no estágio indicado; não demonstra agendamento ou realização de uma aula.
Análise da gravação e dos eventos capturados no Jam; não foi executado um novo teste no sistema.

Encaminhamento: Repetir o cadastro e conferir estágio, total e dados após reabertura.

<a id="rf68"></a>


## RF68 — Cadastrar lead no estágio Proposta

| Campo | Descrição |
| --- | --- |
| Requisito funcional | O lead deve ser criado no estágio Proposta e aparecer na listagem. |
| Ator | Usuário autenticado com acesso a Prospecção. |
| Pré-condição | Sessão autenticada com permissão para adicionar leads. Dados de contato de teste disponíveis e estágio Proposta selecionável. |
| Comportamento esperado | O lead deve ser criado no estágio Proposta e aparecer na listagem. |
| Situação observada | O cadastro retorna código 15 e o registro aparece na listagem com estágio Proposta. O total de leads passa de 10 para 11. |
| Prioridade | Média, proposta. |
| Rastreabilidade | [CT-RF68](Cenario_Teste/CT-RF68_Cadastro_Lead_Proposta.md) · — · [Evidências](Evidencias/CT-RF80_Cadastro_Lead_Proposta/README.md) · [Jam](https://jam.dev/c/84f94285-ae5f-4f95-b640-a9b107565aa6) |

### Critérios de aceitação do RF68

1. O envio utiliza o estágio PROPOSTA.
2. O cadastro retorna um código e o lead é listado como Proposta.
3. O total de leads aumenta em um.
4. Em execução complementar, reabrir o registro para conferir os campos salvos.

### Base da análise e limites do RF68

Aprovado conforme o resumo da gravação. O teste demonstra a classificação do lead no estágio Proposta; não demonstra emissão de proposta comercial.
Análise da gravação e dos eventos capturados no Jam; não foi executado um novo teste no sistema.

Encaminhamento: Repetir o cadastro e conferir estágio e dados após reabertura.

<a id="rf89"></a>


## RF69 — Validar cadastro de lead preenchendo apenas o nome

| Campo | Descrição |
| --- | --- |
| Requisito funcional | Segundo o cenário identificado como bug pelo autor, o cadastro incompleto deveria ser bloqueado e os campos obrigatórios deveriam ser indicados. |
| Ator | Usuário autenticado com acesso a Prospecção. |
| Pré-condição | Sessão autenticada com permissão para adicionar leads. Para concluir o reteste, confirmar com o produto quais campos são obrigatórios além do nome; essa regra não acompanha a evidência. |
| Comportamento esperado | Segundo o cenário identificado como bug pelo autor, o cadastro incompleto deveria ser bloqueado e os campos obrigatórios deveriam ser indicados. |
| Situação observada | O sistema aceita o envio sem bloqueio visível, cria o lead de código 19 e atualiza a listagem. O total de leads passa de 14 para 15. |
| Prioridade | Alta, proposta. |
| Rastreabilidade | [CT-RF69](Cenario_Teste/CT-RF69_Cadastro_Lead_Apenas_Nome.md) · [BUG-037](Relatorio-de-Bugs.md#bug-037) · [Evidências](Evidencias/CT-RF83_Cadastro_Lead_Apenas_Nome/README.md) · [Jam](https://jam.dev/c/ef3df03c-16ce-4cb6-b0c7-d04514cab4f6) |

### Critérios de aceitação do RF69

1. Produto confirma e documenta os campos obrigatórios para o cadastro.
2. Se a regra exigir dados além do nome, o envio incompleto é bloqueado e cada campo faltante é indicado.
3. A validação confirmada é aplicada também no servidor, sem criar registro inválido.
4. Um envio completo conforme a regra permite cadastrar o lead.
5. Se apenas o nome for suficiente pela regra aprovada, reclassificar o caso e encerrar o relato como comportamento esperado.

### Base da análise e limites do RF69

Reprovado conforme o relato; regra de obrigatoriedade a confirmar. A classificação de erro acompanha o título do Jam. A regra formal dos campos obrigatórios não foi fornecida; é necessário validá-la para definir exatamente quais campos devem impedir o cadastro. O e-mail está mascarado nos dados de rede, e sua ausência foi avaliada visualmente.
Análise da gravação e dos eventos capturados no Jam; não foi executado um novo teste no sistema.

Encaminhamento: Confirmar obrigatoriedade com produto antes de definir correção; testar campos isolados, envio completo e ausência de criação inválida.

<a id="rf70"></a>


## RF70 — Cadastrar lead no estágio Fechado

| Campo | Descrição |
| --- | --- |
| Requisito funcional | O lead deve ser criado no estágio Fechado e aparecer na listagem. |
| Ator | Usuário autenticado com acesso a Prospecção. |
| Pré-condição | Sessão autenticada com permissão para adicionar leads. Dados de contato de teste disponíveis e estágio Fechado selecionável. |
| Comportamento esperado | O lead deve ser criado no estágio Fechado e aparecer na listagem. |
| Situação observada | A janela fecha após salvar, o total de leads passa de 12 para 13 e o registro testeFechado aparece com código 17 e identificação Fechado. |
| Prioridade | Média, proposta. |
| Rastreabilidade | [CT-RF70](Cenario_Teste/CT-RF70_Cadastro_Lead_Fechado.md) · — · [Evidências](Evidencias/CT-RF84_Cadastro_Lead_Fechado/README.md) · [Jam](https://jam.dev/c/775b9003-fdf7-4ad5-8882-15ba606b6674) |

### Critérios de aceitação do RF70

1. O estágio selecionado é FECHADO.
2. Salvar fecha a janela e inclui o lead com identificação Fechado.
3. O total de leads aumenta em um.
4. Em execução complementar, reabrir o cadastro para conferir todos os campos.

### Base da análise e limites do RF70

Aprovado conforme o resumo da gravação. O corpo da resposta de salvamento não está disponível no evento consultado; o resultado é sustentado pelo retorno HTTP e pelo registro visível na listagem.
Análise da gravação e dos eventos capturados no Jam; não foi executado um novo teste no sistema.

Encaminhamento: Repetir o cadastro e conferir os dados após reabertura; capturar o corpo da resposta de salvamento.

### Base da análise e integração — RF61 a RF70

Integração documental dos arquivos RESUMO.txt fornecidos em `C:\Users\Leonardo\Desktop\evidencias`, com data de gravação e análise informada de 16/11/2026. Os Jams não foram reabertos nesta integração; eventos de rede, horários e quadros abaixo são transcritos dos resumos, sem verificação independente. Não houve nova execução do SIFIT, reteste, consulta ao banco, logs ou código.

CT-RF61–CT-RF70 acrescentam oito aprovações e três reprovações conforme os resumos fornecidos, com BUG-035–BUG-037 em triagem. CT-RF69 mantém a classificação do relato, condicionada à confirmação da regra de obrigatoriedade. Os dez casos anteriores a validar permanecem inalterados.

A análise passa a cobrir 80 requisitos documentados.

---

<a id="rf62"></a>


## RF71 — Cadastrar um lead com uma única gravação

| Campo | Descrição |
| --- | --- |
| Requisito de QA | O formulário Adicionar Lead deve criar o lead informado uma única vez, apresentá-lo na listagem com o estágio escolhido e atualizar os cartões de resumo. |
| Ator | Usuário autenticado com acesso a Prospecção. |
| Pré-condições | Base de leads conhecida; dados de teste descartáveis. |
| Gatilho | Preencher o formulário Adicionar Lead e acionar Salvar Lead. |
| Caso | [CT-RF71](Cenario_Teste/CT-RF71_Cadastro_Lead_Prospeccao.md) |
| Situação observada | A validar — regra ou contexto pendente. O lead de código 10 é criado e listado (Leads 7 → 8), mas um clique gera dois POST salvar-lead/1 com HTTP 200. |
| Defeito | Sem defeito confirmado |
| Evidências | [Jam](https://jam.dev/c/308607ff-8abc-40af-8c7c-429ce506ed64) e [Evidências](Evidencias/CT-RF88_Cadastro_Lead_Prospeccao/README.md). |

### Critérios de aceitação do RF71

1. Um clique em Salvar Lead gera uma única requisição de criação.
2. O lead é gravado uma única vez e aparece na listagem com o estágio informado.
3. Os cartões Leads e do estágio acompanham o novo registro.
4. O botão é protegido contra segundo envio enquanto a requisição está em andamento.
5. Após recarga, a listagem contém um único lead com os dados informados.

### Pontos a confirmar e limites do RF71

O corpo e a resposta da segunda requisição, a persistência após recarga, os campos obrigatórios e as validações de formato não foram verificados. O mesmo padrão ocorre no [RF51](#rf51); a duplicidade não está confirmada.

---

<a id="rf72"></a>


## RF72 — Validar o telefone do lead

| Campo | Descrição |
| --- | --- |
| Requisito de QA | O campo Telefone do formulário de lead deve aceitar apenas valores no formato definido pelo produto (por exemplo, (00) 00000-0000) e rejeitar tamanhos e caracteres inválidos com mensagem clara. |
| Ator | Usuário autenticado com acesso a Prospecção. |
| Pré-condições | Formulário Adicionar Lead aberto; regra do campo definida com o produto. |
| Gatilho | Informar um telefone com 30 dígitos e acionar Salvar Lead. |
| Caso | [CT-RF72](Cenario_Teste/CT-RF72_Telefone_Lead_Sem_Validacao.md) |
| Situação observada | Reprovado nas evidências. O telefone de 30 dígitos é aceito, gravado (lead 10) e devolvido na consulta, sem máscara nem mensagem de validação. |
| Defeito | [BUG-038](Relatorio-de-Bugs.md#bug-038), em triagem |
| Evidências | [Jam](https://jam.dev/c/308607ff-8abc-40af-8c7c-429ce506ed64) e [Evidências](Evidencias/CT-RF89_Telefone_Lead_Sem_Validacao/README.md). |

### Critérios de aceitação do RF72

1. O campo Telefone limita o tamanho e os caracteres ao formato definido pelo produto.
2. Um telefone com tamanho ou caracteres inválidos é rejeitado antes da gravação, com mensagem clara.
3. A máscara exibida no placeholder é aplicada durante a digitação.
4. O servidor valida o telefone independentemente da interface.
5. O telefone válido é gravado e exibido no formato definido.

### Pontos a confirmar e limites do RF72

A regra do campo e a validação no servidor não foram informadas ou verificadas; se o campo for livre, o placeholder "(00) 00000-0000" deve ser revisto. Telefones de outros tamanhos e valores com letras não foram exercitados.

---

<a id="rf75"></a>


## RF73 — Consultar os detalhes de um lead e cancelar a edição

| Campo | Descrição |
| --- | --- |
| Requisito funcional | O sistema deve carregar os dados do lead e fechar a janela ao cancelar, sem enviar uma gravação da alteração. |
| Ator | Usuário autenticado com acesso a Prospecção. |
| Pré-condição | Sessão autenticada com acesso à Prospecção. Lead existente com dados conhecidos; na evidência, código 3. |
| Comportamento esperado | O sistema deve carregar os dados do lead e fechar a janela ao cancelar, sem enviar uma gravação da alteração. |
| Situação observada | Os dados do lead de código 3 são carregados, incluindo estágio Fechado, contato e observação. Após a alteração no telefone, Cancelar fecha a janela e retorna à listagem. Não há chamada de salvamento na linha do tempo. |
| Prioridade | Média, proposta. |
| Rastreabilidade | [CT-RF73](Cenario_Teste/CT-RF73_Detalhes_Lead_Cancelamento.md) · — · [Evidências](Evidencias/CT-RF75_Detalhes_Lead_Cancelamento/README.md) · [Jam](https://jam.dev/c/7ef0ee0b-497e-48b8-a57d-cd914558d303) |

### Critérios de aceitação do RF73

1. A consulta carrega os dados do lead selecionado.
2. Cancelar fecha a janela e retorna à listagem.
3. Cancelar não envia requisição de salvamento.
4. Em execução complementar, reabrir o lead e conferir que o telefone original foi preservado.

### Base da análise e limites do RF73

Aprovado conforme o resumo da gravação. Não houve reabertura do registro para confirmar o valor persistido do telefone. O sucesso se refere à consulta e ao cancelamento observados.
Análise da gravação e dos eventos capturados no Jam; não foi executado um novo teste no sistema.

Encaminhamento: Reabrir o lead após cancelar e comparar o telefone com o valor original.

<a id="rf74"></a>


## RF74 — Excluir leads com confirmação

| Campo | Descrição |
| --- | --- |
| Requisito funcional | Cada confirmação deve excluir o lead selecionado e atualizar a listagem e o total de registros. |
| Ator | Usuário autenticado com acesso a Prospecção. |
| Pré-condição | Sessão autenticada com permissão de exclusão em Prospecção. Dois leads de teste disponíveis para remoção; na evidência, códigos 3 e 4. |
| Comportamento esperado | Cada confirmação deve excluir o lead selecionado e atualizar a listagem e o total de registros. |
| Situação observada | Os leads de códigos 3 e 4 deixam de aparecer após as confirmações. O total exibido diminui de 8 para 7 e depois para 6. |
| Prioridade | Média, proposta. |
| Rastreabilidade | [CT-RF74](Cenario_Teste/CT-RF74_Exclusao_Leads_Confirmacao.md) · — · [Evidências](Evidencias/CT-RF76_Exclusao_Leads_Confirmacao/README.md) · [Jam](https://jam.dev/c/2ac5e5ed-b10f-4cc9-9f97-7ba65ca560f8) |

### Critérios de aceitação do RF74

1. Cada exclusão depende da confirmação do usuário.
2. Cada confirmação remove somente o lead selecionado.
3. A listagem e o total são atualizados após cada exclusão.
4. Em execução complementar, cancelar a confirmação deve preservar o registro.

### Base da análise e limites do RF74

Aprovado conforme o resumo da gravação. As duas exclusões foram agrupadas no mesmo caso porque pertencem ao mesmo cenário na gravação. O cancelamento da confirmação de exclusão não foi testado.
Análise da gravação e dos eventos capturados no Jam; não foi executado um novo teste no sistema.

Encaminhamento: Repetir com registros descartáveis e testar também o cancelamento da confirmação.

<a id="rf65"></a>


## RF75 — Visualizar e editar um lead

| Campo | Descrição |
| --- | --- |
| Requisito de QA | A lupa da listagem deve abrir os dados do lead e permitir a alteração dos campos, gravando a alteração sem erro e refletindo-a na listagem. |
| Ator | Usuário autenticado com acesso a Prospecção. |
| Pré-condições | Lead descartável cadastrado e visível na listagem. |
| Gatilho | Acionar a lupa do lead, alterar o nome e acionar Salvar Lead. |
| Caso | [CT-RF75](Cenario_Teste/CT-RF75_Edicao_Lead_Prospeccao.md) |
| Situação observada | Aprovado conforme a gravação. O modal abre com os dados do lead 10, o nome é atualizado para "testetete" com HTTP 200 e a listagem apresenta o novo nome. |
| Defeito | Nenhum no fluxo avaliado |
| Evidências | [Jam](https://jam.dev/c/308607ff-8abc-40af-8c7c-429ce506ed64) e [Evidências](Evidencias/CT-RF90_Edicao_Lead_Prospeccao/README.md). |

### Critérios de aceitação do RF75

1. A lupa abre o modal com os dados do lead selecionado.
2. A alteração de qualquer campo é enviada ao servidor e gravada sem erro.
3. A listagem reflete o novo valor sem recarga manual.
4. O valor permanece após recarregar a página.
5. O título do modal corresponde à ação disponível (visualizar ou editar).

### Pontos a confirmar e limites do RF75

A edição dos demais campos, a persistência após recarga, os campos obrigatórios e a revisão do título "Visualizar Lead" em um modal editável não foram exercitadas.

---

<a id="rf16"></a>


## RF76 — Alternar o tema e consultar as notificações na tela Planos

| Campo | Descrição |
| --- | --- |
| Requisito de QA | O cabeçalho da tela Planos deve permitir alternar o tema, gravando a escolha, e abrir o painel de notificações com o estado correspondente. |
| Ator | Usuário autenticado com acesso ao módulo. |
| Pré-condições | Sessão autenticada; tema inicial e notificações conhecidos. |
| Gatilho | Acionar o alternador de tema e o sino. |
| Caso | [CT-RF76](Cenario_Teste/CT-RF76_Tema_Notificacoes_Planos.md) |
| Situação observada | Aprovado conforme a gravação. O tema escuro é aplicado e o claro restaurado, com POST usuario/tema (HTTP 200) a cada troca; o painel de Notificações abre sem pendências. |
| Defeito | Nenhum no fluxo avaliado |
| Evidências | [Jam](https://jam.dev/c/233c5d21-e108-4a55-b6f6-8738cb3fc6a6) e [Evidências](Evidencias/CT-RF100_Tema_Notificacoes_Planos/README.md). |

### Critérios de aceitação do RF76

1. Cada acionamento troca o tema sem perda de legibilidade.
2. Cada troca é gravada no servidor e permanece após recarregar.
3. O sino abre o painel de Notificações com as abas Tudo e Não lidas.
4. Sem pendências, o painel apresenta mensagem explícita.
5. Com pendências, o painel lista os itens.

### Pontos a confirmar e limites do RF76

A persistência após recarga e as notificações pendentes não foram exercitadas.

---

<a id="rf78"></a>


## RF77 — Filtrar planos por código e por nome

| Campo | Descrição |
| --- | --- |
| Requisito de QA | A listagem de Planos deve apresentar apenas os planos que atendam aos critérios de código, nome e status e restaurar a listagem completa ao limpar os campos. |
| Ator | Usuário autenticado com acesso ao módulo. |
| Pré-condições | Base de planos conhecida, com códigos, nomes e status registrados. |
| Gatilho | Informar código ou nome e, depois, limpar os campos. |
| Caso | [CT-RF77](Cenario_Teste/CT-RF77_Filtros_Planos.md) |
| Situação observada | Aprovado conforme a gravação. O código "7" lista os planos 37, 7 e 67 e o nome "a" lista planos de nomes aba e Aba; Buscar recarrega a listagem. |
| Defeito | Nenhum no fluxo avaliado |
| Evidências | [Jam](https://jam.dev/c/233c5d21-e108-4a55-b6f6-8738cb3fc6a6) e [Evidências](Evidencias/CT-RF99_Filtros_Planos/README.md). |

### Critérios de aceitação do RF77

1. O filtro por código retorna os planos cujo código contenha o critério.
2. O filtro por nome retorna os planos cujo nome contenha o critério, sem diferenciar maiúsculas.
3. O seletor Status filtra a listagem conforme a opção.
4. Limpar os campos restaura a listagem completa.
5. Critérios sem correspondência apresentam mensagem explícita.

### Pontos a confirmar e limites do RF77

O filtro por Status, a combinação de critérios, o resultado vazio e o contrato dos cartões não foram exercitados.

---

<a id="rf76"></a>


## RF78 — Cadastrar um plano

| Campo | Descrição |
| --- | --- |
| Requisito de QA | O modal Novo Plano deve criar o plano com os dados informados, devolver o identificador e atualizar o contador de planos e a listagem. |
| Ator | Usuário autenticado com acesso ao módulo. |
| Pré-condições | Modal Novo Plano preenchido; base de planos conhecida. |
| Gatilho | Preencher o modal e acionar Salvar Plano. |
| Caso | [CT-RF78](Cenario_Teste/CT-RF78_Cadastro_Plano.md) |
| Situação observada | Aprovado conforme a gravação. `plano/salvar` retorna HTTP 200 com o id 66 e o cartão Planos passa de 40 para 41. |
| Defeito | Nenhum no fluxo avaliado |
| Evidências | [Jam](https://jam.dev/c/233c5d21-e108-4a55-b6f6-8738cb3fc6a6) e [Evidências](Evidencias/CT-RF101_Cadastro_Plano/README.md). |

### Critérios de aceitação do RF78

1. Salvar com dados válidos cria o plano e retorna o identificador.
2. O contador de planos acompanha o cadastro.
3. A listagem apresenta o plano criado com os dados informados.
4. Campos obrigatórios em branco são validados antes da gravação.
5. Os benefícios informados são gravados com o plano.

### Pontos a confirmar e limites do RF78

A linha do plano na listagem, os campos obrigatórios e os benefícios não foram verificados; o cartão Ativos é tratado no RF79.

---

<a id="rf79"></a>


## RF79 — Manter o cartão Ativos coerente com o status dos planos

| Campo | Descrição |
| --- | --- |
| Requisito de QA | O cartão Ativos da tela Planos deve contar apenas planos com status ativo e não aumentar ao cadastrar ou editar planos inativos, enquanto o cartão Planos acompanha o total de registros. |
| Ator | Usuário autenticado com acesso ao módulo. |
| Pré-condições | Base de planos conhecida, com a regra do cartão definida com o produto. |
| Gatilho | Cadastrar um plano inativo e editar um plano inativo. |
| Caso | [CT-RF79](Cenario_Teste/CT-RF79_Contador_Ativos_Planos.md) |
| Situação observada | Reprovado nas evidências. O cartão Ativos sobe de 29 para 31 após cadastrar e editar planos inativos. |
| Defeito | [BUG-041](Relatorio-de-Bugs.md#bug-041), em triagem |
| Evidências | [Jam](https://jam.dev/c/233c5d21-e108-4a55-b6f6-8738cb3fc6a6) e [Evidências](Evidencias/CT-RF102_Contador_Ativos_Planos/README.md). |

### Critérios de aceitação do RF79

1. O cartão Ativos conta apenas planos com status ativo.
2. Cadastrar um plano inativo não altera o cartão Ativos.
3. Editar um plano sem alterar o status não altera o cartão Ativos.
4. O cartão Planos acompanha o total de registros.
5. O cartão é recalculado de forma consistente após recarregar a página.

### Pontos a confirmar e limites do RF79

A regra de cálculo do cartão e a contagem da listagem não foram verificadas.

---

<a id="rf80"></a>


## RF80 — Editar um plano

| Campo | Descrição |
| --- | --- |
| Requisito de QA | O botão de ação da listagem deve abrir o plano com os dados atuais e permitir a alteração dos campos, gravando sem erro e atualizando a listagem. |
| Ator | Usuário autenticado com acesso ao módulo. |
| Pré-condições | Plano descartável cadastrado e visível na listagem. |
| Gatilho | Acionar o botão de ação do plano, alterar os benefícios e acionar Salvar Plano. |
| Caso | [CT-RF80](Cenario_Teste/CT-RF80_Edicao_Plano.md) |
| Situação observada | Aprovado conforme a gravação. O modal abre com os dados do plano 41 e plano/update retorna HTTP 200 sem erro. |
| Defeito | Nenhum no fluxo avaliado |
| Evidências | [Jam](https://jam.dev/c/233c5d21-e108-4a55-b6f6-8738cb3fc6a6) e [Evidências](Evidencias/CT-RF103_Edicao_Plano/README.md). |

### Critérios de aceitação do RF80

1. O botão de ação abre o plano com os dados atuais.
2. A alteração de qualquer campo é enviada e gravada sem erro.
3. A listagem reflete a alteração.
4. A alteração permanece após recarregar.
5. O cartão Ativos não é alterado por edição sem mudança de status (CT-RF79).

### Pontos a confirmar e limites do RF80

A persistência após recarga, a edição dos demais campos e o efeito no cartão Ativos não foram exercitados.

---

<a id="rf84"></a>


## RF81 — Cadastrar um modelo de contrato

| Campo | Descrição |
| --- | --- |
| Requisito de QA | O formulário Adicionar Modelo Contrato deve criar o modelo com título, status e texto informados e devolvê-lo na lista de modelos. |
| Ator | Usuário autenticado com acesso ao módulo. |
| Pré-condições | Formulário preenchido; modelos existentes conhecidos. |
| Gatilho | Preencher título, status e texto e acionar Salvar modelo. |
| Caso | [CT-RF81](Cenario_Teste/CT-RF81_Cadastro_Modelo_Contrato.md) |
| Situação observada | Aprovado conforme a gravação. `modelo-contrato/salvar` retorna HTTP 201 e o servidor passa a listar o modelo de id 15 ("teste eduardo", Ativo). |
| Defeito | Nenhum no fluxo avaliado |
| Evidências | [Jam](https://jam.dev/c/44dbbd39-6915-45d6-8dd1-5f30c1432ca0) e [Evidências](Evidencias/CT-RF97_Cadastro_Modelo_Contrato/README.md). |

### Critérios de aceitação do RF81

1. Salvar com dados válidos cria o modelo e retorna sucesso.
2. O modelo criado é devolvido pelo servidor na lista de modelos.
3. A listagem na tela apresenta o modelo criado.
4. Título e texto obrigatórios são validados antes da gravação.
5. O texto e as variáveis são gravados sem perda.

### Pontos a confirmar e limites do RF81

O corpo da criação, o texto gravado, os campos obrigatórios e a apresentação na listagem não foram verificados.

---

<a id="rf83"></a>


## RF82 — Inserir variáveis e pré-visualizar o contrato

| Campo | Descrição |
| --- | --- |
| Requisito de QA | O editor do modelo de contrato deve inserir as variáveis clicadas e a pré-visualização deve substituí-las por dados de exemplo, preservando a formatação. |
| Ator | Usuário autenticado com acesso ao módulo. |
| Pré-condições | Editor de modelo de contrato aberto; variáveis disponíveis. |
| Gatilho | Clicar em variáveis e acionar Atualizar preview. |
| Caso | [CT-RF82](Cenario_Teste/CT-RF82_Variaveis_Preview_Modelo_Contrato.md) |
| Situação observada | Aprovado conforme a gravação. As variáveis {numero_contrato}, {nome_aluno} e {cpf_aluno} são inseridas e a pré-visualização apresenta "2024/001 João da Silva 123.456.789-00". |
| Defeito | Nenhum no fluxo avaliado |
| Evidências | [Jam](https://jam.dev/c/44dbbd39-6915-45d6-8dd1-5f30c1432ca0) e [Evidências](Evidencias/CT-RF96_Variaveis_Preview_Modelo_Contrato/README.md). |

### Critérios de aceitação do RF82

1. Cada variável clicada é inserida no ponto do cursor do editor.
2. A pré-visualização substitui as variáveis por dados de exemplo coerentes.
3. A formatação do texto é preservada na pré-visualização.
4. Todas as variáveis dos quatro grupos funcionam.
5. As variáveis permanecem no texto após salvar.

### Pontos a confirmar e limites do RF82

As demais variáveis, a formatação complexa e o texto gravado não foram exercitados.

---

<a id="rf81"></a>


## RF83 — Apresentar na listagem os modelos de contrato retornados pelo servidor

| Campo | Descrição |
| --- | --- |
| Requisito de QA | A tela Modelos Contrato deve apresentar uma linha com código, nome e status para cada modelo retornado pelo servidor, inclusive o recém-criado, ou uma mensagem explícita quando não houver modelos. |
| Ator | Usuário autenticado com acesso ao módulo. |
| Pré-condições | Modelos de contrato existentes no servidor. |
| Gatilho | Acessar Modelos Contrato e, depois, criar um modelo. |
| Caso | [CT-RF83](Cenario_Teste/CT-RF83_Listagem_Modelos_Contrato_Vazia.md) |
| Situação observada | Reprovado nas evidências. O servidor devolve 15 modelos, mas a tabela permanece com apenas o cabeçalho, sem linhas e sem mensagem. |
| Defeito | [BUG-040](Relatorio-de-Bugs.md#bug-040), em triagem |
| Evidências | [Jam](https://jam.dev/c/44dbbd39-6915-45d6-8dd1-5f30c1432ca0) e [Evidências](Evidencias/CT-RF98_Listagem_Modelos_Contrato_Vazia/README.md). |

### Critérios de aceitação do RF83

1. A tabela apresenta uma linha para cada modelo retornado pelo servidor.
2. O modelo recém-criado aparece na listagem sem recarregar manualmente.
3. Código, nome e status são exibidos corretamente.
4. Sem modelos, a tela apresenta mensagem explícita de estado vazio.
5. A listagem permanece correta após recarregar a página.

### Pontos a confirmar e limites do RF83

A causa e o comportamento após recarga não foram confirmados; a lista completa foi lida por texto.

---

<a id="rf77"></a>


## RF84 — Filtrar tipos de pagamento por código, nome, status e tipo

| Campo | Descrição |
| --- | --- |
| Requisito de QA | A listagem de Tipos de Pagamento deve apresentar apenas os tipos que atendam aos critérios de código, nome, status e tipo informados, com cartões coerentes e mensagem explícita de resultado vazio. |
| Ator | Usuário autenticado com acesso ao módulo. |
| Pré-condições | Base de tipos conhecida, com nomes, tipos e status registrados. |
| Gatilho | Informar critérios e acionar Buscar. |
| Caso | [CT-RF84](Cenario_Teste/CT-RF84_Filtros_Tipos_Pagamento.md) |
| Situação observada | A validar — regra ou contexto pendente. Os seletores e Buscar foram acionados sem requisição de listagem e a listagem permaneceu com 16 tipos; o valor escolhido não foi registrado. |
| Defeito | Sem defeito confirmado |
| Evidências | [Jam](https://jam.dev/c/e8734e3d-3f8e-458b-8c7d-e85eea882e50) e [Evidências](Evidencias/CT-RF104_Filtros_Tipos_Pagamento/README.md). |

### Critérios de aceitação do RF84

1. Cada critério isolado (código, nome, status e tipo) filtra corretamente a listagem.
2. A combinação de critérios aplica todos eles simultaneamente.
3. Os cartões acompanham o conjunto exibido conforme o contrato definido.
4. O resultado vazio apresenta mensagem explícita.
5. Limpar os critérios restaura a listagem completa.

### Pontos a confirmar e limites do RF84

Cada critério isolado, a filtragem local ou no servidor e o resultado vazio não foram verificados.

---

<a id="rf85"></a>


## RF85 — Gravar e refletir o status do tipo de pagamento no cadastro

| Campo | Descrição |
| --- | --- |
| Requisito de QA | O cadastro de tipo de pagamento deve gravar os valores informados, inclusive o status, e a listagem e os cartões Ativos e Inativos devem refletir o status real de cada tipo. |
| Ator | Usuário autenticado com acesso ao módulo. |
| Pré-condições | Modal Tipo de Pagamento aberto; regra do status definida com o produto. |
| Gatilho | Informar os campos, manter o Status Ativo e acionar Salvar. |
| Caso | [CT-RF85](Cenario_Teste/CT-RF85_Cadastro_Tipo_Pagamento_Status.md) |
| Situação observada | Reprovado nas evidências. A criação retorna HTTP 201, mas o status Ativo não é enviado, a API não o devolve, todos os tipos aparecem como Inativo e o cartão Ativos permanece em 0. |
| Defeito | [BUG-042](Relatorio-de-Bugs.md#bug-042), em triagem |
| Evidências | [Jam](https://jam.dev/c/e8734e3d-3f8e-458b-8c7d-e85eea882e50) e [Evidências](Evidencias/CT-RF105_Cadastro_Tipo_Pagamento_Status/README.md). |

### Critérios de aceitação do RF85

1. O status escolhido no modal é enviado ao servidor e gravado.
2. A listagem apresenta o status real de cada tipo, e não um valor fixo.
3. O cartão Ativos conta os tipos ativos e Inativos os demais.
4. O novo tipo aparece na listagem com nome, tipo, via gateway e status informados.
5. Reabrir o tipo mostra os valores gravados.

### Pontos a confirmar e limites do RF85

A regra do status e a persistência após recarga não foram verificadas; o novo tipo não está visível nos quadros.

---

<a id="rf86"></a>


## RF86 — Editar um tipo de pagamento

| Campo | Descrição |
| --- | --- |
| Requisito de QA | A lupa da listagem deve abrir o tipo com os dados gravados e permitir alterá-los, gravando sem erro e atualizando a listagem e os cartões. |
| Ator | Usuário autenticado com acesso ao módulo. |
| Pré-condições | Listagem de tipos aberta e tipo existente. |
| Gatilho | Abrir o tipo pela lupa, alterar um campo e acionar Salvar. |
| Caso | [CT-RF86](Cenario_Teste/CT-RF86_Edicao_Tipo_Pagamento.md) |
| Situação observada | Aprovado conforme a gravação. A edição do tipo Dinheiro retorna HTTP 200 sem erro e a listagem reflete Pagamento Pelo Sistema Não; Via gateway passa de 6 para 5. |
| Defeito | Nenhum no fluxo avaliado |
| Evidências | [Jam](https://jam.dev/c/e8734e3d-3f8e-458b-8c7d-e85eea882e50) e [Evidências](Evidencias/CT-RF106_Edicao_Tipo_Pagamento/README.md). |

### Critérios de aceitação do RF86

1. O tipo selecionado é aberto com os valores gravados.
2. A alteração é gravada sem mensagem de erro.
3. A listagem e o cartão Via gateway refletem a alteração.
4. A alteração persiste após recarregar a página.
5. A edição de nome e de tipo também é gravada.

### Pontos a confirmar e limites do RF86

A persistência após recarga e a edição de nome e tipo não foram verificadas.

---

<a id="rf87"></a>


## RF87 — Impedir a exclusão de tipo de pagamento em uso com mensagem clara

| Campo | Descrição |
| --- | --- |
| Requisito de QA | A exclusão de um tipo de pagamento em uso deve ser impedida com mensagem clara ao usuário, código HTTP compatível e sem expor detalhes internos do banco na resposta. |
| Ator | Usuário autenticado com acesso ao módulo. |
| Pré-condições | Tipo de pagamento referenciado por contas a receber; regra de exclusão definida com o produto. |
| Gatilho | Acionar o ícone de exclusão e confirmar o diálogo. |
| Caso | [CT-RF87](Cenario_Teste/CT-RF87_Exclusao_Tipo_Pagamento_Em_Uso.md) |
| Situação observada | Reprovado nas evidências. Dois tipos em uso retornam HTTP 404 com o erro SQL completo na resposta; a tela mostra só "Erro ao deletar tipo de pagamento". |
| Defeito | [BUG-043](Relatorio-de-Bugs.md#bug-043), em triagem |
| Evidências | [Jam](https://jam.dev/c/e8734e3d-3f8e-458b-8c7d-e85eea882e50) e [Evidências](Evidencias/CT-RF107_Exclusao_Tipo_Pagamento_Em_Uso/README.md). |

### Critérios de aceitação do RF87

1. A exclusão de um tipo em uso é impedida com mensagem clara que informe o uso.
2. A resposta do servidor não expõe nomes de esquema, tabela ou restrição do banco.
3. O código HTTP é compatível com o conflito (por exemplo 409) e não 404.
4. A listagem e os cartões permanecem íntegros após a falha.
5. Um tipo sem uso é excluído e removido da listagem.

### Pontos a confirmar e limites do RF87

A regra de exclusão e a exclusão de um tipo sem uso não foram verificadas.

---

<a id="rf88"></a>


## RF88 — Alternar tema Claro/Escuro e abrir as notificações em Tipos de Pagamento

| Campo | Descrição |
| --- | --- |
| Requisito de QA | A tela de Tipos de Pagamento deve aplicar o tema escolhido a todos os elementos e o painel de notificações deve apresentar o estado das notificações. |
| Ator | Usuário autenticado com acesso ao módulo. |
| Pré-condições | Tela aberta com o controle de tema e o sino disponíveis. |
| Gatilho | Alternar o tema e acionar o sino. |
| Caso | [CT-RF88](Cenario_Teste/CT-RF88_Tema_Notificacoes_Tipos_Pagamento.md) |
| Situação observada | Aprovado conforme a gravação. O tema Escuro foi aplicado de forma consistente, as notificações exibiram o estado vazio e o retorno a Claro restaurou a tela; seis chamadas de tema com HTTP 200. |
| Defeito | Nenhum no fluxo avaliado |
| Evidências | [Jam](https://jam.dev/c/e8734e3d-3f8e-458b-8c7d-e85eea882e50) e [Evidências](Evidencias/CT-RF108_Tema_Notificacoes_Tipos_Pagamento/README.md). |

### Critérios de aceitação do RF88

1. O tema Escuro é aplicado ao fundo, aos painéis, aos cartões e à listagem.
2. O painel de notificações apresenta o estado das notificações.
3. O retorno a Claro restaura a tela.
4. O tema escolhido persiste após recarregar a página.
5. Diálogos e modais acompanham o tema.

### Pontos a confirmar e limites do RF88

Contraste, persistência após recarga e modais no tema Escuro não foram verificados.

<a id="rf149"></a>


## RF89 — Cadastrar bandeira com parcela e conferir a listagem

| Campo | Descrição |
| --- | --- |
| Requisito funcional | A bandeira deve ser criada com a configuração de parcela e aparecer na listagem após o salvamento. |
| Ator | Usuário autenticado com acesso a Bandeiras de Cartão. |
| Pré-condição | Sessão autenticada com permissão para cadastrar Bandeiras de Cartão. Ambiente de teste com possibilidade de cadastrar uma bandeira e sua configuração de parcela. |
| Comportamento esperado | A bandeira deve ser criada com a configuração de parcela e aparecer na listagem após o salvamento. |
| Situação observada | A API confirma a criação da bandeira de código 34 e da parcela, mas a consulta seguinte retorna [] e a interface continua exibindo Nenhuma bandeira encontrada. A criação da parcela tem retorno de sucesso; o fluxo completo apresenta erro na recuperação/exibição do cadastro. |
| Prioridade | Alta, proposta. |
| Rastreabilidade | [CT-RF89](Cenario_Teste/CT-RF89_Cadastro_Bandeira_Parcela_Listagem.md) · [BUG-035](Relatorio-de-Bugs.md#bug-035) · [Evidências](Evidencias/CT-RF81_Cadastro_Bandeira_Parcela_Listagem/README.md) · [Jam](https://jam.dev/c/2f0280fb-6b7f-4cf0-a45c-02f8c16b6c5e) |

### Critérios de aceitação do RF89

1. A criação da bandeira e da parcela é concluída de forma coerente.
2. A consulta posterior inclui a bandeira confirmada pela criação.
3. A listagem exibe o novo registro sem exigir um novo cadastro.
4. Reabrir e recarregar a bandeira permite conferir taxas e configuração de parcela.
5. Uma falha parcial deve produzir mensagem clara e permitir recuperação sem duplicidade.

### Base da análise e limites do RF89

Reprovado nas evidências resumidas. A causa da divergência e a persistência efetiva no banco não foram verificadas. A gravação comprova a diferença entre os retornos de criação e de listagem, sem permitir atribuir a causa ao frontend ou ao backend.
Análise da gravação e dos eventos capturados no Jam; não foi executado um novo teste no sistema.

Encaminhamento: Investigar a divergência criação/consulta; retestar listagem, reabertura e recarga com e sem parcela.

<a id="rf90"></a>


## RF90 — Verificar aplicação dos temas na tela de Bandeiras

| Campo | Descrição |
| --- | --- |
| Requisito funcional | O tema selecionado deve ser aplicado de forma consistente ao fundo, aos painéis e aos textos da tela. |
| Ator | Usuário autenticado com acesso a Bandeiras de Cartão. |
| Pré-condição | Sessão autenticada com acesso à tela Bandeiras de Cartão. Controle de tema disponível e listagem no estado vazio observado. |
| Comportamento esperado | O tema selecionado deve ser aplicado de forma consistente ao fundo, aos painéis e aos textos da tela. |
| Situação observada | No tema Escuro, os painéis ficam escuros, mas o fundo principal continua claro. Os textos da área vazia da listagem apresentam baixa legibilidade visual. A descrição do Jam relata: Fundo com falta de cores e modo escuro incompleto. |
| Prioridade | Média, proposta. |
| Rastreabilidade | [CT-RF90](Cenario_Teste/CT-RF90_Tema_Escuro_Bandeiras.md) · [BUG-036](Relatorio-de-Bugs.md#bug-036) · [Evidências](Evidencias/CT-RF82_Tema_Escuro_Bandeiras/README.md) · [Jam](https://jam.dev/c/ae4dc198-8a42-4451-898a-fb376596c744) |

### Critérios de aceitação do RF90

1. O tema Escuro é aplicado ao fundo principal e aos painéis.
2. Os textos do estado vazio permanecem visualmente legíveis.
3. Alternar os temas mantém a consistência entre fundo, painéis e textos.
4. No reteste, conferir também a listagem preenchida.
5. Medições de contraste, se realizadas, devem registrar valores e o critério adotado separadamente.

### Base da análise e limites do RF90

Reprovado nas evidências resumidas. O erro visual é observado na gravação. Não foram medidos índices de contraste nem feita auditoria formal de acessibilidade; a causa técnica não foi determinada.
Análise da gravação e dos eventos capturados no Jam; não foi executado um novo teste no sistema.

Encaminhamento: Revisar os estilos da página e retestar Claro/Escuro com lista vazia e preenchida; medir contraste separadamente.

<a id="rf69"></a>


## RF91 a RF99 — Validações, operações e buscas de Colaboradores

| Requisito | Comportamento esperado | Caso | Defeito | Resultado observado |
| --- | --- | --- | --- | --- |
| <a id="rf91"></a>RF91 | Recusar data de nascimento posterior à data atual. | [CT-RF91](Cenario_Teste/CT-RF91_Data_Nascimento_Futura_Colaborador.md) | [BUG-026](Relatorio-de-Bugs.md#bug-026) | `18/05/2222` aceito; atualização HTTP 200. |
| <a id="rf92"></a>RF92 | Exigir a data de nascimento definida como obrigatória. | [CT-RF92](Cenario_Teste/CT-RF92_Data_Nascimento_Obrigatoria_Colaborador.md) | [BUG-027](Relatorio-de-Bugs.md#bug-027) | Campo vazio aceito; atualização HTTP 200. |
| <a id="rf93"></a>RF93 | Validar o CREF conforme o formato confirmado pelo produto. | [CT-RF93](Cenario_Teste/CT-RF93_CREF_Formato_Colaborador.md) | [BUG-028](Relatorio-de-Bugs.md#bug-028) | Texto `TESTEE` aceito; atualização HTTP 200. |
| <a id="rf94"></a>RF94 | Bloquear edição com qualquer campo obrigatório vazio. | [CT-RF94](Cenario_Teste/CT-RF94_Edicao_Colaborador_Campo_Obrigatorio_Vazio.md) | [BUG-029](Relatorio-de-Bugs.md#bug-029) | Edição aceita sem validação visível; HTTP 200. |
| <a id="rf95"></a>RF95 | Manter uma única associação por colaborador e função. | [CT-RF95](Cenario_Teste/CT-RF95_Funcao_Duplicada_Colaborador.md) | [BUG-030](Relatorio-de-Bugs.md#bug-030) | Mesma função associada três vezes; dois POST HTTP 201. |
| <a id="rf96"></a>RF96 | Excluir colaborador permitido ou explicar o vínculo impeditivo sem HTTP 500. | [CT-RF96](Cenario_Teste/CT-RF96_Exclusao_Colaborador_Erro_500.md) | [BUG-031](Relatorio-de-Bugs.md#bug-031) | Exclusão retorna HTTP 500 e erro interno genérico. |
| <a id="rf97"></a>RF97 | Manter o filtro por nome aplicado em todas as páginas do resultado. | [CT-RF97](Cenario_Teste/CT-RF97_Busca_Nome_Colaborador_Paginacao.md) | [BUG-033](Relatorio-de-Bugs.md#bug-033) | A página seguinte exibe nomes fora do filtro. |
| <a id="rf98"></a>RF98 | Retornar somente o colaborador associado a um código existente. | [CT-RF98](Cenario_Teste/CT-RF98_Busca_Codigo_Existente_Colaborador.md) | — | Usuário correto retornado no exemplo gravado. |
| <a id="rf99"></a>RF99 | Exibir estado vazio para código inexistente, sem linha residual. | [CT-RF99](Cenario_Teste/CT-RF99_Busca_Codigo_Inexistente_Colaborador.md) | [BUG-034](Relatorio-de-Bugs.md#bug-034) | A tabela apresenta uma linha vazia. |

### Critérios gerais de aceitação

1. Regras de obrigatoriedade e formato devem ser aplicadas no cliente e no servidor.
2. Tentativas inválidas não podem persistir dados parcial ou integralmente.
3. A associação colaborador/função deve ser única e resistente a repetição ou concorrência.
4. Impedimentos de exclusão devem ser tratados como regra de negócio, com mensagem específica.
5. Todos os fluxos devem preservar os dados anteriores após falha e permitir correção.
6. Filtros devem permanecer ativos durante a paginação e representar o mesmo conjunto nos totais.
7. Consultas sem correspondência devem apresentar estado vazio sem linhas ou ações residuais.

### Base da análise — revisão de 15/11/2026

RF100 registra HTTP 500 no cadastro de anamnese. Os seis Jams de RF91–RF96 foram lidos por metadados, eventos de interação e registros de rede: RF91–RF94 possuem POST de atualização HTTP 200 sem corpo capturado, por isso a aceitação do endpoint está comprovada, mas a persistência final deve ser reconfirmada; RF95 registra payloads, HTTP 201 e respostas subsequentes com três associações iguais; RF96 registra payload, HTTP 500 e `Erro interno inesperado`. Com a inclusão de RF101 (Modelos de Anamnese), a gravação foi lida por metadados, eventos de interação e registros de rede, confirmando a aprovação sem erro de servidor. RF97–RF99 foram analisados visualmente: falha do filtro na paginação, busca válida por código e linha vazia para código inexistente. Não houve nova execução, acesso ao banco, logs ou código. A análise passa a cobrir 69 requisitos documentados;

---

<a id="rf61"></a>


## RF100 — Cadastrar anamnese sem erro de servidor

| Campo | Descrição |
| --- | --- |
| Requisito de QA | Ao preencher as respostas de um modelo de anamnese e acionar "Salvar rascunho" ou a aplicação definitiva, o backend deve gravar o registro e retornar sucesso, sem erro genérico de servidor. |
| Ator | Usuário autenticado com permissão em Fichas de Anamnese. |
| Pré-condições | Aluno cadastrado e selecionável; modelo de anamnese com ao menos uma pergunta cadastrada. |
| Gatilho | Selecionar aluno e modelo, responder à(s) pergunta(s) e acionar "Salvar rascunho" ou a aplicação definitiva da anamnese. |
| Caso | [CT-RF100](Cenario_Teste/CT-RF100_Cadastro_Anamnese.md) |
| Situação observada | Reprovado nas evidências. As sete tentativas registradas na gravação (quatro em `/api/anamnese/aplicar/{id}` e três em `/api/anamnese/rascunho/{id}`) retornam HTTP 500 com a mesma mensagem genérica, independentemente do modelo de anamnese ou da resposta informada; nenhuma anamnese é cadastrada com sucesso. |
| Defeito | [BUG-032](Relatorio-de-Bugs.md#bug-032), em triagem |
| Evidências | [Jam](https://jam.dev/c/7be0fe71-3419-4050-b63f-473d943fa08e). |

### Critérios de aceitação do RF100

1. Ao preencher corretamente as respostas de um modelo e acionar "Salvar rascunho", o backend grava o rascunho e retorna sucesso.
2. Ao preencher corretamente as respostas e acionar a aplicação definitiva, o backend grava a anamnese com `status: "concluida"` e retorna sucesso.
3. O comportamento é validado para mais de um modelo de anamnese e mais de um aluno.
4. Uma anamnese salva com sucesso fica disponível para consulta na listagem.
5. Um erro de validação específico (por exemplo, pergunta sem resposta) não deve ser reportado como "Erro interno inesperado.".

### Pontos a confirmar e limites do RF100

Não houve acesso a logs do servidor, ao código das rotinas de aplicar/rascunho nem ao banco de dados; a causa real do HTTP 500 não foi determinada. O padrão de resposta é idêntico ao já registrado em [BUG-016](Relatorio-de-Bugs.md#bug-016) e [BUG-024](Relatorio-de-Bugs.md#bug-024), o que sugere tratamento de erro genérico no backend, mas não foi confirmado se a causa de fundo é a mesma. Não foi confirmado se as tentativas de rascunho afetaram o mesmo registro ou criaram registros distintos.

---

---


## RF101 — Gerenciar modelos de anamnese sem erro de servidor

| Campo | Descrição |
| --- | --- |
| Requisito de QA | Ao buscar, filtrar, cadastrar, editar e excluir modelos de anamnese, o backend deve processar cada operação e retornar sucesso, sem erro de servidor. |
| Ator | Usuário autenticado com permissão em Modelos de Anamnese. |
| Pré-condições | Ao menos um modelo de anamnese já cadastrado; banco de perguntas com itens cadastrados e pesquisáveis. |
| Gatilho | Buscar/filtrar a listagem, cadastrar um modelo com perguntas do banco, editar um modelo cadastrado e excluir modelos pela ação do cartão. |
| Caso | [CT-RF101](Cenario_Teste/CT-RF101_Gestao_Modelos_Anamnese.md) |
| Situação observada | Aprovado conforme a gravação. As quinze requisições identificadas aos endpoints `/api/modelos-anamnese/*` (busca/filtro, cadastro, duas edições e duas exclusões) retornam HTTP 200 ou 201; nenhuma requisição ao backend do SIFIT retorna erro 4xx ou 5xx na gravação. |
| Defeito | Nenhum identificado no fluxo avaliado. |
| Evidências | [Jam](https://jam.dev/c/4c1e9deb-20ca-417f-ad09-48749857266e). |

### Critérios de aceitação do RF101

1. A busca e o filtro de status na listagem de modelos retornam resultados consistentes com o termo e o status informados.
2. Um novo modelo é cadastrado com nome, descrição e perguntas do banco, e passa a constar na listagem.
3. Um modelo cadastrado pode ser editado mais de uma vez, preservando as alterações salvas.
4. Um modelo pode ser excluído e deixa de constar na listagem após a exclusão.
5. Nenhuma das operações acima deve retornar erro HTTP 4xx ou 5xx em uso normal.

### Pontos a confirmar e limites do RF101

Os endpoints de escrita (`salvar/1`, `alterar/1` e `deletar/1`) e o de leitura (`GET /api/modelos-anamnese/1`) usam o mesmo sufixo numérico `1`, independentemente do modelo manipulado — compatível com a hipótese já registrada em RF100 de que esse identificador corresponde ao `empresa_id` da conta, e não ao id do modelo. A leitura da listagem retorna HTTP 201 em vez do código 200 mais usual para esse tipo de operação; como permanece na faixa de sucesso, isso não é tratado como defeito, mas fica registrado para confirmação com a equipe de desenvolvimento. Os corpos de solicitação e de resposta das chamadas de API não foram capturados pelo Jam, uma limitação da ferramenta. Não houve nova execução, acesso a logs, ao código ou ao banco, nem reteste.

### Base da análise do RF101 — revisão de 16/11/2026

RF101 utiliza os painéis Informações, Console e Rede do Jam "Modelos de Anamnese", os eventos de clique e digitação entre 0:00 e 2:32 e as quinze requisições aos endpoints `/api/modelos-anamnese/*`, todas com HTTP 200 ou 201. A única requisição com código de erro em toda a gravação é um *beacon* de analytics do Google (HTTP 499), sem relação com o backend do SIFIT. Os corpos de requisição e de resposta não foram capturados pelo Jam. Não houve nova execução, acesso a logs, ao código ou ao banco, nem reteste.

Com RF101, a análise passa a cobrir 58 requisitos documentados (antes da integração de RF91 a RF96).

---


## RF102 — Gerenciar categorias de anamnese sem erro de servidor

| Campo | Descrição |
| --- | --- |
| Requisito de QA | Ao filtrar por status, pesquisar, cadastrar, editar, cancelar uma edição e excluir categorias de anamnese, o backend deve processar cada operação e retornar sucesso, sem erro de servidor, e não enviar requisição alguma quando a edição é cancelada. |
| Ator | Usuário autenticado com permissão em Categorias de Anamnese. |
| Pré-condições | Ao menos uma categoria de anamnese já cadastrada, para exercitar o filtro por status e a busca. |
| Gatilho | Filtrar/pesquisar a listagem, cadastrar uma categoria, editá-la (ícone, nome e status), cancelar uma edição em andamento e excluí-la pelo ícone do cartão. |
| Caso | [CT-RF102](Cenario_Teste/CT-RF102_Gestao_Categorias_Anamnese.md) |
| Situação observada | Aprovado conforme a gravação. As sete requisições identificadas aos endpoints `/api/categorias-anamnese/*` (cadastro, três edições e exclusão) retornam HTTP 200 ou 201; a quarta tentativa de edição é cancelada e não gera requisição; nenhuma requisição ao backend do SIFIT retorna erro 4xx ou 5xx na gravação. |
| Defeito | Nenhum identificado no fluxo avaliado. |
| Evidências | [Jam](https://jam.dev/c/fdb1c9f8-c428-4726-9742-617800325d09). |

### Critérios de aceitação do RF102

1. O filtro de status e a busca por texto na listagem de categorias aplicam-se de forma consistente, sem gerar erro.
2. Uma nova categoria é cadastrada com nome, cor, ícone e status, e passa a constar na listagem.
3. Uma categoria cadastrada pode ser editada mais de uma vez (ícone, nome e status, isoladamente ou em conjunto), preservando as alterações salvas.
4. Ao cancelar uma edição em andamento, nenhuma alteração é enviada ao backend e os valores salvos anteriormente são mantidos.
5. Uma categoria pode ser excluída e deixa de constar na listagem após a exclusão.
6. Nenhuma das operações acima deve retornar erro HTTP 4xx ou 5xx em uso normal.

### Pontos a confirmar e limites do RF102

Os endpoints de escrita (`salvar/1`, `alterar/1` e `deletar/1`) e o de leitura (`GET /api/categorias-anamnese/1`) usam o mesmo sufixo numérico `1`, independentemente da categoria manipulada — reforçando a hipótese já registrada em RF100 e RF101 de que esse identificador corresponde ao `empresa_id` da conta, e não ao id da categoria. Diferentemente de RF101, aqui o cadastro retorna HTTP 201 e as edições e a exclusão retornam HTTP 200, um padrão mais previsível entre operações semelhantes, registrado para confirmação com a equipe de desenvolvimento. A ferramenta de gravação (Jam) apresentou instabilidade ao exibir os cabeçalhos de detalhe de algumas requisições com o mesmo identificador e horário repetidos entre linhas diferentes — tratado como limitação da ferramenta de captura, já que URL, método e código de status de cada requisição permaneceram corretos ao serem reconferidos. Não houve nova execução, acesso a logs, ao código ou ao banco, nem reteste.

### Base da análise do RF102 — revisão de 16/11/2026

RF102 utiliza os painéis Informações, Console, Rede e Ações do Jam "Categorias de Anamnese", os eventos de clique e digitação entre 0:00 e 1:35 e as sete requisições aos endpoints `/api/categorias-anamnese/*`, todas com HTTP 200 ou 201. A única requisição não relacionada ao backend do SIFIT é um *beacon* de telemetria de uma extensão de antivírus do navegador, também com retorno de sucesso. Não foram registradas mensagens de erro no console. Não houve nova execução, acesso a logs, ao código ou ao banco, nem reteste.

Com RF102, a análise passa a cobrir 59 requisitos documentados (antes da integração de RF91 a RF96).

---


## RF103 — Editar pergunta de anamnese sem erro de servidor

| Campo | Descrição |
| --- | --- |
| Requisito de QA | Ao editar o tipo de resposta ou o status de uma pergunta de anamnese cadastrada, o backend deve processar a alteração e retornar sucesso, sem erro de servidor. |
| Ator | Usuário autenticado com permissão em Perguntas Anamnese. |
| Pré-condições | Ao menos uma pergunta de anamnese já cadastrada, com um tipo de resposta definido. |
| Gatilho | Reabrir uma pergunta cadastrada pela ação de editar, alterar o tipo de resposta ou o status e acionar "Salvar". |
| Caso | [CT-RF103](Cenario_Teste/CT-RF103_Edicao_Pergunta_Anamnese.md) |
| Situação observada | Reprovado nas evidências. As quatro tentativas de editar o tipo de resposta e/ou o status de uma pergunta recém-criada retornam HTTP 500, com o mesmo corpo genérico de erro, impedindo qualquer atualização da pergunta. |
| Defeito | [BUG-044](Relatorio-de-Bugs.md#bug-044), em triagem. |
| Evidências | [Jam](https://jam.dev/c/84b116fb-4640-4b1e-9148-9a169b8aa2b0). |

### Critérios de aceitação do RF103

1. O filtro de código, nome e status na listagem de perguntas aplica-se de forma consistente, sem gerar erro.
2. Uma nova pergunta é cadastrada com nome, texto, tipo de resposta e status, e passa a constar na listagem.
3. Uma pergunta cadastrada pode ter o tipo de resposta alterado e salvo, sem erro de servidor, preservando a alteração.
4. Uma pergunta cadastrada pode ter o status alterado e salvo, isoladamente ou em conjunto com o tipo de resposta, sem erro de servidor.
5. Nenhuma das operações acima deve retornar erro HTTP 4xx ou 5xx em uso normal.

### Pontos a confirmar e limites do RF103

As quatro tentativas de edição falham com o mesmo erro genérico independentemente do valor de `resposta` (`"3opcoes"` ou `"2opcoes"`) ou do `status`, o que sugere uma falha na própria rotina de alteração — possivelmente ao ajustar ou remover as opções/complementos do tipo de resposta anterior (`"2opcoes_complemento"`, definido na criação) — e não em um valor específico enviado; isso não foi confirmado com acesso a logs, ao código ou ao banco. O cadastro da pergunta (`salvar/1`) foi registrado em duplicidade para uma única ação de "Salvar" (HTTP 200 e HTTP 201), no mesmo padrão de duplicação por clique já observado em outros módulos (por exemplo, CT-RF51). Não houve nova execução, acesso a logs, ao código ou ao banco, nem reteste.

### Base da análise do RF103 — revisão de 16/11/2026

RF103 utiliza os painéis Informações, Console, Rede e Ações do Jam "Perguntas Anamnese", os eventos de clique e digitação entre 0:00 e 1:30 e as dezenove requisições identificadas, incluindo as quatro requisições `POST /api/pergunta-anamnese/alterar/1`, todas com HTTP 500. As quatro requisições de erro aparecem também na visão "Erros de rede" do painel Console do Jam, nos mesmos instantes observados no painel Rede. Não houve nova execução, acesso a logs, ao código ou ao banco, nem reteste.

Com RF103, a análise passa a cobrir 60 requisitos documentados (antes da integração de RF91 a RF96).

---


## RF104 — Abrir e fechar a configuração de Risco de Evasão

| Campo | Descrição |
| --- | --- |
| Requisito de QA | Abrir o painel correto de Risco de Evasão, consultar as opções e fechá-lo sem gravar uma alteração. |
| Ator | Usuário autenticado com permissão para a operação. |
| Pré-condições | Sessão autenticada com acesso à Central de Automações e cartão Risco de Evasão disponível. |
| Gatilho | Acionar Configurar no cartão Risco de Evasão e fechar o painel com Cancelar. |
| Caso | [CT-RF104](Cenario_Teste/CT-RF104_Central_Configuracao_Risco_Evasao_Cancelar.md) |
| Situação observada | Aprovado conforme a gravação. Configurar abriu Risco de Evasão e Cancelar fechou o painel. O cartão continuou ativo. |
| Defeito | Nenhum no fluxo avaliado |
| Evidências | [Jam — PED-06 — Configuração de Risco de Evasão](https://jam.dev/c/d49b8ffc-a6e2-4e37-a618-c280b5e807db) e [Evidências](Evidencias/CT-RF128_Central_Configuracao_Risco_Evasao_Cancelar/README.md). |

### Critérios de aceitação do RF104

1. O botão Configurar abre Risco de Evasão.
2. As opções e a prévia estão acessíveis no painel.
3. Cancelar retorna à Central e preserva o estado exibido no cartão.

### Pontos a confirmar e limites do RF104

A gravação percorre o painel sem editar opções. O descarte de valores alterados, o salvamento e a execução da automação ficaram fora deste cenário.

<a id="rf109"></a>


## RF105 — Executar Risco de Evasão manualmente pela Central

| Campo | Descrição |
| --- | --- |
| Requisito de QA | Executar Risco de Evasão pelo botão Executar agora e conferir o novo resultado na Central. |
| Ator | Usuário autenticado com permissão para a operação. |
| Pré-condições | Sessão autenticada com acesso à Central. Automação Risco de Evasão ativa em ambiente de teste autorizado. |
| Gatilho | Clicar em Executar agora no cartão Risco de Evasão. |
| Caso | [CT-RF105](Cenario_Teste/CT-RF105_Central_Risco_Evasao_Executar_Agora.md) |
| Situação observada | Aprovado conforme a gravação. Executar agora terminou com sucesso. O relatório e a nova execução ficaram disponíveis na Central. |
| Defeito | Nenhum no fluxo avaliado |
| Evidências | [Jam — PED-04 — Executar Risco de Evasão](https://jam.dev/c/be5418c7-8d87-4b6c-9c64-a9b33b5f7da6) e [Evidências](Evidencias/CT-RF137_Central_Risco_Evasao_Executar_Agora/README.md). |

### Critérios de aceitação do RF105

1. Executar agora retorna sucesso.
2. O novo relatório apresenta o resumo devolvido pela API.
3. A última execução e a atividade recente são atualizadas e permanecem após Atualizar.

### Pontos a confirmar e limites do RF105

A aprovação se limita à execução e à exibição do resultado na Central. O horário é a referência exibida no SIFIT. A entrega pelo canal de notificação não foi verificada. Os recortes mostram apenas informações agregadas.

<a id="rf106"></a>


## RF106 — Abrir os resultados de Risco de Evasão pela Central

| Campo | Descrição |
| --- | --- |
| Requisito de QA | Consultar o relatório existente de Risco de Evasão pela ação Ver resultados e conferir o total e a distribuição por nível. |
| Ator | Usuário autenticado com permissão para a operação. |
| Pré-condições | Sessão autenticada com acesso à Central e uma execução de Risco de Evasão já registrada. |
| Gatilho | Acionar Ver resultados no cartão Risco de Evasão. |
| Caso | [CT-RF106](Cenario_Teste/CT-RF106_Central_Abrir_Resultados_Risco_Evasao.md) |
| Situação observada | Aprovado conforme a gravação. Ver resultados abriu o relatório existente com a mesma distribuição retornada pela API: 0 alto, 23 médio e 0 baixo. |
| Defeito | Nenhum no fluxo avaliado |
| Evidências | [Jam — PED-05 — Ver resultados de Risco de Evasão](https://jam.dev/c/ac5bce26-f4a8-401b-bb23-d09d5253751a) e [Evidências](Evidencias/CT-RF138_Central_Abrir_Resultados_Risco_Evasao/README.md). |

### Critérios de aceitação do RF106

1. Ver resultados abre o relatório da execução existente.
2. O total geral e os totais por nível coincidem com a resposta.
3. Os filtros de nível aparecem no relatório.

### Pontos a confirmar e limites do RF106

A evidência cobre a abertura e os totais. O funcionamento dos filtros de nível não foi verificado. A documentação usa apenas totais agregados e o recorte do cabeçalho do relatório.

<a id="rf127"></a>


## RF107 — Desativar Risco de Evasão e conferir a persistência e o contador

| Campo | Descrição |
| --- | --- |
| Requisito de QA | Confirmar que a desativação de Risco de Evasão persiste após Atualizar e que o resumo acompanha a desativação e a restauração do estado ativo. |
| Ator | Usuário autenticado com permissão para a operação. |
| Pré-condições | Sessão autenticada na Central, com Risco de Evasão como a única automação ativa no cenário de teste. |
| Gatilho | Desativar Risco de Evasão, acionar Atualizar e reativá-la. |
| Caso | [CT-RF107](Cenario_Teste/CT-RF107_Central_Desativar_Risco_Evasao_Contador.md) |
| Situação observada | Reprovado nas evidências. A desativação persistiu. Após reativar Risco de Evasão, o cartão ficou ativo e o contador continuou em zero. |
| Defeito | [BUG-049](Relatorio-de-Bugs.md#bug-049), em triagem |
| Evidências | [Jam — PED-02 — Desativar Risco de Evasão](https://jam.dev/c/b63ec55f-f8b6-41aa-af4c-d4cdd4515de8) e [Evidências](Evidencias/CT-RF135_Central_Desativar_Risco_Evasao_Contador/README.md). |

### Critérios de aceitação do RF107

1. A desativação é salva e permanece após Atualizar.
2. O contador chega a zero quando nenhuma automação está ativa.
3. Após reativar com sucesso, o cartão e o contador refletem o novo estado.

### Pontos a confirmar e limites do RF107

A persistência foi confirmada por nova leitura para a desativação. Após a reativação, a gravação não contém outro clique em Atualizar. A ordem em que o servidor processou o salvamento e o resumo não foi determinada.

<a id="rf110"></a>


## RF108 — Conferir a execução de Risco de Evasão na Central e em Resultados IA

| Campo | Descrição |
| --- | --- |
| Requisito de QA | Refletir a nova execução da automação Risco de Evasão na Central e no resumo de Resultados IA. |
| Ator | Usuário autenticado com permissão para a operação. |
| Pré-condições | Sessão autenticada com acesso à Central e a Resultados IA. Automação Risco de Evasão habilitada em ambiente de teste autorizado. |
| Gatilho | Acionar Executar agora em Risco de Evasão e consultar o filtro Hoje em Resultados IA. |
| Caso | [CT-RF108](Cenario_Teste/CT-RF108_Central_Resultados_IA_Execucao_Evasao.md) |
| Situação observada | Aprovado conforme a gravação. A Central passou a mostrar 00:55. A linha do tempo de Hoje e o resumo de Resultados IA incluíram essa execução. |
| Defeito | Nenhum no fluxo avaliado |
| Evidências | [Jam — PED-14 — Execução de Risco de Evasão](https://jam.dev/c/efe26a44-458a-4802-bd48-8e23c5ac5fd9) e [Evidências](Evidencias/CT-RF123_Central_Resultados_IA_Execucao_Evasao/README.md). |

### Critérios de aceitação do RF108

1. A execução manual retorna sucesso e atualiza a atividade recente.
2. Resultados IA inclui a execução no período correto.
3. A automação e o horário de última execução coincidem nas duas telas.

### Pontos a confirmar e limites do RF108

A hora de 00:55 é a referência exibida pelo SIFIT. O teste valida a exibição do mesmo registro nas duas telas. O recebimento efetivo pelo canal de envio e a regra dos cartões de risco não foram verificados.

<a id="rf126"></a>


## RF109 — Abrir Aniversariantes e conferir a prévia da automação

| Campo | Descrição |
| --- | --- |
| Requisito de QA | Abrir a configuração de Aniversariantes e apresentar uma prévia coerente com a automação selecionada. |
| Ator | Usuário autenticado com permissão para a operação. |
| Pré-condições | Sessão autenticada com acesso à Central de Automações e cartão Aniversariantes disponível. |
| Gatilho | Acionar Configurar no cartão Aniversariantes e rolar até Preview do relatório. |
| Caso | [CT-RF109](Cenario_Teste/CT-RF109_Central_Aniversariantes_Previa_Risco.md) |
| Situação observada | Reprovado nas evidências. O painel Aniversariantes abriu corretamente, mas a prévia exibiu dados de risco de evasão. |
| Defeito | [BUG-048](Relatorio-de-Bugs.md#bug-048), em triagem |
| Evidências | [Jam — PED-07 — Configuração de Aniversariantes](https://jam.dev/c/c66d4d01-aee2-4037-a8fd-858da21a0a14) e [Evidências](Evidencias/CT-RF129_Central_Aniversariantes_Previa_Risco/README.md). |

### Critérios de aceitação do RF109

1. Configurar abre o painel com o título da automação selecionada.
2. A prévia de Aniversariantes apresenta conteúdo compatível com aniversários.
3. Cancelar fecha o painel e preserva o estado do cartão.

### Pontos a confirmar e limites do RF109

A divergência foi observada na prévia do painel. O envio real, o conteúdo recebido e a persistência de alterações não foram exercitados.

<a id="rf111"></a>


## RF110 — Ativar Aniversariantes e conferir a persistência e o contador

| Campo | Descrição |
| --- | --- |
| Requisito de QA | Confirmar que a ativação de Aniversariantes permanece após Atualizar e que o contador acompanha a alteração salva. |
| Ator | Usuário autenticado com permissão para a operação. |
| Pré-condições | Sessão autenticada na Central. Aniversariantes inativa e Risco de Evasão ativa na configuração de teste. |
| Gatilho | Ativar Aniversariantes no cartão e acionar Atualizar. |
| Caso | [CT-RF110](Cenario_Teste/CT-RF110_Central_Ativar_Aniversariantes_Contador.md) |
| Situação observada | Reprovado nas evidências. A ativação persistiu. O resumo ficou em uma automação ativa até Atualizar, quando passou a duas. |
| Defeito | [BUG-049](Relatorio-de-Bugs.md#bug-049), em triagem |
| Evidências | [Jam — PED-03 — Ativar Aniversariantes](https://jam.dev/c/60c724da-6760-4238-91f5-2ddad8f42bb3) e [Evidências](Evidencias/CT-RF136_Central_Ativar_Aniversariantes_Contador/README.md). |

### Critérios de aceitação do RF110

1. O cartão indica o estado ativo após o salvamento.
2. O resumo passa a duas automações ativas depois de o salvamento concluir.
3. Após Atualizar, a automação permanece ativa e o resumo mantém o mesmo total.

### Pontos a confirmar e limites do RF110

O estado ativo persistiu após Atualizar. A divergência observada ocorreu entre o cartão e o resumo depois do salvamento da ativação. A gravação não confirma a causa no servidor.

<a id="rf105"></a>


## RF111 — Verificar recursos marcados como Em desenvolvimento

| Campo | Descrição |
| --- | --- |
| Requisito de QA | Identificar visualmente os recursos em desenvolvimento e impedir que os cartões iniciem um fluxo ainda indisponível. |
| Ator | Usuário autenticado com permissão para a operação. |
| Pré-condições | Sessão autenticada com acesso à Central de Automações e seção Automações disponíveis visível. |
| Gatilho | Clicar nos quatro cartões ou em seus selos Em desenvolvimento. |
| Caso | [CT-RF111](Cenario_Teste/CT-RF111_Central_Recursos_Em_Desenvolvimento.md) |
| Situação observada | Aprovado conforme a gravação. Os quatro recursos exibiram Em desenvolvimento. Os cliques não iniciaram navegação, configuração ou execução. |
| Defeito | Nenhum no fluxo avaliado |
| Evidências | [Jam — PED-08 — Recursos em desenvolvimento](https://jam.dev/c/0a7ae8fb-980d-4df2-8ef8-de78d6b11b8f) e [Evidências](Evidencias/CT-RF130_Central_Recursos_Em_Desenvolvimento/README.md). |

### Critérios de aceitação do RF111

1. Os quatro recursos indicam Em desenvolvimento.
2. Os cliques não iniciam um fluxo indisponível.
3. A Central mantém a seção e os estados exibidos.

### Pontos a confirmar e limites do RF111

A gravação cobre interações com mouse nos cartões nessa versão. A navegação por teclado e o comportamento após a futura liberação dos recursos não foram verificados.

<a id="rf113"></a>


## RF112 — Atualizar a Central de Automações

| Campo | Descrição |
| --- | --- |
| Requisito de QA | Reconsultar o resumo, a atividade recente e os cartões ao acionar Atualizar na Central de Automações. |
| Ator | Usuário autenticado com permissão para a operação. |
| Pré-condições | Sessão autenticada com acesso à Central e pelo menos uma automação disponível. Registrar o estado inicial. |
| Gatilho | Clicar em Atualizar na Central de Automações. |
| Caso | [CT-RF112](Cenario_Teste/CT-RF112_Central_Automacoes_Atualizar.md) |
| Situação observada | Aprovado conforme a gravação. Quatro cliques atualizaram resumo, execuções e cartões com HTTP 200. Os valores permaneceram consistentes na base gravada. |
| Defeito | Nenhum no fluxo avaliado |
| Evidências | [Jam — PED-01 — Atualizar Central de Automações](https://jam.dev/c/efe35b08-8733-434c-a6fa-32c45e248ae1) e [Evidências](Evidencias/CT-RF134_Central_Automacoes_Atualizar/README.md). |

### Critérios de aceitação do RF112

1. Atualizar reconsulta resumo, execuções e automações.
2. Os indicadores e a atividade recente refletem os dados recebidos.
3. Com a base estável, as consultas repetidas mantêm os mesmos valores.

### Pontos a confirmar e limites do RF112

A gravação verifica atualização com dados estáveis. A reação a uma mudança da base e o tratamento de falhas de rede não foram exercitados.

<a id="rf107"></a>


## RF113 — Filtrar Resultados da Inteligência por Hoje

| Campo | Descrição |
| --- | --- |
| Requisito de QA | Selecionar Hoje e refletir o recorte de um dia nos resultados e nos indicadores apresentados. |
| Ator | Usuário autenticado com permissão para a operação. |
| Pré-condições | Sessão autenticada com acesso a Resultados IA e valores de referência para Hoje e Últimos 7 dias. |
| Gatilho | Selecionar Hoje com Últimos 7 dias ativo. |
| Caso | [CT-RF113](Cenario_Teste/CT-RF113_Resultados_IA_Filtro_Hoje.md) |
| Situação observada | Aprovado conforme a gravação. Hoje consultou um dia e o total de aniversariantes passou de 2 para 0, como na resposta. |
| Defeito | Nenhum no fluxo avaliado |
| Evidências | [Jam — PED-09 — Hoje](https://jam.dev/c/a83c4c74-0b8e-4242-9612-0202c9063d56) e [Evidências](Evidencias/CT-RF131_Resultados_IA_Filtro_Hoje/README.md). |

### Critérios de aceitação do RF113

1. Hoje fica destacado após a consulta.
2. A API identifica o período de um dia.
3. Os indicadores exibidos correspondem à resposta desse período.

### Pontos a confirmar e limites do RF113

A troca do filtro e o retorno da API foram confirmados. O limite de horário do dia e o fuso usado pelo sistema não foram validados com dados controlados.

<a id="rf114"></a>


## RF114 — Filtrar Resultados da Inteligência pelos últimos 7 dias

| Campo | Descrição |
| --- | --- |
| Requisito de QA | Voltar de Hoje a Últimos 7 dias e atualizar o resumo com o recorte semanal. |
| Ator | Usuário autenticado com permissão para a operação. |
| Pré-condições | Sessão autenticada com acesso a Resultados IA e dados distintos entre Hoje e Últimos 7 dias. |
| Gatilho | Selecionar Últimos 7 dias após consultar Hoje. |
| Caso | [CT-RF114](Cenario_Teste/CT-RF114_Resultados_IA_Filtro_7_Dias.md) |
| Situação observada | Aprovado conforme a gravação. Ao voltar de Hoje para Últimos 7 dias, o cartão Aniversariantes passou de 0 para 2. |
| Defeito | Nenhum no fluxo avaliado |
| Evidências | [Jam — PED-10 — Últimos 7 dias](https://jam.dev/c/cbf45b87-b7b6-4314-a359-c5e706aa755e) e [Evidências](Evidencias/CT-RF132_Resultados_IA_Filtro_7_Dias/README.md). |

### Critérios de aceitação do RF114

1. Últimos 7 dias fica destacado após a seleção.
2. O GET identifica `periodo=7` e retorna `dias: 7`.
3. A interface reflete os indicadores e a cronologia do recorte retornado.

### Pontos a confirmar e limites do RF114

Foi confirmada a mudança de recorte na interface e na API. A fronteira dos sete dias e a data de cada item não foram validadas com uma base controlada.

<a id="rf115"></a>


## RF115 — Filtrar Resultados da Inteligência pelos últimos 30 dias

| Campo | Descrição |
| --- | --- |
| Requisito de QA | Atualizar os indicadores e a linha do tempo ao selecionar 30 dias e confirmar o resultado ao voltar ao mesmo filtro. |
| Ator | Usuário autenticado com permissão para a operação. |
| Pré-condições | Sessão autenticada com acesso a Resultados IA e automações registradas em períodos que diferenciem 7 e 30 dias. |
| Gatilho | Selecionar Últimos 30 dias, alternar para Últimos 7 dias e voltar a 30 dias. |
| Caso | [CT-RF115](Cenario_Teste/CT-RF115_Resultados_IA_Filtro_30_Dias.md) |
| Situação observada | Aprovado conforme a gravação. O filtro de 30 dias apresentou 12 automações, 12 relatórios e 6 aniversariantes nas duas seleções. |
| Defeito | Nenhum no fluxo avaliado |
| Evidências | [Jam — PED-11 — Últimos 30 dias](https://jam.dev/c/2756d5c1-a823-482b-bf8d-878357b8b087) e [Evidências](Evidencias/CT-RF133_Resultados_IA_Filtro_30_Dias/README.md). |

### Critérios de aceitação do RF115

1. Últimos 30 dias permanece destacado após o carregamento.
2. Cartões e linha do tempo correspondem à resposta de 30 dias.
3. Alternar para 7 e retornar a 30 atualiza e restaura os resultados esperados.

### Pontos a confirmar e limites do RF115

O teste confirma troca de filtro e consistência com a API. Os limites de data e a regra dos cartões que ficaram constantes exigem dados de controle.

<a id="rf112"></a>


## RF116 — Filtrar Resultados da Inteligência pelos últimos 90 dias

| Campo | Descrição |
| --- | --- |
| Requisito de QA | Atualizar os cartões e a linha do tempo quando o usuário seleciona Últimos 90 dias em Resultados da Inteligência. |
| Ator | Usuário autenticado com permissão para a operação. |
| Pré-condições | Sessão autenticada com acesso a Resultados IA e automações registradas em datas que diferenciem os períodos de 7, 30 e 90 dias. |
| Gatilho | Selecionar Últimos 90 dias e alternar para Últimos 30 dias e de volta. |
| Caso | [CT-RF116](Cenario_Teste/CT-RF116_Resultados_IA_Filtro_90_Dias.md) |
| Situação observada | Aprovado conforme a gravação. Cartões e linha do tempo acompanharam a troca de 7, 30 e 90 dias. Os resultados de 90 dias se repetiram. |
| Defeito | Nenhum no fluxo avaliado |
| Evidências | [Jam — PED-12 — Últimos 90 dias](https://jam.dev/c/1728cfc2-1d36-4ea4-ab68-68a84458c359) e [Evidências](Evidencias/CT-RF122_Resultados_IA_Filtro_90_Dias/README.md). |

### Critérios de aceitação do RF116

1. O filtro de 90 dias permanece destacado após carregar.
2. Os cartões e a linha do tempo correspondem à resposta para o período selecionado.
3. Alternar entre 30 e 90 dias atualiza os resultados e reaplicar o mesmo filtro reproduz o resultado da base estável.

### Pontos a confirmar e limites do RF116

A aprovação cobre a troca de filtros e a correspondência entre interface e resposta da API. O recorte nas datas-limite e a regra de cartões que permaneceram constantes não foram conferidos com uma base controlada.

<a id="rf108"></a>


## RF117 — Salvar as configurações gerais de acesso e presença

| Campo | Descrição |
| --- | --- |
| Requisito de QA | As alterações da aba Home de Configurações devem ser salvas com confirmação ao usuário, persistir após recarga, respeitar a faixa válida de cada campo e refletir-se nos cartões de resumo e no menu lateral. |
| Ator | Usuário autenticado com permissão para alterar as Configurações. |
| Pré-condições | Valores iniciais registrados; regra de cada opção e do campo de dias definida com o produto. |
| Gatilho | Alterar as opções e o campo de dias da aba Home e acionar Salvar Configurações. |
| Caso | [CT-RF117](Cenario_Teste/CT-RF117_Configuracoes_Home_Salvamento.md) |
| Situação observada | A validar — regra ou contexto pendente. As alterações são refletidas nos cartões e no menu lateral após o envio, sem mensagem de confirmação visível; o campo de dias vai de -120 para 1100 sem validação visível. |
| Defeito | Sem defeito confirmado |
| Evidências | [Jam](https://jam.dev/c/e6e551ef-9196-4c79-b6a2-89747b1e8b33) e [Evidências](Evidencias/CT-RF44_Configuracoes_Home_Salvamento/README.md). |

### Critérios de aceitação do RF117

1. O salvamento informa o resultado (sucesso ou erro) de forma compreensível.
2. As configurações salvas persistem após recarga da página.
3. O campo "Dias para contar cliente como ausente" rejeita valores fora da faixa definida (incluindo negativos).
4. O menu lateral e os cartões de resumo refletem as opções salvas.
5. Cancelar descarta as alterações não salvas.

### Pontos a confirmar e limites do RF117

A mensagem de salvamento, a persistência após recarga, a faixa válida do campo de dias (valor inicial -120 e valor informado 1100) e os corpos das requisições não foram confirmados. As demais abas (Biometria, Avaliação, Aniversário, Pagamento, Integrações e Design) não foram avaliadas.

---

<a id="rf49"></a>


## RF118 — Validar o salvamento com o campo de dias de ausência vazio

| Campo | Descrição |
| --- | --- |
| Requisito de QA | Tratar explicitamente o campo Dias para contar cliente como ausente quando ele é enviado vazio, conforme a regra de obrigatoriedade e de valor padrão. |
| Ator | Usuário autenticado com permissão para a operação. |
| Pré-condições | Sessão autenticada com permissão para alterar Configurações e um valor inicial conhecido para dias de ausência. |
| Gatilho | Esvaziar o campo Dias para contar cliente como ausente e acionar Salvar Configurações. |
| Caso | [CT-RF118](Cenario_Teste/CT-RF118_Configuracoes_Dias_Ausencia_Vazio.md) |
| Situação observada | A validar — regra ou contexto pendente. Campo vazio convertido em 0, com HTTP 200. A recarga e a consulta confirmaram 0. |
| Defeito | Sem defeito confirmado |
| Evidências | [Jam — PED-20 — Dias de ausência vazio](https://jam.dev/c/4e96d4fa-65b5-459b-a795-854496e5753c) e [Evidências](Evidencias/CT-RF116_Configuracoes_Dias_Ausencia_Vazio/README.md). |

### Critérios de aceitação do RF118

1. O sistema aplica a regra acordada para o campo vazio e comunica o resultado.
2. O valor retornado após recarga corresponde ao tratamento definido.
3. Zero explícito e campo vazio são verificados separadamente.

### Pontos a confirmar e limites do RF118

A conversão de vazio para zero e a persistência estão confirmadas. A obrigatoriedade do campo, o significado de zero e o efeito sobre a contagem de clientes ausentes dependem da regra de produto. O CT-RF117 já registra a necessidade de confirmar a faixa.

<a id="rf122"></a>


## RF119 — Salvar um valor válido de dias de ausência

| Campo | Descrição |
| --- | --- |
| Requisito de QA | Salvar um valor inteiro positivo de dias de ausência e confirmar a persistência após recarregar Configurações. |
| Ator | Usuário autenticado com permissão para a operação. |
| Pré-condições | Sessão autenticada com permissão para editar Configurações e valor inicial conhecido. |
| Gatilho | Preencher o campo Dias para contar cliente como ausente com 15 e salvar a configuração. |
| Caso | [CT-RF119](Cenario_Teste/CT-RF119_Configuracoes_Salvar_Dias_Ausencia_Valido.md) |
| Situação observada | Aprovado conforme a gravação. 15 foi salvo e confirmado após recarga. A segunda recarga confirmou a restauração de 1100. |
| Defeito | Nenhum no fluxo avaliado |
| Evidências | [Jam — PED-16 — Salvar dias de ausência](https://jam.dev/c/12d6bba7-a67e-4882-86a5-4dd08d194af2) e [Evidências](Evidencias/CT-RF125_Configuracoes_Salvar_Dias_Ausencia_Valido/README.md). |

### Critérios de aceitação do RF119

1. Um valor válido é enviado e confirmado pela API.
2. Depois da recarga, o formulário apresenta o valor informado.
3. O valor inicial pode ser restaurado e lido após nova recarga.

### Pontos a confirmar e limites do RF119

A evidência confirma persistência para o valor testado e restauração do valor original observado. A faixa completa e o efeito na contagem de clientes ausentes exigem outros casos.

<a id="rf120"></a>


## RF120 — Bloquear número negativo no campo de dias de ausência

| Campo | Descrição |
| --- | --- |
| Requisito de QA | Impedir o salvamento de valor negativo para dias de ausência e preservar a configuração anterior, conforme o critério do RF117. |
| Ator | Usuário autenticado com permissão para a operação. |
| Pré-condições | Sessão autenticada com acesso a Configurações > Home e valor inicial conhecido para dias de ausência. |
| Gatilho | Informar -1 no campo Dias para contar cliente como ausente e acionar Salvar Configurações. |
| Caso | [CT-RF120](Cenario_Teste/CT-RF120_Configuracoes_Dias_Ausencia_Negativo.md) |
| Situação observada | Reprovado nas evidências. -1 foi aceito com HTTP 200 e confirmado na interface e no GET após recarga. |
| Defeito | [BUG-047](Relatorio-de-Bugs.md#bug-047), em triagem |
| Evidências | [Jam — PED-17 — Dias de ausência negativos](https://jam.dev/c/d5786f67-6e5f-44f5-bbba-fbd763a88740) e [Evidências](Evidencias/CT-RF126_Configuracoes_Dias_Ausencia_Negativo/README.md). |

### Critérios de aceitação do RF120

1. O formulário ou a API bloqueia o salvamento de valor negativo.
2. A interface indica como corrigir a entrada inválida.
3. A recarga preserva o último valor válido.

### Pontos a confirmar e limites do RF120

A evidência confirma a persistência de -1. O efeito sobre a classificação de clientes ausentes e a abrangência para outros negativos não foram exercitados.

<a id="rf121"></a>


## RF121 — Validar letras no campo de dias de ausência

| Campo | Descrição |
| --- | --- |
| Requisito de QA | Rejeitar letras no campo numérico de dias de ausência e tratar o valor vazio resultante conforme a regra de salvamento. |
| Ator | Usuário autenticado com permissão para a operação. |
| Pré-condições | Sessão autenticada com permissão para editar Configurações e valor inicial conhecido no campo de dias de ausência. |
| Gatilho | Apagar o valor do campo, tentar digitar letras e clicar em Salvar Configurações. |
| Caso | [CT-RF121](Cenario_Teste/CT-RF121_Configuracoes_Dias_Ausencia_Texto.md) |
| Situação observada | A validar — regra ou contexto pendente. Letras não apareceram no campo. O salvamento com campo vazio enviou 0 e retornou HTTP 200. |
| Defeito | Sem defeito confirmado |
| Evidências | [Jam — PED-18 — Dias de ausência com texto](https://jam.dev/c/c578ed7a-c11c-4cef-8a6c-84d0244f21a5) e [Evidências](Evidencias/CT-RF127_Configuracoes_Dias_Ausencia_Texto/README.md). |

### Critérios de aceitação do RF121

1. Letras não são aceitas como valor do campo numérico.
2. Se o campo permanecer vazio, o salvamento preserva o valor anterior ou aplica o padrão definido pelo produto.
3. A próxima consulta confirma o comportamento definido para a entrada vazia.

### Pontos a confirmar e limites do RF121

A rejeição da digitação de letras foi observada. A regra para o campo vazio permanece pendente no CT-RF118. A persistência de zero nesta gravação não foi verificada após recarga.

<a id="rf104"></a>


## RF122 — Cancelar uma alteração nas Configurações sem salvar

| Campo | Descrição |
| --- | --- |
| Requisito de QA | Descartar uma alteração feita no formulário de Configurações ao acionar Cancelar e preservar o valor salvo. |
| Ator | Usuário autenticado com permissão para a operação. |
| Pré-condições | Sessão autenticada em Configurações > Home com um valor de dias de ausência já salvo. |
| Gatilho | Alterar o valor do campo e acionar Cancelar. |
| Caso | [CT-RF122](Cenario_Teste/CT-RF122_Configuracoes_Cancelar_Alteracao.md) |
| Situação observada | Aprovado conforme a gravação. Cancelar levou à Página Inicial. O GET ao reabrir Configurações confirmou o valor original 1100. |
| Defeito | Nenhum no fluxo avaliado |
| Evidências | [Jam — PED-20 — Cancelar alteração](https://jam.dev/c/e8faa199-1177-4563-8b00-590606669a1d) e [Evidências](Evidencias/CT-RF117_Configuracoes_Cancelar_Alteracao/README.md). |

### Critérios de aceitação do RF122

1. Cancelar encerra a edição e retorna à Página Inicial.
2. O valor temporário não é gravado.
3. A consulta e a interface apresentam o valor original ao reabrir.

### Pontos a confirmar e limites do RF122

O cancelamento foi verificado para uma alteração no campo de dias de ausência na aba Home. Alterações simultâneas e as demais abas ficam para nova execução.

<a id="rf123"></a>


## RF123 — Alterar e persistir a opção Trabalha com turmas?

| Campo | Descrição |
| --- | --- |
| Requisito de QA | Salvar os estados Sim e Não da opção Trabalha com turmas? e refletir a escolha após recarregar a página. |
| Ator | Usuário autenticado com permissão para a operação. |
| Pré-condições | Sessão autenticada em Configurações > Home com permissão para alterar a opção e valor inicial identificado. |
| Gatilho | Alternar a opção Trabalha com turmas? e acionar Salvar Configurações. |
| Caso | [CT-RF123](Cenario_Teste/CT-RF123_Configuracoes_Trabalha_Com_Turmas.md) |
| Situação observada | Aprovado conforme a gravação. Sim → Não → Sim. Os dois POST e os GET após recarga confirmaram os valores de `usa_turmas`. |
| Defeito | Nenhum no fluxo avaliado |
| Evidências | [Jam — PED-21 — Trabalha com turmas](https://jam.dev/c/a51c33a5-537a-40fd-a55d-990b70ac0696) e [Evidências](Evidencias/CT-RF118_Configuracoes_Trabalha_Com_Turmas/README.md). |

### Critérios de aceitação do RF123

1. Salvar Não atualiza a configuração.
2. Salvar Sim atualiza a configuração.
3. Após cada recarga, seletor e resposta da API refletem o valor salvo.

### Pontos a confirmar e limites do RF123

A evidência cobre o seletor nas Configurações e o valor retornado após recarga. Os efeitos sobre criação de turmas e sobre o menu Turmas exigem casos específicos.

<a id="rf124"></a>


## RF124 — Conferir a configuração Academia marcada como Box?

| Campo | Descrição |
| --- | --- |
| Requisito de QA | Persistir a configuração Academia marcada como Box? e refletir o estado no cartão SifitBox e no menu Principal. |
| Ator | Usuário autenticado com permissão para a operação. |
| Pré-condições | Sessão autenticada em Configurações > Home, com permissão para alterar o estado de Box e acesso ao menu Principal. |
| Gatilho | Alternar a configuração de Box, salvar e recarregar a página. |
| Caso | [CT-RF124](Cenario_Teste/CT-RF124_Configuracoes_Academia_Marcada_Box.md) |
| Situação observada | Aprovado conforme a gravação. Não → Sim → Não. Seletor, cartão SifitBox e menu Principal acompanharam o estado após recarga. |
| Defeito | Nenhum no fluxo avaliado |
| Evidências | [Jam — PED-22 — Academia marcada como Box](https://jam.dev/c/16dc862d-c3f9-4392-9037-526818e86cd6) e [Evidências](Evidencias/CT-RF119_Configuracoes_Academia_Marcada_Box/README.md). |

### Critérios de aceitação do RF124

1. O seletor carrega Sim e Não conforme a escolha persistida.
2. O cartão SifitBox acompanha cada valor.
3. O menu Principal exibe o item em Sim e o oculta em Não.

### Pontos a confirmar e limites do RF124

Foram verificadas persistência e visibilidade do item no menu. Operações e permissões internas do SifitBox não foram exercitadas.

<a id="rf125"></a>


## RF125 — Conferir a configuração de acesso ao sistema desktop

| Campo | Descrição |
| --- | --- |
| Requisito de QA | Persistir a opção Liberar acesso ao sistema desktop? e manter o cartão Desktop coerente com a opção salva. |
| Ator | Usuário autenticado com permissão para a operação. |
| Pré-condições | Sessão autenticada com permissão para alterar a configuração de acesso desktop. |
| Gatilho | Alterar a opção Liberar acesso ao sistema desktop?, salvar e recarregar. |
| Caso | [CT-RF125](Cenario_Teste/CT-RF125_Configuracoes_Acesso_Desktop.md) |
| Situação observada | Aprovado conforme a gravação. Não → Sim → Não. A API, o seletor e o cartão Desktop refletiram o valor salvo nas duas recargas. |
| Defeito | Nenhum no fluxo avaliado |
| Evidências | [Jam — PED-23 — Acesso desktop](https://jam.dev/c/466be253-ad9a-4856-b567-fb17e1fdd479) e [Evidências](Evidencias/CT-RF120_Configuracoes_Acesso_Desktop/README.md). |

### Critérios de aceitação do RF125

1. O seletor mantém o valor salvo após recarga.
2. O cartão Desktop corresponde ao valor do seletor em cada estado.
3. A consulta retorna o flag `desktop` gravado.

### Pontos a confirmar e limites do RF125

A aprovação cobre Configurações no navegador. A autenticação e o uso efetivo do cliente desktop não foram exercitados.

<a id="rf156"></a>


## RF126 — Navegar pelas abas de Configurações com a senha da biometria protegida

| Campo | Descrição |
| --- | --- |
| Requisito de QA | Abrir as abas de Configurações e manter o valor da senha de integração de biometria mascarado por padrão. |
| Ator | Usuário autenticado com permissão para a operação. |
| Pré-condições | Sessão autenticada com acesso às Configurações. Ambiente de teste com integração de biometria configurada com credencial fictícia. |
| Gatilho | Abrir a aba Biometria e continuar pelas demais abas até retornar a Home. |
| Caso | [CT-RF126](Cenario_Teste/CT-RF126_Configuracoes_Abas_Biometria_Senha.md) |
| Situação observada | Reprovado nas evidências. A navegação funcionou. A aba Biometria exibiu o valor do campo Senha sem mascaramento. |
| Defeito | [BUG-046](Relatorio-de-Bugs.md#bug-046), em triagem |
| Evidências | [Jam — PED-15](https://jam.dev/c/38105352-c89c-492e-bca1-78e2f4017ae2) e [Evidências](Evidencias/CT-RF124_Configuracoes_Abas_Biometria_Senha/README.md). |

### Critérios de aceitação do RF126

1. Cada aba exibe o painel correspondente e a navegação permite retornar a Home.
2. O campo Senha em Biometria é mascarado por padrão ao abrir a aba.
3. Voltar a Biometria ou recarregar a página mantém a proteção visual.

### Pontos a confirmar e limites do RF126

O defeito foi observado na interface de uma sessão autenticada. O alcance por perfil, a exposição em respostas de API e a validade do valor exibido não foram testados. As evidências versionadas mostram apenas os cabeçalhos das abas.

<a id="rf119"></a>


## RF127 — Mascarar a API Key no formulário de WhatsApp

| Campo | Descrição |
| --- | --- |
| Requisito de QA | Manter os caracteres da API Key ocultos durante a edição e ao reabrir a aba Integrações. |
| Ator | Usuário autenticado com permissão para a operação. |
| Pré-condições | Sessão autenticada com acesso a Configurações → Integrações → WhatsApp e uma configuração de teste existente. |
| Gatilho | Editar o campo API Key e reabrir a aba Integrações. |
| Caso | [CT-RF127](Cenario_Teste/CT-RF127_Integracoes_WhatsApp_Mascarar_API_Key.md) |
| Situação observada | Aprovado conforme a gravação. A API Key permaneceu mascarada na edição e na reabertura da aba. A gravação não registrou POST de salvamento. |
| Defeito | Nenhum no fluxo avaliado |
| Evidências | [Jam 1 — Mascaramento da API Key](https://jam.dev/c/ef0b67d5-1eea-49b7-84ea-bb306143df4a) e [Evidências](Evidencias/CT-RF139_Integracoes_WhatsApp_Mascarar_API_Key/README.md). |

### Critérios de aceitação do RF127

1. O valor aparece mascarado no formulário e durante a digitação.
2. Reabrir a aba mantém o campo mascarado.
3. A edição sem salvar não dispara o POST de configuração.

### Pontos a confirmar e limites do RF127

A aprovação cobre o mascaramento visual e a ausência de envio ao editar sem salvar. A gravação não verifica proteção em trânsito ou em armazenamento.

<a id="rf128"></a>


## RF128 — Validar uma URL da API sem formato de endereço

| Campo | Descrição |
| --- | --- |
| Requisito de QA | Verificar se a integração recusa uma URL em formato inválido e orienta a correção do campo. |
| Ator | Usuário autenticado com permissão para a operação. |
| Pré-condições | Sessão autenticada com acesso à integração de WhatsApp. No reteste, preencher os demais campos com dados autorizados. |
| Gatilho | Acionar Salvar Configuração após substituir a URL da API por texto sem formato de endereço. |
| Caso | [CT-RF128](Cenario_Teste/CT-RF128_Integracoes_WhatsApp_Validar_URL_API.md) |
| Situação observada | A validar — regra ou contexto pendente. A tentativa com URL fora do formato também tinha a instância vazia. Houve reconsulta sem POST de configuração, e a regra da URL ficou a validar. |
| Defeito | Sem defeito confirmado |
| Evidências | [Jam 2 — Validação da URL da API](https://jam.dev/c/0d7c7274-c798-4e26-91a3-f8162b7ce932) e [Evidências](Evidencias/CT-RF140_Integracoes_WhatsApp_Validar_URL_API/README.md). |

### Critérios de aceitação do RF128

1. A tentativa com apenas a URL inválida é recusada.
2. A interface identifica a URL como o campo a corrigir.
3. A leitura posterior preserva a configuração anterior.

### Pontos a confirmar e limites do RF128

O Nome da Instância vazio impede atribuir a ausência de POST à regra de URL. A gravação não demonstra qual validação bloqueou a tentativa.

<a id="rf129"></a>


## RF129 — Bloquear o salvamento com Nome da Instância vazio

| Campo | Descrição |
| --- | --- |
| Requisito de QA | Verificar que Nome da Instância preenchido pode ser salvo e que a tentativa com o campo vazio preserva o valor existente. |
| Ator | Usuário autenticado com permissão para a operação. |
| Pré-condições | Sessão autenticada com acesso à integração de WhatsApp e aos dados de teste necessários ao salvamento. |
| Gatilho | Limpar Nome da Instância e acionar Salvar Configuração. |
| Caso | [CT-RF129](Cenario_Teste/CT-RF129_Integracoes_WhatsApp_Instancia_Obrigatoria.md) |
| Situação observada | Aprovado conforme a gravação. O nome preenchido foi salvo. As tentativas com a instância vazia ficaram sem POST e o valor anterior voltou ao reabrir. |
| Defeito | Nenhum no fluxo avaliado |
| Evidências | [Jam 3 — Obrigatoriedade do Nome da Instância](https://jam.dev/c/8bb7f049-0299-49c9-9fb5-ff7b144f58d2) e [Evidências](Evidencias/CT-RF141_Integracoes_WhatsApp_Instancia_Obrigatoria/README.md). |

### Critérios de aceitação do RF129

1. Com o controle positivo, o nome preenchido persiste após a consulta.
2. O campo vazio bloqueia o salvamento.
3. Reabrir a aba mantém o nome gravado antes da tentativa.

### Pontos a confirmar e limites do RF129

A evidência confirma o bloqueio e a persistência do valor anterior. A regra para espaços e o texto da orientação de validação ficam para reteste.

<a id="rf130"></a>


## RF130 — Persistir a opção Ativo da integração de WhatsApp

| Campo | Descrição |
| --- | --- |
| Requisito de QA | Confirmar que a configuração grava e reconsulta os estados marcado e desmarcado da opção Ativo. |
| Ator | Usuário autenticado com permissão para a operação. |
| Pré-condições | Sessão autenticada em Integrações → WhatsApp com formulário de teste preenchido. |
| Gatilho | Marcar e desmarcar Ativo, salvando o formulário a cada alteração. |
| Caso | [CT-RF130](Cenario_Teste/CT-RF130_Integracoes_WhatsApp_Persistir_Ativo.md) |
| Situação observada | Aprovado conforme a gravação. Os dois estados de Ativo foram salvos e confirmados por GET, com a conexão permanecendo desconectada. |
| Defeito | Nenhum no fluxo avaliado |
| Evidências | [Jam 4 — Persistência da opção Ativo](https://jam.dev/c/593bb290-936a-4e01-a5af-cc8041c4eb55) e [Evidências](Evidencias/CT-RF142_Integracoes_WhatsApp_Persistir_Ativo/README.md). |

### Critérios de aceitação do RF130

1. A consulta posterior ao salvamento retorna `ativo: true` ao marcar.
2. A consulta posterior ao salvamento retorna `ativo: false` ao desmarcar.
3. O formulário reflete o estado salvo em ambas as consultas.

### Pontos a confirmar e limites do RF130

A aprovação é restrita à persistência da opção. A execução de automações e o envio de mensagens não foram exercitados.

<a id="rf131"></a>


## RF131 — Tratar falha ao conectar WhatsApp via Evolution API

| Campo | Descrição |
| --- | --- |
| Requisito de QA | Verificar a consistência entre a resposta da API e a mensagem da tela quando a tentativa de conexão com WhatsApp falha. |
| Ator | Usuário autenticado com permissão para a operação. |
| Pré-condições | Sessão autenticada na integração de WhatsApp com um provedor de teste. Preparar uma falha controlada com a equipe responsável pelo ambiente. |
| Gatilho | Acionar Conectar WhatsApp quando a tentativa de conexão encontra uma falha. |
| Caso | [CT-RF131](Cenario_Teste/CT-RF131_Integracoes_WhatsApp_Conectar_Evolution.md) |
| Situação observada | Reprovado nas evidências. As duas tentativas exibiram falha. A resposta trouxe a mesma falha, mas devolveu `verifica_erro: false`. |
| Defeito | [BUG-050](Relatorio-de-Bugs.md#bug-050), em triagem |
| Evidências | [Jam 5 — Tentativas de conexão pela Evolution API](https://jam.dev/c/087b5e4f-7d73-4be3-979d-9a39f474b836) e [Evidências](Evidencias/CT-RF143_Integracoes_WhatsApp_Conectar_Evolution/README.md). |

### Critérios de aceitação do RF131

1. A tentativa com falha é indicada como falha no contrato da API e na interface.
2. O estado informado permanece coerente com a ausência de sessão conectada.
3. O retorno de falha não disponibiliza QR Code como se a tentativa tivesse sido bem-sucedida.

### Pontos a confirmar e limites do RF131

Os parâmetros do provedor não foram validados. A causa da falha de conexão e o caminho de sucesso exigem testes controlados. O defeito registrado é a divergência da flag de erro.

<a id="rf132"></a>


## RF132 — Consultar novamente o status da integração de WhatsApp

| Campo | Descrição |
| --- | --- |
| Requisito de QA | Verificar se Atualizar Status reconsulta o serviço e devolve o estado atual da integração. |
| Ator | Usuário autenticado com permissão para a operação. |
| Pré-condições | Sessão autenticada em Integrações → WhatsApp com o cartão Atualizar Status disponível e integração desconectada. |
| Gatilho | Acionar Atualizar no cartão Atualizar Status. |
| Caso | [CT-RF132](Cenario_Teste/CT-RF132_Integracoes_WhatsApp_Atualizar_Status.md) |
| Situação observada | Aprovado conforme a gravação. Sete consultas retornaram HTTP 200 com o estado desconectado e o horário de verificação atualizado. |
| Defeito | [BUG-050](Relatorio-de-Bugs.md#bug-050) na tentativa posterior de conexão |
| Evidências | [Jam 6 — Atualização manual de status](https://jam.dev/c/0da79ab0-b557-46af-a48c-60c1a8a62628) e [Evidências](Evidencias/CT-RF144_Integracoes_WhatsApp_Atualizar_Status/README.md). |

### Critérios de aceitação do RF132

1. Cada clique registrado dispara a consulta de status.
2. A resposta da consulta devolve o estado da conexão e a última verificação.
3. Quando a integração permanece desconectada, a consulta continua retornando esse estado.

### Pontos a confirmar e limites do RF132

A aprovação cobre o comando de consulta e a resposta em estado desconectado. A gravação não mostra a atualização visual do cartão de resumo após os cliques. A conexão posterior tem evidência vinculada ao BUG-050.

<a id="rf134"></a>


## RF133 — Atualizar a verificação do WhatsApp enquanto aguarda QR Code

| Campo | Descrição |
| --- | --- |
| Requisito de QA | Confirmar a atualização visual da última verificação quando o serviço ainda informa que a integração está aguardando QR Code. |
| Ator | Usuário autenticado com permissão para a operação. |
| Pré-condições | Sessão autenticada na integração de WhatsApp com status Aguardando QR Code e ação Atualizar disponível. |
| Gatilho | Acionar Atualizar no cartão Atualizar Status e retornar ao resumo da conexão. |
| Caso | [CT-RF133](Cenario_Teste/CT-RF133_Integracoes_WhatsApp_Atualizar_Status_Aguardando_QR.md) |
| Situação observada | Aprovado conforme a gravação. A API manteve o estado conectando, e a tela continuou em Aguardando QR Code com a verificação atualizada de 02:32 para 02:35. |
| Defeito | Nenhum no fluxo avaliado |
| Evidências | [Jam 6 — Atualização de status enquanto aguarda QR Code](https://jam.dev/c/7a892fd3-b6b0-49bc-a463-1b79c4b6ad50) e [Evidências](Evidencias/CT-RF150_Integracoes_WhatsApp_Atualizar_Status_Aguardando_QR/README.md). |

### Critérios de aceitação do RF133

1. A ação emite a consulta de status.
2. Com `status: conectando`, a tela mantém Aguardando QR Code.
3. O resumo atualiza o horário de verificação conforme a resposta.

### Pontos a confirmar e limites do RF133

O horário citado é o exibido pelo SIFIT e pela API. A gravação cobre a consulta em espera. Pareamento e mudança para conectado não foram exercitados.

<a id="rf142"></a>


## RF134 — Salvar mensagens de aniversário para WhatsApp e SMS

| Campo | Descrição |
| --- | --- |
| Requisito de QA | Confirmar que os canais WhatsApp e SMS e suas mensagens de aniversário persistem após salvar e reabrir a aba. |
| Ator | Usuário autenticado com permissão para a operação. |
| Pré-condições | Sessão autenticada com acesso à aba Aniversário e permissão para alterar as configurações de teste. |
| Gatilho | Marcar WhatsApp e SMS, editar os textos e clicar em Salvar Configurações. |
| Caso | [CT-RF134](Cenario_Teste/CT-RF134_Configuracoes_Aniversario_Salvar_WhatsApp_SMS.md) |
| Situação observada | Aprovado conforme a gravação. WhatsApp e SMS e os dois textos de teste reapareceram após recarregar e reabrir Aniversário. |
| Defeito | Nenhum no fluxo avaliado |
| Evidências | [Jam 1 — Mensagens de aniversário por WhatsApp e SMS](https://jam.dev/c/01502381-e54a-40c9-b65b-e87c7f049154) e [Evidências](Evidencias/CT-RF145_Configuracoes_Aniversario_Salvar_WhatsApp_SMS/README.md). |

### Critérios de aceitação do RF134

1. O salvamento aceita os dois canais e suas mensagens.
2. A nova leitura confirma as opções habilitadas e as mensagens editadas.
3. A interface mostra os valores salvos ao reabrir a aba.

### Pontos a confirmar e limites do RF134

A gravação verifica a configuração. O disparo automático, a entrega e a substituição das variáveis das mensagens estão fora da evidência.

<a id="rf138"></a>


## RF135 — Desabilitar o envio automático de aniversário

| Campo | Descrição |
| --- | --- |
| Requisito de QA | Confirmar que o valor Desabilitado de Envio automático permanece salvo após recarregar e reabrir Aniversário. |
| Ator | Usuário autenticado com permissão para a operação. |
| Pré-condições | Sessão autenticada com permissão para editar Configurações → Aniversário. Registrar o valor inicial com a base de teste. |
| Gatilho | Selecionar Desabilitado em Envio automático e clicar em Salvar Configurações. |
| Caso | [CT-RF135](Cenario_Teste/CT-RF135_Configuracoes_Aniversario_Desabilitar_Envio_Automatico.md) |
| Situação observada | Aprovado conforme a gravação. A consulta e a aba Aniversário confirmaram Desabilitado após recarregar. |
| Defeito | Nenhum no fluxo avaliado |
| Evidências | [Jam 4 — Desativação do envio automático de aniversário](https://jam.dev/c/ee8a2ba9-164c-42bb-8efe-927dd6c534d5) e [Evidências](Evidencias/CT-RF154_Configuracoes_Aniversario_Desabilitar_Envio_Automatico/README.md). |

### Critérios de aceitação do RF135

1. O salvamento de Desabilitado retorna sucesso.
2. O GET após recarregar devolve `enviar_mensagens_aniversario: nao`.
3. O seletor mantém Desabilitado após reabrir a aba.

### Pontos a confirmar e limites do RF135

Os canais estavam desmarcados na gravação. O disparo de mensagens e a interação com canais já habilitados não foram exercitados.

<a id="rf136"></a>


## RF136 — Cancelar a edição da mensagem de aniversário do WhatsApp

| Campo | Descrição |
| --- | --- |
| Requisito de QA | Verificar que Cancelar descarta a edição do texto e a seleção temporária do canal WhatsApp. |
| Ator | Usuário autenticado com permissão para a operação. |
| Pré-condições | Sessão autenticada em Configurações → Aniversário com uma mensagem de WhatsApp cadastrada e o canal desmarcado. |
| Gatilho | Marcar WhatsApp, editar o texto e clicar em Cancelar. |
| Caso | [CT-RF136](Cenario_Teste/CT-RF136_Configuracoes_Aniversario_Cancelar_Mensagem_WhatsApp.md) |
| Situação observada | Aprovado conforme a gravação. Cancelar retornou à Página Inicial e preservou a seleção do canal e a mensagem anterior. |
| Defeito | Nenhum no fluxo avaliado |
| Evidências | [Jam 5 — Cancelamento da edição da mensagem de WhatsApp](https://jam.dev/c/a58b851c-77c2-4a49-be3b-8a5c007d2bcb) e [Evidências](Evidencias/CT-RF155_Configuracoes_Aniversario_Cancelar_Mensagem_WhatsApp/README.md). |

### Critérios de aceitação do RF136

1. Cancelar volta à Página Inicial sem POST de salvamento.
2. O canal permanece desmarcado após a consulta.
3. A mensagem anterior reaparece ao marcar o canal no formulário.

### Pontos a confirmar e limites do RF136

O resultado cobre o cancelamento antes de salvar na aba Aniversário. O envio da mensagem não foi exercitado.

<a id="rf137"></a>


## RF137 — Inserir variáveis na mensagem de aniversário do WhatsApp

| Campo | Descrição |
| --- | --- |
| Requisito de QA | Verificar que as variáveis selecionadas no painel aparecem no campo WhatsApp e que Cancelar descarta essa edição. |
| Ator | Usuário autenticado com permissão para a operação. |
| Pré-condições | Sessão autenticada em Configurações → Aniversário com acesso ao campo WhatsApp e ao painel Variáveis disponíveis. |
| Gatilho | Editar a mensagem de WhatsApp, clicar nas variáveis e depois em Cancelar. |
| Caso | [CT-RF137](Cenario_Teste/CT-RF137_Configuracoes_Aniversario_Inserir_Variaveis_WhatsApp.md) |
| Situação observada | Aprovado conforme a gravação. As quatro variáveis apareceram no editor na ordem selecionada. Ao cancelar, a mensagem anterior foi preservada. |
| Defeito | Nenhum no fluxo avaliado |
| Evidências | [Jam 6 — Inserção de variáveis na mensagem de WhatsApp](https://jam.dev/c/fb2c4949-c68d-4f90-b47c-44da9dbe58a3) e [Evidências](Evidencias/CT-RF156_Configuracoes_Aniversario_Inserir_Variaveis_WhatsApp/README.md). |

### Critérios de aceitação do RF137

1. Cada clique insere o marcador correspondente no campo WhatsApp.
2. Os marcadores permanecem na ordem em que foram selecionados.
3. A edição temporária é descartada com Cancelar.

### Pontos a confirmar e limites do RF137

O caso verifica a inserção dos marcadores no editor e o descarte da edição. A substituição por dados reais e o envio não foram exercitados.

<a id="rf157"></a>


## RF138 — Persistir a desativação do Pagamento Online

| Campo | Descrição |
| --- | --- |
| Requisito de QA | Confirmar que a opção Pagamento Online pode ser alterada para Não e mantém esse valor após recarregar. |
| Ator | Usuário autenticado com permissão para a operação. |
| Pré-condições | Sessão autenticada com acesso à aba Pagamento e uma configuração de teste com Pagamento Online habilitado. |
| Gatilho | Selecionar Não em Pagamento Online e salvar. |
| Caso | [CT-RF138](Cenario_Teste/CT-RF138_Configuracoes_Pagamento_Online_Desativar.md) |
| Situação observada | Aprovado conforme a gravação. A resposta e a tela confirmaram Não após recarregar. O salvamento de restauração para Sim retornou sucesso. |
| Defeito | Nenhum no fluxo avaliado |
| Evidências | [Jam 2 — Desativação do Pagamento Online](https://jam.dev/c/845de9b6-12f7-4002-a8ba-82e1a85affba) e [Evidências](Evidencias/CT-RF146_Configuracoes_Pagamento_Online_Desativar/README.md). |

### Critérios de aceitação do RF138

1. Salvar Não retorna sucesso.
2. O GET posterior retorna `pagarme: nao`.
3. A aba indica Não após ser reaberta.

### Pontos a confirmar e limites do RF138

A aprovação cobre a persistência de Não. A gravação termina após o POST de restauração, sem nova leitura de Sim. Cobrança e validação do token não foram exercitadas.

<a id="rf139"></a>


## RF139 — Salvar uma Cor Principal hexadecimal válida

| Campo | Descrição |
| --- | --- |
| Requisito de QA | Confirmar que uma Cor Principal em formato hexadecimal válido é persistida e apresentada ao reabrir Design. |
| Ator | Usuário autenticado com permissão para a operação. |
| Pré-condições | Sessão autenticada com acesso à aba Design. Registrar a Cor Principal inicial. |
| Gatilho | Editar a Cor Principal para #663399 e salvar. |
| Caso | [CT-RF139](Cenario_Teste/CT-RF139_Configuracoes_Design_Salvar_Cor_Principal.md) |
| Situação observada | Aprovado conforme a gravação. O código #663399 persistiu e a aba Design exibiu o valor com a amostra correspondente. |
| Defeito | Nenhum no fluxo avaliado |
| Evidências | [Jam 3 — Persistência da Cor Principal](https://jam.dev/c/c4f77e18-3b66-4c68-97e7-bd70a9bb70f9) e [Evidências](Evidencias/CT-RF147_Configuracoes_Design_Salvar_Cor_Principal/README.md). |

### Critérios de aceitação do RF139

1. O código válido é aceito pelo salvamento.
2. A consulta devolve o código salvo.
3. O campo e a amostra representam a nova cor ao reabrir.

### Pontos a confirmar e limites do RF139

O resultado cobre a Cor Principal e a amostra da aba Design. A aplicação da cor nos ambientes online não foi verificada.

<a id="rf140"></a>


## RF140 — Rejeitar código hexadecimal inválido na Cor Secundária

| Campo | Descrição |
| --- | --- |
| Requisito de QA | Verificar o bloqueio de código fora do formato hexadecimal no campo Cor Secundária e a preservação da cor já salva. |
| Ator | Usuário autenticado com permissão para a operação. |
| Pré-condições | Sessão autenticada em Design e uma Cor Secundária válida salva como referência. |
| Gatilho | Preencher Cor Secundária com #ZZZZZZ e salvar. |
| Caso | [CT-RF140](Cenario_Teste/CT-RF140_Configuracoes_Design_Validar_Cor_Secundaria.md) |
| Situação observada | Reprovado nas evidências. As duas tentativas com #ZZZZZZ retornaram sucesso. O código fora do conjunto hexadecimal persistiu após recarregar. |
| Defeito | [BUG-051](Relatorio-de-Bugs.md#bug-051), em triagem |
| Evidências | [Jam 4 — Validação da Cor Secundária](https://jam.dev/c/41aaf50a-2506-471a-8eeb-943674571771) e [Evidências](Evidencias/CT-RF148_Configuracoes_Design_Validar_Cor_Secundaria/README.md). |

### Critérios de aceitação do RF140

1. O valor com caracteres fora da faixa hexadecimal é rejeitado.
2. A interface identifica Cor Secundária como o campo a corrigir.
3. O valor inválido não substitui a última configuração válida.

### Pontos a confirmar e limites do RF140

O defeito foi confirmado pela leitura posterior. O efeito do código inválido nos ambientes online não foi avaliado.

<a id="rf141"></a>


## RF141 — Informar o limite de tamanho ao rejeitar o logo

| Campo | Descrição |
| --- | --- |
| Requisito de QA | Verificar se a rejeição de logo por tamanho informa ao usuário o limite retornado pela API. |
| Ator | Usuário autenticado com permissão para a operação. |
| Pré-condições | Sessão autenticada com acesso a Design. Preparar arquivos de teste dos formatos aceitos, com tamanhos medidos abaixo e acima de 6 MB. |
| Gatilho | Selecionar um logo recusado pelo limite de tamanho e clicar em Salvar Configurações. |
| Caso | [CT-RF141](Cenario_Teste/CT-RF141_Configuracoes_Design_Logo_Limite_Tamanho.md) |
| Situação observada | Reprovado nas evidências. A API rejeitou pelo limite de 6 MB. A interface exibiu apenas a mensagem genérica de erro ao salvar. |
| Defeito | [BUG-052](Relatorio-de-Bugs.md#bug-052), em triagem |
| Evidências | [Jam 5 — Rejeição de logo pelo limite de tamanho](https://jam.dev/c/7aaeac50-8269-4cd6-b7f6-4c8c3740b0e5) e [Evidências](Evidencias/CT-RF149_Configuracoes_Design_Logo_Limite_Tamanho/README.md). |

### Critérios de aceitação do RF141

1. A API recusa o arquivo acima do limite.
2. A interface informa o tamanho máximo permitido na recusa.
3. O usuário consegue substituir o arquivo e tentar salvar novamente.

### Pontos a confirmar e limites do RF141

O total em bytes corresponde à requisição inteira. O tamanho exato do arquivo e o logo armazenado após recarregar não ficaram demonstrados.

<a id="rf133"></a>


## RF142 — Desativar a cobrança da avaliação do cliente

| Campo | Descrição |
| --- | --- |
| Requisito de QA | Confirmar que o valor Não de Cobrar Avaliação do Cliente permanece salvo após recarregar e reabrir Avaliação. |
| Ator | Usuário autenticado com permissão para a operação. |
| Pré-condições | Sessão autenticada com permissão para editar Configurações → Avaliação. Registrar o valor inicial com a base de teste. |
| Gatilho | Selecionar Não em “Cobrar Avaliação do Cliente?” e clicar em Salvar Configurações. |
| Caso | [CT-RF142](Cenario_Teste/CT-RF142_Configuracoes_Avaliacao_Desativar_Cobranca.md) |
| Situação observada | Aprovado conforme a gravação. A consulta e a aba Avaliação confirmaram Não após recarregar. |
| Defeito | Nenhum no fluxo avaliado |
| Evidências | [Jam 1 — Desativação da cobrança da avaliação](https://jam.dev/c/851c15d8-4076-4493-ad3f-c2ba0316d0ca) e [Evidências](Evidencias/CT-RF151_Configuracoes_Avaliacao_Desativar_Cobranca/README.md). |

### Critérios de aceitação do RF142

1. O salvamento de Não retorna sucesso.
2. O GET após recarregar devolve `cobrar_avaliacao: nao`.
3. O seletor mantém Não após reabrir a aba.

### Pontos a confirmar e limites do RF142

A evidência cobre a preferência salva. A geração de cobranças e o reflexo no cadastro de avaliação ficam para nova execução.

<a id="rf143"></a>


## RF143 — Alterar o tipo de avaliação para Bioimpedância

| Campo | Descrição |
| --- | --- |
| Requisito de QA | Confirmar que o valor Bioimpedância de Tipo de avaliação permanece salvo após recarregar e reabrir Avaliação. |
| Ator | Usuário autenticado com permissão para a operação. |
| Pré-condições | Sessão autenticada com permissão para editar Configurações → Avaliação. Registrar o valor inicial com a base de teste. |
| Gatilho | Selecionar Bioimpedância em Tipo de avaliação e clicar em Salvar Configurações. |
| Caso | [CT-RF143](Cenario_Teste/CT-RF143_Configuracoes_Avaliacao_Tipo_Bioimpedancia.md) |
| Situação observada | Aprovado conforme a gravação. A consulta e a aba Avaliação confirmaram Bioimpedância após recarregar. O cartão de resumo Avaliação também exibiu Bioimpedância. |
| Defeito | Nenhum no fluxo avaliado |
| Evidências | [Jam 2 — Alteração do tipo para Bioimpedância](https://jam.dev/c/8685a48a-ed9a-4169-a825-90036265b185) e [Evidências](Evidencias/CT-RF152_Configuracoes_Avaliacao_Tipo_Bioimpedancia/README.md). |

### Critérios de aceitação do RF143

1. O salvamento de Bioimpedância retorna sucesso.
2. O GET após recarregar devolve `tipo_avaliacao: BIOIMPEDANCIA`.
3. Bioimpedância aparece no campo Tipo de avaliação e no cartão de resumo Avaliação.

### Pontos a confirmar e limites do RF143

O tipo foi conferido no formulário e no cartão de resumo de Configurações. A gravação não cobre a criação de uma avaliação nesse tipo.

<a id="rf144"></a>


## RF144 — Habilitar Teste Físico nas configurações de avaliação

| Campo | Descrição |
| --- | --- |
| Requisito de QA | Confirmar que o valor Sim de Teste Físico permanece salvo após recarregar e reabrir Avaliação. |
| Ator | Usuário autenticado com permissão para a operação. |
| Pré-condições | Sessão autenticada com permissão para editar Configurações → Avaliação. Registrar o valor inicial com a base de teste. |
| Gatilho | Selecionar Sim em Teste Físico e clicar em Salvar Configurações. |
| Caso | [CT-RF144](Cenario_Teste/CT-RF144_Configuracoes_Avaliacao_Habilitar_Teste_Fisico.md) |
| Situação observada | Aprovado conforme a gravação. A consulta e a aba Avaliação confirmaram Sim após recarregar. |
| Defeito | Nenhum no fluxo avaliado |
| Evidências | [Jam 3 — Habilitação de Teste Físico](https://jam.dev/c/86466f6e-b180-439f-ab1d-dde2484595a3) e [Evidências](Evidencias/CT-RF153_Configuracoes_Avaliacao_Habilitar_Teste_Fisico/README.md). |

### Critérios de aceitação do RF144

1. O salvamento de Sim retorna sucesso.
2. O GET após recarregar devolve `teste_fisico: SIM`.
3. O seletor mantém Sim após reabrir a aba.

### Pontos a confirmar e limites do RF144

A gravação cobre a alteração e a leitura da preferência. A disponibilidade do teste no cadastro de avaliação fica para verificação separada.

<a id="rf135"></a>


## RF145 — Cancelar a edição da senha de Biometria

| Campo | Descrição |
| --- | --- |
| Requisito de QA | Conferir que Cancelar descarta a edição de Senha sem alterar a configuração armazenada. |
| Ator | Usuário autenticado com permissão para a operação. |
| Pré-condições | Sessão autenticada com permissão de edição e credenciais fictícias no ambiente de teste. |
| Gatilho | Editar o campo Senha e acionar Cancelar. |
| Caso | [CT-RF145](Cenario_Teste/CT-RF145_Configuracoes_Biometria_Cancelar_Edicao_Senha.md) |
| Situação observada | Aprovado conforme a gravação. A edição foi descartada e a tela retornou à Página Inicial sem POST de configuração. |
| Defeito | Nenhum no fluxo avaliado |
| Evidências | [Jam 6 — Cancelamento da edição no formulário de Biometria](https://jam.dev/c/ccac55df-d2c8-4b11-898b-d12d87aced72) e [Evidências](Evidencias/CT-RF162_Configuracoes_Biometria_Cancelar_Edicao_Senha/README.md). |

### Critérios de aceitação do RF145

1. Cancelar navega à Página Inicial.
2. O POST de salvamento não ocorre.
3. A configuração anterior é exibida ao voltar.

### Pontos a confirmar e limites do RF145

A aprovação cobre o cancelamento. O comportamento de mascaramento de Senha está documentado no BUG-046.

<a id="rf146"></a>


## RF146 — Rejeitar um valor sem formato de IP em Biometria

| Campo | Descrição |
| --- | --- |
| Requisito de QA | Impedir que uma sequência numérica sem formato de endereço IP substitua o valor configurado para o aparelho. |
| Ator | Usuário autenticado com permissão para a operação. |
| Pré-condições | Sessão autenticada em Biometria com permissão para alterar os dados de um aparelho de teste. |
| Gatilho | Digitar uma sequência numérica sem formato de IP e salvar. |
| Caso | [CT-RF146](Cenario_Teste/CT-RF146_Configuracoes_Biometria_Rejeitar_IP_Invalido.md) |
| Situação observada | Reprovado nas evidências. Um valor sem formato de IP foi salvo e apareceu na consulta e no campo após recarregar. |
| Defeito | [BUG-053](Relatorio-de-Bugs.md#bug-053), em triagem |
| Evidências | [Jam 7 — Validação de IP do aparelho](https://jam.dev/c/5b8eea1f-3c87-4497-8fb1-da49f09f9854) e [Evidências](Evidencias/CT-RF163_Configuracoes_Biometria_Rejeitar_IP_Invalido/README.md). |

### Critérios de aceitação do RF146

1. A entrada sem formato de IP é rejeitada.
2. A interface identifica o campo que precisa de correção.
3. A consulta após a tentativa mantém o valor anterior.

### Pontos a confirmar e limites do RF146

A leitura posterior comprova o valor armazenado. A gravação não verifica a tentativa de conexão ao aparelho.

<a id="rf147"></a>


## RF147 — Persistir a alteração da porta do aparelho de Biometria

| Campo | Descrição |
| --- | --- |
| Requisito de QA | Confirmar que a alteração de Porta é gravada e reaparece ao consultar novamente a configuração de Biometria. |
| Ator | Usuário autenticado com permissão para a operação. |
| Pré-condições | Sessão autenticada com permissão para alterar a porta de um aparelho de teste. |
| Gatilho | Editar Porta e clicar em Salvar Configurações. |
| Caso | [CT-RF147](Cenario_Teste/CT-RF147_Configuracoes_Biometria_Persistir_Porta.md) |
| Situação observada | Aprovado conforme a gravação. A porta alterada no POST foi confirmada no GET após recarga. A restauração retornou sucesso. |
| Defeito | Nenhum no fluxo avaliado |
| Evidências | [Jam 8 — Persistência da porta do aparelho](https://jam.dev/c/7d7bf60a-d8a8-4b7e-80da-1e73b45819cb) e [Evidências](Evidencias/CT-RF164_Configuracoes_Biometria_Persistir_Porta/README.md). |

### Critérios de aceitação do RF147

1. A alteração retorna sucesso.
2. A leitura após recarregar equivale ao valor enviado.
3. A interface mostra o valor consultado.

### Pontos a confirmar e limites do RF147

A gravação cobre a persistência da primeira alteração. A conectividade e a nova leitura após a restauração ficaram fora do trecho.

<a id="rf148"></a>


## RF148 — Validar dias negativos para travar a catraca

| Campo | Descrição |
| --- | --- |
| Requisito de QA | Recusar um número negativo em Travar Catraca Após (dias) ou explicar a correção aplicada antes de confirmar o salvamento. |
| Ator | Usuário autenticado com permissão para a operação. |
| Pré-condições | Sessão autenticada em Biometria com permissão para editar dias de bloqueio no ambiente de teste. |
| Gatilho | Preencher Travar Catraca Após (dias) com -1 e salvar. |
| Caso | [CT-RF148](Cenario_Teste/CT-RF148_Configuracoes_Biometria_Validar_Dias_Bloqueio.md) |
| Situação observada | Reprovado nas evidências. A API confirmou o salvamento de -1. A leitura posterior trouxe 0 e a gravação não mostrou explicação para a diferença. |
| Defeito | [BUG-054](Relatorio-de-Bugs.md#bug-054), em triagem |
| Evidências | [Jam 9 — Validação de dias de bloqueio da catraca](https://jam.dev/c/f607bc49-184f-4d55-81ab-7db825af6021) e [Evidências](Evidencias/CT-RF165_Configuracoes_Biometria_Validar_Dias_Bloqueio/README.md). |

### Critérios de aceitação do RF148

1. O formulário orienta a correção da entrada negativa.
2. O retorno distingue um valor recusado ou ajustado de um valor aceito conforme informado.
3. A leitura posterior mantém um valor válido.

### Pontos a confirmar e limites do RF148

A consulta devolveu 0. A gravação não determina se esse valor resultou de normalização ou se o sistema preservou o valor anterior.

---


## RF149 — Bloquear cadastro de modelo de ficha sem nome

| Campo | Descrição |
| --- | --- |
| Requisito de QA | Impedir a criação de um modelo quando o campo Nome do Modelo estiver vazio e informar como corrigir o preenchimento. |
| Ator | Usuário autenticado com acesso a Modelos de Ficha. |
| Pré-condições | Sessão autenticada com permissão de cadastro e pelo menos um personal disponível. |
| Gatilho | Acionar Criar Modelo com um personal selecionado e o nome em branco. |
| Caso | [CT-RF149](Cenario_Teste/CT-RF149_Modelo_Ficha_Sem_Nome.md) |
| Situação observada | Aprovado conforme a gravação. Aviso “Informe o nome do modelo.”. Modal permaneceu aberto após Entendi, sem requisição capturada. |
| Defeito | Nenhum no fluxo avaliado |
| Evidências | [Jam — PED-25](https://jam.dev/c/fb5673c9-3cd1-46c4-88f4-d5fb32574a8e) e [Evidências](Evidencias/CT-RF109_Modelo_Ficha_Sem_Nome/README.md). |

### Critérios de aceitação do RF149

1. O aviso identifica que o Nome do Modelo precisa ser preenchido.
2. Nenhum modelo é criado com nome vazio.
3. Após fechar o aviso, o formulário está disponível para corrigir o preenchimento.

### Pontos a confirmar e limites do RF149

A gravação cobre o nome vazio com um personal selecionado. Entrada composta apenas por espaços, envio com todos os campos vazios e validação no servidor exigem verificação própria.

<a id="rf150"></a>


## RF150 — Cancelar cadastro de modelo de ficha preenchido

| Campo | Descrição |
| --- | --- |
| Requisito de QA | Encerrar o formulário de cadastro sem salvar os dados preenchidos. |
| Ator | Usuário autenticado com acesso a Modelos de Ficha. |
| Pré-condições | Sessão autenticada com acesso ao cadastro e um personal disponível para seleção. |
| Gatilho | Acionar Cancelar em Novo Modelo de Ficha com os campos preenchidos. |
| Caso | [CT-RF150](Cenario_Teste/CT-RF150_Cancelar_Cadastro_Modelo_Ficha.md) |
| Situação observada | Aprovado conforme a gravação. Cancelar fechou o modal preenchido e manteve 0 registros, sem requisição capturada. |
| Defeito | Nenhum no fluxo avaliado |
| Evidências | [Jam — PED-26](https://jam.dev/c/a2a39e11-04f4-40aa-a97e-75a57a5f1b0f) e [Evidências](Evidencias/CT-RF110_Cancelar_Cadastro_Modelo_Ficha/README.md). |

### Critérios de aceitação do RF150

1. O botão Cancelar fecha o formulário preenchido.
2. O modelo informado não é incluído na listagem e a contagem permanece igual à inicial.
3. Uma nova abertura do formulário exibe os valores iniciais.

### Pontos a confirmar e limites do RF150

O formulário não foi reaberto depois do cancelamento. A listagem inicial e a final mostram 0 registros.

<a id="rf151"></a>


## RF151 — Buscar modelo de ficha por código inexistente

| Campo | Descrição |
| --- | --- |
| Requisito de QA | Exibir zero resultados e uma mensagem clara ao buscar por um código ausente em uma base com modelos cadastrados. |
| Ator | Usuário autenticado com acesso a Modelos de Ficha. |
| Pré-condições | Sessão autenticada e base de controle com pelo menos um modelo de código conhecido e um código comprovadamente ausente. |
| Gatilho | Preencher somente Código com um valor ausente e clicar no botão de busca. |
| Caso | [CT-RF151](Cenario_Teste/CT-RF151_Busca_Modelo_Ficha_Codigo_Inexistente.md) |
| Situação observada | A validar — regra ou contexto pendente. Busca por 989898 exibiu estado vazio. GET retornou HTTP 200 com `[]`. |
| Defeito | Sem defeito confirmado |
| Evidências | [Jam — PED-27](https://jam.dev/c/c1aecaa8-39c7-49b0-89af-9de47a68ba40) e [Evidências](Evidencias/CT-RF111_Busca_Modelo_Ficha_Codigo_Inexistente/README.md). |

### Critérios de aceitação do RF151

1. A busca pelo código ausente mostra a mensagem de estado vazio e 0 registros.
2. Registros com outro código ficam fora do resultado.
3. A busca de controle com código existente identifica o modelo correspondente.

### Pontos a confirmar e limites do RF151

O estado vazio foi observado. A base de controle e a busca positiva não aparecem na gravação, por isso a eficácia do filtro por código permanece a validar.

<a id="rf152"></a>


## RF152 — Buscar modelo de ficha por título inexistente

| Campo | Descrição |
| --- | --- |
| Requisito de QA | Exibir zero resultados quando nenhum modelo satisfaz o filtro por título em uma base com registros. |
| Ator | Usuário autenticado com acesso a Modelos de Ficha. |
| Pré-condições | Sessão autenticada e base de controle com títulos conhecidos, incluindo um termo sem correspondência. |
| Gatilho | Preencher somente Título com um valor ausente e clicar no botão de busca. |
| Caso | [CT-RF152](Cenario_Teste/CT-RF152_Busca_Modelo_Ficha_Titulo_Inexistente.md) |
| Situação observada | A validar — regra ou contexto pendente. Título PEDRO-01 exibiu carregamento e estado vazio. GET retornou HTTP 200 com `[]`. |
| Defeito | Sem defeito confirmado |
| Evidências | [Jam — PED-28](https://jam.dev/c/0c385452-2aeb-427f-8159-79549fe7371d) e [Evidências](Evidencias/CT-RF112_Busca_Modelo_Ficha_Titulo_Inexistente/README.md). |

### Critérios de aceitação do RF152

1. A busca sem correspondência apresenta a mensagem de estado vazio e 0 registros.
2. A indicação de carregamento termina após a resposta.
3. A busca de controle encontra um título existente segundo a regra de correspondência acordada.

### Pontos a confirmar e limites do RF152

A gravação começa com a listagem vazia. O comportamento com títulos registrados e o tipo de correspondência (exata ou parcial) precisam de confirmação.

<a id="rf153"></a>


## RF153 — Buscar modelos de ficha com filtros combinados

| Campo | Descrição |
| --- | --- |
| Requisito de QA | Verificar a aplicação conjunta dos filtros Código, Título e Criador em uma busca com resultados de controle. |
| Ator | Usuário autenticado com acesso a Modelos de Ficha. |
| Pré-condições | Sessão autenticada e modelos de controle que satisfaçam todos os critérios ou apenas parte deles. |
| Gatilho | Preencher os três filtros e efetuar a busca. |
| Caso | [CT-RF153](Cenario_Teste/CT-RF153_Busca_Modelo_Ficha_Filtros_Combinados.md) |
| Situação observada | A validar — regra ou contexto pendente. Três filtros preenchidos, 0 registros. GET sem parâmetros na URL retornou HTTP 200 com `[]`. |
| Defeito | Sem defeito confirmado |
| Evidências | [Jam — PED-29](https://jam.dev/c/006f9722-e643-4b65-904a-25471a7b90ed) e [Evidências](Evidencias/CT-RF113_Busca_Modelo_Ficha_Filtros_Combinados/README.md). |

### Critérios de aceitação do RF153

1. A busca com os três filtros é acionada e mantém os critérios informados.
2. Com a regra de interseção confirmada, somente o modelo compatível com os três critérios é listado.
3. Alterar um critério para uma combinação impossível exibe 0 registros e a mensagem de estado vazio.

### Pontos a confirmar e limites do RF153

A resposta vazia e a ausência de parâmetros na URL não permitem distinguir filtragem local de critérios ignorados. Confirmar a lógica de combinação com o produto e usar dados que diferenciem os resultados.

<a id="rf154"></a>


## RF154 — Limpar os filtros de Modelos de Ficha

| Campo | Descrição |
| --- | --- |
| Requisito de QA | Remover os valores digitados em Código, Título e Criador para preparar uma nova consulta. |
| Ator | Usuário autenticado com acesso a Modelos de Ficha. |
| Pré-condições | Sessão autenticada e tela Modelos de Ficha aberta com os três filtros preenchidos. |
| Gatilho | Apagar manualmente os valores de Criador, Título e Código. |
| Caso | [CT-RF154](Cenario_Teste/CT-RF154_Limpeza_Filtros_Modelos_Ficha.md) |
| Situação observada | Aprovado conforme a gravação. Criador, Título e Código foram limpos manualmente e Buscar permaneceu disponível. |
| Defeito | Nenhum no fluxo avaliado |
| Evidências | [Jam — PED-30](https://jam.dev/c/297eec2b-7be4-498b-a0e6-e962ed93cc00) e [Evidências](Evidencias/CT-RF114_Limpeza_Filtros_Modelos_Ficha/README.md). |

### Critérios de aceitação do RF154

1. Criador, Título e Código podem ser esvaziados manualmente.
2. Os três campos exibem novamente suas indicações de preenchimento.
3. O botão de busca permanece disponível após a limpeza.

### Pontos a confirmar e limites do RF154

Este cenário cobre a limpeza dos campos. A recuperação dos resultados em uma base populada faz parte do cenário de nova busca.

<a id="rf155"></a>


## RF155 — Pesquisar novamente modelos de ficha sem filtros

| Campo | Descrição |
| --- | --- |
| Requisito de QA | Recuperar a listagem padrão após uma pesquisa restritiva e a remoção de todos os filtros. |
| Ator | Usuário autenticado com acesso a Modelos de Ficha. |
| Pré-condições | Sessão autenticada, listagem padrão com registros de referência e busca anterior que restrinja o resultado. |
| Gatilho | Clicar em Buscar após limpar os valores de Código, Título e Criador. |
| Caso | [CT-RF155](Cenario_Teste/CT-RF155_Nova_Busca_Modelos_Ficha_Sem_Filtros.md) |
| Situação observada | A validar — regra ou contexto pendente. Dois cliques em Buscar com campos vazios geraram HTTP 200 com `[]`. A lista permaneceu vazia. |
| Defeito | Sem defeito confirmado |
| Evidências | [Jam — PED-30](https://jam.dev/c/297eec2b-7be4-498b-a0e6-e962ed93cc00) e [Evidências](Evidencias/CT-RF115_Nova_Busca_Modelos_Ficha_Sem_Filtros/README.md). |

### Critérios de aceitação do RF155

1. Buscar com os três campos vazios atualiza a listagem e conclui o carregamento.
2. Em base populada, os registros disponíveis antes da busca restritiva reaparecem na consulta sem filtros.
3. A contagem e os campos refletem a consulta sem filtros.

### Pontos a confirmar e limites do RF155

A gravação não mostra uma listagem padrão populada. O estado vazio é compatível com os retornos, mas a recuperação de registros ocultados por uma pesquisa anterior ficou a validar.

<a id="rf118"></a>


## RF156 — Cadastrar um modelo de ficha com nome e personal

| Campo | Descrição |
| --- | --- |
| Requisito de QA | Cadastrar um novo modelo de ficha com nome e personal e disponibilizá-lo na listagem. |
| Ator | Usuário autenticado com permissão para a operação. |
| Pré-condições | Sessão autenticada com acesso a Modelos de Ficha, permissão para cadastrar e um personal disponível no formulário. |
| Gatilho | Preencher Nome do Modelo e Personal e acionar Criar Modelo. |
| Caso | [CT-RF156](Cenario_Teste/CT-RF156_Cadastro_Modelo_Ficha_Erro_500.md) |
| Situação observada | Reprovado nas evidências. Cadastro preenchido retornou HTTP 500. A interface exibiu “Erro ao salvar modelo.” |
| Defeito | [BUG-045](Relatorio-de-Bugs.md#bug-045), em triagem |
| Evidências | [Jam — PED-24 — Cadastro de modelo de ficha](https://jam.dev/c/04e2cae2-f3f2-43ff-8361-b3b9d9f50d35) e [Evidências](Evidencias/CT-RF121_Cadastro_Modelo_Ficha_Erro_500/README.md). |

### Critérios de aceitação do RF156

1. O formulário envia o nome e o personal escolhidos.
2. A operação termina com sucesso e a interface confirma o cadastro.
3. Após recarga, a listagem encontra o modelo com o personal selecionado.

### Pontos a confirmar e limites do RF156

Uma tentativa foi registrada. A gravação não confirma causa técnica, persistência parcial ou abrangência para outros nomes e personais. Os CT-RF149 e CT-RF150 cobrem, respectivamente, a validação de nome vazio e o cancelamento.

<a id="rf116"></a>


## RF157 — Consultar os detalhes de uma notificação

| Campo | Descrição |
| --- | --- |
| Requisito de QA | Abrir a notificação selecionada e conferir a mensagem, o público indicado e a prévia. |
| Ator | Usuário autenticado com permissão para a operação. |
| Pré-condições | Sessão autenticada com acesso a Aplicativo e ao menos uma notificação de teste na lista. |
| Gatilho | Clicar na lupa da notificação selecionada. |
| Caso | [CT-RF157](Cenario_Teste/CT-RF157_Aplicativo_Consultar_Notificacao.md) |
| Situação observada | Aprovado conforme a gravação. O diálogo exibiu a notificação selecionada e sua prévia. Fechar retornou à listagem. |
| Defeito | Nenhum no fluxo avaliado |
| Evidências | [Jam 1 — Consulta de notificação existente](https://jam.dev/c/32edc5de-4ad3-48ca-9e19-1db449bebcc5) e [Evidências](Evidencias/CT-RF157_Aplicativo_Consultar_Notificacao/README.md). |

### Critérios de aceitação do RF157

1. A ação consulta o registro da linha selecionada.
2. O diálogo exibe a mensagem e a prévia correspondentes.
3. Fechar encerra apenas a consulta.

### Pontos a confirmar e limites do RF157

O caso verifica a consulta no painel. A gravação não demonstra recebimento no celular.

<a id="rf158"></a>


## RF158 — Impedir o envio de uma notificação sem mensagem

| Campo | Descrição |
| --- | --- |
| Requisito de QA | Manter Enviar aviso desabilitado enquanto a mensagem estiver vazia. |
| Ator | Usuário autenticado com permissão para a operação. |
| Pré-condições | Sessão autenticada com acesso a Aplicativo e permissão para abrir a criação. |
| Gatilho | Abrir Criar Notificação e tentar acionar Enviar aviso com a mensagem vazia. |
| Caso | [CT-RF158](Cenario_Teste/CT-RF158_Aplicativo_Bloquear_Notificacao_Vazia.md) |
| Situação observada | Aprovado conforme a gravação. Sem texto, Enviar aviso ficou desabilitado e a captura não registrou uma criação. |
| Defeito | Nenhum no fluxo avaliado |
| Evidências | [Jam 2 — Validação de mensagem obrigatória](https://jam.dev/c/b9ebb9d0-e7c2-4ed8-a50d-00c2948e97fd) e [Evidências](Evidencias/CT-RF158_Aplicativo_Bloquear_Notificacao_Vazia/README.md). |

### Critérios de aceitação do RF158

1. O contador permanece em zero com o campo vazio.
2. O botão fica desabilitado e o endpoint de criação não é chamado.
3. Cancelar fecha o diálogo.

### Pontos a confirmar e limites do RF158

A evidência cobre o campo totalmente vazio. Espaços em branco e limites de comprimento ficam para nova execução.

<a id="rf159"></a>


## RF159 — Criar uma notificação e conferir a prévia e a listagem

| Campo | Descrição |
| --- | --- |
| Requisito de QA | Comparar a mensagem digitada com a prévia e verificar que a criação retorna sucesso e inclui o aviso na lista. |
| Ator | Usuário autenticado com permissão para a operação. |
| Pré-condições | Sessão autorizada em um ambiente de teste com contatos de teste e acesso a Criar Notificação. |
| Gatilho | Preencher a mensagem, conferir a prévia e clicar em Enviar aviso. |
| Caso | [CT-RF159](Cenario_Teste/CT-RF159_Aplicativo_Criar_Notificacao_Preview.md) |
| Situação observada | Aprovado conforme a gravação. A prévia refletiu o texto e a criação retornou HTTP 201. A nova notificação apareceu na lista. |
| Defeito | Nenhum no fluxo avaliado |
| Evidências | [Jam 3 — Criação de notificação com prévia](https://jam.dev/c/6720f25a-45e9-4e8d-9c5f-c48b0bfec5c0) e [Evidências](Evidencias/CT-RF159_Aplicativo_Criar_Notificacao_Preview/README.md). |

### Critérios de aceitação do RF159

1. A prévia exibe o texto digitado.
2. A criação retorna sucesso.
3. A consulta após a criação inclui o novo aviso.

### Pontos a confirmar e limites do RF159

O resultado cobre a criação, a prévia e a listagem. A entrega efetiva no aplicativo dos alunos não foi verificada.

<a id="rf160"></a>


## RF160 — Alternar o filtro de postagens e abrir a lista completa

| Campo | Descrição |
| --- | --- |
| Requisito de QA | Verificar que a lista e o diálogo Todas as postagens mostram o estado vazio correspondente ao filtro selecionado. |
| Ator | Usuário autenticado com permissão para a operação. |
| Pré-condições | Sessão autenticada em Aplicativo com a seção Postagens disponível e lista sem registros. |
| Gatilho | Alternar Só pendentes e Ver todas e abrir Ver todas as postagens em cada estado. |
| Caso | [CT-RF160](Cenario_Teste/CT-RF160_Aplicativo_Postagens_Filtros_Estados_Vazios.md) |
| Situação observada | Aprovado conforme a gravação. O painel e o diálogo alternaram corretamente os avisos para todas e pendentes na base vazia. |
| Defeito | Nenhum no fluxo avaliado |
| Evidências | [Jam 4 — Filtros e lista completa de postagens](https://jam.dev/c/a58327e6-6a5a-4a2e-8b3d-cee9296d1d03) e [Evidências](Evidencias/CT-RF160_Aplicativo_Postagens_Filtros_Estados_Vazios/README.md). |

### Critérios de aceitação do RF160

1. Os dois modos exibem textos de lista vazia coerentes com o filtro.
2. Todas as postagens abre e mostra o mesmo modo aplicado no painel.
3. O diálogo fecha e retorna ao painel.

### Pontos a confirmar e limites do RF160

A aprovação se limita à base vazia e à troca dos avisos. A filtragem de registros com estados diferentes exige massa de teste.

<a id="rf161"></a>


## RF161 — Alternar o filtro de denúncias com a lista vazia

| Campo | Descrição |
| --- | --- |
| Requisito de QA | Conferir a troca entre todos os registros e apenas pendentes na seção Denúncias com a lista vazia. |
| Ator | Usuário autenticado com permissão para a operação. |
| Pré-condições | Sessão autenticada em Aplicativo com a seção Denúncias disponível. |
| Gatilho | Alternar Ver todas e Só pendentes na seção Denúncias. |
| Caso | [CT-RF161](Cenario_Teste/CT-RF161_Aplicativo_Denuncias_Filtros_Estados_Vazios.md) |
| Situação observada | Aprovado conforme a gravação. A lista vazia apresentou a mensagem correspondente em todas as alternâncias entre todas e pendentes. |
| Defeito | Nenhum no fluxo avaliado |
| Evidências | [Jam 5 — Filtros de denúncias sem registros](https://jam.dev/c/709cd210-f823-4348-805f-3cb61e7fb23f) e [Evidências](Evidencias/CT-RF161_Aplicativo_Denuncias_Filtros_Estados_Vazios/README.md). |

### Critérios de aceitação do RF161

1. O modo todas indica ausência de denúncias registradas.
2. O modo pendentes indica ausência de denúncias pendentes.
3. A alternância pode ser repetida durante a mesma sessão.

### Pontos a confirmar e limites do RF161

A evidência cobre a interface sem denúncias. A filtragem com registros pendentes e tratados ficou fora da gravação.

<a id="rf145"></a>


## 🔗 Rastreabilidade

| Requisito | Cenário / caso | Defeito | Resultado | Evidências |
| --- | --- | --- | --- | --- |
| RF01 | [CT-RF01_loginComSucesso](Cenario_Teste/CT-RF01_loginComSucesso.md) | Nenhum identificado no fluxo avaliado | Aprovado conforme a gravação | [Resumo das evidências](Evidencias/CT-RF04_loginComSucesso/README.md) e [Jam](https://jam.dev/c/5e4a28be-4e80-43d3-9587-1b113723cc38) |
| RF02 | [CT-RF02](Cenario_Teste/CT-RF02_Login_SenhaIncorreta.md) | Nenhum no fluxo avaliado | Aprovado conforme a gravação | [Evidências](Evidencias/CT-RF05_Login_SenhaIncorreta/README.md) e [Jam](https://jam.dev/c/75f16436-7201-4de0-b191-1c4d0d63bfe8) |
| RF03 | [CT-RF03](Cenario_Teste/CT-RF03_Login_UsuarioInexistente.md) | Nenhum no fluxo avaliado | Aprovado conforme a gravação | [Evidências](Evidencias/CT-RF06_Login_UsuarioInexistente/README.md) e [Jam](https://jam.dev/c/b184e875-2cb1-4a01-b4dd-bc85b3741ff6) |
| RF04 | [CT-RF04](Cenario_Teste/CT-RF04_Esqueci-senha.md) | [BUG-001](Relatorio-de-Bugs.md#bug-001--link-esqueci-minha-senha-não-executa-nenhuma-ação) | Reprovado nas evidências; reteste pendente | [Drive](https://drive.google.com/file/d/1f6AqYunchDH4R9Yw1JpbyX9x28UQGcbo/view?usp=sharing) e [Jam](https://jam.dev/c/0273b203-b999-493d-9919-2d143bc13301) |
| RF05 | [CT-RF05_ERRO](Cenario_Teste/CT-RF05_ERRO.md) | [BUG-002](Relatorio-de-Bugs.md#bug-002--perfil-com-dados-fictícios-campos-ausentes-e-layout-desconfigurado) | Reprovado nas evidências; reteste pendente | [Captura](Evidencias/CT-RF02_ERRO/erro-na-tela.png), [HTML](Evidencias/CT-RF02_ERRO/recorte-dom.html) e [Jam](https://jam.dev/c/c61241d5-bff5-4a0a-9684-991318f9b51c) |
| RF06 | [CT-RF06](Cenario_Teste/CT-RF06_Periodo_Dashboard.md) | [BUG-006](Relatorio-de-Bugs.md#bug-006) | Reprovado nas evidências | [Evidências](Evidencias/CT-RF12_Periodo_Dashboard/README.md) e [Jam](https://jam.dev/c/93165ba3-3bfe-4dd5-9379-ab8db2d686ba) |
| RF07 | [CT-RF07](Cenario_Teste/CT-RF07_Codigos_Personais.md) | Sem defeito confirmado | A validar — regra ou contexto pendente | [Evidências](Evidencias/CT-RF13_Codigos_Personais/README.md) e [Jam](https://jam.dev/c/69330ca9-ef19-4ece-918f-31a460628016) |
| RF08 | [CT-RF08](Cenario_Teste/CT-RF08_Erro_Servidor_Excesso_Requisicoes.md) | [BUG-018](Relatorio-de-Bugs.md#bug-018), em triagem | Reprovado — múltiplas requisições retornam HTTP 500. | [Jam](https://jam.dev/c/eea58e17-b62f-432b-97b2-b14c14bed555) e [Evidências](Evidencias/CT-RF34_Erro_Servidor_Excesso_Requisicoes/README.md) |
| RF09 | [CT-RF09](Cenario_Teste/CT-RF09_FILTRO_TelaClientes.md) | [BUG-003](Relatorio-de-Bugs.md#bug-003--filtros-combinados-da-página-clientes-não-restringem-a-listagem) | Reprovado conforme o relato; reteste pendente | [Índice e limites](Evidencias/CT-RF03_Filtros_Clientes/README.md), [captura 1](Evidencias/CT-RF03_Filtros_Clientes/filtros-clientes-01.png), [captura 2](Evidencias/CT-RF03_Filtros_Clientes/filtros-clientes-02.png) e [Jam](https://jam.dev/c/657627ec-e7e2-455d-a505-9b2a26f44bf1) |
| RF10 | [CT-RF10](Cenario_Teste/CT-RF10_Cadastro_Avaliacao.md) | [BUG-010](Relatorio-de-Bugs.md#bug-010) | Reprovado nas evidências | [Evidências](Evidencias/CT-RF21_Cadastro_Avaliacao/README.md) e [Jam](https://jam.dev/c/2e5eca1f-7cd2-4ee3-854b-02ef4635955a) |
| RF11 | [CT-RF11](Cenario_Teste/CT-RF11_Exportacao_Financeiro.md) | [BUG-004](Relatorio-de-Bugs.md#bug-004) | Reprovado nas evidências | [Evidências](Evidencias/CT-RF07_Exportacao_Financeiro/README.md) e [Jam](https://jam.dev/c/1084cb18-cb3d-4b85-9c2f-ee431b59a06b) |
| RF12 | [CT-RF12](Cenario_Teste/CT-RF12_Contagem_Mensalidades.md) | [BUG-005](Relatorio-de-Bugs.md#bug-005) | Reprovado nas evidências | [Evidências](Evidencias/CT-RF09_Contagem_Mensalidades/README.md) e [Jam](https://jam.dev/c/1874d0b3-5c7c-4f28-85be-91750e20cbe1) |
| RF13 | [CT-RF13](Cenario_Teste/CT-RF13_Filtro_Mensalidades.md) | [BUG-005](Relatorio-de-Bugs.md#bug-005) | Reprovado nas evidências | [Evidências](Evidencias/CT-RF10_Filtro_Mensalidades/README.md) e [Jam](https://jam.dev/c/3f78cf16-2c3b-48bc-8622-23b829debbec) |
| RF14 | [CT-RF14](Cenario_Teste/CT-RF14_Calculo_Cobranca.md) | Sem defeito confirmado | A validar — regra ou contexto pendente | [Evidências](Evidencias/CT-RF08_Calculo_Cobranca/README.md) e [Jam](https://jam.dev/c/79b712ae-d9e0-4600-862f-fd3a278285ff) |
| RF15 | [CT-RF15](Cenario_Teste/CT-RF15_Metricas_Financeiro.md) | Sem defeito confirmado | A validar — regra ou contexto pendente | [Evidências](Evidencias/CT-RF11_Metricas_Financeiro/README.md) e [Jam](https://jam.dev/c/4491c9e7-7e00-4063-91ce-8683e316df06) |
| RF16 | [CT-RF16](Cenario_Teste/CT-RF16_Filtros_Contas_Pagar.md) | Sem defeito confirmado | A validar — regra ou contexto pendente | [Evidências](Evidencias/CT-RF91_Filtros_Contas_Pagar/README.md) e [Jam](https://jam.dev/c/5d0afaf4-5abd-4e85-923f-27448304a9ef) |
| RF17 | [CT-RF17](Cenario_Teste/CT-RF17_Cadastro_Conta_Colaborador_Sem_Colaborador.md) | [BUG-039](Relatorio-de-Bugs.md#bug-039), em triagem | Reprovado nas evidências; reteste pendente. | [Evidências](Evidencias/CT-RF92_Cadastro_Conta_Colaborador_Sem_Colaborador/README.md) e [Jam](https://jam.dev/c/5d0afaf4-5abd-4e85-923f-27448304a9ef) |
| RF18 | [CT-RF18](Cenario_Teste/CT-RF18_Busca_Colaborador_Conta_Pagar.md) | Sem defeito confirmado | A validar — regra ou contexto pendente | [Evidências](Evidencias/CT-RF93_Busca_Colaborador_Conta_Pagar/README.md) e [Jam](https://jam.dev/c/5d0afaf4-5abd-4e85-923f-27448304a9ef) |
| RF19 | [CT-RF19](Cenario_Teste/CT-RF19_Visualizacao_Conta_Pagar.md) | Nenhum no fluxo avaliado | Aprovado conforme a gravação | [Evidências](Evidencias/CT-RF94_Visualizacao_Conta_Pagar/README.md) e [Jam](https://jam.dev/c/5d0afaf4-5abd-4e85-923f-27448304a9ef) |
| RF20 | [CT-RF20](Cenario_Teste/CT-RF20_Exclusao_Conta_Pagar.md) | Nenhum no fluxo avaliado | Aprovado conforme a gravação | [Evidências](Evidencias/CT-RF95_Exclusao_Conta_Pagar/README.md) e [Jam](https://jam.dev/c/5d0afaf4-5abd-4e85-923f-27448304a9ef) |
| RF21 | [CT-RF21](Cenario_Teste/CT-RF21_Digitacao_Codigo_Exercicio.md) | [BUG-011](Relatorio-de-Bugs.md#bug-011), em triagem | Reprovado conforme o relato; reprodução independente pendente. | [Jam](https://jam.dev/c/2696db03-0a18-4c39-a75d-4987a43c04f0) e relato do testador |
| RF22 | [CT-RF22](Cenario_Teste/CT-RF22_Exclusao_Exercicio.md) | Sem defeito confirmado | Aprovado no trecho consultado. | [Jam](https://jam.dev/c/32adfca3-489f-4a4b-a08d-933c1d1a3c32) e [Evidências](Evidencias/CT-RF23_Exclusao_Exercicio/README.md) |
| RF23 | [CT-RF23](Cenario_Teste/CT-RF23_Edicao_Exercicio.md) | [BUG-012](Relatorio-de-Bugs.md#bug-012), em triagem | Reprovado no trecho consultado; confirmar operação e identidade dos registros na reprodução. | [Jam](https://jam.dev/c/073f70d6-4052-4e0f-a4bb-e9f37305d618) e [Evidências](Evidencias/CT-RF24_Edicao_Exercicio/README.md) |
| RF24 | [CT-RF24](Cenario_Teste/CT-RF24_Envio_Exercicio_Imagem.md) | Sem defeito confirmado | A validar — criação visível; persistência e associação da imagem não confirmadas. | [Jam](https://jam.dev/c/25c37a9b-e9bd-4e0c-adf1-4da528ae1d58) e [Evidências](Evidencias/CT-RF25_Envio_Exercicio_Imagem/README.md) |
| RF25 | [CT-RF25](Cenario_Teste/CT-RF25_Exercicio_Campos_Vazios.md) | [BUG-013](Relatorio-de-Bugs.md#bug-013), em triagem | Reprovado — sem feedback de validação visível. | [Jam](https://jam.dev/c/bc07ca5f-d3a9-45f6-84cb-12c0b562a211) |
| RF26 | [CT-RF26](Cenario_Teste/CT-RF26_Video_Campo_Imagem.md) | [BUG-014](Relatorio-de-Bugs.md#bug-014), em triagem | Reprovado — arquivo rejeitado sem feedback visível. | [Jam](https://jam.dev/c/00740108-9a7d-4151-8723-171c89635567) |
| RF27 | [CT-RF27](Cenario_Teste/CT-RF27_Imagem_Campo_Video.md) | [BUG-015](Relatorio-de-Bugs.md#bug-015), em triagem | Reprovado — arquivo rejeitado sem feedback visível. | [Jam](https://jam.dev/c/be9437a4-4fe9-4756-a2af-6777d3f43e25) |
| RF28 | [CT-RF28](Cenario_Teste/CT-RF28_Exclusao_GrupoMuscular.md) | [BUG-016](Relatorio-de-Bugs.md#bug-016), em triagem | Reprovado nas evidências; reteste pendente. | [Jam](https://jam.dev/c/98008390-0040-475e-ba7b-7f1e72cc0b2e) |
| RF29 | [CT-RF29](Cenario_Teste/CT-RF29_Imagens_GruposMusculares.md) | [BUG-017](Relatorio-de-Bugs.md#bug-017), em triagem | Reprovado nas evidências; reteste pendente. | [Jam](https://jam.dev/c/98008390-0040-475e-ba7b-7f1e72cc0b2e) |
| RF30 | [CT-RF30](Cenario_Teste/CT-RF30_Cadastro_GrupoMuscular.md) | Nenhum no fluxo avaliado | Aprovado conforme a gravação | [Jam](https://jam.dev/c/98008390-0040-475e-ba7b-7f1e72cc0b2e) |
| RF31 | [CT-RF31](Cenario_Teste/CT-RF31_Edicao_TipoMembro.md) | Nenhum no fluxo avaliado | Aprovado conforme a gravação | [Jam](https://jam.dev/c/98008390-0040-475e-ba7b-7f1e72cc0b2e) |
| RF32 | [CT-RF32](Cenario_Teste/CT-RF32_Filtros_GruposMusculares.md) | Nenhum no fluxo avaliado | Aprovado conforme a gravação | [Jam](https://jam.dev/c/98008390-0040-475e-ba7b-7f1e72cc0b2e) |
| RF33 | [CT-RF33](Cenario_Teste/CT-RF33_Cadastro_Objetivo_Treino.md) | [BUG-019](Relatorio-de-Bugs.md#bug-019), em triagem | Reprovado nas evidências; reteste pendente. | [Evidências](Evidencias/CT-RF35_Cadastro_Objetivo_Treino/README.md) e [Jam](https://jam.dev/c/1d474477-2411-4a81-b85c-74207402b783) |
| RF34 | [CT-RF34](Cenario_Teste/CT-RF34_Exclusao_Grupo.md) | [BUG-024](Relatorio-de-Bugs.md#bug-024), em triagem | Reprovado nas evidências; reteste pendente. | [Jam](https://jam.dev/c/b1231a75-1a65-4bf0-b795-f52a8c7d3365) |
| RF35 | [CT-RF35](Cenario_Teste/CT-RF35_Edicao_Grupo.md) | [BUG-025](Relatorio-de-Bugs.md#bug-025), em triagem | Reprovado nas evidências; reteste pendente. | [Jam](https://jam.dev/c/b1231a75-1a65-4bf0-b795-f52a8c7d3365) |
| RF36 | [CT-RF36](Cenario_Teste/CT-RF36_Filtros_Categorias.md) | Nenhum no fluxo avaliado | Aprovado conforme a gravação | [Evidências](Evidencias/CT-RF17_Filtros_Categorias/README.md) e [Jam](https://jam.dev/c/5e75e423-9c7e-43d7-aade-9b1a32c5e559) |
| RF37 | [CT-RF37](Cenario_Teste/CT-RF37_Atualizacao_Categoria.md) | Nenhum no fluxo avaliado | Aprovado conforme a gravação | [Evidências](Evidencias/CT-RF18_Atualizacao_Categoria/README.md) e [Jam](https://jam.dev/c/67664a98-2a4a-4134-91a9-7ca9b8aa9dbd) |
| RF38 | [CT-RF38](Cenario_Teste/CT-RF38_Exclusao_Categoria.md) | [BUG-009](Relatorio-de-Bugs.md#bug-009) | Reprovado nas evidências | [Evidências](Evidencias/CT-RF19_Exclusao_Categoria/README.md) e [Jam](https://jam.dev/c/c5c78b3b-2865-4226-836f-bcb0a8fc612f) |
| RF39 | [CT-RF39](Cenario_Teste/CT-RF39_Criacao_Categoria.md) | Nenhum no fluxo avaliado | Aprovado conforme a gravação | [Evidências](Evidencias/CT-RF20_Criacao_Categoria/README.md) e [Jam](https://jam.dev/c/b48ab94e-517d-48d6-8e46-70b18c033b8b) |
| RF40 | [CT-RF40](Cenario_Teste/CT-RF40_Cadastro_Categoria_Codigo_Automatico.md) | Nenhum no fluxo avaliado | Aprovado conforme a gravação | [Evidências](Evidencias/CT-RF38_Cadastro_Categoria_Codigo_Automatico/README.md) e [Jam](https://jam.dev/c/be1dbd05-217d-44c3-8a3d-240b7f6344e1) |
| RF41 | [CT-RF41](Cenario_Teste/CT-RF41_Contraste_TemaEscuro.md) | [BUG-007](Relatorio-de-Bugs.md#bug-007) | Reprovado nas evidências | [Evidências](Evidencias/CT-RF14_Contraste_TemaEscuro/README.md) e [Jam](https://jam.dev/c/6889db07-bed1-472b-8ec2-00402919cd65) |
| RF42 | [CT-RF42](Cenario_Teste/CT-RF42_Edicao_Modalidade.md) | [BUG-008](Relatorio-de-Bugs.md#bug-008) | Reprovado nas evidências | [Evidências](Evidencias/CT-RF15_Edicao_Modalidade/README.md) e [Jam](https://jam.dev/c/951efaf8-bf32-44b0-b640-a2935a6b554a) |
| RF43 | [CT-RF43](Cenario_Teste/CT-RF43_Exclusao_Modalidade.md) | Sem defeito confirmado | A validar — regra ou contexto pendente | [Evidências](Evidencias/CT-RF16_Exclusao_Modalidade/README.md) e [Jam](https://jam.dev/c/0f55f76a-cd31-4cee-93da-23c13b1ba637) |
| RF44 | [CT-RF44](Cenario_Teste/CT-RF44_Cadastro_Modalidade.md) | Nenhum no fluxo avaliado | Aprovado conforme a gravação | [Evidências](Evidencias/CT-RF39_Cadastro_Modalidade/README.md) e [Jam](https://jam.dev/c/ee9a133b-d6b1-442d-b4b0-dd87595b7e70) |
| RF45 | [CT-RF45](Cenario_Teste/CT-RF45_Exclusao_Turmas_Modalidades.md) | Sem defeito confirmado | A validar — regra ou contexto pendente | [Evidências](Evidencias/CT-RF40_Exclusao_Turmas_Modalidades/README.md) e [Jam](https://jam.dev/c/ee9a133b-d6b1-442d-b4b0-dd87595b7e70) |
| RF46 | [CT-RF46](Cenario_Teste/CT-RF46_Cadastro_Turma_Sem_Modalidade.md) | [BUG-020](Relatorio-de-Bugs.md#bug-020), em triagem | Reprovado nas evidências; reteste pendente. | [Evidências](Evidencias/CT-RF41_Cadastro_Turma_Sem_Modalidade/README.md) e [Jam](https://jam.dev/c/ee9a133b-d6b1-442d-b4b0-dd87595b7e70) |
| RF47 | [CT-RF47](Cenario_Teste/CT-RF47_Solicitacao_Saque_PagarMe.md) | Sem defeito confirmado | A validar — regra ou contexto pendente | [Evidências](Evidencias/CT-RF42_Solicitacao_Saque_PagarMe/README.md) e [Jam](https://jam.dev/c/e6e551ef-9196-4c79-b6a2-89747b1e8b33) |
| RF48 | [CT-RF48](Cenario_Teste/CT-RF48_Criacao_Cobranca_PagarMe.md) | Nenhum no fluxo avaliado | Aprovado conforme a gravação | [Evidências](Evidencias/CT-RF43_Criacao_Cobranca_PagarMe/README.md) e [Jam](https://jam.dev/c/e6e551ef-9196-4c79-b6a2-89747b1e8b33) |
| RF49 | [CT-RF49](Cenario_Teste/CT-RF49_Painel_PagarMe_Periodo.md) | [BUG-021](Relatorio-de-Bugs.md#bug-021), em triagem | Reprovado nas evidências; reteste pendente. | [Evidências](Evidencias/CT-RF45_Painel_PagarMe_Periodo/README.md) e [Jam](https://jam.dev/c/e6e551ef-9196-4c79-b6a2-89747b1e8b33) |
| RF50 | [CT-RF50](Cenario_Teste/CT-RF50_Filtros_Despesas_Fixas.md) | Nenhum no fluxo avaliado | Aprovado conforme a gravação | [Evidências](Evidencias/CT-RF46_Filtros_Despesas_Fixas/README.md) e [Jam](https://jam.dev/c/a4bac99d-e436-4792-831e-8c3a875272bb) |
| RF51 | [CT-RF51](Cenario_Teste/CT-RF51_Cadastro_Despesa_Fixa.md) | Sem defeito confirmado | A validar — regra ou contexto pendente | [Evidências](Evidencias/CT-RF47_Cadastro_Despesa_Fixa/README.md) e [Jam](https://jam.dev/c/a4bac99d-e436-4792-831e-8c3a875272bb) |
| RF52 | [CT-RF52](Cenario_Teste/CT-RF52_Exclusao_Despesa_Fixa.md) | Nenhum no fluxo avaliado | Aprovado conforme a gravação | [Evidências](Evidencias/CT-RF48_Exclusao_Despesa_Fixa/README.md) e [Jam](https://jam.dev/c/a4bac99d-e436-4792-831e-8c3a875272bb) |
| RF53 | [CT-RF53](Cenario_Teste/CT-RF53_Edicao_Despesa_Fixa.md) | Nenhum no fluxo avaliado | Aprovado conforme a gravação | [Evidências](Evidencias/CT-RF49_Edicao_Despesa_Fixa/README.md) e [Jam](https://jam.dev/c/a4bac99d-e436-4792-831e-8c3a875272bb) |
| RF54 | [CT-RF54](Cenario_Teste/CT-RF54_Relatorio_Matriculas.md) | Nenhum no fluxo avaliado | Aprovado conforme a gravação | [Evidências](Evidencias/CT-RF50_Relatorio_Matriculas/README.md) e [Jam](https://jam.dev/c/3b4777a4-e1b0-4038-9b06-26c73669d7d1) |
| RF55 | [CT-RF55](Cenario_Teste/CT-RF55_Relatorio_Contas_Receber.md) | [BUG-022](Relatorio-de-Bugs.md#bug-022), em triagem | Reprovado nas evidências; reteste pendente. | [Evidências](Evidencias/CT-RF51_Relatorio_Contas_Receber/README.md) e [Jam](https://jam.dev/c/3b4777a4-e1b0-4038-9b06-26c73669d7d1) |
| RF56 | [CT-RF56](Cenario_Teste/CT-RF56_Relatorio_Contas_Pagar_Pagas.md) | Sem defeito confirmado | A validar — regra ou contexto pendente | [Evidências](Evidencias/CT-RF52_Relatorio_Contas_Pagar_Pagas/README.md) e [Jam](https://jam.dev/c/3b4777a4-e1b0-4038-9b06-26c73669d7d1) |
| RF57 | [CT-RF57](Cenario_Teste/CT-RF57_Relatorio_Avaliacoes_Vazio.md) | [BUG-023](Relatorio-de-Bugs.md#bug-023), em triagem | Reprovado nas evidências; reteste pendente. | [Evidências](Evidencias/CT-RF53_Relatorio_Avaliacoes_Vazio/README.md) e [Jam](https://jam.dev/c/3b4777a4-e1b0-4038-9b06-26c73669d7d1) |
| RF58 | [CT-RF58](Cenario_Teste/CT-RF58_Relatorio_Clientes_Vazio.md) | [BUG-023](Relatorio-de-Bugs.md#bug-023), em triagem | Reprovado nas evidências; reteste pendente. | [Evidências](Evidencias/CT-RF54_Relatorio_Clientes_Vazio/README.md) e [Jam](https://jam.dev/c/3b4777a4-e1b0-4038-9b06-26c73669d7d1) |
| RF59 | [CT-RF59](Cenario_Teste/CT-RF59_Relatorio_Colaboradores_Vazio.md) | [BUG-023](Relatorio-de-Bugs.md#bug-023), em triagem | Reprovado nas evidências; reteste pendente. | [Evidências](Evidencias/CT-RF55_Relatorio_Colaboradores_Vazio/README.md) e [Jam](https://jam.dev/c/3b4777a4-e1b0-4038-9b06-26c73669d7d1) |
| RF60 | [CT-RF60](Cenario_Teste/CT-RF60_Relatorio_Caixas_Vazio.md) | [BUG-023](Relatorio-de-Bugs.md#bug-023), em triagem | Reprovado nas evidências; reteste pendente. | [Evidências](Evidencias/CT-RF56_Relatorio_Caixas_Vazio/README.md) e [Jam](https://jam.dev/c/3b4777a4-e1b0-4038-9b06-26c73669d7d1) |
| RF61 | [CT-RF61](Cenario_Teste/CT-RF61_Temas_Prospeccao.md) | — | Aprovado conforme o resumo da gravação | [Evidências](Evidencias/CT-RF74_Temas_Prospeccao/README.md) e [Jam](https://jam.dev/c/5dc9fc15-8e13-4f90-b21f-a49aedc6731e) |
| RF62 | [CT-RF62](Cenario_Teste/CT-RF62_Tema_Notificacoes_Prospeccao.md) | Nenhum no fluxo avaliado | Aprovado conforme a gravação | [Evidências](Evidencias/CT-RF85_Tema_Notificacoes_Prospeccao/README.md) e [Jam](https://jam.dev/c/308607ff-8abc-40af-8c7c-429ce506ed64) |
| RF63 | [CT-RF63](Cenario_Teste/CT-RF63_Busca_Leads_Prospeccao.md) | Nenhum no fluxo avaliado | Aprovado conforme a gravação | [Evidências](Evidencias/CT-RF86_Busca_Leads_Prospeccao/README.md) e [Jam](https://jam.dev/c/308607ff-8abc-40af-8c7c-429ce506ed64) |
| RF64 | [CT-RF64](Cenario_Teste/CT-RF64_Filtro_Estagio_Leads.md) | Nenhum no fluxo avaliado | Aprovado conforme a gravação | [Evidências](Evidencias/CT-RF87_Filtro_Estagio_Leads/README.md) e [Jam](https://jam.dev/c/308607ff-8abc-40af-8c7c-429ce506ed64) |
| RF65 | [CT-RF65](Cenario_Teste/CT-RF65_Cadastro_Lead_Novo_Contato.md) | — | Aprovado conforme o resumo da gravação | [Evidências](Evidencias/CT-RF77_Cadastro_Lead_Novo_Contato/README.md) e [Jam](https://jam.dev/c/29447c6a-90f5-48b2-ac5d-d43cad44a782) |
| RF66 | [CT-RF66](Cenario_Teste/CT-RF66_Cadastro_Lead_Interessado.md) | — | Aprovado conforme o resumo da gravação | [Evidências](Evidencias/CT-RF78_Cadastro_Lead_Interessado/README.md) e [Jam](https://jam.dev/c/f8735cbf-4043-4467-b43f-3cad7eff0da8) |
| RF67 | [CT-RF67](Cenario_Teste/CT-RF67_Cadastro_Lead_Aula_Experimental.md) | — | Aprovado conforme o resumo da gravação | [Evidências](Evidencias/CT-RF79_Cadastro_Lead_Aula_Experimental/README.md) e [Jam](https://jam.dev/c/bef3d877-056b-4274-87c3-da37869c54fd) |
| RF68 | [CT-RF68](Cenario_Teste/CT-RF68_Cadastro_Lead_Proposta.md) | — | Aprovado conforme o resumo da gravação | [Evidências](Evidencias/CT-RF80_Cadastro_Lead_Proposta/README.md) e [Jam](https://jam.dev/c/84f94285-ae5f-4f95-b640-a9b107565aa6) |
| RF69 | [CT-RF69](Cenario_Teste/CT-RF69_Cadastro_Lead_Apenas_Nome.md) | [BUG-037](Relatorio-de-Bugs.md#bug-037) | Reprovado conforme o relato; regra de obrigatoriedade a confirmar | [Evidências](Evidencias/CT-RF83_Cadastro_Lead_Apenas_Nome/README.md) e [Jam](https://jam.dev/c/ef3df03c-16ce-4cb6-b0c7-d04514cab4f6) |
| RF70 | [CT-RF70](Cenario_Teste/CT-RF70_Cadastro_Lead_Fechado.md) | — | Aprovado conforme o resumo da gravação | [Evidências](Evidencias/CT-RF84_Cadastro_Lead_Fechado/README.md) e [Jam](https://jam.dev/c/775b9003-fdf7-4ad5-8882-15ba606b6674) |
| RF71 | [CT-RF71](Cenario_Teste/CT-RF71_Cadastro_Lead_Prospeccao.md) | Sem defeito confirmado | A validar — regra ou contexto pendente | [Evidências](Evidencias/CT-RF88_Cadastro_Lead_Prospeccao/README.md) e [Jam](https://jam.dev/c/308607ff-8abc-40af-8c7c-429ce506ed64) |
| RF72 | [CT-RF72](Cenario_Teste/CT-RF72_Telefone_Lead_Sem_Validacao.md) | [BUG-038](Relatorio-de-Bugs.md#bug-038), em triagem | Reprovado nas evidências; reteste pendente. | [Evidências](Evidencias/CT-RF89_Telefone_Lead_Sem_Validacao/README.md) e [Jam](https://jam.dev/c/308607ff-8abc-40af-8c7c-429ce506ed64) |
| RF73 | [CT-RF73](Cenario_Teste/CT-RF73_Detalhes_Lead_Cancelamento.md) | — | Aprovado conforme o resumo da gravação | [Evidências](Evidencias/CT-RF75_Detalhes_Lead_Cancelamento/README.md) e [Jam](https://jam.dev/c/7ef0ee0b-497e-48b8-a57d-cd914558d303) |
| RF74 | [CT-RF74](Cenario_Teste/CT-RF74_Exclusao_Leads_Confirmacao.md) | — | Aprovado conforme o resumo da gravação | [Evidências](Evidencias/CT-RF76_Exclusao_Leads_Confirmacao/README.md) e [Jam](https://jam.dev/c/2ac5e5ed-b10f-4cc9-9f97-7ba65ca560f8) |
| RF75 | [CT-RF75](Cenario_Teste/CT-RF75_Edicao_Lead_Prospeccao.md) | Nenhum no fluxo avaliado | Aprovado conforme a gravação | [Evidências](Evidencias/CT-RF90_Edicao_Lead_Prospeccao/README.md) e [Jam](https://jam.dev/c/308607ff-8abc-40af-8c7c-429ce506ed64) |
| RF76 | [CT-RF76](Cenario_Teste/CT-RF76_Tema_Notificacoes_Planos.md) | Nenhum no fluxo avaliado | Aprovado conforme a gravação | [Evidências](Evidencias/CT-RF100_Tema_Notificacoes_Planos/README.md) e [Jam](https://jam.dev/c/233c5d21-e108-4a55-b6f6-8738cb3fc6a6) |
| RF77 | [CT-RF77](Cenario_Teste/CT-RF77_Filtros_Planos.md) | Nenhum no fluxo avaliado | Aprovado conforme a gravação | [Evidências](Evidencias/CT-RF99_Filtros_Planos/README.md) e [Jam](https://jam.dev/c/233c5d21-e108-4a55-b6f6-8738cb3fc6a6) |
| RF78 | [CT-RF78](Cenario_Teste/CT-RF78_Cadastro_Plano.md) | Nenhum no fluxo avaliado | Aprovado conforme a gravação | [Evidências](Evidencias/CT-RF101_Cadastro_Plano/README.md) e [Jam](https://jam.dev/c/233c5d21-e108-4a55-b6f6-8738cb3fc6a6) |
| RF79 | [CT-RF79](Cenario_Teste/CT-RF79_Contador_Ativos_Planos.md) | [BUG-041](Relatorio-de-Bugs.md#bug-041), em triagem | Reprovado nas evidências; reteste pendente. | [Evidências](Evidencias/CT-RF102_Contador_Ativos_Planos/README.md) e [Jam](https://jam.dev/c/233c5d21-e108-4a55-b6f6-8738cb3fc6a6) |
| RF80 | [CT-RF80](Cenario_Teste/CT-RF80_Edicao_Plano.md) | Nenhum no fluxo avaliado | Aprovado conforme a gravação | [Evidências](Evidencias/CT-RF103_Edicao_Plano/README.md) e [Jam](https://jam.dev/c/233c5d21-e108-4a55-b6f6-8738cb3fc6a6) |
| RF81 | [CT-RF81](Cenario_Teste/CT-RF81_Cadastro_Modelo_Contrato.md) | Nenhum no fluxo avaliado | Aprovado conforme a gravação | [Evidências](Evidencias/CT-RF97_Cadastro_Modelo_Contrato/README.md) e [Jam](https://jam.dev/c/44dbbd39-6915-45d6-8dd1-5f30c1432ca0) |
| RF82 | [CT-RF82](Cenario_Teste/CT-RF82_Variaveis_Preview_Modelo_Contrato.md) | Nenhum no fluxo avaliado | Aprovado conforme a gravação | [Evidências](Evidencias/CT-RF96_Variaveis_Preview_Modelo_Contrato/README.md) e [Jam](https://jam.dev/c/44dbbd39-6915-45d6-8dd1-5f30c1432ca0) |
| RF83 | [CT-RF83](Cenario_Teste/CT-RF83_Listagem_Modelos_Contrato_Vazia.md) | [BUG-040](Relatorio-de-Bugs.md#bug-040), em triagem | Reprovado nas evidências; reteste pendente. | [Evidências](Evidencias/CT-RF98_Listagem_Modelos_Contrato_Vazia/README.md) e [Jam](https://jam.dev/c/44dbbd39-6915-45d6-8dd1-5f30c1432ca0) |
| RF84 | [CT-RF84](Cenario_Teste/CT-RF84_Filtros_Tipos_Pagamento.md) | Sem defeito confirmado | A validar — regra ou contexto pendente | [Evidências](Evidencias/CT-RF104_Filtros_Tipos_Pagamento/README.md) e [Jam](https://jam.dev/c/e8734e3d-3f8e-458b-8c7d-e85eea882e50) |
| RF85 | [CT-RF85](Cenario_Teste/CT-RF85_Cadastro_Tipo_Pagamento_Status.md) | [BUG-042](Relatorio-de-Bugs.md#bug-042), em triagem | Reprovado nas evidências; reteste pendente. | [Evidências](Evidencias/CT-RF105_Cadastro_Tipo_Pagamento_Status/README.md) e [Jam](https://jam.dev/c/e8734e3d-3f8e-458b-8c7d-e85eea882e50) |
| RF86 | [CT-RF86](Cenario_Teste/CT-RF86_Edicao_Tipo_Pagamento.md) | Nenhum no fluxo avaliado | Aprovado conforme a gravação | [Evidências](Evidencias/CT-RF106_Edicao_Tipo_Pagamento/README.md) e [Jam](https://jam.dev/c/e8734e3d-3f8e-458b-8c7d-e85eea882e50) |
| RF87 | [CT-RF87](Cenario_Teste/CT-RF87_Exclusao_Tipo_Pagamento_Em_Uso.md) | [BUG-043](Relatorio-de-Bugs.md#bug-043), em triagem | Reprovado nas evidências; reteste pendente. | [Evidências](Evidencias/CT-RF107_Exclusao_Tipo_Pagamento_Em_Uso/README.md) e [Jam](https://jam.dev/c/e8734e3d-3f8e-458b-8c7d-e85eea882e50) |
| RF88 | [CT-RF88](Cenario_Teste/CT-RF88_Tema_Notificacoes_Tipos_Pagamento.md) | Nenhum no fluxo avaliado | Aprovado conforme a gravação | [Evidências](Evidencias/CT-RF108_Tema_Notificacoes_Tipos_Pagamento/README.md) e [Jam](https://jam.dev/c/e8734e3d-3f8e-458b-8c7d-e85eea882e50) |
| RF89 | [CT-RF89](Cenario_Teste/CT-RF89_Cadastro_Bandeira_Parcela_Listagem.md) | [BUG-035](Relatorio-de-Bugs.md#bug-035) | Reprovado nas evidências resumidas | [Evidências](Evidencias/CT-RF81_Cadastro_Bandeira_Parcela_Listagem/README.md) e [Jam](https://jam.dev/c/2f0280fb-6b7f-4cf0-a45c-02f8c16b6c5e) |
| RF90 | [CT-RF90](Cenario_Teste/CT-RF90_Tema_Escuro_Bandeiras.md) | [BUG-036](Relatorio-de-Bugs.md#bug-036) | Reprovado nas evidências resumidas | [Evidências](Evidencias/CT-RF82_Tema_Escuro_Bandeiras/README.md) e [Jam](https://jam.dev/c/ae4dc198-8a42-4451-898a-fb376596c744) |
| RF91 | [CT-RF91](Cenario_Teste/CT-RF91_Data_Nascimento_Futura_Colaborador.md) | [BUG-026](Relatorio-de-Bugs.md#bug-026), em triagem | Reprovado nas evidências; reteste pendente. | [Jam](https://jam.dev/c/6dd75961-8e8f-4c8e-939a-19595a1f8a32) |
| RF92 | [CT-RF92](Cenario_Teste/CT-RF92_Data_Nascimento_Obrigatoria_Colaborador.md) | [BUG-027](Relatorio-de-Bugs.md#bug-027), em triagem | Reprovado nas evidências; reteste pendente. | [Jam](https://jam.dev/c/04aa5ba0-ac7e-43b6-a7f3-91ae82417a85) |
| RF93 | [CT-RF93](Cenario_Teste/CT-RF93_CREF_Formato_Colaborador.md) | [BUG-028](Relatorio-de-Bugs.md#bug-028), em triagem | Reprovado nas evidências; formato a confirmar. | [Jam](https://jam.dev/c/243d9699-4bee-495d-ae65-9a02e42813b3) |
| RF94 | [CT-RF94](Cenario_Teste/CT-RF94_Edicao_Colaborador_Campo_Obrigatorio_Vazio.md) | [BUG-029](Relatorio-de-Bugs.md#bug-029), em triagem | Reprovado nas evidências; campo exato pendente. | [Jam](https://jam.dev/c/4219c1b3-085e-4218-b181-5cf448d64cea) |
| RF95 | [CT-RF95](Cenario_Teste/CT-RF95_Funcao_Duplicada_Colaborador.md) | [BUG-030](Relatorio-de-Bugs.md#bug-030), em triagem | Reprovado nas evidências; reteste pendente. | [Jam](https://jam.dev/c/ba2400f9-dbb0-45bc-a509-187249dbe9da) |
| RF96 | [CT-RF96](Cenario_Teste/CT-RF96_Exclusao_Colaborador_Erro_500.md) | [BUG-031](Relatorio-de-Bugs.md#bug-031), em triagem | Reprovado nas evidências; reteste pendente. | [Jam](https://jam.dev/c/05be297b-22d9-4d26-beff-937526bcd816) |
| RF97 | [CT-RF97](Cenario_Teste/CT-RF97_Busca_Nome_Colaborador_Paginacao.md) | [BUG-033](Relatorio-de-Bugs.md#bug-033), em triagem | Reprovado nas evidências; reteste pendente. | [Jam](https://jam.dev/c/b35516e3-c571-47ea-b233-28f00d1fca4c) |
| RF98 | [CT-RF98](Cenario_Teste/CT-RF98_Busca_Codigo_Existente_Colaborador.md) | — | Aprovado conforme a gravação. | [Jam](https://jam.dev/c/415a6ea3-273b-40f7-b3e4-f2b767dc7dfd) |
| RF99 | [CT-RF99](Cenario_Teste/CT-RF99_Busca_Codigo_Inexistente_Colaborador.md) | [BUG-034](Relatorio-de-Bugs.md#bug-034), em triagem | Reprovado nas evidências; reteste pendente. | [Jam](https://jam.dev/c/cdbb3d76-3d6a-4d36-adf9-edd935b5a449) |
| RF100 | [CT-RF100](Cenario_Teste/CT-RF100_Cadastro_Anamnese.md) | [BUG-032](Relatorio-de-Bugs.md#bug-032), em triagem | Reprovado nas evidências; reteste pendente. | [Jam](https://jam.dev/c/7be0fe71-3419-4050-b63f-473d943fa08e) |
| RF101 | [CT-RF101](Cenario_Teste/CT-RF101_Gestao_Modelos_Anamnese.md) | Nenhum identificado no fluxo avaliado | Aprovado conforme a gravação | [Jam](https://jam.dev/c/4c1e9deb-20ca-417f-ad09-48749857266e) |
| RF102 | [CT-RF102](Cenario_Teste/CT-RF102_Gestao_Categorias_Anamnese.md) | Nenhum identificado no fluxo avaliado | Aprovado conforme a gravação | [Jam](https://jam.dev/c/fdb1c9f8-c428-4726-9742-617800325d09) |
| RF103 | [CT-RF103](Cenario_Teste/CT-RF103_Edicao_Pergunta_Anamnese.md) | [BUG-044](Relatorio-de-Bugs.md#bug-044), em triagem | Reprovado nas evidências | [Jam](https://jam.dev/c/84b116fb-4640-4b1e-9148-9a169b8aa2b0) |
| RF104 | [CT-RF104](Cenario_Teste/CT-RF104_Central_Configuracao_Risco_Evasao_Cancelar.md) | Nenhum no fluxo avaliado | Aprovado conforme a gravação | [Evidências](Evidencias/CT-RF128_Central_Configuracao_Risco_Evasao_Cancelar/README.md) e [Jam — PED-06 — Configuração de Risco de Evasão](https://jam.dev/c/d49b8ffc-a6e2-4e37-a618-c280b5e807db) |
| RF105 | [CT-RF105](Cenario_Teste/CT-RF105_Central_Risco_Evasao_Executar_Agora.md) | Nenhum no fluxo avaliado | Aprovado conforme a gravação | [Evidências](Evidencias/CT-RF137_Central_Risco_Evasao_Executar_Agora/README.md) e [Jam — PED-04 — Executar Risco de Evasão](https://jam.dev/c/be5418c7-8d87-4b6c-9c64-a9b33b5f7da6) |
| RF106 | [CT-RF106](Cenario_Teste/CT-RF106_Central_Abrir_Resultados_Risco_Evasao.md) | Nenhum no fluxo avaliado | Aprovado conforme a gravação | [Evidências](Evidencias/CT-RF138_Central_Abrir_Resultados_Risco_Evasao/README.md) e [Jam — PED-05 — Ver resultados de Risco de Evasão](https://jam.dev/c/ac5bce26-f4a8-401b-bb23-d09d5253751a) |
| RF107 | [CT-RF107](Cenario_Teste/CT-RF107_Central_Desativar_Risco_Evasao_Contador.md) | [BUG-049](Relatorio-de-Bugs.md#bug-049), em triagem | Reprovado nas evidências | [Evidências](Evidencias/CT-RF135_Central_Desativar_Risco_Evasao_Contador/README.md) e [Jam — PED-02 — Desativar Risco de Evasão](https://jam.dev/c/b63ec55f-f8b6-41aa-af4c-d4cdd4515de8) |
| RF108 | [CT-RF108](Cenario_Teste/CT-RF108_Central_Resultados_IA_Execucao_Evasao.md) | Nenhum no fluxo avaliado | Aprovado conforme a gravação | [Evidências](Evidencias/CT-RF123_Central_Resultados_IA_Execucao_Evasao/README.md) e [Jam — PED-14 — Execução de Risco de Evasão](https://jam.dev/c/efe26a44-458a-4802-bd48-8e23c5ac5fd9) |
| RF109 | [CT-RF109](Cenario_Teste/CT-RF109_Central_Aniversariantes_Previa_Risco.md) | [BUG-048](Relatorio-de-Bugs.md#bug-048), em triagem | Reprovado nas evidências | [Evidências](Evidencias/CT-RF129_Central_Aniversariantes_Previa_Risco/README.md) e [Jam — PED-07 — Configuração de Aniversariantes](https://jam.dev/c/c66d4d01-aee2-4037-a8fd-858da21a0a14) |
| RF110 | [CT-RF110](Cenario_Teste/CT-RF110_Central_Ativar_Aniversariantes_Contador.md) | [BUG-049](Relatorio-de-Bugs.md#bug-049), em triagem | Reprovado nas evidências | [Evidências](Evidencias/CT-RF136_Central_Ativar_Aniversariantes_Contador/README.md) e [Jam — PED-03 — Ativar Aniversariantes](https://jam.dev/c/60c724da-6760-4238-91f5-2ddad8f42bb3) |
| RF111 | [CT-RF111](Cenario_Teste/CT-RF111_Central_Recursos_Em_Desenvolvimento.md) | Nenhum no fluxo avaliado | Aprovado conforme a gravação | [Evidências](Evidencias/CT-RF130_Central_Recursos_Em_Desenvolvimento/README.md) e [Jam — PED-08 — Recursos em desenvolvimento](https://jam.dev/c/0a7ae8fb-980d-4df2-8ef8-de78d6b11b8f) |
| RF112 | [CT-RF112](Cenario_Teste/CT-RF112_Central_Automacoes_Atualizar.md) | Nenhum no fluxo avaliado | Aprovado conforme a gravação | [Evidências](Evidencias/CT-RF134_Central_Automacoes_Atualizar/README.md) e [Jam — PED-01 — Atualizar Central de Automações](https://jam.dev/c/efe35b08-8733-434c-a6fa-32c45e248ae1) |
| RF113 | [CT-RF113](Cenario_Teste/CT-RF113_Resultados_IA_Filtro_Hoje.md) | Nenhum no fluxo avaliado | Aprovado conforme a gravação | [Evidências](Evidencias/CT-RF131_Resultados_IA_Filtro_Hoje/README.md) e [Jam — PED-09 — Hoje](https://jam.dev/c/a83c4c74-0b8e-4242-9612-0202c9063d56) |
| RF114 | [CT-RF114](Cenario_Teste/CT-RF114_Resultados_IA_Filtro_7_Dias.md) | Nenhum no fluxo avaliado | Aprovado conforme a gravação | [Evidências](Evidencias/CT-RF132_Resultados_IA_Filtro_7_Dias/README.md) e [Jam — PED-10 — Últimos 7 dias](https://jam.dev/c/cbf45b87-b7b6-4314-a359-c5e706aa755e) |
| RF115 | [CT-RF115](Cenario_Teste/CT-RF115_Resultados_IA_Filtro_30_Dias.md) | Nenhum no fluxo avaliado | Aprovado conforme a gravação | [Evidências](Evidencias/CT-RF133_Resultados_IA_Filtro_30_Dias/README.md) e [Jam — PED-11 — Últimos 30 dias](https://jam.dev/c/2756d5c1-a823-482b-bf8d-878357b8b087) |
| RF116 | [CT-RF116](Cenario_Teste/CT-RF116_Resultados_IA_Filtro_90_Dias.md) | Nenhum no fluxo avaliado | Aprovado conforme a gravação | [Evidências](Evidencias/CT-RF122_Resultados_IA_Filtro_90_Dias/README.md) e [Jam — PED-12 — Últimos 90 dias](https://jam.dev/c/1728cfc2-1d36-4ea4-ab68-68a84458c359) |
| RF117 | [CT-RF117](Cenario_Teste/CT-RF117_Configuracoes_Home_Salvamento.md) | Sem defeito confirmado | A validar — regra ou contexto pendente | [Evidências](Evidencias/CT-RF44_Configuracoes_Home_Salvamento/README.md) e [Jam](https://jam.dev/c/e6e551ef-9196-4c79-b6a2-89747b1e8b33) |
| RF118 | [CT-RF118](Cenario_Teste/CT-RF118_Configuracoes_Dias_Ausencia_Vazio.md) | Sem defeito confirmado | A validar — regra ou contexto pendente | [Evidências](Evidencias/CT-RF116_Configuracoes_Dias_Ausencia_Vazio/README.md) e [Jam — PED-20 — Dias de ausência vazio](https://jam.dev/c/4e96d4fa-65b5-459b-a795-854496e5753c) |
| RF119 | [CT-RF119](Cenario_Teste/CT-RF119_Configuracoes_Salvar_Dias_Ausencia_Valido.md) | Nenhum no fluxo avaliado | Aprovado conforme a gravação | [Evidências](Evidencias/CT-RF125_Configuracoes_Salvar_Dias_Ausencia_Valido/README.md) e [Jam — PED-16 — Salvar dias de ausência](https://jam.dev/c/12d6bba7-a67e-4882-86a5-4dd08d194af2) |
| RF120 | [CT-RF120](Cenario_Teste/CT-RF120_Configuracoes_Dias_Ausencia_Negativo.md) | [BUG-047](Relatorio-de-Bugs.md#bug-047), em triagem | Reprovado nas evidências | [Evidências](Evidencias/CT-RF126_Configuracoes_Dias_Ausencia_Negativo/README.md) e [Jam — PED-17 — Dias de ausência negativos](https://jam.dev/c/d5786f67-6e5f-44f5-bbba-fbd763a88740) |
| RF121 | [CT-RF121](Cenario_Teste/CT-RF121_Configuracoes_Dias_Ausencia_Texto.md) | Sem defeito confirmado | A validar — regra ou contexto pendente | [Evidências](Evidencias/CT-RF127_Configuracoes_Dias_Ausencia_Texto/README.md) e [Jam — PED-18 — Dias de ausência com texto](https://jam.dev/c/c578ed7a-c11c-4cef-8a6c-84d0244f21a5) |
| RF122 | [CT-RF122](Cenario_Teste/CT-RF122_Configuracoes_Cancelar_Alteracao.md) | Nenhum no fluxo avaliado | Aprovado conforme a gravação | [Evidências](Evidencias/CT-RF117_Configuracoes_Cancelar_Alteracao/README.md) e [Jam — PED-20 — Cancelar alteração](https://jam.dev/c/e8faa199-1177-4563-8b00-590606669a1d) |
| RF123 | [CT-RF123](Cenario_Teste/CT-RF123_Configuracoes_Trabalha_Com_Turmas.md) | Nenhum no fluxo avaliado | Aprovado conforme a gravação | [Evidências](Evidencias/CT-RF118_Configuracoes_Trabalha_Com_Turmas/README.md) e [Jam — PED-21 — Trabalha com turmas](https://jam.dev/c/a51c33a5-537a-40fd-a55d-990b70ac0696) |
| RF124 | [CT-RF124](Cenario_Teste/CT-RF124_Configuracoes_Academia_Marcada_Box.md) | Nenhum no fluxo avaliado | Aprovado conforme a gravação | [Evidências](Evidencias/CT-RF119_Configuracoes_Academia_Marcada_Box/README.md) e [Jam — PED-22 — Academia marcada como Box](https://jam.dev/c/16dc862d-c3f9-4392-9037-526818e86cd6) |
| RF125 | [CT-RF125](Cenario_Teste/CT-RF125_Configuracoes_Acesso_Desktop.md) | Nenhum no fluxo avaliado | Aprovado conforme a gravação | [Evidências](Evidencias/CT-RF120_Configuracoes_Acesso_Desktop/README.md) e [Jam — PED-23 — Acesso desktop](https://jam.dev/c/466be253-ad9a-4856-b567-fb17e1fdd479) |
| RF126 | [CT-RF126](Cenario_Teste/CT-RF126_Configuracoes_Abas_Biometria_Senha.md) | [BUG-046](Relatorio-de-Bugs.md#bug-046), em triagem | Reprovado nas evidências | [Evidências](Evidencias/CT-RF124_Configuracoes_Abas_Biometria_Senha/README.md) e [Jam — PED-15](https://jam.dev/c/38105352-c89c-492e-bca1-78e2f4017ae2) |
| RF127 | [CT-RF127](Cenario_Teste/CT-RF127_Integracoes_WhatsApp_Mascarar_API_Key.md) | Nenhum no fluxo avaliado | Aprovado conforme a gravação | [Evidências](Evidencias/CT-RF139_Integracoes_WhatsApp_Mascarar_API_Key/README.md) e [Jam 1 — Mascaramento da API Key](https://jam.dev/c/ef0b67d5-1eea-49b7-84ea-bb306143df4a) |
| RF128 | [CT-RF128](Cenario_Teste/CT-RF128_Integracoes_WhatsApp_Validar_URL_API.md) | Sem defeito confirmado | A validar — regra ou contexto pendente | [Evidências](Evidencias/CT-RF140_Integracoes_WhatsApp_Validar_URL_API/README.md) e [Jam 2 — Validação da URL da API](https://jam.dev/c/0d7c7274-c798-4e26-91a3-f8162b7ce932) |
| RF129 | [CT-RF129](Cenario_Teste/CT-RF129_Integracoes_WhatsApp_Instancia_Obrigatoria.md) | Nenhum no fluxo avaliado | Aprovado conforme a gravação | [Evidências](Evidencias/CT-RF141_Integracoes_WhatsApp_Instancia_Obrigatoria/README.md) e [Jam 3 — Obrigatoriedade do Nome da Instância](https://jam.dev/c/8bb7f049-0299-49c9-9fb5-ff7b144f58d2) |
| RF130 | [CT-RF130](Cenario_Teste/CT-RF130_Integracoes_WhatsApp_Persistir_Ativo.md) | Nenhum no fluxo avaliado | Aprovado conforme a gravação | [Evidências](Evidencias/CT-RF142_Integracoes_WhatsApp_Persistir_Ativo/README.md) e [Jam 4 — Persistência da opção Ativo](https://jam.dev/c/593bb290-936a-4e01-a5af-cc8041c4eb55) |
| RF131 | [CT-RF131](Cenario_Teste/CT-RF131_Integracoes_WhatsApp_Conectar_Evolution.md) | [BUG-050](Relatorio-de-Bugs.md#bug-050), em triagem | Reprovado nas evidências | [Evidências](Evidencias/CT-RF143_Integracoes_WhatsApp_Conectar_Evolution/README.md) e [Jam 5 — Tentativas de conexão pela Evolution API](https://jam.dev/c/087b5e4f-7d73-4be3-979d-9a39f474b836) |
| RF132 | [CT-RF132](Cenario_Teste/CT-RF132_Integracoes_WhatsApp_Atualizar_Status.md) | [BUG-050](Relatorio-de-Bugs.md#bug-050) na tentativa posterior de conexão | Aprovado conforme a gravação | [Evidências](Evidencias/CT-RF144_Integracoes_WhatsApp_Atualizar_Status/README.md) e [Jam 6 — Atualização manual de status](https://jam.dev/c/0da79ab0-b557-46af-a48c-60c1a8a62628) |
| RF133 | [CT-RF133](Cenario_Teste/CT-RF133_Integracoes_WhatsApp_Atualizar_Status_Aguardando_QR.md) | Nenhum no fluxo avaliado | Aprovado conforme a gravação | [Evidências](Evidencias/CT-RF150_Integracoes_WhatsApp_Atualizar_Status_Aguardando_QR/README.md) e [Jam 6 — Atualização de status enquanto aguarda QR Code](https://jam.dev/c/7a892fd3-b6b0-49bc-a463-1b79c4b6ad50) |
| RF134 | [CT-RF134](Cenario_Teste/CT-RF134_Configuracoes_Aniversario_Salvar_WhatsApp_SMS.md) | Nenhum no fluxo avaliado | Aprovado conforme a gravação | [Evidências](Evidencias/CT-RF145_Configuracoes_Aniversario_Salvar_WhatsApp_SMS/README.md) e [Jam 1 — Mensagens de aniversário por WhatsApp e SMS](https://jam.dev/c/01502381-e54a-40c9-b65b-e87c7f049154) |
| RF135 | [CT-RF135](Cenario_Teste/CT-RF135_Configuracoes_Aniversario_Desabilitar_Envio_Automatico.md) | Nenhum no fluxo avaliado | Aprovado conforme a gravação | [Evidências](Evidencias/CT-RF154_Configuracoes_Aniversario_Desabilitar_Envio_Automatico/README.md) e [Jam 4 — Desativação do envio automático de aniversário](https://jam.dev/c/ee8a2ba9-164c-42bb-8efe-927dd6c534d5) |
| RF136 | [CT-RF136](Cenario_Teste/CT-RF136_Configuracoes_Aniversario_Cancelar_Mensagem_WhatsApp.md) | Nenhum no fluxo avaliado | Aprovado conforme a gravação | [Evidências](Evidencias/CT-RF155_Configuracoes_Aniversario_Cancelar_Mensagem_WhatsApp/README.md) e [Jam 5 — Cancelamento da edição da mensagem de WhatsApp](https://jam.dev/c/a58b851c-77c2-4a49-be3b-8a5c007d2bcb) |
| RF137 | [CT-RF137](Cenario_Teste/CT-RF137_Configuracoes_Aniversario_Inserir_Variaveis_WhatsApp.md) | Nenhum no fluxo avaliado | Aprovado conforme a gravação | [Evidências](Evidencias/CT-RF156_Configuracoes_Aniversario_Inserir_Variaveis_WhatsApp/README.md) e [Jam 6 — Inserção de variáveis na mensagem de WhatsApp](https://jam.dev/c/fb2c4949-c68d-4f90-b47c-44da9dbe58a3) |
| RF138 | [CT-RF138](Cenario_Teste/CT-RF138_Configuracoes_Pagamento_Online_Desativar.md) | Nenhum no fluxo avaliado | Aprovado conforme a gravação | [Evidências](Evidencias/CT-RF146_Configuracoes_Pagamento_Online_Desativar/README.md) e [Jam 2 — Desativação do Pagamento Online](https://jam.dev/c/845de9b6-12f7-4002-a8ba-82e1a85affba) |
| RF139 | [CT-RF139](Cenario_Teste/CT-RF139_Configuracoes_Design_Salvar_Cor_Principal.md) | Nenhum no fluxo avaliado | Aprovado conforme a gravação | [Evidências](Evidencias/CT-RF147_Configuracoes_Design_Salvar_Cor_Principal/README.md) e [Jam 3 — Persistência da Cor Principal](https://jam.dev/c/c4f77e18-3b66-4c68-97e7-bd70a9bb70f9) |
| RF140 | [CT-RF140](Cenario_Teste/CT-RF140_Configuracoes_Design_Validar_Cor_Secundaria.md) | [BUG-051](Relatorio-de-Bugs.md#bug-051), em triagem | Reprovado nas evidências | [Evidências](Evidencias/CT-RF148_Configuracoes_Design_Validar_Cor_Secundaria/README.md) e [Jam 4 — Validação da Cor Secundária](https://jam.dev/c/41aaf50a-2506-471a-8eeb-943674571771) |
| RF141 | [CT-RF141](Cenario_Teste/CT-RF141_Configuracoes_Design_Logo_Limite_Tamanho.md) | [BUG-052](Relatorio-de-Bugs.md#bug-052), em triagem | Reprovado nas evidências | [Evidências](Evidencias/CT-RF149_Configuracoes_Design_Logo_Limite_Tamanho/README.md) e [Jam 5 — Rejeição de logo pelo limite de tamanho](https://jam.dev/c/7aaeac50-8269-4cd6-b7f6-4c8c3740b0e5) |
| RF142 | [CT-RF142](Cenario_Teste/CT-RF142_Configuracoes_Avaliacao_Desativar_Cobranca.md) | Nenhum no fluxo avaliado | Aprovado conforme a gravação | [Evidências](Evidencias/CT-RF151_Configuracoes_Avaliacao_Desativar_Cobranca/README.md) e [Jam 1 — Desativação da cobrança da avaliação](https://jam.dev/c/851c15d8-4076-4493-ad3f-c2ba0316d0ca) |
| RF143 | [CT-RF143](Cenario_Teste/CT-RF143_Configuracoes_Avaliacao_Tipo_Bioimpedancia.md) | Nenhum no fluxo avaliado | Aprovado conforme a gravação | [Evidências](Evidencias/CT-RF152_Configuracoes_Avaliacao_Tipo_Bioimpedancia/README.md) e [Jam 2 — Alteração do tipo para Bioimpedância](https://jam.dev/c/8685a48a-ed9a-4169-a825-90036265b185) |
| RF144 | [CT-RF144](Cenario_Teste/CT-RF144_Configuracoes_Avaliacao_Habilitar_Teste_Fisico.md) | Nenhum no fluxo avaliado | Aprovado conforme a gravação | [Evidências](Evidencias/CT-RF153_Configuracoes_Avaliacao_Habilitar_Teste_Fisico/README.md) e [Jam 3 — Habilitação de Teste Físico](https://jam.dev/c/86466f6e-b180-439f-ab1d-dde2484595a3) |
| RF145 | [CT-RF145](Cenario_Teste/CT-RF145_Configuracoes_Biometria_Cancelar_Edicao_Senha.md) | Nenhum no fluxo avaliado | Aprovado conforme a gravação | [Evidências](Evidencias/CT-RF162_Configuracoes_Biometria_Cancelar_Edicao_Senha/README.md) e [Jam 6 — Cancelamento da edição no formulário de Biometria](https://jam.dev/c/ccac55df-d2c8-4b11-898b-d12d87aced72) |
| RF146 | [CT-RF146](Cenario_Teste/CT-RF146_Configuracoes_Biometria_Rejeitar_IP_Invalido.md) | [BUG-053](Relatorio-de-Bugs.md#bug-053), em triagem | Reprovado nas evidências | [Evidências](Evidencias/CT-RF163_Configuracoes_Biometria_Rejeitar_IP_Invalido/README.md) e [Jam 7 — Validação de IP do aparelho](https://jam.dev/c/5b8eea1f-3c87-4497-8fb1-da49f09f9854) |
| RF147 | [CT-RF147](Cenario_Teste/CT-RF147_Configuracoes_Biometria_Persistir_Porta.md) | Nenhum no fluxo avaliado | Aprovado conforme a gravação | [Evidências](Evidencias/CT-RF164_Configuracoes_Biometria_Persistir_Porta/README.md) e [Jam 8 — Persistência da porta do aparelho](https://jam.dev/c/7d7bf60a-d8a8-4b7e-80da-1e73b45819cb) |
| RF148 | [CT-RF148](Cenario_Teste/CT-RF148_Configuracoes_Biometria_Validar_Dias_Bloqueio.md) | [BUG-054](Relatorio-de-Bugs.md#bug-054), em triagem | Reprovado nas evidências | [Evidências](Evidencias/CT-RF165_Configuracoes_Biometria_Validar_Dias_Bloqueio/README.md) e [Jam 9 — Validação de dias de bloqueio da catraca](https://jam.dev/c/f607bc49-184f-4d55-81ab-7db825af6021) |
| RF149 | [CT-RF149](Cenario_Teste/CT-RF149_Modelo_Ficha_Sem_Nome.md) | Nenhum no fluxo avaliado | Aprovado conforme a gravação | [Evidências](Evidencias/CT-RF109_Modelo_Ficha_Sem_Nome/README.md) e [Jam — PED-25](https://jam.dev/c/fb5673c9-3cd1-46c4-88f4-d5fb32574a8e) |
| RF150 | [CT-RF150](Cenario_Teste/CT-RF150_Cancelar_Cadastro_Modelo_Ficha.md) | Nenhum no fluxo avaliado | Aprovado conforme a gravação | [Evidências](Evidencias/CT-RF110_Cancelar_Cadastro_Modelo_Ficha/README.md) e [Jam — PED-26](https://jam.dev/c/a2a39e11-04f4-40aa-a97e-75a57a5f1b0f) |
| RF151 | [CT-RF151](Cenario_Teste/CT-RF151_Busca_Modelo_Ficha_Codigo_Inexistente.md) | Sem defeito confirmado | A validar — regra ou contexto pendente | [Evidências](Evidencias/CT-RF111_Busca_Modelo_Ficha_Codigo_Inexistente/README.md) e [Jam — PED-27](https://jam.dev/c/c1aecaa8-39c7-49b0-89af-9de47a68ba40) |
| RF152 | [CT-RF152](Cenario_Teste/CT-RF152_Busca_Modelo_Ficha_Titulo_Inexistente.md) | Sem defeito confirmado | A validar — regra ou contexto pendente | [Evidências](Evidencias/CT-RF112_Busca_Modelo_Ficha_Titulo_Inexistente/README.md) e [Jam — PED-28](https://jam.dev/c/0c385452-2aeb-427f-8159-79549fe7371d) |
| RF153 | [CT-RF153](Cenario_Teste/CT-RF153_Busca_Modelo_Ficha_Filtros_Combinados.md) | Sem defeito confirmado | A validar — regra ou contexto pendente | [Evidências](Evidencias/CT-RF113_Busca_Modelo_Ficha_Filtros_Combinados/README.md) e [Jam — PED-29](https://jam.dev/c/006f9722-e643-4b65-904a-25471a7b90ed) |
| RF154 | [CT-RF154](Cenario_Teste/CT-RF154_Limpeza_Filtros_Modelos_Ficha.md) | Nenhum no fluxo avaliado | Aprovado conforme a gravação | [Evidências](Evidencias/CT-RF114_Limpeza_Filtros_Modelos_Ficha/README.md) e [Jam — PED-30](https://jam.dev/c/297eec2b-7be4-498b-a0e6-e962ed93cc00) |
| RF155 | [CT-RF155](Cenario_Teste/CT-RF155_Nova_Busca_Modelos_Ficha_Sem_Filtros.md) | Sem defeito confirmado | A validar — regra ou contexto pendente | [Evidências](Evidencias/CT-RF115_Nova_Busca_Modelos_Ficha_Sem_Filtros/README.md) e [Jam — PED-30](https://jam.dev/c/297eec2b-7be4-498b-a0e6-e962ed93cc00) |
| RF156 | [CT-RF156](Cenario_Teste/CT-RF156_Cadastro_Modelo_Ficha_Erro_500.md) | [BUG-045](Relatorio-de-Bugs.md#bug-045), em triagem | Reprovado nas evidências | [Evidências](Evidencias/CT-RF121_Cadastro_Modelo_Ficha_Erro_500/README.md) e [Jam — PED-24 — Cadastro de modelo de ficha](https://jam.dev/c/04e2cae2-f3f2-43ff-8361-b3b9d9f50d35) |
| RF157 | [CT-RF157](Cenario_Teste/CT-RF157_Aplicativo_Consultar_Notificacao.md) | Nenhum no fluxo avaliado | Aprovado conforme a gravação | [Evidências](Evidencias/CT-RF157_Aplicativo_Consultar_Notificacao/README.md) e [Jam 1 — Consulta de notificação existente](https://jam.dev/c/32edc5de-4ad3-48ca-9e19-1db449bebcc5) |
| RF158 | [CT-RF158](Cenario_Teste/CT-RF158_Aplicativo_Bloquear_Notificacao_Vazia.md) | Nenhum no fluxo avaliado | Aprovado conforme a gravação | [Evidências](Evidencias/CT-RF158_Aplicativo_Bloquear_Notificacao_Vazia/README.md) e [Jam 2 — Validação de mensagem obrigatória](https://jam.dev/c/b9ebb9d0-e7c2-4ed8-a50d-00c2948e97fd) |
| RF159 | [CT-RF159](Cenario_Teste/CT-RF159_Aplicativo_Criar_Notificacao_Preview.md) | Nenhum no fluxo avaliado | Aprovado conforme a gravação | [Evidências](Evidencias/CT-RF159_Aplicativo_Criar_Notificacao_Preview/README.md) e [Jam 3 — Criação de notificação com prévia](https://jam.dev/c/6720f25a-45e9-4e8d-9c5f-c48b0bfec5c0) |
| RF160 | [CT-RF160](Cenario_Teste/CT-RF160_Aplicativo_Postagens_Filtros_Estados_Vazios.md) | Nenhum no fluxo avaliado | Aprovado conforme a gravação | [Evidências](Evidencias/CT-RF160_Aplicativo_Postagens_Filtros_Estados_Vazios/README.md) e [Jam 4 — Filtros e lista completa de postagens](https://jam.dev/c/a58327e6-6a5a-4a2e-8b3d-cee9296d1d03) |
| RF161 | [CT-RF161](Cenario_Teste/CT-RF161_Aplicativo_Denuncias_Filtros_Estados_Vazios.md) | Nenhum no fluxo avaliado | Aprovado conforme a gravação | [Evidências](Evidencias/CT-RF161_Aplicativo_Denuncias_Filtros_Estados_Vazios/README.md) e [Jam 5 — Filtros de denúncias sem registros](https://jam.dev/c/709cd210-f823-4348-805f-3cb61e7fb23f) |

---


## 🔎 Base da análise

- **Relato:** a opção "Esqueci minha senha" não funciona e não dispara requisição ao ser acionada.
- **Jam:** gravação criada em 23/10/2026, com 14 segundos, em https://sifitalfa.centrion.com.br/login; cliques repetidos, permanência na tela de login, 0 requisições registradas e 0 erros de console registrados.
- **Drive:** arquivo de vídeo identificado como `CT-RF04_Esqueci-senha`, mantido como evidência complementar; conteúdo não inspecionado nesta revisão.
- **Limite:** não houve inspeção do código da aplicação nem nova execução no sistema em 10/11/2026.

### Base da análise do RF05 — revisão de 12/11/2026

- **Relato:** perfil com dados fictícios, textos em inglês, campos não exibidos e rolagem horizontal.
- **Captura:** seções Usuário, Documentos e Endereço sem campos visíveis, imagem fora de proporção e textos em inglês.
- **HTML:** conteúdo de demonstração e tags de componentes preservadas no DOM; os trechos de cadastro não contêm elementos `<input>` internos. [Recorte preservado](Evidencias/CT-RF02_ERRO/recorte-dom.html).
- **Jam:** gravação de 22/10/2026 às 21:45 BRT, com aproximadamente 15 segundos; Info indica `/configuracoes`, enquanto Actions registra `/profile` em 00:02 e 00:12 no domínio `sifit.centrion.com.br`. Quadro em 00:05 consultado.
- **Limite:** hipótese de componentes não resolvidos requer inspeção do código. Não houve nova execução, reteste, diagnóstico de rede/console ou validação de salvamento nesta revisão. O ambiente do RF05 é distinto do domínio `sifitalfa.centrion.com.br` registrado no RF04.

### Base da análise do RF09 — revisão de 12/11/2026

- **Relato:** seleção de Ativo, Inadimplente, Plano Hendreu e Marcelo Longo Zandonadi sem restringir corretamente a listagem; alternar para Adimplente mantém resultados praticamente iguais.
- **Rede informada:** três chamadas a `POST https://backendsifit.centrion.com.br/api/clientesPorNome/1`, em aproximadamente 00:05, 00:20 e 00:28, com HTTP 200 e cerca de 180,9 KB por resposta. O corpo simplificado contém apenas `empresa_id: 1` e `nome: ""`, sem os outros quatro critérios; autenticação omitida.
- **Capturas:** mostram filtros selecionados com textos truncados e listagens semelhantes. A primeira mostra uma entrada XHR HTTP 200; a segunda não lista requisições naquele instante. Não permitem confirmar isoladamente os vínculos de cada cliente nem o corpo das chamadas.
- **Jam:** [link fornecido](https://jam.dev/c/657627ec-e7e2-455d-a505-9b2a26f44bf1), sem acesso direto pela ferramenta de consulta na revisão. Horários, endpoint, payload e volumes foram registrados conforme o relato. [Origem e limites das evidências](Evidencias/CT-RF03_Filtros_Clientes/README.md).
- **Limite:** código e contrato da API não analisados; causa não confirmada. Não houve nova execução ou reteste. URL do frontend, data da gravação e versão não confirmadas. As variações de Código, Nome e demais combinações são propostas de validação, sem resultado de execução nesta revisão.

---

### Base da análise do RF01 — revisão de 13/11/2026

- **Jam:** Login com sucesso, criado em 13/11/2026 por Leonardo Barbosa, com aproximadamente 12 segundos; metadados, cronologia e seis quadros consultados diretamente.
- **Ações e rede:** preenchimento de credenciais e clique em Entrar em aproximadamente 00:06; `POST /api/login` e `POST /api/verifica-token-logado` retornam HTTP 200, seguidos de navegação para `/dashboard`.
- **Visual:** menu e resumo da academia visíveis após o envio; cartões preenchidos nos quadros de aproximadamente 00:09 e 00:11.
- **Limite:** sem nova execução, inspeção do código ou validação de persistência da sessão e dos dados do painel. [Origem e cronologia](Evidencias/CT-RF04_loginComSucesso/README.md).

### Base da análise do RF02 ao RF39 — revisão de 14/11/2026

Foram incorporadas as 16 gravações do JAM.txt, na ordem definida pelo solicitante a partir de CT-RF02. A revisão anterior desta sessão consultou detalhes, cronologia e quadros de todas elas; os vídeos originais e seus resumos foram copiados com hash conferido para o repositório. O [índice de evidências](Evidencias/README.md) associa cada caso ao Jam, ao vídeo e aos metadados.

Os novos resultados são cinco aprovações, sete reprovações de manifestações observadas e quatro pontos a validar. As duas reprovações de contagem/filtro financeiro compartilham um defeito. Não houve nova execução, reteste ou análise do código da aplicação.

### Base da análise do RF10 — revisão de 15/11/2026

O relato original foi copiado integralmente. A consulta ao Jam confirmou os detalhes, a cronologia, o evento 16 (HTTP 500, 1363 ms, corpo “Erro interno inesperado.”) e os quadros do formulário em 00:12,479 e do alerta em 00:14,748. Foram preservados os dados de negócio sem autenticação. Não houve nova execução, acesso ao código/banco ou reteste. As referências históricas a evidências ausentes nesta cópia estão identificadas no índice de evidências.


### Base da análise do RF21 ao RF27 — revisão de 15/11/2026

RF21 utiliza relato, imagem inicial e Info do Jam. RF22–RF24 utilizam quadros, Info e listagem Network. RF25–RF27 utilizam quadros e Info dos Jams, sem confirmação de arquivo, MIME, persistência ou resposta detalhada da API. RF22 demonstra remoção e redução de 11 para 10; RF23 apresenta total de 10 para 11 no teste declarado como edição, exigindo confirmar operação e IDs; RF24 demonstra criação com imagem selecionada, sem conferir a imagem salva; RF25–RF27 demonstram ausência de feedback visual nos testes negativos. BUG-011–BUG-015 estão em triagem. Não houve revisão integral quadro a quadro, nova execução, reteste ou diagnóstico de causa raiz.

### Base da análise do RF08 — revisão de 15/11/2026

RF08 utiliza quadros, Info e a listagem Network do Jam. A evidência mostra 23 eventos visíveis, múltiplos HTTP 500 e um diálogo de erro, mas os endpoints aparecem truncados e não foram inspecionados corpos ou logs. BUG-018 permanece em triagem. Não houve nova execução, reteste ou diagnóstico de causa raiz.

### Base da análise do RF28 — revisão de 15/11/2026

RF28 utiliza os painéis Informações, Rede e Console do Jam "Tela de Grupos Musculares", lidos diretamente, e os quadros de 1:18 e 1:21. As duas requisições de exclusão, seus horários, tempos de resposta, cabeçalhos e corpo de resposta foram registrados a partir do painel de rede. Não houve nova execução, acesso ao código ou ao banco, nem reteste. BUG-016 está em triagem.

### Base da análise do RF29 — revisão de 15/11/2026

RF29 utiliza a lista de rede do Jam filtrada por erros, a cronologia do painel Console e os quadros de 0:20, 0:55, 1:18, 1:21, 1:45 e 2:00. Foram registrados os quatro arquivos requisitados, doze ocorrências de HTTP 422 entre 0:06 e 1:59 e três ocorrências de `net::ERR_ABORTED`. Os cabeçalhos de resposta das imagens não foram utilizados por inconsistência do painel de detalhe. Não houve verificação no servidor de arquivos, acesso ao banco, nova execução ou reteste. BUG-017 está em triagem.

### Base da análise do RF30 — revisão de 15/11/2026

RF30 utiliza a cronologia do painel Console entre 0:17 e 0:53 e os quadros de 0:20, 0:48 e 0:55. O quadro de 0:48 mostra o formulário no momento do envio, com o campo Código em branco e o campo Imagem em "Nenhum arquivo escolhido". A comparação com o quadro de 0:55 sustenta a criação do registro e a atualização dos cartões. Não houve nova execução, acesso ao código ou ao banco, nem reteste.

### Base da análise do RF31 — revisão de 15/11/2026

RF31 utiliza a cronologia do painel Console entre 0:57 e 1:38 e os quadros de 0:55, 1:02, 1:08, 1:45 e 2:00. O quadro de 1:02 mostra o formulário aberto em edição com os dados do registro de código 1; o de 1:08 mostra a listagem já com o novo tipo de membro e os cartões recalculados. As alterações posteriores a 1:08 não têm quadro de antes e depois individual e sustentam-se no quadro de 1:45 e nos cartões de 2:00. Não houve nova execução, acesso ao código ou ao banco, nem reteste.

### Base da análise do RF32 — revisão de 15/11/2026

RF32 utiliza a cronologia do painel Console e os quadros de 0:15, 1:45 e 2:00. O quadro de 0:15 registra o estado sem resultados; os de 1:45 e 2:00 registram buscas por tipo de membro e por código, com o rodapé correspondente. O resultado da busca pelo código "1", acionada entre 1:53 e 1:55, não teve quadro consultado e está registrado apenas como ação. Não houve nova execução, acesso ao código ou ao banco, nem reteste.

Com RF28 a RF08, a análise passa a cobrir 34 requisitos. A tela Grupos Musculares acrescenta duas reprovações, com BUG-016 e BUG-017 em triagem, e três aprovações limitadas aos exemplos gravados. O dashboard acrescenta uma reprovação vinculada ao BUG-018, também em triagem.

### Base da análise do RF33 — revisão de 15/11/2026

RF33 utiliza os painéis Info, Console (atividade do usuário e erros de rede), Network e Actions do Jam "Objetivos Treino", lidos diretamente, os cabeçalhos de resposta da última requisição de gravação e os quadros de 0:04, 0:21, 0:41, 0:46, 0:52, 0:58, 1:00, 1:04, 1:06 e 1:11. Foram registrados o endpoint, as duas ocorrências de HTTP 500, o preflight HTTP 204, os tempos e o texto do diálogo de erro; o corpo da requisição e da resposta aparece como indisponível no Jam. As capturas e a cronologia estão na [pasta local de evidências](Evidencias/CT-RF35_Cadastro_Objetivo_Treino/README.md). Não houve nova execução, acesso ao código ou ao banco, nem reteste. BUG-019 está em triagem.

Com RF33, a análise passa a cobrir 35 requisitos. A tela Objetivos Treino acrescenta uma reprovação, vinculada ao BUG-019, também em triagem.

### Base da análise do RF40 — revisão de 15/11/2026

RF40 utiliza os painéis Info, Console (atividade do usuário), Network e Actions do Jam "Categorias Crossfit", lidos diretamente, o corpo da requisição e da resposta de criação, os cabeçalhos de resposta e os quadros de 0:02, 0:08, 0:14, 0:27, 0:28, 0:32 e 0:36. Foram registrados o filtro por nome e por código, a tentativa de digitar no campo Código, a criação com HTTP 201, o código 9 atribuído e a localização do registro pelo filtro. As capturas e a cronologia estão na [pasta local de evidências](Evidencias/CT-RF38_Cadastro_Categoria_Codigo_Automatico/README.md). Não houve nova execução, acesso ao código ou ao banco, nem reteste.

Com RF40, a análise passa a cobrir 36 requisitos documentados (RF04–RF33 e RF40). A tela Categorias Crossfit acrescenta uma aprovação limitada aos exemplos gravados.

### Base da análise do RF44 — revisão de 15/11/2026

RF44 utiliza os painéis Info, Console (atividade do usuário), Network e Actions do Jam "SifitBox – Turmas", o corpo da requisição e da resposta de criação e os quadros de 1:17, 1:28 e 1:35. Foram registrados o `POST modalidades/salvar` com HTTP 201, a modalidade de id 4 e a atualização da listagem. As capturas e a cronologia estão na [pasta local de evidências](Evidencias/CT-RF39_Cadastro_Modalidade/README.md). Não houve nova execução, acesso ao código ou ao banco, nem reteste.

Com RF44, a análise passa a cobrir 37 requisitos documentados. A tela SifitBox – Turmas acrescenta uma aprovação limitada ao exemplo gravado.

### Base da análise do RF45 — revisão de 15/11/2026

RF45 utiliza os painéis Info, Console, Network e Actions do Jam "SifitBox – Turmas", os cabeçalhos e a resposta das exclusões, as listas retornadas (todas as turmas e modalidades com status "inativo") e os quadros de 1:00 e 1:05. Foram registrados quatro `POST turmas/excluir` e cinco `POST modalidades/excluir`, todos com HTTP 200. Não houve nova execução, acesso ao código ou ao banco, nem reteste. A regra permanece a confirmar.

Com RF45, a análise passa a cobrir 38 requisitos documentados. SifitBox – Turmas acrescenta um ponto a validar, sem defeito confirmado.

### Base da análise do RF46 — revisão de 15/11/2026

RF46 utiliza os painéis Info, Console (atividade do usuário), Network e Actions do Jam "SifitBox – Turmas", o corpo da requisição e da resposta de atualização e os quadros de 0:19, 0:58, 1:29, 1:33 e 1:35. Nas 35 entradas de rede não há requisição de criação de turma. A classificação não confirma que a modalidade seja obrigatória nem que a validação esteja ausente. Não houve nova execução, acesso ao código ou ao banco, nem reteste. BUG-020 está em triagem.

Com RF46, a análise passa a cobrir 39 requisitos documentados. SifitBox – Turmas acrescenta uma reprovação, vinculada ao BUG-020, em triagem.

### Base da análise do RF47 — revisão de 15/11/2026

RF47 utiliza os painéis Info, Console, Network e Actions do Jam "Pagar.me" e os quadros de 0:00, 0:04 e 0:05. Foram registrados a requisição de saque com HTTP 200 e a ausência de mensagem de resultado. Corpos de requisição e de resposta indisponíveis. Não houve nova execução, acesso ao código ou ao banco, nem reteste.

Com RF47, a análise passa a cobrir 40 requisitos documentados. O CT-RF47 acrescenta um ponto a validar, sem defeito confirmado.

### Base da análise do RF48 — revisão de 15/11/2026

RF48 utiliza os painéis Info, Console, Network e Actions do Jam "Pagar.me" e os quadros de 0:29 e 0:31. Foram registrados o formulário preenchido, a requisição de criação com HTTP 200 e a mensagem de sucesso. Corpos de requisição e de resposta indisponíveis. Não houve nova execução, acesso ao código ou ao banco, nem reteste.

Com RF48, a análise passa a cobrir 41 requisitos documentados. O CT-RF48 acrescenta uma aprovação limitada ao exemplo gravado.

### Base da análise do RF117 — revisão de 15/11/2026

RF117 utiliza os painéis Info, Console, Network e Actions do Jam "Pagar.me" (trecho de Configurações) e os quadros de 0:33, 0:41, 0:46 e 0:56. Foram registrados as alterações, o valor 1100 no campo de dias, a mudança do menu lateral e a ausência de mensagem de confirmação. Não houve nova execução, acesso ao código ou ao banco, nem reteste.

Com RF117, a análise passa a cobrir 42 requisitos documentados. O CT-RF117 acrescenta um ponto a validar, sem defeito confirmado.

### Base da análise do RF49 — revisão de 15/11/2026

RF49 utiliza os painéis Info, Console, Network e Actions do Jam "Pagar.me" e os quadros de 0:00 e 0:25. A comparação entre os dois quadros mostra o mesmo valor e o mesmo gráfico com períodos diferentes. A leitura do eixo de datas é aproximada. Não houve nova execução, acesso ao código ou ao banco, nem reteste. BUG-021 está em triagem.

Com RF49, a análise passa a cobrir 43 requisitos documentados. O CT-RF49 acrescenta uma reprovação, vinculada ao BUG-021, em triagem.

### Base da análise do RF50 — revisão de 15/11/2026

RF50 utiliza os painéis Info, Console, Network e Actions do Jam "Despesas Fixas" e os quadros de 0:03, 0:11, 0:19 e 0:42. Foram registrados os filtros por código e por nome, o cartão Valor Listado e a ausência de requisição nos filtros. Não houve nova execução, acesso ao código ou ao banco, nem reteste.

Com RF50, a análise passa a cobrir 44 requisitos documentados. O CT-RF50 acrescenta uma aprovação limitada ao exemplo gravado.

### Base da análise do RF51 — revisão de 15/11/2026

RF51 utiliza os painéis Info, Console, Network e Actions do Jam "Despesas Fixas", o corpo e a resposta da primeira requisição de criação e os quadros de 0:34, 0:36 e 0:42. Foram registrados duas requisições de criação com HTTP 201 e um único registro novo visível. A segunda requisição não teve corpo nem resposta capturados. Não houve nova execução, acesso ao código ou ao banco, nem reteste.

Com RF51, a análise passa a cobrir 45 requisitos documentados. O CT-RF51 acrescenta um ponto a validar, sem defeito confirmado.

### Base da análise do RF52 — revisão de 15/11/2026

RF52 utiliza os painéis Info, Console, Network e Actions do Jam "Despesas Fixas", o corpo e a resposta da exclusão e os quadros de 0:42, 0:44 e 0:51. Foram registrados o diálogo de confirmação, a requisição de exclusão com HTTP 200 e a atualização da listagem. Não houve nova execução, acesso ao código ou ao banco, nem reteste.

Com RF52, a análise passa a cobrir 46 requisitos documentados. O CT-RF52 acrescenta uma aprovação limitada ao exemplo gravado.

### Base da análise do RF53 — revisão de 15/11/2026

RF53 utiliza os painéis Info, Console, Network e Actions do Jam "Despesas Fixas", o corpo e a resposta de seleção e de edição e os quadros de 0:48 e 0:51. Foram registrados a requisição de edição com HTTP 200 e a nova recorrência na listagem. Não houve nova execução, acesso ao código ou ao banco, nem reteste.

Com RF53, a análise passa a cobrir 47 requisitos documentados. O CT-RF53 acrescenta uma aprovação limitada ao exemplo gravado.

### Base da análise do RF54 — revisão de 15/11/2026

RF54 utiliza os painéis Info, Console e Network do Jam "Relatórios", o quadro de 0:38 e o conteúdo do PDF baixado. O PDF foi identificado pelo conteúdo. Não houve nova execução, acesso ao código ou ao banco, nem reteste.

Com RF54, a análise passa a cobrir 48 requisitos documentados. O CT-RF54 acrescenta uma aprovação limitada ao exemplo gravado.

### Base da análise do RF55 — revisão de 15/11/2026

RF55 utiliza os painéis Info, Console e Network do Jam "Relatórios", o quadro de 0:43 e o conteúdo do PDF baixado, com três contas e o valor a receber ausente. Não houve nova execução, acesso ao código ou ao banco, nem reteste. BUG-022 está em triagem.

Com RF55, a análise passa a cobrir 49 requisitos documentados. O CT-RF55 acrescenta uma reprovação, vinculada ao BUG-022, em triagem.

### Base da análise do RF56 — revisão de 15/11/2026

RF56 utiliza os painéis Info, Console e Network do Jam "Relatórios", o quadro de 0:48 e o conteúdo do PDF baixado, sem linhas e com totalizadores zerados. Não houve nova execução, acesso ao código ou ao banco, nem reteste.

Com RF56, a análise passa a cobrir 50 requisitos documentados. O CT-RF56 acrescenta um ponto a validar, sem defeito confirmado.

### Base da análise do RF57 — revisão de 15/11/2026

RF57 utiliza os painéis Info, Console e Network do Jam "Relatórios", os quadros do vídeo e os arquivos baixados (tamanho zero e carimbos de hora). A atividade do usuário não foi registrada no Console do Jam. A correspondência do arquivo com o tipo é inferida. Não houve nova execução, acesso ao código ou ao banco, nem reteste. BUG-023 está em triagem.

Com RF57, a análise passa a cobrir 51 requisitos documentados. O CT-RF57 acrescenta uma reprovação, vinculada ao BUG-023, em triagem.

### Base da análise do RF58 — revisão de 15/11/2026

RF58 utiliza os painéis Info, Console e Network do Jam "Relatórios", os quadros do vídeo e os arquivos baixados (tamanho zero e carimbos de hora). A atividade do usuário não foi registrada no Console do Jam. A correspondência do arquivo com o tipo é inferida. Não houve nova execução, acesso ao código ou ao banco, nem reteste. BUG-023 está em triagem.

Com RF58, a análise passa a cobrir 52 requisitos documentados. O CT-RF58 acrescenta uma reprovação, vinculada ao BUG-023, em triagem.

### Base da análise do RF59 — revisão de 15/11/2026

RF59 utiliza os painéis Info, Console e Network do Jam "Relatórios", os quadros do vídeo e os arquivos baixados (tamanho zero e carimbos de hora). A atividade do usuário não foi registrada no Console do Jam. A correspondência do arquivo com o tipo é inferida. Não houve nova execução, acesso ao código ou ao banco, nem reteste. BUG-023 está em triagem.

Com RF59, a análise passa a cobrir 53 requisitos documentados. O CT-RF59 acrescenta uma reprovação, vinculada ao BUG-023, em triagem.

### Base da análise do RF60 — revisão de 15/11/2026

RF60 utiliza os painéis Info, Console e Network do Jam "Relatórios", os quadros do vídeo e os arquivos baixados (tamanho zero e carimbos de hora). A atividade do usuário não foi registrada no Console do Jam. A correspondência do arquivo com o tipo é inferida. Não houve nova execução, acesso ao código ou ao banco, nem reteste. BUG-023 está em triagem.

Com RF60, a análise passa a cobrir 54 requisitos documentados. O CT-RF60 acrescenta uma reprovação, vinculada ao BUG-023, em triagem.

### Base da análise do RF34 — revisão de 15/11/2026

RF34 utiliza os painéis Informações, Console e Rede do Jam "Tela de Grupos", os quadros do vídeo entre 0:00 e 1:38 e as duas requisições de exclusão com HTTP 500. Não houve nova execução, acesso ao código ou ao banco, nem reteste.

Com RF34, a análise passa a cobrir 55 requisitos documentados. O CT-RF34 acrescenta uma reprovação, vinculada ao BUG-024, em triagem.

### Base da análise do RF35 — revisão de 15/11/2026

RF35 utiliza os painéis Informações, Console e Rede do mesmo Jam "Tela de Grupos" do RF34, os eventos de clique entre 0:57 e 1:16 e as requisições `POST /api/edita/grupo/1`, `GET /api/grupos/1` e `POST /api/seleciona/grupo/1` correspondentes às duas edições do grupo "Treino sla" (código 11). Foram registrados os corpos de requisição e resposta das duas edições e das consultas imediatamente seguintes. Não houve nova execução, acesso ao código ou ao banco, nem reteste.

Com RF35, a análise passa a cobrir 56 requisitos documentados. O CT-RF35 acrescenta uma reprovação, vinculada ao BUG-025, em triagem.

### Base da análise do RF100 — revisão de 15/11/2026

RF100 utiliza os painéis Informações, Console e Rede do Jam "Fichas de Anamnese", os eventos de clique e digitação entre 0:00 e 1:28 e as sete requisições com HTTP 500 (quatro em `POST /api/anamnese/aplicar/1` e três em `POST /api/anamnese/rascunho/1`), registradas com dois modelos de anamnese e três respostas distintas. Foram registrados os corpos de requisição e resposta de duas dessas tentativas, representativas das demais. Não houve nova execução, acesso a logs, ao código ou ao banco, nem reteste.

Com RF100, a análise passava a cobrir 57 requisitos documentados (antes da inclusão de RF101 e da integração de RF91 a RF96). O CT-RF100 acrescenta uma reprovação, vinculada ao BUG-032, em triagem.

### Base da análise do RF62 — revisão de 15/11/2026

RF62 utiliza os painéis Info, Console, Network e Actions do Jam "Prospecção" e os quadros de 0:01 e 0:03. Foram registrados a troca de tema, os POST usuario/tema e o painel de Notificações. Não houve nova execução, acesso ao código ou ao banco, nem reteste.

Com RF62, a análise passa a cobrir 55 requisitos documentados. O CT-RF62 acrescenta uma aprovação limitada ao exemplo gravado.

### Base da análise do RF63 — revisão de 15/11/2026

RF63 utiliza os painéis Info, Console, Network e Actions do Jam "Prospecção" e os quadros de 0:12, 0:13 e 0:44. Foram registrados a busca por texto, os cartões e a ausência de requisição na busca. Não houve nova execução, acesso ao código ou ao banco, nem reteste.

Com RF63, a análise passa a cobrir 56 requisitos documentados. O CT-RF63 acrescenta uma aprovação limitada ao exemplo gravado.

### Base da análise do RF64 — revisão de 15/11/2026

RF64 utiliza os painéis Info, Console, Network e Actions do Jam "Prospecção" e os quadros de 0:16, 0:19 e 0:21. Foram registrados o filtro por estágio, o indicador Novos Contatos, o botão Limpar e a ausência de requisição. Não houve nova execução, acesso ao código ou ao banco, nem reteste.

Com RF64, a análise passa a cobrir 57 requisitos documentados. O CT-RF64 acrescenta uma aprovação limitada ao exemplo gravado.

### Base da análise do RF71 — revisão de 15/11/2026

RF71 utiliza os painéis Info, Console, Network e Actions do Jam "Prospecção", os corpos da primeira requisição e os quadros de 0:24 e 0:39. Foram registrados o cadastro, os dois POST de criação e a atualização dos cartões. Não houve nova execução, acesso ao código ou ao banco, nem reteste.

Com RF71, a análise passa a cobrir 58 requisitos documentados. O CT-RF71 acrescenta um ponto a validar, sem defeito confirmado.

### Base da análise do RF72 — revisão de 15/11/2026

RF72 utiliza os painéis Info, Console, Network e Actions do Jam "Prospecção", o corpo do salvar-lead, a resposta do buscar-lead e os quadros de 0:47. Foram registrados o telefone de 30 dígitos, a ausência de validação e a gravação do valor. Não houve nova execução, acesso ao código ou ao banco, nem reteste.

Com RF72, a análise passa a cobrir 59 requisitos documentados. O CT-RF72 acrescenta uma reprovação, vinculada ao BUG-038, em triagem.

### Base da análise do RF75 — revisão de 15/11/2026

RF75 utiliza os painéis Info, Console, Network e Actions do Jam "Prospecção", os corpos de buscar-lead e atualizar-lead e os quadros de 0:47, 0:57 e 1:01. Foram registrados a abertura do lead, a atualização do nome e a listagem atualizada. Não houve nova execução, acesso ao código ou ao banco, nem reteste.

Com RF75, a análise passa a cobrir 60 requisitos documentados. O CT-RF75 acrescenta uma aprovação limitada ao exemplo gravado.

### Base da análise do RF16 — revisão de 15/11/2026

RF16 utiliza os painéis Info, Console, Network e Actions do Jam "Contas a Pagar" e os quadros de 0:03 e 0:12. Foram registrados os filtros por nome, tipo de data, período e status e o resultado vazio. Não houve nova execução, acesso ao código ou ao banco, nem reteste.

Com RF16, a análise passa a cobrir 61 requisitos documentados. O CT-RF16 acrescenta um ponto a validar, sem defeito confirmado.

### Base da análise do RF17 — revisão de 15/11/2026

RF17 utiliza os painéis Info, Console, Network e Actions do Jam "Contas a Pagar", o corpo e a resposta da criação e os quadros de 0:15, 0:41 e 0:50. Foram registrados o cadastro sem colaborador, o HTTP 201 e a listagem com "-". Não houve nova execução, acesso ao código ou ao banco, nem reteste.

Com RF17, a análise passa a cobrir 62 requisitos documentados. O CT-RF17 acrescenta uma reprovação, vinculada ao BUG-039, em triagem.

### Base da análise do RF18 — revisão de 15/11/2026

RF18 utiliza os painéis Info, Console, Network e Actions do Jam "Contas a Pagar" e o quadro de 0:26. Foram registrados a abertura do modal, a busca sem resultado e a resposta de 2 B. Não houve nova execução, acesso ao código ou ao banco, nem reteste.

Com RF18, a análise passa a cobrir 63 requisitos documentados. O CT-RF18 acrescenta um ponto a validar, sem defeito confirmado.

### Base da análise do RF19 — revisão de 15/11/2026

RF19 utiliza os painéis Info, Console, Network e Actions do Jam "Contas a Pagar" e o quadro de 0:52. Foram registrados a abertura do modal e os dados apresentados. Não houve nova execução, acesso ao código ou ao banco, nem reteste.

Com RF19, a análise passa a cobrir 64 requisitos documentados. O CT-RF19 acrescenta uma aprovação limitada ao exemplo gravado.

### Base da análise do RF20 — revisão de 15/11/2026

RF20 utiliza os painéis Info, Console, Network e Actions do Jam "Contas a Pagar", o corpo e a resposta da exclusão e os quadros de 0:54 e 0:59. Foram registrados o diálogo, a exclusão e a listagem. Não houve nova execução, acesso ao código ou ao banco, nem reteste.

Com RF20, a análise passa a cobrir 65 requisitos documentados. O CT-RF20 acrescenta uma aprovação limitada ao exemplo gravado.

### Base da análise do RF82 — revisão de 15/11/2026

RF82 utiliza os painéis Info, Console, Network e Actions do Jam "Modelos de Contrato" e os quadros de 0:09, 0:21, 0:33 e 0:36. Foram registrados a inserção das variáveis e a pré-visualização. Não houve nova execução, acesso ao código ou ao banco, nem reteste.

Com RF82, a análise passa a cobrir 66 requisitos documentados. O CT-RF82 acrescenta uma aprovação limitada ao exemplo gravado.

### Base da análise do RF81 — revisão de 15/11/2026

RF81 utiliza os painéis Info, Console, Network e Actions do Jam "Modelos de Contrato" e a resposta da lista de modelos. Foram registrados a criação (HTTP 201) e o modelo de id 15 na lista do servidor. Não houve nova execução, acesso ao código ou ao banco, nem reteste.

Com RF81, a análise passa a cobrir 67 requisitos documentados. O CT-RF81 acrescenta uma aprovação limitada ao exemplo gravado.

### Base da análise do RF83 — revisão de 15/11/2026

RF83 utiliza os painéis Info, Console, Network e Actions do Jam "Modelos de Contrato", a resposta de modelos-contrato e os quadros de 0:00, 0:39, 0:45 e 0:49. Foram registrados a lista de 15 modelos e a tabela sem linhas. Não houve nova execução, acesso ao código ou ao banco, nem reteste.

Com RF83, a análise passa a cobrir 68 requisitos documentados. O CT-RF83 acrescenta uma reprovação, vinculada ao BUG-040, em triagem.

### Base da análise do RF77 — revisão de 15/11/2026

RF77 utiliza os painéis Info, Console, Network e Actions do Jam "Planos" e os quadros de 0:03, 0:06 e 0:13. Foram registrados os filtros por código e nome e o botão Buscar. Não houve nova execução, acesso ao código ou ao banco, nem reteste.

Com RF77, a análise passa a cobrir 69 requisitos documentados. O CT-RF77 acrescenta uma aprovação limitada ao exemplo gravado.

### Base da análise do RF76 — revisão de 15/11/2026

RF76 utiliza os painéis Info, Console, Network e Actions do Jam "Planos" e os quadros de 0:16 e 0:19. Foram registrados a troca de tema, os POST usuario/tema e o painel de Notificações. Não houve nova execução, acesso ao código ou ao banco, nem reteste.

Com RF76, a análise passa a cobrir 70 requisitos documentados. O CT-RF76 acrescenta uma aprovação limitada ao exemplo gravado.

### Base da análise do RF78 — revisão de 15/11/2026

RF78 utiliza os painéis Info, Console, Network e Actions do Jam "Planos", o corpo e a resposta da criação e os quadros de 0:24, 0:46 e 0:53. Foram registrados o cadastro e o contador de planos. Não houve nova execução, acesso ao código ou ao banco, nem reteste.

Com RF78, a análise passa a cobrir 71 requisitos documentados. O CT-RF78 acrescenta uma aprovação limitada ao exemplo gravado.

### Base da análise do RF79 — revisão de 15/11/2026

RF79 utiliza os painéis Info, Console, Network e Actions do Jam "Planos", os corpos das requisições de criação e atualização e os quadros de 0:03, 0:53 e 1:08. Foram registrados os cartões Planos e Ativos e o status dos planos nas requisições. Não houve nova execução, acesso ao código ou ao banco, nem reteste.

Com RF79, a análise passa a cobrir 72 requisitos documentados. O CT-RF79 acrescenta uma reprovação, vinculada ao BUG-041, em triagem.

### Base da análise do RF80 — revisão de 15/11/2026

RF80 utiliza os painéis Info, Console, Network e Actions do Jam "Planos", os corpos das requisições e respostas de seleção e atualização e o quadro de 1:02. Foram registrados a abertura do plano e a atualização. Não houve nova execução, acesso ao código ou ao banco, nem reteste.

Com RF80, a análise passa a cobrir 73 requisitos documentados. O CT-RF80 acrescenta uma aprovação limitada ao exemplo gravado.

### Base da análise do RF84 — revisão de 16/11/2026

RF84 utiliza os painéis Info, Console, Network e Actions do Jam "Tipos de Pagamento" e os quadros de 0:00 e 0:14. Foram registrados o preenchimento do nome, o acionamento dos seletores e de Buscar e a ausência de requisição de listagem. Não houve nova execução, acesso ao código ou ao banco, nem reteste.

Com RF84, a análise passa a cobrir 97 requisitos documentados. O CT-RF84 acrescenta um ponto a validar, sem defeito confirmado.

### Base da análise do RF85 — revisão de 16/11/2026

RF85 utiliza os painéis Info, Console, Network e Actions do Jam "Tipos de Pagamento", o corpo e a resposta da criação, a resposta da lista e os quadros de 0:00, 0:19, 0:24 e 0:27. Foram registrados o cadastro com HTTP 201, a ausência de status no corpo e na resposta e os cartões. Não houve nova execução, acesso ao código ou ao banco, nem reteste.

Com RF85, a análise passa a cobrir 98 requisitos documentados. O CT-RF85 acrescenta uma reprovação, vinculada ao BUG-042, em triagem.

### Base da análise do RF86 — revisão de 16/11/2026

RF86 utiliza os painéis Info, Console, Network e Actions do Jam "Tipos de Pagamento", o corpo e a resposta da seleção e da edição e os quadros de 0:34 e 0:45. Foram registrados a abertura do tipo, a edição e a atualização da listagem. Não houve nova execução, acesso ao código ou ao banco, nem reteste.

Com RF86, a análise passa a cobrir 99 requisitos documentados. O CT-RF86 acrescenta uma aprovação limitada ao exemplo gravado.

### Base da análise do RF87 — revisão de 16/11/2026

RF87 utiliza os painéis Info, Console, Network e Actions do Jam "Tipos de Pagamento", os corpos e as respostas das duas exclusões e os quadros de 0:37, 0:40, 0:43 e 0:45. Foram registrados o HTTP 404, o erro de integridade referencial e a mensagem genérica da tela. Não houve nova execução, acesso ao código ou ao banco, nem reteste.

Com RF87, a análise passa a cobrir 100 requisitos documentados. O CT-RF87 acrescenta uma reprovação, vinculada ao BUG-043, em triagem.

### Base da análise do RF88 — revisão de 16/11/2026

RF88 utiliza os painéis Info, Console, Network e Actions do Jam "Tipos de Pagamento" e os quadros de 0:41, 0:45, 0:50 e 0:57. Foram registrados a alternância de tema e o painel de notificações. Não houve nova execução, acesso ao código ou ao banco, nem reteste.

Com RF88, a análise passa a cobrir 101 requisitos documentados. O CT-RF88 acrescenta uma aprovação limitada ao exemplo gravado.

### Base da análise de Modelos de Ficha — revisão de 17/11/2026

A revisão de Modelos de Ficha inclui CT-RF149–CT-RF155 com base em 6 gravações do Jam de 16/11/2026. A revisão documental foi feita em 17/11/2026. Os resultados se baseiam nos vídeos, metadados e eventos capturados pelo Jam.

- RF149: Aviso “Informe o nome do modelo.”. Modal permaneceu aberto após Entendi, sem requisição capturada. [Jam — PED-25](https://jam.dev/c/fb5673c9-3cd1-46c4-88f4-d5fb32574a8e).
- RF150: Cancelar fechou o modal preenchido e manteve 0 registros, sem requisição capturada. [Jam — PED-26](https://jam.dev/c/a2a39e11-04f4-40aa-a97e-75a57a5f1b0f).
- RF151: Busca por 989898 exibiu estado vazio. GET retornou HTTP 200 com `[]`. [Jam — PED-27](https://jam.dev/c/c1aecaa8-39c7-49b0-89af-9de47a68ba40).
- RF152: Título PEDRO-01 exibiu carregamento e estado vazio. GET retornou HTTP 200 com `[]`. [Jam — PED-28](https://jam.dev/c/0c385452-2aeb-427f-8159-79549fe7371d).
- RF153: Três filtros preenchidos, 0 registros. GET sem parâmetros na URL retornou HTTP 200 com `[]`. [Jam — PED-29](https://jam.dev/c/006f9722-e643-4b65-904a-25471a7b90ed).
- RF154: Criador, Título e Código foram limpos manualmente e Buscar permaneceu disponível. [Jam — PED-30](https://jam.dev/c/297eec2b-7be4-498b-a0e6-e962ed93cc00).
- RF155: Dois cliques em Buscar com campos vazios geraram HTTP 200 com `[]`. A lista permaneceu vazia. [Jam — PED-30](https://jam.dev/c/297eec2b-7be4-498b-a0e6-e962ed93cc00).

### Base da análise de Configurações e Modelos de Ficha — revisão de 17/11/2026

CT-RF118–CT-RF156 amplia a cobertura de Configurações e Modelos de Ficha com gravações de 16/11/2026 entre 22:03:53 e 22:18:52 BRT.

- RF118: Campo vazio convertido em 0, com HTTP 200. A recarga e a consulta confirmaram 0. [Jam — PED-20 — Dias de ausência vazio](https://jam.dev/c/4e96d4fa-65b5-459b-a795-854496e5753c).
- RF122: Cancelar levou à Página Inicial. O GET ao reabrir Configurações confirmou o valor original 1100. [Jam — PED-20 — Cancelar alteração](https://jam.dev/c/e8faa199-1177-4563-8b00-590606669a1d).
- RF123: Sim → Não → Sim. Os dois POST e os GET após recarga confirmaram os valores de `usa_turmas`. [Jam — PED-21 — Trabalha com turmas](https://jam.dev/c/a51c33a5-537a-40fd-a55d-990b70ac0696).
- RF124: Não → Sim → Não. Seletor, cartão SifitBox e menu Principal acompanharam o estado após recarga. [Jam — PED-22 — Academia marcada como Box](https://jam.dev/c/16dc862d-c3f9-4392-9037-526818e86cd6).
- RF125: Não → Sim → Não. A API, o seletor e o cartão Desktop refletiram o valor salvo nas duas recargas. [Jam — PED-23 — Acesso desktop](https://jam.dev/c/466be253-ad9a-4856-b567-fb17e1fdd479).
- RF156: Cadastro preenchido retornou HTTP 500. A interface exibiu “Erro ao salvar modelo.” [Jam — PED-24 — Cadastro de modelo de ficha](https://jam.dev/c/04e2cae2-f3f2-43ff-8361-b3b9d9f50d35).

### Base da análise de Inteligência e Configurações — revisão de 17/11/2026

CT-RF116–CT-RF121 cobre Inteligência e Configurações com gravações de 16/11/2026 entre 21:50:51 e 22:02:16 BRT.

- RF116: Cartões e linha do tempo acompanharam a troca de 7, 30 e 90 dias. Os resultados de 90 dias se repetiram. [Jam — PED-12 — Últimos 90 dias](https://jam.dev/c/1728cfc2-1d36-4ea4-ab68-68a84458c359).
- RF108: A Central passou a mostrar 00:55. A linha do tempo de Hoje e o resumo de Resultados IA incluíram essa execução. [Jam — PED-14 — Execução de Risco de Evasão](https://jam.dev/c/efe26a44-458a-4802-bd48-8e23c5ac5fd9).
- RF126: A navegação funcionou. A aba Biometria exibiu o valor do campo Senha sem mascaramento. [Jam — PED-15](https://jam.dev/c/38105352-c89c-492e-bca1-78e2f4017ae2).
- RF119: 15 foi salvo e confirmado após recarga. A segunda recarga confirmou a restauração de 1100. [Jam — PED-16 — Salvar dias de ausência](https://jam.dev/c/12d6bba7-a67e-4882-86a5-4dd08d194af2).
- RF120: -1 foi aceito com HTTP 200 e confirmado na interface e no GET após recarga. [Jam — PED-17 — Dias de ausência negativos](https://jam.dev/c/d5786f67-6e5f-44f5-bbba-fbd763a88740).
- RF121: Letras não apareceram no campo. O salvamento com campo vazio enviou 0 e retornou HTTP 200. [Jam — PED-18 — Dias de ausência com texto](https://jam.dev/c/c578ed7a-c11c-4cef-8a6c-84d0244f21a5).

### Base da análise de Inteligência e Automação — revisão de 17/11/2026

CT-RF104–CT-RF115 cobre Inteligência e Automação com gravações de 16/11/2026 entre 21:40:31 e 21:49:48 BRT.

- RF104: Configurar abriu Risco de Evasão e Cancelar fechou o painel. O cartão continuou ativo. [Jam — PED-06 — Configuração de Risco de Evasão](https://jam.dev/c/d49b8ffc-a6e2-4e37-a618-c280b5e807db).
- RF109: O painel Aniversariantes abriu corretamente, mas a prévia exibiu dados de risco de evasão. [Jam — PED-07 — Configuração de Aniversariantes](https://jam.dev/c/c66d4d01-aee2-4037-a8fd-858da21a0a14).
- RF111: Os quatro recursos exibiram Em desenvolvimento. Os cliques não iniciaram navegação, configuração ou execução. [Jam — PED-08 — Recursos em desenvolvimento](https://jam.dev/c/0a7ae8fb-980d-4df2-8ef8-de78d6b11b8f).
- RF113: Hoje consultou um dia e o total de aniversariantes passou de 2 para 0, como na resposta. [Jam — PED-09 — Hoje](https://jam.dev/c/a83c4c74-0b8e-4242-9612-0202c9063d56).
- RF114: Ao voltar de Hoje para Últimos 7 dias, o cartão Aniversariantes passou de 0 para 2. [Jam — PED-10 — Últimos 7 dias](https://jam.dev/c/cbf45b87-b7b6-4314-a359-c5e706aa755e).
- RF115: O filtro de 30 dias apresentou 12 automações, 12 relatórios e 6 aniversariantes nas duas seleções. [Jam — PED-11 — Últimos 30 dias](https://jam.dev/c/2756d5c1-a823-482b-bf8d-878357b8b087).

### Base da análise de Inteligência e Automação / Central de Automações — revisão de 17/11/2026

CT-RF112–CT-RF106 cobrem a Central de Automações com gravações de 16/11/2026 entre 21:25:26 e 21:38:29 BRT.

- RF112: Quatro cliques atualizaram resumo, execuções e cartões com HTTP 200. Os valores permaneceram consistentes na base gravada. [Jam — PED-01 — Atualizar Central de Automações](https://jam.dev/c/efe35b08-8733-434c-a6fa-32c45e248ae1).
- RF107: A desativação persistiu. Após reativar Risco de Evasão, o cartão ficou ativo e o contador continuou em zero. [Jam — PED-02 — Desativar Risco de Evasão](https://jam.dev/c/b63ec55f-f8b6-41aa-af4c-d4cdd4515de8).
- RF110: A ativação persistiu. O resumo ficou em uma automação ativa até Atualizar, quando passou a duas. [Jam — PED-03 — Ativar Aniversariantes](https://jam.dev/c/60c724da-6760-4238-91f5-2ddad8f42bb3).
- RF105: Executar agora terminou com sucesso. O relatório e a nova execução ficaram disponíveis na Central. [Jam — PED-04 — Executar Risco de Evasão](https://jam.dev/c/be5418c7-8d87-4b6c-9c64-a9b33b5f7da6).
- RF106: Ver resultados abriu o relatório existente com a mesma distribuição retornada pela API: 0 alto, 23 médio e 0 baixo. [Jam — PED-05 — Ver resultados de Risco de Evasão](https://jam.dev/c/ac5bce26-f4a8-401b-bb23-d09d5253751a).

### Base da análise de Configurações / Integrações / WhatsApp — revisão de 17/11/2026

CT-RF127–CT-RF132 cobrem a integração do WhatsApp com gravações de 16/11/2026 entre 23:37:22 e 23:45:52 BRT.

- RF127: A API Key permaneceu mascarada na edição e na reabertura da aba. A gravação não registrou POST de salvamento. [Jam 1 — Mascaramento da API Key](https://jam.dev/c/ef0b67d5-1eea-49b7-84ea-bb306143df4a).
- RF128: A tentativa com URL fora do formato também tinha a instância vazia. Houve reconsulta sem POST de configuração, e a regra da URL ficou a validar. [Jam 2 — Validação da URL da API](https://jam.dev/c/0d7c7274-c798-4e26-91a3-f8162b7ce932).
- RF129: O nome preenchido foi salvo. As tentativas com a instância vazia ficaram sem POST e o valor anterior voltou ao reabrir. [Jam 3 — Obrigatoriedade do Nome da Instância](https://jam.dev/c/8bb7f049-0299-49c9-9fb5-ff7b144f58d2).
- RF130: Os dois estados de Ativo foram salvos e confirmados por GET, com a conexão permanecendo desconectada. [Jam 4 — Persistência da opção Ativo](https://jam.dev/c/593bb290-936a-4e01-a5af-cc8041c4eb55).
- RF131: As duas tentativas exibiram falha. A resposta trouxe a mesma falha, mas devolveu `verifica_erro: false`. [Jam 5 — Tentativas de conexão pela Evolution API](https://jam.dev/c/087b5e4f-7d73-4be3-979d-9a39f474b836).
- RF132: Sete consultas retornaram HTTP 200 com o estado desconectado e o horário de verificação atualizado. [Jam 6 — Atualização manual de status](https://jam.dev/c/0da79ab0-b557-46af-a48c-60c1a8a62628).

### Base da análise de Configurações — revisão de 17/11/2026

CT-RF134–CT-RF133 cobrem funcionalidades de Configurações com gravações de 16/11/2026 entre 23:21:59 e 23:36:13 BRT.

- RF134: WhatsApp e SMS e os dois textos de teste reapareceram após recarregar e reabrir Aniversário. [Jam 1 — Mensagens de aniversário por WhatsApp e SMS](https://jam.dev/c/01502381-e54a-40c9-b65b-e87c7f049154).
- RF138: A resposta e a tela confirmaram Não após recarregar. O salvamento de restauração para Sim retornou sucesso. [Jam 2 — Desativação do Pagamento Online](https://jam.dev/c/845de9b6-12f7-4002-a8ba-82e1a85affba).
- RF139: O código #663399 persistiu e a aba Design exibiu o valor com a amostra correspondente. [Jam 3 — Persistência da Cor Principal](https://jam.dev/c/c4f77e18-3b66-4c68-97e7-bd70a9bb70f9).
- RF140: As duas tentativas com #ZZZZZZ retornaram sucesso. O código fora do conjunto hexadecimal persistiu após recarregar. [Jam 4 — Validação da Cor Secundária](https://jam.dev/c/41aaf50a-2506-471a-8eeb-943674571771).
- RF141: A API rejeitou pelo limite de 6 MB. A interface exibiu apenas a mensagem genérica de erro ao salvar. [Jam 5 — Rejeição de logo pelo limite de tamanho](https://jam.dev/c/7aaeac50-8269-4cd6-b7f6-4c8c3740b0e5).
- RF133: A API manteve o estado conectando, e a tela continuou em Aguardando QR Code com a verificação atualizada de 02:32 para 02:35. [Jam 6 — Atualização de status enquanto aguarda QR Code](https://jam.dev/c/7a892fd3-b6b0-49bc-a463-1b79c4b6ad50).

### Base da análise de Configurações / Avaliação e Aniversário — revisão de 18/11/2026

CT-RF142–CT-RF137 cobrem as abas Avaliação e Aniversário com gravações de 16/11/2026 entre 23:10:04 e 23:20:07 BRT.

- RF142: A consulta e a aba Avaliação confirmaram Não após recarregar. [Jam 1 — Desativação da cobrança da avaliação](https://jam.dev/c/851c15d8-4076-4493-ad3f-c2ba0316d0ca).
- RF143: A consulta e a aba Avaliação confirmaram Bioimpedância após recarregar. O cartão de resumo Avaliação também exibiu Bioimpedância. [Jam 2 — Alteração do tipo para Bioimpedância](https://jam.dev/c/8685a48a-ed9a-4169-a825-90036265b185).
- RF144: A consulta e a aba Avaliação confirmaram Sim após recarregar. [Jam 3 — Habilitação de Teste Físico](https://jam.dev/c/86466f6e-b180-439f-ab1d-dde2484595a3).
- RF135: A consulta e a aba Aniversário confirmaram Desabilitado após recarregar. [Jam 4 — Desativação do envio automático de aniversário](https://jam.dev/c/ee8a2ba9-164c-42bb-8efe-927dd6c534d5).
- RF136: Cancelar retornou à Página Inicial e preservou a seleção do canal e a mensagem anterior. [Jam 5 — Cancelamento da edição da mensagem de WhatsApp](https://jam.dev/c/a58b851c-77c2-4a49-be3b-8a5c007d2bcb).
- RF137: As quatro variáveis apareceram no editor na ordem selecionada. Ao cancelar, a mensagem anterior foi preservada. [Jam 6 — Inserção de variáveis na mensagem de WhatsApp](https://jam.dev/c/fb2c4949-c68d-4f90-b47c-44da9dbe58a3).

### Base da análise de Aplicativo e Configurações / Biometria — revisão de 18/11/2026

CT-RF157–CT-RF148 cobrem Aplicativo e a aba Biometria com gravações de 16/11/2026 entre 22:39:05 e 23:07:08 BRT.

- RF157: O diálogo exibiu a notificação selecionada e sua prévia. Fechar retornou à listagem. [Jam 1 — Consulta de notificação existente](https://jam.dev/c/32edc5de-4ad3-48ca-9e19-1db449bebcc5).
- RF158: Sem texto, Enviar aviso ficou desabilitado e a captura não registrou uma criação. [Jam 2 — Validação de mensagem obrigatória](https://jam.dev/c/b9ebb9d0-e7c2-4ed8-a50d-00c2948e97fd).
- RF159: A prévia refletiu o texto e a criação retornou HTTP 201. A nova notificação apareceu na lista. [Jam 3 — Criação de notificação com prévia](https://jam.dev/c/6720f25a-45e9-4e8d-9c5f-c48b0bfec5c0).
- RF160: O painel e o diálogo alternaram corretamente os avisos para todas e pendentes na base vazia. [Jam 4 — Filtros e lista completa de postagens](https://jam.dev/c/a58327e6-6a5a-4a2e-8b3d-cee9296d1d03).
- RF161: A lista vazia apresentou a mensagem correspondente em todas as alternâncias entre todas e pendentes. [Jam 5 — Filtros de denúncias sem registros](https://jam.dev/c/709cd210-f823-4348-805f-3cb61e7fb23f).
- RF145: A edição foi descartada e a tela retornou à Página Inicial sem POST de configuração. [Jam 6 — Cancelamento da edição no formulário de Biometria](https://jam.dev/c/ccac55df-d2c8-4b11-898b-d12d87aced72).
- RF146: Um valor sem formato de IP foi salvo e apareceu na consulta e no campo após recarregar. [Jam 7 — Validação de IP do aparelho](https://jam.dev/c/5b8eea1f-3c87-4497-8fb1-da49f09f9854).
- RF147: A porta alterada no POST foi confirmada no GET após recarga. A restauração retornou sucesso. [Jam 8 — Persistência da porta do aparelho](https://jam.dev/c/7d7bf60a-d8a8-4b7e-80da-1e73b45819cb).
- RF148: A API confirmou o salvamento de -1. A leitura posterior trouxe 0 e a gravação não mostrou explicação para a diferença. [Jam 9 — Validação de dias de bloqueio da catraca](https://jam.dev/c/f607bc49-184f-4d55-81ab-7db825af6021).

---

[← Início](../README.md) · [Cenários de teste](Cenario_Teste/) · [Evidências de Clientes](Evidencias/CT-RF03_Filtros_Clientes/README.md)
