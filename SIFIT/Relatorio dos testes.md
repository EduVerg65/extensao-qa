# 📊 Relatório de Testes — SIFIT

**Escopo:** 60 casos documentados (CT-RF01–CT-RF35, CT-RF38–CT-RF56 e CT-RF58–CT-RF63) — autenticação, recuperação, perfil, Clientes, financeiro, página inicial e dashboard, modalidades / tema de SifitBox, Categorias Crossfit, Avaliações, Exercícios, Grupos Musculares, Objetivos de Treino cadastro de categorias com código automático, SifitBox – Turmas, Pagar.me, Configurações, Despesas Fixas, Relatórios e Prospecção (leads).

**Datas das gravações do Jam:** CT-RF01 em 23/10/2026; CT-RF02_ERRO em 22/10/2026 às 21:45 BRT; CT-RF03 não confirmada; CT-RF04_loginComSucesso em 13/11/2026; CT-RF05–CT-RF20 em 14/11/2026; CT-RF21 em 15/11/2026 às 15:07:51,265 BRT; CT-RF22–28 em 15/11/2026 às 15:25, 15:40, 15:38, 15:35, 16:11, 16:08 e 16:07 BRT; CT-RF29–33 em 15/11/2026 às 15h56 BRT (uma única gravação); CT-RF34 em 15/11/2026 às 17:23 BRT; CT-RF35 em 15/11/2026 às 18:13 BRT; CT-RF38 em 15/11/2026 às 18:41 BRT; CT-RF39–41 em 15/11/2026 às 18:51 BRT (uma única gravação); CT-RF42–45 às 19:06, CT-RF46–49 às 19:07 e CT-RF50–56 às 19:09 e CT-RF58–63 às 21:52 BRT (uma gravação por grupo).

**Data da revisão documental:** 15/11/2026, com integração de CT-RF22–CT-RF35, CT-RF38–CT-RF56 e CT-RF58–CT-RF63; BUG-011–BUG-024 em triagem. Resultados anteriores preservados.

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

CT-RF30 acrescenta uma reprovação e o BUG-017 (imagens dos grupos musculares com HTTP 422); CT-RF31–33 acrescentam três aprovações limitadas aos exemplos gravados. O **CT-RF35** acrescenta uma reprovação e o BUG-019: o cadastro de objetivo de treino retorna HTTP 500 em duas ocorrências, com o diálogo "Erro ao salvar objetivo" e a listagem sem registros; o corpo da requisição e da resposta não foi capturado e a causa não foi determinada. O **CT-RF38** acrescenta uma aprovação limitada ao exemplo gravado: o cadastro de categoria cria o registro apenas com o nome (HTTP 201), o código 9 é atribuído pelo sistema e o filtro por código localiza o novo registro; sem defeito. O **CT-RF39** acrescenta uma aprovação (cadastro de modalidade com HTTP 201); o **CT-RF40** acrescenta um ponto a validar (exclusão por lixeira que inativa os registros, regra a confirmar); o **CT-RF41** acrescenta uma reprovação e o BUG-020 (cadastro de turma sem modalidade, sem retorno visível; validação nativa não confirmada). CT-RF42 a CT-RF45 (Pagar.me e Configurações) acrescentam uma aprovação (criação de cobrança), dois pontos a validar (saque e salvamento das configurações) e uma reprovação com o BUG-021 (painel que mantém Recebimentos ao trocar o período); CT-RF46 a CT-RF49 (Despesas Fixas) acrescentam três aprovações (filtros, exclusão e edição) e um ponto a validar (cadastro com duas requisições de criação); CT-RF50 a CT-RF56 (Relatórios) acrescentam uma aprovação (Matrículas), um ponto a validar (Contas a Pagar sem registros) e cinco reprovações, com o BUG-022 (Contas a Receber sem valor) e o BUG-023 (quatro relatórios com arquivo vazio de 0 bytes). CT-RF58 a CT-RF63 (Prospecção) acrescentam quatro aprovações (tema e notificações, busca, filtro por estágio e edição), um ponto a validar (cadastro de lead com duas requisições de criação) e uma reprovação com o BUG-024 (telefone com 30 dígitos aceito sem validação). As contagens consolidadas são:

