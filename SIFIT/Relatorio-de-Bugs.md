# 🐞 Relatório de Bugs — SIFIT

**Escopo:** defeitos de 158 casos documentados (CT-RF01–CT-RF35, CT-RF38–CT-RF62 e CT-RF65–CT-RF162): recuperação, Perfil, Clientes, financeiro, página inicial e dashboard, tema, modalidades, categorias, avaliações, exercícios, grupos musculares, objetivos de treino, SifitBox – Turmas, Pagar.me, configurações, despesas fixas, relatórios, grupos (treino), fichas de anamnese, colaboradores, modelos de anamnese, categorias de anamnese, perguntas de anamnese, Prospecção, Bandeiras de Cartão, Contas a Pagar, Modelos de Contrato, Planos, Tipos de Pagamento, Modelos de Ficha, Central de Automações, Integrações de WhatsApp e Configurações de Avaliação, Aniversário, Pagamento, Design e Biometria, além de Aplicativo. CT-RF60 (Modelos de Anamnese) e CT-RF61 (Categorias de Anamnese) são aprovados conforme a gravação, sem defeito identificado. CT-RF62 (Perguntas Anamnese) é reprovado nas evidências e acrescenta o BUG-044 (44 defeitos registrados).

**Ambientes:** CT-RF01 em https://sifitalfa.centrion.com.br/login; CT-RF02_ERRO em https://sifit.centrion.com.br/profile. CT-RF03: URL do frontend não confirmada; backend informado em `https://backendsifit.centrion.com.br/api/clientesPorNome/1`.

**Datas das gravações do Jam:** CT-RF01 em 23/10/2026; CT-RF02_ERRO em 22/10/2026 às 21:45 BRT; CT-RF03 não confirmada.

**Atualização documental:** 18/11/2026 — 52 defeitos registrados: 10 abertos (BUG-001 a BUG-010) e 42 em triagem (BUG-011 a BUG-052). BUG-019 registra o HTTP 500 no cadastro de objetivo de treino, BUG-020 a ausência de retorno visível no cadastro de turma sem modalidade, BUG-024 e BUG-025 cobrem Grupos (treino), BUG-026–BUG-031 cobrem Colaboradores e BUG-032 o HTTP 500 no cadastro de anamnese (aplicar e rascunho), todos sem causa técnica confirmada. CT-RF60 (Modelos de Anamnese) e CT-RF61 (Categorias de Anamnese), incluídos em 16/11/2026, são aprovados conforme a gravação e não geram novo defeito. BUG-038 a BUG-041 cobrem Prospecção (telefone), Contas a Pagar, Modelos de Contrato e Planos; BUG-042 e BUG-043 cobrem Tipos de Pagamento (status e exclusão); BUG-044, também em 16/11/2026, registra o HTTP 500 na edição do tipo de resposta de pergunta de anamnese (CT-RF62); BUG-035 e BUG-036 cobrem Bandeiras; BUG-037 registra o relato de cadastro de lead apenas com nome, com regra a confirmar. As análises anteriores foram preservadas.

**Gravação de CT-RF104–CT-RF108:** 15/11/2026, Tipos de Pagamento, 22:03 BRT, Chrome 157.0.8103.78 / Windows 11; uma única gravação; evidência e limites no BUG-042 e no BUG-043.

**Gravação de CT-RF99–CT-RF103:** 15/11/2026, Planos, 21:54 BRT, Chrome 157.0.8103.78 / Windows 11; uma única gravação; evidência e limites no BUG-041.

**Gravação de CT-RF96–CT-RF98:** 15/11/2026, Modelos de Contrato, 21:55 BRT, Chrome 157.0.8103.78 / Windows 11; uma única gravação; evidência e limites no BUG-040.

**Gravação de CT-RF91–CT-RF95:** 15/11/2026, Contas a Pagar, 21:58 BRT, Chrome 157.0.8103.78 / Windows 11; uma única gravação; evidência e limites no BUG-039.

**Gravação de CT-RF85–CT-RF90:** 15/11/2026, Prospecção, 21:52 BRT, Chrome 157.0.8103.78 / Windows 11; uma única gravação; evidência e limites no BUG-038.

**Gravação de CT-RF57 e CT-RF58:** 15/11/2026, Grupos, 21h03 BRT, Chrome 157.0.8103.78 / Windows 11; mesma gravação, evidências e limites no BUG-024 e no BUG-025. **Gravação de CT-RF59:** 15/11/2026, Fichas de Anamnese, 22h07 BRT, Chrome 157.0.8103.78 / Windows 11; evidências e limites no BUG-032. **Gravações de CT-RF65–CT-RF70:** 15/11/2026, Colaboradores, entre 22:06 e 22:13 BRT, Chrome 157.0.8103.78 / Windows 11; evidências e limites no BUG-026 a BUG-031. **Gravação de CT-RF60:** 15/11/2026, Modelos de Anamnese, 23h34 BRT, Chrome 157.0.8103.78 / Windows 11; aprovada conforme a gravação, sem defeito — ver [CT-RF60](Cenario_Teste/CT-RF60_Gestao_Modelos_Anamnese.md). **Gravação de CT-RF61:** 16/11/2026, Categorias de Anamnese, 15h24 BRT, Chrome 157.0.8103.78 / Windows 11; aprovada conforme a gravação, sem defeito — ver [CT-RF61](Cenario_Teste/CT-RF61_Gestao_Categorias_Anamnese.md). **Gravação de CT-RF62:** 16/11/2026, Perguntas Anamnese, 15h57 BRT, Chrome 157.0.8103.78 / Windows 11; reprovada nas evidências, com o BUG-044 — ver [CT-RF62](Cenario_Teste/CT-RF62_Edicao_Pergunta_Anamnese.md).

**Padronização documental:** 13/11/2026, sem alteração do status dos defeitos.

