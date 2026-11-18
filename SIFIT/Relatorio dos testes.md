# 📊 Relatório de Testes — SIFIT

**Escopo:** 129 casos documentados (CT-RF01–CT-RF35, CT-RF38–CT-RF62 e CT-RF65–CT-RF133) — autenticação, recuperação, perfil, Clientes, financeiro, página inicial e dashboard, modalidades / tema de SifitBox, Categorias Crossfit, Avaliações, Exercícios, Grupos Musculares, Objetivos de Treino cadastro de categorias com código automático, SifitBox – Turmas, Pagar.me, Configurações, Despesas Fixas, Relatórios, Grupos (treino), Fichas de Anamnese, gestão de Modelos de Anamnese, gestão de Categorias de Anamnese, edição de Perguntas Anamnese, validações/funções/exclusão/busca de Colaboradores, Prospecção, Bandeiras de Cartão, Contas a Pagar, Modelos de Contrato, Planos, Tipos de Pagamento e Modelos de Ficha.

**Datas das gravações do Jam:** CT-RF01 em 23/10/2026; CT-RF02_ERRO em 22/10/2026 às 21:45 BRT; CT-RF03 não confirmada; CT-RF04_loginComSucesso em 13/11/2026; CT-RF05–CT-RF20 em 14/11/2026; CT-RF21 em 15/11/2026 às 15:07:51,265 BRT; CT-RF22–28 em 15/11/2026 às 15:25, 15:40, 15:38, 15:35, 16:11, 16:08 e 16:07 BRT; CT-RF29–33 em 15/11/2026 às 15h56 BRT (uma única gravação); CT-RF34 em 15/11/2026 às 17:23 BRT; CT-RF35 em 15/11/2026 às 18:13 BRT; CT-RF38 em 15/11/2026 às 18:41 BRT; CT-RF39–41 em 15/11/2026 às 18:51 BRT (uma única gravação); CT-RF42–45 às 19:06, CT-RF46–49 às 19:07 e CT-RF50–56 às 19:09 BRT (uma gravação por grupo); CT-RF57 e CT-RF58 em 15/11/2026 às 21h03 BRT (mesma gravação); CT-RF59 em 15/11/2026 às 22h07 BRT; CT-RF60 em 15/11/2026 às 23h34 BRT; CT-RF61 em 16/11/2026 às 15h24 BRT; CT-RF62 em 16/11/2026 às 15h57 BRT. CT-RF74–CT-RF84: 16/11/2026 conforme os resumos, sem horário informado. CT-RF85–90 às 21:52, CT-RF91–95 às 21:58, CT-RF96–98 às 21:55 e CT-RF99–103 às 21:54 e CT-RF104–108 às 22:03 BRT em 15/11/2026 (uma gravação por grupo). CT-RF109–CT-RF115 em 16/11/2026 entre 22:19:51 e 22:29:07 BRT. CT-RF116–CT-RF121 amplia a cobertura de Configurações e Modelos de Ficha com gravações de 16/11/2026 entre 22:03:53 e 22:18:52 BRT. CT-RF122–CT-RF127 cobre Inteligência e Configurações com gravações de 16/11/2026 entre 21:50:51 e 22:02:16 BRT. CT-RF128–CT-RF133 cobre Inteligência e Automação com gravações de 16/11/2026 entre 21:40:31 e 21:49:48 BRT.

**Data da revisão documental:** 17/11/2026, com integração de CT-RF128–CT-RF133 (Inteligência e Automação).

**Origem do resultado:** análise de evidências fornecidas; sem nova execução no sistema nesta revisão.

**Padronização documental:** 13/11/2026, preservando as datas e os resultados das análises anteriores.

---

## 📊 1. Resumo dos resultados

O caso **CT-RF01** foi classificado como **reprovado**: a opção "Esqueci minha senha" não inicia o fluxo de recuperação. O Jam mostra cliques repetidos e permanência na tela de login; a consulta aos registros da captura retorna **0 requisições de rede** e **0 mensagens de erro no console**.

O **CT-RF02_ERRO** também foi classificado como **reprovado**: o perfil apresenta conteúdo fictício, textos em inglês, seções sem campos visíveis e layout desconfigurado. A classificação se apoia no relato, na captura, no HTML fornecido e na consulta ao Jam. A causa técnica não foi confirmada no código.

O **CT-RF03** foi classificado como **reprovado conforme o relato**: a busca com filtros combinados mantém clientes incompatíveis e resultados praticamente iguais ao alternar a situação financeira. As capturas foram fornecidas como apoio; não mostram todos os valores completos nem os vínculos de cada cliente. O conteúdo do Jam não pôde ser consultado diretamente nesta revisão, e a causa não foi confirmada no código.

O **CT-RF04_loginComSucesso** foi classificado como **aprovado conforme a gravação**: o usuário preenche credenciais válidas, clica em Entrar e acessa `/dashboard`. As chamadas de login e verificação da sessão retornam HTTP 200; os quadros mostram o menu e o resumo da academia após a autenticação. Não houve nova execução no sistema.

Os 16 cenários incluídos em 14/11/2026 acrescentaram **5 aprovações**, **7 reprovações nas evidências** e **4 pontos a validar**. CT-RF21 acrescentou uma reprovação e o BUG-010. CT-RF22–25 acrescentaram uma aprovação, duas reprovações com confirmação pendente e um ponto a validar. CT-RF26–28 acrescentam três reprovações por ausência de feedback visual nos testes negativos, vinculadas a BUG-013–BUG-015 em triagem.

O **CT-RF29** acrescenta uma reprovação e o BUG-016: a exclusão de grupo muscular retorna HTTP 500 em duas tentativas, com o corpo `{"verifica_erro": true, "mensagem": "Erro interno inesperado."}`; a interface apresenta o diálogo "Erro ao deletar Grupo" e o registro permanece na listagem. A causa não foi determinada.

CT-RF30 acrescenta uma reprovação e o BUG-017 (imagens dos grupos musculares com HTTP 422); CT-RF31–33 acrescentam três aprovações limitadas aos exemplos gravados. O **CT-RF35** acrescenta uma reprovação e o BUG-019: o cadastro de objetivo de treino retorna HTTP 500 em duas ocorrências, com o diálogo "Erro ao salvar objetivo" e a listagem sem registros; o corpo da requisição e da resposta não foi capturado e a causa não foi determinada. O **CT-RF38** acrescenta uma aprovação limitada ao exemplo gravado: o cadastro de categoria cria o registro apenas com o nome (HTTP 201), o código 9 é atribuído pelo sistema e o filtro por código localiza o novo registro; sem defeito. O **CT-RF39** acrescenta uma aprovação (cadastro de modalidade com HTTP 201); o **CT-RF40** acrescenta um ponto a validar (exclusão por lixeira que inativa os registros, regra a confirmar); o **CT-RF41** acrescenta uma reprovação e o BUG-020 (cadastro de turma sem modalidade, sem retorno visível; validação nativa não confirmada). CT-RF42 a CT-RF45 (Pagar.me e Configurações) acrescentam uma aprovação (criação de cobrança), dois pontos a validar (saque e salvamento das configurações) e uma reprovação com o BUG-021 (painel que mantém Recebimentos ao trocar o período); CT-RF46 a CT-RF49 (Despesas Fixas) acrescentam três aprovações (filtros, exclusão e edição) e um ponto a validar (cadastro com duas requisições de criação); CT-RF50 a CT-RF56 (Relatórios) acrescentam uma aprovação (Matrículas), um ponto a validar (Contas a Pagar sem registros) e cinco reprovações, com o BUG-022 (Contas a Receber sem valor) e o BUG-023 (quatro relatórios com arquivo vazio de 0 bytes). O **CT-RF57** acrescenta uma reprovação e o BUG-024: a exclusão de grupo retorna HTTP 500 em duas tentativas, com o corpo `{"verifica_erro": true, "mensagem": "Erro interno inesperado."}` — endpoint e mensagem idênticos aos do BUG-016 para grupos musculares; o registro permanece na listagem e a causa não foi determinada. O **CT-RF58**, na mesma gravação, acrescenta uma reprovação e o BUG-025: a edição do grupo retorna sucesso (`verifica_erro: false`) ao alterar o campo Status para "Inativo", mas a consulta seguinte mostra o registro ainda com o status anterior; na mesma sessão, a edição do campo Descrição é persistida corretamente, isolando a falha ao campo status. O **CT-RF59** acrescenta uma reprovação e o BUG-032: o cadastro de uma anamnese retorna HTTP 500 em sete tentativas — quatro pela rota de aplicar e três pela de salvar rascunho, com dois modelos e três respostas diferentes — sempre com o corpo `{"verifica_erro": true, "mensagem": "Erro interno inesperado."}`, mesmo padrão já observado nos BUG-016 e BUG-024; nenhuma anamnese é cadastrada com sucesso na gravação. O **CT-RF60** acrescenta uma aprovação: a busca, o filtro, o cadastro com três perguntas do banco, duas edições e duas exclusões de modelos de anamnese retornam HTTP 200 ou 201 em todas as quinze requisições identificadas, sem nenhuma ocorrência de erro 4xx ou 5xx; nenhum defeito foi identificado no fluxo avaliado. O **CT-RF61** acrescenta uma aprovação: o filtro por status, a busca por texto, o cadastro, três edições sucessivas (ícone, nome e status), o cancelamento correto de uma quarta edição sem salvar e a exclusão de uma categoria de anamnese retornam HTTP 200 ou 201 em todas as sete requisições identificadas aos endpoints `/api/categorias-anamnese/*`, sem nenhuma ocorrência de erro 4xx ou 5xx; nenhum defeito foi identificado no fluxo avaliado. O **CT-RF62** acrescenta uma reprovação e o BUG-044: o cadastro de uma pergunta de anamnese é concluído com sucesso, mas as quatro tentativas seguintes de editar o tipo de resposta e/ou o status dessa mesma pergunta retornam HTTP 500 com o mesmo corpo genérico `{"verifica_erro": true, "mensagem": "Erro interno inesperado."}`, no mesmo padrão já observado nos BUG-016, BUG-024 e BUG-032; nenhuma alteração é persistida. Os **CT-RF65 a CT-RF70** acrescentam seis reprovações e os BUG-026 a BUG-031: validações de data de nascimento, formato de CREF e campos obrigatórios aceitam atualização com HTTP 200 e sem validação visível; a mesma função pode ser associada repetidamente ao colaborador; e a exclusão de colaborador retorna HTTP 500 com o mesmo corpo genérico já observado nos BUG-016 e BUG-024. CT-RF85 a CT-RF90 (Prospecção) acrescentam quatro aprovações (tema e notificações, busca, filtro por estágio e edição), um ponto a validar (cadastro de lead com duas requisições de criação) e uma reprovação com o BUG-038 (telefone com 30 dígitos aceito sem validação). CT-RF91 a CT-RF95 (Contas a Pagar) acrescentam duas aprovações (visualização e exclusão), dois pontos a validar (filtros e busca de colaborador) e uma reprovação com o BUG-039 (conta a colaborador gravada sem colaborador); CT-RF96 a CT-RF98 (Modelos de Contrato) acrescentam duas aprovações (variáveis e cadastro) e uma reprovação com o BUG-040 (tabela vazia com 15 modelos retornados); CT-RF99 a CT-RF103 (Planos) acrescentam quatro aprovações (filtros, tema, cadastro e edição) e uma reprovação com o BUG-041 (cartão Ativos aumenta com planos inativos). CT-RF104 a CT-RF108 (Tipos de Pagamento) acrescentam duas aprovações (edição e tema com notificações), um ponto a validar (filtros) e duas reprovações, com o BUG-042 (status Ativo não enviado nem refletido) e o BUG-043 (exclusão de tipo em uso com HTTP 404 e erro SQL). As contagens consolidadas são:

CT-RF74–CT-RF84 acrescentam oito aprovações e três reprovações conforme os resumos fornecidos, com BUG-035–BUG-037 em triagem. CT-RF83 mantém a classificação do relato, condicionada à confirmação da regra de obrigatoriedade. Os dez casos anteriores a validar permanecem inalterados.

A revisão de Modelos de Ficha inclui CT-RF109–CT-RF115 com base em 6 gravações do Jam de 16/11/2026. A revisão documental foi feita em 17/11/2026. 3 aprovado(s) conforme a gravação e 4 a validar. O material não acrescenta defeitos confirmados.

CT-RF116–CT-RF121 amplia a cobertura de Configurações e Modelos de Ficha com gravações de 16/11/2026 entre 22:03:53 e 22:18:52 BRT. Casos aprovados: 4. Reprovados: 1. A validar: 1.

CT-RF122–CT-RF127 cobre Inteligência e Configurações com gravações de 16/11/2026 entre 21:50:51 e 22:02:16 BRT. Casos aprovados: 3. Reprovados: 2. A validar: 1.

CT-RF128–CT-RF133 cobre Inteligência e Automação com gravações de 16/11/2026 entre 21:40:31 e 21:49:48 BRT. Casos aprovados: 5. Reprovados: 1. A validar: 0.

| Casos documentados | Aprovados | Reprovados | A validar | Defeitos registrados | Casos com reteste corretivo pendente |
| :---: | :---: | :---: | :---: | :---: | :---: |
| 129 | 57 | 52 | 20 | 48 (10 abertos + 38 em triagem) | 52 |

Os 48 retestes incluem CT-RF22/24/26/27/28/29/30/35/41/45/51/53/54/55/56/57/58/59/62/65/66/67/68/69/70/71/73/81/82/83/89/92/98/102/105/107, sujeitos à confirmação funcional e técnica. As contagens representam os casos documentados com base nas fontes indicadas, sem novas execuções nesta revisão. As nove variações planejadas para o reteste do CT-RF03 não foram executadas e não são contabilizadas como testes adicionais realizados.

---

## 🔍 2. Cobertura e resultado por caso