| Casos documentados | Aprovados | Reprovados | A validar | Defeitos registrados | Casos com reteste corretivo pendente |
| :---: | :---: | :---: | :---: | :---: | :---: |
| 60 | 21 | 28 | 11 | 24 (10 abertos + 14 em triagem) | 28 |

Os 28 retestes incluem CT-RF22/24/26/27/28/29/30/35/41/45/51/53/54/55/56/62, sujeitos à confirmação funcional e técnica. As contagens representam os casos documentados com base nas fontes indicadas, sem novas execuções nesta revisão. As nove variações planejadas para o reteste do CT-RF03 não foram executadas e não são contabilizadas como testes adicionais realizados.

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
| [CT-RF58](Cenario_Teste/CT-RF58_Tema_Notificacoes_Prospeccao.md) | [RF58](Analise%20de%20requisitos.md#rf58) | Trocar o tema, gravar a escolha e abrir o painel de notificações. | Tema escuro e claro aplicados com POST usuario/tema (HTTP 200); painel de Notificações aberto sem pendências. | Aprovado conforme a gravação | Nenhum no fluxo avaliado |
| [CT-RF59](Cenario_Teste/CT-RF59_Busca_Leads_Prospeccao.md) | [RF59](Analise%20de%20requisitos.md#rf59) | Apresentar apenas os leads correspondentes e restaurar a lista ao limpar. | Termos digitados reduzem a lista (códigos 3 e 7; 4 e 10 com "tes"); campo vazio restaura os 7 leads. | Aprovado conforme a gravação | Nenhum no fluxo avaliado |
| [CT-RF60](Cenario_Teste/CT-RF60_Filtro_Estagio_Leads.md) | [RF60](Analise%20de%20requisitos.md#rf60) | Apresentar apenas os leads do estágio e restaurar a lista ao limpar. | Novo Contato lista os leads 7 e 8; Proposta lista o lead 4; Limpar restaura os 7 leads. | Aprovado conforme a gravação | Nenhum no fluxo avaliado |
| [CT-RF61](Cenario_Teste/CT-RF61_Cadastro_Lead_Prospeccao.md) | [RF61](Analise%20de%20requisitos.md#rf61) | Uma única criação e um único lead na listagem. | Lead 10 criado e listado (Leads 7 → 8); um clique gerou dois POST salvar-lead/1 (HTTP 200); segunda resposta não capturada. | A validar — regra ou contexto pendente | Sem defeito confirmado |
| [CT-RF62](Cenario_Teste/CT-RF62_Telefone_Lead_Sem_Validacao.md) | [RF62](Analise%20de%20requisitos.md#rf62) | Rejeitar telefone com tamanho ou formato inválido. | Telefone de 30 dígitos aceito e gravado (lead 10), sem máscara nem mensagem. | Reprovado nas evidências | [BUG-024](Relatorio-de-Bugs.md#bug-024), em triagem |
| [CT-RF63](Cenario_Teste/CT-RF63_Edicao_Lead_Prospeccao.md) | [RF63](Analise%20de%20requisitos.md#rf63) | Abrir o lead, gravar a alteração sem erro e refletir na lista. | Lead 10 aberto pela lupa; nome alterado para "testetete"; POST atualizar-lead/1 com HTTP 200; listagem atualizada. | Aprovado conforme a gravação | Nenhum no fluxo avaliado |

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
| [BUG-024](Relatorio-de-Bugs.md#bug-024) | Telefone do lead aceita 30 dígitos sem máscara nem validação | Média, proposta | Média, proposta | Em triagem; regra do campo e reteste pendentes. |

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

### CT-RF58 a CT-RF63

| Item | Registro |
| --- | --- |
| Página / API | https://sifit.centrion.com.br/prospeccao / https://backendsifit.centrion.com.br |
| Data / duração | 15/11/2026, 21:52 BRT / 1 min 2 s; uma única gravação cobre os casos do grupo. |
| Navegador / sistema / janela | Chrome 157.0.8103.78 / Windows (x86) 11 / 1920 × 911, conforme Info; autor do Jam: Gustavo Pelissari Oenning. |
| Material e limites | Painéis Info, Console, Network e Actions do Jam, corpos de requisições e respostas selecionadas e quadros do vídeo, com uma pasta local por caso. Corpo e resposta da segunda criação, filtragem local e persistência não confirmados; quadros com e-mail digitado não foram incluídos; sem inspeção de código ou nova execução. |

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
| [Jam — Prospecção](https://jam.dev/c/308607ff-8abc-40af-8c7c-429ce506ed64) e evidências por caso | CT-RF58: quatro `POST usuario/tema` (HTTP 200) e painel de Notificações sem pendências. CT-RF59: busca por texto reduz a listagem (códigos 3 e 7; 4 e 10 com "tes") sem requisição de rede. CT-RF60: filtro por estágio (Novo Contato: códigos 7 e 8; Proposta: código 4) e Limpar. CT-RF61: um clique em Salvar Lead gera dois `POST salvar-lead` com HTTP 200 e um lead novo (código 10). CT-RF62: telefone de 30 dígitos aceito e gravado sem máscara nem mensagem. CT-RF63: `POST atualizar-lead` com HTTP 200 e nome atualizado na listagem. |

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

O consolidado atual é de 54 casos documentados (CT-RF01–CT-RF35 e CT-RF38–CT-RF56): 17 aprovados, 27 reprovados e 10 a validar; 23 defeitos registrados (10 abertos e 13 em triagem) e 27 casos com reteste corretivo pendente. CT-RF09/10 compartilham BUG-005 e CT-RF53 a CT-RF56 compartilham BUG-023, de modo que 27 casos reprovados correspondem a 23 defeitos. Sem nova execução.

## Inclusão de 15/11/2026 — CT-RF58 a CT-RF63

| Caso | Situação | Encaminhamento |
| --- | --- | --- |
| [CT-RF58](Cenario_Teste/CT-RF58_Tema_Notificacoes_Prospeccao.md) | Aprovado conforme a gravação | Usar como regressão; persistência após recarga e notificações pendentes exigem execuções adicionais. |
| [CT-RF59](Cenario_Teste/CT-RF59_Busca_Leads_Prospeccao.md) | Aprovado conforme a gravação | Usar como regressão; regra de correspondência, busca por e-mail, telefone e código e resultado vazio exigem execuções adicionais. |
| [CT-RF60](Cenario_Teste/CT-RF60_Filtro_Estagio_Leads.md) | Aprovado conforme a gravação | Usar como regressão; demais estágios, combinação com a busca e estágio sem leads exigem execuções adicionais. |
| [CT-RF61](Cenario_Teste/CT-RF61_Cadastro_Lead_Prospeccao.md) | A validar — regra ou contexto pendente | Confirmar se o segundo POST gerou registro adicional, capturando corpos e respostas, e testar campos obrigatórios; registrar defeito apenas se houver duplicidade confirmada. |
| [CT-RF62](Cenario_Teste/CT-RF62_Telefone_Lead_Sem_Validacao.md) | Reprovado nas evidências | Confirmar a regra do campo, reproduzir com a validação visível e retestar telefones válidos e inválidos e a persistência. |
| [CT-RF63](Cenario_Teste/CT-RF63_Edicao_Lead_Prospeccao.md) | Aprovado conforme a gravação | Usar como regressão; edição dos demais campos, persistência após recarga e campos obrigatórios exigem execuções adicionais. |

O defeito [BUG-024](Relatorio-de-Bugs.md#bug-024) está em triagem. O ponto a validar (CT-RF61) não gera defeito antes da confirmação da duplicidade de criação.

O consolidado atual é de 60 casos documentados (CT-RF01–CT-RF35, CT-RF38–CT-RF56 e CT-RF58–CT-RF63): 21 aprovados, 28 reprovados e 11 a validar; 24 defeitos registrados (10 abertos e 14 em triagem) e 28 casos com reteste corretivo pendente. CT-RF09/10 compartilham BUG-005 e CT-RF53 a CT-RF56 compartilham BUG-023, de modo que 28 casos reprovados correspondem a 24 defeitos. Sem nova execução.

---

[← Início](../README.md) · [Cenários de teste](Cenario_Teste/) · [Evidências de Clientes](Evidencias/CT-RF03_Filtros_Clientes/README.md)