**Caso aprovado incluído em 13/11/2026:** [CT-RF04_loginComSucesso](Cenario_Teste/CT-RF04_loginComSucesso.md), vinculado ao RF04, não gerou defeito para o fluxo avaliado. O [Jam de login](https://jam.dev/c/5e4a28be-4e80-43d3-9587-1b113723cc38) mostra acesso ao dashboard após autenticação. Essa aprovação não altera os três bugs existentes; resultados e limites constam no [relatório dos testes](Relatorio%20dos%20testes.md).

**Gravação de CT-RF42–CT-RF45:** 15/11/2026, Pagar.me e Configurações, 19:06 BRT, Chrome 157.0.8103.78 / Windows 11; uma única gravação; evidência e limites no BUG-021.

**Gravação de CT-RF50–CT-RF56:** 15/11/2026, Relatórios, 19:09 BRT, Chrome 157.0.8103.78 / Windows 11; uma única gravação e oito arquivos PDF baixados; evidência e limites no BUG-022 e no BUG-023.

**Gravação de CT-RF39–CT-RF41:** 15/11/2026, SifitBox – Turmas, 18:51 BRT, Chrome 157.0.8103.78 / Windows 11; uma única gravação; evidência e limites no BUG-020.

**Gravação de CT-RF35:** 15/11/2026, Objetivos Treino, 18:13 BRT, Chrome 157.0.8103.78 / Windows 11; evidência e limites no BUG-019.

**Gravação de CT-RF21:** 15/11/2026, Avaliações, início às 15:07:51,265 BRT; evidência e limites no BUG-010.

**Novas gravações de CT-RF05–CT-RF20:** 14/11/2026, Chrome 157.0.8103.51 / Windows 11, no domínio `sifit.centrion.com.br`. Cada cenário registra página, horário e limites. A inclusão é documental, sem nova execução ou reteste.

## 📋 Resumo dos defeitos

| ID | Funcionalidade afetada | Severidade / prioridade | Status | Caso relacionado |
| --- | --- | --- | --- | --- |
| [BUG-001](#bug-001--link-esqueci-minha-senha-não-executa-nenhuma-ação) | Recuperação de senha | Alta / Alta | Aberto | [CT-RF01](Cenario_Teste/CT-RF01_Esqueci-senha.md) |
| [BUG-002](#bug-002--perfil-com-dados-fictícios-campos-ausentes-e-layout-desconfigurado) | Perfil do usuário | Alta / Alta, propostas | Aberto | [CT-RF02_ERRO](Cenario_Teste/CT-RF02_ERRO.md) |
| [BUG-003](#bug-003--filtros-combinados-da-página-clientes-não-restringem-a-listagem) | Filtros de Clientes | Alta / Alta, propostas | Aberto | [CT-RF03](Cenario_Teste/CT-RF03_FILTRO_TelaClientes.md) |
| [BUG-004](#bug-004) | Exportar não oferece retorno visível no financeiro | Média / Média, propostas | Aberto | [CT-RF07](Cenario_Teste/CT-RF07_Exportacao_Financeiro.md) |
| [BUG-005](#bug-005) | Contadores financeiros divergem das mensalidades acessíveis | Alta / Alta, propostas | Aberto | [CT-RF09](Cenario_Teste/CT-RF09_Contagem_Mensalidades.md) e [CT-RF10](Cenario_Teste/CT-RF10_Filtro_Mensalidades.md) |
| [BUG-006](#bug-006) | Seletor de período permite intervalo com datas invertidas | Média / Média, propostas | Aberto | [CT-RF12](Cenario_Teste/CT-RF12_Periodo_Dashboard.md) |
| [BUG-007](#bug-007) | Tema escuro reduz a legibilidade das tabelas de Box – Turmas | Média / Média, propostas | Aberto | [CT-RF14](Cenario_Teste/CT-RF14_Contraste_TemaEscuro.md) |
| [BUG-008](#bug-008) | Edição de modalidade não apresenta ação clara para salvar | Média / Média, propostas | Aberto | [CT-RF15](Cenario_Teste/CT-RF15_Edicao_Modalidade.md) |
| [BUG-009](#bug-009) | Exclusão de categoria retorna HTTP 500 e mensagem genérica | Média / Alta, propostas | Aberto | [CT-RF19](Cenario_Teste/CT-RF19_Exclusao_Categoria.md) |
| [BUG-010](#bug-010) | Cadastro de avaliação retorna HTTP 500 | Alta / Alta, propostas | Aberto | [CT-RF21](Cenario_Teste/CT-RF21_Cadastro_Avaliacao.md) |
| [BUG-011](#bug-011) | Campo Código do exercício não aceita digitação conforme o relato | Média / Média, propostas | Em triagem — confirmação pendente | [CT-RF22](Cenario_Teste/CT-RF22_Digitacao_Codigo_Exercicio.md) |
| [BUG-012](#bug-012) | Edição de exercício aumenta o total e mantém duas entradas | Média / Média, propostas | Em triagem — confirmação pendente | [CT-RF24](Cenario_Teste/CT-RF24_Edicao_Exercicio.md) |
| [BUG-013](#bug-013) | Campos obrigatórios vazios sem feedback de validação | Média / Alta, propostas | Em triagem — persistência não confirmada | [CT-RF26](Cenario_Teste/CT-RF26_Exercicio_Campos_Vazios.md) |
| [BUG-014](#bug-014) | Vídeo rejeitado no campo Imagem sem feedback | Baixa / Média, propostas | Em triagem — MIME não confirmado | [CT-RF27](Cenario_Teste/CT-RF27_Video_Campo_Imagem.md) |
| [BUG-015](#bug-015) | Imagem rejeitada no campo Vídeo sem feedback | Baixa / Média, propostas | Em triagem — MIME não confirmado | [CT-RF28](Cenario_Teste/CT-RF28_Imagem_Campo_Video.md) |
| [BUG-016](#bug-016) | Exclusão de grupo muscular retorna HTTP 500 e mensagem genérica | Média / Alta, propostas | Em triagem — causa não determinada | [CT-RF29](Cenario_Teste/CT-RF29_Exclusao_GrupoMuscular.md) |
| [BUG-017](#bug-017) | Imagens dos grupos musculares não são exibidas e retornam HTTP 422 | Média / Média, propostas | Em triagem — causa não determinada | [CT-RF30](Cenario_Teste/CT-RF30_Imagens_GruposMusculares.md) |
| [BUG-018](#bug-018) | Dashboard apresenta múltiplos HTTP 500 durante o carregamento | Alta / Alta, propostas | Em triagem — causa não determinada | [CT-RF34](Cenario_Teste/CT-RF34_Erro_Servidor_Excesso_Requisicoes.md) |
| [BUG-019](#bug-019) | Cadastro de objetivo de treino retorna HTTP 500 | Alta / Alta, propostas | Em triagem — causa não determinada | [CT-RF35](Cenario_Teste/CT-RF35_Cadastro_Objetivo_Treino.md) |
| [BUG-020](#bug-020) | Cadastro de turma sem modalidade não apresenta retorno visível | Média / Alta, propostas | Em triagem — validação nativa não confirmada | [CT-RF41](Cenario_Teste/CT-RF41_Cadastro_Turma_Sem_Modalidade.md) |
| [BUG-021](#bug-021) | Painel Pagar.me mantém Recebimentos e gráfico ao trocar o período | Média / Média, propostas | Em triagem — dados reais ou de demonstração não confirmados | [CT-RF45](Cenario_Teste/CT-RF45_Painel_PagarMe_Periodo.md) |
| [BUG-022](#bug-022) | Relatório de Contas a Receber exibe "----" em Valor a Receber | Alta / Alta, propostas | Em triagem — origem do valor e comparação com o módulo não confirmadas | [CT-RF51](Cenario_Teste/CT-RF51_Relatorio_Contas_Receber.md) |
| [BUG-023](#bug-023) | Relatórios de Avaliações, Clientes, Colaboradores e Caixas geram arquivo PDF vazio (0 bytes) | Alta / Alta, propostas | Em triagem — correspondência dos arquivos inferida; causa não determinada | [CT-RF53](Cenario_Teste/CT-RF53_Relatorio_Avaliacoes_Vazio.md), [CT-RF54](Cenario_Teste/CT-RF54_Relatorio_Clientes_Vazio.md), [CT-RF55](Cenario_Teste/CT-RF55_Relatorio_Colaboradores_Vazio.md) e [CT-RF56](Cenario_Teste/CT-RF56_Relatorio_Caixas_Vazio.md) |
| [BUG-024](#bug-024) | Exclusão de grupo retorna HTTP 500 e mensagem genérica | Média / Alta, propostas | Em triagem — causa não determinada | [CT-RF57](Cenario_Teste/CT-RF57_Exclusao_Grupo.md) |
| [BUG-025](#bug-025) | Edição de grupo não persiste o campo status apesar de retorno de sucesso | Média / Alta, propostas | Em triagem — causa não determinada | [CT-RF58](Cenario_Teste/CT-RF58_Edicao_Grupo.md) |
| [BUG-026](#bug-026) | Data de nascimento futura aceita na edição | Alta / Alta, propostas | Em triagem | [CT-RF65](Cenario_Teste/CT-RF65_Data_Nascimento_Futura_Colaborador.md) |
| [BUG-027](#bug-027) | Data de nascimento obrigatória vazia aceita | Alta / Alta, propostas | Em triagem | [CT-RF66](Cenario_Teste/CT-RF66_Data_Nascimento_Obrigatoria_Colaborador.md) |
| [BUG-028](#bug-028) | CREF aceita texto fora do formato esperado | Média / Média, propostas | Em triagem — formato a confirmar | [CT-RF67](Cenario_Teste/CT-RF67_CREF_Formato_Colaborador.md) |
| [BUG-029](#bug-029) | Edição aceita campo obrigatório vazio | Alta / Alta, propostas | Em triagem | [CT-RF68](Cenario_Teste/CT-RF68_Edicao_Colaborador_Campo_Obrigatorio_Vazio.md) |
| [BUG-030](#bug-030) | Mesma função pode ser associada repetidamente | Média / Alta, propostas | Em triagem | [CT-RF69](Cenario_Teste/CT-RF69_Funcao_Duplicada_Colaborador.md) |
| [BUG-031](#bug-031) | Exclusão de colaborador retorna HTTP 500 | Alta / Alta, propostas | Em triagem — causa não determinada | [CT-RF70](Cenario_Teste/CT-RF70_Exclusao_Colaborador_Erro_500.md) |
| [BUG-032](#bug-032) | Cadastro de anamnese retorna HTTP 500 ao salvar ou aplicar | Média / Alta, propostas | Em triagem — causa não determinada | [CT-RF59](Cenario_Teste/CT-RF59_Cadastro_Anamnese.md) |
| [BUG-033](#bug-033) | Busca por nome perde o filtro ao avançar a página | Média / Alta, propostas | Em triagem — causa não determinada | [CT-RF71](Cenario_Teste/CT-RF71_Busca_Nome_Colaborador_Paginacao.md) |
| [BUG-034](#bug-034) | Busca por código inexistente renderiza linha vazia | Média / Alta, propostas | Em triagem — causa não determinada | [CT-RF73](Cenario_Teste/CT-RF73_Busca_Codigo_Inexistente_Colaborador.md) |
| [BUG-035](#bug-035) | Bandeira criada com parcela não aparece na listagem | Média / Alta, propostas | Em triagem — causa não determinada | [CT-RF81](Cenario_Teste/CT-RF81_Cadastro_Bandeira_Parcela_Listagem.md) |
| [BUG-036](#bug-036) | Tema escuro aplicado de forma incompleta em Bandeiras | Média / Média, propostas | Em triagem — causa não determinada | [CT-RF82](Cenario_Teste/CT-RF82_Tema_Escuro_Bandeiras.md) |
| [BUG-037](#bug-037) | Cadastro de lead aceito apenas com nome, com obrigatoriedade a confirmar | Média / Alta, propostas | Em triagem — obrigatoriedade a confirmar | [CT-RF83](Cenario_Teste/CT-RF83_Cadastro_Lead_Apenas_Nome.md) |
| [BUG-038](#bug-038) | Telefone do lead aceita 30 dígitos sem máscara nem validação | Média / Média, propostas | Em triagem — regra do campo e validação no servidor não confirmadas | [CT-RF89](Cenario_Teste/CT-RF89_Telefone_Lead_Sem_Validacao.md) |
| [BUG-039](#bug-039) | Conta a pagar a colaborador é cadastrada sem colaborador informado | Alta / Alta, propostas | Em triagem — regra de obrigatoriedade e validação no servidor não confirmadas | [CT-RF92](Cenario_Teste/CT-RF92_Cadastro_Conta_Colaborador_Sem_Colaborador.md) |
| [BUG-040](#bug-040) | Listagem de modelos de contrato aparece vazia com 15 modelos retornados | Alta / Alta, propostas | Em triagem — causa de renderização não confirmada | [CT-RF98](Cenario_Teste/CT-RF98_Listagem_Modelos_Contrato_Vazia.md) |
| [BUG-041](#bug-041) | Cartão Ativos de Planos aumenta ao cadastrar e editar planos inativos | Média / Média, propostas | Em triagem — regra de cálculo do cartão não confirmada | [CT-RF102](Cenario_Teste/CT-RF102_Contador_Ativos_Planos.md) |
| [BUG-042](#bug-042) | Status do tipo de pagamento não é enviado nem refletido: todos aparecem Inativo | Média / Média, propostas | Em triagem — regra do status do tipo de pagamento não confirmada | [CT-RF105](Cenario_Teste/CT-RF105_Cadastro_Tipo_Pagamento_Status.md) |
| [BUG-043](#bug-043) | Exclusão de tipo de pagamento em uso retorna HTTP 404 com erro SQL e mensagem genérica | Média / Média, propostas | Em triagem — regra de exclusão e tratamento do erro não confirmados | [CT-RF107](Cenario_Teste/CT-RF107_Exclusao_Tipo_Pagamento_Em_Uso.md) |
| [BUG-044](#bug-044) | Edição do tipo de resposta de pergunta de anamnese retorna HTTP 500 | Alta / Alta, propostas | Em triagem — causa não determinada | [CT-RF62](Cenario_Teste/CT-RF62_Edicao_Pergunta_Anamnese.md) |
| [BUG-045](#bug-045) | Cadastro de modelo de ficha com nome e personal retorna HTTP 500 | Alta / Alta, propostas | Em triagem. Causa a confirmar. | [CT-RF121](Cenario_Teste/CT-RF121_Cadastro_Modelo_Ficha_Erro_500.md) |
| [BUG-046](#bug-046) | Configurações de Biometria exibem senha sem mascaramento | Alta / Alta, propostas | Em triagem. Reteste após correção. | [CT-RF124](Cenario_Teste/CT-RF124_Configuracoes_Abas_Biometria_Senha.md) |
| [BUG-047](#bug-047) | Configurações aceitam e persistem dias de ausência negativos | Média / Média, propostas | Em triagem. Reteste após correção. | [CT-RF126](Cenario_Teste/CT-RF126_Configuracoes_Dias_Ausencia_Negativo.md) |
| [BUG-048](#bug-048) | Configuração de Aniversariantes exibe prévia de risco de evasão | Média / Média, propostas | Em triagem. Reteste após correção. | [CT-RF129](Cenario_Teste/CT-RF129_Central_Aniversariantes_Previa_Risco.md) |
| [BUG-049](#bug-049) | Contador de automações ativas mantém total anterior após ativar automação | Média / Média, propostas | Em triagem. Reteste após correção. | [CT-RF135](Cenario_Teste/CT-RF135_Central_Desativar_Risco_Evasao_Contador.md) e [CT-RF136](Cenario_Teste/CT-RF136_Central_Ativar_Aniversariantes_Contador.md) |
| [BUG-050](#bug-050) | API de conexão do WhatsApp indica sucesso quando a tentativa falha | Média / Média, propostas | Em triagem. Reteste após correção. | [CT-RF143](Cenario_Teste/CT-RF143_Integracoes_WhatsApp_Conectar_Evolution.md) |
| [BUG-051](#bug-051) | Configurações persiste código inválido na Cor Secundária | Média / Média, propostas | Em triagem. Reteste após correção. | [CT-RF148](Cenario_Teste/CT-RF148_Configuracoes_Design_Validar_Cor_Secundaria.md) |
| [BUG-052](#bug-052) | Design omite o limite de 6 MB ao rejeitar o salvamento do logo | Baixa / Baixa, propostas | Em triagem. Reteste após correção. | [CT-RF149](Cenario_Teste/CT-RF149_Configuracoes_Design_Logo_Limite_Tamanho.md) |

BUG-001–BUG-010 aguardam correção e reteste. BUG-011–BUG-052 aguardam confirmação das premissas e triagem antes do encaminhamento de correção. As causas técnicas permanecem não confirmadas; o BUG-003 se apoia no relato e nas capturas fornecidos, com os limites registrados no caso.

---

## BUG-001 — Link "Esqueci minha senha" não executa nenhuma ação

| Campo | Descrição |
| --- | --- |
| **Status** | Aberto — reteste pendente após a correção. |
| **Módulo** | Autenticação / Recuperação de senha. |
| **Severidade** | Alta — impede o início da recuperação autônoma de acesso. |
| **Prioridade** | Alta. |
| **Requisito** | [RF01 — Iniciar recuperação de senha](Analise%20de%20requisitos.md#rf01--iniciar-recuperação-de-senha). |
| **Caso de teste** | [CT-RF01](Cenario_Teste/CT-RF01_Esqueci-senha.md). |

**Pré-condições:** Acessar a tela de login sem estar autenticado, com a opção "Esqueci minha senha" visível. Não é necessário informar credenciais para iniciar esse fluxo.

| **Passo a passo para reprodução** |
| --- |
| 1. Acessar https://sifitalfa.centrion.com.br/login. |
| 2. Abrir Network (Rede) e Console nas ferramentas de desenvolvedor, habilitar a captura de todas as requisições e limpar os registros. |
| 3. Clicar no link "Esqueci minha senha". |
| 4. Observar se o fluxo de recuperação abre e se há requisição ou erro correspondente ao clique. |

| **Comportamento esperado** | **Comportamento obtido** |
| --- | --- |
| Exibição de formulário ou página para iniciar a solicitação de redefinição de senha, com os campos e as orientações necessários para prosseguir. Requisições ao servidor devem ocorrer nas etapas que dependam dele; uma abertura local de formulário pode ocorrer sem requisição. | O clique não produz abertura de formulário nem navegação para o fluxo de recuperação. O Jam registra cliques repetidos entre aproximadamente 00:02 e 00:12 e a interface permanece na tela de login. A consulta aos registros de rede da gravação retorna **0 requisições**; a consulta aos erros de console retorna **0 mensagens**. |

**Impacto:** O usuário não consegue iniciar a recuperação de senha pela opção disponibilizada na tela de login.

**Análise técnica:** A causa ainda não foi confirmada no código. As evidências mostram a falha de abertura do fluxo e a ausência de requisições registradas. A ausência de requisição isoladamente não caracteriza defeito quando o formulário é aberto localmente; neste caso, o fluxo não abre.

**Encaminhamento:** Inspecionar o tratamento do clique e o destino do fluxo, corrigir a abertura e executar o reteste CT-RF01 conforme o [plano de testes](Plano%20de%20testes.md). Não houve alteração nem validação do código da aplicação nesta revisão documental.

**Evidências:**

- [Vídeo no Google Drive — CT-RF01_Esqueci-senha](https://drive.google.com/file/d/1f6AqYunchDH4R9Yw1JpbyX9x28UQGcbo/view?usp=sharing) — evidência complementar fornecida; metadados consultados, conteúdo não inspecionado nesta revisão.
- [Jam — Erro no esqueci a senhas](https://jam.dev/c/0273b203-b999-493d-9919-2d143bc13301) — eventos, quadros do vídeo, rede e erros de console consultados.

---

## BUG-002 — Perfil com dados fictícios, campos ausentes e layout desconfigurado

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

| **Passo a passo para reprodução** |
| --- |
| 1. Acessar o SIFIT e autenticar-se com uma conta de teste. |
| 2. Abrir o menu do usuário e selecionar **Perfil**. |
| 3. Conferir os dados e textos apresentados, incluindo o cabeçalho e o cartão de perfil. |
| 4. Verificar se as seções **Usuário**, **Documentos** e **Endereço** exibem os campos e seus valores. |
| 5. Observar o dimensionamento das imagens, o alinhamento e a presença de rolagem horizontal. |
| 6. Inspecionar o DOM e registrar as condições de navegador, resolução e zoom para comparação após a correção. |

| **Comportamento esperado** | **Comportamento obtido** |
| --- | --- |
| Exibição dos dados da conta autenticada, com campos carregados corretamente, textos em português e layout organizado conforme o padrão do sistema, sem imagens desproporcionais ou rolagem horizontal indevida. Os campos editáveis devem permitir interação conforme as permissões da conta. | A página apresenta conteúdo fictício e textos em inglês, como “Hello Jesse”, “Jessica Jones”, “Edit profile” e “About me”. A captura mostra as seções Usuário, Documentos e Endereço sem campos visíveis e uma imagem fora de proporção. O quadro do Jam consultado em 00:05 também mostra seções vazias e uma barra horizontal. Os eventos registram acessos a `/profile` em aproximadamente 00:02 e 00:12. |

**Impacto:** O usuário não consegue visualizar adequadamente seus dados nem utilizar os campos de edição ausentes. A navegação fica prejudicada pelo layout desconfigurado. A persistência de alterações não foi testada.

**Análise técnica do HTML:** O conteúdo fornecido mantém `<base-input>`, `<base-header>`, `<base-button>` e `<card>` no DOM. Os campos de cadastro aparecem como `<base-input ... modelvalue=""></base-input>`, sem controles `<input>` internos; o `<textarea>` nativo de About me é exibido com texto de demonstração. Isso sugere componentes não resolvidos ou tratados como elementos personalizados, mas não confirma a causa. Investigar registro/importação de componentes, configuração do compilador, vínculo com a conta autenticada e estilos de imagens/contêineres. Não há evidência suficiente para atribuir o defeito à API ou confirmar um erro específico no console.

**Encaminhamento:** Corrigir o carregamento e a apresentação do perfil no código da aplicação e executar o reteste do [CT-RF02_ERRO](Cenario_Teste/CT-RF02_ERRO.md), conforme o [plano](Plano%20de%20testes.md). O repositório atual contém documentação de QA; esta revisão não corrige o sistema nem fecha o defeito.

**Evidências:**

- [Captura — erro na tela](Evidencias/CT-RF02_ERRO/erro-na-tela.png) — arquivo fornecido, copiado sem alterações e inspecionado visualmente; não mostra toda a página.
- [HTML — recorte do DOM fornecido](Evidencias/CT-RF02_ERRO/recorte-dom.html) — trechos selecionados, com omissões sinalizadas; não é o HTML integral.
- [Jam — Tela de perfil do usuário com erro](https://jam.dev/c/c61241d5-bff5-4a0a-9684-991318f9b51c) — Info, Actions e quadro em 00:05 consultados. Não foi estabelecido diagnóstico de rede ou console nesta revisão.

---

## BUG-003 — Filtros combinados da página Clientes não restringem a listagem

| Campo | Descrição |
| --- | --- |
| **Status** | Aberto — correção não realizada e reteste pendente. |
| **Módulo** | Clientes / Pesquisa com filtros. |
| **Severidade** | Alta, proposta pelo impacto na confiabilidade da consulta de clientes. |
| **Prioridade** | Alta, proposta para triagem. |
| **Caso de teste** | [CT-RF03 — Filtros da página Clientes](Cenario_Teste/CT-RF03_FILTRO_TelaClientes.md). |
| **Requisito** | [RF03 — Pesquisar clientes com filtros combinados](Analise%20de%20requisitos.md#rf03--pesquisar-clientes-com-filtros-combinados). |
| **Comportamento requerido** | Retornar exclusivamente clientes que atendam simultaneamente a todos os filtros selecionados, com lógica AND. |
| **Endpoint informado** | `POST https://backendsifit.centrion.com.br/api/clientesPorNome/1`. |
| **Ambiente** | Página Clientes; URL do frontend, versão, navegador, resolução e zoom não confirmados. Empresa informada no payload: `1`. |
| **Origem do registro** | Relato técnico e duas capturas fornecidos; link do Jam referenciado, sem acesso direto ao seu conteúdo nesta revisão. |
| **Datas** | Revisão documental em 12/11/2026; data da gravação não confirmada. |

**Objetivo e pré-condições:** Verificar a interseção dos filtros de Clientes com sessão autenticada e acesso à empresa da pesquisa. No reteste, utilizar base conhecida com Status, Situação Financeira, Plano e Personal identificados por cliente, além de registros incompatíveis para conferir sua exclusão. Confirmar os IDs reais das opções e preparar Network e Console, sem registrar autenticação.

| **Passo a passo para reprodução** |
| --- |
| 1. Acessar a página **Clientes** e manter Código e Nome vazios. |
| 2. Selecionar Status **Ativo**, Situação **Inadimplente**, Plano **Plano Hendreu** e Personal **Marcelo Longo Zandonadi**. |
| 3. Clicar em **Buscar** e conferir todos os registros com os critérios selecionados e os cadastros de referência. |
| 4. Inspecionar a requisição e a aplicação dos filtros na atualização da tabela. |
| 5. Alterar somente a Situação para **Adimplente**, clicar em **Buscar** e conferir novamente os resultados. |

| **Comportamento esperado** | **Comportamento obtido** |
| --- | --- |
| Apenas clientes que atendam a todos os critérios simultaneamente. Ao alterar a situação financeira, a nova busca deve refletir essa seleção e manter os demais filtros. Quando não houver correspondências, apresentar **"Nenhum cliente encontrado"**, sem linhas residuais. | Segundo o relato, a listagem manteve clientes de outros planos e incompatíveis com os critérios selecionados. Ao alternar Inadimplente para Adimplente, os resultados permaneceram praticamente iguais, com os filtros ainda selecionados visualmente. As capturas mostram filtros e listagens semelhantes, mas não permitem confirmar os valores completos de todas as opções nem os vínculos individuais dos clientes. |

**Impacto:** A consulta não oferece resultados confiáveis para identificar clientes por plano, personal, status e situação financeira. O usuário pode tomar decisões com base em registros incompatíveis com a pesquisa.

**Análise técnica das requisições:** O solicitante informa três chamadas ao endpoint acima, em aproximadamente **00:05, 00:20 e 00:28**, todas HTTP 200 e com respostas de aproximadamente **180,9 KB**. O corpo simplificado informado contém apenas `empresa_id` e `nome`; o token foi omitido:

```json
{
  "empresa_id": 1,
  "nome": ""
}
```

Status, Situação Financeira, Plano e Personal não aparecem nesse corpo. HTTP 200 não demonstra que os filtros foram aplicados, e volumes semelhantes não comprovam respostas idênticas. A captura 1 mostra uma entrada XHR HTTP 200, 26,9 kB transferidos e 185 kB de recursos; não exibe payload nem URL completa. A captura 2 não tem requisições listadas naquele instante, o que não comprova ausência de chamadas em toda a execução. A [cronologia e os limites das evidências](Evidencias/CT-RF03_Filtros_Clientes/README.md) distinguem os dados informados dos elementos visíveis.

**Possível causa:** Falha na integração entre os campos e a função de busca, que pode estar encaminhando somente Nome, ou ausência de aplicação correta da filtragem local. **Hipótese não confirmada:** o código da aplicação e o contrato da API não foram analisados. É necessário verificar se os filtros devem ser processados no servidor, no frontend ou em ambos.

**Correção recomendada:** Revisar o evento de Buscar e a captura dos seis campos, confirmar os valores e IDs e verificar o suporte do endpoint aos filtros. Se a filtragem ocorrer no servidor, enviar os parâmetros conforme o contrato e ajustar a API se necessário. Se for local, garantir dados e atributos suficientes, sem limitar a busca a uma página recebida. Aplicar as condições com lógica AND e atualizar a tabela, incluindo o estado sem resultados. Os IDs exemplificativos `plano_id: 60` e `personal_id: 36` não têm correspondência confirmada e não devem ser adotados sem validação.

**Critérios de aceitação e reteste:**

- Todos os registros apresentados devem satisfazer todos os filtros selecionados, e todos os clientes esperados na base conhecida devem ser encontrados, considerando eventual paginação.
- Validar Ativo + plano específico; Inativo + Plano Hendreu; Ativo + Inadimplente; Adimplente + personal específico; todos os filtros combinados; alternância da situação financeira; e combinação sem correspondências.
- Verificar Código e Nome em conjunto com os demais filtros e a remoção de restrições ao limpar campos.
- Em pesquisa vazia, apresentar **"Nenhum cliente encontrado"**, sem resultados anteriores.
- Conferir a integração conforme a arquitetura efetiva e registrar evidências sem tokens. A [matriz detalhada do CT-RF03](Cenario_Teste/CT-RF03_FILTRO_TelaClientes.md#matriz-de-reteste-proposta) está pendente de execução.

**Evidências:**

- [Jam — gravação fornecida](https://jam.dev/c/657627ec-e7e2-455d-a505-9b2a26f44bf1) — acesso direto indisponível pela ferramenta de consulta nesta revisão; horários, payload e volumes registrados conforme o relato.
- [Captura 1 — filtros e requisição HTTP 200](Evidencias/CT-RF03_Filtros_Clientes/filtros-clientes-01.png).
- [Captura 2 — filtros e listagem semelhante](Evidencias/CT-RF03_Filtros_Clientes/filtros-clientes-02.png).
- [Índice de evidências, origem e limites](Evidencias/CT-RF03_Filtros_Clientes/README.md).

**Encaminhamento:** Investigar e corrigir no repositório da aplicação; executar o CT-RF03 após disponibilização da correção. Esta entrega altera somente a documentação de QA e organiza as capturas fornecidas. Não houve alteração de código-fonte, nova execução ou confirmação de correção.


---

<a id="bug-004"></a>

## BUG-004 — Exportar não oferece retorno visível no financeiro

| Campo | Descrição |
| --- | --- |
| Status | Aberto — reteste pendente após correção. |
| Severidade / prioridade | Média / Média, propostas para triagem. |
| Módulo | Financeiro / Financeiro em Aberto |
| Requisitos | [RF07](Analise%20de%20requisitos.md#rf07) |
| Casos | [CT-RF07](Cenario_Teste/CT-RF07_Exportacao_Financeiro.md) |
| Data da evidência / revisão | 14/11/2026; sem nova execução. |
| Página | https://sifit.centrion.com.br/dashboard |
| Ambiente | Chrome 157.0.8103.51 / Windows 11 (x86); versão e zoom não confirmados. |

### Pré-condições e reprodução

**[CT-RF07](Cenario_Teste/CT-RF07_Exportacao_Financeiro.md):** Sessão autenticada com permissão para consultar e exportar o financeiro. Modal Financeiro em Aberto aberto e registros disponíveis.

1. Abrir Financeiro em Aberto a partir da página inicial.
2. Clicar uma vez em Exportar e aguardar a conclusão.
3. Verificar retorno visual e o arquivo no histórico de downloads; repetir somente para conferir comportamento.

### Esperado e obtido

| Caso | Esperado | Obtido |
| --- | --- | --- |
| CT-RF07 | Iniciar a exportação e apresentar um retorno claro ao usuário. | Vários cliques em Exportar não produzem mudança ou confirmação visível durante a gravação. |

**Impacto:** A ausência de retorno impede distinguir conclusão, falha e ausência de processamento da exportação.

### Evidências

- [CT-RF07](Cenario_Teste/CT-RF07_Exportacao_Financeiro.md): [Jam — botão de exporta sem função](https://jam.dev/c/1084cb18-cb3d-4b85-9c2f-ee431b59a06b), [vídeo original](Evidencias/CT-RF07_Exportacao_Financeiro/video.webm) e [Evidências](Evidencias/CT-RF07_Exportacao_Financeiro/README.md). 0:02–0:03: cinco cliques em Exportar. Nenhuma requisição de rede ou mensagem de console foi capturada nesse Jam.

### Análise, limites e encaminhamento

O defeito registrado é a falta de retorno visível. A geração ou ausência do arquivo ainda precisa ser conferida no histórico de downloads. A causa técnica não foi confirmada no código da aplicação. O status permanece aberto até que uma nova execução comprove os critérios de aceitação dos casos associados.

Investigar o retorno do botão; no reteste capturar o histórico de downloads e abrir o arquivo antes de concluir se a exportação foi gerada.

---

<a id="bug-005"></a>

## BUG-005 — Contadores financeiros divergem das mensalidades acessíveis

| Campo | Descrição |
| --- | --- |
| Status | Aberto — reteste pendente após correção. |
| Severidade / prioridade | Alta / Alta, propostas para triagem. |
| Módulo | Financeiro / Financeiro em Aberto |
| Requisitos | [RF09](Analise%20de%20requisitos.md#rf09) e [RF10](Analise%20de%20requisitos.md#rf10) |
| Casos | [CT-RF09](Cenario_Teste/CT-RF09_Contagem_Mensalidades.md) e [CT-RF10](Cenario_Teste/CT-RF10_Filtro_Mensalidades.md) |
| Data da evidência / revisão | 14/11/2026; sem nova execução. |
| Página | https://sifit.centrion.com.br/dashboard |
| Ambiente | Chrome 157.0.8103.51 / Windows 11 (x86); versão e zoom não confirmados. |

### Pré-condições e reprodução

**[CT-RF09](Cenario_Teste/CT-RF09_Contagem_Mensalidades.md):** Sessão autenticada com acesso ao financeiro. Base de referência com mensalidades conhecidas e distribuídas entre as faixas de vencimento.

1. Abrir Financeiro em Aberto e selecionar Todos.
2. Comparar o contador com as linhas e o total do rodapé; percorrer páginas quando disponíveis.
3. Selecionar +30 dias e repetir a conferência da quantidade e dos registros acessíveis.

**[CT-RF10](Cenario_Teste/CT-RF10_Filtro_Mensalidades.md):** Sessão autenticada e modal Financeiro em Aberto disponível. Mensalidade conhecida que pertença à faixa Até 7 dias conforme a regra do produto.

1. Selecionar Até 7 dias no modal financeiro.
2. Aguardar o carregamento e comparar contador, linhas e estado vazio.
3. Conferir que os registros esperados estão acessíveis e que a mensagem vazia só aparece para conjunto vazio.

### Esperado e obtido

| Caso | Esperado | Obtido |
| --- | --- | --- |
| CT-RF09 | Manter a contagem, a listagem e a paginação coerentes e permitir consultar todos os registros contabilizados. | Todos informa três mensalidades, mas aparece uma linha. No filtro +30 dias, o contador indica dois registros e apenas uma linha permanece disponível. |
| CT-RF10 | O contador do filtro e os registros exibidos devem representar o mesmo conjunto. | O filtro mantém o contador 1, enquanto a lista informa “Nenhuma mensalidade encontrada para o filtro atual”. |

**Impacto:** Mensalidades contabilizadas não podem ser conferidas pela lista correspondente, prejudicando a consulta financeira.

### Evidências

- [CT-RF09](Cenario_Teste/CT-RF09_Contagem_Mensalidades.md): [Jam — Informa que tem 3 mensalidades e tem apenas 1.](https://jam.dev/c/1874d0b3-5c7c-4f28-85be-91750e20cbe1), [vídeo original](Evidencias/CT-RF09_Contagem_Mensalidades/video.webm) e [Evidências](Evidencias/CT-RF09_Contagem_Mensalidades/README.md). 0:01–0:05: Todos 3 com uma linha e rodapé 1–1 de 3. 0:10–0:19: +30 dias 2 com uma linha.
- [CT-RF10](Cenario_Teste/CT-RF10_Filtro_Mensalidades.md): [Jam — Erro no filtro de mensalidade](https://jam.dev/c/3f78cf16-2c3b-48bc-8622-23b829debbec), [vídeo original](Evidencias/CT-RF10_Filtro_Mensalidades/video.webm) e [Evidências](Evidencias/CT-RF10_Filtro_Mensalidades/README.md). 0:00: clique em Até 7 dias 1 e POST /api/contas-receber/vencidas/1 com HTTP 200. 0:02–0:09: estado vazio.

### Análise, limites e encaminhamento

As gravações de Todos/+30 dias e Até 7 dias foram agrupadas em um único defeito. Não há diagnóstico da causa no banco ou nos corpos das respostas. A causa técnica não foi confirmada no código da aplicação. O status permanece aberto até que uma nova execução comprove os critérios de aceitação dos casos associados.

Retestar com o CT-RF10; os dois cenários documentam manifestações do BUG-005, sem criar um defeito duplicado. Retestar em conjunto com CT-RF09 e conferir o contrato da faixa Até 7 dias antes de preparar a base.

---

<a id="bug-006"></a>

## BUG-006 — Seletor de período permite intervalo com datas invertidas

| Campo | Descrição |
| --- | --- |
| Status | Aberto — reteste pendente após correção. |
| Severidade / prioridade | Média / Média, propostas para triagem. |
| Módulo | Página inicial / Período |
| Requisitos | [RF12](Analise%20de%20requisitos.md#rf12) |
| Casos | [CT-RF12](Cenario_Teste/CT-RF12_Periodo_Dashboard.md) |
| Data da evidência / revisão | 14/11/2026; sem nova execução. |
| Página | https://sifit.centrion.com.br/dashboard |
| Ambiente | Chrome 157.0.8103.51 / Windows 11 (x86); versão e zoom não confirmados. |

### Pré-condições e reprodução

**[CT-RF12](Cenario_Teste/CT-RF12_Periodo_Dashboard.md):** Sessão autenticada com acesso ao seletor de período da página inicial. Registrar as regras de aplicação do filtro e preparar um intervalo válido de controle.

1. Alterar a data final para 10/11/2026 na base de referência da gravação.
2. Alterar a inicial para 19/11/2026, posterior à data final.
3. Verificar a validação e tentar aplicar; depois selecionar um período válido e conferir os dados de referência.

### Esperado e obtido

| Caso | Esperado | Obtido |
| --- | --- | --- |
| CT-RF12 | Validar a ordem das datas, orientar o usuário e aplicar um período válido com retorno perceptível. | O seletor chega a exibir 19/11/2026–10/11/2026, com início posterior ao fim, sem uma validação visível. Os indicadores permanecem com os mesmos valores nos quadros conferidos. |

**Impacto:** O usuário pode deixar o filtro com um período inválido, sem orientação visível.

### Evidências

- [CT-RF12](Cenario_Teste/CT-RF12_Periodo_Dashboard.md): [Jam — Botões de datas sem função e sem atualização](https://jam.dev/c/93165ba3-3bfe-4dd5-9379-ab8db2d686ba), [vídeo original](Evidencias/CT-RF12_Periodo_Dashboard/video.webm) e [Evidências](Evidencias/CT-RF12_Periodo_Dashboard/README.md). 0:04–0:08: seleção das datas. 0:10: intervalo invertido visível. No começo foram capturadas várias chamadas POST /api/dados-principais-home/1 com HTTP 200.

### Análise, limites e encaminhamento

A reprodução documentada é a falta de validação de início posterior ao fim; indicadores constantes não comprovam falha de cálculo nem ausência de requisições. A causa técnica não foi confirmada no código da aplicação. O status permanece aberto até que uma nova execução comprove os critérios de aceitação dos casos associados.

Corrigir e retestar a validação do intervalo; avaliar a atualização dos indicadores em base controlada como verificação complementar.

---

<a id="bug-007"></a>

## BUG-007 — Tema escuro reduz a legibilidade das tabelas de Box – Turmas

| Campo | Descrição |
| --- | --- |
| Status | Aberto — reteste pendente após correção. |
| Severidade / prioridade | Média / Média, propostas para triagem. |
| Módulo | SifitBox / Turmas / Tema |
| Requisitos | [RF14](Analise%20de%20requisitos.md#rf14) |
| Casos | [CT-RF14](Cenario_Teste/CT-RF14_Contraste_TemaEscuro.md) |
| Data da evidência / revisão | 14/11/2026; sem nova execução. |
| Página | https://sifit.centrion.com.br/sifitbox/turmas |
| Ambiente | Chrome 157.0.8103.51 / Windows 11 (x86); versão e zoom não confirmados. |

### Pré-condições e reprodução

**[CT-RF14](Cenario_Teste/CT-RF14_Contraste_TemaEscuro.md):** Sessão autenticada com acesso a SifitBox – Turmas. Página com modalidades e turmas recorrentes cadastradas.

1. Registrar a apresentação das tabelas no tema Claro.
2. Selecionar Escuro.
3. Conferir títulos, nomes, status e ações sobre os fundos das duas tabelas.

### Esperado e obtido

| Caso | Esperado | Obtido |
| --- | --- | --- |
| CT-RF14 | Aplicar cores de texto e de fundo que preservem a legibilidade em ambos os temas. | As áreas de Modalidades e Turmas recorrentes permanecem brancas enquanto diversos textos ficam muito claros, dificultando sua leitura. |

**Impacto:** Dificulta ler modalidades, turmas e seus atributos no tema escuro.

### Evidências

- [CT-RF14](Cenario_Teste/CT-RF14_Contraste_TemaEscuro.md): [Jam — falta de acessibilidade nas cores](https://jam.dev/c/6889db07-bed1-472b-8ec2-00402919cd65), [vídeo original](Evidencias/CT-RF14_Contraste_TemaEscuro/video.webm) e [Evidências](Evidencias/CT-RF14_Contraste_TemaEscuro/README.md). 0:02: seleção de Escuro e POST /api/usuario/tema com HTTP 200. 0:02–0:09: perda de legibilidade nas tabelas.

### Análise, limites e encaminhamento

A evidência é visual; não houve medição de razão de contraste ou conclusão de conformidade com um padrão formal. A causa técnica não foi confirmada no código da aplicação. O status permanece aberto até que uma nova execução comprove os critérios de aceitação dos casos associados.

Ajustar as cores e retestar ambos os temas; medir contraste se houver critério formal de acessibilidade definido.

---

<a id="bug-008"></a>

## BUG-008 — Edição de modalidade não apresenta ação clara para salvar

| Campo | Descrição |
| --- | --- |
| Status | Aberto — reteste pendente após correção. |
| Severidade / prioridade | Média / Média, propostas para triagem. |
| Módulo | SifitBox / Modalidades |
| Requisitos | [RF15](Analise%20de%20requisitos.md#rf15) |
| Casos | [CT-RF15](Cenario_Teste/CT-RF15_Edicao_Modalidade.md) |
| Data da evidência / revisão | 14/11/2026; sem nova execução. |
| Página | https://sifit.centrion.com.br/sifitbox/turmas |
| Ambiente | Chrome 157.0.8103.51 / Windows 11 (x86); versão e zoom não confirmados. |

### Pré-condições e reprodução

**[CT-RF15](Cenario_Teste/CT-RF15_Edicao_Modalidade.md):** Sessão autenticada com permissão para editar modalidades. Modalidade de teste com nome, descrição e status conhecidos.

1. Clicar no lápis de uma modalidade.
2. Verificar o preenchimento dos campos e alterar um valor de teste.
3. Localizar e usar a ação de salvar; conferir confirmação e recarregar a lista para validar persistência.

### Esperado e obtido

| Caso | Esperado | Obtido |
| --- | --- | --- |
| CT-RF15 | Oferecer ações visíveis de salvar e cancelar e confirmar a atualização. | Há ícones de lápis na lista. Ao clicar, os campos superiores são preenchidos para edição, mas não aparece uma ação clara para salvar ou concluir a alteração nos quadros analisados. |

**Impacto:** O usuário altera os campos sem encontrar uma ação clara para concluir ou cancelar a edição.

### Evidências

- [CT-RF15](Cenario_Teste/CT-RF15_Edicao_Modalidade.md): [Jam — Sem botão para editar modalidades](https://jam.dev/c/951efaf8-bf32-44b0-b640-a2935a6b554a), [vídeo original](Evidencias/CT-RF15_Edicao_Modalidade/video.webm) e [Evidências](Evidencias/CT-RF15_Edicao_Modalidade/README.md). 0:03–0:13: cliques no lápis, campos preenchidos e alternância entre Ativo e Inativo. Nenhuma chamada de atualização foi capturada.

### Análise, limites e encaminhamento

Há ícone de lápis e carregamento dos campos. A evidência não demonstra a ausência de todo mecanismo de salvamento; a persistência precisa ser retestada. A causa técnica não foi confirmada no código da aplicação. O status permanece aberto até que uma nova execução comprove os critérios de aceitação dos casos associados.

Verificar o fluxo de conclusão da edição e retestar persistência. A evidência reprova a clareza da ação de salvar; não afirma que o ícone de editar inexiste.

---

<a id="bug-009"></a>

## BUG-009 — Exclusão de categoria retorna HTTP 500 e mensagem genérica

| Campo | Descrição |
| --- | --- |
| Status | Aberto — reteste pendente após correção. |
| Severidade / prioridade | Média / Alta, propostas para triagem. |
| Módulo | Categorias Crossfit / Exclusão |
| Requisitos | [RF19](Analise%20de%20requisitos.md#rf19) |
| Casos | [CT-RF19](Cenario_Teste/CT-RF19_Exclusao_Categoria.md) |
| Data da evidência / revisão | 14/11/2026; sem nova execução. |
| Página | https://sifit.centrion.com.br/categorias-exercicios-crossfit |
| Ambiente | Chrome 157.0.8103.51 / Windows 11 (x86); versão e zoom não confirmados. |

### Pré-condições e reprodução

**[CT-RF19](Cenario_Teste/CT-RF19_Exclusao_Categoria.md):** Sessão autenticada com permissão para excluir categorias. Categoria descartável e vínculos conhecidos; confirmar os impedimentos de exclusão previstos.

1. Acionar a lixeira da categoria de teste.
2. Confirmar a exclusão no diálogo.
3. Conferir retorno visual, status da chamada e presença do registro após a operação.

### Esperado e obtido

| Caso | Esperado | Obtido |
| --- | --- | --- |
| CT-RF19 | Concluir a exclusão permitida ou explicar de forma tratável por que o registro não pode ser excluído. | Após a confirmação, aparece o diálogo “Erro” / “Erro ao deletar categoria”. A categoria permanece na lista. |

**Impacto:** A exclusão não é concluída e o usuário recebe uma mensagem sem motivo tratável.

### Evidências

- [CT-RF19](Cenario_Teste/CT-RF19_Exclusao_Categoria.md): [Jam — Erro a o deletar categoria](https://jam.dev/c/c5c78b3b-2865-4226-836f-bcb0a8fc612f), [vídeo original](Evidencias/CT-RF19_Exclusao_Categoria/video.webm) e [Evidências](Evidencias/CT-RF19_Exclusao_Categoria/README.md). 0:02: POST /api/categoria-exercicio-cross/excluir retorna HTTP 500. 0:03–0:05: mensagem de erro.

### Análise, limites e encaminhamento

HTTP 500 está registrado no Jam. A causa, os vínculos e a regra para impedir a exclusão ainda precisam ser investigados. A causa técnica não foi confirmada no código da aplicação. O status permanece aberto até que uma nova execução comprove os critérios de aceitação dos casos associados.

Investigar o HTTP 500 com logs do servidor e vínculos da categoria; corrigir e retestar cenários permitido e impedido.

---

<a id="bug-010"></a>

## BUG-010 — Cadastro de avaliação retorna HTTP 500

| Campo | Descrição |
| --- | --- |
| Status | Aberto — reteste pendente após correção pela equipe da aplicação. |
| Severidade / prioridade | Alta / Alta, propostas para triagem; bloqueia a confirmação do cadastro no cenário registrado. |
| Módulo | Avaliações / Cadastrar Avaliação |
| Requisito / caso | [RF21](Analise%20de%20requisitos.md#rf21) / [CT-RF21](Cenario_Teste/CT-RF21_Cadastro_Avaliacao.md) |
| Data da evidência / revisão | 15/11/2026; sem nova execução. |
| Página | https://sifit.centrion.com.br/avaliacoes |
| Ambiente | Chrome 157.0.8103.51 / Windows 11 (x86), captura 1536 × 742. Versão, zoom e classificação do ambiente não identificados. |
| Frequência conhecida | Uma tentativa de salvamento no Jam; recorrência não determinada. |

### Pré-condições e reprodução

Sessão autenticada com acesso ao cadastro e personal Gabriella disponível. A existência e a elegibilidade do aluno 3423 não foram confirmadas.

1. Abrir Avaliações e clicar em Cadastrar Avaliação.
2. Digitar Nome leonardp e Código 3423, sem acionar a busca.
3. Selecionar Gabriella (personal 7); o funcionário cadastrante exibido é Jair (11).
4. Manter a data 15/11/2026 e informar 06:00.
5. Clicar em Salvar e observar o alerta e a requisição de rede.

### Esperado e obtido

| Esperado | Obtido |
| --- | --- |
| Cadastrar e confirmar dados válidos; informar validação específica para dados recusados, sem erro interno genérico. | POST /api/avaliacao/adicionar-agendamento/1 retorna HTTP 500 e “Erro interno inesperado.”. A interface exibe “Erro ao cadastrar Avaliação.” e mantém o formulário aberto. |

**Impacto:** o cadastro fica sem confirmação e a mensagem não orienta a correção dos dados. A persistência não foi conferida; verificar antes de reenviar.

### Evidências técnicas

- [Jam](https://jam.dev/c/2e5eca1f-7cd2-4ee3-854b-02ef4635955a), evento 16 em aproximadamente 00:12: POST HTTP 500 em 1363 ms; OPTIONS anterior HTTP 204.
- Payload de negócio: cliente_id "3423", func_cadastrante_id 11, data_avaliacao "15/11/2026", hora_avaliacao "06:00", personal_id 7. Autenticação omitida.
- Resposta: verifica_erro true, mensagem “Erro interno inesperado.”; cabeçalho de data 15/11/2026 18:08:04 UTC.
- Request ID: 04ce089a65dc48f03fd72b4a6d64961d-asc-edge11.
- [Formulário em 00:12,479](Evidencias/CT-RF21_Cadastro_Avaliacao/formulario_00-12-479.jpg), [alerta em 00:14,748](Evidencias/CT-RF21_Cadastro_Avaliacao/erro_00-14-748.jpg), [requisição/resposta](Evidencias/CT-RF21_Cadastro_Avaliacao/requisicao_resposta.json) e [Evidências](Evidencias/CT-RF21_Cadastro_Avaliacao/README.md).
- Zero mensagens de console capturadas segundo o resumo de eventos do Jam.

### Análise, limites e encaminhamento

A falha HTTP 500 está confirmada; a causa raiz depende do código e dos logs do servidor. Correlacionar o endpoint com 18:08:03–18:08:04 UTC de 15/11/2026 e o request ID. Verificar o aluno 3423 no contexto da rota /1, os vínculos do personal 7 e do funcionário 11, a interpretação de DD/MM/AAAA e o tratamento de horário retroativo. O nome digitado não integra o payload. O sufixo /1 tem significado não confirmado.

O horário 06:00 precede a tentativa de aproximadamente 15:08; o aluno foi digitado sem confirmação pela busca. Esses fatos orientam verificações e não comprovam a causa. Não houve inspeção do código, consulta ao banco, nova execução ou correção da aplicação.

**Reteste:** executar a [matriz do CT-RF21](Cenario_Teste/CT-RF21_Cadastro_Avaliacao.md#critérios-de-aceitação-e-matriz-de-reteste-proposta), confirmar sucesso com dados válidos, validação para dados recusados, persistência e ausência de registros parciais/duplicados. Manter aberto até nova evidência em versão identificada.

---

<a id="bug-011"></a>

## BUG-011 — Campo Código do exercício não aceita digitação conforme o relato

| Campo | Descrição |
| --- | --- |
| Status | Em triagem — confirmação funcional e reprodução pendentes; causa técnica não confirmada. |
| Severidade / prioridade | Média / Média, propostas para triagem. |
| Módulo | Exercícios / Formulário Exercício |
| Requisito / caso | [RF22](Analise%20de%20requisitos.md#rf22) / [CT-RF22](Cenario_Teste/CT-RF22_Digitacao_Codigo_Exercicio.md) |
| Data da evidência / revisão | 15/11/2026, 15:25 BRT / 15/11/2026; sem nova execução. |
| Página / ambiente | https://sifit.centrion.com.br/exercicios; Edge 157.0.8103.80 / Windows 11 (x86), janela 1912 × 960. Versão, zoom e classificação do ambiente não confirmados. |
| Frequência conhecida | Um registro do Jam; recorrência não determinada. |

### Pré-condições e reprodução

Confirmar se o código é manual ou automático e quais operações permitem edição. Sessão autenticada com permissão e dados de teste autorizados.

1. Abrir o formulário Exercício com permissão adequada.
2. Selecionar Código e digitar um valor válido.
3. Apagar e corrigir o valor, sair com Tab e verificar sua manutenção.

### Esperado e obtido

| Esperado | Obtido |
| --- | --- |
| Quando editável, o campo Código deve aceitar e manter um código válido e permitir sua correção. | O testador relata não conseguir digitar o código. A imagem inicial confirma o campo Código no formulário Exercício; a reprodução integral, as teclas e o foco não foram confirmados. |

**Impacto:** impede informar manualmente o código quando a regra permitir essa operação.

### Evidências técnicas

- [Jam](https://jam.dev/c/2696db03-0a18-4c39-a75d-4987a43c04f0) e relato do testador.
- O impedimento é relatado pelo testador. Não foram confirmados foco, teclas ou valor tentado; rede e console não analisados.

### Análise, limites e encaminhamento

Não foram confirmadas a operação de criação/edição, a sequência de teclas ou a causa. A classificação se apoia no relato e na imagem inicial, sem análise de rede ou console. Confirmar a regra, reproduzir o impedimento e retestar o campo após correção.

**Reteste:** executar os critérios do [CT-RF22](Cenario_Teste/CT-RF22_Digitacao_Codigo_Exercicio.md) em versão identificada, confirmar a premissa funcional e registrar nova evidência. Se o código for automático ou a operação original tiver sido criação, reavaliar o registro correspondente. Não encerrar por revisão documental.

---

<a id="bug-012"></a>

## BUG-012 — Edição de exercício aumenta o total e mantém duas entradas

| Campo | Descrição |
| --- | --- |
| Status | Em triagem — confirmação funcional e reprodução pendentes; causa técnica não confirmada. |
| Severidade / prioridade | Média / Média, propostas para triagem. |
| Módulo | Exercícios / Formulário Exercício |
| Requisito / caso | [RF24](Analise%20de%20requisitos.md#rf24) / [CT-RF24](Cenario_Teste/CT-RF24_Edicao_Exercicio.md) |
| Data da evidência / revisão | 15/11/2026, 15:38 BRT / 15/11/2026; sem nova execução. |
| Página / ambiente | https://sifit.centrion.com.br/exercicios; Edge 157.0.8103.80 / Windows 11 (x86), janela 1912 × 960. Versão, zoom e classificação do ambiente não confirmados. |
| Frequência conhecida | Um registro do Jam; recorrência não determinada. |

### Pré-condições e reprodução

Exercício de teste existente, com identificador e nome original registrados antes da edição. Sessão autenticada com permissão e dados de teste autorizados.

1. Registrar identificador, nome e total do exercício de teste.
2. Abrir explicitamente a ação de edição desse registro.
3. Alterar o nome para um nome de teste distinguível, como Levantamento de Peso 02.
4. Clicar em Salvar.
5. Conferir o nome atualizado, a identidade do registro e a manutenção do total.
6. Verificar se a lista criou uma segunda entrada em vez de atualizar a original.

### Esperado e obtido

| Esperado | Obtido |
| --- | --- |
| Salvar a edição deve atualizar o mesmo exercício, sem criar um registro adicional e sem aumentar o total da biblioteca. | O Jam está identificado como teste de edição. Nos quadros intermediários, o formulário Exercício está aberto com código 16, o nome é preenchido e a biblioteca ao fundo indica total 10. No quadro final, o formulário fecha, o total é 11 e a lista contém Levantamento de Peso e Levantamento de Peso 02. O aumento e a coexistência dos nomes divergem do resultado esperado para uma edição. |

**Impacto:** pode criar um exercício adicional em vez de atualizar o existente, alterando a identidade e os totais.

### Evidências técnicas

- [Jam](https://jam.dev/c/073f70d6-4052-4e0f-a4bb-e9f37305d618) e [Evidências](Evidencias/CT-RF24_Edicao_Exercicio/README.md).
- A aba Network apresenta POST com HTTP 200, GET de arquivo MP4 com HTTP 200, POST com HTTP 201 e outro POST com HTTP 200. O HTTP 201 é compatível com criação, mas isoladamente não confirma a causa: caminhos, corpos e contrato da API não foram inspecionados.

### Análise, limites e encaminhamento

O acionamento inicial da edição e os identificadores das duas entradas não foram confirmados. A classificação considera o propósito declarado do Jam e a divergência visual; se a operação tiver sido criação, reavaliar a conclusão. Reproduzir a partir da ação explícita de edição e comparar os identificadores antes e depois. Investigar eventual envio para criação como hipótese, sem atribuir causa técnica antes de verificar código e contrato da API.

**Reteste:** executar os critérios do [CT-RF24](Cenario_Teste/CT-RF24_Edicao_Exercicio.md) em versão identificada, confirmar a premissa funcional e registrar nova evidência. Se o código for automático ou a operação original tiver sido criação, reavaliar o registro correspondente. Não encerrar por revisão documental.

---

<a id="bug-013"></a>

## BUG-013 — Campos obrigatórios vazios sem feedback de validação

| Campo | Descrição |
| --- | --- |
| Status | Em triagem — bloqueio aparente; persistência e causa técnica não confirmadas. |
| Severidade / prioridade | Média / Alta, propostas para triagem. |
| Módulo | Exercícios / Validação do cadastro |
| Requisito / caso | [RF26](Analise%20de%20requisitos.md#rf26) / [CT-RF26](Cenario_Teste/CT-RF26_Exercicio_Campos_Vazios.md) |
| Data da evidência / revisão | 15/11/2026, 16:11 BRT / 15/11/2026; sem nova execução. |
| Página / ambiente | https://sifit.centrion.com.br/exercicios; Edge 157.0.8103.80 / Windows 11 (x86), janela 1912 × 960. |
| Frequência conhecida | Um registro do Jam; recorrência não determinada. |

### Pré-condições

- Sessão autenticada com permissão para cadastrar exercícios.
- Formulário de novo exercício aberto.
- Campos obrigatórios mantidos vazios.

### Passos para reproduzir

1. Acessar Exercícios e abrir o formulário de novo exercício.
2. Manter código, nome e demais campos obrigatórios vazios.
3. Clicar em Salvar.
4. Observar o formulário, as mensagens e a biblioteca.

### Resultado esperado

O envio deve ser bloqueado, cada campo obrigatório deve receber indicação compreensível e nenhum registro vazio deve ser criado.

### Resultado obtido

O formulário permanece aberto e não é observada mensagem, indicação por campo ou orientação visível. A gravação não demonstra se houve requisição ou persistência.

**Impacto:** o usuário não sabe quais dados corrigir e pode repetir a tentativa sem compreender por que o cadastro não foi concluído.

### Evidências, limites e encaminhamento

- [Jam](https://jam.dev/c/bc07ca5f-d3a9-45f6-84cb-12c0b562a211).
- Gravação aproximada de 4 segundos; resposta da API, persistência e consulta posterior à biblioteca não confirmadas.

Investigar a validação do cliente e do servidor, implementar feedback junto aos campos e manter o registro em triagem até reprodução controlada.

**Reteste:** registrar o total inicial, executar combinações de campos vazios, conferir foco e mensagens, observar a rede e confirmar após recarga que nenhum registro vazio foi criado.

---

<a id="bug-014"></a>

## BUG-014 — Vídeo rejeitado no campo Imagem sem feedback

| Campo | Descrição |
| --- | --- |
| Status | Em triagem — rejeição visual aparente; MIME, upload e causa técnica não confirmados. |
| Severidade / prioridade | Baixa / Média, propostas para triagem. |
| Módulo | Exercícios / Validação de mídia |
| Requisito / caso | [RF27](Analise%20de%20requisitos.md#rf27) / [CT-RF27](Cenario_Teste/CT-RF27_Video_Campo_Imagem.md) |
| Data da evidência / revisão | 15/11/2026, 16:08 BRT / 15/11/2026; sem nova execução. |
| Página / ambiente | https://sifit.centrion.com.br/exercicios; Edge 157.0.8103.80 / Windows 11 (x86), janela 1912 × 960. |
| Frequência conhecida | Um registro do Jam; recorrência não determinada. |

### Passos para reproduzir

1. Abrir o formulário de exercício.
2. Acionar a seleção de arquivo do campo Imagem.
3. Selecionar um arquivo de vídeo.
4. Observar o campo, as mensagens e a rede.

### Resultado esperado

O vídeo deve ser rejeitado e o campo deve informar os formatos e limites aceitos para imagens, preservando os demais dados.

### Resultado obtido

O arquivo não aparece anexado, mas não é observada mensagem explicando a rejeição ou os formatos permitidos.

**Impacto:** o usuário não recebe orientação para escolher um arquivo compatível e pode interpretar a ausência de anexo como falha do sistema.

### Evidências, limites e encaminhamento

- [Jam](https://jam.dev/c/00740108-9a7d-4151-8723-171c89635567).
- Nome, extensão, MIME, tamanho, upload e resposta da API não foram confirmados.

Exibir feedback no campo e validar tipo real e extensão tanto no cliente quanto no servidor, sem atribuir causa antes da inspeção.

**Reteste:** usar vídeos controlados com extensões e MIME conhecidos, capturar rede, confirmar ausência de upload/vínculo e verificar preservação dos demais campos.

---

<a id="bug-015"></a>

## BUG-015 — Imagem rejeitada no campo Vídeo sem feedback

| Campo | Descrição |
| --- | --- |
| Status | Em triagem — rejeição visual aparente; MIME, upload e causa técnica não confirmados. |
| Severidade / prioridade | Baixa / Média, propostas para triagem. |
| Módulo | Exercícios / Validação de mídia |
| Requisito / caso | [RF28](Analise%20de%20requisitos.md#rf28) / [CT-RF28](Cenario_Teste/CT-RF28_Imagem_Campo_Video.md) |
| Data da evidência / revisão | 15/11/2026, 16:07 BRT / 15/11/2026; sem nova execução. |
| Página / ambiente | https://sifit.centrion.com.br/exercicios; Edge 157.0.8103.80 / Windows 11 (x86), janela 1912 × 960. |
| Frequência conhecida | Um registro do Jam; recorrência não determinada. |

### Passos para reproduzir

1. Abrir o formulário de exercício.
2. Acionar a seleção de arquivo do campo Vídeo.
3. Selecionar um arquivo de imagem.
4. Observar o campo, as mensagens e a rede.

### Resultado esperado

A imagem deve ser rejeitada e o campo deve informar os formatos e limites aceitos para vídeos, preservando os demais dados.

### Resultado obtido

O arquivo não aparece anexado, mas não é observada mensagem explicando a rejeição ou os formatos permitidos.

**Impacto:** o usuário não recebe orientação para escolher um arquivo compatível e pode interpretar a ausência de anexo como falha do sistema.

### Evidências, limites e encaminhamento

- [Jam](https://jam.dev/c/be9437a4-4fe9-4756-a2af-6777d3f43e25).
- Nome, extensão, MIME, tamanho, upload e resposta da API não foram confirmados.

Exibir feedback no campo e validar tipo real e extensão tanto no cliente quanto no servidor, sem atribuir causa antes da inspeção.

**Reteste:** usar imagens controladas com extensões e MIME conhecidos, capturar rede, confirmar ausência de upload/vínculo e verificar preservação dos demais campos.

---

<a id="bug-016"></a>

## BUG-016 — Exclusão de grupo muscular retorna HTTP 500 e mensagem genérica

| Campo | Descrição |
| --- | --- |
| Status | Em triagem — causa não determinada; reteste pendente após correção. |
| Severidade / prioridade | Média / Alta, propostas para triagem. |
| Módulo | Grupos Musculares / Exclusão |
| Requisitos | [RF29](Analise%20de%20requisitos.md#rf29) |
| Casos | [CT-RF29](Cenario_Teste/CT-RF29_Exclusao_GrupoMuscular.md) |
| Data da evidência / revisão | 15/11/2026; sem nova execução. |
| Página | https://sifit.centrion.com.br/grupos-musculares |
| Ambiente | Chrome 157.0.8103.78 / Windows (x86) 11; versão e zoom não confirmados. |

### Pré-condições e reprodução

**[CT-RF29](Cenario_Teste/CT-RF29_Exclusao_GrupoMuscular.md):** Sessão autenticada com permissão para excluir grupos musculares. Registro de teste cuja exclusão seja permitida, com vínculos conhecidos para distinguir impedimento de regra de falha do servidor.

1. Acionar o ícone de exclusão na linha do grupo muscular.
2. Confirmar a exclusão no diálogo "Deseja deletar o Grupo?".
3. Conferir o retorno visual, o status da chamada e a presença do registro após a operação.

### Esperado e obtido

| Caso | Esperado | Obtido |
| --- | --- | --- |
| CT-RF29 | Concluir a exclusão permitida, removendo o registro e atualizando os contadores; ou explicar de forma tratável o impedimento, sem erro interno. | Diálogo "Erro" / "Erro ao deletar Grupo" com o botão "Fechar". O registro permanece na listagem e os contadores não se alteram. |

**Impacto:** A exclusão não é concluída e o usuário recebe uma mensagem sem motivo tratável. O comportamento repete a assinatura de [BUG-009](#bug-009) e [BUG-010](#bug-010), em módulos distintos.

### Evidências

- [CT-RF29](Cenario_Teste/CT-RF29_Exclusao_GrupoMuscular.md): [Jam — Tela de Grupos Musculares](https://jam.dev/c/98008390-0040-475e-ba7b-7f1e72cc0b2e). 1:17: acionamento do ícone de exclusão. 1:18: diálogo de confirmação. 1:19: `POST /api/deleta/grupo-muscular/1` retorna HTTP 500 em 990 ms. 1:21: diálogo de erro, com a listagem inalterada. 1:23: segunda tentativa no mesmo endpoint, também HTTP 500, em 184 ms.
- Corpo de resposta nas duas tentativas: `{"verifica_erro": true, "mensagem": "Erro interno inesperado."}`.
- Cabeçalhos registrados: `content-type: application/json; charset=utf-8`, `content-length: 64`, `x-powered-by: PHP/8.2.35`. Primeira tentativa em `Dom, 15 de nov de 2026 18:55:46 GMT`, `x-hcdn-request-id: d7f7c4b73412a500c5bdb50eb9be6ec1-asc-edge11`; segunda em `18:55:49 GMT`, `x-hcdn-request-id: c467f11f867c2cdb2c23ce6029e59251-asc-edge11`.

### Análise, limites e encaminhamento

O HTTP 500 e o endpoint estão registrados no Jam. Não houve acesso a logs do servidor, ao corpo completo da resposta além dos 64 bytes retornados nem ao banco de dados, de modo que não é possível distinguir entre falha de infraestrutura, exceção não tratada na aplicação e restrição de integridade referencial não capturada. A causa técnica não foi confirmada no código.

Não foi verificado se o registro permanece íntegro após as duas tentativas enviadas para o mesmo recurso, nem exercitado o cenário de exclusão com impedimento de regra. A mensagem "Erro ao deletar Grupo" é genérica e não informa a causa ao usuário.

Investigar o HTTP 500 com logs do servidor e os vínculos do registro; corrigir e retestar os cenários permitido e impedido. O status permanece em triagem até que a causa seja determinada e uma nova execução comprove os critérios de aceitação do caso associado.

---

<a id="bug-017"></a>

## BUG-017 — Imagens dos grupos musculares não são exibidas e retornam HTTP 422

| Campo | Descrição |
| --- | --- |
| Status | Em triagem — causa não determinada; reteste pendente após correção. |
| Severidade / prioridade | Média / Média, propostas para triagem. |
| Módulo | Grupos Musculares / Listagem |
| Requisitos | [RF30](Analise%20de%20requisitos.md#rf30) |
| Casos | [CT-RF30](Cenario_Teste/CT-RF30_Imagens_GruposMusculares.md) |
| Data da evidência / revisão | 15/11/2026; sem nova execução. |
| Página | https://sifit.centrion.com.br/grupos-musculares |
| Ambiente | Chrome 157.0.8103.78 / Windows (x86) 11; versão e zoom não confirmados. |

### Pré-condições e reprodução

**[CT-RF30](Cenario_Teste/CT-RF30_Imagens_GruposMusculares.md):** Sessão autenticada com acesso a Grupos Musculares. Ao menos um registro com imagem cadastrada e o caminho esperado dos arquivos conhecido.

1. Acessar a tela Grupos Musculares com o painel de rede aberto.
2. Observar a coluna IMAGEM de cada linha.
3. Conferir o status das requisições para `/img/grupos_musculares/imagens/`.
4. Repetir após uma busca e após a troca de tema.

### Esperado e obtido

| Caso | Esperado | Obtido |
| --- | --- | --- |
| CT-RF30 | A coluna IMAGEM apresenta a imagem de cada registro e as requisições dos arquivos são concluídas com sucesso. | Todas as linhas exibem o ícone de imagem quebrada e as requisições retornam HTTP 422, com ocorrências de `net::ERR_ABORTED`. |

**Impacto:** A listagem não apresenta a identificação visual dos grupos musculares em nenhuma linha. A falha é constante durante toda a gravação e independe do filtro aplicado ou do tema selecionado.

### Evidências

- [CT-RF30](Cenario_Teste/CT-RF30_Imagens_GruposMusculares.md): [Jam — Tela de Grupos Musculares](https://jam.dev/c/98008390-0040-475e-ba7b-7f1e72cc0b2e). Ocorrências de HTTP 422 em 0:06, 0:16, 0:53, 0:57, 1:07, 1:09, 1:12, 1:33, 1:35, 1:39, 1:47 e 1:59; três ocorrências de `net::ERR_ABORTED` em 0:53, 0:57 e 1:12.
- Arquivos requisitados: `6ad0c27c20a04.png`, `6abbd0a11ec04.png`, `655226c71114f.png` e `6afa0017749b3.jpg`, todos em `https://sifit.centrion.com.br/img/grupos_musculares/imagens/`.
- Quadros de 0:20, 0:55, 1:18, 1:21, 1:45 e 2:00, com o ícone de imagem quebrada em todas as linhas, nos temas escuro e claro.

### Análise, limites e encaminhamento

Os códigos de status foram lidos na coluna Status da lista de rede. O painel de detalhe da ferramenta repetiu cabeçalhos de resposta e `x-hcdn-request-id` entre linhas distintas durante a consulta, de modo que os cabeçalhos de resposta das requisições de imagem não foram considerados confiáveis e não são reproduzidos aqui.

O código 422 não é o retorno usual para arquivo ausente ou sem permissão, o que sugere tratamento por aplicação em vez de entrega direta de arquivo estático. Essa é uma hipótese a confirmar, não um diagnóstico. Não foi verificada a existência dos arquivos no servidor, nem o conteúdo do campo de imagem de cada registro no banco, nem o resultado do acesso direto às URLs fora da página.

Verificar também o comportamento para registros criados sem imagem: o formulário de inclusão foi enviado com "Nenhum arquivo escolhido" e, a partir de 0:53, passa a existir um quarto arquivo requisitado com o mesmo 422. Nos trechos em que a listagem é filtrada e exibe apenas esse registro, ele é o único arquivo requisitado, o que o associa a ele; a associação decorre da correlação entre filtros e requisições, sem confirmação no banco.

Investigar a existência dos arquivos no caminho indicado, o nome gravado em cada registro e a regra que responde HTTP 422 a uma requisição de imagem. O status permanece em triagem até que a causa seja determinada e uma nova execução comprove os critérios de aceitação do caso associado.

---

<a id="bug-018"></a>

## BUG-018 — Dashboard apresenta múltiplos HTTP 500 durante o carregamento

| Campo | Descrição |
| --- | --- |
| Status | Em triagem — causa não determinada; reteste pendente. |
| Severidade / prioridade | Alta / Alta, propostas para triagem. |
| Módulo | Dashboard / carregamento de dados |
| Requisito | [RF34](Analise%20de%20requisitos.md#rf34) |
| Caso | [CT-RF34](Cenario_Teste/CT-RF34_Erro_Servidor_Excesso_Requisicoes.md) |
| Evidência | [Jam](https://jam.dev/c/eea58e17-b62f-432b-97b2-b14c14bed555) |

Ao carregar o dashboard, a interface apresenta um diálogo de erro e diversas chamadas GET/POST retornam HTTP 500 entre 23 eventos visíveis. Os endpoints aparecem truncados na evidência, portanto a quantidade de requisições não foi confirmada como causa da falha.

**Esperado:** carregar os componentes disponíveis e tratar falhas parciais com mensagens específicas, sem erro interno não tratado.

**Reteste:** identificar os endpoints completos, correlacionar cada chamada ao componente de origem, inspecionar os logs do servidor, confirmar se existem requisições redundantes e repetir o carregamento após a correção.

---

<a id="bug-019"></a>

## BUG-019 — Cadastro de objetivo de treino retorna HTTP 500

| Campo | Descrição |
| --- | --- |
| Status | Em triagem — causa não determinada; reteste pendente após correção. |
| Severidade / prioridade | Alta / Alta, propostas para triagem; impede confirmar o cadastro no cenário registrado. |
| Módulo | Treinamento / Objetivos Treino / Cadastro |
| Requisitos | [RF35](Analise%20de%20requisitos.md#rf35) |
| Casos | [CT-RF35](Cenario_Teste/CT-RF35_Cadastro_Objetivo_Treino.md) |
| Data da evidência / revisão | 15/11/2026, 18:13 BRT; sem nova execução. |
| Página | https://sifit.centrion.com.br/objetivos-treino |
| Ambiente | Chrome 157.0.8103.78 / Windows (x86) 11, janela 1920 × 911; versão e zoom não confirmados. |
| Frequência conhecida | Um registro do Jam, com duas ocorrências de HTTP 500 na mesma tentativa; recorrência não determinada. |

### Pré-condições e reprodução

**[CT-RF35](Cenario_Teste/CT-RF35_Cadastro_Objetivo_Treino.md):** Sessão autenticada com acesso a Objetivos Treino e à ação Novo Objetivo. Nome de teste disponível, estado inicial da listagem registrado e regra do campo Código e da descrição confirmada.

1. Acessar Objetivos Treino com o painel de rede aberto e registrar a listagem e os cartões.
2. Clicar em Novo Objetivo.
3. Informar o nome Gustavo e a descrição Gustavo 45254#@v.
4. Clicar em Salvar.
5. Observar o diálogo, o status da requisição e a listagem.

### Esperado e obtido

| Caso | Esperado | Obtido |
| --- | --- | --- |
| CT-RF35 | Cadastrar e confirmar dados válidos; informar validação específica para dados recusados, sem erro interno. | `POST /api/objetivo-treino/salvar/1` retorna HTTP 500; a interface exibe o diálogo "Erro ao salvar objetivo" e a listagem permanece sem registros. |

**Impacto:** o objetivo não é cadastrado e a mensagem não orienta a correção dos dados. A persistência de registro parcial não foi conferida; verificar antes de reenviar.

### Evidências técnicas

- [Jam](https://jam.dev/c/1d474477-2411-4a81-b85c-74207402b783), 1:01: clique em Salvar e `POST https://backendsifit.centrion.com.br/api/objetivo-treino/salvar/1` com HTTP 500 (1077 ms); 1:02: segunda ocorrência de POST 500 (856 ms), com OPTIONS HTTP 204 (218 ms) na lista de rede.
- Cabeçalhos de resposta da última entrada: `content-type: application/json; charset=utf-8`, `content-length: 64`, `x-powered-by: PHP/8.2.35`, `date: Sun, 15 Nov 2026 21:12:42 GMT`, `x-hcdn-request-id: dfcc75d79c00e3202a38d84598b45e4b-asc-edge13`. Autenticação omitida.
- Corpo da requisição e da resposta: indisponíveis no Jam ("body unavailable").
- [Formulário preenchido em 1:00](Evidencias/CT-RF35_Cadastro_Objetivo_Treino/formulario_preenchido_01-00.png), [diálogo de erro em 1:04](Evidencias/CT-RF35_Cadastro_Objetivo_Treino/erro_01-04.png), [listagem vazia em 1:11](Evidencias/CT-RF35_Cadastro_Objetivo_Treino/lista_vazia_01-11.png), [lista de rede](Evidencias/CT-RF35_Cadastro_Objetivo_Treino/rede_lista.png) e [Evidências](Evidencias/CT-RF35_Cadastro_Objetivo_Treino/README.md).

### Análise, limites e encaminhamento

O HTTP 500 e o endpoint estão registrados no Jam. Sem logs do servidor, corpos da requisição e da resposta e acesso ao banco, não é possível distinguir exceção não tratada, rejeição de dados (a descrição continha `#@`) ou falha de infraestrutura. A causa técnica não foi confirmada no código. O sufixo `/1` tem significado não confirmado. Duas ocorrências de HTTP 500 para um único clique em Salvar registrado sugerem reenvio ou duplicidade de submissão; é uma hipótese a confirmar, relevante para evitar registros duplicados após a correção.

O comportamento repete a assinatura de [BUG-009](#bug-009), [BUG-010](#bug-010), [BUG-016](#bug-016): resposta de erro interno em operação do servidor, em módulos distintos. O campo Código permaneceu vazio nos quadros apesar da digitação registrada; não foi tratado como defeito, pois pode ser atribuído automaticamente (ver [BUG-011](#bug-011) e [CT-RF31](Cenario_Teste/CT-RF31_Cadastro_GrupoMuscular.md)).

**Reteste:** executar a [matriz do CT-RF35](Cenario_Teste/CT-RF35_Cadastro_Objetivo_Treino.md#critérios-de-aceitação-e-matriz-de-reteste-proposta), confirmar sucesso com dados válidos, validação para dados recusados, persistência, uma única gravação por clique e ausência de registros parciais. Investigar o HTTP 500 correlacionando o endpoint com 21:12:42 GMT de 15/11/2026 e o request ID. Manter em triagem até nova evidência em versão identificada.

---

<a id="bug-020"></a>

## BUG-020 — Cadastro de turma sem modalidade não apresenta retorno visível

| Campo | Descrição |
| --- | --- |
| Status | Em triagem — validação nativa do navegador e obrigatoriedade da modalidade não confirmadas; reteste pendente. |
| Severidade / prioridade | Média / Alta, propostas para triagem. |
| Módulo | SifitBox / Turmas recorrentes / Cadastro |
| Requisitos | [RF41](Analise%20de%20requisitos.md#rf41) |
| Casos | [CT-RF41](Cenario_Teste/CT-RF41_Cadastro_Turma_Sem_Modalidade.md) |
| Data da evidência / revisão | 15/11/2026, 18:51 BRT; sem nova execução. |
| Página | https://sifit.centrion.com.br/sifitbox/turmas |
| Ambiente | Chrome 157.0.8103.78 / Windows (x86) 11, janela 1920 × 911; versão e zoom não confirmados. |
| Frequência conhecida | Um registro do Jam, com tentativas de envio em 0:17–0:20, 1:28 e 1:33; recorrência não determinada. |

### Pré-condições e reprodução

**[CT-RF41](Cenario_Teste/CT-RF41_Cadastro_Turma_Sem_Modalidade.md):** Sessão autenticada com acesso a SifitBox – Turmas, ao menos uma modalidade ativa e turmas existentes registradas.

1. Acessar SifitBox – Turmas com o painel de rede aberto e registrar a listagem de turmas.
2. No formulário de Turma, informar o nome "teste", os horários, os dias da semana e as vagas, mantendo o seletor Modalidade em branco.
3. Acionar o botão de envio de Turma.
4. Observar mensagens, foco, listagem e a rede.

### Esperado e obtido

| Caso | Esperado | Obtido |
| --- | --- | --- |
| CT-RF41 | Bloquear o envio, indicar de forma visível o campo pendente e não criar a turma. | Nenhuma mensagem de validação visível e nenhuma requisição de criação de turma; o formulário permanece preenchido e a listagem mantém as quatro turmas. |

**Impacto:** o usuário não sabe se o envio foi aceito, por que a turma não foi criada nem qual dado corrigir, e pode repetir a tentativa sem compreender o impedimento.

### Evidências técnicas

- [Jam](https://jam.dev/c/ee9a133b-d6b1-442d-b4b0-dd87595b7e70): cinco cliques de envio com os formulários vazios em 0:17–0:20 (cursor sobre o botão Turma em 0:19) e cliques de envio com o formulário de Turma preenchido e a modalidade em branco em 1:28 e 1:33, sem mensagem visível.
- Rede: 35 entradas, sem requisição de criação de turma; o único POST de criação é `modalidades/salvar` (HTTP 201), de outro fluxo.
- [Formulário em 1:29](Evidencias/CT-RF41_Cadastro_Turma_Sem_Modalidade/formulario_turma_01-29.png), [formulário em 1:33](Evidencias/CT-RF41_Cadastro_Turma_Sem_Modalidade/formulario_turma_01-33.png), [listagens em 1:35](Evidencias/CT-RF41_Cadastro_Turma_Sem_Modalidade/lista_apos_tentativa_01-35.png) e [Evidências](Evidencias/CT-RF41_Cadastro_Turma_Sem_Modalidade/README.md).

### Análise, limites e encaminhamento

A ausência de requisição é compatível com validação no cliente (por exemplo, campo obrigatório com validação nativa do navegador), cujo balão normalmente não aparece em gravações de tela; nesse caso o defeito se reduz à falta de indicação própria do sistema, ou deixa de existir. Também é compatível com um envio que não dispara a ação. Não foi confirmado se a modalidade é obrigatória, qual botão foi acionado em 1:17 e em 1:28, nem a causa. O padrão repete o de [BUG-013](#bug-013) (campos obrigatórios vazios sem feedback), em outro módulo. O horário de início igual ao de término em 1:28 não foi tratado como causa.

**Reteste:** reproduzir com a captura de rede preparada e a gravação da tela, confirmar a regra de obrigatoriedade, o foco e as mensagens, enviar a turma válida e conferir a criação e a persistência após recarga. Manter em triagem até nova evidência em versão identificada.

---

<a id="bug-021"></a>

## BUG-021 — Painel Pagar.me mantém Recebimentos e gráfico ao trocar o período

| Campo | Descrição |
| --- | --- |
| Status | Em triagem — causa não determinada; reteste pendente após correção. |
| Severidade / prioridade | Média / Média, propostas para triagem. |
| Módulo | Financeiro / Pagar.me / Painel |
| Requisitos | [RF45](Analise%20de%20requisitos.md#rf45) |
| Casos | [CT-RF45](Cenario_Teste/CT-RF45_Painel_PagarMe_Periodo.md) |
| Data da evidência / revisão | 15/11/2026, 19:06 BRT; sem nova execução. |
| Página | https://sifit.centrion.com.br/pagarme |
| Ambiente | Chrome 157.0.8103.78 / Windows (x86) 11, janela 1920 × 911; versão e zoom não confirmados. |
| Frequência conhecida | Um registro do Jam; recorrência não determinada. |

### Pré-condições e reprodução

**[CT-RF45](Cenario_Teste/CT-RF45_Painel_PagarMe_Periodo.md):** Sessão autenticada com acesso ao módulo Pagar.me e conta de pagamento com movimentação conhecida nos últimos 30 e 7 dias.

1. Acessar o painel Pagar.me com o painel de rede aberto e registrar Recebimentos, o gráfico e os meios de pagamento em "Últimos 30 dias".
2. Selecionar "Últimos 7 dias" no cartão Recebimentos.
3. Comparar o valor, a variação, o gráfico e os meios de pagamento.
4. Conferir os indicadores de saldo (Disponível para saque, Em processamento, Recebíveis futuros e Recebido no mês).

### Esperado e obtido

| Esperado | Obtido |
| --- | --- |
| Ao trocar o período, o valor de Recebimentos, o gráfico e o eixo de datas passam a representar o novo período, de forma coerente com os demais indicadores. | Com "Últimos 7 dias", Recebimentos permanece R$ 38.420,00 e o gráfico é idêntico ao de "Últimos 30 dias"; os indicadores de saldo permanecem "R$ --". |

**Impacto:** O usuário não consegue analisar recebimentos por período e pode tomar decisões com base em valores que não correspondem ao período escolhido. O painel não distingue dados reais de dados de demonstração.

### Evidências técnicas

- [Jam — Pagar.me](https://jam.dev/c/e6e551ef-9196-4c79-b6a2-89747b1e8b33): quadro de 0:00 (período "Últimos 30 dias", Recebimentos R$ 38.420,00) e quadro de 0:25 (período "Últimos 7 dias", mesmo valor e mesmo gráfico); grupos repetidos de `POST` ver-saldo, pagarme, recebiveis e transacoes (HTTP 200) sem corpo capturado.
- [Painel em 0:00](Evidencias/CT-RF45_Painel_PagarMe_Periodo/painel_00-00.png), [painel em 0:25](Evidencias/CT-RF45_Painel_PagarMe_Periodo/painel_periodo_7dias_00-25.png) e [Evidências](Evidencias/CT-RF45_Painel_PagarMe_Periodo/README.md).

### Análise, limites e encaminhamento

O valor e o gráfico idênticos em períodos diferentes são compatíveis com dados de demonstração ou com falha na atualização por período; a leitura do eixo de datas (aparentemente de maio) é aproximada. Os indicadores de saldo em "R$ --" sugerem indisponibilidade da conta de pagamento, o que reforça a hipótese de dados estáticos, sem confirmação. A causa técnica não foi confirmada no código; o clique no seletor não consta na cronologia do Jam.

**Reteste:** Reproduzir com conta de movimentação conhecida, capturando corpo e resposta de `recebiveis`, `transacoes` e `pagarme`, e comparar os períodos; confirmar se os valores exibidos são reais. Manter em triagem até nova evidência em versão identificada.

---

<a id="bug-022"></a>

## BUG-022 — Relatório de Contas a Receber exibe "----" em Valor a Receber

| Campo | Descrição |
| --- | --- |
| Status | Em triagem — causa não determinada; reteste pendente após correção. |
| Severidade / prioridade | Alta / Alta, propostas para triagem. |
| Módulo | Relatórios / Contas a Receber |
| Requisitos | [RF51](Analise%20de%20requisitos.md#rf51) |
| Casos | [CT-RF51](Cenario_Teste/CT-RF51_Relatorio_Contas_Receber.md) |
| Data da evidência / revisão | 15/11/2026, 19:09 BRT; sem nova execução. |
| Página | https://sifit.centrion.com.br/relatorios |
| Ambiente | Chrome 157.0.8103.78 / Windows (x86) 11, janela 1920 × 911; versão e zoom não confirmados. |
| Frequência conhecida | Um relatório gerado; recorrência não determinada. |

### Pré-condições e reprodução

**[CT-RF51](Cenario_Teste/CT-RF51_Relatorio_Contas_Receber.md):** Sessão autenticada com permissão para gerar relatórios e contas a receber pendentes do período com valores conhecidos.

1. Acessar Relatórios e selecionar "Contas a Receber", Tipo de Pagamento "Todos", Status "Pendente" e o período 01/11/2026 a 15/11/2026.
2. Acionar Gerar Relatório.
3. Abrir o PDF e conferir a coluna Valor a Receber e os totais.
4. Comparar com as contas pendentes do módulo Contas a Receber.

### Esperado e obtido

| Esperado | Obtido |
| --- | --- |
| Cada conta pendente apresenta o valor a receber e os totais correspondem às linhas apresentadas. | O PDF lista três contas pendentes, mas a coluna Valor a Receber apresenta "----" em todas as linhas; o rodapé informa "Quantidade de registros: 3" e "Valor Recebido: R$ 0,00". |

**Impacto:** O relatório não permite saber quanto há a receber, o que o torna inadequado para conferência financeira e cobrança.

### Evidências técnicas

- [Jam — Relatórios](https://jam.dev/c/3b4777a4-e1b0-4038-9b06-26c73669d7d1): `POST /api/relatorio/1` com HTTP 200 e quadro de 0:43 com o tipo Contas a Receber e o status Pendente; arquivo `relatorio (6).pdf` (7.882 bytes) gravado às 19:09:39.
- [PDF gerado](Evidencias/CT-RF51_Relatorio_Contas_Receber/relatorio_6_contas_receber.pdf), [formulário em 0:43](Evidencias/CT-RF51_Relatorio_Contas_Receber/formulario_contas_receber_00-43.png) e [Evidências](Evidencias/CT-RF51_Relatorio_Contas_Receber/README.md).

### Análise, limites e encaminhamento

Os valores ausentes são compatíveis com contas sem valor preenchido, com falha na leitura do campo de valor pelo relatório ou com formatação que converte o valor em marcador. A matrícula do aluno de demonstração aparece com R$ 20,00 no relatório de Matrículas (CT-RF50) e com "----" neste relatório, o que sugere que o valor existe em outra origem. A causa técnica não foi confirmada no código; o conteúdo das contas no módulo não foi comparado.

**Reteste:** Comparar as contas pendentes com o módulo Contas a Receber, reexecutar com valores conhecidos e com a opção Detalhado e confirmar valores e totais. Manter em triagem até nova evidência em versão identificada.

---

<a id="bug-023"></a>

## BUG-023 — Relatórios de Avaliações, Clientes, Colaboradores e Caixas geram PDF vazio

| Campo | Descrição |
| --- | --- |
| Status | Em triagem — causa não determinada; reteste pendente após correção. |
| Severidade / prioridade | Alta / Alta, propostas para triagem. |
| Módulo | Relatórios / Avaliações, Clientes, Colaboradores e Caixas |
| Requisitos | [RF53](Analise%20de%20requisitos.md#rf53), [RF54](Analise%20de%20requisitos.md#rf54), [RF55](Analise%20de%20requisitos.md#rf55) e [RF56](Analise%20de%20requisitos.md#rf56) |
| Casos | [CT-RF53](Cenario_Teste/CT-RF53_Relatorio_Avaliacoes_Vazio.md), [CT-RF54](Cenario_Teste/CT-RF54_Relatorio_Clientes_Vazio.md), [CT-RF55](Cenario_Teste/CT-RF55_Relatorio_Colaboradores_Vazio.md) e [CT-RF56](Cenario_Teste/CT-RF56_Relatorio_Caixas_Vazio.md) |
| Data da evidência / revisão | 15/11/2026, 19:09 BRT; sem nova execução. |
| Página | https://sifit.centrion.com.br/relatorios |
| Ambiente | Chrome 157.0.8103.78 / Windows (x86) 11, janela 1920 × 911; versão e zoom não confirmados. |
| Frequência conhecida | Cinco arquivos vazios em uma gravação (Avaliações duas vezes); recorrência não determinada. |

### Pré-condições e reprodução

**CT-RF53 a CT-RF56:** Sessão autenticada com permissão para gerar relatórios, visualizador de PDF e pasta de downloads conferida; período e filtros registrados.

1. Acessar Relatórios, selecionar o tipo (Avaliações, Clientes, Colaboradores ou Caixas) e preencher o período.
2. Acionar Gerar Relatório e observar a requisição de rede.
3. Conferir o arquivo baixado (tamanho e abertura).
4. Repetir para cada um dos quatro tipos e, como controle, para Matrículas.

### Esperado e obtido

| Esperado | Obtido |
| --- | --- |
| O sistema gera um PDF válido com o conteúdo do relatório ou a estrutura vazia explícita e informa falhas ao usuário. | Cada requisição `POST /api/relatorio/1` retorna HTTP 200, mas os arquivos baixados para Avaliações (duas vezes), Clientes, Colaboradores e Caixas têm 0 bytes e não abrem; os relatórios de Matrículas, Contas a Receber e Contas a Pagar abrem. |

**Impacto:** O usuário não consegue obter quatro dos sete relatórios e não recebe mensagem de erro, repetindo a geração sem saber que o arquivo está vazio.

### Evidências técnicas

- [Jam — Relatórios](https://jam.dev/c/3b4777a4-e1b0-4038-9b06-26c73669d7d1): oito `POST /api/relatorio/1` com HTTP 200 e um `OPTIONS` HTTP 204; quadros com os tipos Avaliações (0:08–0:18), Clientes (0:23), Colaboradores (0:28–0:33) e Caixas (0:53–0:57).
- Arquivos baixados: `relatorio (1).pdf`, `(2)`, `(3)`, `(4)` e `(8)` com 0 bytes (SHA-256 `e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855`); `(5)`, `(6)` e `(7)` com 7.784, 7.882 e 7.872 bytes.
- [Evidências de CT-RF53](Evidencias/CT-RF53_Relatorio_Avaliacoes_Vazio/README.md), [CT-RF54](Evidencias/CT-RF54_Relatorio_Clientes_Vazio/README.md), [CT-RF55](Evidencias/CT-RF55_Relatorio_Colaboradores_Vazio/README.md) e [CT-RF56](Evidencias/CT-RF56_Relatorio_Caixas_Vazio/README.md).

### Análise, limites e encaminhamento

A geração com HTTP 200 e arquivo de 0 bytes é compatível com falha silenciosa na construção do PDF (exceção capturada sem retorno de erro), resposta vazia do servidor ou falha no download no navegador; não foi possível distinguir. A correspondência dos cinco arquivos vazios com os tipos é inferida pela ordem dos downloads e pela ordem dos tipos selecionados no vídeo; os arquivos 5 a 7 foram identificados pelo conteúdo e seguem a mesma ordem. O corpo e a resposta das requisições não foram capturados e a causa técnica não foi confirmada no código.

**Reteste:** Reproduzir cada tipo separadamente, capturando requisição e resposta e o tamanho do arquivo, com e sem registros no período; confirmar a causa nos logs do servidor e comparar com os relatórios que abrem. Manter em triagem até nova evidência em versão identificada.

---

## BUG-026 a BUG-031 — Colaboradores

| ID | Reprodução resumida | Esperado | Obtido / evidência | Encaminhamento |
| --- | --- | --- | --- | --- |
| <a id="bug-026"></a>BUG-026 | Informar `18/05/2222` e salvar. | Recusar data futura. | Atualização HTTP 200 e navegação à lista. | Validar limites e confirmar ausência de persistência. |
| <a id="bug-027"></a>BUG-027 | Limpar a data obrigatória e salvar. | Bloquear e indicar o campo. | Atualização HTTP 200. | Mapear obrigatoriedade e preservar valor anterior. |
| <a id="bug-028"></a>BUG-028 | Informar CREF `TESTEE` e salvar. | Aplicar formato definido. | Atualização HTTP 200. | Confirmar regra e testar exemplos válidos/inválidos. |
| <a id="bug-029"></a>BUG-029 | Deixar campo obrigatório vazio e salvar. | Bloquear e identificar o campo. | Atualização HTTP 200. | Identificar o campo na reprodução e testar todos os obrigatórios. |
| <a id="bug-030"></a>BUG-030 | Adicionar duas vezes `funcao_id: 2` ao colaborador 4. | Manter associação única. | Dois HTTP 201; consulta retorna ids 51, 154 e 155. | Impedir duplicidade no servidor e testar concorrência. |
| <a id="bug-031"></a>BUG-031 | Confirmar exclusão do colaborador id 3. | Excluir ou explicar vínculo impeditivo. | HTTP 500 e `Erro interno inesperado`. | Consultar logs/vínculos e retestar permitido/impedido. |

**Status comum:** Em triagem; severidades e prioridades propostas. As gravações ocorreram entre 22:06 e 22:13 BRT de 15/11/2026. Não houve nova execução, consulta ao banco ou inspeção do código.

## BUG-033 e BUG-034 — Buscas de Colaboradores

| ID | Reprodução resumida | Esperado | Obtido / evidência | Encaminhamento |
| --- | --- | --- | --- | --- |
| <a id="bug-033"></a>BUG-033 | Buscar colaborador por nome e avançar para a próxima página. | Manter o filtro e exibir somente nomes correspondentes em todas as páginas. | A página seguinte inclui nomes fora do filtro; [Jam](https://jam.dev/c/b35516e3-c571-47ea-b233-28f00d1fca4c). | Verificar parâmetros da paginação, total filtrado e estado do formulário; retestar avançar e voltar. |
| <a id="bug-034"></a>BUG-034 | Buscar um código sem colaborador associado. | Exibir mensagem de nenhum resultado, sem linhas ou ações. | A tabela renderiza uma linha vazia; [Jam](https://jam.dev/c/cdbb3d76-3d6a-4d36-adf9-edd935b5a449). | Validar resposta vazia, normalização dos dados e renderização condicional da tabela. |

**Status comum:** Em triagem; severidade Média e prioridade Alta propostas. Gravações em 15/11/2026, na página `/colaboradores`, Edge 157.0.8103.80 / Windows 11. A análise foi visual; requisições e respostas não foram inspecionadas, não houve nova execução e a causa técnica não foi confirmada.
<a id="bug-024"></a>

## BUG-024 — Exclusão de grupo retorna HTTP 500 e mensagem genérica

| Campo | Descrição |
| --- | --- |
| Status | Em triagem — causa não determinada; reteste pendente após correção. |
| Severidade / prioridade | Média / Alta, propostas para triagem. |
| Módulo | Treinamento / Grupos / Exclusão |
| Requisitos | [RF57](Analise%20de%20requisitos.md#rf57) |
| Casos | [CT-RF57](Cenario_Teste/CT-RF57_Exclusao_Grupo.md) |
| Data da evidência / revisão | 15/11/2026, 21h03 BRT; sem nova execução. |
| Página | https://sifit.centrion.com.br/grupos |
| Ambiente | Chrome 157.0.8103.78 / Windows (x86) 11; versão e zoom não confirmados. |

### Pré-condições e reprodução

**[CT-RF57](Cenario_Teste/CT-RF57_Exclusao_Grupo.md):** Sessão autenticada com permissão para excluir grupos. Registro de teste cuja exclusão seja permitida, com vínculos conhecidos para distinguir impedimento de regra de falha do servidor.

1. Acionar o ícone de exclusão na linha do grupo.
2. Confirmar a exclusão no diálogo "Deseja deletar o Grupo?".
3. Conferir o retorno visual, o status da chamada e a presença do registro após a operação.

### Esperado e obtido

| Caso | Esperado | Obtido |
| --- | --- | --- |
| CT-RF57 | Concluir a exclusão permitida, removendo o registro e atualizando os contadores; ou explicar de forma tratável o impedimento, sem erro interno. | O registro (grupo código 1, "Treino Livre") permanece na listagem e os contadores de cartões não se alteram entre as tentativas. |

**Impacto:** A exclusão não é concluída. O endpoint e a mensagem genérica retornada coincidem exatamente com os já registrados em [BUG-016](#bug-016) para a exclusão de grupo muscular, o que sugere uma causa comum no tratamento de exclusões do backend.

### Evidências

- [CT-RF57](Cenario_Teste/CT-RF57_Exclusao_Grupo.md): [Jam — Tela de Grupos](https://jam.dev/c/b1231a75-1a65-4bf0-b795-f52a8c7d3365). 1:19: acionamento do ícone de exclusão. 1:20: diálogo de confirmação "Deseja deletar o Grupo?". 1:21: `POST /api/deleta/grupo/1` retorna HTTP 500 em 987 ms. 1:30: segunda tentativa no mesmo endpoint, também HTTP 500, em 230 ms.
- Corpo de resposta nas duas tentativas: `{"verifica_erro": true, "mensagem": "Erro interno inesperado."}`.
- Cabeçalhos registrados: `content-type: application/json; charset=utf-8`, `content-length: 64`, `content-encoding: br`, `x-powered-by: PHP/8.2.35`. Primeira tentativa em `Seg, 16 de nov de 2026 00:03:09 GMT`, `x-hcdn-request-id: 8f18afe5ff0e3a9e3d1c944d69811576-asc-edge13`; segunda em `00:03:19 GMT`, `x-hcdn-request-id: bc5d59dc99d0c01de186f1b3125a9b80-asc-edge13`.

### Análise, limites e encaminhamento

O HTTP 500 e o endpoint estão registrados no Jam. Não houve acesso a logs do servidor, ao corpo completo da resposta além dos 64 bytes retornados nem ao banco de dados, de modo que não é possível distinguir entre falha de infraestrutura, exceção não tratada na aplicação e restrição de integridade referencial não capturada. Não foi possível confirmar visualmente o texto do diálogo de erro apresentado após a falha, pois o componente de alerta é fechado em menos de um segundo na gravação.

Não foi verificado se o registro permanece íntegro após as duas tentativas enviadas para o mesmo recurso, nem exercitado o cenário de exclusão com impedimento de regra.

Investigar o HTTP 500 com logs do servidor e os vínculos do registro, em conjunto com a investigação já proposta para o BUG-016, dada a coincidência de endpoint e mensagem; corrigir e retestar os cenários permitido e impedido. O status permanece em triagem até que a causa seja determinada e uma nova execução comprove os critérios de aceitação do caso associado.

---

<a id="bug-025"></a>

## BUG-025 — Edição de grupo não persiste o campo status apesar de retorno de sucesso

| Campo | Descrição |
| --- | --- |
| Status | Em triagem — causa não determinada; reteste pendente após correção. |
| Severidade / prioridade | Média / Alta, propostas para triagem. |
| Módulo | Treinamento / Grupos / Edição |
| Requisitos | [RF58](Analise%20de%20requisitos.md#rf58) |
| Casos | [CT-RF58](Cenario_Teste/CT-RF58_Edicao_Grupo.md) |
| Data da evidência / revisão | 15/11/2026, 21h03 BRT; sem nova execução. |
| Página | https://sifit.centrion.com.br/grupos |
| Ambiente | Chrome 157.0.8103.78 / Windows (x86) 11; versão e zoom não confirmados. |

### Pré-condições e reprodução

**[CT-RF58](Cenario_Teste/CT-RF58_Edicao_Grupo.md):** Sessão autenticada com permissão para editar grupos. Grupo de teste com todos os campos atuais registrados antes da edição.

1. Abrir a edição do grupo e alterar apenas o campo Status, mantendo os demais campos.
2. Acionar o botão Salvar.
3. Conferir a resposta da API e, em seguida, consultar novamente o registro.

### Esperado e obtido

| Caso | Esperado | Obtido |
| --- | --- | --- |
| CT-RF58 | A edição do campo Status retorna sucesso somente quando o valor é persistido; a consulta seguinte reflete o novo status. | A edição retorna sucesso (`verifica_erro: false`), mas a consulta imediatamente seguinte mostra o grupo ainda com o status anterior ("ativo"). |

**Impacto:** O usuário recebe confirmação de sucesso para uma alteração que não foi salva, sem qualquer indicação de falha na interface. Na mesma sessão e no mesmo registro, a edição do campo Descrição é persistida corretamente, o que isola a falha ao campo `status` e descarta causa geral de sessão, rede ou salvamento.

### Evidências

- [CT-RF58](Cenario_Teste/CT-RF58_Edicao_Grupo.md): [Jam — Tela de Grupos](https://jam.dev/c/b1231a75-1a65-4bf0-b795-f52a8c7d3365). 0:58: clique no botão Salvar após selecionar Status = "Inativo". `POST /api/edita/grupo/1` com `{"id":11,"nome":"Treino sla","mostrar_home":"nao","caixa":"interno","descricao":"Esse treino","status":"inativo"}` retorna HTTP 200, `{"verifica_erro": false}`. No mesmo instante, `GET /api/grupos/1` e `POST /api/seleciona/grupo/1` retornam o grupo id 11 ainda com `"status": "ativo"`. 1:10: segunda edição, alterando apenas a descrição para "Ess"; `POST /api/edita/grupo/1` retorna HTTP 200, `{"verifica_erro": false}`, e a consulta seguinte confirma `"descricao": "Ess"` persistida.
- Cabeçalhos registrados: `content-type: application/json; charset=utf-8`. Primeira edição em `Segunda-feira, 16 de novembro de 2026, 08:02:46 GMT`; segunda em `08:02:58 GMT`. O campo `updated_at` do corpo da resposta registra `12:02:46` e `12:02:58` para os mesmos instantes — descompasso de cerca de 4 horas em relação ao cabeçalho HTTP `data`, sem causa determinada.

### Análise, limites e encaminhamento

A falha é específica do campo `status`: o mesmo endpoint, no mesmo registro e na mesma sessão, persiste corretamente o campo `descricao` logo em seguida. Isso aponta para uma causa na rotina de edição do backend — por exemplo, uma whitelist de campos editáveis que exclui `status`, ou uma atualização que o ignora silenciosamente — e não para uma falha geral de sessão, rede ou salvamento. Não houve acesso a logs do servidor, ao código da rotina nem ao banco de dados para confirmar o valor realmente gravado.

Investigar a rotina de edição do grupo (`/api/edita/grupo/{id}`), com foco no tratamento do campo `status`; verificar se o mesmo ocorre ao reativar um grupo (Inativo → Ativo) e em outras entidades com campo de status semelhante, incluindo grupo muscular, dado o padrão de nomenclatura de endpoints já observado nos BUG-016 e BUG-024. O status permanece em triagem até que a causa seja determinada e uma nova execução comprove os critérios de aceitação do caso associado.

---

## BUG-026 a BUG-031 — Colaboradores

| ID | Reprodução resumida | Esperado | Obtido / evidência | Encaminhamento |
| --- | --- | --- | --- | --- |
| <a id="bug-026"></a>BUG-026 | Informar `18/05/2222` e salvar. | Recusar data futura. | Atualização HTTP 200 e navegação à lista. | Validar limites e confirmar ausência de persistência. |
| <a id="bug-027"></a>BUG-027 | Limpar a data obrigatória e salvar. | Bloquear e indicar o campo. | Atualização HTTP 200. | Mapear obrigatoriedade e preservar valor anterior. |
| <a id="bug-028"></a>BUG-028 | Informar CREF `TESTEE` e salvar. | Aplicar formato definido. | Atualização HTTP 200. | Confirmar regra e testar exemplos válidos/inválidos. |
| <a id="bug-029"></a>BUG-029 | Deixar campo obrigatório vazio e salvar. | Bloquear e identificar o campo. | Atualização HTTP 200. | Identificar o campo na reprodução e testar todos os obrigatórios. |
| <a id="bug-030"></a>BUG-030 | Adicionar duas vezes `funcao_id: 2` ao colaborador 4. | Manter associação única. | Dois HTTP 201; consulta retorna ids 51, 154 e 155. | Impedir duplicidade no servidor e testar concorrência. |
| <a id="bug-031"></a>BUG-031 | Confirmar exclusão do colaborador id 3. | Excluir ou explicar vínculo impeditivo. | HTTP 500 e `Erro interno inesperado`. | Consultar logs/vínculos e retestar permitido/impedido. |

**Status comum:** Em triagem; severidades e prioridades propostas. As gravações ocorreram entre 22:06 e 22:13 BRT de 15/11/2026. Não houve nova execução, consulta ao banco ou inspeção do código.

---

## BUG-032 — Cadastro de anamnese retorna HTTP 500 ao salvar ou aplicar

| Campo | Descrição |
| --- | --- |
| Status | Em triagem — causa não determinada; reteste pendente após correção. |
| Severidade / prioridade | Média / Alta, propostas para triagem. |
| Módulo | Treinamento / Fichas de Anamnese / Cadastro |
| Requisitos | [RF59](Analise%20de%20requisitos.md#rf59) |
| Casos | [CT-RF59](Cenario_Teste/CT-RF59_Cadastro_Anamnese.md) |
| Data da evidência / revisão | 15/11/2026, 22h07 BRT; sem nova execução. |
| Página | https://sifit.centrion.com.br/anamneses |
| Ambiente | Chrome 157.0.8103.78 / Windows (x86) 11; versão e zoom não confirmados. |

### Pré-condições e reprodução

**[CT-RF59](Cenario_Teste/CT-RF59_Cadastro_Anamnese.md):** Sessão autenticada com permissão para cadastrar anamneses. Aluno cadastrado e selecionável; modelo de anamnese com ao menos uma pergunta.

1. Abrir "Nova Anamnese", selecionar aluno e modelo, avançar até a pergunta.
2. Preencher a resposta e avançar até a revisão final.
3. Acionar "Salvar rascunho" ou a aplicação definitiva.

### Esperado e obtido

| Caso | Esperado | Obtido |
| --- | --- | --- |
| CT-RF59 | O backend grava o rascunho ou a anamnese aplicada e retorna sucesso. | As sete tentativas registradas (quatro em `aplicar`, três em `rascunho`) retornam HTTP 500 com a mesma mensagem genérica; nenhuma anamnese é cadastrada com sucesso. |

**Impacto:** O usuário não consegue concluir o cadastro de nenhuma anamnese, nem como rascunho nem de forma definitiva, em nenhuma das tentativas registradas na gravação, com dois modelos e três respostas diferentes.

### Evidências

- [CT-RF59](Cenario_Teste/CT-RF59_Cadastro_Anamnese.md): [Jam — Fichas de Anamnese](https://jam.dev/c/7be0fe71-3419-4050-b63f-473d943fa08e). 0:28: `POST /api/anamnese/aplicar/1` com `{"modelo_id":3,"respostas":[{"pergunta_id":"5","resposta":"Esse"}],"status":"concluida"}` retorna HTTP 500, `{"verifica_erro": true, "mensagem": "Erro interno inesperado."}`. 0:42, 1:03 e 1:10: três tentativas de `POST /api/anamnese/rascunho/1` retornam o mesmo HTTP 500. 1:12: `POST /api/anamnese/aplicar/1` com `{"modelo_id":5,"respostas":[{"pergunta_id":"5","resposta":"Agachamento"}],"status":"concluida"}` retorna o mesmo HTTP 500.
- Cabeçalhos registrados: `content-type: application/json; charset=utf-8`, `comprimento-do-conteúdo: 64`. Data registrada em uma das tentativas de rascunho: `Segunda-feira, 16 de novembro de 2026, 01:05:48 GMT`.

### Análise, limites e encaminhamento

O erro ocorre de forma idêntica nos dois endpoints envolvidos (`aplicar` e `rascunho`), em dois modelos de anamnese diferentes e com três respostas de conteúdo distinto, sempre com a mesma mensagem genérica — o mesmo padrão de resposta já registrado em [BUG-016](#bug-016) e [BUG-024](#bug-024). Não houve acesso a logs do servidor, ao código das rotinas nem ao banco de dados para identificar a exceção real por trás do erro.

Investigar as rotinas de servidor acionadas por `/api/anamnese/aplicar/{id}` e `/api/anamnese/rascunho/{id}`, com acesso a logs para confirmar se a causa é a mesma do BUG-016/BUG-024 ou uma falha independente do módulo de anamnese; confirmar também se o identificador final da URL corresponde ao `empresa_id`. O status permanece em triagem até que a causa seja determinada e uma nova execução comprove os critérios de aceitação do caso associado.

---

<a id="bug-035"></a>

## BUG-035 — Bandeira criada com parcela não aparece na listagem

| Campo | Descrição |
| --- | --- |
| Status | Em triagem — causa não determinada; reteste pendente após correção. |
| Severidade / prioridade | Média / Alta, propostas para triagem. |
| Módulo | Bandeiras de Cartão |
| Requisito | [RF81](Analise%20de%20requisitos.md#rf81) |
| Caso | [CT-RF81](Cenario_Teste/CT-RF81_Cadastro_Bandeira_Parcela_Listagem.md) |
| Data da evidência / integração | 16/11/2026, conforme o resumo; sem nova execução. |
| Ambiente | URL, navegador, sistema operacional, versão e zoom não informados no resumo. |

### Pré-condições e reprodução

- Sessão autenticada com permissão para cadastrar Bandeiras de Cartão.
- Ambiente de teste com possibilidade de cadastrar uma bandeira e sua configuração de parcela.

1. Clicar em Nova Bandeira.
2. Informar nome master e taxas adicional e de débito de 1,11.
3. Adicionar a configuração de parcela número 2 com taxa 3,33 e confirmar a inclusão.
4. Clicar em Salvar e conferir a listagem.

### Esperado e obtido

| Caso | Esperado | Obtido |
| --- | --- | --- |
| CT-RF81 | A bandeira deve ser criada com a configuração de parcela e aparecer na listagem após o salvamento. | A API confirma a criação da bandeira de código 34 e da parcela, mas a consulta seguinte retorna [] e a interface continua exibindo Nenhuma bandeira encontrada. A criação da parcela tem retorno de sucesso; o fluxo completo apresenta erro na recuperação/exibição do cadastro. |

**Impacto:** O usuário recebe retornos de criação bem-sucedida, mas não consegue localizar a bandeira; repetir o cadastro pode gerar duplicidade.

### Evidências técnicas informadas no resumo

- 00:11: POST /api/cria/bandeira/1 retorna HTTP 201, verifica_erro=false e id=34.
- 00:11: POST /api/cria/parcela-bandeira/1 envia bandeira_id=34, n_parcela=2 e taxa=3,33; retorna HTTP 201 e verifica_erro=false.
- 00:11: POST /api/bandeiras/1 retorna HTTP 200 com corpo [].
- Quadro de 00:13.191 mostra a listagem vazia após fechar a janela.

Fonte: [Evidências](Evidencias/CT-RF81_Cadastro_Bandeira_Parcela_Listagem/README.md) ([RESUMO.txt](Evidencias/CT-RF81_Cadastro_Bandeira_Parcela_Listagem/RESUMO.txt)) e [Jam](https://jam.dev/c/2f0280fb-6b7f-4cf0-a45c-02f8c16b6c5e).

### Análise, limites e encaminhamento

A causa da divergência e a persistência efetiva no banco não foram verificadas. A gravação comprova a diferença entre os retornos de criação e de listagem, sem permitir atribuir a causa ao frontend ou ao backend.
Análise da gravação e dos eventos capturados no Jam; não foi executado um novo teste no sistema.

Investigar a divergência criação/consulta; retestar listagem, reabertura e recarga com e sem parcela.

Os retornos HTTP 201 de criação e HTTP 200 com lista vazia comprovam a divergência relatada no resumo; não permitem atribuir a causa ao frontend, ao backend ou à persistência no banco.

### Critérios para reteste

1. A criação da bandeira e da parcela é concluída de forma coerente.
2. A consulta posterior inclui a bandeira confirmada pela criação.
3. A listagem exibe o novo registro sem exigir um novo cadastro.
4. Reabrir e recarregar a bandeira permite conferir taxas e configuração de parcela.
5. Uma falha parcial deve produzir mensagem clara e permitir recuperação sem duplicidade.

Integração documental dos arquivos RESUMO.txt fornecidos em `C:\Users\Leonardo\Desktop\evidencias`, com data de gravação e análise informada de 16/11/2026. Os Jams não foram reabertos nesta integração; eventos de rede, horários e quadros abaixo são transcritos dos resumos, sem verificação independente. Não houve nova execução do SIFIT, reteste, consulta ao banco, logs ou código.

---

<a id="bug-036"></a>

## BUG-036 — Tema escuro aplicado de forma incompleta em Bandeiras

| Campo | Descrição |
| --- | --- |
| Status | Em triagem — causa não determinada; reteste pendente após correção. |
| Severidade / prioridade | Média / Média, propostas para triagem. |
| Módulo | Bandeiras de Cartão |
| Requisito | [RF82](Analise%20de%20requisitos.md#rf82) |
| Caso | [CT-RF82](Cenario_Teste/CT-RF82_Tema_Escuro_Bandeiras.md) |
| Data da evidência / integração | 16/11/2026, conforme o resumo; sem nova execução. |
| Ambiente | URL, navegador, sistema operacional, versão e zoom não informados no resumo. |

### Pré-condições e reprodução

- Sessão autenticada com acesso à tela Bandeiras de Cartão.
- Controle de tema disponível e listagem no estado vazio observado.

1. Observar a tela com o tema Escuro selecionado.
2. Alternar para Claro, retornar a Escuro e selecionar Claro novamente.
3. Comparar o fundo da página com os painéis de busca e listagem.

### Esperado e obtido

| Caso | Esperado | Obtido |
| --- | --- | --- |
| CT-RF82 | O tema selecionado deve ser aplicado de forma consistente ao fundo, aos painéis e aos textos da tela. | No tema Escuro, os painéis ficam escuros, mas o fundo principal continua claro. Os textos da área vazia da listagem apresentam baixa legibilidade visual. A descrição do Jam relata: Fundo com falta de cores e modo escuro incompleto. |

**Impacto:** A aplicação parcial do tema prejudica a consistência visual e a leitura do estado vazio da listagem.

### Evidências técnicas informadas no resumo

- Quadro de 00:03.800 mostra o tema Escuro selecionado, painéis escuros e fundo principal claro.
- Quadros de 00:05.320 e 00:06.840 permitem comparar os temas Claro e Escuro.
- 00:04–00:07: alterações de tema chamam POST /api/usuario/tema e recebem HTTP 200.

Fonte: [Evidências](Evidencias/CT-RF82_Tema_Escuro_Bandeiras/README.md) ([RESUMO.txt](Evidencias/CT-RF82_Tema_Escuro_Bandeiras/RESUMO.txt)) e [Jam](https://jam.dev/c/ae4dc198-8a42-4451-898a-fb376596c744).

### Análise, limites e encaminhamento

O erro visual é observado na gravação. Não foram medidos índices de contraste nem feita auditoria formal de acessibilidade; a causa técnica não foi determinada.
Análise da gravação e dos eventos capturados no Jam; não foi executado um novo teste no sistema.

Revisar os estilos da página e retestar Claro/Escuro com lista vazia e preenchida; medir contraste separadamente.

Não foram medidos índices de contraste; a classificação se limita à aplicação visual incompleta do tema descrita no resumo. A semelhança com BUG-007, de outra tela, não confirma causa compartilhada.

### Critérios para reteste

1. O tema Escuro é aplicado ao fundo principal e aos painéis.
2. Os textos do estado vazio permanecem visualmente legíveis.
3. Alternar os temas mantém a consistência entre fundo, painéis e textos.
4. No reteste, conferir também a listagem preenchida.
5. Medições de contraste, se realizadas, devem registrar valores e o critério adotado separadamente.

Integração documental dos arquivos RESUMO.txt fornecidos em `C:\Users\Leonardo\Desktop\evidencias`, com data de gravação e análise informada de 16/11/2026. Os Jams não foram reabertos nesta integração; eventos de rede, horários e quadros abaixo são transcritos dos resumos, sem verificação independente. Não houve nova execução do SIFIT, reteste, consulta ao banco, logs ou código.

---

<a id="bug-037"></a>

## BUG-037 — Cadastro de lead aceito apenas com nome, com obrigatoriedade a confirmar

| Campo | Descrição |
| --- | --- |
| Status | Em triagem — regra de obrigatoriedade a confirmar antes de definir correção. |
| Severidade / prioridade | Média / Alta, propostas para triagem. |
| Módulo | Prospecção |
| Requisito | [RF83](Analise%20de%20requisitos.md#rf83) |
| Caso | [CT-RF83](Cenario_Teste/CT-RF83_Cadastro_Lead_Apenas_Nome.md) |
| Data da evidência / integração | 16/11/2026, conforme o resumo; sem nova execução. |
| Ambiente | URL, navegador, sistema operacional, versão e zoom não informados no resumo. |

### Pré-condições e reprodução

- Sessão autenticada com permissão para adicionar leads.
- Para concluir o reteste, confirmar com o produto quais campos são obrigatórios além do nome; essa regra não acompanha a evidência.

1. Na janela Adicionar Lead, preencher somente o nome Leo.
2. Manter telefone, e-mail e observação visualmente vazios e o estágio padrão Novo Contato.
3. Clicar em Salvar Lead.

### Esperado e obtido

| Caso | Esperado | Obtido |
| --- | --- | --- |
| CT-RF83 | Segundo o cenário identificado como bug pelo autor, o cadastro incompleto deveria ser bloqueado e os campos obrigatórios deveriam ser indicados. | O sistema aceita o envio sem bloqueio visível, cria o lead de código 19 e atualiza a listagem. O total de leads passa de 14 para 15. |

**Impacto:** Se a regra exigir dados adicionais, o cadastro aceita leads incompletos e pode comprometer o contato posterior. O impacto depende da regra de produto.

### Evidências técnicas informadas no resumo

- 00:02: nome Leo preenchido; os demais campos de contato permanecem visualmente vazios.
- 00:03: POST /api/salvar-lead/1 retorna HTTP 200, verifica_erro=false e id=19. O corpo enviado confirma telefone e observacao vazios.
- 00:03: GET /api/leads/1 retorna HTTP 200; quadro de 00:08.223 mostra o registro de código 19.

Fonte: [Evidências](Evidencias/CT-RF83_Cadastro_Lead_Apenas_Nome/README.md) ([RESUMO.txt](Evidencias/CT-RF83_Cadastro_Lead_Apenas_Nome/RESUMO.txt)) e [Jam](https://jam.dev/c/ef3df03c-16ce-4cb6-b0c7-d04514cab4f6).

### Análise, limites e encaminhamento

A classificação de erro acompanha o título do Jam. A regra formal dos campos obrigatórios não foi fornecida; é necessário validá-la para definir exatamente quais campos devem impedir o cadastro. O e-mail está mascarado nos dados de rede, e sua ausência foi avaliada visualmente.
Análise da gravação e dos eventos capturados no Jam; não foi executado um novo teste no sistema.

Confirmar obrigatoriedade com produto antes de definir correção; testar campos isolados, envio completo e ausência de criação inválida.

O relato é mantido como reprovação provisória, sem afirmar que telefone, e-mail ou observação sejam obrigatórios. O e-mail está mascarado na rede e sua ausência foi avaliada visualmente pelo autor do resumo. Se o produto permitir cadastro somente com nome, reclassificar o caso e encerrar este relato como comportamento esperado.

### Critérios para reteste

1. Produto confirma e documenta os campos obrigatórios para o cadastro.
2. Se a regra exigir dados além do nome, o envio incompleto é bloqueado e cada campo faltante é indicado.
3. A validação confirmada é aplicada também no servidor, sem criar registro inválido.
4. Um envio completo conforme a regra permite cadastrar o lead.
5. Se apenas o nome for suficiente pela regra aprovada, reclassificar o caso e encerrar o relato como comportamento esperado.

Integração documental dos arquivos RESUMO.txt fornecidos em `C:\Users\Leonardo\Desktop\evidencias`, com data de gravação e análise informada de 16/11/2026. Os Jams não foram reabertos nesta integração; eventos de rede, horários e quadros abaixo são transcritos dos resumos, sem verificação independente. Não houve nova execução do SIFIT, reteste, consulta ao banco, logs ou código.

---

<a id="bug-038"></a>

## BUG-038 — Telefone do lead aceita 30 dígitos sem máscara nem validação

| Campo | Descrição |
| --- | --- |
| Status | Em triagem — causa não determinada; reteste pendente após correção. |
| Severidade / prioridade | Média / Média, propostas para triagem. |
| Módulo | Prospecção / Leads / Validação do telefone |
| Requisitos | [RF89](Analise%20de%20requisitos.md#rf89) |
| Casos | [CT-RF89](Cenario_Teste/CT-RF89_Telefone_Lead_Sem_Validacao.md) |
| Data da evidência / revisão | 15/11/2026, 21:52 BRT; sem nova execução. |
| Página | https://sifit.centrion.com.br/prospeccao |
| Ambiente | Chrome 157.0.8103.78 / Windows (x86) 11, janela 1920 × 911; versão e zoom não confirmados. |
| Frequência conhecida | Um registro do Jam; recorrência não determinada. |

### Pré-condições e reprodução

**[CT-RF89](Cenario_Teste/CT-RF89_Telefone_Lead_Sem_Validacao.md):** Sessão autenticada com acesso a Prospecção e regra do campo Telefone definida com o produto.

1. Acessar Prospecção e acionar Adicionar Lead.
2. Preencher o nome e o estágio e informar no campo Telefone (placeholder "(00) 00000-0000") um valor de 30 dígitos, como 44999999999 seguido de 5757534534534534534.
3. Acionar Salvar Lead e observar a mensagem de validação e a rede.
4. Abrir o lead criado pela lupa e conferir o telefone gravado.
5. Repetir com telefones de 8, 10 e 11 dígitos e com letras para confirmar o formato aceito.

### Esperado e obtido

| Esperado | Obtido |
| --- | --- |
| O campo limita o tamanho e os caracteres ao formato exibido e rejeita um telefone com 30 dígitos, com mensagem clara. | O campo aceitou 30 dígitos sem máscara, o lead foi criado (código 10) e o valor retornou na consulta do lead, sem mensagem de validação. |

**Impacto:** O cadastro aceita telefones inválidos, o que compromete o contato com o lead e a qualidade da base de prospecção; o placeholder induz o usuário a esperar um formato que não é aplicado.

### Evidências técnicas

- [Jam — Prospecção](https://jam.dev/c/308607ff-8abc-40af-8c7c-429ce506ed64): quadro de 0:47 com o campo Telefone de valor longo e sem máscara; `POST /api/salvar-lead/1` (HTTP 200) com `"telefone"` de 30 dígitos e resposta `{"verifica_erro": false, "id": 10}`; `POST /api/buscar-lead/1` (HTTP 200) devolvendo o mesmo telefone.
- [Telefone em 0:47](Evidencias/CT-RF89_Telefone_Lead_Sem_Validacao/telefone_30_digitos_00-47.png), [corpo do salvar-lead](Evidencias/CT-RF89_Telefone_Lead_Sem_Validacao/requisicao_salvar.png), [resposta do buscar-lead](Evidencias/CT-RF89_Telefone_Lead_Sem_Validacao/resposta_buscar.png) e [Evidências](Evidencias/CT-RF89_Telefone_Lead_Sem_Validacao/README.md).

### Análise, limites e encaminhamento

O valor gravado com 30 dígitos é compatível com ausência de validação de tamanho e de máscara no cliente e no servidor; não foi possível distinguir se a regra do campo permite texto livre, caso em que o ponto passa a ser a adequação do placeholder. A leitura assume que os dois trechos digitados em 0:33 e 0:37 pertencem ao mesmo campo, o que o quadro de 0:47 e o corpo da requisição sustentam, sem prova independente. A causa técnica não foi confirmada no código.

**Reteste:** Reproduzir com telefones de 8, 10, 11 e 30 dígitos e com letras, capturando mensagem, corpo e resposta; confirmar a regra com o produto e a validação no servidor. Manter em triagem até nova evidência em versão identificada.

---

<a id="bug-039"></a>

## BUG-039 — Conta a pagar a colaborador é cadastrada sem colaborador informado

| Campo | Descrição |
| --- | --- |
| Status | Em triagem — causa não determinada; reteste pendente após correção. |
| Severidade / prioridade | Alta / Alta, propostas para triagem. |
| Módulo | Financeiro / Contas a Pagar / Cadastro |
| Requisitos | [RF92](Analise%20de%20requisitos.md#rf92) |
| Casos | [CT-RF92](Cenario_Teste/CT-RF92_Cadastro_Conta_Colaborador_Sem_Colaborador.md) |
| Data da evidência / revisão | 15/11/2026, 21:58 BRT; sem nova execução. |
| Página | https://sifit.centrion.com.br/contas-pagar |
| Ambiente | Chrome 157.0.8103.78 / Windows (x86) 11, janela 1920 × 911; versão e zoom não confirmados. |
| Frequência conhecida | Um registro do Jam; recorrência não determinada. |

### Pré-condições e reprodução

**[CT-RF92](Cenario_Teste/CT-RF92_Cadastro_Conta_Colaborador_Sem_Colaborador.md):** Sessão autenticada com acesso a Contas a Pagar e regra de obrigatoriedade do colaborador definida com o produto.

1. Acessar Contas a Pagar e acionar Nova Conta.
2. Selecionar o tipo Pagto. Colaborador e preencher título, documento, categoria e valor sem informar o colaborador (Código e Colaborador vazios).
3. Acionar Salvar e observar a mensagem de validação e a rede.
4. Conferir a listagem e a coluna Fornecedor / Colaborador da conta criada.
5. Repetir informando o colaborador e comparar.

### Esperado e obtido

| Esperado | Obtido |
| --- | --- |
| Uma conta do tipo Pagto. Colaborador exige o colaborador favorecido e a gravação é impedida, com mensagem clara, enquanto o campo estiver vazio. | A conta foi gravada (HTTP 201, `verifica_erro` false) com `colaborador_recebedor_id` e `colaborador_nome` vazios e aparece na listagem (código 29) com "-" em Fornecedor / Colaborador, sem mensagem de validação. |

**Impacto:** Pagamentos a colaboradores podem ser lançados sem favorecido, o que compromete a conciliação financeira e a rastreabilidade do pagamento.

### Evidências técnicas

- [Jam — Contas a Pagar](https://jam.dev/c/5d0afaf4-5abd-4e85-923f-27448304a9ef): quadro de 0:41 (formulário preenchido sem colaborador), `POST /api/cadastrar-conta-pagar/1` (HTTP 201) com `"tipo_conta": "PAG_COLABORADOR"` e `"colaborador_recebedor_id": ""`, e quadro de 0:50 com a conta 29 listada com "-" no colaborador.
- [Formulário em 0:41](Evidencias/CT-RF92_Cadastro_Conta_Colaborador_Sem_Colaborador/formulario_preenchido_00-41.png), [listagem em 0:50](Evidencias/CT-RF92_Cadastro_Conta_Colaborador_Sem_Colaborador/lista_apos_cadastro_00-50.png), [corpo da requisição](Evidencias/CT-RF92_Cadastro_Conta_Colaborador_Sem_Colaborador/requisicao_cadastrar.png) e [Evidências](Evidencias/CT-RF92_Cadastro_Conta_Colaborador_Sem_Colaborador/README.md).

### Análise, limites e encaminhamento

A gravação sem colaborador é compatível com ausência de validação no cliente e no servidor; o quadro consultado não indica obrigatoriedade no campo e a regra de negócio não foi informada. A causa técnica não foi confirmada no código.

**Reteste:** Confirmar a regra com o produto, reproduzir com a validação visível e testar também o tipo fornecedor sem fornecedor; retestar envio válido e inválido e a persistência. Manter em triagem até nova evidência em versão identificada.

---

<a id="bug-040"></a>

## BUG-040 — Listagem de modelos de contrato aparece vazia com 15 modelos retornados

| Campo | Descrição |
| --- | --- |
| Status | Em triagem — causa não determinada; reteste pendente após correção. |
| Severidade / prioridade | Alta / Alta, propostas para triagem. |
| Módulo | Modelos de Contrato / Listagem |
| Requisitos | [RF98](Analise%20de%20requisitos.md#rf98) |
| Casos | [CT-RF98](Cenario_Teste/CT-RF98_Listagem_Modelos_Contrato_Vazia.md) |
| Data da evidência / revisão | 15/11/2026, 21:55 BRT; sem nova execução. |
| Página | https://sifit.centrion.com.br/modelos-contrato |
| Ambiente | Chrome 157.0.8103.78 / Windows (x86) 11, janela 1920 × 855; versão e zoom não confirmados. |
| Frequência conhecida | Observado durante toda a gravação; recorrência não determinada. |

### Pré-condições e reprodução

**[CT-RF98](Cenario_Teste/CT-RF98_Listagem_Modelos_Contrato_Vazia.md):** Sessão autenticada com acesso a Modelos de Contrato e modelos existentes no servidor.

1. Acessar Modelos Contrato com o painel de rede aberto e registrar a resposta de `modelos-contrato`.
2. Conferir a tabela da tela com a resposta do servidor.
3. Cadastrar um modelo e voltar à listagem.
4. Recarregar a página e conferir novamente.

### Esperado e obtido

| Esperado | Obtido |
| --- | --- |
| A tabela apresenta uma linha com código, nome e status para cada modelo retornado pelo servidor, inclusive o recém-criado, ou mensagem explícita quando não houver modelos. | O servidor devolveu 15 modelos em `GET modelos-contrato/1`, mas a tabela apresentou apenas o cabeçalho (Código, Nome e Status), sem linhas e sem mensagem, antes e depois do cadastro. |

**Impacto:** O usuário não consegue consultar, editar ou excluir modelos de contrato pela tela e não sabe se o cadastro funcionou, podendo criar modelos duplicados.

### Evidências técnicas

- [Jam — Modelos de Contrato](https://jam.dev/c/44dbbd39-6915-45d6-8dd1-5f30c1432ca0): `GET /api/modelos-contrato/1` (HTTP 200, 1,0 KiB) com 15 modelos (ids 1 a 15, incluindo "teste eduardo") e quadros de 0:00, 0:39, 0:45 e 0:49 com a tabela sem linhas.
- [Tabela em 0:39](Evidencias/CT-RF98_Listagem_Modelos_Contrato_Vazia/lista_vazia_00-39.png), [tabela em 0:49](Evidencias/CT-RF98_Listagem_Modelos_Contrato_Vazia/lista_vazia_00-49.png), [resposta do servidor](Evidencias/CT-RF98_Listagem_Modelos_Contrato_Vazia/lista_servidor_resposta.png) e [Evidências](Evidencias/CT-RF98_Listagem_Modelos_Contrato_Vazia/README.md).

### Análise, limites e encaminhamento

A divergência entre a resposta e a tabela é compatível com falha na renderização, divergência no formato dos campos esperados pela tela ou filtro implícito; não foi possível distinguir. A causa técnica não foi confirmada no código.

**Reteste:** Reproduzir comparando a resposta de `modelos-contrato` com a tabela, investigar a renderização e o formato dos dados e retestar com e sem modelos. Manter em triagem até nova evidência em versão identificada.

---

<a id="bug-041"></a>

## BUG-041 — Cartão Ativos de Planos aumenta ao cadastrar e editar planos inativos

| Campo | Descrição |
| --- | --- |
| Status | Em triagem — causa não determinada; reteste pendente após correção. |
| Severidade / prioridade | Média / Média, propostas para triagem. |
| Módulo | Planos / Cartões de resumo |
| Requisitos | [RF102](Analise%20de%20requisitos.md#rf102) |
| Casos | [CT-RF102](Cenario_Teste/CT-RF102_Contador_Ativos_Planos.md) |
| Data da evidência / revisão | 15/11/2026, 21:54 BRT; sem nova execução. |
| Página | https://sifit.centrion.com.br/planos |
| Ambiente | Chrome 157.0.8103.78 / Windows (x86) 11, janela 1920 × 855; versão e zoom não confirmados. |
| Frequência conhecida | Duas operações consecutivas na mesma gravação; recorrência não determinada. |

### Pré-condições e reprodução

**[CT-RF102](Cenario_Teste/CT-RF102_Contador_Ativos_Planos.md):** Sessão autenticada com acesso a Planos e base de planos com a regra do cartão Ativos definida com o produto.

1. Acessar Planos e registrar os cartões Planos e Ativos.
2. Cadastrar um plano com status Inativo e conferir os cartões.
3. Editar o plano inativo sem alterar o status e conferir os cartões.
4. Comparar o cartão Ativos com a contagem de planos ativos da listagem.

### Esperado e obtido

| Esperado | Obtido |
| --- | --- |
| O cartão Ativos conta apenas planos com status ativo; cadastrar ou editar um plano inativo não o altera. | Cadastrar um plano com `status` "inativo" elevou Planos de 40 para 41 e Ativos de 29 para 30; editar o plano 41, que continuou "inativo", elevou Ativos para 31. |

**Impacto:** O indicador de planos ativos fica superestimado, o que distorce a leitura da carteira de planos e as decisões comerciais baseadas nele.

### Evidências técnicas

- [Jam — Planos](https://jam.dev/c/233c5d21-e108-4a55-b6f6-8738cb3fc6a6): quadros de 0:03 (Planos 40, Ativos 29), 0:53 (Planos 41, Ativos 30) e 1:08 (Planos 41, Ativos 31); `POST /api/plano/salvar/1` com `"status": "inativo"` e `POST /api/plano/update/1` com `"status": "inativo"`.
- [Cartões em 0:03](Evidencias/CT-RF102_Contador_Ativos_Planos/cartoes_antes_00-03.png), [em 0:53](Evidencias/CT-RF102_Contador_Ativos_Planos/cartoes_apos_cadastro_00-53.png), [em 1:08](Evidencias/CT-RF102_Contador_Ativos_Planos/cartoes_apos_edicao_01-08.png) e [Evidências](Evidencias/CT-RF102_Contador_Ativos_Planos/README.md).

### Análise, limites e encaminhamento

O aumento do cartão Ativos a cada operação com planos inativos é compatível com contagem que não considera o status ou com cálculo baseado em outro critério (por exemplo, planos com matrículas); a regra do cartão não foi informada e a contagem da listagem por status não foi conferida. A causa técnica não foi confirmada no código.

**Reteste:** Reproduzir com a base e o contrato do cartão conhecidos, comparando o cartão com a contagem por status da listagem, após cadastro, edição e alteração de status. Manter em triagem até nova evidência em versão identificada.

---

<a id="bug-042"></a>

## BUG-042 — Status do tipo de pagamento não é enviado nem refletido: todos aparecem Inativo

| Campo | Descrição |
| --- | --- |
| Status | Em triagem — causa não determinada; reteste pendente após correção. |
| Severidade / prioridade | Média / Média, propostas para triagem. |
| Módulo | Financeiro / Tipos de Pagamento / Cadastro e listagem |
| Requisitos | [RF105](Analise%20de%20requisitos.md#rf105) |
| Casos | [CT-RF105](Cenario_Teste/CT-RF105_Cadastro_Tipo_Pagamento_Status.md) |
| Data da evidência / revisão | 15/11/2026, 22:03 BRT; sem nova execução. |
| Página | https://sifit.centrion.com.br/tipos-pagamento |
| Ambiente | Chrome 157.0.8103.78 / Windows (x86) 11, janela 1920 × 855; versão e zoom não confirmados. |
| Frequência conhecida | Observado em todos os tipos listados, no cadastro e na edição da mesma gravação; recorrência não determinada. |

### Pré-condições e reprodução

**[CT-RF105](Cenario_Teste/CT-RF105_Cadastro_Tipo_Pagamento_Status.md):** Sessão autenticada com acesso a Tipos de Pagamento e regra do status do tipo definida com o produto.

1. Acessar Tipos de Pagamento e registrar a coluna Status e os cartões Total, Ativos e Inativos.
2. Acionar Novo, informar o nome, manter o Status Ativo e escolher Tipo, Escolher Bandeira e Pagamento Pelo Sistema.
3. Acionar Salvar e capturar o corpo e a resposta da criação e a resposta da lista.
4. Conferir a coluna Status do novo tipo e os cartões Ativos e Inativos.
5. Abrir um tipo existente pela lupa e comparar o Status do modal com o da listagem.

### Esperado e obtido

| Esperado | Obtido |
| --- | --- |
| O status escolhido no modal é enviado e gravado; a listagem exibe o status real de cada tipo e os cartões Ativos e Inativos acompanham o cadastro. | A criação retornou HTTP 201, mas o corpo enviado não traz status e os registros devolvidos pela API não têm esse campo; os cartões foram de Total 16 / Inativos 16 para Total 17 / Inativos 17, com Ativos em 0, e todos os tipos aparecem como Inativo. O modal de edição do tipo Dinheiro exibiu Status "Ativo" enquanto a listagem o exibia como Inativo. |

**Impacto:** O usuário não consegue ativar ou desativar tipos de pagamento nem confiar nos cartões e no filtro de status, e o seletor de Status do modal induz a erro por parecer gravar um valor que não é enviado.

### Evidências técnicas

- [Jam — Tipos de Pagamento](https://jam.dev/c/e8734e3d-3f8e-458b-8c7d-e85eea882e50): `POST /api/cria/tipo-pagamento/1` (HTTP 201) com `nome`, `tipo`, `via_gateway` e `escolher_bandeira`, sem status; `GET /api/tipo-pagamento/1` com registros sem campo de status; quadros de 0:00 (Total 16, Ativos 0, Inativos 16), 0:19 (Status Ativo no modal) e 0:27 (Total 17, Ativos 0, Inativos 17).
- [Cartões em 0:00](Evidencias/CT-RF105_Cadastro_Tipo_Pagamento_Status/cartoes_antes_00-00.jpg), [modal em 0:19](Evidencias/CT-RF105_Cadastro_Tipo_Pagamento_Status/modal_cadastro_00-19.jpg), [listagem em 0:27](Evidencias/CT-RF105_Cadastro_Tipo_Pagamento_Status/lista_apos_cadastro_00-27.jpg) e [Evidências](Evidencias/CT-RF105_Cadastro_Tipo_Pagamento_Status/README.md).

### Análise, limites e encaminhamento

O padrão é compatível com um campo de status que existe apenas na interface, sem coluna ou envio correspondente; também é compatível com uma regra em que o status é calculado de outra forma. A regra não foi informada, o novo tipo não está visível nos quadros e a causa técnica não foi confirmada no código.

**Reteste:** Confirmar com o produto se o tipo de pagamento tem status, reproduzir conferindo corpo, resposta e coluna Status e retestar cadastro e edição com Ativo e Inativo, o filtro de Status e os cartões. Manter em triagem até nova evidência em versão identificada.

---

<a id="bug-043"></a>

## BUG-043 — Exclusão de tipo de pagamento em uso retorna HTTP 404 com erro SQL e mensagem genérica

| Campo | Descrição |
| --- | --- |
| Status | Em triagem — causa não determinada; reteste pendente após correção. |
| Severidade / prioridade | Média / Média, propostas para triagem. |
| Módulo | Financeiro / Tipos de Pagamento / Exclusão |
| Requisitos | [RF107](Analise%20de%20requisitos.md#rf107) |
| Casos | [CT-RF107](Cenario_Teste/CT-RF107_Exclusao_Tipo_Pagamento_Em_Uso.md) |
| Data da evidência / revisão | 15/11/2026, 22:03 BRT; sem nova execução. |
| Página | https://sifit.centrion.com.br/tipos-pagamento |
| Ambiente | Chrome 157.0.8103.78 / Windows (x86) 11, janela 1920 × 855; versão e zoom não confirmados. |
| Frequência conhecida | Duas ocorrências consecutivas na mesma gravação (códigos 1 e 3); recorrência não determinada. |

### Pré-condições e reprodução

**[CT-RF107](Cenario_Teste/CT-RF107_Exclusao_Tipo_Pagamento_Em_Uso.md):** Sessão autenticada com acesso a Tipos de Pagamento e tipos de pagamento referenciados por contas a receber.

1. Acessar Tipos de Pagamento com o painel de rede aberto.
2. Acionar o ícone de exclusão da linha do tipo Dinheiro (código 1) e confirmar o diálogo.
3. Registrar o código HTTP, a resposta e a mensagem da tela.
4. Repetir com o tipo Cheque (código 3).
5. Repetir com um tipo sem uso e comparar.

### Esperado e obtido

| Esperado | Obtido |
| --- | --- |
| A exclusão de um tipo em uso é impedida com mensagem clara ao usuário, código HTTP compatível e resposta sem detalhes internos do banco. | Os dois `POST deleta/tipo-pagamento/1` (ids 1 e 3) retornaram HTTP 404 com `verifica_erro` true e o erro SQL completo (violação de chave estrangeira com `contas_receber`, nome do esquema e da restrição). A tela mostrou apenas "Erro / Erro ao deletar tipo de pagamento" e a listagem permaneceu com 17 tipos. |

**Impacto:** O usuário não sabe que o tipo está em uso e não recebe orientação para a ação seguinte; a resposta expõe nomes internos do banco a qualquer cliente que consulte a API, o que facilita o reconhecimento da estrutura; o código 404 induz a tratamento incorreto de erro.

### Evidências técnicas

- [Jam — Tipos de Pagamento](https://jam.dev/c/e8734e3d-3f8e-458b-8c7d-e85eea882e50): `POST /api/deleta/tipo-pagamento/1` (HTTP 404, 359 B) com `{"id": 1}` e `{"id": 3}`, resposta com `verifica_erro` true e texto de erro SQLSTATE 23000 / 1451 (violação de chave estrangeira com `contas_receber`); quadros de 0:37, 0:40 e 0:43.
- [Confirmação em 0:37](Evidencias/CT-RF107_Exclusao_Tipo_Pagamento_Em_Uso/dialogo_confirmar_00-37.jpg), [erro em 0:40](Evidencias/CT-RF107_Exclusao_Tipo_Pagamento_Em_Uso/erro_exclusao_00-40.jpg), [lista de rede](Evidencias/CT-RF107_Exclusao_Tipo_Pagamento_Em_Uso/rede_lista.jpg) e [Evidências](Evidencias/CT-RF107_Exclusao_Tipo_Pagamento_Em_Uso/README.md).

### Análise, limites e encaminhamento

O impedimento de excluir um tipo referenciado é compatível com a integridade referencial do banco; o defeito apontado é o tratamento do erro (código HTTP, mensagem ao usuário e conteúdo da resposta), e não o bloqueio em si. O comportamento para um tipo sem uso não foi exercitado e a causa técnica não foi confirmada no código.

**Reteste:** Reproduzir com tipo em uso e sem uso, conferindo código HTTP, corpo da resposta e mensagem da tela; verificar também se outras rotas de exclusão expõem erros SQL. Manter em triagem até nova evidência em versão identificada.

---

<a id="bug-044"></a>

## BUG-044 — Edição do tipo de resposta de pergunta de anamnese retorna HTTP 500

| Campo | Descrição |
| --- | --- |
| Status | Em triagem — causa não determinada; reteste pendente após correção. |
| Severidade / prioridade | Alta / Alta, propostas para triagem. |
| Módulo | Treinamento / Fichas de Anamnese / Perguntas Anamnese |
| Requisitos | [RF62](Analise%20de%20requisitos.md#rf62--editar-pergunta-de-anamnese-sem-erro-de-servidor) |
| Casos | [CT-RF62](Cenario_Teste/CT-RF62_Edicao_Pergunta_Anamnese.md) |
| Data da evidência / revisão | 16/11/2026, 15h57 BRT; sem nova execução. |
| Página | https://sifit.centrion.com.br/perguntas-anamnese |
| Ambiente | Chrome 157.0.8103.78 / Windows 11; versão e zoom não confirmados. |
| Frequência conhecida | Quatro tentativas consecutivas na mesma gravação, com valores de `resposta` e `status` diferentes; recorrência não determinada. |

### Pré-condições e reprodução

**[CT-RF62](Cenario_Teste/CT-RF62_Edicao_Pergunta_Anamnese.md):** Sessão autenticada com permissão para gerenciar perguntas de anamnese; pergunta cadastrada com um tipo de resposta.

1. Cadastrar uma nova pergunta de anamnese com um tipo de resposta (por exemplo, "2 opções com complemento").
2. Reabrir a pergunta pela ação de editar.
3. Alterar o tipo de resposta (ou o status) e acionar "Salvar".
4. Registrar o código HTTP e a resposta.
5. Repetir com outros valores de tipo de resposta e de status.

### Esperado e obtido

| Caso | Esperado | Obtido |
| --- | --- | --- |
| CT-RF62 | A edição do tipo de resposta ou do status de uma pergunta cadastrada é persistida e retorna sucesso. | As quatro tentativas registradas (`resposta: "3opcoes"` duas vezes, `"2opcoes"` com status INATIVO e depois ATIVO) retornam HTTP 500 com a mesma mensagem genérica; nenhuma alteração é persistida. |

**Impacto:** O usuário não consegue editar o tipo de resposta nem o status de uma pergunta de anamnese já cadastrada, em nenhuma das quatro tentativas registradas na gravação, com dois valores de tipo de resposta e os dois valores de status.

### Evidências

- [CT-RF62](Cenario_Teste/CT-RF62_Edicao_Pergunta_Anamnese.md): [Jam — Perguntas Anamnese](https://jam.dev/c/84b116fb-4640-4b1e-9148-9a169b8aa2b0). 1:00 e 1:04: `POST /api/pergunta-anamnese/alterar/1` com `{"id": 11, "nome": "Pergunta", "pergunta": "Pergunta isso", "resposta": "3opcoes", "numero": 12, "status": "INATIVO"}`, ambas HTTP 500. 1:08: mesmo endpoint com `"resposta": "2opcoes"`, status INATIVO, HTTP 500. 1:12: mesmo endpoint com `"resposta": "2opcoes"`, status ATIVO, HTTP 500. Todas as quatro respostas: `{"verifica_erro": true, "mensagem": "Erro interno inesperado."}` — mesmo padrão já observado nos BUG-016, BUG-024 e BUG-032.
- As quatro requisições de erro aparecem também na visão "Erros de rede" do painel Console do Jam, nos mesmos instantes.

### Análise, limites e encaminhamento

A falha ocorre de forma idêntica para dois valores diferentes de tipo de resposta (`"3opcoes"` e `"2opcoes"`) e para os dois valores de status, sempre com a mesma mensagem genérica — o mesmo padrão de resposta já registrado em [BUG-016](#bug-016), [BUG-024](#bug-024) e [BUG-032](#bug-032). A pergunta foi criada com o tipo de resposta `"2opcoes_complemento"`, o que sugere que a rotina de alteração pode estar falhando ao tentar ajustar ou remover as opções/complementos associados ao tipo anterior, mas essa hipótese não foi confirmada. Não houve acesso a logs do servidor, ao código da rotina nem ao banco de dados.

**Reteste:** Investigar a rotina de servidor acionada por `/api/pergunta-anamnese/alterar/{id}`, com acesso a logs, cobrindo especificamente a transição entre tipos de resposta com e sem complemento; confirmar também se o identificador final da URL corresponde ao `empresa_id`, como já hipotetizado em CT-RF59 a CT-RF61. Manter em triagem até nova evidência em versão identificada.

---

<a id="bug-045"></a>

## BUG-045 — Cadastro de modelo de ficha com nome e personal retorna HTTP 500

| Campo | Descrição |
| --- | --- |
| Status | Em triagem. Causa técnica a confirmar e reteste após correção. |
| Severidade / prioridade | Alta / Alta, propostas para triagem. |
| Módulo | Treinamento / Modelos de Ficha / Cadastro |
| Requisitos | [RF121](Analise%20de%20requisitos.md#rf121) |
| Casos | [CT-RF121](Cenario_Teste/CT-RF121_Cadastro_Modelo_Ficha_Erro_500.md) |
| Data da evidência / revisão | 16/11/2026, 22:18:52 BRT / 17/11/2026. |
| Página | https://sifit.centrion.com.br/fichas-treino-modelo |
| Ambiente | Chrome 157.0.8103.79 / Windows 10 (x86). Versão da aplicação e zoom a confirmar. |
| Frequência conhecida | Uma tentativa no Jam. Recorrência a verificar. |

### Pré-condições e reprodução

- Sessão autenticada com acesso a Modelos de Ficha, permissão para cadastrar e um personal disponível no formulário.

1. Abrir Modelos de Ficha e acionar o botão de adição.
2. Preencher o nome do modelo e selecionar um personal disponível.
3. Clicar em Criar Modelo e registrar o retorno da interface e da API.

### Esperado e obtido

**Esperado:** O cadastro é concluído com o personal selecionado, a interface confirma a criação e o novo modelo pode ser localizado após recarga.

**Obtido:** O envio com Pedro-01 e um personal selecionado produziu HTTP 500 em `POST /api/adicionar-ficha/1`. O servidor retornou `verifica_erro: true` e “Erro interno inesperado.” A interface exibiu “Erro ao salvar modelo.” e a gravação não mostrou confirmação de criação.

### Evidências técnicas

- 0:17,62  POST `/api/adicionar-ficha/1` (HTTP 500). O corpo registra `tipo_ficha: modelo`, `nome_ficha` e `nome_modelo` com Pedro-01 e `prescritor_id` preenchido.
- A resposta traz `verifica_erro: true` e `mensagem: "Erro interno inesperado."`.
- [Jam — PED-24 — Cadastro de modelo de ficha](https://jam.dev/c/04e2cae2-f3f2-43ff-8361-b3b9d9f50d35) e [Evidências](Evidencias/CT-RF121_Cadastro_Modelo_Ficha_Erro_500/README.md).

### Análise, limites e encaminhamento

A falha bloqueou o cadastro no fluxo gravado. Uma tentativa foi registrada. A gravação não confirma causa técnica, persistência parcial ou abrangência para outros nomes e personais. Os CT-RF109 e CT-RF110 cobrem, respectivamente, a validação de nome vazio e o cancelamento.

Reproduzir com dados de teste distintos, investigar a falha do endpoint e conferir a listagem e o vínculo após a correção. Para o reteste, registrar o retorno da criação e o modelo na listagem após recarga.

---

<a id="bug-046"></a>

## BUG-046 — Configurações de Biometria exibem senha sem mascaramento

| Campo | Descrição |
| --- | --- |
| Status | Em triagem. Causa técnica a confirmar e reteste após correção. |
| Severidade / prioridade | Alta / Alta, propostas para triagem. |
| Módulo | Configurações / Navegação e Biometria |
| Requisitos | [RF124](Analise%20de%20requisitos.md#rf124) |
| Casos | [CT-RF124](Cenario_Teste/CT-RF124_Configuracoes_Abas_Biometria_Senha.md) |
| Data da evidência / revisão | 16/11/2026, 21:57:29 BRT / 17/11/2026. |
| Página | https://sifit.centrion.com.br/configuracoes |
| Ambiente | Chrome 157.0.8103.79 / Windows 10 (x86). Versão da aplicação e zoom a confirmar. |
| Frequência conhecida | Uma ocorrência registrada. Recorrência a verificar. |

### Pré-condições e reprodução

- Sessão autenticada com acesso às Configurações. Ambiente de teste com integração de biometria configurada com credencial fictícia.

1. Abrir Configurações e registrar a aba Home.
2. Abrir Biometria e conferir o painel e o mascaramento do campo Senha com dados fictícios.
3. Visitar Avaliação, Aniversário, Pagamento, Integrações e Design.

### Esperado e obtido

**Esperado:** Todas as abas carregam o painel selecionado. O valor da senha configurada vem mascarado ao abrir Biometria.

**Obtido:** As abas percorridas carregaram seus painéis e foi possível retornar a Home. Ao abrir Biometria, o campo Senha exibiu o valor configurado em texto legível, sem ação para revelar a senha.

### Evidências técnicas

- 0:15,55  A abertura de Integrações gerou OPTIONS (HTTP 204) e a consulta do estado da integração retornou HTTP 200.
- O defeito de exibição foi observado na interface. A revisão não reproduz dados de integração.
- Jam — PED-15 (gravação restrita por conter dados de integração) e [Evidências](Evidencias/CT-RF124_Configuracoes_Abas_Biometria_Senha/README.md).

### Análise, limites e encaminhamento

O defeito foi observado na interface de uma sessão autenticada. O alcance por perfil, a exposição em respostas de API e a validade do valor exibido não foram testados. As evidências versionadas mostram apenas os cabeçalhos das abas.

Corrigir o mascaramento por padrão e retestar com credenciais fictícias, incluindo a troca de abas e a recarga.

---

<a id="bug-047"></a>

## BUG-047 — Configurações aceitam e persistem dias de ausência negativos

| Campo | Descrição |
| --- | --- |
| Status | Em triagem. Causa técnica a confirmar e reteste após correção. |
| Severidade / prioridade | Média / Média, propostas para triagem. |
| Módulo | Configurações / Home / Dias de ausência |
| Requisitos | [RF126](Analise%20de%20requisitos.md#rf126) |
| Casos | [CT-RF126](Cenario_Teste/CT-RF126_Configuracoes_Dias_Ausencia_Negativo.md) |
| Data da evidência / revisão | 16/11/2026, 22:00:22 BRT / 17/11/2026. |
| Página | https://sifit.centrion.com.br/configuracoes |
| Ambiente | Chrome 157.0.8103.79 / Windows 10 (x86). Versão da aplicação e zoom a confirmar. |
| Frequência conhecida | Uma ocorrência registrada. Recorrência a verificar. |

### Pré-condições e reprodução

- Sessão autenticada com acesso a Configurações > Home e valor inicial conhecido para dias de ausência.

1. Abrir Configurações > Home e registrar o valor original.
2. Preencher o campo com -1 e clicar em Salvar Configurações.
3. Conferir o feedback, a resposta e o valor após recarregar.

### Esperado e obtido

**Esperado:** O sistema rejeita valores negativos, orienta a correção do campo e preserva o valor anterior após recarga.

**Obtido:** O POST com `dias_ausente=-1` retornou HTTP 200 com `verifica_erro: false`. Após recarregar, o campo exibiu -1 e o GET confirmou `dias_ausente: -1`. No fim, 1100 foi reenviado com HTTP 200.

### Evidências técnicas

- 0:06,91  POST `/api/configuracoes/alterar/1` (HTTP 200), com `dias_ausente=-1` e `verifica_erro: false`.
- 0:10,44  GET `/api/configuracoes/1` (HTTP 200), com `dias_ausente: -1`.
- 0:23,65  POST (HTTP 200), com `dias_ausente=1100`. O vídeo termina antes de nova consulta para confirmar a restauração.
- [Jam — PED-17 — Dias de ausência negativos](https://jam.dev/c/d5786f67-6e5f-44f5-bbba-fbd763a88740) e [Evidências](Evidencias/CT-RF126_Configuracoes_Dias_Ausencia_Negativo/README.md).

### Análise, limites e encaminhamento

A evidência confirma a persistência de -1. O efeito sobre a classificação de clientes ausentes e a abrangência para outros negativos não foram exercitados.

Aplicar validação na gravação da configuração e retestar com -1, um inteiro válido e o limite mínimo definido pelo produto.

---

<a id="bug-048"></a>

## BUG-048 — Configuração de Aniversariantes exibe prévia de risco de evasão

| Campo | Descrição |
| --- | --- |
| Status | Em triagem. Causa técnica a confirmar e reteste após correção. |
| Severidade / prioridade | Média / Média, propostas para triagem. |
| Módulo | Inteligência e Automação / Central / Aniversariantes |
| Requisitos | [RF129](Analise%20de%20requisitos.md#rf129) |
| Casos | [CT-RF129](Cenario_Teste/CT-RF129_Central_Aniversariantes_Previa_Risco.md) |
| Data da evidência / revisão | 16/11/2026, 21:41:32 BRT / 17/11/2026. |
| Página | https://sifit.centrion.com.br/inteligencia-automacao |
| Ambiente | Chrome 157.0.8103.79 / Windows 10 (x86). Versão da aplicação e zoom a confirmar. |
| Frequência conhecida | Uma ocorrência registrada. Recorrência a verificar. |

### Pré-condições e reprodução

- Sessão autenticada com acesso à Central de Automações e cartão Aniversariantes disponível.

1. Na Central, localizar Aniversariantes e acionar Configurar.
2. Conferir o título, frequência, horário e canais exibidos.
3. Rolar até Preview do relatório e comparar o conteúdo com a automação selecionada.

### Esperado e obtido

**Esperado:** O painel de Aniversariantes abre e a prévia apresenta conteúdo de aniversários, coerente com a automação selecionada.

**Obtido:** O painel abriu com o título Aniversariantes, frequência diária e horário 08:00. A prévia exibiu um relatório com 24 alunos em risco, redução de frequência, pagamentos atrasados e falta de presença recente. Cancelar fechou o painel e o cartão continuou inativo.

### Evidências técnicas

- O Jam registrou Configurar às 0:03,41 e Cancelar às 0:18,18. Não houve requisições capturadas.
- [Jam — PED-07 — Configuração de Aniversariantes](https://jam.dev/c/c66d4d01-aee2-4037-a8fd-858da21a0a14) e [Evidências](Evidencias/CT-RF129_Central_Aniversariantes_Previa_Risco/README.md).

### Análise, limites e encaminhamento

A divergência foi observada na prévia do painel. O envio real, o conteúdo recebido e a persistência de alterações não foram exercitados.

Corrigir o conteúdo da prévia e retestar separadamente Aniversariantes e Risco de Evasão.

---

<a id="bug-049"></a>

## BUG-049 — Contador de automações ativas mantém total anterior após ativar automação

| Campo | Descrição |
| --- | --- |
| Status | Em triagem. Causa técnica a confirmar e reteste após correção. |
| Severidade / prioridade | Média / Média, propostas para triagem. |
| Módulo | Inteligência e Automação / Central de Automações |
| Requisitos | [RF135](Analise%20de%20requisitos.md#rf135) e [RF136](Analise%20de%20requisitos.md#rf136) |
| Casos | [CT-RF135](Cenario_Teste/CT-RF135_Central_Desativar_Risco_Evasao_Contador.md) e [CT-RF136](Cenario_Teste/CT-RF136_Central_Ativar_Aniversariantes_Contador.md) |
| Data da evidência / revisão | 16/11/2026, 21:28:33 e 21:31:02 BRT / 17/11/2026. |
| Página | https://sifit.centrion.com.br/inteligencia-automacao |
| Ambiente | Chrome 157.0.8103.79 / Windows 10 (x86). Versão da aplicação e zoom a confirmar. |
| Frequência conhecida | Duas ocorrências gravadas, uma por automação. |

### Pré-condições e reprodução

**CT-RF135**

- Sessão autenticada na Central, com Risco de Evasão como a única automação ativa no cenário de teste.

1. Registrar o estado inicial do cartão e o contador de automações ativas.
2. Desativar Risco de Evasão e aguardar a resposta do salvamento.
3. Acionar Atualizar e conferir a persistência do estado inativo.
4. Reativar a automação e comparar o cartão e o contador após o sucesso do salvamento.

**CT-RF136**

- Sessão autenticada na Central. Aniversariantes inativa e Risco de Evasão ativa na configuração de teste.

1. Registrar o estado de Aniversariantes e o total de automações ativas.
2. Ativar a automação. Conferir o retorno do salvamento, o cartão e o contador.
3. Acionar Atualizar e conferir a persistência na lista e no resumo.
4. Restaurar o estado inativo e registrar o contador final.

### Esperado e obtido

**Esperado:** Após ativar e salvar com sucesso, o contador no resumo deve refletir o total de cartões ativos sem exigir Atualizar.

**Obtido (CT-RF135):** A desativação foi salva com HTTP 200. Após Atualizar, a lista confirmou `ativo: 0` e o contador marcou zero. A reativação também retornou sucesso e o cartão voltou a indicar o estado ativo, mas o resumo retornou `ativas: 0`. O contador permaneceu em zero no restante da gravação.

**Obtido (CT-RF136):** O POST de ativação retornou sucesso e o cartão passou a indicar o estado ativo, mas o resumo ainda retornou `ativas: 1`. O contador chegou a dois quando o usuário acionou Atualizar, e a listagem confirmou Aniversariantes com `ativo: 1`. Em seguida, a desativação de restauração retornou sucesso e o contador voltou a um.

### Evidências técnicas

[CT-RF135](Cenario_Teste/CT-RF135_Central_Desativar_Risco_Evasao_Contador.md)

- 0:05,41  POST `/api/automacoes/salvar/1` (HTTP 200), com `tipo: risco_evasao`, `ativo: 0` e `verifica_erro: false` na resposta. O GET de resumo retornou `ativas: 0`.
- 0:09,30  Atualizar. GET `/api/automacoes/1` com `ativo: 0` para Risco de Evasão e GET de resumo com `ativas: 0` (HTTP 200).
- 0:12,74  POST com `ativo: 1` (HTTP 200, `verifica_erro: false`). O GET de resumo associado retornou `ativas: 0`.
- [Jam — PED-02 — Desativar Risco de Evasão](https://jam.dev/c/b63ec55f-f8b6-41aa-af4c-d4cdd4515de8) e [Evidências](Evidencias/CT-RF135_Central_Desativar_Risco_Evasao_Contador/README.md).

[CT-RF136](Cenario_Teste/CT-RF136_Central_Ativar_Aniversariantes_Contador.md)

- 0:04,54  POST `/api/automacoes/salvar/1` (HTTP 200), com `tipo: aniversario`, `ativo: 1` e `verifica_erro: false` na resposta. O GET de resumo retornou `ativas: 1`.
- 0:09,31  Atualizar. GET `/api/automacoes/1` confirmou `ativo: 1` para Aniversariantes e o GET de resumo retornou `ativas: 2` (HTTP 200).
- 0:13,29  POST de restauração com `ativo: 0` (HTTP 200, `verifica_erro: false`), seguido de resumo com `ativas: 1`.
- [Jam — PED-03 — Ativar Aniversariantes](https://jam.dev/c/60c724da-6760-4238-91f5-2ddad8f42bb3) e [Evidências](Evidencias/CT-RF136_Central_Ativar_Aniversariantes_Contador/README.md).

### Análise, limites e encaminhamento

A divergência aparece no contador do resumo após a ativação. A causa técnica precisa ser investigada.

**Limites (CT-RF135):** A persistência foi confirmada por nova leitura para a desativação. Após a reativação, a gravação não contém outro clique em Atualizar. A ordem em que o servidor processou o salvamento e o resumo não foi determinada.

**Limites (CT-RF136):** O estado ativo persistiu após Atualizar. A divergência observada ocorreu entre o cartão e o resumo depois do salvamento da ativação. A gravação não confirma a causa no servidor.

Retestar a ativação e a desativação de cada automação. Comparar o valor de `ativas` no GET de resumo com os cartões e a lista após cada salvamento e após Atualizar.

---

<a id="bug-050"></a>

## BUG-050 — API de conexão do WhatsApp indica sucesso quando a tentativa falha

| Campo | Descrição |
| --- | --- |
| Status | Em triagem. Contrato da resposta a confirmar e reteste após correção. |
| Severidade / prioridade | Média / Média, propostas para triagem. |
| Módulo | Configurações / Integrações / WhatsApp |
| Requisito | [RF143](Analise%20de%20requisitos.md#rf143) |
| Caso reprovado | [CT-RF143](Cenario_Teste/CT-RF143_Integracoes_WhatsApp_Conectar_Evolution.md) |
| Data da evidência / revisão | 16/11/2026, 23:44:10 BRT / 17/11/2026. |
| Página | https://sifit.centrion.com.br/configuracoes |
| Ambiente | Chrome 157.0.8103.79 / Windows 10 (x86). Versão da aplicação e zoom a confirmar. |
| Frequência conhecida | Três tentativas em duas gravações. |

### Pré-condições e reprodução

Sessão autenticada na integração de WhatsApp com um provedor de teste. Preparar uma falha controlada com a equipe responsável pelo ambiente.

1. Abrir Configurações → Integrações → WhatsApp com um provedor de teste.
2. Em ambiente autorizado, preparar uma resposta de falha controlada do provedor.
3. Acionar Conectar WhatsApp e registrar a mensagem, a flag de erro e a indicação de conexão.
4. Repetir a tentativa após salvar a opção Ativo e comparar os resultados.

### Esperado e obtido

**Esperado:** Se a tentativa falhar, os indicadores e a mensagem da API representam a falha. A interface informa o erro sem apresentar um QR Code utilizável nem indicar uma conexão estabelecida.

**Obtido:** A tela exibiu “Falha ao conectar na Evolution API” nas duas tentativas e não apresentou QR Code utilizável. Em ambas, o POST retornou HTTP 200 com `verifica_erro: false`, `status: conectando` e `conectado: false`. A resposta continha a mensagem de falha, em desacordo com a flag `verifica_erro`.

### Evidências técnicas

- 0:02,48 e 0:12,94  POST `/api/empresa/whatsapp/conectar/1` (HTTP 200). As duas respostas indicaram falha na mensagem com `verifica_erro: false`, `status: conectando` e `conectado: false`.
- 0:08,59–0:08,72  O POST de configuração confirmou o salvamento de Ativo. O GET trouxe `ativo: true` e `status: desconectado` antes da segunda tentativa.
- Jam 5 — Tentativas de conexão pela Evolution API (gravação restrita por conter dados de integração) e [Evidências](Evidencias/CT-RF143_Integracoes_WhatsApp_Conectar_Evolution/README.md).
- [CT-RF144](Cenario_Teste/CT-RF144_Integracoes_WhatsApp_Atualizar_Status.md), evidência complementar de conexão após as consultas de status. 0:14,84  POST `/api/empresa/whatsapp/conectar/1` (HTTP 200), com mensagem “Erro ao conectar” e `verifica_erro: false`. Esse evento pertence à ação de conexão. [Evidências](Evidencias/CT-RF144_Integracoes_WhatsApp_Atualizar_Status/README.md).

### Análise, impacto e encaminhamento

A flag `verifica_erro: false` pode levar consumidores da resposta a interpretar a tentativa como bem-sucedida. Confirmar a semântica do campo e do status intermediário com a equipe responsável. Os parâmetros do provedor não foram validados. A causa da falha de conexão e o caminho de sucesso exigem testes controlados. O defeito registrado é a divergência da flag de erro.

Retestar com falha controlada e configuração válida de controle, conferindo o contrato da resposta e o estado final apresentado.

---

<a id="bug-051"></a>

## BUG-051 — Configurações persiste código inválido na Cor Secundária

| Campo | Descrição |
| --- | --- |
| Status | Em triagem. Reteste após correção. |
| Severidade / prioridade | Média / Média, propostas para triagem. |
| Módulo | Configurações / Design |
| Requisito | [RF148](Analise%20de%20requisitos.md#rf148) |
| Caso reprovado | [CT-RF148](Cenario_Teste/CT-RF148_Configuracoes_Design_Validar_Cor_Secundaria.md) |
| Data da evidência / revisão | 16/11/2026, 23:26:21 BRT / 17/11/2026. |
| Página | https://sifit.centrion.com.br/configuracoes |
| Ambiente | Chrome 157.0.8103.79 / Windows 10 (x86). Versão da aplicação e zoom a confirmar. |
| Frequência conhecida | Duas tentativas de salvamento na mesma gravação e uma leitura posterior. |

### Pré-condições e reprodução

Sessão autenticada em Design e uma Cor Secundária válida salva como referência.

1. Abrir Design e registrar a Cor Secundária salva.
2. Trocar a Cor Secundária para #ZZZZZZ e salvar.
3. Conferir a resposta, recarregar e reabrir Design.

### Esperado e obtido

**Esperado:** A interface ou a API rejeita o código #ZZZZZZ com uma mensagem de validação e preserva a cor válida armazenada.

**Obtido:** As duas tentativas retornaram HTTP 200 com `verifica_erro: false`. O GET após recarregar devolveu `cor_secundaria: #ZZZZZZ` e o campo ainda mostrou esse valor ao reabrir a aba. Não houve indicação de rejeição na gravação. Ao reabrir, a amostra da Cor Secundária ficou sem a cor preta original.

### Evidências técnicas

- 0:08,01 e 0:09,20  POST `/api/configuracoes/alterar/1` com `cor_secundaria: #ZZZZZZ` (HTTP 200, `verifica_erro: false`).
- 0:12,33  GET `/api/configuracoes/1` (HTTP 200), com `cor_secundaria: #ZZZZZZ`.
- Jam 4 — Validação da Cor Secundária (gravação restrita por conter dados de integração) e [Evidências](Evidencias/CT-RF148_Configuracoes_Design_Validar_Cor_Secundaria/README.md).

### Análise, impacto e encaminhamento

O valor inválido substitui a configuração anterior e pode impedir a aplicação da cor secundária nos ambientes que a usam. O defeito foi confirmado pela leitura posterior. O efeito do código inválido nos ambientes online não foi avaliado.

Retestar com códigos hexadecimais válidos e inválidos e conferir, após cada tentativa, a cor devolvida pela consulta.

---

<a id="bug-052"></a>

## BUG-052 — Design omite o limite de 6 MB ao rejeitar o salvamento do logo

| Campo | Descrição |
| --- | --- |
| Status | Em triagem. Reteste após correção. |
| Severidade / prioridade | Baixa / Baixa, propostas para triagem. |
| Módulo | Configurações / Design |
| Requisito | [RF149](Analise%20de%20requisitos.md#rf149) |
| Caso reprovado | [CT-RF149](Cenario_Teste/CT-RF149_Configuracoes_Design_Logo_Limite_Tamanho.md) |
| Data da evidência / revisão | 16/11/2026, 23:27:58 BRT / 17/11/2026. |
| Página | https://sifit.centrion.com.br/configuracoes |
| Ambiente | Chrome 157.0.8103.79 / Windows 10 (x86). Versão da aplicação e zoom a confirmar. |
| Frequência conhecida | Uma tentativa na gravação. |

### Pré-condições e reprodução

Sessão autenticada com acesso a Design. Preparar arquivos de teste dos formatos aceitos, com tamanhos medidos abaixo e acima de 6 MB.

1. Abrir Design e registrar o logo salvo.
2. Selecionar um JPG ou PNG de teste com tamanho medido acima de 6 MB.
3. Acionar Salvar Configurações e comparar o texto da tela com o motivo da API.

### Esperado e obtido

**Esperado:** Ao rejeitar um logo pelo tamanho, o sistema informa na tela o limite de 6 MB e permite que o usuário substitua o arquivo.

**Obtido:** A imagem selecionada apareceu na prévia. No salvamento, a API retornou HTTP 400 com “O arquivo deve ter no máximo 6 MB.” O diálogo mostrou apenas “Erro ao salvar configurações”. A prévia permaneceu na tela após fechar o diálogo.

### Evidências técnicas

- 0:09,40  POST `/api/configuracoes/alterar/1` em multipart, corpo de 10.081.448 bytes conforme o Jam. HTTP 400 com “O arquivo deve ter no máximo 6 MB.”
- Jam 5 — Rejeição de logo pelo limite de tamanho (gravação restrita por conter dados de integração) e [Evidências](Evidencias/CT-RF149_Configuracoes_Design_Logo_Limite_Tamanho/README.md).

### Análise, impacto e encaminhamento

A mensagem genérica dificulta a correção do arquivo, embora a API já identifique o limite. O total em bytes corresponde à requisição inteira. O tamanho exato do arquivo e o logo armazenado após recarregar não ficaram demonstrados.

Retestar com arquivos de tamanho conhecido no entorno do limite e confirmar a mensagem de validação e a preservação do logo salvo na recusa.

---

## Modelos de Ficha — revisão de 17/11/2026

A revisão de Modelos de Ficha inclui CT-RF109–CT-RF115 com base em 6 gravações do Jam de 16/11/2026. A revisão documental foi feita em 17/11/2026. A triagem documental de [CT-RF109](Cenario_Teste/CT-RF109_Modelo_Ficha_Sem_Nome.md), [CT-RF110](Cenario_Teste/CT-RF110_Cancelar_Cadastro_Modelo_Ficha.md), [CT-RF111](Cenario_Teste/CT-RF111_Busca_Modelo_Ficha_Codigo_Inexistente.md), [CT-RF112](Cenario_Teste/CT-RF112_Busca_Modelo_Ficha_Titulo_Inexistente.md), [CT-RF113](Cenario_Teste/CT-RF113_Busca_Modelo_Ficha_Filtros_Combinados.md), [CT-RF114](Cenario_Teste/CT-RF114_Limpeza_Filtros_Modelos_Ficha.md), [CT-RF115](Cenario_Teste/CT-RF115_Nova_Busca_Modelos_Ficha_Sem_Filtros.md) registrou 4 caso(s) de Modelos de Ficha a validar e zero novos defeitos confirmados.

## Configurações e Modelos de Ficha — revisão de 17/11/2026 (CT-RF116–CT-RF121)

CT-RF116–CT-RF121 amplia a cobertura de Configurações e Modelos de Ficha com gravações de 16/11/2026 entre 22:03:53 e 22:18:52 BRT. Casos aprovados: 4. Reprovados: 1. A validar: 1. A falha de cadastro está em [BUG-045](#bug-045).

## Inteligência e Configurações — revisão de 17/11/2026 (CT-RF122–CT-RF127)

CT-RF122–CT-RF127 cobre Inteligência e Configurações com gravações de 16/11/2026 entre 21:50:51 e 22:02:16 BRT. Casos aprovados: 3. Reprovados: 2. A validar: 1. Defeitos do lote: [BUG-046](#bug-046) e [BUG-047](#bug-047).

## Inteligência e Automação — revisão de 17/11/2026 (CT-RF128–CT-RF133)

CT-RF128–CT-RF133 cobre Inteligência e Automação com gravações de 16/11/2026 entre 21:40:31 e 21:49:48 BRT. Casos aprovados: 5. Reprovados: 1. A validar: 0. Defeitos do lote: [BUG-048](#bug-048).

## Inteligência e Automação / Central de Automações — revisão de 17/11/2026 (CT-RF134–CT-RF138)

CT-RF134–CT-RF138 cobrem a Central de Automações com gravações de 16/11/2026 entre 21:25:26 e 21:38:29 BRT. Casos aprovados: 3. Reprovados: 2. A validar: 0. Defeitos do lote: [BUG-049](#bug-049).

## Configurações / Integrações / WhatsApp — revisão de 17/11/2026 (CT-RF139–CT-RF144)

CT-RF139–CT-RF144 cobrem a integração do WhatsApp com gravações de 16/11/2026 entre 23:37:22 e 23:45:52 BRT. Casos aprovados: 4. Reprovados: 1. A validar: 1. Defeitos do lote: [BUG-050](#bug-050).

## Configurações — revisão de 17/11/2026 (CT-RF145–CT-RF150)

CT-RF145–CT-RF150 cobrem funcionalidades de Configurações com gravações de 16/11/2026 entre 23:21:59 e 23:36:13 BRT. Casos aprovados: 4. Reprovados: 2. A validar: 0. Defeitos do lote: [BUG-051](#bug-051) e [BUG-052](#bug-052).

## Configurações / Avaliação e Aniversário — revisão de 18/11/2026 (CT-RF151–CT-RF156)

CT-RF151–CT-RF156 cobrem as abas Avaliação e Aniversário com gravações de 16/11/2026 entre 23:10:04 e 23:20:07 BRT. Casos aprovados: 6. Reprovados: 0. A validar: 0. Nenhum defeito identificado nos fluxos gravados.

## Aplicativo e Configurações / Biometria — revisão de 18/11/2026 (CT-RF157–CT-RF162)

CT-RF157–CT-RF162 cobrem Aplicativo e a aba Biometria com gravações de 16/11/2026 entre 22:39:05 e 23:02:14 BRT. Casos aprovados: 6. Reprovados: 0. A validar: 0.

## Pontos a validar — sem defeito confirmado

| Caso | Questão pendente | Evidência |
| --- | --- | --- |
| [CT-RF08](Cenario_Teste/CT-RF08_Calculo_Cobranca.md) | Confirmar a origem dos R$ 20,83 além de principal e multa e a regra da mensagem; não registrar cálculo incorreto antes dessa validação. | [Jam](https://jam.dev/c/79b712ae-d9e0-4600-862f-fd3a278285ff) e [Evidências](Evidencias/CT-RF08_Calculo_Cobranca/README.md) |
| [CT-RF11](Cenario_Teste/CT-RF11_Metricas_Financeiro.md) | Confirmar os contratos dos cartões; a constância de totais globais não é suficiente para abrir outro defeito financeiro. | [Jam](https://jam.dev/c/4491c9e7-7e00-4063-91ce-8683e316df06) e [Evidências](Evidencias/CT-RF11_Metricas_Financeiro/README.md) |
| [CT-RF13](Cenario_Teste/CT-RF13_Codigos_Personais.md) | Confirmar a semântica da coluna Código; quatro linhas e total quatro não sustentam um defeito de quantidade. | [Jam](https://jam.dev/c/69330ca9-ef19-4ece-918f-31a460628016) e [Evidências](Evidencias/CT-RF13_Codigos_Personais/README.md) |
| [CT-RF16](Cenario_Teste/CT-RF16_Exclusao_Modalidade.md) | Confirmar a exclusão lógica e a nomenclatura da ação; registrar defeito apenas se houver divergência com a regra definida. | [Jam](https://jam.dev/c/0f55f76a-cd31-4cee-93da-23c13b1ba637) e [Evidências](Evidencias/CT-RF16_Exclusao_Modalidade/README.md) |
| [CT-RF25](Cenario_Teste/CT-RF25_Envio_Exercicio_Imagem.md) | Conferir a imagem após reabrir e recarregar o exercício; criação visível não comprova associação persistida. | [Jam](https://jam.dev/c/25c37a9b-e9bd-4e0c-adf1-4da528ae1d58) e [Evidências](Evidencias/CT-RF25_Envio_Exercicio_Imagem/README.md) |
| [CT-RF40](Cenario_Teste/CT-RF40_Exclusao_Turmas_Modalidades.md) | Confirmar a exclusão lógica de turmas e modalidades, a ausência de confirmação prévia e a exibição de registros inativos sob o filtro "Ativo"; registrar defeito apenas se houver divergência com a regra definida. | [Jam](https://jam.dev/c/ee9a133b-d6b1-442d-b4b0-dd87595b7e70) e [Evidências](Evidencias/CT-RF40_Exclusao_Turmas_Modalidades/README.md) |
| [CT-RF42](Cenario_Teste/CT-RF42_Solicitacao_Saque_PagarMe.md) | Confirmar a regra de saque com saldo indisponível e capturar corpo e resposta; o envio retorna HTTP 200 sem mensagem de resultado visível. | [Jam](https://jam.dev/c/e6e551ef-9196-4c79-b6a2-89747b1e8b33) e [Evidências](Evidencias/CT-RF42_Solicitacao_Saque_PagarMe/README.md) |
| [CT-RF44](Cenario_Teste/CT-RF44_Configuracoes_Home_Salvamento.md) | Confirmar a faixa do campo "Dias para contar cliente como ausente" (valor inicial -120 e valor informado 1100) e a mensagem de salvamento esperada. | [Jam](https://jam.dev/c/e6e551ef-9196-4c79-b6a2-89747b1e8b33) e [Evidências](Evidencias/CT-RF44_Configuracoes_Home_Salvamento/README.md) |
| [CT-RF47](Cenario_Teste/CT-RF47_Cadastro_Despesa_Fixa.md) | Confirmar se o segundo POST de criação (HTTP 201) gerou registro adicional ou foi descartado; registrar defeito apenas se houver duplicidade confirmada. | [Jam](https://jam.dev/c/a4bac99d-e436-4792-831e-8c3a875272bb) e [Evidências](Evidencias/CT-RF47_Cadastro_Despesa_Fixa/README.md) |
| [CT-RF52](Cenario_Teste/CT-RF52_Relatorio_Contas_Pagar_Pagas.md) | Conferir se existem contas pagas no período; PDF sem linhas e com totalizadores R$ 0,00 é compatível com período sem pagamentos. | [Jam](https://jam.dev/c/3b4777a4-e1b0-4038-9b06-26c73669d7d1) e [Evidências](Evidencias/CT-RF52_Relatorio_Contas_Pagar_Pagas/README.md) |
| [CT-RF88](Cenario_Teste/CT-RF88_Cadastro_Lead_Prospeccao.md) | Cadastro de lead com duas requisições de criação | Confirmar se o segundo POST de criação gerou registro adicional ou foi descartado; registrar defeito apenas se houver duplicidade confirmada. | [Jam](https://jam.dev/c/308607ff-8abc-40af-8c7c-429ce506ed64) e [Evidências](Evidencias/CT-RF88_Cadastro_Lead_Prospeccao/README.md) |
| [CT-RF91](Cenario_Teste/CT-RF91_Filtros_Contas_Pagar.md) | Filtros da tela Contas a Pagar por nome, data e status | Reexecutar com contas de controle e conferir cada critério isolado e combinado; o resultado vazio da combinação gravada não pôde ser conferido contra a base. | [Jam](https://jam.dev/c/5d0afaf4-5abd-4e85-923f-27448304a9ef) e [Evidências](Evidencias/CT-RF91_Filtros_Contas_Pagar/README.md) |
| [CT-RF93](Cenario_Teste/CT-RF93_Busca_Colaborador_Conta_Pagar.md) | Busca de colaborador no cadastro de conta a pagar | Reexecutar com um nome existente para conferir listagem e seleção e confirmar a mensagem esperada de resultado vazio. | [Jam](https://jam.dev/c/5d0afaf4-5abd-4e85-923f-27448304a9ef) e [Evidências](Evidencias/CT-RF93_Busca_Colaborador_Conta_Pagar/README.md) |
| [CT-RF104](Cenario_Teste/CT-RF104_Filtros_Tipos_Pagamento.md) | Filtros de busca da tela Tipos de Pagamento | Reexecutar com critérios conhecidos, registrando o valor escolhido em cada seletor, a listagem e a rede, e confirmar se a filtragem é local ou no servidor; Buscar não emitiu requisição de listagem. | [Jam](https://jam.dev/c/e8734e3d-3f8e-458b-8c7d-e85eea882e50) e [Evidências](Evidencias/CT-RF104_Filtros_Tipos_Pagamento/README.md) |
| [CT-RF111](Cenario_Teste/CT-RF111_Busca_Modelo_Ficha_Codigo_Inexistente.md) | Reexecutar com um código existente e um comprovadamente ausente na mesma base. O estado vazio foi observado. A base de controle e a busca positiva não aparecem na gravação, por isso a eficácia do filtro por código permanece a validar. | [Jam — PED-27](https://jam.dev/c/c1aecaa8-39c7-49b0-89af-9de47a68ba40) e [Evidências](Evidencias/CT-RF111_Busca_Modelo_Ficha_Codigo_Inexistente/README.md) |
| [CT-RF112](Cenario_Teste/CT-RF112_Busca_Modelo_Ficha_Titulo_Inexistente.md) | Reexecutar com título existente e inexistente e confirmar o critério de correspondência com o produto. A gravação começa com a listagem vazia. O comportamento com títulos registrados e o tipo de correspondência (exata ou parcial) precisam de confirmação. | [Jam — PED-28](https://jam.dev/c/0c385452-2aeb-427f-8159-79549fe7371d) e [Evidências](Evidencias/CT-RF112_Busca_Modelo_Ficha_Titulo_Inexistente/README.md) |
| [CT-RF113](Cenario_Teste/CT-RF113_Busca_Modelo_Ficha_Filtros_Combinados.md) | Reexecutar com registros que correspondam a todos os filtros e a apenas parte deles. Confirmar onde a filtragem é feita. A resposta vazia e a ausência de parâmetros na URL não permitem distinguir filtragem local de critérios ignorados. Confirmar a lógica de combinação com o produto e usar dados que diferenciem os resultados. | [Jam — PED-29](https://jam.dev/c/006f9722-e643-4b65-904a-25471a7b90ed) e [Evidências](Evidencias/CT-RF113_Busca_Modelo_Ficha_Filtros_Combinados/README.md) |
| [CT-RF115](Cenario_Teste/CT-RF115_Nova_Busca_Modelos_Ficha_Sem_Filtros.md) | Reexecutar com listagem padrão populada, pesquisa restritiva e comparação dos registros após a nova busca. A gravação não mostra uma listagem padrão populada. O estado vazio é compatível com os retornos, mas a recuperação de registros ocultados por uma pesquisa anterior ficou a validar. | [Jam — PED-30](https://jam.dev/c/297eec2b-7be4-498b-a0e6-e962ed93cc00) e [Evidências](Evidencias/CT-RF115_Nova_Busca_Modelos_Ficha_Sem_Filtros/README.md) |
| [CT-RF116](Cenario_Teste/CT-RF116_Configuracoes_Dias_Ausencia_Vazio.md) | Confirmar com o produto a regra para vazio e zero. Repetir com vazio, zero explícito e os limites da faixa. A conversão de vazio para zero e a persistência estão confirmadas. A obrigatoriedade do campo, o significado de zero e o efeito sobre a contagem de clientes ausentes dependem da regra de produto. O CT-RF44 já registra a necessidade de confirmar a faixa. | [Jam — PED-20 — Dias de ausência vazio](https://jam.dev/c/4e96d4fa-65b5-459b-a795-854496e5753c) e [Evidências](Evidencias/CT-RF116_Configuracoes_Dias_Ausencia_Vazio/README.md) |
| [CT-RF140](Cenario_Teste/CT-RF140_Integracoes_WhatsApp_Validar_URL_API.md) | Isolar a URL no reteste, mantendo a instância e a chave preenchidas, e confirmar o formato aceito com produto. O Nome da Instância vazio impede atribuir a ausência de POST à regra de URL. A gravação não demonstra qual validação bloqueou a tentativa. | Jam 2 — Validação da URL da API (gravação restrita por conter dados de integração) e [Evidências](Evidencias/CT-RF140_Integracoes_WhatsApp_Validar_URL_API/README.md) |
| [CT-RF127](Cenario_Teste/CT-RF127_Configuracoes_Dias_Ausencia_Texto.md) | Confirmar a regra de vazio com o produto e repetir a digitação e a colagem de texto, conferindo também a recarga. A rejeição da digitação de letras foi observada. A regra para o campo vazio permanece pendente no CT-RF116. A persistência de zero nesta gravação não foi verificada após recarga. | [Jam — PED-18 — Dias de ausência com texto](https://jam.dev/c/c578ed7a-c11c-4cef-8a6c-84d0244f21a5) e [Evidências](Evidencias/CT-RF127_Configuracoes_Dias_Ausencia_Texto/README.md) |

A contagem de 52 defeitos registrados considera os itens do resumo de bugs. BUG-011–BUG-052 estão em triagem. Os pontos desta tabela aguardam confirmação antes de receber um registro de defeito.


**Exclusão de exercício:** CT-RF23 está aprovado no trecho consultado, com remoção e total 11 para 10; não gerou defeito adicional. Persistência e efeitos sobre vínculos permanecem como verificações complementares.

---

[← Início](../README.md) · [Cenários de teste](Cenario_Teste/) · [Evidências de Clientes](Evidencias/CT-RF03_Filtros_Clientes/README.md)