| Caso | Requisito | Esperado | Obtido | Resultado | Defeito |
| --- | --- | --- | --- | --- | --- |
| [CT-RF01](Cenario_Teste/CT-RF01_Esqueci-senha.md) | [RF01](Analise%20de%20requisitos.md#rf01--iniciar-recuperação-de-senha) | Abrir formulário ou página para iniciar a recuperação de senha. | Tela de login permanece sem abertura do fluxo; nenhum registro de requisição no Jam. | Reprovado | [BUG-001](Relatorio-de-Bugs.md#bug-001--link-esqueci-minha-senha-não-executa-nenhuma-ação) |
| [CT-RF02_ERRO](Cenario_Teste/CT-RF02_ERRO.md) | [RF02](Analise%20de%20requisitos.md#rf02--exibir-perfil-do-usuário-autenticado) | Exibir dados da conta, campos visíveis, textos em português e layout organizado. | Conteúdo fictício, campos não exibidos, imagem desproporcional e rolagem horizontal. | Reprovado | [BUG-002](Relatorio-de-Bugs.md#bug-002--perfil-com-dados-fictícios-campos-ausentes-e-layout-desconfigurado) |
| [CT-RF03](Cenario_Teste/CT-RF03_FILTRO_TelaClientes.md) | [RF03](Analise%20de%20requisitos.md#rf03--pesquisar-clientes-com-filtros-combinados) | Retornar somente clientes que atendam a todos os filtros selecionados, com lógica AND, e apresentar mensagem para conjunto vazio. | Relato de clientes incompatíveis com a seleção e resultados praticamente iguais ao alternar Inadimplente/Adimplente. | Reprovado conforme o relato | [BUG-003](Relatorio-de-Bugs.md#bug-003--filtros-combinados-da-página-clientes-não-restringem-a-listagem) |
| [CT-RF04_loginComSucesso](Cenario_Teste/CT-RF04_loginComSucesso.md) | [RF04](Analise%20de%20requisitos.md#rf04--autenticar-usuário-com-credenciais-válidas) | Autenticar com credenciais válidas e apresentar o dashboard. | Chamadas de autenticação HTTP 200, navegação para `/dashboard`, menu e resumo da academia visíveis. | Aprovado conforme a gravação | Nenhum identificado no fluxo avaliado. |
| [CT-RF05](Cenario_Teste/CT-RF05_Login_SenhaIncorreta.md) | [RF05](Analise%20de%20requisitos.md#rf05) | Recusar a autenticação e informar a falha sem abrir a área autenticada. | Após o envio, a tela permanece no login e apresenta “O nome de usuário e senha não correspondem.” | Aprovado conforme a gravação | Nenhum no fluxo avaliado |
| [CT-RF06](Cenario_Teste/CT-RF06_Login_UsuarioInexistente.md) | [RF06](Analise%20de%20requisitos.md#rf06) | Recusar o acesso para credenciais inválidas. | A gravação termina na página de login com a mensagem genérica de credenciais inválidas, sem acesso ao painel. | Aprovado conforme a gravação | Nenhum no fluxo avaliado |
| [CT-RF07](Cenario_Teste/CT-RF07_Exportacao_Financeiro.md) | [RF07](Analise%20de%20requisitos.md#rf07) | Iniciar a exportação e apresentar um retorno claro ao usuário. | Vários cliques em Exportar não produzem mudança ou confirmação visível durante a gravação. | Reprovado nas evidências | [BUG-004](Relatorio-de-Bugs.md#bug-004) |
| [CT-RF08](Cenario_Teste/CT-RF08_Calculo_Cobranca.md) | [RF08](Analise%20de%20requisitos.md#rf08) | Exibir a composição do total, incluindo eventuais juros, e deixar claro qual valor será comunicado. | O modal mostra valor original de R$ 350,00, multa de R$ 7,00 e total atualizado de R$ 377,83. A mensagem inicial cita R$ 350,00; o autor escreve que o valor deveria ser R$ 357,00. | A validar — regra ou contexto pendente | Sem defeito confirmado |
| [CT-RF09](Cenario_Teste/CT-RF09_Contagem_Mensalidades.md) | [RF09](Analise%20de%20requisitos.md#rf09) | Manter a contagem, a listagem e a paginação coerentes e permitir consultar todos os registros contabilizados. | Todos informa três mensalidades, mas aparece uma linha. No filtro +30 dias, o contador indica dois registros e apenas uma linha permanece disponível. | Reprovado nas evidências | [BUG-005](Relatorio-de-Bugs.md#bug-005) |
| [CT-RF10](Cenario_Teste/CT-RF10_Filtro_Mensalidades.md) | [RF10](Analise%20de%20requisitos.md#rf10) | O contador do filtro e os registros exibidos devem representar o mesmo conjunto. | O filtro mantém o contador 1, enquanto a lista informa “Nenhuma mensalidade encontrada para o filtro atual”. | Reprovado nas evidências | [BUG-005](Relatorio-de-Bugs.md#bug-005) |
| [CT-RF11](Cenario_Teste/CT-RF11_Metricas_Financeiro.md) | [RF11](Analise%20de%20requisitos.md#rf11) | Indicar claramente quais métricas seguem o filtro e quais representam o total geral ou o mês. | A lista alterna entre uma linha e estado vazio. O cartão de atraso muda de dois para zero alunos; outros totais, como Total em aberto de R$ 470,00 e Recuperado no mês de R$ 45,00, permanecem. | A validar — regra ou contexto pendente | Sem defeito confirmado |
| [CT-RF12](Cenario_Teste/CT-RF12_Periodo_Dashboard.md) | [RF12](Analise%20de%20requisitos.md#rf12) | Validar a ordem das datas, orientar o usuário e aplicar um período válido com retorno perceptível. | O seletor chega a exibir 19/11/2026–10/11/2026, com início posterior ao fim, sem uma validação visível. Os indicadores permanecem com os mesmos valores nos quadros conferidos. | Reprovado nas evidências | [BUG-006](Relatorio-de-Bugs.md#bug-006) |
| [CT-RF13](Cenario_Teste/CT-RF13_Codigos_Personais.md) | [RF13](Analise%20de%20requisitos.md#rf13) | Se a coluna for um identificador de cadastro, lacunas são aceitáveis. Se deveria numerar linhas, a regra precisa ser esclarecida. | A lista contém quatro personais e o total informado é quatro. A coluna Código apresenta identificadores não sequenciais, como #1, #2, #4 e #11. | A validar — regra ou contexto pendente | Sem defeito confirmado |
| [CT-RF14](Cenario_Teste/CT-RF14_Contraste_TemaEscuro.md) | [RF14](Analise%20de%20requisitos.md#rf14) | Aplicar cores de texto e de fundo que preservem a legibilidade em ambos os temas. | As áreas de Modalidades e Turmas recorrentes permanecem brancas enquanto diversos textos ficam muito claros, dificultando sua leitura. | Reprovado nas evidências | [BUG-007](Relatorio-de-Bugs.md#bug-007) |
| [CT-RF15](Cenario_Teste/CT-RF15_Edicao_Modalidade.md) | [RF15](Analise%20de%20requisitos.md#rf15) | Oferecer ações visíveis de salvar e cancelar e confirmar a atualização. | Há ícones de lápis na lista. Ao clicar, os campos superiores são preenchidos para edição, mas não aparece uma ação clara para salvar ou concluir a alteração nos quadros analisados. | Reprovado nas evidências | [BUG-008](Relatorio-de-Bugs.md#bug-008) |
| [CT-RF16](Cenario_Teste/CT-RF16_Exclusao_Modalidade.md) | [RF16](Analise%20de%20requisitos.md#rf16) | O nome, o ícone e a confirmação da ação devem informar se o efeito é desativar ou excluir definitivamente. | As modalidades passam a aparecer como inativas e continuam na listagem, mesmo após novos cliques. A linha do tempo registra chamadas a /api/sifitbox/modalidades/excluir/1 e recargas das listas com HTTP 200. | A validar — regra ou contexto pendente | Sem defeito confirmado |
| [CT-RF17](Cenario_Teste/CT-RF17_Filtros_Categorias.md) | [RF17](Analise%20de%20requisitos.md#rf17) | Exibir apenas os registros correspondentes aos critérios e restaurar a lista ao limpar. | A quantidade de linhas exibidas muda conforme o código informado; a limpeza retorna a lista e a busca por barbell mostra a categoria correspondente. | Aprovado conforme a gravação | Nenhum no fluxo avaliado |
| [CT-RF18](Cenario_Teste/CT-RF18_Atualizacao_Categoria.md) | [RF18](Analise%20de%20requisitos.md#rf18) | Persistir a alteração e atualizar a listagem. | O modal fecha e a lista exibe Barbell novo. | Aprovado conforme a gravação | Nenhum no fluxo avaliado |
| [CT-RF19](Cenario_Teste/CT-RF19_Exclusao_Categoria.md) | [RF19](Analise%20de%20requisitos.md#rf19) | Concluir a exclusão permitida ou explicar de forma tratável por que o registro não pode ser excluído. | Após a confirmação, aparece o diálogo “Erro” / “Erro ao deletar categoria”. A categoria permanece na lista. | Reprovado nas evidências | [BUG-009](Relatorio-de-Bugs.md#bug-009) |
| [CT-RF20](Cenario_Teste/CT-RF20_Criacao_Categoria.md) | [RF20](Analise%20de%20requisitos.md#rf20) | Criar a categoria e apresentar o novo registro na listagem. | O modal fecha, o contador passa de sete para oito e a lista passa a incluir cardio leve. | Aprovado conforme a gravação | Nenhum no fluxo avaliado |
| [CT-RF21](Cenario_Teste/CT-RF21_Cadastro_Avaliacao.md) | [RF21](Analise%20de%20requisitos.md#rf21) | Cadastrar dados válidos ou informar validação específica, sem HTTP 500. | POST de agendamento retorna HTTP 500; alerta “Erro ao cadastrar Avaliação.”; formulário aberto. | Reprovado nas evidências | [BUG-010](Relatorio-de-Bugs.md#bug-010) |
| [CT-RF22](Cenario_Teste/CT-RF22_Digitacao_Codigo_Exercicio.md) | [RF22](Analise%20de%20requisitos.md#rf22) | Quando editável, o campo Código deve aceitar e manter um código válido e permitir sua correção. | O testador relata não conseguir digitar o código. A imagem inicial confirma o campo Código no formulário Exercício; a reprodução integral, as teclas e o foco não foram confirmados. | Reprovado conforme o relato; reprodução independente pendente. | [BUG-011](Relatorio-de-Bugs.md#bug-011), em triagem |
| [CT-RF23](Cenario_Teste/CT-RF23_Exclusao_Exercicio.md) | [RF23](Analise%20de%20requisitos.md#rf23) | O sistema deve remover o exercício permitido da biblioteca e atualizar os totais. Se houver impedimento, deve explicá-lo sem indicar sucesso indevido. | No quadro de aproximadamente 0:02, a biblioteca apresenta total 11 e o exercício Levantamento de Peso. No quadro final, em aproximadamente 0:06, esse registro não aparece e o total é 10. A lista continua contendo Levantamento de Peso 02, registro distinto. | Aprovado no trecho consultado. | Sem defeito confirmado |
| [CT-RF24](Cenario_Teste/CT-RF24_Edicao_Exercicio.md) | [RF24](Analise%20de%20requisitos.md#rf24) | Salvar a edição deve atualizar o mesmo exercício, sem criar um registro adicional e sem aumentar o total da biblioteca. | O Jam está identificado como teste de edição. Nos quadros intermediários, o formulário Exercício está aberto com código 16, o nome é preenchido e a biblioteca ao fundo indica total 10. No quadro final, o formulário fecha, o total é 11 e a lista contém Levantamento de Peso e Levantamento de Peso 02. O aumento e a coexistência dos nomes divergem do resultado esperado para uma edição. | Reprovado no trecho consultado; confirmar operação e identidade dos registros na reprodução. | [BUG-012](Relatorio-de-Bugs.md#bug-012), em triagem |
| [CT-RF25](Cenario_Teste/CT-RF25_Envio_Exercicio_Imagem.md) | [RF25](Analise%20de%20requisitos.md#rf25) | O sistema deve cadastrar o exercício, atualizar a biblioteca e manter a imagem vinculada ao registro, disponível após reabrir o cadastro. | O quadro inicial consultado mostra o formulário Exercício preenchido com nome braço forte e uma miniatura na seção Imagem; a biblioteca ao fundo indica total 9. O quadro final mostra o formulário fechado, braço forte na lista e total 10. Esses quadros sustentam a criação com imagem selecionada, mas não demonstram a reabertura ou a visualização da imagem salva. | A validar — criação visível; persistência e associação da imagem não confirmadas. | Sem defeito confirmado |
| [CT-RF26](Cenario_Teste/CT-RF26_Exercicio_Campos_Vazios.md) | [RF26](Analise%20de%20requisitos.md#rf26) | Bloquear o envio, indicar os campos obrigatórios e não criar registro vazio. | O formulário permanece aberto após a tentativa de salvar, sem mensagem, destaque ou orientação de validação visível. A persistência não foi demonstrada. | Reprovado — sem feedback de validação visível. | [BUG-013](Relatorio-de-Bugs.md#bug-013), em triagem |
| [CT-RF27](Cenario_Teste/CT-RF27_Video_Campo_Imagem.md) | [RF27](Analise%20de%20requisitos.md#rf27) | Rejeitar vídeo no campo Imagem e informar formatos e limites aceitos. | O vídeo não aparece anexado e não há mensagem visível explicando a rejeição ou os formatos permitidos. | Reprovado — arquivo rejeitado sem feedback visível. | [BUG-014](Relatorio-de-Bugs.md#bug-014), em triagem |
| [CT-RF28](Cenario_Teste/CT-RF28_Imagem_Campo_Video.md) | [RF28](Analise%20de%20requisitos.md#rf28) | Rejeitar imagem no campo Vídeo e informar formatos e limites aceitos. | A imagem não aparece anexada e não há mensagem visível explicando a rejeição ou os formatos permitidos. | Reprovado — arquivo rejeitado sem feedback visível. | [BUG-015](Relatorio-de-Bugs.md#bug-015), em triagem |
| [CT-RF29](Cenario_Teste/CT-RF29_Exclusao_GrupoMuscular.md) | [RF29](Analise%20de%20requisitos.md#rf29) | Concluir a exclusão permitida, removendo o registro e atualizando os contadores, ou explicar de forma tratável o impedimento, sem erro interno. | Diálogo "Erro" / "Erro ao deletar Grupo" com o botão "Fechar". O registro permanece na listagem e os contadores não se alteram. Duas tentativas retornam HTTP 500. | Reprovado nas evidências | [BUG-016](Relatorio-de-Bugs.md#bug-016), em triagem |
| [CT-RF30](Cenario_Teste/CT-RF30_Imagens_GruposMusculares.md) | [RF30](Analise%20de%20requisitos.md#rf30) | Apresentar a imagem cadastrada de cada grupo muscular. | Todas as linhas exibem o ícone de imagem quebrada; as requisições de arquivo retornam HTTP 422 durante toda a gravação. | Reprovado nas evidências | [BUG-017](Relatorio-de-Bugs.md#bug-017), em triagem |
| [CT-RF31](Cenario_Teste/CT-RF31_Cadastro_GrupoMuscular.md) | [RF31](Analise%20de%20requisitos.md#rf31) | Criar o grupo muscular, listá-lo e atualizar os contadores. | O registro "Tríceps" é criado com código 6; listagem de 3 para 4 registros e cartões atualizados. | Aprovado conforme a gravação | Nenhum no fluxo avaliado |
| [CT-RF32](Cenario_Teste/CT-RF32_Edicao_TipoMembro.md) | [RF32](Analise%20de%20requisitos.md#rf32) | Alterar o tipo de membro e refletir a mudança na listagem e nos cartões. | A alteração é aplicada, a listagem é atualizada e os cartões permanecem coerentes. | Aprovado conforme a gravação | Nenhum no fluxo avaliado |
| [CT-RF33](Cenario_Teste/CT-RF33_Filtros_GruposMusculares.md) | [RF33](Analise%20de%20requisitos.md#rf33) | Filtrar por código e tipo de membro, com rodapé coerente e resultado vazio informado. | Os filtros exercitados retornam conjuntos coerentes; o tipo sem registros apresenta "Nenhum grupo muscular encontrado". A lógica combinada não foi demonstrada. | Aprovado conforme a gravação | Nenhum no fluxo avaliado |
| [CT-RF34](Cenario_Teste/CT-RF34_Erro_Servidor_Excesso_Requisicoes.md) | [RF34](Analise%20de%20requisitos.md#rf34) | Carregar os componentes do dashboard sem HTTP 500 e tratar falhas parciais de forma específica. | O dashboard apresenta diálogo de erro; entre 23 eventos visíveis, diversas chamadas GET/POST retornam HTTP 500. Endpoints e causa não foram confirmados. | Reprovado nas evidências. | [BUG-018](Relatorio-de-Bugs.md#bug-018), em triagem |
| [CT-RF35](Cenario_Teste/CT-RF35_Cadastro_Objetivo_Treino.md) | [RF35](Analise%20de%20requisitos.md#rf35) | Cadastrar o objetivo e listá-lo, ou informar validação específica, sem HTTP 500. | `POST /api/objetivo-treino/salvar/1` retorna HTTP 500 (duas ocorrências); diálogo "Erro ao salvar objetivo"; a listagem permanece sem registros. | Reprovado nas evidências | [BUG-019](Relatorio-de-Bugs.md#bug-019), em triagem |
| [CT-RF38](Cenario_Teste/CT-RF38_Cadastro_Categoria_Codigo_Automatico.md) | [RF38](Analise%20de%20requisitos.md#rf38) | Cadastrar a categoria com código atribuído pelo sistema, atualizar a listagem e os cartões e localizar o registro pelos filtros. | `POST /api/categoria-exercicio-cross/criar` retorna HTTP 201 com apenas o nome; a listagem passa de oito para nove categorias (código 9) e o filtro Código "9" retorna só o novo registro. O campo Código não retém o texto digitado. | Aprovado conforme a gravação | Nenhum no fluxo avaliado |
| [CT-RF39](Cenario_Teste/CT-RF39_Cadastro_Modalidade.md) | [RF39](Analise%20de%20requisitos.md#rf39) | Criar a modalidade com os dados informados, listá-la e limpar o formulário. | `POST /api/sifitbox/modalidades/salvar/1` retorna HTTP 201 (id 4, status "ativo"); a listagem passa de três para quatro modalidades. | Aprovado conforme a gravação | Nenhum no fluxo avaliado |
| [CT-RF40](Cenario_Teste/CT-RF40_Exclusao_Turmas_Modalidades.md) | [RF40](Analise%20de%20requisitos.md#rf40) | Aplicar e comunicar a regra de exclusão e refletir o resultado na listagem conforme o filtro de status. | Quatro `POST turmas/excluir` e cinco `POST modalidades/excluir` retornam HTTP 200 e `{"erro": false}`; os registros continuam listados com o status "inativo", sem diálogo de confirmação. | A validar — regra ou contexto pendente | Sem defeito confirmado |
| [CT-RF41](Cenario_Teste/CT-RF41_Cadastro_Turma_Sem_Modalidade.md) | [RF41](Analise%20de%20requisitos.md#rf41) | Bloquear o envio sem modalidade, indicar o campo pendente e não criar a turma. | Nenhuma mensagem de validação visível e nenhuma requisição de criação de turma nas tentativas de envio; o formulário permanece preenchido. | Reprovado — sem feedback de validação visível | [BUG-020](Relatorio-de-Bugs.md#bug-020), em triagem |
| [CT-RF42](Cenario_Teste/CT-RF42_Solicitacao_Saque_PagarMe.md) | [RF42](Analise%20de%20requisitos.md#rf42) | Registrar a solicitação e informar o resultado ao usuário. | `POST sacar-saldo` retorna HTTP 200; sem mensagem de resultado visível e com o saldo "R$ --". | A validar — regra ou contexto pendente | Sem defeito confirmado |
| [CT-RF43](Cenario_Teste/CT-RF43_Criacao_Cobranca_PagarMe.md) | [RF43](Analise%20de%20requisitos.md#rf43) | Criar a cobrança e informar o sucesso ao usuário. | `POST criar-cobranca` retorna HTTP 200 e o diálogo "Cobrança criada com sucesso!". | Aprovado conforme a gravação | Nenhum no fluxo avaliado |
| [CT-RF44](Cenario_Teste/CT-RF44_Configuracoes_Home_Salvamento.md) | [RF44](Analise%20de%20requisitos.md#rf44) | Salvar com confirmação, persistir e refletir nas opções e no menu. | Opções e campo de dias alterados; menu lateral muda após Salvar Configurações; sem mensagem de confirmação visível. | A validar — regra ou contexto pendente | Sem defeito confirmado |
| [CT-RF45](Cenario_Teste/CT-RF45_Painel_PagarMe_Periodo.md) | [RF45](Analise%20de%20requisitos.md#rf45) | Atualizar valor, gráfico e eixo conforme o período selecionado. | Recebimentos R$ 38.420,00 e gráfico idênticos em "Últimos 30 dias" e "Últimos 7 dias"; saldos "R$ --". | Reprovado nas evidências | [BUG-021](Relatorio-de-Bugs.md#bug-021), em triagem |
| [CT-RF46](Cenario_Teste/CT-RF46_Filtros_Despesas_Fixas.md) | [RF46](Analise%20de%20requisitos.md#rf46) | Apresentar apenas as despesas correspondentes e restaurar a lista ao limpar. | Código "1" lista os códigos 10 a 19; nome "Teste" retorna #5 e #7; Valor Listado acompanha o filtro; os campos limpos restauram a lista. | Aprovado conforme a gravação | Nenhum no fluxo avaliado |
| [CT-RF47](Cenario_Teste/CT-RF47_Cadastro_Despesa_Fixa.md) | [RF47](Analise%20de%20requisitos.md#rf47) | Criar uma única despesa com uma única requisição de criação. | Despesa 23 criada (16 para 17 registros); um clique gera dois `POST cria/despesa-fixa` com HTTP 201. | A validar — regra ou contexto pendente | Sem defeito confirmado |
| [CT-RF48](Cenario_Teste/CT-RF48_Exclusao_Despesa_Fixa.md) | [RF48](Analise%20de%20requisitos.md#rf48) | Confirmar, excluir e atualizar a listagem e os cartões. | Diálogo de confirmação; `POST deleta/despesa-fixa` retorna HTTP 200; listagem de 17 para 16 despesas. | Aprovado conforme a gravação | Nenhum no fluxo avaliado |
| [CT-RF49](Cenario_Teste/CT-RF49_Edicao_Despesa_Fixa.md) | [RF49](Analise%20de%20requisitos.md#rf49) | Atualizar a mesma despesa e refletir a alteração na listagem. | `POST edita/despesa-fixa` retorna HTTP 200; a despesa 7 passa a "7 Dias" e a quantidade de despesas permanece 16. | Aprovado conforme a gravação | Nenhum no fluxo avaliado |
| [CT-RF50](Cenario_Teste/CT-RF50_Relatorio_Matriculas.md) | [RF50](Analise%20de%20requisitos.md#rf50) | Gerar PDF válido com as matrículas do período. | PDF de 7.784 bytes com cabeçalho, período e uma matrícula (R$ 20,00); "Quantidade de registros: 1". | Aprovado conforme a gravação | Nenhum no fluxo avaliado |
| [CT-RF51](Cenario_Teste/CT-RF51_Relatorio_Contas_Receber.md) | [RF51](Analise%20de%20requisitos.md#rf51) | Apresentar o valor a receber de cada conta e totais coerentes. | PDF com três contas pendentes e Valor a Receber "----" em todas as linhas; "Valor Recebido: R$ 0,00". | Reprovado nas evidências | [BUG-022](Relatorio-de-Bugs.md#bug-022), em triagem |
| [CT-RF52](Cenario_Teste/CT-RF52_Relatorio_Contas_Pagar_Pagas.md) | [RF52](Analise%20de%20requisitos.md#rf52) | Apresentar as contas pagas do período ou a estrutura vazia explícita. | PDF com a estrutura do relatório, sem linhas e com totalizadores R$ 0,00. | A validar — regra ou contexto pendente | Sem defeito confirmado |
| [CT-RF53](Cenario_Teste/CT-RF53_Relatorio_Avaliacoes_Vazio.md) | [RF53](Analise%20de%20requisitos.md#rf53) | Gerar PDF válido com o conteúdo do relatório ou a estrutura vazia explícita. | HTTP 200 e arquivo PDF de 0 bytes, que não abre; sem mensagem de erro. | Reprovado nas evidências | [BUG-023](Relatorio-de-Bugs.md#bug-023), em triagem |
| [CT-RF54](Cenario_Teste/CT-RF54_Relatorio_Clientes_Vazio.md) | [RF54](Analise%20de%20requisitos.md#rf54) | Gerar PDF válido com o conteúdo do relatório ou a estrutura vazia explícita. | HTTP 200 e arquivo PDF de 0 bytes, que não abre; sem mensagem de erro. | Reprovado nas evidências | [BUG-023](Relatorio-de-Bugs.md#bug-023), em triagem |
| [CT-RF55](Cenario_Teste/CT-RF55_Relatorio_Colaboradores_Vazio.md) | [RF55](Analise%20de%20requisitos.md#rf55) | Gerar PDF válido com o conteúdo do relatório ou a estrutura vazia explícita. | HTTP 200 e arquivo PDF de 0 bytes, que não abre; sem mensagem de erro. | Reprovado nas evidências | [BUG-023](Relatorio-de-Bugs.md#bug-023), em triagem |
| [CT-RF56](Cenario_Teste/CT-RF56_Relatorio_Caixas_Vazio.md) | [RF56](Analise%20de%20requisitos.md#rf56) | Gerar PDF válido com o conteúdo do relatório ou a estrutura vazia explícita. | HTTP 200 e arquivo PDF de 0 bytes, que não abre; sem mensagem de erro. | Reprovado nas evidências | [BUG-023](Relatorio-de-Bugs.md#bug-023), em triagem |
| [CT-RF57](Cenario_Teste/CT-RF57_Exclusao_Grupo.md) | [RF57](Analise%20de%20requisitos.md#rf57) | Excluir o grupo de teste e atualizar a listagem e os contadores. | Duas tentativas de `POST /api/deleta/grupo/1` retornam HTTP 500 com o corpo "Erro interno inesperado."; o registro permanece na listagem. | Reprovado nas evidências | [BUG-024](Relatorio-de-Bugs.md#bug-024), em triagem |
| [CT-RF58](Cenario_Teste/CT-RF58_Edicao_Grupo.md) | [RF58](Analise%20de%20requisitos.md#rf58) | Editar o campo Status do grupo de teste e confirmar a persistência na consulta seguinte. | `POST /api/edita/grupo/1` com `status: "inativo"` retorna HTTP 200, `{"verifica_erro": false}`, mas a consulta seguinte mantém o status "ativo"; a edição do campo descrição, na mesma sessão, persiste normalmente. | Reprovado nas evidências | [BUG-025](Relatorio-de-Bugs.md#bug-025), em triagem |
| [CT-RF59](Cenario_Teste/CT-RF59_Cadastro_Anamnese.md) | [RF59](Analise%20de%20requisitos.md#rf59) | Cadastrar uma anamnese (rascunho ou aplicada) para um aluno sem erro de servidor. | Sete tentativas (`aplicar` e `rascunho`) retornam HTTP 500 com o mesmo corpo "Erro interno inesperado.", em dois modelos e três respostas diferentes; nenhuma anamnese é cadastrada. | Reprovado nas evidências | [BUG-032](Relatorio-de-Bugs.md#bug-032), em triagem |
| [CT-RF60](Cenario_Teste/CT-RF60_Gestao_Modelos_Anamnese.md) | [RF60](Analise%20de%20requisitos.md#rf60--gerenciar-modelos-de-anamnese-sem-erro-de-servidor) | Buscar, filtrar, cadastrar, editar e excluir modelos de anamnese sem erro de servidor. | Quinze requisições aos endpoints `/api/modelos-anamnese/*` (busca/filtro, cadastro com três perguntas, duas edições e duas exclusões) retornam HTTP 200 ou 201; nenhuma com erro 4xx ou 5xx. | Aprovado conforme a gravação | Nenhum identificado no fluxo avaliado. |
| [CT-RF61](Cenario_Teste/CT-RF61_Gestao_Categorias_Anamnese.md) | [RF61](Analise%20de%20requisitos.md#rf61) | Filtrar, pesquisar, cadastrar, editar, cancelar edição e excluir categorias de anamnese sem erro de servidor. | Sete requisições aos endpoints `/api/categorias-anamnese/*` (cadastro, três edições e exclusão) retornam HTTP 200 ou 201; a quarta edição é cancelada sem requisição; nenhuma com erro 4xx ou 5xx. | Aprovado conforme a gravação | Nenhum identificado no fluxo avaliado. |
| [CT-RF62](Cenario_Teste/CT-RF62_Edicao_Pergunta_Anamnese.md) | [RF62](Analise%20de%20requisitos.md#rf62) | Editar o tipo de resposta ou o status de uma pergunta de anamnese sem erro de servidor. | Quatro tentativas de `POST /api/pergunta-anamnese/alterar/1` (tipo de resposta e/ou status) retornam HTTP 500 com a mesma mensagem genérica; nenhuma alteração é persistida. | Reprovado nas evidências | [BUG-044](Relatorio-de-Bugs.md#bug-044), em triagem |
| [CT-RF65](Cenario_Teste/CT-RF65_Data_Nascimento_Futura_Colaborador.md) | [RF65](Analise%20de%20requisitos.md#rf65) | Recusar data de nascimento futura na edição de colaborador. | Informar `18/05/2222` e salvar retorna HTTP 200 e navegação à lista, sem bloqueio visível. | Reprovado nas evidências | [BUG-026](Relatorio-de-Bugs.md#bug-026), em triagem |
| [CT-RF66](Cenario_Teste/CT-RF66_Data_Nascimento_Obrigatoria_Colaborador.md) | [RF66](Analise%20de%20requisitos.md#rf66) | Exigir data de nascimento obrigatória do colaborador. | Limpar a data obrigatória e salvar retorna HTTP 200, sem bloqueio visível. | Reprovado nas evidências | [BUG-027](Relatorio-de-Bugs.md#bug-027), em triagem |
| [CT-RF67](Cenario_Teste/CT-RF67_CREF_Formato_Colaborador.md) | [RF67](Analise%20de%20requisitos.md#rf67) | Validar o formato do CREF do colaborador. | Informar CREF `TESTEE` e salvar retorna HTTP 200, sem aplicação de formato. | Reprovado, com formato a confirmar | [BUG-028](Relatorio-de-Bugs.md#bug-028), em triagem |
| [CT-RF68](Cenario_Teste/CT-RF68_Edicao_Colaborador_Campo_Obrigatorio_Vazio.md) | [RF68](Analise%20de%20requisitos.md#rf68) | Bloquear edição de colaborador com campo obrigatório vazio. | Deixar campo obrigatório vazio e salvar retorna HTTP 200, sem validação visível. | Reprovado nas evidências | [BUG-029](Relatorio-de-Bugs.md#bug-029), em triagem |
| [CT-RF69](Cenario_Teste/CT-RF69_Funcao_Duplicada_Colaborador.md) | [RF69](Analise%20de%20requisitos.md#rf69) | Impedir função duplicada para o mesmo colaborador. | Adicionar duas vezes `funcao_id: 2` ao colaborador 4 gera dois HTTP 201 e a consulta passa de uma para três funções idênticas. | Reprovado nas evidências | [BUG-030](Relatorio-de-Bugs.md#bug-030), em triagem |
| [CT-RF70](Cenario_Teste/CT-RF70_Exclusao_Colaborador_Erro_500.md) | [RF70](Analise%20de%20requisitos.md#rf70) | Excluir colaborador sem erro de servidor. | Confirmar exclusão do colaborador id 3 retorna HTTP 500 e `Erro interno inesperado`. | Reprovado nas evidências | [BUG-031](Relatorio-de-Bugs.md#bug-031), em triagem |
| [CT-RF74](Cenario_Teste/CT-RF74_Temas_Prospeccao.md) | [RF74](Analise%20de%20requisitos.md#rf74) | A tela deve acompanhar a seleção de tema, mantendo os dados da listagem. | A gravação mostra a tela passando de escura para clara e retornando ao tema escuro. A listagem permanece visível. | Aprovado conforme o resumo da gravação | — |
| [CT-RF75](Cenario_Teste/CT-RF75_Detalhes_Lead_Cancelamento.md) | [RF75](Analise%20de%20requisitos.md#rf75) | O sistema deve carregar os dados do lead e fechar a janela ao cancelar, sem enviar uma gravação da alteração. | Os dados do lead de código 3 são carregados, incluindo estágio Fechado, contato e observação. Após a alteração no telefone, Cancelar fecha a janela e retorna à listagem. Não há chamada de salvamento na linha do tempo. | Aprovado conforme o resumo da gravação | — |
| [CT-RF76](Cenario_Teste/CT-RF76_Exclusao_Leads_Confirmacao.md) | [RF76](Analise%20de%20requisitos.md#rf76) | Cada confirmação deve excluir o lead selecionado e atualizar a listagem e o total de registros. | Os leads de códigos 3 e 4 deixam de aparecer após as confirmações. O total exibido diminui de 8 para 7 e depois para 6. | Aprovado conforme o resumo da gravação | — |
| [CT-RF77](Cenario_Teste/CT-RF77_Cadastro_Lead_Novo_Contato.md) | [RF77](Analise%20de%20requisitos.md#rf77) | O lead deve ser criado no estágio Novo Contato e aparecer na listagem. | O lead de teste é criado com o estágio NOVO_CONTATO, recebe código 11 e aparece na listagem. O total passa de 6 para 7, e o indicador Novo Contato passa de 2 para 3. | Aprovado conforme o resumo da gravação | — |
| [CT-RF78](Cenario_Teste/CT-RF78_Cadastro_Lead_Interessado.md) | [RF78](Analise%20de%20requisitos.md#rf78) | O lead deve ser criado no estágio Interessado e aparecer na listagem. | O cadastro retorna código 12 e o lead aparece na listagem com a identificação Interessado. | Aprovado conforme o resumo da gravação | — |
| [CT-RF79](Cenario_Teste/CT-RF79_Cadastro_Lead_Aula_Experimental.md) | [RF79](Analise%20de%20requisitos.md#rf79) | O lead deve ser criado com o estágio Fez Aula Experimental e aparecer na listagem. | O lead é criado com código 14 e estágio FEZ_AULA_EXP. A linha correspondente aparece ao final, e o total de leads passa de 9 para 10. | Aprovado conforme o resumo da gravação | — |
| [CT-RF80](Cenario_Teste/CT-RF80_Cadastro_Lead_Proposta.md) | [RF80](Analise%20de%20requisitos.md#rf80) | O lead deve ser criado no estágio Proposta e aparecer na listagem. | O cadastro retorna código 15 e o registro aparece na listagem com estágio Proposta. O total de leads passa de 10 para 11. | Aprovado conforme o resumo da gravação | — |
| [CT-RF81](Cenario_Teste/CT-RF81_Cadastro_Bandeira_Parcela_Listagem.md) | [RF81](Analise%20de%20requisitos.md#rf81) | A bandeira deve ser criada com a configuração de parcela e aparecer na listagem após o salvamento. | A API confirma a criação da bandeira de código 34 e da parcela, mas a consulta seguinte retorna [] e a interface continua exibindo Nenhuma bandeira encontrada. A criação da parcela tem retorno de sucesso; o fluxo completo apresenta erro na recuperação/exibição do cadastro. | Reprovado nas evidências resumidas | [BUG-035](Relatorio-de-Bugs.md#bug-035) |
| [CT-RF82](Cenario_Teste/CT-RF82_Tema_Escuro_Bandeiras.md) | [RF82](Analise%20de%20requisitos.md#rf82) | O tema selecionado deve ser aplicado de forma consistente ao fundo, aos painéis e aos textos da tela. | No tema Escuro, os painéis ficam escuros, mas o fundo principal continua claro. Os textos da área vazia da listagem apresentam baixa legibilidade visual. A descrição do Jam relata: Fundo com falta de cores e modo escuro incompleto. | Reprovado nas evidências resumidas | [BUG-036](Relatorio-de-Bugs.md#bug-036) |
| [CT-RF83](Cenario_Teste/CT-RF83_Cadastro_Lead_Apenas_Nome.md) | [RF83](Analise%20de%20requisitos.md#rf83) | Segundo o cenário identificado como bug pelo autor, o cadastro incompleto deveria ser bloqueado e os campos obrigatórios deveriam ser indicados. | O sistema aceita o envio sem bloqueio visível, cria o lead de código 19 e atualiza a listagem. O total de leads passa de 14 para 15. | Reprovado conforme o relato; regra de obrigatoriedade a confirmar | [BUG-037](Relatorio-de-Bugs.md#bug-037) |
| [CT-RF84](Cenario_Teste/CT-RF84_Cadastro_Lead_Fechado.md) | [RF84](Analise%20de%20requisitos.md#rf84) | O lead deve ser criado no estágio Fechado e aparecer na listagem. | A janela fecha após salvar, o total de leads passa de 12 para 13 e o registro testeFechado aparece com código 17 e identificação Fechado. | Aprovado conforme o resumo da gravação | — |
| [CT-RF85](Cenario_Teste/CT-RF85_Tema_Notificacoes_Prospeccao.md) | [RF85](Analise%20de%20requisitos.md#rf85) | Trocar o tema, gravar a escolha e abrir o painel de notificações. | Tema escuro e claro aplicados com POST usuario/tema (HTTP 200); painel de Notificações aberto sem pendências. | Aprovado conforme a gravação | Nenhum no fluxo avaliado |
| [CT-RF86](Cenario_Teste/CT-RF86_Busca_Leads_Prospeccao.md) | [RF86](Analise%20de%20requisitos.md#rf86) | Apresentar apenas os leads correspondentes e restaurar a lista ao limpar. | Termos digitados reduzem a lista (códigos 3 e 7; 4 e 10 com "tes"); campo vazio restaura os 7 leads. | Aprovado conforme a gravação | Nenhum no fluxo avaliado |
| [CT-RF87](Cenario_Teste/CT-RF87_Filtro_Estagio_Leads.md) | [RF87](Analise%20de%20requisitos.md#rf87) | Apresentar apenas os leads do estágio e restaurar a lista ao limpar. | Novo Contato lista os leads 7 e 8; Proposta lista o lead 4; Limpar restaura os 7 leads. | Aprovado conforme a gravação | Nenhum no fluxo avaliado |
| [CT-RF88](Cenario_Teste/CT-RF88_Cadastro_Lead_Prospeccao.md) | [RF88](Analise%20de%20requisitos.md#rf88) | Uma única criação e um único lead na listagem. | Lead 10 criado e listado (Leads 7 → 8); um clique gerou dois POST salvar-lead/1 (HTTP 200); segunda resposta não capturada. | A validar — regra ou contexto pendente | Sem defeito confirmado |
| [CT-RF89](Cenario_Teste/CT-RF89_Telefone_Lead_Sem_Validacao.md) | [RF89](Analise%20de%20requisitos.md#rf89) | Rejeitar telefone com tamanho ou formato inválido. | Telefone de 30 dígitos aceito e gravado (lead 10), sem máscara nem mensagem. | Reprovado nas evidências | [BUG-038](Relatorio-de-Bugs.md#bug-038), em triagem |
| [CT-RF90](Cenario_Teste/CT-RF90_Edicao_Lead_Prospeccao.md) | [RF90](Analise%20de%20requisitos.md#rf90) | Abrir o lead, gravar a alteração sem erro e refletir na lista. | Lead 10 aberto pela lupa; nome alterado para "testetete"; POST atualizar-lead/1 com HTTP 200; listagem atualizada. | Aprovado conforme a gravação | Nenhum no fluxo avaliado |
| [CT-RF91](Cenario_Teste/CT-RF91_Filtros_Contas_Pagar.md) | [RF91](Analise%20de%20requisitos.md#rf91) | Apresentar apenas as contas que atendem aos critérios. | Filtros combinados deixam a lista vazia (0 contas); resultado compatível, sem dado de controle. | A validar — regra ou contexto pendente | Sem defeito confirmado |
| [CT-RF92](Cenario_Teste/CT-RF92_Cadastro_Conta_Colaborador_Sem_Colaborador.md) | [RF92](Analise%20de%20requisitos.md#rf92) | Exigir o colaborador e impedir a gravação sem ele. | Conta Pagto. Colaborador gravada (HTTP 201) sem colaborador e listada com "-". | Reprovado nas evidências | [BUG-039](Relatorio-de-Bugs.md#bug-039), em triagem |
| [CT-RF93](Cenario_Teste/CT-RF93_Busca_Colaborador_Conta_Pagar.md) | [RF93](Analise%20de%20requisitos.md#rf93) | Listar, permitir seleção e informar resultado vazio. | Busca "sds" devolve lista vazia, sem mensagem; seleção não exercitada. | A validar — regra ou contexto pendente | Sem defeito confirmado |
| [CT-RF94](Cenario_Teste/CT-RF94_Visualizacao_Conta_Pagar.md) | [RF94](Analise%20de%20requisitos.md#rf94) | Apresentar os dados da conta e permitir fechar. | Modal da conta 29 apresenta os dados gravados; tipo exibido como PAG_COLABORADOR. | Aprovado conforme a gravação | Nenhum no fluxo avaliado |
| [CT-RF95](Cenario_Teste/CT-RF95_Exclusao_Conta_Pagar.md) | [RF95](Analise%20de%20requisitos.md#rf95) | Confirmar, excluir sem erro e atualizar a lista. | Confirmação, deletar-conta-pagar (HTTP 200) e listagem sem a conta 29. | Aprovado conforme a gravação | Nenhum no fluxo avaliado |
| [CT-RF96](Cenario_Teste/CT-RF96_Variaveis_Preview_Modelo_Contrato.md) | [RF96](Analise%20de%20requisitos.md#rf96) | Inserir variáveis e substituí-las na pré-visualização. | Variáveis inseridas e pré-visualização com dados de exemplo e negrito preservado. | Aprovado conforme a gravação | Nenhum no fluxo avaliado |
| [CT-RF97](Cenario_Teste/CT-RF97_Cadastro_Modelo_Contrato.md) | [RF97](Analise%20de%20requisitos.md#rf97) | Criar o modelo e devolvê-lo na lista. | POST salvar (HTTP 201) e lista do servidor com o modelo de id 15. | Aprovado conforme a gravação | Nenhum no fluxo avaliado |
| [CT-RF98](Cenario_Teste/CT-RF98_Listagem_Modelos_Contrato_Vazia.md) | [RF98](Analise%20de%20requisitos.md#rf98) | Uma linha por modelo, inclusive o recém-criado. | Servidor devolve 15 modelos; tabela mostra só o cabeçalho, sem linhas nem mensagem. | Reprovado nas evidências | [BUG-040](Relatorio-de-Bugs.md#bug-040), em triagem |
| [CT-RF99](Cenario_Teste/CT-RF99_Filtros_Planos.md) | [RF99](Analise%20de%20requisitos.md#rf99) | Apresentar apenas os planos correspondentes e restaurar a lista. | Código "7" lista os planos 37, 7 e 67; nome "a" lista planos aba e Aba; lista completa ao limpar. | Aprovado conforme a gravação | Nenhum no fluxo avaliado |
| [CT-RF100](Cenario_Teste/CT-RF100_Tema_Notificacoes_Planos.md) | [RF100](Analise%20de%20requisitos.md#rf100) | Trocar o tema, gravar a escolha e abrir as notificações. | Tema escuro/claro com POST usuario/tema (HTTP 200); notificações abertas sem pendências. | Aprovado conforme a gravação | Nenhum no fluxo avaliado |
| [CT-RF101](Cenario_Teste/CT-RF101_Cadastro_Plano.md) | [RF101](Analise%20de%20requisitos.md#rf101) | Criar o plano e atualizar o contador. | plano/salvar com HTTP 200 e id 66; Planos 40 → 41. | Aprovado conforme a gravação | Nenhum no fluxo avaliado |
| [CT-RF102](Cenario_Teste/CT-RF102_Contador_Ativos_Planos.md) | [RF102](Analise%20de%20requisitos.md#rf102) | Ativos conta apenas planos ativos. | Ativos 29 → 30 ao cadastrar plano inativo e 30 → 31 ao editar plano inativo. | Reprovado nas evidências | [BUG-041](Relatorio-de-Bugs.md#bug-041), em triagem |
| [CT-RF103](Cenario_Teste/CT-RF103_Edicao_Plano.md) | [RF103](Analise%20de%20requisitos.md#rf103) | Abrir, gravar a alteração sem erro e atualizar a lista. | Plano 41 aberto; plano/update com HTTP 200 e verifica_erro false; lista recarregada. | Aprovado conforme a gravação | Nenhum no fluxo avaliado |
| [CT-RF104](Cenario_Teste/CT-RF104_Filtros_Tipos_Pagamento.md) | [RF104](Analise%20de%20requisitos.md#rf104) | Apresentar apenas os tipos que atendem aos critérios. | Seletores e Buscar acionados sem requisição de listagem; listagem inalterada com 16 tipos. | A validar — regra ou contexto pendente | Sem defeito confirmado |
| [CT-RF105](Cenario_Teste/CT-RF105_Cadastro_Tipo_Pagamento_Status.md) | [RF105](Analise%20de%20requisitos.md#rf105) | Gravar o status e refletir Ativo e Inativo na listagem e nos cartões. | Criação com HTTP 201, mas Status Ativo não enviado; Ativos permanece 0 e todos aparecem Inativo. | Reprovado nas evidências | [BUG-042](Relatorio-de-Bugs.md#bug-042), em triagem |
| [CT-RF106](Cenario_Teste/CT-RF106_Edicao_Tipo_Pagamento.md) | [RF106](Analise%20de%20requisitos.md#rf106) | Salvar sem erro e atualizar listagem e cartões. | Edição com HTTP 200; Dinheiro exibe Via gateway Não; cartão Via gateway 6 → 5. | Aprovado conforme a gravação | Nenhum no fluxo avaliado |
| [CT-RF107](Cenario_Teste/CT-RF107_Exclusao_Tipo_Pagamento_Em_Uso.md) | [RF107](Analise%20de%20requisitos.md#rf107) | Impedir com mensagem clara, código compatível e sem expor o banco. | Exclusão de tipos em uso: HTTP 404 com erro SQL; tela com mensagem genérica; Total 17. | Reprovado nas evidências | [BUG-043](Relatorio-de-Bugs.md#bug-043), em triagem |
| [CT-RF108](Cenario_Teste/CT-RF108_Tema_Notificacoes_Tipos_Pagamento.md) | [RF108](Analise%20de%20requisitos.md#rf108) | Aplicar o tema escolhido e exibir o estado das notificações. | Tema Escuro aplicado, notificações vazias e retorno a Claro; seis POST tema HTTP 200. | Aprovado conforme a gravação | Nenhum no fluxo avaliado |
| [CT-RF109](Cenario_Teste/CT-RF109_Modelo_Ficha_Sem_Nome.md) | [RF109](Analise%20de%20requisitos.md#rf109) | O sistema exibe um aviso de nome obrigatório, mantém o formulário disponível para correção e não cria um modelo. | Aviso “Informe o nome do modelo.”. Modal permaneceu aberto após Entendi, sem requisição capturada. | Aprovado conforme a gravação | Nenhum no fluxo avaliado |
| [CT-RF110](Cenario_Teste/CT-RF110_Cancelar_Cadastro_Modelo_Ficha.md) | [RF110](Analise%20de%20requisitos.md#rf110) | Cancelar fecha o formulário e mantém a listagem e a contagem, sem criar o modelo informado. | Cancelar fechou o modal preenchido e manteve 0 registros, sem requisição capturada. | Aprovado conforme a gravação | Nenhum no fluxo avaliado |
| [CT-RF111](Cenario_Teste/CT-RF111_Busca_Modelo_Ficha_Codigo_Inexistente.md) | [RF111](Analise%20de%20requisitos.md#rf111) | A pesquisa pelo código ausente exibe a mensagem de lista vazia e 0 registros, mesmo com outros modelos disponíveis. | Busca por 989898 exibiu estado vazio. GET retornou HTTP 200 com `[]`. | A validar — regra ou contexto pendente | Sem defeito confirmado |
| [CT-RF112](Cenario_Teste/CT-RF112_Busca_Modelo_Ficha_Titulo_Inexistente.md) | [RF112](Analise%20de%20requisitos.md#rf112) | O carregamento termina e a busca pelo título inexistente exibe o estado vazio com 0 registros. | Título PEDRO-01 exibiu carregamento e estado vazio. GET retornou HTTP 200 com `[]`. | A validar — regra ou contexto pendente | Sem defeito confirmado |
| [CT-RF113](Cenario_Teste/CT-RF113_Busca_Modelo_Ficha_Filtros_Combinados.md) | [RF113](Analise%20de%20requisitos.md#rf113) | Como critério de QA, a pesquisa lista a interseção dos três filtros. Uma combinação sem correspondência mostra a mensagem de estado vazio com 0 registros. | Três filtros preenchidos, 0 registros. GET sem parâmetros na URL retornou HTTP 200 com `[]`. | A validar — regra ou contexto pendente | Sem defeito confirmado |
| [CT-RF114](Cenario_Teste/CT-RF114_Limpeza_Filtros_Modelos_Ficha.md) | [RF114](Analise%20de%20requisitos.md#rf114) | Os três campos voltam a ficar vazios, com seus textos de indicação, e a ação de busca continua disponível. | Criador, Título e Código foram limpos manualmente e Buscar permaneceu disponível. | Aprovado conforme a gravação | Nenhum no fluxo avaliado |
| [CT-RF115](Cenario_Teste/CT-RF115_Nova_Busca_Modelos_Ficha_Sem_Filtros.md) | [RF115](Analise%20de%20requisitos.md#rf115) | Após a nova pesquisa, os registros padrão reaparecem, a contagem é atualizada e os campos permanecem em branco. | Dois cliques em Buscar com campos vazios geraram HTTP 200 com `[]`. A lista permaneceu vazia. | A validar — regra ou contexto pendente | Sem defeito confirmado |
| [CT-RF116](Cenario_Teste/CT-RF116_Configuracoes_Dias_Ausencia_Vazio.md) | [RF116](Analise%20de%20requisitos.md#rf116) | Se o campo for obrigatório, o sistema impede o salvamento e preserva o valor anterior. Se o campo for opcional, aplica o padrão definido e informa como tratou a entrada vazia. | Campo vazio convertido em 0, com HTTP 200. A recarga e a consulta confirmaram 0. | A validar — regra ou contexto pendente | Sem defeito confirmado |
| [CT-RF117](Cenario_Teste/CT-RF117_Configuracoes_Cancelar_Alteracao.md) | [RF117](Analise%20de%20requisitos.md#rf117) | Cancelar leva à Página Inicial e descarta a edição. Ao voltar a Configurações, o valor salvo permanece. | Cancelar levou à Página Inicial. O GET ao reabrir Configurações confirmou o valor original 1100. | Aprovado conforme a gravação | Nenhum no fluxo avaliado |
| [CT-RF118](Cenario_Teste/CT-RF118_Configuracoes_Trabalha_Com_Turmas.md) | [RF118](Analise%20de%20requisitos.md#rf118) | Cada valor salvo permanece no seletor após recarga e a consulta devolve o mesmo valor para `usa_turmas`. | Sim → Não → Sim. Os dois POST e os GET após recarga confirmaram os valores de `usa_turmas`. | Aprovado conforme a gravação | Nenhum no fluxo avaliado |
| [CT-RF119](Cenario_Teste/CT-RF119_Configuracoes_Academia_Marcada_Box.md) | [RF119](Analise%20de%20requisitos.md#rf119) | O seletor e o cartão SifitBox acompanham o estado persistido. O item SifitBox aparece no menu Principal em Sim e deixa de aparecer em Não. | Não → Sim → Não. Seletor, cartão SifitBox e menu Principal acompanharam o estado após recarga. | Aprovado conforme a gravação | Nenhum no fluxo avaliado |
| [CT-RF120](Cenario_Teste/CT-RF120_Configuracoes_Acesso_Desktop.md) | [RF120](Analise%20de%20requisitos.md#rf120) | O estado selecionado fica salvo em ambos os sentidos e o cartão Desktop mostra o valor carregado. | Não → Sim → Não. A API, o seletor e o cartão Desktop refletiram o valor salvo nas duas recargas. | Aprovado conforme a gravação | Nenhum no fluxo avaliado |
| [CT-RF121](Cenario_Teste/CT-RF121_Cadastro_Modelo_Ficha_Erro_500.md) | [RF121](Analise%20de%20requisitos.md#rf121) | O cadastro é concluído com o personal selecionado, a interface confirma a criação e o novo modelo pode ser localizado após recarga. | Cadastro preenchido retornou HTTP 500. A interface exibiu “Erro ao salvar modelo.” | Reprovado nas evidências | [BUG-045](Relatorio-de-Bugs.md#bug-045), em triagem |
| [CT-RF122](Cenario_Teste/CT-RF122_Resultados_IA_Filtro_90_Dias.md) | [RF122](Analise%20de%20requisitos.md#rf122) | O filtro selecionado é destacado. Cartões e linha do tempo acompanham o período consultado, e voltar aos 90 dias restaura os resultados desse período. | Cartões e linha do tempo acompanharam a troca de 7, 30 e 90 dias. Os resultados de 90 dias se repetiram. | Aprovado conforme a gravação | Nenhum no fluxo avaliado |
| [CT-RF123](Cenario_Teste/CT-RF123_Central_Resultados_IA_Execucao_Evasao.md) | [RF123](Analise%20de%20requisitos.md#rf123) | A Central é atualizada após a execução e o mesmo registro aparece em Resultados IA no filtro que inclui a data da execução. | A Central passou a mostrar 00:55. A linha do tempo de Hoje e o resumo de Resultados IA incluíram essa execução. | Aprovado conforme a gravação | Nenhum no fluxo avaliado |
| [CT-RF124](Cenario_Teste/CT-RF124_Configuracoes_Abas_Biometria_Senha.md) | [RF124](Analise%20de%20requisitos.md#rf124) | Todas as abas carregam o painel selecionado. O valor da senha configurada vem mascarado ao abrir Biometria. | A navegação funcionou. A aba Biometria exibiu o valor do campo Senha sem mascaramento. | Reprovado nas evidências | [BUG-046](Relatorio-de-Bugs.md#bug-046), em triagem |
| [CT-RF125](Cenario_Teste/CT-RF125_Configuracoes_Salvar_Dias_Ausencia_Valido.md) | [RF125](Analise%20de%20requisitos.md#rf125) | O valor 15 é salvo e exibido após recarregar. Ao restaurar o valor inicial, a próxima leitura apresenta o valor restaurado. | 15 foi salvo e confirmado após recarga. A segunda recarga confirmou a restauração de 1100. | Aprovado conforme a gravação | Nenhum no fluxo avaliado |
| [CT-RF126](Cenario_Teste/CT-RF126_Configuracoes_Dias_Ausencia_Negativo.md) | [RF126](Analise%20de%20requisitos.md#rf126) | O sistema rejeita valores negativos, orienta a correção do campo e preserva o valor anterior após recarga. | -1 foi aceito com HTTP 200 e confirmado na interface e no GET após recarga. | Reprovado nas evidências | [BUG-047](Relatorio-de-Bugs.md#bug-047), em triagem |
| [CT-RF127](Cenario_Teste/CT-RF127_Configuracoes_Dias_Ausencia_Texto.md) | [RF127](Analise%20de%20requisitos.md#rf127) | O campo permanece numérico. Se ficar vazio, aplica a regra de obrigatoriedade ou o padrão explícito aprovado pelo produto. | Letras não apareceram no campo. O salvamento com campo vazio enviou 0 e retornou HTTP 200. | A validar — regra ou contexto pendente | Sem defeito confirmado |
| [CT-RF128](Cenario_Teste/CT-RF128_Central_Configuracao_Risco_Evasao_Cancelar.md) | [RF128](Analise%20de%20requisitos.md#rf128) | Configurar abre o painel correto. Cancelar fecha a configuração e preserva o estado da automação. | Configurar abriu Risco de Evasão e Cancelar fechou o painel. O cartão continuou ativo. | Aprovado conforme a gravação | Nenhum no fluxo avaliado |
| [CT-RF129](Cenario_Teste/CT-RF129_Central_Aniversariantes_Previa_Risco.md) | [RF129](Analise%20de%20requisitos.md#rf129) | O painel de Aniversariantes abre e a prévia apresenta conteúdo de aniversários, coerente com a automação selecionada. | O painel Aniversariantes abriu corretamente, mas a prévia exibiu dados de risco de evasão. | Reprovado nas evidências | [BUG-048](Relatorio-de-Bugs.md#bug-048), em triagem |
| [CT-RF130](Cenario_Teste/CT-RF130_Central_Recursos_Em_Desenvolvimento.md) | [RF130](Analise%20de%20requisitos.md#rf130) | Cada recurso apresenta Em desenvolvimento e permanece indisponível para configurar ou executar. | Os quatro recursos exibiram Em desenvolvimento. Os cliques não iniciaram navegação, configuração ou execução. | Aprovado conforme a gravação | Nenhum no fluxo avaliado |
| [CT-RF131](Cenario_Teste/CT-RF131_Resultados_IA_Filtro_Hoje.md) | [RF131](Analise%20de%20requisitos.md#rf131) | Hoje é destacado e a API retorna o período de um dia. A tela reflete os dados desse recorte. | Hoje consultou um dia e o total de aniversariantes passou de 2 para 0, como na resposta. | Aprovado conforme a gravação | Nenhum no fluxo avaliado |
| [CT-RF132](Cenario_Teste/CT-RF132_Resultados_IA_Filtro_7_Dias.md) | [RF132](Analise%20de%20requisitos.md#rf132) | Últimos 7 dias fica selecionado, a API retorna sete dias e a página exibe o conjunto correspondente. | Ao voltar de Hoje para Últimos 7 dias, o cartão Aniversariantes passou de 0 para 2. | Aprovado conforme a gravação | Nenhum no fluxo avaliado |
| [CT-RF133](Cenario_Teste/CT-RF133_Resultados_IA_Filtro_30_Dias.md) | [RF133](Analise%20de%20requisitos.md#rf133) | O período de 30 dias é destacado, cartões e linha do tempo mudam de acordo com a resposta, e reaplicar o filtro repete os resultados em uma base estável. | O filtro de 30 dias apresentou 12 automações, 12 relatórios e 6 aniversariantes nas duas seleções. | Aprovado conforme a gravação | Nenhum no fluxo avaliado |

---

## 🐞 3. Resumo dos bugs reportados

| ID | Funcionalidade | Severidade | Prioridade | Status |
| --- | --- | --- | --- | --- |
| [BUG-001](Relatorio-de-Bugs.md#bug-001--link-esqueci-minha-senha-não-executa-nenhuma-ação) | Início da recuperação de senha | Alta | Alta | Aberto; reteste pendente. |
| [BUG-002](Relatorio-de-Bugs.md#bug-002--perfil-com-dados-fictícios-campos-ausentes-e-layout-desconfigurado) | Dados e layout do perfil | Alta, proposta | Alta, proposta | Aberto; reteste pendente. |
| [BUG-003](Relatorio-de-Bugs.md#bug-003--filtros-combinados-da-página-clientes-não-restringem-a-listagem) | Filtros combinados de Clientes | Alta, proposta | Alta, proposta | Aberto; reteste pendente. |
| [BUG-004](Relatorio-de-Bugs.md#bug-004) | Exportar não oferece retorno visível no financeiro | Média, proposta | Média, proposta | Aberto; reteste pendente. |
| [BUG-005](Relatorio-de-Bugs.md#bug-005) | Contadores financeiros divergem das mensalidades acessíveis | Alta, proposta | Alta, proposta | Aberto; reteste pendente. |
| [BUG-006](Relatorio-de-Bugs.md#bug-006) | Seletor de período permite intervalo com datas invertidas | Média, proposta | Média, proposta | Aberto; reteste pendente. |
| [BUG-007](Relatorio-de-Bugs.md#bug-007) | Tema escuro reduz a legibilidade das tabelas de Box – Turmas | Média, proposta | Média, proposta | Aberto; reteste pendente. |
| [BUG-008](Relatorio-de-Bugs.md#bug-008) | Edição de modalidade não apresenta ação clara para salvar | Média, proposta | Média, proposta | Aberto; reteste pendente. |
| [BUG-009](Relatorio-de-Bugs.md#bug-009) | Exclusão de categoria retorna HTTP 500 e mensagem genérica | Média, proposta | Alta, proposta | Aberto; reteste pendente. |
| [BUG-010](Relatorio-de-Bugs.md#bug-010) | Cadastro de avaliação retorna HTTP 500 | Alta, proposta | Alta, proposta | Aberto; reteste pendente. |
| [BUG-011](Relatorio-de-Bugs.md#bug-011) | Campo Código do exercício não aceita digitação conforme o relato | Média, proposta | Média, proposta | Em triagem; confirmação e reteste pendentes. |
| [BUG-012](Relatorio-de-Bugs.md#bug-012) | Edição de exercício aumenta o total e mantém duas entradas | Média, proposta | Média, proposta | Em triagem; confirmação e reteste pendentes. |
| [BUG-013](Relatorio-de-Bugs.md#bug-013) | Campos obrigatórios vazios sem feedback de validação | Média, proposta | Alta, proposta | Em triagem; confirmação de persistência e reteste pendentes. |
| [BUG-014](Relatorio-de-Bugs.md#bug-014) | Vídeo rejeitado no campo Imagem sem feedback | Baixa, proposta | Média, proposta | Em triagem; MIME e reteste pendentes. |
| [BUG-015](Relatorio-de-Bugs.md#bug-015) | Imagem rejeitada no campo Vídeo sem feedback | Baixa, proposta | Média, proposta | Em triagem; MIME e reteste pendentes. |
| [BUG-016](Relatorio-de-Bugs.md#bug-016) | Exclusão de grupo muscular retorna HTTP 500 | Média, proposta | Alta, proposta | Em triagem; causa pendente. |
| [BUG-017](Relatorio-de-Bugs.md#bug-017) | Imagens dos grupos musculares retornam HTTP 422 | Média, proposta | Média, proposta | Em triagem; causa pendente. |
| [BUG-018](Relatorio-de-Bugs.md#bug-018) | Dashboard apresenta múltiplos HTTP 500 durante o carregamento | Alta, proposta | Alta, proposta | Em triagem; endpoints, repetição e causa pendentes. |
| [BUG-019](Relatorio-de-Bugs.md#bug-019) | Cadastro de objetivo de treino retorna HTTP 500 | Alta, proposta | Alta, proposta | Em triagem; causa e reteste pendentes. |
| [BUG-020](Relatorio-de-Bugs.md#bug-020) | Cadastro de turma sem modalidade não apresenta retorno visível | Média, proposta | Alta, proposta | Em triagem; validação nativa e reteste pendentes. |
| [BUG-021](Relatorio-de-Bugs.md#bug-021) | Painel Pagar.me mantém Recebimentos e gráfico ao trocar o período | Média, proposta | Média, proposta | Em triagem; dados reais ou de demonstração e reteste pendentes. |
| [BUG-022](Relatorio-de-Bugs.md#bug-022) | Relatório de Contas a Receber exibe "----" em Valor a Receber | Alta, proposta | Alta, proposta | Em triagem; comparação com o módulo e reteste pendentes. |
| [BUG-023](Relatorio-de-Bugs.md#bug-023) | Relatórios de Avaliações, Clientes, Colaboradores e Caixas geram PDF vazio | Alta, proposta | Alta, proposta | Em triagem; causa e reteste pendentes. |
| [BUG-024](Relatorio-de-Bugs.md#bug-024) | Exclusão de grupo retorna HTTP 500 | Média, proposta | Alta, proposta | Em triagem; causa pendente. |
| [BUG-025](Relatorio-de-Bugs.md#bug-025) | Edição de grupo não persiste o campo status | Média, proposta | Alta, proposta | Em triagem; causa pendente. |
| [BUG-026](Relatorio-de-Bugs.md#bug-026) | Data de nascimento futura aceita na edição de colaborador | Média, proposta | Alta, proposta | Em triagem; confirmação e reteste pendentes. |
| [BUG-027](Relatorio-de-Bugs.md#bug-027) | Data de nascimento obrigatória não exigida na edição de colaborador | Média, proposta | Alta, proposta | Em triagem; confirmação e reteste pendentes. |
| [BUG-028](Relatorio-de-Bugs.md#bug-028) | Formato de CREF não validado no colaborador | Média, proposta | Média, proposta | Em triagem; regra e exemplos pendentes. |
| [BUG-029](Relatorio-de-Bugs.md#bug-029) | Edição de colaborador aceita campo obrigatório vazio | Média, proposta | Alta, proposta | Em triagem; campo exato e reteste pendentes. |
| [BUG-030](Relatorio-de-Bugs.md#bug-030) | Função duplicada aceita para o mesmo colaborador | Média, proposta | Média, proposta | Em triagem; causa e reteste pendentes. |
| [BUG-031](Relatorio-de-Bugs.md#bug-031) | Exclusão de colaborador retorna HTTP 500 | Média, proposta | Alta, proposta | Em triagem; causa pendente. |
| [BUG-032](Relatorio-de-Bugs.md#bug-032) | Cadastro de anamnese retorna HTTP 500 | Média, proposta | Alta, proposta | Em triagem; causa pendente. |
| [BUG-035](Relatorio-de-Bugs.md#bug-035) | Bandeira criada com parcela não aparece na listagem | Média, proposta | Alta, proposta | Em triagem; causa e reteste pendentes. |
| [BUG-036](Relatorio-de-Bugs.md#bug-036) | Tema escuro aplicado de forma incompleta em Bandeiras | Média, proposta | Média, proposta | Em triagem; causa e reteste pendentes. |
| [BUG-037](Relatorio-de-Bugs.md#bug-037) | Cadastro de lead aceito apenas com nome, com obrigatoriedade a confirmar | Média, proposta | Alta, proposta | Em triagem; obrigatoriedade a confirmar. |
| [BUG-038](Relatorio-de-Bugs.md#bug-038) | Telefone do lead aceita 30 dígitos sem máscara nem validação | Média, proposta | Média, proposta | Em triagem; regra do campo e reteste pendentes. |
| [BUG-039](Relatorio-de-Bugs.md#bug-039) | Conta a pagar a colaborador é cadastrada sem colaborador informado | Alta, proposta | Alta, proposta | Em triagem; regra do campo e reteste pendentes. |
| [BUG-040](Relatorio-de-Bugs.md#bug-040) | Listagem de modelos de contrato aparece vazia com 15 modelos retornados | Alta, proposta | Alta, proposta | Em triagem; causa de renderização e reteste pendentes. |
| [BUG-041](Relatorio-de-Bugs.md#bug-041) | Cartão Ativos de Planos aumenta ao cadastrar e editar planos inativos | Média, proposta | Média, proposta | Em triagem; regra do cartão e reteste pendentes. |
| [BUG-042](Relatorio-de-Bugs.md#bug-042) | Status do tipo de pagamento não é enviado nem refletido: todos aparecem Inativo | Média, proposta | Média, proposta | Em triagem; regra do status e reteste pendentes. |
| [BUG-043](Relatorio-de-Bugs.md#bug-043) | Exclusão de tipo de pagamento em uso retorna HTTP 404 com erro SQL e mensagem genérica | Média, proposta | Média, proposta | Em triagem; regra de exclusão e tratamento do erro pendentes. |
| [BUG-044](Relatorio-de-Bugs.md#bug-044) | Edição do tipo de resposta de pergunta de anamnese retorna HTTP 500 | Alta, proposta | Alta, proposta | Em triagem. Reteste após correção. |
| [BUG-045](Relatorio-de-Bugs.md#bug-045) | Cadastro de modelo de ficha com nome e personal retorna HTTP 500 | Alta, proposta | Alta, proposta | Em triagem. Reteste após correção. |
| [BUG-046](Relatorio-de-Bugs.md#bug-046) | Configurações de Biometria exibem senha sem mascaramento | Alta, proposta | Alta, proposta | Em triagem. Reteste após correção. |
| [BUG-047](Relatorio-de-Bugs.md#bug-047) | Configurações aceitam e persistem dias de ausência negativos | Média, proposta | Média, proposta | Em triagem. Reteste após correção. |
| [BUG-048](Relatorio-de-Bugs.md#bug-048) | Configuração de Aniversariantes exibe prévia de risco de evasão | Média, proposta | Média, proposta | Em triagem. Reteste após correção. |

As classificações propostas dependem de triagem. O BUG-003 mantém o resultado atribuído ao relato fornecido.

---

## 🔐 4. Ambientes identificados

### CT-RF01

| Item | Valor |
| --- | --- |
| Página gravada | https://sifitalfa.centrion.com.br/login |
| Navegador | Chrome 155.0.8059.85 |
| Sistema operacional | Windows 11 |
| Duração da gravação | 14 segundos |
| Autor do Jam | Leonardo Barbosa |
| Versão da aplicação | Não identificada nas informações consultadas. |

### CT-RF02_ERRO

| Item | Valor |
| --- | --- |
| Página afetada | https://sifit.centrion.com.br/profile, conforme Actions do Jam; Info apresenta `/configuracoes`. |
| Navegador / sistema | Chrome 155.0.8059.85 / Windows 11 (x86). |
| Janela da gravação | 1536 × 742; zoom não confirmado. A captura fornecida tem 1895 × 900 pixels e não estabelece o tamanho da janela do navegador. |
| Data / duração da gravação | 22/10/2026 às 21:45 BRT / aproximadamente 15 segundos. |
| Autor do Jam | Leonardo Dos Santos Barbosa. |
| Versão da aplicação | Não confirmada. Os nomes de bundles no HTML não identificam, por si só, a versão funcional do sistema. |

O domínio do CT-RF02_ERRO é diferente do domínio `sifitalfa.centrion.com.br` do CT-RF01; resultados e condições de ambiente são registrados por caso.

### CT-RF03

| Item | Valor |
| --- | --- |
| Página afetada | Clientes; URL do frontend não confirmada. |
| Endpoint informado | `POST https://backendsifit.centrion.com.br/api/clientesPorNome/1`. |
| Empresa | `empresa_id: 1`, conforme o corpo simplificado informado. |
| Seleção relatada | Ativo + Inadimplente + Plano Hendreu + Marcelo Longo Zandonadi; em seguida, alteração da Situação para Adimplente. |
| Navegador / sistema / resolução / zoom | Não confirmados para esta execução; não foram herdados dos demais casos. |
| Data / duração / versão da aplicação | Não confirmadas. Os momentos aproximados informados não estabelecem a duração total da gravação. |
| Validação de IDs | Os exemplos `plano_id: 60` e `personal_id: 36` não têm correspondência confirmada. |
| Fonte do resultado | Relato técnico e duas capturas fornecidos; Jam referenciado sem inspeção direta do conteúdo nesta revisão. |

---

### CT-RF04_loginComSucesso

| Item | Valor |
| --- | --- |
| Página / destino | `https://sifit.centrion.com.br/login` → `https://sifit.centrion.com.br/dashboard`. |
| Navegador / sistema / janela | Chrome 157.0.8103.51 / Windows 11 (x86) / 1536 × 742. |
| Data / duração / autor | 13/11/2026 / aproximadamente 12 segundos / Leonardo Barbosa. |
| Dados de teste | Credenciais válidas utilizadas no Jam; valores omitidos. Manter conectado desmarcado nos quadros consultados. |
| Versão da aplicação / zoom / classificação do ambiente | Não informados nas evidências consultadas. |
| Fonte do resultado | Metadados, cronologia de ações e rede e seis quadros do vídeo consultados diretamente. |

---

### CT-RF05 a CT-RF20

| Item | Valor |
| --- | --- |
| Data / horário das gravações | 14/11/2026, aproximadamente 00:23–00:45 BRT. Horários por caso nos metadados. |
| Frontend / backend | https://sifit.centrion.com.br / https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.51 / Windows 11 (x86). |
| Tela informada / vídeo original | 1920 × 957 / 1918 × 956 pixels. |
| Mídias | 16 vídeos WebM originais, 39.490.598 bytes; duração total informada 234,499 segundos. Sem narração. |
| Versão / zoom / ambiente | Não confirmados. |
| Material da análise | Metadados, cronologia e quadros dos vídeos consultados na revisão anterior desta sessão; cópia local conferida por tamanho e hash. |
| Execução desta atualização | Documental: sem nova execução no Sifit, correção de código ou reteste. |

---

### CT-RF21

| Item | Registro |
| --- | --- |
| Página / API | https://sifit.centrion.com.br/avaliacoes / https://backendsifit.centrion.com.br |
| Data / duração | 15/11/2026, início às 15:07:51,265 BRT / 20,420 s. |
| Navegador / sistema / captura | Chrome 157.0.8103.51 / Windows 11 (x86) / 1536 × 742. |
| Dados | Aluno 3423 digitado sem confirmação pela busca; personal 7; funcionário 11; 15/11/2026 às 06:00. |
| Limites | Versão, zoom, classificação do ambiente, causa raiz e persistência não confirmados. |

### CT-RF22 a CT-RF28

| Item | Registro |
| --- | --- |
| Página / autor | https://sifit.centrion.com.br/exercicios / Bruno Madeira. |
| Navegador / sistema / janela | Edge 157.0.8103.80 / Windows 11 (x86) / 1912 × 960, conforme Info. |
| Data / duração | 15/11/2026; RF22: 15:25 / 5 s; RF23: 15:40 / 6 s; RF24: 15:38 / 9 s; RF25: 15:35 / 5 s; RF26: 16:11 / 4 s; RF27: 16:08 / 7 s; RF28: 16:07 / 7 s; durações aproximadas. |
| Material e limites | RF22: relato, imagem inicial e Info. RF23–25: quadros, Info e Network, com resumo e cronologia locais. RF26–28: quadros e Info, sem confirmação de MIME, persistência ou resposta detalhada da API. Sem cópia dos vídeos, inspeção de código ou nova execução. |

### CT-RF29

| Item | Registro |
| --- | --- |
| Página / backend | https://sifit.centrion.com.br/grupos-musculares / https://backendsifit.centrion.com.br. |
| Navegador / sistema / janela | Chrome 157.0.8103.78 / Windows (x86) 11 / 1920 × 911, conforme Info. |
| Data / duração | 15/11/2026 às 15h56 BRT; 2 min 3 s. |
| Rede | Rápida, mais de 10 Mbps, latência de 50 ms, conforme Info. |
| Servidor | `x-powered-by: PHP/8.2.35`, `servidor: hcdn`, `plataforma: hospedagem`. |
| Material e limites | Painéis Informações, Rede e Console do Jam lidos diretamente, com cabeçalhos e corpo das duas requisições de exclusão, e quadros de 1:18 e 1:21. Sem logs do servidor, acesso ao banco, inspeção de código ou nova execução. |

### CT-RF30 a CT-RF33

| Item | Registro |
| --- | --- |
| Página / backend | https://sifit.centrion.com.br/grupos-musculares / https://backendsifit.centrion.com.br. |
| Data / duração | 15/11/2026 às 15h56 BRT; 2 min 3 s; a mesma gravação de CT-RF29, com navegador, sistema e janela idênticos. |
| Material e limites | CT-RF30: lista de rede filtrada por erros, cronologia e quadros de 0:20, 0:55, 1:18, 1:21, 1:45 e 2:00; os cabeçalhos de resposta das imagens foram descartados por inconsistência do painel. CT-RF31–33: cronologia do painel Console e quadros de 0:15, 0:20, 0:48, 0:55, 1:45 e 2:00; a cronologia não registra as requisições de criação, atualização e consulta com código de status. Sem pasta local de evidências, inspeção de código ou nova execução. |

### CT-RF34

| Item | Registro |
| --- | --- |
| Página / autor | https://sifit.centrion.com.br/dashboard / Bruno Madeira. |
| Navegador / sistema / janela | Edge 157.0.8103.80 / Windows 11 (x86) / 1912 × 960, conforme Info. |
| Data / duração | 15/11/2026, 17:23 BRT / aproximadamente 4 s. |
| Material e limites | Quadros, Info e Network. Há 23 eventos visíveis e múltiplos HTTP 500; endpoints completos, corpos, logs, componentes de origem e causa não foram confirmados. |


### CT-RF35

| Item | Registro |
| --- | --- |
| Página / API | https://sifit.centrion.com.br/objetivos-treino / https://backendsifit.centrion.com.br |
| Data / duração | 15/11/2026, 18:13 BRT / 1 min 12 s. |
| Navegador / sistema / janela | Chrome 157.0.8103.78 / Windows (x86) 11 / 1920 × 911, conforme Info; autor do Jam: Gustavo Pelissari Oenning. |
| Dados | Nome Gustavo e descrição Gustavo 45254#@v; base sem objetivos cadastrados; usuário exibido Jair. |
| Material e limites | Painéis Info, Console, Network e Actions do Jam, cabeçalhos de resposta e quadros do vídeo, com pasta local de evidências. Corpo da requisição e da resposta indisponíveis no Jam; sem inspeção de código ou nova execução. |


### CT-RF38

| Item | Registro |
| --- | --- |
| Página / API | https://sifit.centrion.com.br/categorias-exercicios-crossfit / https://backendsifit.centrion.com.br |
| Data / duração | 15/11/2026, 18:41 BRT / 37 s. |
| Navegador / sistema / janela | Chrome 157.0.8103.78 / Windows (x86) 11 / 1920 × 911, conforme Info; autor do Jam: Gustavo Pelissari Oenning. |
| Dados | Base com oito categorias (códigos 1 a 8); nome "teste"; texto "qwdas" digitado no campo Código; usuário exibido Jair. |
| Material e limites | Painéis Info, Console, Network e Actions do Jam, corpo da requisição e da resposta de criação e quadros do vídeo, com pasta local de evidências. Filtros sem requisição de rede; persistência após recarga, regra do campo Código e contrato dos cartões não verificados; sem inspeção de código ou nova execução. |

### CT-RF39 a CT-RF41

| Item | Registro |
| --- | --- |
| Página / API | https://sifit.centrion.com.br/sifitbox/turmas / https://backendsifit.centrion.com.br |
| Data / duração | 15/11/2026, 18:51 BRT / 1 min 39 s; uma única gravação cobre os três casos. |
| Navegador / sistema / janela | Chrome 157.0.8103.78 / Windows (x86) 11 / 1920 × 911, conforme Info; autor do Jam: Gustavo Pelissari Oenning. |
| Dados | Três modalidades e quatro turmas existentes; modalidade "teste" criada; usuário exibido Jair. |
| Material e limites | Painéis Info, Console, Network e Actions do Jam, corpos de requisições e respostas selecionadas e quadros do vídeo, com uma pasta local de evidências por caso. Corpos das exclusões, filtro "Inativo", envio válido de turma e persistência não verificados; sem inspeção de código ou nova execução. |

### CT-RF42 a CT-RF45

| Item | Registro |
| --- | --- |
| Página / API | https://sifit.centrion.com.br/pagarme / https://backendsifit.centrion.com.br |
| Data / duração | 15/11/2026, 19:06 BRT / 1 min 11 s; uma única gravação cobre os casos do grupo. |
| Navegador / sistema / janela | Chrome 157.0.8103.78 / Windows (x86) 11 / 1920 × 911, conforme Info; autor do Jam: Gustavo Pelissari Oenning. |
| Material e limites | Painéis Info, Console, Network e Actions do Jam e quadros do vídeo, com uma pasta local de evidências por caso. Corpos de requisição e de resposta indisponíveis; resultado do saque, persistência das configurações e origem dos dados do painel não confirmados; sem inspeção de código ou nova execução. |

### CT-RF46 a CT-RF49

| Item | Registro |
| --- | --- |
| Página / API | https://sifit.centrion.com.br/despesas-fixas / https://backendsifit.centrion.com.br |
| Data / duração | 15/11/2026, 19:07 BRT / 52 s; uma única gravação cobre os casos do grupo. |
| Navegador / sistema / janela | Chrome 157.0.8103.78 / Windows (x86) 11 / 1920 × 911, conforme Info; autor do Jam: Gustavo Pelissari Oenning. |
| Material e limites | Painéis Info, Console, Network e Actions do Jam, corpos de requisições e respostas selecionadas e quadros do vídeo, com uma pasta local por caso. Corpo e resposta da segunda criação, filtragem local e persistência não confirmados; sem inspeção de código ou nova execução. |

### CT-RF50 a CT-RF56

| Item | Registro |
| --- | --- |
| Página / API | https://sifit.centrion.com.br/relatorios / https://backendsifit.centrion.com.br |
| Data / duração | 15/11/2026, 19:09 BRT / 58 s; uma única gravação cobre os casos do grupo. |
| Navegador / sistema / janela | Chrome 157.0.8103.78 / Windows (x86) 11 / 1920 × 911, conforme Info; autor do Jam: Gustavo Pelissari Oenning. |
| Material e limites | Painéis Info, Console e Network do Jam, quadros do vídeo e oito arquivos PDF baixados (três com conteúdo, cinco com 0 bytes), com uma pasta local por caso. A atividade do usuário não consta no Console do Jam; a correspondência dos arquivos vazios com os tipos é inferida pela ordem dos downloads; sem inspeção de código ou nova execução. |

### CT-RF57

| Item | Registro |
| --- | --- |
| Página / API | https://sifit.centrion.com.br/grupos / https://backendsifit.centrion.com.br |
| Data / duração | 15/11/2026, 21h03 BRT / 1 min 38 s. |
| Navegador / sistema / janela | Chrome 157.0.8103.78 / Windows (x86) 11 / 1920 × 911, conforme Info; autor do Jam: Eduardo Vergentino Malaquias. |
| Material e limites | Painéis Informações, Console e Rede do Jam, quadros do vídeo entre 0:00 e 1:38 e as duas requisições de exclusão com HTTP 500. O texto do diálogo de erro não foi confirmado visualmente; sem inspeção de código, acesso a logs ou nova execução. |

### CT-RF58

| Item | Registro |
| --- | --- |
| Página / API | https://sifit.centrion.com.br/grupos / https://backendsifit.centrion.com.br |
| Data / duração | 15/11/2026, 21h03 BRT / 1 min 38 s; mesma gravação do CT-RF57. |
| Navegador / sistema / janela | Chrome 157.0.8103.78 / Windows (x86) 11 / 1920 × 911, conforme Info; autor do Jam: Eduardo Vergentino Malaquias. |
| Material e limites | Painéis Informações, Console e Rede do Jam, eventos de clique entre 0:57 e 1:16 e as requisições de edição (`POST /api/edita/grupo/1`) e de consulta (`GET /api/grupos/1`, `POST /api/seleciona/grupo/1`) correspondentes às duas edições do grupo. Reteste alterando o status isoladamente de volta para "Ativo" e verificação em outros grupos não exercitados; sem inspeção de código, acesso a logs ou nova execução. |

### CT-RF59

| Item | Registro |
| --- | --- |
| Página / API | https://sifit.centrion.com.br/anamneses / https://backendsifit.centrion.com.br |
| Data / duração | 15/11/2026, 22h07 BRT / 1 min 28 s. |
| Navegador / sistema / janela | Chrome 157.0.8103.78 / Windows (x86) 11 / 1920 × 911, conforme Info; autor do Jam: Eduardo Vergentino Malaquias. |
| Material e limites | Painéis Informações, Console e Rede do Jam, eventos de clique e digitação entre 0:00 e 1:28 e as sete requisições com HTTP 500 (quatro em `POST /api/anamnese/aplicar/1`, três em `POST /api/anamnese/rascunho/1`), com corpos de requisição e resposta de duas tentativas representativas. Não foi confirmado se as tentativas de rascunho afetaram o mesmo registro ou criaram registros distintos; sem inspeção de código, acesso a logs ou nova execução. |

### CT-RF60

| Item | Registro |
| --- | --- |
| Página / API | https://sifit.centrion.com.br/anamnese/modelos / https://backendsifit.centrion.com.br |
| Data / duração | 15/11/2026, 23h34 BRT / 2 min 32 s. |
| Navegador / sistema / janela | Chrome 157.0.8103.78 / Windows (x86) 11 / 1920 × 911, conforme Info; autor do Jam: Eduardo Vergentino Malaquias. |
| Material e limites | Painéis Informações, Console e Rede do Jam, eventos de clique e digitação entre 0:00 e 2:32 e as quinze requisições aos endpoints `/api/modelos-anamnese/*`, todas com HTTP 200 ou 201. Os corpos de requisição e de resposta não foram capturados pelo Jam; sem inspeção de código, acesso a logs ou nova execução. |

### CT-RF61

| Item | Registro |
| --- | --- |
| Página / API | https://sifit.centrion.com.br/anamnese/categorias / https://backendsifit.centrion.com.br |
| Data / duração | 16/11/2026, 15h24 BRT / 1 min 35 s. |
| Navegador / sistema | Chrome 157.0.8103.78 / Windows 11, conforme Info; autor do Jam: Eduardo Vergentino Malaquias. |
| Material e limites | Painéis Informações, Console, Rede e Ações do Jam, eventos de clique e digitação entre 0:00 e 1:35 e as sete requisições aos endpoints `/api/categorias-anamnese/*`, todas com HTTP 200 ou 201. Sem inspeção de código, acesso a logs ou nova execução. |

### CT-RF62

| Item | Registro |
| --- | --- |
| Página / API | https://sifit.centrion.com.br/perguntas-anamnese / https://backendsifit.centrion.com.br |
| Data / duração | 16/11/2026, 15h57 BRT / 1 min 30 s. |
| Navegador / sistema | Chrome 157.0.8103.78 / Windows 11, conforme Info; autor do Jam: Eduardo Vergentino Malaquias. |
| Material e limites | Painéis Informações, Console, Rede e Ações do Jam, eventos de clique e digitação entre 0:00 e 1:30 e as dezenove requisições identificadas, incluindo as quatro requisições `POST /api/pergunta-anamnese/alterar/1`, todas com HTTP 500. Sem inspeção de código, acesso a logs ou nova execução. |

---
### CT-RF74 a CT-RF84

- Telas: Prospecção (CT-RF74–CT-RF80, CT-RF83 e CT-RF84) e Bandeiras de Cartão (CT-RF81 e CT-RF82).
- Data informada dos registros: 16/11/2026; sem horário, fuso, navegador, sistema, versão ou zoom nos resumos.
- Fonte desta integração: onze arquivos RESUMO.txt fornecidos, preservados nas pastas de evidências. Não houve consulta direta aos Jams nesta revisão.

---
### CT-RF85 a CT-RF90

| Item | Registro |
| --- | --- |
| Página / API | https://sifit.centrion.com.br/prospeccao / https://backendsifit.centrion.com.br |
| Data / duração | 15/11/2026, 21:52 BRT / 1 min 2 s; uma única gravação cobre os casos do grupo. |
| Navegador / sistema / janela | Chrome 157.0.8103.78 / Windows (x86) 11 / 1920 × 911, conforme Info; autor do Jam: Gustavo Pelissari Oenning. |
| Material e limites | Painéis Info, Console, Network e Actions do Jam, corpos de requisições e respostas selecionadas e quadros do vídeo, com uma pasta local por caso. Corpo e resposta da segunda criação, filtragem local e persistência não confirmados; quadros com e-mail digitado não foram incluídos; sem inspeção de código ou nova execução. |

### CT-RF91 a CT-RF95

| Item | Registro |
| --- | --- |
| Página / API | https://sifit.centrion.com.br/contas-pagar / https://backendsifit.centrion.com.br |
| Data / duração | 15/11/2026, 21:58 BRT / 1 min; uma única gravação cobre os casos do grupo. |
| Navegador / sistema / janela | Chrome 157.0.8103.78 / Windows (x86) 11 / 1920 × 911, conforme Info; autor do Jam: Gustavo Pelissari Oenning. |
| Material e limites | Painéis Info, Console, Network e Actions do Jam, corpos de requisições e respostas selecionadas e quadros do vídeo, com uma pasta local por caso. Resultado vazio dos filtros sem dados de controle; busca de colaborador sem resultado; sem inspeção de código ou nova execução. |

### CT-RF96 a CT-RF98

| Item | Registro |
| --- | --- |
| Página / API | https://sifit.centrion.com.br/modelos-contrato / https://backendsifit.centrion.com.br |
| Data / duração | 15/11/2026, 21:55 BRT / 50 s; uma única gravação cobre os casos do grupo. |
| Navegador / sistema / janela | Chrome 157.0.8103.78 / Windows (x86) 11 / 1920 × 855, conforme Info; autor do Jam: Gustavo Pelissari Oenning. |
| Material e limites | Painéis Info, Console, Network e Actions do Jam, resposta da lista de modelos e quadros do vídeo, com uma pasta local por caso. Corpo e resposta da criação indisponíveis; causa da tabela vazia não determinada; sem inspeção de código ou nova execução. |

### CT-RF99 a CT-RF103

| Item | Registro |
| --- | --- |
| Página / API | https://sifit.centrion.com.br/planos / https://backendsifit.centrion.com.br |
| Data / duração | 15/11/2026, 21:54 BRT / 1 min 10 s; uma única gravação cobre os casos do grupo. |
| Navegador / sistema / janela | Chrome 157.0.8103.78 / Windows (x86) 11 / 1920 × 855, conforme Info; autor do Jam: Gustavo Pelissari Oenning. |
| Material e limites | Painéis Info, Console, Network e Actions do Jam, corpos de requisições e respostas selecionadas e quadros do vídeo, com uma pasta local por caso. Regra de cálculo do cartão Ativos não informada; filtragem local e persistência não confirmadas; sem inspeção de código ou nova execução. |

### CT-RF104 a CT-RF108

| Item | Registro |
| --- | --- |
| Página / API | https://sifit.centrion.com.br/tipos-pagamento / https://backendsifit.centrion.com.br |
| Data / duração | 15/11/2026, 22:03 BRT / 1 min; uma única gravação cobre os casos do grupo. |
| Navegador / sistema / janela | Chrome 157.0.8103.78 / Windows (x86) 11 / 1920 × 855, conforme Info; autor do Jam: Gustavo Pelissari Oenning. |
| Material e limites | Painéis Info, Console, Network e Actions do Jam, corpos de requisições e respostas selecionadas e quadros do vídeo, com uma pasta local por caso. Filtros sem requisição de rede e sem valor registrado; status do novo tipo não visível nos quadros; exclusão de tipo sem uso não exercitada; sem inspeção de código ou nova execução. |

### Modelos de Ficha

| Item | Registro |
| --- | --- |
| Página / API | https://sifit.centrion.com.br/fichas-treino-modelo / https://backendsifit.centrion.com.br |
| Data / horário | 16/11/2026 entre 22:19:51 e 22:29:07 BRT. |
| Navegador / sistema / vídeo | Chrome 157.0.8103.79 / Windows (x86) 10 (identificação do Jam) / 1918 × 998 (vídeo). |
| Material e limites | Os resultados se baseiam nos vídeos, metadados e eventos capturados pelo Jam. Versão da aplicação e zoom a confirmar. |

### Configurações e Modelos de Ficha (CT-RF116–CT-RF121)

| Item | Definição |
| --- | --- |
| Página | https://sifit.centrion.com.br/configuracoes e https://sifit.centrion.com.br/fichas-treino-modelo |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema / vídeo | Chrome 157.0.8103.79 / Windows 10 (x86) / 1918 × 998. |
| Gravações | 16/11/2026 entre 22:03:53 e 22:18:52 BRT. |
| Dados e permissões | Conta com permissão para as operações. Registrar os valores iniciais das Configurações e restaurá-los após os testes. Para o cadastro, usar um modelo descartável e um personal de teste. |
| Preparação | Registrar estado inicial, ações e respostas da API. Usar recortes da interface e omitir dados de autenticação. |

### Inteligência e Configurações (CT-RF122–CT-RF127)

| Item | Definição |
| --- | --- |
| Páginas | https://sifit.centrion.com.br/inteligencia/resultados, https://sifit.centrion.com.br/inteligencia-automacao, https://sifit.centrion.com.br/configuracoes |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema / vídeo | Chrome 157.0.8103.79 / Windows 10 (x86) / 1918 × 998. |
| Gravações | 16/11/2026 entre 21:50:51 e 22:02:16 BRT. |
| Dados e permissões | Conta com permissão para as operações. Preparar resultados em períodos distintos e automação de teste autorizada. Em Configurações, usar credenciais fictícias e registrar o valor inicial dos campos. |
| Preparação | Registrar o estado inicial, os controles usados e as respostas relevantes. Excluir dados de integração e de autenticação dos recortes e da documentação. |

### Inteligência e Automação (CT-RF128–CT-RF133)

| Item | Definição |
| --- | --- |
| Páginas | https://sifit.centrion.com.br/inteligencia-automacao, https://sifit.centrion.com.br/inteligencia/resultados |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema / vídeo | Chrome 157.0.8103.79 / Windows 10 (x86) / 1918 × 998. |
| Gravações | 16/11/2026 entre 21:40:31 e 21:49:48 BRT. |
| Dados e permissões | Conta com acesso à Central e a Resultados IA. Usar automações de teste, estados iniciais conhecidos e resultados em períodos distintos. |
| Preparação | Registrar o estado inicial, os controles usados e as respostas relevantes. Excluir dados de integração e de autenticação dos recortes e da documentação. |

## 📸 5. Evidências e observações

| Evidência | Informação utilizada |
| --- | --- |
| [Jam — Erro no esqueci a senhas](https://jam.dev/c/0273b203-b999-493d-9919-2d143bc13301) | Eventos de clique entre aproximadamente 00:02 e 00:12, quadros do vídeo sem abertura do fluxo, 0 requisições registradas e 0 erros de console registrados. |
| [Google Drive — CT-RF01_Esqueci-senha](https://drive.google.com/file/d/1f6AqYunchDH4R9Yw1JpbyX9x28UQGcbo/view?usp=sharing) | Vídeo complementar fornecido pelo solicitante; metadados consultados, conteúdo não inspecionado nesta revisão. |
| [Captura — CT-RF02_ERRO](Evidencias/CT-RF02_ERRO/erro-na-tela.png) | Seções Usuário, Documentos e Endereço sem campos visíveis, imagem fora de proporção, “Edit profile” e About me com texto de demonstração. |
| [HTML — CT-RF02_ERRO](Evidencias/CT-RF02_ERRO/recorte-dom.html) | Recorte do DOM fornecido, incluindo “Hello Jesse”, “Jessica Jones” e tags de componentes sem controles nativos de entrada nos campos de cadastro. |
| [Jam — Tela de perfil do usuário com erro](https://jam.dev/c/c61241d5-bff5-4a0a-9684-991318f9b51c) | Info, Actions e quadro em 00:05 consultados. Navegações para `/profile` em 00:02 e 00:12; seções sem campos visíveis e barra horizontal no quadro consultado. |
| [Jam — Filtros de Clientes](https://jam.dev/c/657627ec-e7e2-455d-a505-9b2a26f44bf1) | Link fornecido, sem acesso direto ao conteúdo nesta revisão. Horários, endpoint, payload e volumes atribuídos à gravação foram registrados conforme o relato. |
| [Captura 1 — CT-RF03](Evidencias/CT-RF03_Filtros_Clientes/filtros-clientes-01.png) | Filtros com textos truncados, listagem e uma entrada XHR HTTP 200; painel com 26,9 kB transferidos e 185 kB de recursos. Não mostra payload ou URL completa. |
| [Captura 2 — CT-RF03](Evidencias/CT-RF03_Filtros_Clientes/filtros-clientes-02.png) | Filtros selecionados e listagem semelhante, com painel Network sem requisições listadas naquele instante. Não comprova ausência de chamadas em toda a execução. |
| [Índice e limites — CT-RF03](Evidencias/CT-RF03_Filtros_Clientes/README.md) | Origem das capturas, cronologia de rede informada e corpo simplificado transcrito do relato, sem autenticação. |
| [Jam — Login com sucesso](https://jam.dev/c/5e4a28be-4e80-43d3-9587-1b113723cc38) | Entrar em aproximadamente 00:06; `POST /api/login` e `POST /api/verifica-token-logado` HTTP 200; navegação para `/dashboard` e painel visível nos quadros seguintes. |
| [Índice e limites — CT-RF04_loginComSucesso](Evidencias/CT-RF04_loginComSucesso/README.md) | Resumo da gravação, ambiente, cronologia e limites da aprovação do login. |
| [Jam — CT-RF05: Teste senha incorreta](https://jam.dev/c/75f16436-7201-4de0-b191-1c4d0d63bfe8) e [Evidências](Evidencias/CT-RF05_Login_SenhaIncorreta/README.md) | 0:05–0:12: envio e mensagem de recusa. A linha do tempo registra POST /api/login com HTTP 200. HTTP 200 é o status da resposta da API; a recusa é demonstrada pela interface. O vídeo não valida bloqueio por tentativas ou outras regras de segurança. |
| [Jam — CT-RF06: Teste Usuário que não existe](https://jam.dev/c/b184e875-2cb1-4a01-b4dd-bc85b3741ff6) e [Evidências](Evidencias/CT-RF06_Login_UsuarioInexistente/README.md) | 0:08–0:12: POST /api/login retorna HTTP 200 e a interface permanece no login. A inexistência do usuário é o cenário declarado no título; não foi conferida no banco. A mensagem já está visível no início do vídeo e permanece após a nova tentativa. |
| [Jam — CT-RF07: botão de exporta sem função](https://jam.dev/c/1084cb18-cb3d-4b85-9c2f-ee431b59a06b) e [Evidências](Evidencias/CT-RF07_Exportacao_Financeiro/README.md) | 0:02–0:03: cinco cliques em Exportar. Nenhuma requisição de rede ou mensagem de console foi capturada nesse Jam. O vídeo não mostra o diretório de downloads; portanto, não comprova sozinho que nenhum arquivo foi gerado. A ausência de requisição também não exclui uma exportação feita no próprio navegador. |
| [Jam — CT-RF08: Valor sendo calculado errado](https://jam.dev/c/79b712ae-d9e0-4600-862f-fd3a278285ff) e [Evidências](Evidencias/CT-RF08_Calculo_Cobranca/README.md) | 0:04–0:08: comparação dos valores. 0:14–0:24: anotação do autor no campo da mensagem. R$ 350,00 + R$ 7,00 = R$ 357,00, mas os R$ 20,83 restantes podem corresponder a juros. A regra de cálculo e as configurações não foram fornecidas; não é possível afirmar que o total está incorreto. |
| [Jam — CT-RF09: Informa que tem 3 mensalidades e tem apenas 1.](https://jam.dev/c/1874d0b3-5c7c-4f28-85be-91750e20cbe1) e [Evidências](Evidencias/CT-RF09_Contagem_Mensalidades/README.md) | 0:01–0:05: Todos 3 com uma linha e rodapé 1–1 de 3. 0:10–0:19: +30 dias 2 com uma linha. Não foram inspecionados os corpos das respostas ou o banco. Os casos CT-RF09, CT-RF10 e CT-RF11 tratam de aspectos relacionados do mesmo modal. |
| [Jam — CT-RF10: Erro no filtro de mensalidade](https://jam.dev/c/3f78cf16-2c3b-48bc-8622-23b829debbec) e [Evidências](Evidencias/CT-RF10_Filtro_Mensalidades/README.md) | 0:00: clique em Até 7 dias 1 e POST /api/contas-receber/vencidas/1 com HTTP 200. 0:02–0:09: estado vazio. A evidência confirma a divergência visual. A causa técnica não foi investigada. Relacionado ao CT-RF09. |
| [Jam — CT-RF11: Erro nas métricas](https://jam.dev/c/4491c9e7-7e00-4063-91ce-8683e316df06) e [Evidências](Evidencias/CT-RF11_Metricas_Financeiro/README.md) | 0:01–0:12: troca dos filtros e comparação dos cartões. Foram capturadas chamadas financeiras com HTTP 200. Totais globais podem permanecer constantes por definição. Sem a regra de cada indicador, não é possível classificar toda permanência de valor como erro. A divergência de contagens está documentada nos itens 05 e 06. |
| [Jam — CT-RF12: Botões de datas sem função e sem atualização](https://jam.dev/c/93165ba3-3bfe-4dd5-9379-ab8db2d686ba) e [Evidências](Evidencias/CT-RF12_Periodo_Dashboard/README.md) | 0:04–0:08: seleção das datas. 0:10: intervalo invertido visível. No começo foram capturadas várias chamadas POST /api/dados-principais-home/1 com HTTP 200. A captura comprova o intervalo invertido. Indicadores constantes, isoladamente, não demonstram falha no cálculo; os botões de seta geraram requisições, portanto não se pode dizer que todos estavam sem função. |
| [Jam — CT-RF13: erro na numeração dos personais](https://jam.dev/c/69330ca9-ef19-4ece-918f-31a460628016) e [Evidências](Evidencias/CT-RF13_Codigos_Personais/README.md) | 0:01–0:13: total 4 e quatro linhas. GET /api/colaboradores-personais/1 com HTTP 200. Não foi demonstrada uma divergência entre o total e a quantidade listada. A numeração não sequencial por si só não confirma defeito. |
| [Jam — CT-RF14: falta de acessibilidade nas cores](https://jam.dev/c/6889db07-bed1-472b-8ec2-00402919cd65) e [Evidências](Evidencias/CT-RF14_Contraste_TemaEscuro/README.md) | 0:02: seleção de Escuro e POST /api/usuario/tema com HTTP 200. 0:02–0:09: perda de legibilidade nas tabelas. A observação é visual. Não foi medida a razão de contraste nem realizada uma auditoria formal de acessibilidade. |
| [Jam — CT-RF15: Sem botão para editar modalidades](https://jam.dev/c/951efaf8-bf32-44b0-b640-a2935a6b554a) e [Evidências](Evidencias/CT-RF15_Edicao_Modalidade/README.md) | 0:03–0:13: cliques no lápis, campos preenchidos e alternância entre Ativo e Inativo. Nenhuma chamada de atualização foi capturada. O título original diz “Sem botão para editar modalidades”, mas o lápis existe. A dificuldade demonstrada é concluir a edição; a gravação não prova ausência de toda alternativa de salvamento. |
| [Jam — CT-RF16: Botões apenas para desativar e não excluir! Apenas inativa e não exclui.](https://jam.dev/c/0f55f76a-cd31-4cee-93da-23c13b1ba637) e [Evidências](Evidencias/CT-RF16_Exclusao_Modalidade/README.md) | 0:02–0:15: ações de lixeira e novas consultas. 0:10–0:18: registros inativos ainda presentes. A inativação pode ser uma exclusão lógica prevista pelo sistema. É necessário confirmar a regra do produto antes de exigir exclusão definitiva. Nenhuma exclusão foi executada nesta revisão. |
| [Jam — CT-RF17: filtros corretos e funcionando](https://jam.dev/c/5e75e423-9c7e-43d7-aade-9b1a32c5e559) e [Evidências](Evidencias/CT-RF17_Filtros_Categorias/README.md) | 0:00–0:09: buscas por código. 0:11: limpeza. 0:14–0:17: pesquisa por nome. Resultado válido para os exemplos gravados. Não cobre combinações de filtros, valores inválidos, caracteres especiais ou paginação. |
| [Jam — CT-RF18: Teste de atualização funcionando](https://jam.dev/c/67664a98-2a4a-4134-91a9-7ca9b8aa9dbd) e [Evidências](Evidencias/CT-RF18_Atualizacao_Categoria/README.md) | 0:06: POST /api/categoria-exercicio-cross/atualizar com HTTP 200, seguido de GET /listar com HTTP 200. 0:08–0:11: nome atualizado na tabela. A atualização está demonstrada na própria gravação. Não houve novo teste de persistência após outra sessão ou novo login. |
| [Jam — CT-RF19: Erro a o deletar categoria](https://jam.dev/c/c5c78b3b-2865-4226-836f-bcb0a8fc612f) e [Evidências](Evidencias/CT-RF19_Exclusao_Categoria/README.md) | 0:02: POST /api/categoria-exercicio-cross/excluir retorna HTTP 500. 0:03–0:05: mensagem de erro. O erro e o endpoint estão registrados. Sem o corpo completo da resposta, logs do servidor ou banco, a causa do HTTP 500 não foi determinada. |
| [Jam — CT-RF20: Teste criação de nova categorias](https://jam.dev/c/b48ab94e-517d-48d6-8e46-70b18c033b8b) e [Evidências](Evidencias/CT-RF20_Criacao_Categoria/README.md) | 0:10: POST /api/categoria-exercicio-cross/criar retorna HTTP 201, seguido de GET /listar com HTTP 200. 0:11–0:15: novo registro visível. O teste demonstra criação no cenário gravado. Não cobre campos vazios, duplicidade ou validações de tamanho. |
| [Jam — CT-RF21: erro no cadastro da avaliação](https://jam.dev/c/2e5eca1f-7cd2-4ee3-854b-02ef4635955a) e [Evidências](Evidencias/CT-RF21_Cadastro_Avaliacao/README.md) | Em 00:12, evento 16: POST /api/avaliacao/adicionar-agendamento/1 HTTP 500 em 1363 ms, resposta “Erro interno inesperado.”. Em 00:14,748: alerta “Erro ao cadastrar Avaliação.”. Sem confirmação de persistência ou causa raiz. |
| [Jam — CT-RF22](https://jam.dev/c/2696db03-0a18-4c39-a75d-4987a43c04f0) e relato do testador | O testador relata não conseguir digitar o código. A imagem inicial confirma o campo Código no formulário Exercício; a reprodução integral, as teclas e o foco não foram confirmados. Não foram confirmadas a operação de criação/edição, a sequência de teclas ou a causa. A classificação se apoia no relato e na imagem inicial, sem análise de rede ou console. |
| [Jam — CT-RF23](https://jam.dev/c/32adfca3-489f-4a4b-a08d-933c1d1a3c32) e [Evidências](Evidencias/CT-RF23_Exclusao_Exercicio/README.md) | No quadro de aproximadamente 0:02, a biblioteca apresenta total 11 e o exercício Levantamento de Peso. No quadro final, em aproximadamente 0:06, esse registro não aparece e o total é 10. A lista continua contendo Levantamento de Peso 02, registro distinto. Não foram confirmados o diálogo de confirmação, a persistência após recarregar ou os efeitos sobre fichas de treino vinculadas. |
| [Jam — CT-RF24](https://jam.dev/c/073f70d6-4052-4e0f-a4bb-e9f37305d618) e [Evidências](Evidencias/CT-RF24_Edicao_Exercicio/README.md) | O Jam está identificado como teste de edição. Nos quadros intermediários, o formulário Exercício está aberto com código 16, o nome é preenchido e a biblioteca ao fundo indica total 10. No quadro final, o formulário fecha, o total é 11 e a lista contém Levantamento de Peso e Levantamento de Peso 02. O aumento e a coexistência dos nomes divergem do resultado esperado para uma edição. O acionamento inicial da edição e os identificadores das duas entradas não foram confirmados. A classificação considera o propósito declarado do Jam e a divergência visual; se a operação tiver sido criação, reavaliar a conclusão. |
| [Jam — CT-RF25](https://jam.dev/c/25c37a9b-e9bd-4e0c-adf1-4da528ae1d58) e [Evidências](Evidencias/CT-RF25_Envio_Exercicio_Imagem/README.md) | O quadro inicial consultado mostra o formulário Exercício preenchido com nome braço forte e uma miniatura na seção Imagem; a biblioteca ao fundo indica total 9. O quadro final mostra o formulário fechado, braço forte na lista e total 10. Esses quadros sustentam a criação com imagem selecionada, mas não demonstram a reabertura ou a visualização da imagem salva. Não foram confirmados nome, formato, tamanho ou conteúdo integral do arquivo, nem a persistência da imagem, sua recuperação ou a ausência de duplicação após nova submissão. |
| [Jam — CT-RF26](https://jam.dev/c/bc07ca5f-d3a9-45f6-84cb-12c0b562a211) | O formulário de exercício aparece com campos obrigatórios vazios. Após a tentativa de salvar, permanece aberto sem mensagem ou destaque de validação visível. A gravação não confirma resposta da API nem consulta posterior à biblioteca. |
| [Jam — CT-RF27](https://jam.dev/c/00740108-9a7d-4151-8723-171c89635567) | Após selecionar um vídeo no campo Imagem, não há arquivo anexado nem mensagem visível sobre tipo incompatível. Nome, extensão, MIME, tamanho e resposta da API não foram confirmados. |
| [Jam — CT-RF28](https://jam.dev/c/be9437a4-4fe9-4756-a2af-6777d3f43e25) | Após selecionar uma imagem no campo Vídeo, não há arquivo anexado nem mensagem visível sobre tipo incompatível. Nome, extensão, MIME, tamanho e resposta da API não foram confirmados. |
| [Jam — CT-RF29: Tela de Grupos Musculares](https://jam.dev/c/98008390-0040-475e-ba7b-7f1e72cc0b2e) | 1:17: acionamento do ícone de exclusão. 1:18: diálogo "Deseja deletar o Grupo?" com Cancelar e Confirmar, listagem com quatro registros. 1:19: `POST /api/deleta/grupo-muscular/1` retorna HTTP 500 em 990 ms, com `x-hcdn-request-id: d7f7c4b73412a500c5bdb50eb9be6ec1-asc-edge11`. 1:21: diálogo "Erro" / "Erro ao deletar Grupo" / "Fechar", com a listagem inalterada. 1:23: segunda tentativa no mesmo endpoint, HTTP 500 em 184 ms. Corpo das duas respostas: `{"verifica_erro": true, "mensagem": "Erro interno inesperado."}`. A evidência registra o erro e o endpoint; não distingue entre falha de infraestrutura, exceção não tratada e restrição de integridade. |
| [Jam — CT-RF30 a CT-RF33: Tela de Grupos Musculares](https://jam.dev/c/98008390-0040-475e-ba7b-7f1e72cc0b2e) | CT-RF30: quatro arquivos de imagem requisitados, doze ocorrências de HTTP 422 entre 0:06 e 1:59 e três de `net::ERR_ABORTED`. CT-RF31: cadastro de Tríceps (código 6), listagem de 3 para 4 registros. CT-RF32: alteração do tipo de membro com cartões recalculados. CT-RF33: filtros por tipo e por código com rodapé coerente. Causas das falhas não determinadas. |
| [Jam — CT-RF34](https://jam.dev/c/eea58e17-b62f-432b-97b2-b14c14bed555) e [Evidências](Evidencias/CT-RF34_Erro_Servidor_Excesso_Requisicoes/README.md) | O dashboard apresenta um diálogo de erro. A aba Network mostra 23 eventos visíveis: verificação de token HTTP 200, diversas chamadas GET/POST HTTP 500 e OPTIONS HTTP 204. Os endpoints aparecem truncados; a relação causal entre quantidade de chamadas e falhas não foi confirmada. |
| [Jam — CT-RF35: Objetivos Treino](https://jam.dev/c/1d474477-2411-4a81-b85c-74207402b783) e [Evidências](Evidencias/CT-RF35_Cadastro_Objetivo_Treino/README.md) | 1:01 e 1:02: `POST /api/objetivo-treino/salvar/1` com HTTP 500 (1077 ms e 856 ms), OPTIONS HTTP 204; 1:04: diálogo "Erro ao salvar objetivo"; 1:11: listagem sem registros. O campo Código permanece vazio nos quadros apesar da digitação registrada (regra não confirmada) e a base vazia impede avaliar os filtros. Corpo da requisição e da resposta indisponíveis; sem causa raiz. |
| [Jam — CT-RF38: Categorias Crossfit](https://jam.dev/c/be1dbd05-217d-44c3-8a3d-240b7f6344e1) e [Evidências](Evidencias/CT-RF38_Cadastro_Categoria_Codigo_Automatico/README.md) | 0:27: Salvar com o nome "teste" e o Código vazio; `POST /api/categoria-exercicio-cross/criar` com HTTP 201, corpo `{"nome": "teste"}` e "Categoria criada com sucesso!". 0:28: nove categorias, código 9 "teste". 0:32: filtro Código "9" retorna só esse registro; 0:02 e 0:08: filtros por nome e por código com uma linha cada. Os filtros não geram requisição de rede (compatível com filtragem local, sem confirmação). Regra do campo Código não confirmada. |
| [Jam — CT-RF39 a CT-RF41: SifitBox – Turmas](https://jam.dev/c/ee9a133b-d6b1-442d-b4b0-dd87595b7e70) e evidências ([CT-RF39](Evidencias/CT-RF39_Cadastro_Modalidade/README.md), [CT-RF40](Evidencias/CT-RF40_Exclusao_Turmas_Modalidades/README.md), [CT-RF41](Evidencias/CT-RF41_Cadastro_Turma_Sem_Modalidade/README.md)) | CT-RF39: `POST modalidades/salvar` com HTTP 201, modalidade de id 4 "ativo" e listagem de três para quatro modalidades (1:34–1:35). CT-RF40: quatro `POST turmas/excluir` e cinco `POST modalidades/excluir` com HTTP 200 e `{"erro": false}` entre 1:00 e 1:05, registros mantidos na listagem com o status "inativo" e sem confirmação visível. CT-RF41: sem requisição de criação de turma e sem mensagem visível nas tentativas de envio (0:17–0:20, 1:28 e 1:33), com a modalidade em branco; a edição da turma de id 4 gera `POST turmas/atualizar` com HTTP 200. Validação nativa do navegador, regras de exclusão e de obrigatoriedade e persistência não confirmadas. |
| [Jam — Pagar.me e Configurações](https://jam.dev/c/e6e551ef-9196-4c79-b6a2-89747b1e8b33) e evidências por caso | CT-RF42: `sacar-saldo` com HTTP 200 sem mensagem de resultado visível. CT-RF43: `criar-cobranca` com HTTP 200 e "Cobrança criada com sucesso!". CT-RF44: configurações alteradas e menu lateral modificado após Salvar, sem mensagem de confirmação, com o campo de dias em -120 e depois 1100. CT-RF45: Recebimentos R$ 38.420,00 e gráfico idênticos em "Últimos 30 dias" e "Últimos 7 dias". |
| [Jam — Despesas Fixas](https://jam.dev/c/a4bac99d-e436-4792-831e-8c3a875272bb) e evidências por caso | CT-RF46: filtros por código e nome com Valor Listado acompanhando o conjunto. CT-RF47: um clique em Salvar Despesa gera dois `POST cria/despesa-fixa` com HTTP 201 e um registro novo (código 23). CT-RF48: diálogo de confirmação e `POST deleta/despesa-fixa` com HTTP 200. CT-RF49: `POST edita/despesa-fixa` com HTTP 200 e recorrência "7 Dias" na listagem. |
| [Jam — Relatórios](https://jam.dev/c/3b4777a4-e1b0-4038-9b06-26c73669d7d1) e evidências por caso | Oito `POST /api/relatorio/1` com HTTP 200 e oito arquivos baixados: Matrículas (uma matrícula, R$ 20,00), Contas a Receber (três contas com Valor a Receber "----") e Contas a Pagar (Pagas) sem linhas abrem; Avaliações (duas vezes), Clientes, Colaboradores e Caixas geram arquivos de 0 bytes. |
| [Jam — CT-RF57: Tela de Grupos](https://jam.dev/c/b1231a75-1a65-4bf0-b795-f52a8c7d3365) | 1:19: acionamento do ícone de exclusão do grupo código 1 ("Treino Livre"). 1:20: diálogo "Deseja deletar o Grupo?" com Cancelar e Confirmar, listagem com 10 registros. 1:21: `POST /api/deleta/grupo/1` retorna HTTP 500 em 987 ms, com `x-hcdn-request-id: 8f18afe5ff0e3a9e3d1c944d69811576-asc-edge13`. 1:30: segunda tentativa no mesmo endpoint, HTTP 500 em 230 ms. Corpo das duas respostas: `{"verifica_erro": true, "mensagem": "Erro interno inesperado."}` — idêntico ao do CT-RF29. O texto do diálogo de erro não foi confirmado visualmente. A mesma gravação mostra o cadastro bem-sucedido de um novo grupo ("Treino sla", código 11). |
| [Jam — CT-RF58: Tela de Grupos](https://jam.dev/c/b1231a75-1a65-4bf0-b795-f52a8c7d3365) | Mesma gravação do CT-RF57. 0:58: clique em Salvar após selecionar Status = "Inativo" no grupo 11 ("Treino sla"); `POST /api/edita/grupo/1` retorna HTTP 200, `{"verifica_erro": false}`, mas `GET /api/grupos/1` e `POST /api/seleciona/grupo/1`, no mesmo instante, mostram o grupo ainda com `"status": "ativo"`. 1:10: segunda edição, alterando apenas a descrição para "Ess"; HTTP 200, `{"verifica_erro": false}`, e a consulta seguinte confirma a descrição persistida. Cabeçalhos "data" em `08:02:46 GMT` e `08:02:58 GMT`; campo `updated_at` do corpo com `12:02:46` e `12:02:58` — descompasso de cerca de 4 horas não investigado. |
| [Jam — CT-RF59: Fichas de Anamnese](https://jam.dev/c/7be0fe71-3419-4050-b63f-473d943fa08e) | 0:28: seleção do aluno "Jorge" e do modelo de anamnese; `POST /api/anamnese/aplicar/1` com `{"modelo_id":3,"respostas":[{"pergunta_id":"5","resposta":"Esse"}],"status":"concluida"}` retorna HTTP 500, `{"verifica_erro": true, "mensagem": "Erro interno inesperado."}`. 0:39, 0:56 e 1:12: novas tentativas de aplicar, com respostas e, na última, modelo diferentes (`modelo_id: 5`, resposta "Agachamento"); mesmo HTTP 500. 0:42, 1:03 e 1:10: três tentativas de `POST /api/anamnese/rascunho/1`, mesmo HTTP 500 — data registrada em uma delas: `Segunda-feira, 16 de novembro de 2026, 01:05:48 GMT`. Nenhuma das sete tentativas é concluída com sucesso. |
| [Jam — CT-RF60: Modelos de Anamnese](https://jam.dev/c/4c1e9deb-20ca-417f-ad09-48749857266e) | 1:57: `POST /api/modelos-anamnese/salvar/1` (cadastro com três perguntas do banco) retorna HTTP 201. 2:12 e 2:19: duas edições do mesmo modelo via `POST /api/modelos-anamnese/alterar/1`, ambas HTTP 201. 2:21 e 2:23: duas exclusões via `POST /api/modelos-anamnese/deletar/1`, ambas HTTP 201. `GET /api/modelos-anamnese/1` (listagem) também retorna HTTP 201 em vez do 200 mais usual para leitura, registrado como ponto a confirmar. A única requisição com erro em toda a gravação é um *beacon* de analytics do Google (HTTP 499), sem relação com o backend do SIFIT. Corpos de requisição e de resposta não capturados pelo Jam. |
| [Jam — CT-RF61: Categorias de Anamnese](https://jam.dev/c/fdb1c9f8-c428-4726-9742-617800325d09) | 0:52: `POST /api/categorias-anamnese/salvar/1` (cadastro) retorna HTTP 201 com `{"nome": "Novo ", "cor": "#d97706", "icone": "bi-bicycle", "status": "INATIVO"}`. 0:59, 1:12 e 1:19: três edições via `POST /api/categorias-anamnese/alterar/1`, todas HTTP 200 (ícone, depois nome, depois status). 1:28: uma quarta tentativa de edição é cancelada, sem requisição ao backend. 1:30: `POST /api/categorias-anamnese/deletar/1` retorna HTTP 200. Filtro por status e busca por texto são aplicados no navegador, sem requisição de rede própria. Nenhuma requisição ao backend do SIFIT retornou erro 4xx ou 5xx. |
| [Jam — CT-RF62: Perguntas Anamnese](https://jam.dev/c/84b116fb-4640-4b1e-9148-9a169b8aa2b0) | 0:51: `POST /api/pergunta-anamnese/salvar/1` (cadastro, duplicado em uma única ação) retorna HTTP 200/201 com `{"nome": "Pergunta", "pergunta": "Pergunta isso", "resposta": "2opcoes_complemento", "numero": 12, "status": "INATIVO"}`, id 11. 1:00, 1:04, 1:08 e 1:12: quatro tentativas de editar o tipo de resposta e/ou o status da pergunta 11 via `POST /api/pergunta-anamnese/alterar/1`, **todas com HTTP 500** e o corpo `{"verifica_erro": true, "mensagem": "Erro interno inesperado."}`. 1:14: a edição é cancelada sem sucesso. 1:21–1:28: três `POST /api/usuario/tema` retornam HTTP 200. |
| [Jam — Prospecção](https://jam.dev/c/308607ff-8abc-40af-8c7c-429ce506ed64) e evidências por caso | CT-RF85: quatro `POST usuario/tema` (HTTP 200) e painel de Notificações sem pendências. CT-RF86: busca por texto reduz a listagem (códigos 3 e 7; 4 e 10 com "tes") sem requisição de rede. CT-RF87: filtro por estágio (Novo Contato: códigos 7 e 8; Proposta: código 4) e Limpar. CT-RF88: um clique em Salvar Lead gera dois `POST salvar-lead` com HTTP 200 e um lead novo (código 10). CT-RF89: telefone de 30 dígitos aceito e gravado sem máscara nem mensagem. CT-RF90: `POST atualizar-lead` com HTTP 200 e nome atualizado na listagem. |
| [Jam — Contas a Pagar](https://jam.dev/c/5d0afaf4-5abd-4e85-923f-27448304a9ef) e evidências por caso | CT-RF91: filtros combinados deixam a listagem vazia, sem dado de controle. CT-RF92: `POST cadastrar-conta-pagar` com HTTP 201 e colaborador vazio; conta 29 listada com "-". CT-RF93: busca de colaborador "sds" sem resultado e sem mensagem. CT-RF94: modal Visualizar Conta a Pagar com os dados da conta. CT-RF95: `POST deletar-conta-pagar` com HTTP 200 e conta removida. |
| [Jam — Modelos de Contrato](https://jam.dev/c/44dbbd39-6915-45d6-8dd1-5f30c1432ca0) e evidências por caso | CT-RF96: variáveis inseridas e pré-visualização com dados de exemplo. CT-RF97: `POST modelo-contrato/salvar` com HTTP 201 e modelo de id 15 na lista do servidor. CT-RF98: tabela vazia com 15 modelos retornados. |
| [Jam — Planos](https://jam.dev/c/233c5d21-e108-4a55-b6f6-8738cb3fc6a6) e evidências por caso | CT-RF99: filtros por código e nome. CT-RF100: cinco `POST usuario/tema` e notificações sem pendências. CT-RF101: `POST plano/salvar` com HTTP 200 e id 66; Planos 40 → 41. CT-RF102: Ativos 29 → 30 → 31 com planos inativos. CT-RF103: `POST plano/update` com HTTP 200. |
| [Jam — Tipos de Pagamento](https://jam.dev/c/e8734e3d-3f8e-458b-8c7d-e85eea882e50) e evidências por caso | CT-RF104: Buscar e seletores sem requisição de listagem; 16 tipos inalterados. CT-RF105: `POST cria/tipo-pagamento` com HTTP 201 sem status; Total 17, Ativos 0, Inativos 17. CT-RF106: `POST edita/tipo-pagamento` com HTTP 200; Via gateway 6 → 5. CT-RF107: dois `POST deleta/tipo-pagamento` com HTTP 404 e erro SQL de chave estrangeira. CT-RF108: seis `POST usuario/tema` e notificações sem pendências. |
| [Jam — PED-25](https://jam.dev/c/fb5673c9-3cd1-46c4-88f4-d5fb32574a8e) e [Evidências](Evidencias/CT-RF109_Modelo_Ficha_Sem_Nome/README.md) | CT-RF109: Nenhuma requisição de rede capturada durante o trecho, incluindo o clique em Criar Modelo. |
| [Jam — PED-26](https://jam.dev/c/a2a39e11-04f4-40aa-a97e-75a57a5f1b0f) e [Evidências](Evidencias/CT-RF110_Cancelar_Cadastro_Modelo_Ficha/README.md) | CT-RF110: Nenhuma requisição de rede capturada durante a gravação, incluindo o clique em Cancelar. |
| [Jam — PED-27](https://jam.dev/c/c1aecaa8-39c7-49b0-89af-9de47a68ba40) e [Evidências](Evidencias/CT-RF111_Busca_Modelo_Ficha_Codigo_Inexistente/README.md) | CT-RF111: Em 0:06, GET `/api/fichas-modelo/1` com HTTP 200 e corpo `[]` (2 B). A URL capturada não contém parâmetros de filtro. |
| [Jam — PED-28](https://jam.dev/c/0c385452-2aeb-427f-8159-79549fe7371d) e [Evidências](Evidencias/CT-RF112_Busca_Modelo_Ficha_Titulo_Inexistente/README.md) | CT-RF112: Em 0:06, GET `/api/fichas-modelo/1` com HTTP 200 e corpo `[]` (2 B), sem parâmetros de filtro visíveis na URL capturada. |
| [Jam — PED-29](https://jam.dev/c/006f9722-e643-4b65-904a-25471a7b90ed) e [Evidências](Evidencias/CT-RF113_Busca_Modelo_Ficha_Filtros_Combinados/README.md) | CT-RF113: Em 0:11, GET `/api/fichas-modelo/1` com HTTP 200 e corpo `[]` (2 B). O evento não mostra os filtros na URL. |
| [Jam — PED-30](https://jam.dev/c/297eec2b-7be4-498b-a0e6-e962ed93cc00) e [Evidências](Evidencias/CT-RF114_Limpeza_Filtros_Modelos_Ficha/README.md) | CT-RF114: Nenhuma requisição durante a limpeza. Os dois GET ocorreram após os cliques de busca com os campos vazios. |
| [Jam — PED-30](https://jam.dev/c/297eec2b-7be4-498b-a0e6-e962ed93cc00) e [Evidências](Evidencias/CT-RF115_Nova_Busca_Modelos_Ficha_Sem_Filtros/README.md) | CT-RF115: Em 0:11 e 0:13, dois GET `/api/fichas-modelo/1`, ambos com HTTP 200 e corpo `[]` (2 B cada). |
| [Jam — PED-20 — Dias de ausência vazio](https://jam.dev/c/4e96d4fa-65b5-459b-a795-854496e5753c) e [Evidências](Evidencias/CT-RF116_Configuracoes_Dias_Ausencia_Vazio/README.md) | CT-RF116: Campo vazio convertido em 0, com HTTP 200. A recarga e a consulta confirmaram 0. |
| [Jam — PED-20 — Cancelar alteração](https://jam.dev/c/e8faa199-1177-4563-8b00-590606669a1d) e [Evidências](Evidencias/CT-RF117_Configuracoes_Cancelar_Alteracao/README.md) | CT-RF117: Cancelar levou à Página Inicial. O GET ao reabrir Configurações confirmou o valor original 1100. |
| [Jam — PED-21 — Trabalha com turmas](https://jam.dev/c/a51c33a5-537a-40fd-a55d-990b70ac0696) e [Evidências](Evidencias/CT-RF118_Configuracoes_Trabalha_Com_Turmas/README.md) | CT-RF118: Sim → Não → Sim. Os dois POST e os GET após recarga confirmaram os valores de `usa_turmas`. |
| [Jam — PED-22 — Academia marcada como Box](https://jam.dev/c/16dc862d-c3f9-4392-9037-526818e86cd6) e [Evidências](Evidencias/CT-RF119_Configuracoes_Academia_Marcada_Box/README.md) | CT-RF119: Não → Sim → Não. Seletor, cartão SifitBox e menu Principal acompanharam o estado após recarga. |
| [Jam — PED-23 — Acesso desktop](https://jam.dev/c/466be253-ad9a-4856-b567-fb17e1fdd479) e [Evidências](Evidencias/CT-RF120_Configuracoes_Acesso_Desktop/README.md) | CT-RF120: Não → Sim → Não. A API, o seletor e o cartão Desktop refletiram o valor salvo nas duas recargas. |
| [Jam — PED-24 — Cadastro de modelo de ficha](https://jam.dev/c/04e2cae2-f3f2-43ff-8361-b3b9d9f50d35) e [Evidências](Evidencias/CT-RF121_Cadastro_Modelo_Ficha_Erro_500/README.md) | CT-RF121: Cadastro preenchido retornou HTTP 500. A interface exibiu “Erro ao salvar modelo.” |
| [Jam — PED-12 — Últimos 90 dias](https://jam.dev/c/1728cfc2-1d36-4ea4-ab68-68a84458c359) e [Evidências](Evidencias/CT-RF122_Resultados_IA_Filtro_90_Dias/README.md) | CT-RF122: Cartões e linha do tempo acompanharam a troca de 7, 30 e 90 dias. Os resultados de 90 dias se repetiram. |
| [Jam — PED-14 — Execução de Risco de Evasão](https://jam.dev/c/efe26a44-458a-4802-bd48-8e23c5ac5fd9) e [Evidências](Evidencias/CT-RF123_Central_Resultados_IA_Execucao_Evasao/README.md) | CT-RF123: A Central passou a mostrar 00:55. A linha do tempo de Hoje e o resumo de Resultados IA incluíram essa execução. |
| Jam — PED-15 (gravação restrita por conter dados de integração) e [Evidências](Evidencias/CT-RF124_Configuracoes_Abas_Biometria_Senha/README.md) | CT-RF124: A navegação funcionou. A aba Biometria exibiu o valor do campo Senha sem mascaramento. |
| [Jam — PED-16 — Salvar dias de ausência](https://jam.dev/c/12d6bba7-a67e-4882-86a5-4dd08d194af2) e [Evidências](Evidencias/CT-RF125_Configuracoes_Salvar_Dias_Ausencia_Valido/README.md) | CT-RF125: 15 foi salvo e confirmado após recarga. A segunda recarga confirmou a restauração de 1100. |
| [Jam — PED-17 — Dias de ausência negativos](https://jam.dev/c/d5786f67-6e5f-44f5-bbba-fbd763a88740) e [Evidências](Evidencias/CT-RF126_Configuracoes_Dias_Ausencia_Negativo/README.md) | CT-RF126: -1 foi aceito com HTTP 200 e confirmado na interface e no GET após recarga. |
| [Jam — PED-18 — Dias de ausência com texto](https://jam.dev/c/c578ed7a-c11c-4cef-8a6c-84d0244f21a5) e [Evidências](Evidencias/CT-RF127_Configuracoes_Dias_Ausencia_Texto/README.md) | CT-RF127: Letras não apareceram no campo. O salvamento com campo vazio enviou 0 e retornou HTTP 200. |
| [Jam — PED-06 — Configuração de Risco de Evasão](https://jam.dev/c/d49b8ffc-a6e2-4e37-a618-c280b5e807db) e [Evidências](Evidencias/CT-RF128_Central_Configuracao_Risco_Evasao_Cancelar/README.md) | CT-RF128: Configurar abriu Risco de Evasão e Cancelar fechou o painel. O cartão continuou ativo. |
| [Jam — PED-07 — Configuração de Aniversariantes](https://jam.dev/c/c66d4d01-aee2-4037-a8fd-858da21a0a14) e [Evidências](Evidencias/CT-RF129_Central_Aniversariantes_Previa_Risco/README.md) | CT-RF129: O painel Aniversariantes abriu corretamente, mas a prévia exibiu dados de risco de evasão. |
| [Jam — PED-08 — Recursos em desenvolvimento](https://jam.dev/c/0a7ae8fb-980d-4df2-8ef8-de78d6b11b8f) e [Evidências](Evidencias/CT-RF130_Central_Recursos_Em_Desenvolvimento/README.md) | CT-RF130: Os quatro recursos exibiram Em desenvolvimento. Os cliques não iniciaram navegação, configuração ou execução. |
| [Jam — PED-09 — Hoje](https://jam.dev/c/a83c4c74-0b8e-4242-9612-0202c9063d56) e [Evidências](Evidencias/CT-RF131_Resultados_IA_Filtro_Hoje/README.md) | CT-RF131: Hoje consultou um dia e o total de aniversariantes passou de 2 para 0, como na resposta. |
| [Jam — PED-10 — Últimos 7 dias](https://jam.dev/c/cbf45b87-b7b6-4314-a359-c5e706aa755e) e [Evidências](Evidencias/CT-RF132_Resultados_IA_Filtro_7_Dias/README.md) | CT-RF132: Ao voltar de Hoje para Últimos 7 dias, o cartão Aniversariantes passou de 0 para 2. |
| [Jam — PED-11 — Últimos 30 dias](https://jam.dev/c/2756d5c1-a823-482b-bf8d-878357b8b087) e [Evidências](Evidencias/CT-RF133_Resultados_IA_Filtro_30_Dias/README.md) | CT-RF133: O filtro de 30 dias apresentou 12 automações, 12 relatórios e 6 aniversariantes nas duas seleções. |

A mensagem de credenciais incorretas já aparece no início do vídeo do Jam; não foi considerada uma resposta ao clique em "Esqueci minha senha". A ausência de requisição, isoladamente, não caracteriza defeito se a interface abrir um formulário local. Aqui, o resultado reprovado decorre de o fluxo não abrir.

No CT-RF02_ERRO, a permanência de tags como `<base-input>` no DOM é um indício a investigar, sem confirmação da causa. A captura estática não mostra toda a página ou a barra horizontal; o relato e o quadro do Jam complementam essa evidência. Não foi estabelecido diagnóstico de rede/console, não houve comparação individual com o cadastro real nem teste de salvamento. As contagens de rede e console do CT-RF01 não se aplicam ao CT-RF02_ERRO.

### Análise técnica e limites do CT-RF03

O relato informa três chamadas ao endpoint de Clientes em aproximadamente **00:05, 00:20 e 00:28**, todas HTTP 200, com cerca de **180,9 KB** por resposta. O corpo simplificado contém apenas `empresa_id: 1` e `nome: ""`, sem Status, Situação Financeira, Plano e Personal. Não foi estabelecida a correspondência exata entre cada horário e a situação financeira selecionada.

A ausência desses critérios no corpo informado sustenta a hipótese de falha na integração dos filtros com a busca, mas é necessário analisar o código e o contrato da API para verificar se a filtragem deve ocorrer no servidor, localmente ou em ambos. HTTP 200 não comprova a aplicação dos critérios, e tamanhos semelhantes não demonstram conteúdo idêntico. As métricas visíveis na captura 1 não foram tratadas como equivalentes ao volume informado para o Jam.

Não foram fornecidos HAR, respostas integrais ou cadastros de referência para comprovar os vínculos de cada registro. Não houve diagnóstico de console, nova execução, análise do código ou confirmação da correção. Os testes com Código, Nome, conjunto vazio e as demais combinações da [matriz de reteste](Cenario_Teste/CT-RF03_FILTRO_TelaClientes.md#matriz-de-reteste-proposta) permanecem **pendentes de execução**, sem resultado atribuído.

---

### Análise e limites do CT-RF04_loginComSucesso

A aprovação considera o resultado visível após a autenticação, além da URL e dos status HTTP. O painel aparece em aproximadamente 00:07 e mostra cartões preenchidos em 00:09 e 00:11. A gravação não comprova persistência da sessão, logout, expiração, comportamento com credenciais inválidas, permissões de outros perfis, correspondência do nome exibido com o cadastro ou exatidão dos dados do painel. Não foram inspecionados corpos de autenticação ou logs do console. Senha e tokens não foram reproduzidos.

---

## 📌 6. Pendências e encaminhamento

- **BUG-001:** aberto, com severidade e prioridade altas; causa técnica ainda não confirmada no código.
- **Reteste de CT-RF01:** pendente após a correção, conforme o [plano de testes](Plano%20de%20testes.md).
- **BUG-002:** aberto, com severidade e prioridade propostas como altas; investigar renderização dos componentes, dados de demonstração e estilos do perfil.
- **Reteste de CT-RF02_ERRO:** pendente após a correção, com conta de teste de dados conhecidos e condições de layout registradas, conforme o [plano](Plano%20de%20testes.md).
- **BUG-003:** aberto, com severidade e prioridade propostas como altas; investigar a captura dos critérios, o contrato da API e eventual filtragem local. Causa não confirmada.
- **Reteste de CT-RF03:** pendente após a correção, com base conhecida, IDs validados e execução das nove variações previstas no [plano](Plano%20de%20testes.md#ct-rf03). Registrar inclusão, exclusão, completude e estado sem resultados antes de encerrar o defeito.
- **Etapas seguintes:** não avaliadas nesta evidência, pois não foi possível iniciar a recuperação; detalhamento depende da definição das regras do fluxo.
- **CT-RF04_loginComSucesso:** aprovado conforme a gravação; sem defeito associado e sem reteste corretivo pendente. Utilizar o caso como regressão em novas versões. Variações de autenticação exigem casos próprios e permanecem fora da cobertura atual.

## Ampliação de 14/11/2026 — pendências e próximos passos

| Caso | Situação | Encaminhamento |
| --- | --- | --- |
| [CT-RF05](Cenario_Teste/CT-RF05_Login_SenhaIncorreta.md) | Aprovado conforme a gravação | Usar como regressão de autenticação negativa; preparar conta conhecida e repetir após alterações no login. |
| [CT-RF06](Cenario_Teste/CT-RF06_Login_UsuarioInexistente.md) | Aprovado conforme a gravação | Repetir com identificador de inexistência comprovada; a classificação atual refere-se à recusa visível do cenário declarado pelo autor. |
| [CT-RF07](Cenario_Teste/CT-RF07_Exportacao_Financeiro.md) | Reprovado nas evidências | Investigar o retorno do botão; no reteste capturar o histórico de downloads e abrir o arquivo antes de concluir se a exportação foi gerada. |
| [CT-RF08](Cenario_Teste/CT-RF08_Calculo_Cobranca.md) | A validar — regra ou contexto pendente | Confirmar a origem dos R$ 20,83 além de principal e multa e a regra da mensagem; não registrar cálculo incorreto antes dessa validação. |
| [CT-RF09](Cenario_Teste/CT-RF09_Contagem_Mensalidades.md) | Reprovado nas evidências | Retestar com o CT-RF10; os dois cenários documentam manifestações do BUG-005, sem criar um defeito duplicado. |
| [CT-RF10](Cenario_Teste/CT-RF10_Filtro_Mensalidades.md) | Reprovado nas evidências | Retestar em conjunto com CT-RF09 e conferir o contrato da faixa Até 7 dias antes de preparar a base. |
| [CT-RF11](Cenario_Teste/CT-RF11_Metricas_Financeiro.md) | A validar — regra ou contexto pendente | Confirmar os contratos dos cartões; a constância de totais globais não é suficiente para abrir outro defeito financeiro. |
| [CT-RF12](Cenario_Teste/CT-RF12_Periodo_Dashboard.md) | Reprovado nas evidências | Corrigir e retestar a validação do intervalo; avaliar a atualização dos indicadores em base controlada como verificação complementar. |
| [CT-RF13](Cenario_Teste/CT-RF13_Codigos_Personais.md) | A validar — regra ou contexto pendente | Confirmar a semântica da coluna Código; quatro linhas e total quatro não sustentam um defeito de quantidade. |
| [CT-RF14](Cenario_Teste/CT-RF14_Contraste_TemaEscuro.md) | Reprovado nas evidências | Ajustar as cores e retestar ambos os temas; medir contraste se houver critério formal de acessibilidade definido. |
| [CT-RF15](Cenario_Teste/CT-RF15_Edicao_Modalidade.md) | Reprovado nas evidências | Verificar o fluxo de conclusão da edição e retestar persistência. A evidência reprova a clareza da ação de salvar; não afirma que o ícone de editar inexiste. |
| [CT-RF16](Cenario_Teste/CT-RF16_Exclusao_Modalidade.md) | A validar — regra ou contexto pendente | Confirmar a exclusão lógica e a nomenclatura da ação; registrar defeito apenas se houver divergência com a regra definida. |
| [CT-RF17](Cenario_Teste/CT-RF17_Filtros_Categorias.md) | Aprovado conforme a gravação | Usar como regressão; combinações, conjunto vazio, caracteres especiais e paginação exigem execuções adicionais. |
| [CT-RF18](Cenario_Teste/CT-RF18_Atualizacao_Categoria.md) | Aprovado conforme a gravação | Usar como regressão; acrescentar recarga e nova consulta para ampliar a verificação de persistência. |
| [CT-RF19](Cenario_Teste/CT-RF19_Exclusao_Categoria.md) | Reprovado nas evidências | Investigar o HTTP 500 com logs do servidor e vínculos da categoria; corrigir e retestar cenários permitido e impedido. |
| [CT-RF20](Cenario_Teste/CT-RF20_Criacao_Categoria.md) | Aprovado conforme a gravação | Usar como regressão; campos vazios, nomes duplicados e limites de tamanho permanecem fora do cenário gravado. |

Os sete novos casos reprovados aguardam reteste corretivo e correspondem a seis defeitos. As quatro pendências de regra/contexto não foram reprovadas por suposição. CT-RF05/06/17/18/20 são referências de regressão; sua aprovação se limita aos exemplos gravados. Nenhuma variação planejada recebe contagem de execução sem evidência própria.

As análises históricas de CT-RF01–CT-RF04 acima continuam com seus limites originais. A nova cobertura de login negativo está em CT-RF05 e CT-RF06; ela não amplia retroativamente a aprovação do CT-RF04.

## Inclusão de 15/11/2026 — CT-RF21

O caso [CT-RF21](Cenario_Teste/CT-RF21_Cadastro_Avaliacao.md) está reprovado nas evidências e vinculado ao [BUG-010](Relatorio-de-Bugs.md#bug-010), aberto, com severidade/prioridade altas propostas. Foram conferidos detalhes, cronologia, evento 16 e quadros do Jam; o relato original foi preservado, com dados de negócio sem autenticação.

Confirmar existência/vínculo do aluno e regra de retroatividade, investigar os logs da API e executar a matriz de reteste com dados válidos e recusados. Essas verificações são propostas, sem resultado de execução. A persistência da tentativa original não foi consultada. Não houve nova execução nem correção da aplicação.

Na inclusão de CT-RF21, o consolidado histórico passou a 21 casos: 6 aprovados, 11 reprovados e 4 a validar; 10 bugs abertos e 11 retestes corretivos pendentes. As conclusões históricas de CT-RF01–CT-RF20 foram preservadas. Os arquivos locais de evidências anteriores citados nesses documentos não estavam nesta cópia; o [índice de evidências](Evidencias/README.md) registra essa disponibilidade.


## Inclusão de 15/11/2026 — CT-RF22 a CT-RF28

| Caso | Situação | Encaminhamento |
| --- | --- | --- |
| [CT-RF22](Cenario_Teste/CT-RF22_Digitacao_Codigo_Exercicio.md) | Reprovado conforme o relato; reprodução independente pendente. | Confirmar a regra, reproduzir o impedimento e retestar o campo após correção. |
| [CT-RF23](Cenario_Teste/CT-RF23_Exclusao_Exercicio.md) | Aprovado no trecho consultado. | Manter como regressão. Em nova execução, recarregar a página para conferir persistência e testar separadamente as regras para exercícios vinculados. |
| [CT-RF24](Cenario_Teste/CT-RF24_Edicao_Exercicio.md) | Reprovado no trecho consultado; confirmar operação e identidade dos registros na reprodução. | Reproduzir a partir da ação explícita de edição e comparar os identificadores antes e depois. Investigar eventual envio para criação como hipótese, sem atribuir causa técnica antes de verificar código e contrato da API. |
| [CT-RF25](Cenario_Teste/CT-RF25_Envio_Exercicio_Imagem.md) | A validar — criação visível; persistência e associação da imagem não confirmadas. | Reabrir o exercício criado e conferir a imagem salva. Testar formatos e tamanhos inválidos em casos separados; essas variações não recebem resultado nesta análise. |
| [CT-RF26](Cenario_Teste/CT-RF26_Exercicio_Campos_Vazios.md) | Reprovado — sem feedback de validação visível. | Implementar mensagens por campo e confirmar ausência de persistência no reteste. |
| [CT-RF27](Cenario_Teste/CT-RF27_Video_Campo_Imagem.md) | Reprovado — arquivo rejeitado sem feedback visível. | Informar formatos aceitos e retestar extensão, MIME, tamanho, rede e persistência. |
| [CT-RF28](Cenario_Teste/CT-RF28_Imagem_Campo_Video.md) | Reprovado — arquivo rejeitado sem feedback visível. | Informar formatos aceitos e retestar extensão, MIME, tamanho, rede e persistência. |
| [CT-RF34](Cenario_Teste/CT-RF34_Erro_Servidor_Excesso_Requisicoes.md) | Reprovado — múltiplas chamadas retornam HTTP 500. | Correlacionar endpoints e componentes, inspecionar logs, verificar repetição e retestar o carregamento completo. |

O consolidado atual é de 34 casos documentados: 10 aprovados, 19 reprovados e 5 a validar; 18 defeitos registrados (10 abertos e 8 em triagem) e 19 casos com reteste corretivo pendente. CT-RF09/10 compartilham BUG-005. BUG-018 registra os HTTP 500 do dashboard sem confirmar que excesso de requisições seja a causa. Sem nova execução.

## Inclusão de 15/11/2026 — CT-RF29

| Caso | Situação | Encaminhamento |
| --- | --- | --- |
| [CT-RF29](Cenario_Teste/CT-RF29_Exclusao_GrupoMuscular.md) | Reprovado nas evidências | Investigar o HTTP 500 com logs do servidor e os vínculos do registro; corrigir e retestar os cenários permitido e impedido. Verificar se o registro permanece íntegro após as duas tentativas enviadas ao mesmo recurso. |

O [BUG-016](Relatorio-de-Bugs.md#bug-016) está em triagem, com severidade Média e prioridade Alta propostas. O comportamento repete a assinatura de [BUG-009](Relatorio-de-Bugs.md#bug-009) e [BUG-010](Relatorio-de-Bugs.md#bug-010): mesmo corpo de resposta e mesmo tamanho, em três módulos distintos. Essa coincidência sugere um tratamento de exceção comum, mas não foi confirmada no código.

O cenário de exclusão com impedimento de regra não foi exercitado, de modo que não se sabe se o sistema distingue impedimento de falha. A mensagem apresentada é genérica e não informa a causa ao usuário.

As conclusões anteriores foram preservadas. Não houve nova execução nem correção da aplicação.

## Inclusão de 15/11/2026 — CT-RF30 a CT-RF33 e CT-RF35

| Caso | Situação | Encaminhamento |
| --- | --- | --- |
| [CT-RF30](Cenario_Teste/CT-RF30_Imagens_GruposMusculares.md) | Reprovado nas evidências | Verificar a existência dos arquivos, o nome gravado em cada registro e a regra que responde 422; definir o estado neutro para registros sem imagem. |
| [CT-RF31](Cenario_Teste/CT-RF31_Cadastro_GrupoMuscular.md) | Aprovado conforme a gravação | Usar como regressão; campos em branco, nomes duplicados, limites de tamanho e código informado manualmente exigem execuções adicionais. |
| [CT-RF32](Cenario_Teste/CT-RF32_Edicao_TipoMembro.md) | Aprovado conforme a gravação | Usar como regressão; conferir persistência após recarga e confirmar se a imagem enviada na edição é salva. |
| [CT-RF33](Cenario_Teste/CT-RF33_Filtros_GruposMusculares.md) | Aprovado conforme a gravação | Usar como regressão; executar um caso com critérios contraditórios para demonstrar a lógica combinada. |
| [CT-RF35](Cenario_Teste/CT-RF35_Cadastro_Objetivo_Treino.md) | Reprovado nas evidências | Investigar o HTTP 500 com logs do servidor; retestar dados válidos, descrição com caracteres especiais, campos vazios, código manual e persistência; conferir que um clique gera uma única gravação. |

O [BUG-019](Relatorio-de-Bugs.md#bug-019) está em triagem, com severidade e prioridade Altas propostas. O corpo da requisição e da resposta não foi capturado pelo Jam; o campo Código e a avaliação dos filtros com a base vazia permanecem como pontos a confirmar, sem defeito próprio.

O consolidado atual, com a inclusão do CT-RF35, é de 35 casos documentados (CT-RF01–CT-RF35): 10 aprovados, 20 reprovados e 5 a validar; 19 defeitos registrados (10 abertos e 9 em triagem) e 20 casos com reteste corretivo pendente. CT-RF09/10 compartilham BUG-005, de modo que 20 casos reprovados correspondem a 19 defeitos. Sem nova execução.

## Inclusão de 15/11/2026 — CT-RF38

| Caso | Situação | Encaminhamento |
| --- | --- | --- |
| [CT-RF38](Cenario_Teste/CT-RF38_Cadastro_Categoria_Codigo_Automatico.md) | Aprovado conforme a gravação | Usar como regressão; nome vazio, nome duplicado, limites de tamanho, código inexistente no filtro e persistência após recarga exigem execuções adicionais; confirmar a regra do campo Código e o contrato dos cartões. |

O CT-RF38 complementa os casos [CT-RF17](Cenario_Teste/CT-RF17_Filtros_Categorias.md) (filtros) e [CT-RF20](Cenario_Teste/CT-RF20_Criacao_Categoria.md) (criação) da mesma tela, sem substituí-los; não gera defeito. O campo Código não retém o texto digitado e não consta no corpo da requisição, o que é compatível com um código automático, como em CT-RF31 e CT-RF35, sem confirmação do produto.

O consolidado atual é de 36 casos documentados (CT-RF01–CT-RF35 e CT-RF38): 11 aprovados, 20 reprovados e 5 a validar; 19 defeitos registrados (10 abertos e 9 em triagem) e 20 casos com reteste corretivo pendente. Sem nova execução.

## Inclusão de 15/11/2026 — CT-RF39 a CT-RF41

| Caso | Situação | Encaminhamento |
| --- | --- | --- |
| [CT-RF39](Cenario_Teste/CT-RF39_Cadastro_Modalidade.md) | Aprovado conforme a gravação | Usar como regressão; nome vazio, nome duplicado, limites de tamanho, status Inativo e persistência após recarga exigem execuções adicionais. |
| [CT-RF40](Cenario_Teste/CT-RF40_Exclusao_Turmas_Modalidades.md) | A validar — regra ou contexto pendente | Confirmar a exclusão lógica, a confirmação prévia e a exibição de registros inativos sob o filtro "Ativo"; registrar defeito apenas se houver divergência com a regra definida. |
| [CT-RF41](Cenario_Teste/CT-RF41_Cadastro_Turma_Sem_Modalidade.md) | Reprovado — sem feedback de validação visível | Confirmar a obrigatoriedade da modalidade, reproduzir com a validação nativa visível e retestar o envio válido e a persistência. |

O [BUG-020](Relatorio-de-Bugs.md#bug-020) está em triagem, com severidade Média e prioridade Alta propostas; repete o padrão de ausência de feedback do [BUG-013](Relatorio-de-Bugs.md#bug-013) em outro módulo. O CT-RF40 se relaciona ao ponto a validar do [CT-RF16](Cenario_Teste/CT-RF16_Exclusao_Modalidade.md).

O consolidado atual é de 39 casos documentados (CT-RF01–CT-RF35 e CT-RF38–CT-RF41): 12 aprovados, 21 reprovados e 6 a validar; 20 defeitos registrados (10 abertos e 10 em triagem) e 21 casos com reteste corretivo pendente. CT-RF09/10 compartilham BUG-005, de modo que 21 casos reprovados correspondem a 20 defeitos. Sem nova execução.

## Inclusão de 15/11/2026 — CT-RF42 a CT-RF56

| Caso | Situação | Encaminhamento |
| --- | --- | --- |
| [CT-RF42](Cenario_Teste/CT-RF42_Solicitacao_Saque_PagarMe.md) | A validar — regra ou contexto pendente | Confirmar a regra de saque e reexecutar com saldo conhecido, capturando corpo e resposta; testar valor acima do saldo e valor inválido. |
| [CT-RF43](Cenario_Teste/CT-RF43_Criacao_Cobranca_PagarMe.md) | Aprovado conforme a gravação | Usar como regressão; outros métodos, dados inválidos, link gerado e presença da cobrança em Transações recentes exigem execuções adicionais. |
| [CT-RF44](Cenario_Teste/CT-RF44_Configuracoes_Home_Salvamento.md) | A validar — regra ou contexto pendente | Confirmar a faixa do campo de dias e a mensagem de salvamento; reexecutar com recarga, Cancelar e valores limite. |
| [CT-RF45](Cenario_Teste/CT-RF45_Painel_PagarMe_Periodo.md) | Reprovado nas evidências | Reproduzir com conta de movimentação conhecida, comparar períodos e capturar corpo e resposta de recebiveis, transacoes e pagarme. |
| [CT-RF46](Cenario_Teste/CT-RF46_Filtros_Despesas_Fixas.md) | Aprovado conforme a gravação | Usar como regressão; combinação de critérios, resultado vazio, filtros de status e recorrência e a regra de correspondência do código exigem execuções adicionais. |
| [CT-RF47](Cenario_Teste/CT-RF47_Cadastro_Despesa_Fixa.md) | A validar — regra ou contexto pendente | Reproduzir capturando as duas requisições de criação e conferir a quantidade de registros após recarga; confirmar a regra do código. |
| [CT-RF48](Cenario_Teste/CT-RF48_Exclusao_Despesa_Fixa.md) | Aprovado conforme a gravação | Usar como regressão; Cancelar, despesa com vínculos, natureza da exclusão e persistência após recarga exigem execuções adicionais. |
| [CT-RF49](Cenario_Teste/CT-RF49_Edicao_Despesa_Fixa.md) | Aprovado conforme a gravação | Usar como regressão; edição de nome, valor e status, Cancelar, pré-preenchimento da recorrência e persistência após recarga exigem execuções adicionais. |
| [CT-RF50](Cenario_Teste/CT-RF50_Relatorio_Matriculas.md) | Aprovado conforme a gravação | Usar como regressão; conferir com a lista de matrículas e exercitar filtros e período sem registros. |
| [CT-RF51](Cenario_Teste/CT-RF51_Relatorio_Contas_Receber.md) | Reprovado nas evidências | Comparar com o módulo Contas a Receber e reexecutar com valores conhecidos, Detalhado e outros status. |
| [CT-RF52](Cenario_Teste/CT-RF52_Relatorio_Contas_Pagar_Pagas.md) | A validar — regra ou contexto pendente | Conferir as contas pagas do período no módulo e reexecutar com um período que contenha pagamentos. |
| [CT-RF53](Cenario_Teste/CT-RF53_Relatorio_Avaliacoes_Vazio.md) | Reprovado nas evidências | Investigar a geração com logs do servidor e retestar com e sem registros no período, comparando com os relatórios que abrem. |
| [CT-RF54](Cenario_Teste/CT-RF54_Relatorio_Clientes_Vazio.md) | Reprovado nas evidências | Investigar a geração com logs do servidor e retestar com e sem registros no período, comparando com os relatórios que abrem. |
| [CT-RF55](Cenario_Teste/CT-RF55_Relatorio_Colaboradores_Vazio.md) | Reprovado nas evidências | Investigar a geração com logs do servidor e retestar com e sem registros no período, comparando com os relatórios que abrem. |
| [CT-RF56](Cenario_Teste/CT-RF56_Relatorio_Caixas_Vazio.md) | Reprovado nas evidências | Investigar a geração com logs do servidor e retestar com e sem registros no período, comparando com os relatórios que abrem. |

Os defeitos [BUG-021](Relatorio-de-Bugs.md#bug-021), [BUG-022](Relatorio-de-Bugs.md#bug-022) e [BUG-023](Relatorio-de-Bugs.md#bug-023) estão em triagem. O BUG-023 é compartilhado por CT-RF53 a CT-RF56 (arquivos de 0 bytes) e, por isso, seis casos reprovados deste grupo correspondem a três defeitos. Os pontos a validar (CT-RF42, CT-RF44, CT-RF47 e CT-RF52) não geram defeito antes da confirmação da regra ou da duplicidade.

O consolidado atual é de 66 casos documentados: 18 aprovados, 38 reprovados e 10 a validar; 34 defeitos registrados (10 abertos e 24 em triagem) e 38 casos com reteste corretivo pendente. CT-RF09/10 compartilham BUG-005 e CT-RF53 a CT-RF56 compartilham BUG-023. Sem nova execução.

---

## Resultado de CT-RF65 a CT-RF70 — Colaboradores

| Caso | Resultado observado | Situação | Defeito |
| --- | --- | --- | --- |
| [CT-RF65](Cenario_Teste/CT-RF65_Data_Nascimento_Futura_Colaborador.md) | Data `18/05/2222`; atualização HTTP 200. | Reprovado | [BUG-026](Relatorio-de-Bugs.md#bug-026) |
| [CT-RF66](Cenario_Teste/CT-RF66_Data_Nascimento_Obrigatoria_Colaborador.md) | Data obrigatória vazia; atualização HTTP 200. | Reprovado | [BUG-027](Relatorio-de-Bugs.md#bug-027) |
| [CT-RF67](Cenario_Teste/CT-RF67_CREF_Formato_Colaborador.md) | CREF `TESTEE`; atualização HTTP 200. | Reprovado, com formato a confirmar | [BUG-028](Relatorio-de-Bugs.md#bug-028) |
| [CT-RF68](Cenario_Teste/CT-RF68_Edicao_Colaborador_Campo_Obrigatorio_Vazio.md) | Campo obrigatório vazio; atualização HTTP 200. | Reprovado | [BUG-029](Relatorio-de-Bugs.md#bug-029) |
| [CT-RF69](Cenario_Teste/CT-RF69_Funcao_Duplicada_Colaborador.md) | Consulta passa de uma para três funções idênticas. | Reprovado | [BUG-030](Relatorio-de-Bugs.md#bug-030) |
| [CT-RF70](Cenario_Teste/CT-RF70_Exclusao_Colaborador_Erro_500.md) | Exclusão retorna HTTP 500 e erro interno. | Reprovado | [BUG-031](Relatorio-de-Bugs.md#bug-031) |

RF65–RF68 precisam de reteste com corpo do POST e reabertura do cadastro para comprovar a persistência. RF69 possui evidência direta da duplicidade. RF70 confirma o erro interno, mas não sua causa.

## Resultado de CT-RF71 a CT-RF73 — Buscas de Colaboradores

| Caso | Resultado observado | Situação | Defeito |
| --- | --- | --- | --- |
| [CT-RF71](Cenario_Teste/CT-RF71_Busca_Nome_Colaborador_Paginacao.md) | A busca por nome retorna correspondências, mas a próxima página inclui nomes fora do filtro. | Reprovado | [BUG-033](Relatorio-de-Bugs.md#bug-033) |
| [CT-RF72](Cenario_Teste/CT-RF72_Busca_Codigo_Existente_Colaborador.md) | A busca por código existente retorna o usuário correto no exemplo gravado. | Aprovado conforme a gravação | — |
| [CT-RF73](Cenario_Teste/CT-RF73_Busca_Codigo_Inexistente_Colaborador.md) | A busca por código inexistente renderiza uma linha vazia. | Reprovado | [BUG-034](Relatorio-de-Bugs.md#bug-034) |

As três gravações foram realizadas em 15/11/2026, entre 21:58 e 22:01 BRT, na página de Colaboradores. A análise foi visual e documental; não houve nova execução nem inspeção das respostas de rede. CT-RF71 e CT-RF73 aguardam correção e reteste, enquanto a aprovação de CT-RF72 se limita ao código existente demonstrado.
O consolidado em 15/11/2026, antes da inclusão de CT-RF57, era de 54 casos documentados (CT-RF01–CT-RF35 e CT-RF38–CT-RF56): 17 aprovados, 27 reprovados e 10 a validar; 23 defeitos registrados (10 abertos e 13 em triagem) e 27 casos com reteste corretivo pendente. CT-RF09/10 compartilham BUG-005 e CT-RF53 a CT-RF56 compartilham BUG-023, de modo que 27 casos reprovados correspondem a 23 defeitos. Sem nova execução.

---

## Inclusão de 15/11/2026 — CT-RF57

| Caso | Situação | Encaminhamento |
| --- | --- | --- |
| [CT-RF57](Cenario_Teste/CT-RF57_Exclusao_Grupo.md) | Reprovado nas evidências | Investigar o HTTP 500 com logs do servidor e os vínculos do grupo de código 1, em conjunto com o BUG-016 (mesmo endpoint e mensagem para grupos musculares); corrigir e retestar os cenários permitido e impedido. |

O defeito [BUG-024](Relatorio-de-Bugs.md#bug-024) está em triagem. O endpoint `/api/deleta/grupo/{id}` e a mensagem genérica retornada coincidem exatamente com os já registrados no BUG-016 para `/api/deleta/grupo-muscular/{id}`, o que sugere uma causa comum no tratamento de exclusões do backend. A mesma gravação também mostra o cadastro bem-sucedido de um novo grupo e duas edições desse grupo, tratadas em caso próprio (CT-RF58).

O consolidado em 15/11/2026, antes da inclusão de CT-RF58, era de 55 casos documentados (CT-RF01–CT-RF35, CT-RF38–CT-RF56 e CT-RF57): 17 aprovados, 28 reprovados e 10 a validar; 24 defeitos registrados (10 abertos e 14 em triagem) e 28 casos com reteste corretivo pendente. CT-RF09/10 compartilham BUG-005 e CT-RF53 a CT-RF56 compartilham BUG-023, de modo que 28 casos reprovados correspondem a 24 defeitos. Sem nova execução.

---

## Inclusão de 15/11/2026 — CT-RF58

| Caso | Situação | Encaminhamento |
| --- | --- | --- |
| [CT-RF58](Cenario_Teste/CT-RF58_Edicao_Grupo.md) | Reprovado nas evidências | Investigar a rotina de edição do grupo (`/api/edita/grupo/{id}`) quanto ao tratamento do campo status; corrigir e retestar a edição de cada campo isoladamente, incluindo a reativação. |

O defeito [BUG-025](Relatorio-de-Bugs.md#bug-025) está em triagem. Na mesma gravação do CT-RF57, a alteração do campo Status do grupo "Treino sla" (código 11) de "Ativo" para "Inativo" retorna sucesso (`verifica_erro: false`), mas a consulta imediatamente seguinte mostra o registro ainda com o status anterior. Na mesma sessão e no mesmo registro, a alteração do campo Descrição é persistida corretamente, o que isola a falha ao campo `status` e descarta causa geral de sessão, rede ou salvamento. Foi observado também um descompasso de cerca de 4 horas entre o cabeçalho HTTP `data` e o campo `updated_at` da resposta, sem causa determinada e sem relação confirmada com o defeito.

O consolidado em 15/11/2026, antes da inclusão de CT-RF59, era de 56 casos documentados (CT-RF01–CT-RF35, CT-RF38–CT-RF56, CT-RF57 e CT-RF58): 17 aprovados, 29 reprovados e 10 a validar; 25 defeitos registrados (10 abertos e 15 em triagem) e 29 casos com reteste corretivo pendente. CT-RF09/10 compartilham BUG-005 e CT-RF53 a CT-RF56 compartilham BUG-023, de modo que 29 casos reprovados correspondem a 25 defeitos. Sem nova execução.

---

## Inclusão de 15/11/2026 — CT-RF59

| Caso | Situação | Encaminhamento |
| --- | --- | --- |
| [CT-RF59](Cenario_Teste/CT-RF59_Cadastro_Anamnese.md) | Reprovado nas evidências | Investigar as rotinas de servidor de `/api/anamnese/aplicar/{id}` e `/api/anamnese/rascunho/{id}` com acesso a logs, em conjunto com o BUG-016 e o BUG-024 (mesma mensagem genérica); corrigir e retestar o cadastro completo de uma anamnese. |

O defeito [BUG-032](Relatorio-de-Bugs.md#bug-032) está em triagem. Na gravação, sete tentativas de cadastrar uma anamnese para o aluno "Jorge" — quatro pela rota de aplicar e três pela de salvar rascunho, com dois modelos de anamnese (`modelo_id` 3 e 5) e três respostas diferentes — retornam todas HTTP 500 com o mesmo corpo `{"verifica_erro": true, "mensagem": "Erro interno inesperado."}`, coincidindo com o padrão já registrado nos BUG-016 e BUG-024. Nenhuma anamnese é cadastrada com sucesso ao longo da gravação, e o trecho final (1:17 a 1:28), de retorno à listagem, busca e filtros, não produz novos erros.

O consolidado em 15/11/2026, antes da inclusão de CT-RF65 a CT-RF70, era de 57 casos documentados (CT-RF01–CT-RF35, CT-RF38–CT-RF56, CT-RF57, CT-RF58 e CT-RF59): 17 aprovados, 30 reprovados e 10 a validar; 26 defeitos registrados (10 abertos e 16 em triagem) e 30 casos com reteste corretivo pendente. CT-RF09/10 compartilham BUG-005 e CT-RF53 a CT-RF56 compartilham BUG-023, de modo que 30 casos reprovados correspondem a 26 defeitos. Sem nova execução.

---

## Resultado de CT-RF65 a CT-RF70 — Colaboradores

| Caso | Resultado observado | Situação | Defeito |
| --- | --- | --- | --- |
| [CT-RF65](Cenario_Teste/CT-RF65_Data_Nascimento_Futura_Colaborador.md) | Data `18/05/2222`; atualização HTTP 200. | Reprovado | [BUG-026](Relatorio-de-Bugs.md#bug-026) |
| [CT-RF66](Cenario_Teste/CT-RF66_Data_Nascimento_Obrigatoria_Colaborador.md) | Data obrigatória vazia; atualização HTTP 200. | Reprovado | [BUG-027](Relatorio-de-Bugs.md#bug-027) |
| [CT-RF67](Cenario_Teste/CT-RF67_CREF_Formato_Colaborador.md) | CREF `TESTEE`; atualização HTTP 200. | Reprovado, com formato a confirmar | [BUG-028](Relatorio-de-Bugs.md#bug-028) |
| [CT-RF68](Cenario_Teste/CT-RF68_Edicao_Colaborador_Campo_Obrigatorio_Vazio.md) | Campo obrigatório vazio; atualização HTTP 200. | Reprovado | [BUG-029](Relatorio-de-Bugs.md#bug-029) |
| [CT-RF69](Cenario_Teste/CT-RF69_Funcao_Duplicada_Colaborador.md) | Consulta passa de uma para três funções idênticas. | Reprovado | [BUG-030](Relatorio-de-Bugs.md#bug-030) |
| [CT-RF70](Cenario_Teste/CT-RF70_Exclusao_Colaborador_Erro_500.md) | Exclusão retorna HTTP 500 e erro interno. | Reprovado | [BUG-031](Relatorio-de-Bugs.md#bug-031) |

RF65–RF68 precisam de reteste com corpo do POST e reabertura do cadastro para comprovar a persistência. RF69 possui evidência direta da duplicidade. RF70 confirma o erro interno, mas não sua causa.

O consolidado em 15/11/2026, antes da inclusão de CT-RF60, era de 63 casos documentados (CT-RF01–CT-RF35, CT-RF38–CT-RF59 e CT-RF65–CT-RF70): 17 aprovados, 36 reprovados e 10 a validar; 32 defeitos registrados (10 abertos e 22 em triagem) e 36 casos com reteste corretivo pendente. CT-RF09/10 compartilham BUG-005 e CT-RF53 a CT-RF56 compartilham BUG-023, de modo que 36 casos reprovados correspondem a 32 defeitos. Sem nova execução.

---

## Inclusão de 16/11/2026 — CT-RF60

| Caso | Situação | Encaminhamento |
| --- | --- | --- |
| [CT-RF60](Cenario_Teste/CT-RF60_Gestao_Modelos_Anamnese.md) | Aprovado conforme a gravação | Usar como regressão; repetir busca, filtro, cadastro com perguntas do banco, edição e exclusão em versão identificada, capturando os corpos de requisição e resposta. |

Nenhum defeito foi identificado no fluxo avaliado. Na gravação, busca e filtro da listagem, cadastro de um modelo com três perguntas selecionadas do banco de perguntas, duas edições e duas exclusões de modelos retornam HTTP 200 ou 201 em todas as quinze requisições aos endpoints `/api/modelos-anamnese/*`; a única requisição com código de erro em toda a gravação é um *beacon* de analytics do Google (HTTP 499), sem relação com o backend do SIFIT. Dois pontos ficam registrados para confirmação, sem efeito sobre o resultado: o sufixo numérico `1`, comum aos quatro endpoints exercitados, é compatível com a hipótese já registrada em CT-RF59 de que corresponde ao `empresa_id` da conta, e não ao id do modelo; e a leitura da listagem (`GET`) retorna HTTP 201 em vez do 200 mais usual para esse tipo de operação.

O consolidado atual é de 64 casos documentados (CT-RF01–CT-RF35, CT-RF38–CT-RF59, CT-RF60 e CT-RF65–CT-RF70): 18 aprovados, 36 reprovados e 10 a validar; 32 defeitos registrados (10 abertos e 22 em triagem) e 36 casos com reteste corretivo pendente. CT-RF09/10 compartilham BUG-005 e CT-RF53 a CT-RF56 compartilham BUG-023, de modo que 36 casos reprovados correspondem a 32 defeitos. Sem nova execução.

---

## Inclusão de 16/11/2026 — CT-RF61

| Caso | Situação | Encaminhamento |
| --- | --- | --- |
| [CT-RF61](Cenario_Teste/CT-RF61_Gestao_Categorias_Anamnese.md) | Aprovado conforme a gravação | Usar como regressão; repetir filtro, busca, cadastro, edição (ícone, nome e status), cancelamento de edição e exclusão em versão identificada, capturando os corpos de requisição e resposta ainda não registrados. |

Nenhum defeito foi identificado no fluxo avaliado. Na gravação, o filtro por status, a busca por texto, o cadastro de uma categoria, três edições sucessivas (ícone, depois nome, depois status), o cancelamento correto de uma quarta edição sem salvar e a exclusão da categoria retornam HTTP 200 ou 201 em todas as sete requisições aos endpoints `/api/categorias-anamnese/*`, sem nenhuma ocorrência de erro 4xx ou 5xx. O mesmo sufixo numérico `1`, comum aos quatro endpoints exercitados, reforça a hipótese já registrada em CT-RF59 e CT-RF60 de que corresponde ao `empresa_id` da conta, e não ao id do registro; diferentemente de CT-RF60, aqui o cadastro retorna HTTP 201 e as demais operações retornam HTTP 200, um padrão mais previsível, registrado para confirmação com a equipe de desenvolvimento.

O consolidado atual é de 65 casos documentados (CT-RF01–CT-RF35, CT-RF38–CT-RF59, CT-RF60, CT-RF61 e CT-RF65–CT-RF70): 19 aprovados, 36 reprovados e 10 a validar; 32 defeitos registrados (10 abertos e 22 em triagem) e 36 casos com reteste corretivo pendente. CT-RF09/10 compartilham BUG-005 e CT-RF53 a CT-RF56 compartilham BUG-023, de modo que 36 casos reprovados correspondem a 32 defeitos. Sem nova execução.

---

## Inclusão de 16/11/2026 — CT-RF62

| Caso | Situação | Encaminhamento |
| --- | --- | --- |
| [CT-RF62](Cenario_Teste/CT-RF62_Edicao_Pergunta_Anamnese.md) | Reprovado nas evidências — [BUG-044](Relatorio-de-Bugs.md#bug-044) | Investigar a rotina de `alterar` de perguntas de anamnese com acesso a logs; retestar a edição do tipo de resposta e do status em versão corrigida. |

O cadastro de uma nova pergunta de anamnese é concluído com sucesso, mas as quatro tentativas seguintes de editar o tipo de resposta e/ou o status dessa mesma pergunta retornam HTTP 500 em todas as ocorrências, com o mesmo corpo genérico `{"verifica_erro": true, "mensagem": "Erro interno inesperado."}` já observado nos BUG-016, BUG-024 e BUG-032; nenhuma alteração é persistida. O cadastro (`salvar/1`) foi registrado em duplicidade para uma única ação de "Salvar" (HTTP 200 e HTTP 201), no mesmo padrão de duplicação por clique já observado em CT-RF47.

O consolidado atual é de 66 casos documentados (CT-RF01–CT-RF35, CT-RF38–CT-RF59, CT-RF60, CT-RF61, CT-RF62 e CT-RF65–CT-RF70): 19 aprovados, 37 reprovados e 10 a validar; 33 defeitos registrados (10 abertos e 23 em triagem) e 37 casos com reteste corretivo pendente. CT-RF09/10 compartilham BUG-005 e CT-RF53 a CT-RF56 compartilham BUG-023, de modo que 37 casos reprovados correspondem a 33 defeitos. Sem nova execução.

---

## Inclusão de 16/11/2026 — CT-RF74 a CT-RF84

Integração documental dos arquivos RESUMO.txt fornecidos em `C:\Users\Leonardo\Desktop\evidencias`, com data de gravação e análise informada de 16/11/2026. Os Jams não foram reabertos nesta integração; eventos de rede, horários e quadros abaixo são transcritos dos resumos, sem verificação independente. Não houve nova execução do SIFIT, reteste, consulta ao banco, logs ou código.

CT-RF74–CT-RF84 acrescentam oito aprovações e três reprovações conforme os resumos fornecidos, com BUG-035–BUG-037 em triagem. CT-RF83 mantém a classificação do relato, condicionada à confirmação da regra de obrigatoriedade. Os dez casos anteriores a validar permanecem inalterados.

| Caso | Resultado | Defeito | Fontes |
| --- | --- | --- | --- |
| [CT-RF74](Cenario_Teste/CT-RF74_Temas_Prospeccao.md) | Aprovado conforme o resumo da gravação | — | [Evidências](Evidencias/CT-RF74_Temas_Prospeccao/README.md) · [Jam](https://jam.dev/c/5dc9fc15-8e13-4f90-b21f-a49aedc6731e) |
| [CT-RF75](Cenario_Teste/CT-RF75_Detalhes_Lead_Cancelamento.md) | Aprovado conforme o resumo da gravação | — | [Evidências](Evidencias/CT-RF75_Detalhes_Lead_Cancelamento/README.md) · [Jam](https://jam.dev/c/7ef0ee0b-497e-48b8-a57d-cd914558d303) |
| [CT-RF76](Cenario_Teste/CT-RF76_Exclusao_Leads_Confirmacao.md) | Aprovado conforme o resumo da gravação | — | [Evidências](Evidencias/CT-RF76_Exclusao_Leads_Confirmacao/README.md) · [Jam](https://jam.dev/c/2ac5e5ed-b10f-4cc9-9f97-7ba65ca560f8) |
| [CT-RF77](Cenario_Teste/CT-RF77_Cadastro_Lead_Novo_Contato.md) | Aprovado conforme o resumo da gravação | — | [Evidências](Evidencias/CT-RF77_Cadastro_Lead_Novo_Contato/README.md) · [Jam](https://jam.dev/c/29447c6a-90f5-48b2-ac5d-d43cad44a782) |
| [CT-RF78](Cenario_Teste/CT-RF78_Cadastro_Lead_Interessado.md) | Aprovado conforme o resumo da gravação | — | [Evidências](Evidencias/CT-RF78_Cadastro_Lead_Interessado/README.md) · [Jam](https://jam.dev/c/f8735cbf-4043-4467-b43f-3cad7eff0da8) |
| [CT-RF79](Cenario_Teste/CT-RF79_Cadastro_Lead_Aula_Experimental.md) | Aprovado conforme o resumo da gravação | — | [Evidências](Evidencias/CT-RF79_Cadastro_Lead_Aula_Experimental/README.md) · [Jam](https://jam.dev/c/bef3d877-056b-4274-87c3-da37869c54fd) |
| [CT-RF80](Cenario_Teste/CT-RF80_Cadastro_Lead_Proposta.md) | Aprovado conforme o resumo da gravação | — | [Evidências](Evidencias/CT-RF80_Cadastro_Lead_Proposta/README.md) · [Jam](https://jam.dev/c/84f94285-ae5f-4f95-b640-a9b107565aa6) |
| [CT-RF81](Cenario_Teste/CT-RF81_Cadastro_Bandeira_Parcela_Listagem.md) | Reprovado nas evidências resumidas | [BUG-035](Relatorio-de-Bugs.md#bug-035) | [Evidências](Evidencias/CT-RF81_Cadastro_Bandeira_Parcela_Listagem/README.md) · [Jam](https://jam.dev/c/2f0280fb-6b7f-4cf0-a45c-02f8c16b6c5e) |
| [CT-RF82](Cenario_Teste/CT-RF82_Tema_Escuro_Bandeiras.md) | Reprovado nas evidências resumidas | [BUG-036](Relatorio-de-Bugs.md#bug-036) | [Evidências](Evidencias/CT-RF82_Tema_Escuro_Bandeiras/README.md) · [Jam](https://jam.dev/c/ae4dc198-8a42-4451-898a-fb376596c744) |
| [CT-RF83](Cenario_Teste/CT-RF83_Cadastro_Lead_Apenas_Nome.md) | Reprovado conforme o relato; regra de obrigatoriedade a confirmar | [BUG-037](Relatorio-de-Bugs.md#bug-037) | [Evidências](Evidencias/CT-RF83_Cadastro_Lead_Apenas_Nome/README.md) · [Jam](https://jam.dev/c/ef3df03c-16ce-4cb6-b0c7-d04514cab4f6) |
| [CT-RF84](Cenario_Teste/CT-RF84_Cadastro_Lead_Fechado.md) | Aprovado conforme o resumo da gravação | — | [Evidências](Evidencias/CT-RF84_Cadastro_Lead_Fechado/README.md) · [Jam](https://jam.dev/c/775b9003-fdf7-4ad5-8882-15ba606b6674) |

**Consolidado após a inclusão:** 77 casos documentados: 26 aprovados, 41 reprovados e 10 a validar; 37 defeitos registrados (10 abertos e 27 em triagem) e 41 casos com reteste corretivo pendente. CT-RF09/10 compartilham BUG-005 e CT-RF53–CT-RF56 compartilham BUG-023. O total anterior era de 66 casos: 18 aprovados, 38 reprovados e 10 a validar; 34 defeitos.

**Limites e encaminhamento:** as aprovações se restringem ao que os resumos descrevem. CT-RF74 não comprova persistência do tema; CT-RF75 não comprova o telefone após reabertura; CT-RF76 não cobre cancelamento da exclusão. Os cadastros de estágio não comprovam fluxos comerciais posteriores ou reabertura de todos os campos. CT-RF81 não determina a causa da divergência nem a persistência no banco; CT-RF82 não constitui auditoria formal de acessibilidade; CT-RF83 aguarda regra de produto; CT-RF84 não possui corpo da resposta de salvamento disponível no resumo. Retestes e verificações adicionais seguem no plano e nos casos, sem resultado de execução atribuído nesta integração.

## Inclusão de 15/11/2026 — CT-RF85 a CT-RF90

| Caso | Situação | Encaminhamento |
| --- | --- | --- |
| [CT-RF85](Cenario_Teste/CT-RF85_Tema_Notificacoes_Prospeccao.md) | Aprovado conforme a gravação | Usar como regressão; persistência após recarga e notificações pendentes exigem execuções adicionais. |
| [CT-RF86](Cenario_Teste/CT-RF86_Busca_Leads_Prospeccao.md) | Aprovado conforme a gravação | Usar como regressão; regra de correspondência, busca por e-mail, telefone e código e resultado vazio exigem execuções adicionais. |
| [CT-RF87](Cenario_Teste/CT-RF87_Filtro_Estagio_Leads.md) | Aprovado conforme a gravação | Usar como regressão; demais estágios, combinação com a busca e estágio sem leads exigem execuções adicionais. |
| [CT-RF88](Cenario_Teste/CT-RF88_Cadastro_Lead_Prospeccao.md) | A validar — regra ou contexto pendente | Confirmar se o segundo POST gerou registro adicional, capturando corpos e respostas, e testar campos obrigatórios; registrar defeito apenas se houver duplicidade confirmada. |
| [CT-RF89](Cenario_Teste/CT-RF89_Telefone_Lead_Sem_Validacao.md) | Reprovado nas evidências | Confirmar a regra do campo, reproduzir com a validação visível e retestar telefones válidos e inválidos e a persistência. |
| [CT-RF90](Cenario_Teste/CT-RF90_Edicao_Lead_Prospeccao.md) | Aprovado conforme a gravação | Usar como regressão; edição dos demais campos, persistência após recarga e campos obrigatórios exigem execuções adicionais. |

O defeito [BUG-038](Relatorio-de-Bugs.md#bug-038) está em triagem. O ponto a validar (CT-RF88) não gera defeito antes da confirmação da duplicidade de criação.

O consolidado atual é de 60 casos documentados (CT-RF01–CT-RF35, CT-RF38–CT-RF56 e CT-RF85–CT-RF90): 21 aprovados, 28 reprovados e 11 a validar; 24 defeitos registrados (10 abertos e 14 em triagem) e 28 casos com reteste corretivo pendente. CT-RF09/10 compartilham BUG-005 e CT-RF53 a CT-RF56 compartilham BUG-023, de modo que 28 casos reprovados correspondem a 24 defeitos. Sem nova execução.

## Inclusão de 15/11/2026 — CT-RF91 a CT-RF103

| Caso | Situação | Encaminhamento |
| --- | --- | --- |
| [CT-RF91](Cenario_Teste/CT-RF91_Filtros_Contas_Pagar.md) | A validar — regra ou contexto pendente | Reexecutar com contas de controle e exercitar cada critério isolado e a combinação. |
| [CT-RF92](Cenario_Teste/CT-RF92_Cadastro_Conta_Colaborador_Sem_Colaborador.md) | Reprovado nas evidências | Confirmar a regra, reproduzir com a validação visível e retestar envio válido e inválido e a persistência. |
| [CT-RF93](Cenario_Teste/CT-RF93_Busca_Colaborador_Conta_Pagar.md) | A validar — regra ou contexto pendente | Reexecutar com um nome existente e confirmar a mensagem de resultado vazio. |
| [CT-RF94](Cenario_Teste/CT-RF94_Visualizacao_Conta_Pagar.md) | Aprovado conforme a gravação | Usar como regressão; contas de outros tipos e status e o rótulo do tipo exigem execuções adicionais. |
| [CT-RF95](Cenario_Teste/CT-RF95_Exclusao_Conta_Pagar.md) | Aprovado conforme a gravação | Usar como regressão; cancelar, recarga e contas vinculadas exigem execuções adicionais. |
| [CT-RF96](Cenario_Teste/CT-RF96_Variaveis_Preview_Modelo_Contrato.md) | Aprovado conforme a gravação | Usar como regressão; demais variáveis, formatação complexa e texto gravado exigem execuções adicionais. |
| [CT-RF97](Cenario_Teste/CT-RF97_Cadastro_Modelo_Contrato.md) | Aprovado conforme a gravação | Usar como regressão; campos obrigatórios e conferência do texto gravado exigem execuções adicionais. |
| [CT-RF98](Cenario_Teste/CT-RF98_Listagem_Modelos_Contrato_Vazia.md) | Reprovado nas evidências | Reproduzir comparando resposta e tabela, investigar a renderização e retestar após correção. |
| [CT-RF99](Cenario_Teste/CT-RF99_Filtros_Planos.md) | Aprovado conforme a gravação | Usar como regressão; filtro por Status, combinação de critérios e resultado vazio exigem execuções adicionais. |
| [CT-RF100](Cenario_Teste/CT-RF100_Tema_Notificacoes_Planos.md) | Aprovado conforme a gravação | Usar como regressão; persistência após recarga e notificações pendentes exigem execuções adicionais. |
| [CT-RF101](Cenario_Teste/CT-RF101_Cadastro_Plano.md) | Aprovado conforme a gravação | Usar como regressão; campos obrigatórios, valores extremos e conferência na listagem exigem execuções adicionais. |
| [CT-RF102](Cenario_Teste/CT-RF102_Contador_Ativos_Planos.md) | Reprovado nas evidências | Reproduzir com a base e o contrato do cartão conhecidos e retestar o cartão após cadastro, edição e alteração de status. |
| [CT-RF103](Cenario_Teste/CT-RF103_Edicao_Plano.md) | Aprovado conforme a gravação | Usar como regressão; persistência após recarga e demais campos exigem execuções adicionais. |

Os defeitos [BUG-039](Relatorio-de-Bugs.md#bug-039), [BUG-040](Relatorio-de-Bugs.md#bug-040) e [BUG-041](Relatorio-de-Bugs.md#bug-041) estão em triagem. Os pontos a validar (CT-RF91 e CT-RF93) não geram defeito antes da confirmação dos dados de controle e da mensagem de resultado vazio.

O consolidado atual é de 73 casos documentados (CT-RF01–CT-RF35, CT-RF38–CT-RF56 e CT-RF85–CT-RF103): 29 aprovados, 31 reprovados e 13 a validar; 27 defeitos registrados (10 abertos e 17 em triagem) e 31 casos com reteste corretivo pendente. CT-RF09/10 compartilham BUG-005 e CT-RF53 a CT-RF56 compartilham BUG-023, de modo que 31 casos reprovados correspondem a 27 defeitos. Sem nova execução.

## Inclusão de 16/11/2026 — CT-RF104 a CT-RF108

| Caso | Situação | Encaminhamento |
| --- | --- | --- |
| [CT-RF104](Cenario_Teste/CT-RF104_Filtros_Tipos_Pagamento.md) | A validar — regra ou contexto pendente | Reexecutar com critérios conhecidos e capturar o valor escolhido, a listagem e a rede. |
| [CT-RF105](Cenario_Teste/CT-RF105_Cadastro_Tipo_Pagamento_Status.md) | Reprovado nas evidências | Confirmar a regra do status, reproduzir conferindo corpo, resposta e coluna Status e retestar com status Ativo e Inativo. |
| [CT-RF106](Cenario_Teste/CT-RF106_Edicao_Tipo_Pagamento.md) | Aprovado conforme a gravação | Usar como regressão; persistência após recarga, edição de nome e tipo e a coluna Status exigem execuções adicionais. |
| [CT-RF107](Cenario_Teste/CT-RF107_Exclusao_Tipo_Pagamento_Em_Uso.md) | Reprovado nas evidências | Confirmar a regra, reproduzir com tipo em uso e sem uso e retestar código HTTP, resposta e mensagem. |
| [CT-RF108](Cenario_Teste/CT-RF108_Tema_Notificacoes_Tipos_Pagamento.md) | Aprovado conforme a gravação | Usar como regressão visual; conferir diálogos e modais no tema Escuro e a persistência do tema. |

Os defeitos [BUG-042](Relatorio-de-Bugs.md#bug-042) e [BUG-043](Relatorio-de-Bugs.md#bug-043) estão em triagem. O ponto a validar (CT-RF104) não gera defeito antes da confirmação da filtragem e dos valores escolhidos.

O consolidado na inclusão de Tipos de Pagamento era de 104 casos documentados (CT-RF01–CT-RF35, CT-RF38–CT-RF59, CT-RF60, CT-RF61, CT-RF62, CT-RF65–CT-RF84, CT-RF85–CT-RF103 e CT-RF104–CT-RF108): 42 aprovados, 48 reprovados e 14 a validar; 44 defeitos registrados (10 abertos e 34 em triagem) e 48 casos com reteste corretivo pendente. CT-RF09/10 compartilham BUG-005 e CT-RF53 a CT-RF56 compartilham BUG-023, de modo que 48 casos reprovados correspondem a 44 defeitos. Sem nova execução.

## Inclusão de 17/11/2026 — Modelos de Ficha

| Caso | Situação | Encaminhamento |
| --- | --- | --- |
| [CT-RF109](Cenario_Teste/CT-RF109_Modelo_Ficha_Sem_Nome.md) | Aprovado conforme a gravação | Usar como regressão e verificar nome composto apenas por espaços e submissão com todos os campos vazios. |
| [CT-RF110](Cenario_Teste/CT-RF110_Cancelar_Cadastro_Modelo_Ficha.md) | Aprovado conforme a gravação | Usar como regressão e reabrir o formulário após o cancelamento para conferir a limpeza dos campos. |
| [CT-RF111](Cenario_Teste/CT-RF111_Busca_Modelo_Ficha_Codigo_Inexistente.md) | A validar — regra ou contexto pendente | Reexecutar com um código existente e um comprovadamente ausente na mesma base. |
| [CT-RF112](Cenario_Teste/CT-RF112_Busca_Modelo_Ficha_Titulo_Inexistente.md) | A validar — regra ou contexto pendente | Reexecutar com título existente e inexistente e confirmar o critério de correspondência com o produto. |
| [CT-RF113](Cenario_Teste/CT-RF113_Busca_Modelo_Ficha_Filtros_Combinados.md) | A validar — regra ou contexto pendente | Reexecutar com registros que correspondam a todos os filtros e a apenas parte deles. Confirmar onde a filtragem é feita. |
| [CT-RF114](Cenario_Teste/CT-RF114_Limpeza_Filtros_Modelos_Ficha.md) | Aprovado conforme a gravação | Usar como regressão de interface e conferir o uso dos campos com teclado e mouse. |
| [CT-RF115](Cenario_Teste/CT-RF115_Nova_Busca_Modelos_Ficha_Sem_Filtros.md) | A validar — regra ou contexto pendente | Reexecutar com listagem padrão populada, pesquisa restritiva e comparação dos registros após a nova busca. |

O consolidado na inclusão dos CT-RF109 a CT-RF115 era de 111 casos documentados: 45 aprovados, 48 reprovados e 18 a validar; 44 defeitos registrados (10 abertos e 34 em triagem) e 48 casos com reteste corretivo pendente. Os resultados acima se limitam ao material do Jam.

## Inclusão de 17/11/2026 — Configurações e Modelos de Ficha (CT-RF116–CT-RF121)

| Caso | Situação | Encaminhamento |
| --- | --- | --- |
| [CT-RF116](Cenario_Teste/CT-RF116_Configuracoes_Dias_Ausencia_Vazio.md) | A validar — regra ou contexto pendente | Confirmar com o produto a regra para vazio e zero. Repetir com vazio, zero explícito e os limites da faixa. |
| [CT-RF117](Cenario_Teste/CT-RF117_Configuracoes_Cancelar_Alteracao.md) | Aprovado conforme a gravação | Usar como regressão e repetir com múltiplos campos alterados na mesma aba. |
| [CT-RF118](Cenario_Teste/CT-RF118_Configuracoes_Trabalha_Com_Turmas.md) | Aprovado conforme a gravação | Usar como regressão para persistência de ambos os estados. Verificar separadamente os efeitos sobre o módulo de turmas. |
| [CT-RF119](Cenario_Teste/CT-RF119_Configuracoes_Academia_Marcada_Box.md) | Aprovado conforme a gravação | Usar como regressão da configuração e da navegação. Conferir as permissões internas em um cenário dedicado. |
| [CT-RF120](Cenario_Teste/CT-RF120_Configuracoes_Acesso_Desktop.md) | Aprovado conforme a gravação | Usar como regressão da persistência e do cartão. Validar o acesso no aplicativo desktop em um caso próprio. |
| [CT-RF121](Cenario_Teste/CT-RF121_Cadastro_Modelo_Ficha_Erro_500.md) | Reprovado nas evidências | Reproduzir com dados de teste distintos, investigar a falha do endpoint e conferir a listagem e o vínculo após a correção. |

Na inclusão dos CT-RF116 a CT-RF121, o consolidado era de 117 casos documentados: 49 aprovados, 49 reprovados e 19 a validar. 45 defeitos registrados (10 abertos e 35 em triagem) e 49 casos com reteste corretivo pendente.

## Inclusão de 17/11/2026 — Inteligência e Configurações (CT-RF122–CT-RF127)

| Caso | Situação | Encaminhamento |
| --- | --- | --- |
| [CT-RF122](Cenario_Teste/CT-RF122_Resultados_IA_Filtro_90_Dias.md) | Aprovado conforme a gravação | Usar como regressão e criar dados nas datas-limite dos períodos para conferir a inclusão e a exclusão. |
| [CT-RF123](Cenario_Teste/CT-RF123_Central_Resultados_IA_Execucao_Evasao.md) | Aprovado conforme a gravação | Usar como regressão da integração entre telas. Verificar entrega pelo canal em um caso dedicado, com destinatários de teste. |
| [CT-RF124](Cenario_Teste/CT-RF124_Configuracoes_Abas_Biometria_Senha.md) | Reprovado nas evidências | Corrigir o mascaramento por padrão e retestar com credenciais fictícias, incluindo a troca de abas e a recarga. |
| [CT-RF125](Cenario_Teste/CT-RF125_Configuracoes_Salvar_Dias_Ausencia_Valido.md) | Aprovado conforme a gravação | Usar como regressão de salvamento. Verificar os limites do campo e o impacto na listagem de clientes ausentes. |
| [CT-RF126](Cenario_Teste/CT-RF126_Configuracoes_Dias_Ausencia_Negativo.md) | Reprovado nas evidências | Aplicar validação na gravação da configuração e retestar com -1, um inteiro válido e o limite mínimo definido pelo produto. |
| [CT-RF127](Cenario_Teste/CT-RF127_Configuracoes_Dias_Ausencia_Texto.md) | A validar — regra ou contexto pendente | Confirmar a regra de vazio com o produto e repetir a digitação e a colagem de texto, conferindo também a recarga. |

Na inclusão dos CT-RF122 a CT-RF127, o consolidado era de 123 casos documentados: 52 aprovados, 51 reprovados e 20 a validar. 47 defeitos registrados (10 abertos e 37 em triagem) e 51 casos com reteste corretivo pendente.

## Inclusão de 17/11/2026 — Inteligência e Automação (CT-RF128–CT-RF133)

| Caso | Situação | Encaminhamento |
| --- | --- | --- |
| [CT-RF128](Cenario_Teste/CT-RF128_Central_Configuracao_Risco_Evasao_Cancelar.md) | Aprovado conforme a gravação | Usar como regressão de abertura e fechamento. Em um caso complementar, alterar uma opção de teste e conferir o descarte após cancelar. |
| [CT-RF129](Cenario_Teste/CT-RF129_Central_Aniversariantes_Previa_Risco.md) | Reprovado nas evidências | Corrigir o conteúdo da prévia e retestar separadamente Aniversariantes e Risco de Evasão. |
| [CT-RF130](Cenario_Teste/CT-RF130_Central_Recursos_Em_Desenvolvimento.md) | Aprovado conforme a gravação | Usar como regressão do estado indisponível e conferir a navegação por teclado em execução complementar. |
| [CT-RF131](Cenario_Teste/CT-RF131_Resultados_IA_Filtro_Hoje.md) | Aprovado conforme a gravação | Usar como regressão e conferir o recorte com eventos antes e depois da virada do dia. |
| [CT-RF132](Cenario_Teste/CT-RF132_Resultados_IA_Filtro_7_Dias.md) | Aprovado conforme a gravação | Usar como regressão e preparar dados nos dias de fronteira para verificar inclusão e exclusão. |
| [CT-RF133](Cenario_Teste/CT-RF133_Resultados_IA_Filtro_30_Dias.md) | Aprovado conforme a gravação | Usar como regressão e retestar com registros preparados no limite de 30 dias. |

129 casos documentados: 57 aprovados, 52 reprovados e 20 a validar. 48 defeitos registrados (10 abertos e 38 em triagem) e 52 casos com reteste corretivo pendente.

---

[← Início](../README.md) · [Cenários de teste](Cenario_Teste/) · [Evidências de Clientes](Evidencias/CT-RF03_Filtros_Clientes/README.md)
