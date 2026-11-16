# 🧪 Plano de Testes — SIFIT

**Atualização:** 16/11/2026 — 64 cenários documentados (CT-RF01–CT-RF35, CT-RF38–CT-RF59, CT-RF60 e CT-RF65–CT-RF70), com inclusão de CT-RF42 a CT-RF56 / Pagar.me, Configurações, Despesas Fixas e Relatórios, CT-RF57 e CT-RF58 / Grupos (treino), CT-RF59 / Fichas de Anamnese, CT-RF60 / Modelos de Anamnese e CT-RF65 a CT-RF70 / Colaboradores; BUG-011–BUG-032 em triagem.

**Padronização documental:** 13/11/2026, com resultados e pendências preservados.

**Escopo:** 64 casos (CT-RF01–CT-RF35, CT-RF38–CT-RF59, CT-RF60 e CT-RF65–CT-RF70) — autenticação, recuperação de senha, perfil, Clientes, financeiro, página inicial e dashboard, modalidades / tema de SifitBox, Categorias Crossfit, Avaliações, Exercícios, Grupos Musculares, Objetivos de Treino, Grupos (treino), Fichas de Anamnese, gestão de Modelos de Anamnese e validações, funções e exclusão de Colaboradores.

## 📌 1. Identificação

| Item | Definição |
| --- | --- |
| Projeto | SIFIT — Sistema de gestão de academias. |
| Tipo de teste | Funcional manual, com análise exploratória e de evidências. |
| Versão avaliada | Não confirmada; registrar por caso no reteste. |
| Funcionalidades | Autenticação positiva e negativa, recuperação, Perfil, filtros de Clientes, financeiro, período, personais, modalidades / tema, Categorias Crossfit, Avaliações e Exercícios. |
| Situação | 62 casos documentados: 17 aprovados, 35 reprovados e 10 a validar; 31 defeitos registrados (10 abertos e 21 em triagem) e 35 casos com reteste corretivo pendente. |

---

## 🎯 2. Objetivo

Verificar os fluxos dos 54 cenários documentados, comparando os critérios de aceitação com as evidências de autenticação, recuperação, perfil, Clientes, financeiro, página inicial, SifitBox, Categorias Crossfit, Avaliações, Exercícios e Grupos Musculares. Manter rastreabilidade entre requisitos, casos, Jam, vídeos, resultados e defeitos, distinguindo revisões documentais de novas execuções.

---

## 🧩 3. Escopo

**Incluído:**

- Login com credenciais válidas, senha mascarada, envio por Entrar, navegação para `/dashboard` e apresentação do menu e resumo da academia.
- Disponibilidade da opção na tela de login, antes da autenticação.
- Abertura do formulário ou da página de recuperação após o clique.
- Observação da interface, das requisições de rede e dos erros de console.
- Registro e reteste do BUG-001 após disponibilização da correção.
- Carregamento dos dados, renderização dos campos, idioma, dimensionamento das imagens e navegação na tela de Perfil.
- Registro e reteste do BUG-002 após disponibilização da correção, incluindo análise do DOM e comparação com os dados da conta de teste.
- Pesquisa por Código, Nome, Status, Situação Financeira, Plano e Personal, com lógica AND, alteração e remoção de restrições e estado sem resultados.
- Registro e reteste do BUG-003, com conferência da inclusão e exclusão de clientes em uma base conhecida e da integração conforme a arquitetura efetiva.

**Ampliação de escopo em 14/11/2026:**

- CT-RF05–06: recusa de senha incorreta e de usuário declarado inexistente.
- CT-RF07–11: retorno de exportação, composição da cobrança, contagens, filtro de mensalidades e escopo dos indicadores.
- CT-RF12–13: validade do período e significado dos códigos de personais.
- CT-RF14–16: legibilidade no tema escuro, conclusão da edição e regra de remoção de modalidades.
- CT-RF17–20: pesquisa, atualização, exclusão e criação de Categorias Crossfit.
- As quatro regras a validar (CT-RF08, CT-RF11, CT-RF13 e CT-RF16) exigem confirmação de produto antes de conclusão definitiva.

**Ampliação de escopo em 15/11/2026:** CT-RF21 — envio do cadastro de avaliação, tratamento de erro e critérios para reteste com dados válidos e inválidos; BUG-010 aberto.

**Exercícios — CT-RF22–CT-RF28:** código conforme a regra, exclusão e totais, edição preservando identidade, cadastro com imagem, campos obrigatórios e validação cruzada dos tipos de mídia. BUG-011–BUG-015 aguardam triagem; a imagem persistida de CT-RF25 permanece a validar.

**Grupos Musculares — CT-RF29–CT-RF33:** exclusão de registro, carregamento das imagens da listagem, cadastro, alteração do tipo de membro e filtros por código e por tipo. BUG-016 e BUG-017 aguardam triagem; a lógica de combinação dos filtros permanece não demonstrada.

**Objetivos de Treino — CT-RF35:** cadastro de objetivo pela tela Objetivos Treino, tratamento do erro de gravação, regra do campo Código e critérios para reteste com dados válidos e recusados. BUG-019 aguarda triagem; filtros por código e nome da mesma tela não puderam ser avaliados com a base vazia da gravação. A numeração CT-RF34 permanece reservada.

**Categorias Crossfit — CT-RF38:** cadastro de categoria informando apenas o nome, código atribuído pelo sistema, atualização da listagem e dos cartões e localização do registro pelos filtros de código e de nome. Sem defeito no fluxo gravado; a regra do campo Código e o contrato dos cartões permanecem a confirmar.

**SifitBox – Turmas — CT-RF39–CT-RF41:** cadastro de modalidade, exclusão de turmas e modalidades pela lixeira e cadastro de turma sem modalidade selecionada, a partir de uma única gravação. BUG-020 aguarda triagem; a regra de exclusão (CT-RF40) e a obrigatoriedade da modalidade (CT-RF41) permanecem a confirmar.

**Pagar.me e Configurações — CT-RF42–CT-RF45:** solicitação de saque, criação de cobrança, salvamento das Configurações (aba Home) e atualização do painel por período, a partir de uma única gravação. BUG-021 aguarda triagem; a regra de saque e a faixa do campo de dias permanecem a confirmar.

**Despesas Fixas — CT-RF46–CT-RF49:** filtros por código e nome, cadastro (com duas requisições de criação), exclusão com confirmação e edição, a partir de uma única gravação. O cadastro permanece a validar quanto à duplicidade.

**Relatórios — CT-RF50–CT-RF56:** geração de PDF de Matrículas, Contas a Receber, Contas a Pagar (Pagas), Avaliações, Clientes, Colaboradores e Caixas, a partir de uma gravação e de oito arquivos baixados (cinco vazios). BUG-022 e BUG-023 aguardam triagem.

**Grupos (treino) — CT-RF57 e CT-RF58:** exclusão e edição de grupo pela listagem, a partir de uma única gravação que também mostra o cadastro bem-sucedido de um novo grupo. BUG-024 (exclusão, HTTP 500) e BUG-025 (edição, status não persistido) aguardam triagem; o BUG-024 coincide com o BUG-016 já registrado para grupos musculares.

**Fichas de Anamnese — CT-RF59:** cadastro de anamnese para um aluno, testado com dois modelos e três respostas diferentes, tanto pela rota de aplicar quanto pela de salvar rascunho. BUG-032 (HTTP 500 em ambas as rotas, mensagem genérica) aguarda triagem; coincide no padrão de resposta com o BUG-016 e o BUG-024.

**Colaboradores — CT-RF65 a CT-RF70:** validações de data de nascimento, formato de CREF e campos obrigatórios na edição, duplicidade de função e exclusão de colaborador, a partir de seis gravações distintas. BUG-026 a BUG-031 aguardam triagem; o BUG-031 (exclusão, HTTP 500) coincide no padrão de resposta com o BUG-016 e o BUG-024.

**Ampliação de escopo em 16/11/2026:** CT-RF60 — Modelos de Anamnese: busca, filtro, cadastro com três perguntas do banco, duas edições e duas exclusões de modelo, a partir de uma única gravação. Aprovado conforme a gravação; nenhum defeito identificado no fluxo avaliado.

**Limites da cobertura atual:**

O CT-RF04_loginComSucesso foi aprovado conforme a gravação, sem nova execução nesta revisão. Não cobre credenciais inválidas, campos vazios, logout, expiração, persistência de Manter conectado, outros perfis ou exatidão dos dados exibidos no painel.

As etapas de envio da solicitação, entrega de mensagem, uso de token e definição de nova senha dependem da abertura do fluxo e da definição de suas regras. Não estão cobertas pela execução gravada.

A gravação de Perfil não valida o salvamento de alterações, as regras de obrigatoriedade ou todas as permissões. Esses fluxos exigem casos específicos após a definição das regras e a correção da apresentação.

O CT-RF03 foi documentado conforme o relato e as capturas fornecidos. Não houve acesso direto ao conteúdo do Jam, análise do código ou execução da matriz de reteste nesta revisão. A classificação atual não comprova falha específica no backend nem define onde a filtragem deve ocorrer.

---

## 🛠️ 4. Ferramentas utilizadas

| Ferramenta | Finalidade |
| --- | --- |
| Navegador | Executar os fluxos e registrar as condições de ambiente. |
| DevTools — Elements | Inspecionar a renderização dos campos e o DOM do perfil. |
| DevTools — Network e Console | Correlacionar interface, requisições e erros durante execução e reteste. |
| Jam e capturas | Preservar evidências e contexto dos comportamentos observados. |
| Google Drive | Referenciar o vídeo complementar do CT-RF01. |
| Markdown e GitHub | Documentar requisitos, cenários, resultados e defeitos. |

## 🔬 5. Técnicas de teste

- **Teste funcional:** comparar cada fluxo com os critérios de aceitação do requisito.
- **Análise exploratória:** observar interface, DOM, rede e console conforme as evidências disponíveis.
- **BDD:** descrever os cenários com Dado, Quando e Então.
- **Combinação de condições:** planejar a validação da lógica AND nos filtros de Clientes, incluindo correspondências parciais e conjunto vazio.

As técnicas previstas para o reteste não representam novas execuções realizadas nesta revisão.

---

## 🔐 6. Ambiente e preparação

### CT-RF01 — Recuperação de senha

| Item | Definição |
| --- | --- |
| URL da evidência atual | https://sifitalfa.centrion.com.br/login |
| Ambiente | Homologação; confirmar a mesma versão no reteste. |
| Navegador / sistema da gravação | Chrome 155.0.8059.85 / Windows 11, conforme metadados do Jam. |
| Estado da sessão | Usuário não autenticado. |
| Credenciais | Não são necessárias para acionar a opção. |
| Ferramentas | Navegador, DevTools (Network e Console) e Jam para evidências. |
| Preparação da rede no reteste | Habilitar captura de todas as requisições, remover filtros, limpar o histórico e preservar registros se houver navegação. |

### CT-RF02_ERRO — Perfil

| Item | Definição |
| --- | --- |
| URL afetada | https://sifit.centrion.com.br/profile, conforme Actions do Jam. Info apresenta `/configuracoes`. |
| Ambiente | Domínio distinto do CT-RF01; classificação e versão devem ser confirmadas antes do reteste. |
| Navegador / sistema / janela da gravação | Chrome 155.0.8059.85 / Windows 11 (x86) / 1536 × 742. Zoom não confirmado. |
| Gravação | 22/10/2026 às 21:45 BRT; aproximadamente 15 segundos. |
| Estado da sessão | Usuário autenticado, com acesso à opção Perfil. |
| Dados de teste | Conta com cadastro conhecido, campos preenchidos e permissões identificadas para comparação. Não registrar credenciais nos documentos. |
| Ferramentas | Navegador, DevTools (Elements, Network e Console), captura de tela e Jam. |
| Preparação | Registrar resolução e zoom, limpar registros e habilitar captura antes de acessar Perfil. |
| Variações de layout | Repetir na janela de referência 1536 × 742 e nas resoluções suportadas acordadas com o produto; registrar quais foram efetivamente executadas. |

### CT-RF03 — Filtros da página Clientes

| Item | Definição |
| --- | --- |
| Página afetada | Clientes; URL do frontend não confirmada. Registrar o endereço real antes da execução. |
| Endpoint informado | `POST https://backendsifit.centrion.com.br/api/clientesPorNome/1`; confirmar contrato e ambiente antes do reteste. |
| Ambiente / versão / navegador | Não confirmados; registrar também sistema operacional, resolução e zoom. Não herdar as condições dos outros casos. |
| Gravação | Data não confirmada; [Jam fornecido](https://jam.dev/c/657627ec-e7e2-455d-a505-9b2a26f44bf1), sem consulta direta ao conteúdo nesta revisão. |
| Estado da sessão | Usuário autenticado, com acesso à página Clientes e à empresa da pesquisa; `empresa_id: 1` foi informado no relato. |
| Dados de teste | Base com Código, Nome, Status, Situação Financeira, Plano e Personal conhecidos por cliente. Incluir correspondências completas, correspondências parciais e uma combinação sem resultados. |
| Valores de referência | Ativo/Inativo, Adimplente/Inadimplente, Plano Hendreu e Marcelo Longo Zandonadi. Confirmar IDs e regras; os exemplos `60` e `36` não estão validados. |
| Ferramentas | Navegador, DevTools (Network e Console), capturas e Jam. Remover autenticação dos registros compartilhados. |
| Preparação | Confirmar regras de Código/Nome, situação financeira e vínculos; listar previamente os clientes esperados para cada combinação. Habilitar a captura, remover filtros do painel de rede e limpar o histórico. |

---

### CT-RF04_loginComSucesso — Login

| Item | Definição |
| --- | --- |
| URL inicial / destino | `https://sifit.centrion.com.br/login` → `https://sifit.centrion.com.br/dashboard`. |
| Backend | `https://backendsifit.centrion.com.br`; chamadas registradas: `POST /api/login` e `POST /api/verifica-token-logado`. |
| Navegador / sistema / janela | Chrome 157.0.8103.51 / Windows 11 (x86) / 1536 × 742. |
| Gravação | 13/11/2026; aproximadamente 12 segundos; autor Leonardo Barbosa. |
| Versão / zoom / classificação do ambiente | Não informados; registrar antes de nova execução. |
| Dados de teste | Conta ativa com credenciais válidas e acesso ao dashboard. Omitir senha e tokens das evidências compartilhadas. |
| Preparação para nova execução | Iniciar sem sessão autenticada, preparar captura de rede e navegação e manter Manter conectado desmarcado, como na gravação. |
| Fonte | [Jam](https://jam.dev/c/5e4a28be-4e80-43d3-9587-1b113723cc38), com metadados, cronologia e quadros consultados diretamente. |

---

### CT-RF05 a CT-RF20 — ambiente das novas evidências

Gravações de 14/11/2026, entre aproximadamente 00:23 e 00:45 BRT, no frontend `https://sifit.centrion.com.br`. Chrome 157.0.8103.51 / Windows 11 (x86); tela informada 1920 × 957 e vídeos originais 1918 × 956 pixels. Versão, zoom e classificação do ambiente não confirmados. As páginas e os horários individuais estão em cada cenário e nos metadados da evidência.

| Grupo | Preparação para nova execução |
| --- | --- |
| CT-RF05–06 | Iniciar sem sessão; usar conta existente/senha incorreta ou identificador comprovadamente inexistente. |
| CT-RF07–12 | Base financeira conhecida; confirmar encargos, faixas de vencimento, referência dos cartões e aplicação do período. |
| CT-RF13 | Cadastro de personais conhecido; confirmar se Código é ID ou posição da lista. |
| CT-RF14–16 | Modalidades e turmas de teste; permissões de edição e regra de remoção confirmadas; conferir ambos os temas. |
| CT-RF17–20 | Categorias descartáveis, permissões e vínculos conhecidos para testar pesquisa e operações de cadastro. |

As ações de edição, criação e exclusão descritas ocorreram nas gravações fornecidas. Nenhuma dessas operações foi reexecutada durante esta atualização documental.

---

### CT-RF21 — ambiente e preparação

Gravação de 15/11/2026, início às 15:07:51,265 BRT, na página https://sifit.centrion.com.br/avaliacoes. Chrome 157.0.8103.51 / Windows 11 (x86), captura 1536 × 742. Versão, zoom e classificação do ambiente não identificados.

Para o reteste, preparar aluno existente selecionável pela busca, personal habilitado e data/hora permitidas. Os dados históricos são aluno 3423, funcionário 11, personal 7 e 15/11/2026 às 06:00; existência do aluno e regra de retroatividade precisam ser confirmadas. Conferir persistência antes de repetir envios.

### CT-RF22 a CT-RF28 — ambiente e preparação

| Item | Definição |
| --- | --- |
| Página | https://sifit.centrion.com.br/exercicios |
| Navegador / sistema / janela | Edge 157.0.8103.80 / Windows 11 (x86) / 1912 × 960, conforme Info. |
| Gravações | 15/11/2026: RF22 às 15:25 (5 s), RF23 às 15:40 (6 s), RF24 às 15:38 (9 s), RF25 às 15:35 (5 s), RF26 às 16:11 (4 s), RF27 às 16:08 (7 s) e RF28 às 16:07 (7 s), durações aproximadas. |
| Dados e permissões | Confirmar regra do código; preparar exercícios descartáveis com IDs e totais conhecidos; imagem e vídeo controlados, com extensão, MIME e tamanho registrados, sem dados pessoais. |
| Preparação | Registrar versão, zoom e ambiente; capturar foco, ação explícita de edição, IDs antes/depois, totais, mensagens de validação, rede e mídias após reabertura. Omitir credenciais e tokens. |
| Limites | RF22 baseado no relato e imagem inicial; RF23–25 em quadros e listagem Network; RF26–28 em quadros e Info, sem confirmação de MIME, persistência ou resposta detalhada da API; sem nova execução. |

### CT-RF29 a CT-RF33 — ambiente e preparação

| Item | Definição |
| --- | --- |
| Página | https://sifit.centrion.com.br/grupos-musculares |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema / janela | Chrome 157.0.8103.78 / Windows (x86) 11 / 1920 × 911, conforme Info. |
| Gravação | 15/11/2026 às 15h56 BRT, duração de 2 min 3 s; uma única gravação cobre os cinco casos. |
| Rede | Classificada como rápida no Jam: mais de 10 Mbps, latência de 50 ms. |
| Dados e permissões | Preparar grupo muscular descartável com vínculos conhecidos, registro com imagem cadastrada, nome de teste disponível e ao menos um tipo de membro sem registros associados, para exercitar o resultado vazio. |
| Preparação | Registrar versão, zoom e ambiente; capturar listagem, cartões de resumo, rodapé de contagem, diálogos, rede e console antes e depois de cada operação. Omitir credenciais e tokens. |
| Limites | Análise documental dos painéis do Jam, sem nova execução. Os cabeçalhos de resposta das imagens foram descartados por inconsistência do painel de detalhe. A cronologia não registra requisições de criação e de atualização com código de status. |

### CT-RF35 — ambiente e preparação

| Item | Definição |
| --- | --- |
| Página | https://sifit.centrion.com.br/objetivos-treino |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema / janela | Chrome 157.0.8103.78 / Windows (x86) 11 / 1920 × 911, conforme Info. |
| Gravação | 15/11/2026 às 18:13 BRT, duração de 1 min 12 s. |
| Rede | Classificada como rápida no Jam: 8,8 Mbps, latência de 100 ms. |
| Dados e permissões | Preparar objetivo de teste com nome disponível; definir a regra do campo Código e da descrição (caracteres especiais, tamanho); ter ao menos um objetivo cadastrado para exercitar filtros e cartões. |
| Preparação | Registrar versão, zoom e ambiente; capturar listagem, cartões de resumo, formulário, diálogos, rede (incluindo payload e resposta) e console antes e depois do envio. Omitir credenciais e tokens. |
| Limites | Análise documental dos painéis do Jam, sem nova execução. O Jam não capturou o corpo da requisição nem da resposta; a base estava vazia durante toda a gravação. |

### CT-RF38 — ambiente e preparação

| Item | Definição |
| --- | --- |
| Página | https://sifit.centrion.com.br/categorias-exercicios-crossfit |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema / janela | Chrome 157.0.8103.78 / Windows (x86) 11 / 1920 × 911, conforme Info. |
| Gravação | 15/11/2026 às 18:41 BRT, duração de 37 s. |
| Rede | Classificada como rápida no Jam: 8,8 Mbps, latência de 100 ms. |
| Dados e permissões | Base com categorias de códigos conhecidos; nome de teste disponível; confirmar com o produto a regra do campo Código e o contrato dos cartões Categorias, Exibidas e Atualizadas. |
| Preparação | Registrar versão, zoom e ambiente; capturar listagem, cartões, formulário, mensagens, rede (incluindo corpo da requisição e da resposta) e console antes e depois do cadastro. Omitir credenciais e tokens. |
| Limites | Análise documental dos painéis do Jam, sem nova execução. Os filtros não geram requisição de rede; a captura pode não incluir o carregamento inicial. Persistência após recarga não verificada. |

### CT-RF39 a CT-RF41 — ambiente e preparação

| Item | Definição |
| --- | --- |
| Página | https://sifit.centrion.com.br/sifitbox/turmas |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema / janela | Chrome 157.0.8103.78 / Windows (x86) 11 / 1920 × 911, conforme Info. |
| Gravação | 15/11/2026 às 18:51 BRT, duração de 1 min 39 s; uma única gravação cobre os três casos. |
| Rede | Classificada como rápida no Jam: 6,8 Mbps, latência de 50 ms. |
| Dados e permissões | Modalidades e turmas descartáveis com status e vínculos conhecidos; ao menos uma modalidade ativa; regra de exclusão (lógica ou física), de confirmação e de obrigatoriedade da modalidade definida com o produto. |
| Preparação | Registrar versão, zoom e ambiente; capturar listagens, formulários, mensagens, filtro de status, rede (incluindo corpos) e console antes e depois de cada operação, e gravar a tela com a validação nativa do navegador visível quando possível. Omitir credenciais e tokens. |
| Limites | Análise documental dos painéis do Jam, sem nova execução. Corpos das exclusões, filtro "Inativo", envio válido de turma e persistência após recarga não verificados. |

### CT-RF42 a CT-RF45 — ambiente e preparação

| Item | Definição |
| --- | --- |
| Página | https://sifit.centrion.com.br/pagarme e https://sifit.centrion.com.br/configuracoes |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema / janela | Chrome 157.0.8103.78 / Windows (x86) 11 / 1920 × 911, conforme Info. |
| Gravação | 15/11/2026 às 19:06 BRT, duração de 1 min 11 s; uma única gravação cobre os quatro casos. |
| Rede | Classificada como rápida no Jam: 6,8 Mbps, latência de 50 ms. |
| Dados e permissões | Conta de pagamento com saldo e movimentação conhecidos nos últimos 30 e 7 dias; valores de saque e de cobrança de teste autorizados; regra de saque e faixa válida dos campos de Configurações definidas com o produto. |
| Preparação | Registrar versão, zoom e ambiente; capturar indicadores, formulários, mensagens, rede (incluindo corpos) e console antes e depois de cada operação. Omitir credenciais e tokens. |
| Limites | Análise documental dos painéis do Jam, sem nova execução. Corpos de requisição e de resposta indisponíveis; resultado do saque, persistência das configurações e origem dos dados do painel não confirmados. |

### CT-RF46 a CT-RF49 — ambiente e preparação

| Item | Definição |
| --- | --- |
| Página | https://sifit.centrion.com.br/despesas-fixas |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema / janela | Chrome 157.0.8103.78 / Windows (x86) 11 / 1920 × 911, conforme Info. |
| Gravação | 15/11/2026 às 19:07 BRT, duração de 52 s; uma única gravação cobre os quatro casos. |
| Rede | Classificada como rápida no Jam: 6,8 Mbps, latência de 50 ms. |
| Dados e permissões | Base com despesas de códigos, status e recorrências conhecidos; despesa descartável para cadastro, edição e exclusão; contrato dos cartões definido com o produto. |
| Preparação | Registrar versão, zoom e ambiente; capturar listagem, cartões, formulários, diálogos, rede (incluindo corpos, com atenção ao número de requisições de criação) e console antes e depois de cada operação. Omitir credenciais e tokens. |
| Limites | Análise documental dos painéis do Jam, sem nova execução. Filtros sem requisição de rede (filtragem local não confirmada); corpo e resposta da segunda criação e persistência após recarga não verificados. |

### CT-RF50 a CT-RF56 — ambiente e preparação

| Item | Definição |
| --- | --- |
| Página | https://sifit.centrion.com.br/relatorios |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema / janela | Chrome 157.0.8103.78 / Windows (x86) 11 / 1920 × 911, conforme Info. |
| Gravação | 15/11/2026 às 19:09 BRT, duração de 58 s; uma única gravação e oito arquivos PDF baixados cobrem os sete casos. |
| Rede | Classificada como rápida no Jam: 6,8 Mbps, latência de 50 ms. |
| Dados e permissões | Período e filtros de cada relatório registrados; base com e sem registros no período conhecida; visualizador de PDF e pasta de downloads conferida antes e depois de cada geração. |
| Preparação | Registrar versão, zoom e ambiente; gerar um relatório por vez, capturando a requisição, o tamanho e o conteúdo do arquivo e comparando com os dados do módulo de origem. Omitir credenciais e tokens. |
| Limites | Análise documental do Jam e dos arquivos baixados, sem nova execução. A atividade do usuário não foi registrada no Console do Jam; a correspondência dos arquivos vazios com os tipos é inferida pela ordem dos downloads. |

### CT-RF57 — ambiente e preparação

| Item | Definição |
| --- | --- |
| Página | https://sifit.centrion.com.br/grupos |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema / janela | Chrome 157.0.8103.78 / Windows (x86) 11 / 1920 × 911, conforme Info. |
| Gravação | 15/11/2026 às 21h03 BRT, duração de 1 min 38 s; uma única gravação cobre o cadastro e a tentativa de exclusão. |
| Rede | Classificada como rápida no Jam: mais de 10 Mbps, latência de 50 ms. |
| Dados e permissões | Grupo de teste conhecido (código 1, "Treino Livre") cuja exclusão é esperada ser permitida; vínculos não confirmados previamente. |
| Preparação | Registrar versão, zoom e ambiente; capturar listagem, contadores, diálogo de confirmação, rede (corpo e cabeçalhos das duas tentativas) e console antes e depois da operação. Omitir credenciais e tokens. |
| Limites | Análise documental dos painéis do Jam, sem nova execução. O texto do diálogo de erro não foi confirmado visualmente (fecha em menos de um segundo na gravação); persistência após recarga e cenário de impedimento de regra não exercitados. |

---

### CT-RF58 — ambiente e preparação

| Item | Definição |
| --- | --- |
| Página | https://sifit.centrion.com.br/grupos |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema / janela | Chrome 157.0.8103.78 / Windows (x86) 11 / 1920 × 911, conforme Info. |
| Gravação | Mesma gravação do CT-RF57 — 15/11/2026 às 21h03 BRT, duração de 1 min 38 s; cobre o cadastro, duas edições e a tentativa de exclusão do grupo "Treino sla". |
| Rede | Classificada como rápida no Jam: mais de 10 Mbps, latência de 50 ms. |
| Dados e permissões | Grupo de teste conhecido (código 11, "Treino sla", recém-criado na mesma gravação) com todos os campos registrados antes de cada edição. |
| Preparação | Registrar versão, zoom e ambiente; capturar o formulário de edição, a seleção de cada campo, a rede (corpo e cabeçalhos de cada `POST /api/edita/grupo/{id}` e das consultas seguintes) e o console antes e depois de cada alteração. Omitir credenciais e tokens. |
| Limites | Análise documental dos painéis do Jam, sem nova execução. Não houve reteste alterando o status isoladamente de volta para "Ativo", nem verificação em outros grupos ou na entidade grupo muscular. |

---

### CT-RF59 — ambiente e preparação

| Item | Definição |
| --- | --- |
| Página | https://sifit.centrion.com.br/anamneses |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema / janela | Chrome 157.0.8103.78 / Windows (x86) 11 / 1920 × 911, conforme Info. |
| Gravação | 15/11/2026 às 22h07 BRT, duração de 1 min 28 s; cobre quatro tentativas de aplicar e três de salvar rascunho. |
| Rede | Classificada como rápida no Jam: mais de 10 Mbps, latência de 50 ms. |
| Dados e permissões | Aluno de teste ("Jorge") selecionável na busca; dois modelos de anamnese (identificados por `modelo_id` 3 e 5) com uma pergunta cada. |
| Preparação | Registrar versão, zoom e ambiente; capturar a seleção de aluno e modelo, o preenchimento da resposta, a revisão final, a rede (corpo e cabeçalhos de cada `POST /api/anamnese/aplicar/{id}` e `POST /api/anamnese/rascunho/{id}`) e o console antes e depois de cada tentativa. Omitir credenciais e tokens. |
| Limites | Análise documental dos painéis do Jam, sem nova execução. Não houve acesso a logs do servidor; não foi confirmado se as tentativas de rascunho afetaram o mesmo registro ou criaram registros distintos. |

---

## 📋 7. Casos de teste e situação

| Requisito | Caso de teste | Tipo | Resultado nas evidências | Defeito | Próxima ação |
| --- | --- | --- | --- | --- | --- |
| [RF01](Analise%20de%20requisitos.md#rf01--iniciar-recuperação-de-senha) | [CT-RF01 — Acionar "Esqueci minha senha"](Cenario_Teste/CT-RF01_Esqueci-senha.md) | Funcional / fluxo positivo, com análise exploratória de rede | Reprovado | [BUG-001](Relatorio-de-Bugs.md#bug-001--link-esqueci-minha-senha-não-executa-nenhuma-ação) | Corrigir e retestar. |
| [RF02](Analise%20de%20requisitos.md#rf02--exibir-perfil-do-usuário-autenticado) | [CT-RF02_ERRO — Exibir Perfil](Cenario_Teste/CT-RF02_ERRO.md) | Funcional / interface, com análise do DOM e evidências | Reprovado | [BUG-002](Relatorio-de-Bugs.md#bug-002--perfil-com-dados-fictícios-campos-ausentes-e-layout-desconfigurado) | Corrigir e retestar. |
| [RF03](Analise%20de%20requisitos.md#rf03--pesquisar-clientes-com-filtros-combinados) | [CT-RF03 — Filtrar Clientes](Cenario_Teste/CT-RF03_FILTRO_TelaClientes.md) | Funcional / filtros combinados, com análise de integração e evidências | Reprovado conforme o relato; sem nova execução | [BUG-003](Relatorio-de-Bugs.md#bug-003--filtros-combinados-da-página-clientes-não-restringem-a-listagem) | Investigar a causa, corrigir e executar a matriz de reteste. |
| [RF04](Analise%20de%20requisitos.md#rf04--autenticar-usuário-com-credenciais-válidas) | [CT-RF04_loginComSucesso](Cenario_Teste/CT-RF04_loginComSucesso.md) | Funcional / fluxo positivo de autenticação | Aprovado conforme a gravação; sem nova execução | Nenhum identificado no fluxo avaliado | Utilizar como regressão em futuras versões. |
| [RF05](Analise%20de%20requisitos.md#rf05) | [CT-RF05](Cenario_Teste/CT-RF05_Login_SenhaIncorreta.md) | Funcional manual / regressão | Aprovado conforme a gravação | Nenhum no fluxo avaliado | Usar como regressão de autenticação negativa; preparar conta conhecida e repetir após alterações no login. |
| [RF06](Analise%20de%20requisitos.md#rf06) | [CT-RF06](Cenario_Teste/CT-RF06_Login_UsuarioInexistente.md) | Funcional manual / regressão | Aprovado conforme a gravação | Nenhum no fluxo avaliado | Repetir com identificador de inexistência comprovada; a classificação atual refere-se à recusa visível do cenário declarado pelo autor. |
| [RF07](Analise%20de%20requisitos.md#rf07) | [CT-RF07](Cenario_Teste/CT-RF07_Exportacao_Financeiro.md) | Funcional / manifestação observada | Reprovado nas evidências | [BUG-004](Relatorio-de-Bugs.md#bug-004) | Investigar o retorno do botão; no reteste capturar o histórico de downloads e abrir o arquivo antes de concluir se a exportação foi gerada. |
| [RF08](Analise%20de%20requisitos.md#rf08) | [CT-RF08](Cenario_Teste/CT-RF08_Calculo_Cobranca.md) | Exploratório / regra a confirmar | A validar — regra ou contexto pendente | Sem defeito confirmado | Confirmar a origem dos R$ 20,83 além de principal e multa e a regra da mensagem; não registrar cálculo incorreto antes dessa validação. |
| [RF09](Analise%20de%20requisitos.md#rf09) | [CT-RF09](Cenario_Teste/CT-RF09_Contagem_Mensalidades.md) | Funcional / manifestação observada | Reprovado nas evidências | [BUG-005](Relatorio-de-Bugs.md#bug-005) | Retestar com o CT-RF10; os dois cenários documentam manifestações do BUG-005, sem criar um defeito duplicado. |
| [RF10](Analise%20de%20requisitos.md#rf10) | [CT-RF10](Cenario_Teste/CT-RF10_Filtro_Mensalidades.md) | Funcional / manifestação observada | Reprovado nas evidências | [BUG-005](Relatorio-de-Bugs.md#bug-005) | Retestar em conjunto com CT-RF09 e conferir o contrato da faixa Até 7 dias antes de preparar a base. |
| [RF11](Analise%20de%20requisitos.md#rf11) | [CT-RF11](Cenario_Teste/CT-RF11_Metricas_Financeiro.md) | Exploratório / regra a confirmar | A validar — regra ou contexto pendente | Sem defeito confirmado | Confirmar os contratos dos cartões; a constância de totais globais não é suficiente para abrir outro defeito financeiro. |
| [RF12](Analise%20de%20requisitos.md#rf12) | [CT-RF12](Cenario_Teste/CT-RF12_Periodo_Dashboard.md) | Funcional / manifestação observada | Reprovado nas evidências | [BUG-006](Relatorio-de-Bugs.md#bug-006) | Corrigir e retestar a validação do intervalo; avaliar a atualização dos indicadores em base controlada como verificação complementar. |
| [RF13](Analise%20de%20requisitos.md#rf13) | [CT-RF13](Cenario_Teste/CT-RF13_Codigos_Personais.md) | Exploratório / regra a confirmar | A validar — regra ou contexto pendente | Sem defeito confirmado | Confirmar a semântica da coluna Código; quatro linhas e total quatro não sustentam um defeito de quantidade. |
| [RF14](Analise%20de%20requisitos.md#rf14) | [CT-RF14](Cenario_Teste/CT-RF14_Contraste_TemaEscuro.md) | Funcional / manifestação observada | Reprovado nas evidências | [BUG-007](Relatorio-de-Bugs.md#bug-007) | Ajustar as cores e retestar ambos os temas; medir contraste se houver critério formal de acessibilidade definido. |
| [RF15](Analise%20de%20requisitos.md#rf15) | [CT-RF15](Cenario_Teste/CT-RF15_Edicao_Modalidade.md) | Funcional / manifestação observada | Reprovado nas evidências | [BUG-008](Relatorio-de-Bugs.md#bug-008) | Verificar o fluxo de conclusão da edição e retestar persistência. A evidência reprova a clareza da ação de salvar; não afirma que o ícone de editar inexiste. |
| [RF16](Analise%20de%20requisitos.md#rf16) | [CT-RF16](Cenario_Teste/CT-RF16_Exclusao_Modalidade.md) | Exploratório / regra a confirmar | A validar — regra ou contexto pendente | Sem defeito confirmado | Confirmar a exclusão lógica e a nomenclatura da ação; registrar defeito apenas se houver divergência com a regra definida. |
| [RF17](Analise%20de%20requisitos.md#rf17) | [CT-RF17](Cenario_Teste/CT-RF17_Filtros_Categorias.md) | Funcional manual / regressão | Aprovado conforme a gravação | Nenhum no fluxo avaliado | Usar como regressão; combinações, conjunto vazio, caracteres especiais e paginação exigem execuções adicionais. |
| [RF18](Analise%20de%20requisitos.md#rf18) | [CT-RF18](Cenario_Teste/CT-RF18_Atualizacao_Categoria.md) | Funcional manual / regressão | Aprovado conforme a gravação | Nenhum no fluxo avaliado | Usar como regressão; acrescentar recarga e nova consulta para ampliar a verificação de persistência. |
| [RF19](Analise%20de%20requisitos.md#rf19) | [CT-RF19](Cenario_Teste/CT-RF19_Exclusao_Categoria.md) | Funcional / manifestação observada | Reprovado nas evidências | [BUG-009](Relatorio-de-Bugs.md#bug-009) | Investigar o HTTP 500 com logs do servidor e vínculos da categoria; corrigir e retestar cenários permitido e impedido. |
| [RF20](Analise%20de%20requisitos.md#rf20) | [CT-RF20](Cenario_Teste/CT-RF20_Criacao_Categoria.md) | Funcional manual / regressão | Aprovado conforme a gravação | Nenhum no fluxo avaliado | Usar como regressão; campos vazios, nomes duplicados e limites de tamanho permanecem fora do cenário gravado. |
| [RF21](Analise%20de%20requisitos.md#rf21) | [CT-RF21](Cenario_Teste/CT-RF21_Cadastro_Avaliacao.md) | Funcional manual / tratamento de erro | Reprovado nas evidências | [BUG-010](Relatorio-de-Bugs.md#bug-010) | Investigar o HTTP 500; retestar dados válidos, vínculo inválido, retroatividade e persistência. |
| [RF22](Analise%20de%20requisitos.md#rf22) | [CT-RF22](Cenario_Teste/CT-RF22_Digitacao_Codigo_Exercicio.md) | Funcional manual / análise documental | Reprovado conforme o relato; reprodução independente pendente. | [BUG-011](Relatorio-de-Bugs.md#bug-011), em triagem | Confirmar a regra, reproduzir o impedimento e retestar o campo após correção. |
| [RF23](Analise%20de%20requisitos.md#rf23) | [CT-RF23](Cenario_Teste/CT-RF23_Exclusao_Exercicio.md) | Funcional manual / análise documental | Aprovado no trecho consultado. | Sem defeito confirmado | Manter como regressão. Em nova execução, recarregar a página para conferir persistência e testar separadamente as regras para exercícios vinculados. |
| [RF24](Analise%20de%20requisitos.md#rf24) | [CT-RF24](Cenario_Teste/CT-RF24_Edicao_Exercicio.md) | Funcional manual / análise documental | Reprovado no trecho consultado; confirmar operação e identidade dos registros na reprodução. | [BUG-012](Relatorio-de-Bugs.md#bug-012), em triagem | Reproduzir a partir da ação explícita de edição e comparar os identificadores antes e depois. Investigar eventual envio para criação como hipótese, sem atribuir causa técnica antes de verificar código e contrato da API. |
| [RF25](Analise%20de%20requisitos.md#rf25) | [CT-RF25](Cenario_Teste/CT-RF25_Envio_Exercicio_Imagem.md) | Funcional manual / análise documental | A validar — criação visível; persistência e associação da imagem não confirmadas. | Sem defeito confirmado | Reabrir o exercício criado e conferir a imagem salva. Testar formatos e tamanhos inválidos em casos separados; essas variações não recebem resultado nesta análise. |
| [RF26](Analise%20de%20requisitos.md#rf26) | [CT-RF26](Cenario_Teste/CT-RF26_Exercicio_Campos_Vazios.md) | Funcional manual / teste negativo | Reprovado — sem feedback de validação visível. | [BUG-013](Relatorio-de-Bugs.md#bug-013), em triagem | Exibir validação por campo, confirmar bloqueio da persistência e retestar. |
| [RF27](Analise%20de%20requisitos.md#rf27) | [CT-RF27](Cenario_Teste/CT-RF27_Video_Campo_Imagem.md) | Funcional manual / teste negativo de mídia | Reprovado — arquivo rejeitado sem feedback visível. | [BUG-014](Relatorio-de-Bugs.md#bug-014), em triagem | Informar tipos aceitos e retestar arquivo por extensão e MIME, incluindo persistência. |
| [RF28](Analise%20de%20requisitos.md#rf28) | [CT-RF28](Cenario_Teste/CT-RF28_Imagem_Campo_Video.md) | Funcional manual / teste negativo de mídia | Reprovado — arquivo rejeitado sem feedback visível. | [BUG-015](Relatorio-de-Bugs.md#bug-015), em triagem | Informar tipos aceitos e retestar arquivo por extensão e MIME, incluindo persistência. |
| [RF29](Analise%20de%20requisitos.md#rf29) | [CT-RF29](Cenario_Teste/CT-RF29_Exclusao_GrupoMuscular.md) | Funcional manual / análise de evidências | Reprovado nas evidências | [BUG-016](Relatorio-de-Bugs.md#bug-016), em triagem | Investigar o HTTP 500 com logs do servidor e vínculos do registro; corrigir e retestar os cenários permitido e impedido. |
| [RF30](Analise%20de%20requisitos.md#rf30) | [CT-RF30](Cenario_Teste/CT-RF30_Imagens_GruposMusculares.md) | Funcional manual / análise de evidências | Reprovado nas evidências | [BUG-017](Relatorio-de-Bugs.md#bug-017), em triagem | Verificar a existência dos arquivos, o nome gravado em cada registro e a regra que responde 422; definir o estado neutro para registros sem imagem. |
| [RF31](Analise%20de%20requisitos.md#rf31) | [CT-RF31](Cenario_Teste/CT-RF31_Cadastro_GrupoMuscular.md) | Funcional manual / regressão | Aprovado conforme a gravação | Nenhum no fluxo avaliado | Usar como regressão; campos em branco, nomes duplicados, limites de tamanho e código informado manualmente exigem execuções adicionais. |
| [RF32](Analise%20de%20requisitos.md#rf32) | [CT-RF32](Cenario_Teste/CT-RF32_Edicao_TipoMembro.md) | Funcional manual / regressão | Aprovado conforme a gravação | Nenhum no fluxo avaliado | Usar como regressão; conferir persistência após recarga e confirmar se a imagem enviada na edição é salva. |
| [RF33](Analise%20de%20requisitos.md#rf33) | [CT-RF33](Cenario_Teste/CT-RF33_Filtros_GruposMusculares.md) | Funcional manual / regressão | Aprovado conforme a gravação | Nenhum no fluxo avaliado | Usar como regressão; executar um caso com critérios contraditórios para demonstrar a lógica combinada, além de busca por nome, valores inválidos e paginação. |
| [RF35](Analise%20de%20requisitos.md#rf35) | [CT-RF35](Cenario_Teste/CT-RF35_Cadastro_Objetivo_Treino.md) | Funcional manual / tratamento de erro | Reprovado nas evidências | [BUG-019](Relatorio-de-Bugs.md#bug-019), em triagem | Investigar o HTTP 500 com logs do servidor; retestar dados válidos, descrição com caracteres especiais, campos vazios, código manual e persistência; conferir que um clique gera uma única gravação. |
| [RF38](Analise%20de%20requisitos.md#rf38) | [CT-RF38](Cenario_Teste/CT-RF38_Cadastro_Categoria_Codigo_Automatico.md) | Funcional manual / regressão | Aprovado conforme a gravação | Nenhum no fluxo avaliado | Usar como regressão; nome vazio, nome duplicado, limites de tamanho, código inexistente no filtro e persistência após recarga exigem execuções adicionais; confirmar a regra do campo Código. |
| [RF39](Analise%20de%20requisitos.md#rf39) | [CT-RF39](Cenario_Teste/CT-RF39_Cadastro_Modalidade.md) | Funcional manual / regressão | Aprovado conforme a gravação | Nenhum no fluxo avaliado | Usar como regressão; nome vazio, nome duplicado, limites de tamanho, status Inativo e persistência após recarga exigem execuções adicionais. |
| [RF40](Analise%20de%20requisitos.md#rf40) | [CT-RF40](Cenario_Teste/CT-RF40_Exclusao_Turmas_Modalidades.md) | Exploratório / regra a confirmar | A validar — regra ou contexto pendente | Sem defeito confirmado | Confirmar a exclusão lógica, a confirmação prévia e a exibição de registros inativos sob o filtro "Ativo"; registrar defeito apenas se houver divergência com a regra definida. |
| [RF41](Analise%20de%20requisitos.md#rf41) | [CT-RF41](Cenario_Teste/CT-RF41_Cadastro_Turma_Sem_Modalidade.md) | Funcional manual / teste negativo | Reprovado — sem feedback de validação visível | [BUG-020](Relatorio-de-Bugs.md#bug-020), em triagem | Confirmar a obrigatoriedade da modalidade, reproduzir com a validação nativa visível e retestar o envio válido e a persistência. |
| [RF42](Analise%20de%20requisitos.md#rf42) | [CT-RF42](Cenario_Teste/CT-RF42_Solicitacao_Saque_PagarMe.md) | Exploratório / regra a confirmar | A validar — regra ou contexto pendente | Sem defeito confirmado | Confirmar a regra de saque e reexecutar com saldo conhecido, capturando corpo e resposta; testar valor acima do saldo e valor inválido. |
| [RF43](Analise%20de%20requisitos.md#rf43) | [CT-RF43](Cenario_Teste/CT-RF43_Criacao_Cobranca_PagarMe.md) | Funcional manual / regressão | Aprovado conforme a gravação | Nenhum no fluxo avaliado | Usar como regressão; outros métodos, dados inválidos, link gerado e presença da cobrança em Transações recentes exigem execuções adicionais. |
| [RF44](Analise%20de%20requisitos.md#rf44) | [CT-RF44](Cenario_Teste/CT-RF44_Configuracoes_Home_Salvamento.md) | Exploratório / regra a confirmar | A validar — regra ou contexto pendente | Sem defeito confirmado | Confirmar a faixa do campo de dias e a mensagem de salvamento; reexecutar com recarga, Cancelar e valores limite. |
| [RF45](Analise%20de%20requisitos.md#rf45) | [CT-RF45](Cenario_Teste/CT-RF45_Painel_PagarMe_Periodo.md) | Funcional manual / manifestação observada | Reprovado nas evidências | [BUG-021](Relatorio-de-Bugs.md#bug-021), em triagem | Reproduzir com conta de movimentação conhecida, comparar períodos e capturar corpo e resposta de recebiveis, transacoes e pagarme. |
| [RF46](Analise%20de%20requisitos.md#rf46) | [CT-RF46](Cenario_Teste/CT-RF46_Filtros_Despesas_Fixas.md) | Funcional manual / regressão | Aprovado conforme a gravação | Nenhum no fluxo avaliado | Usar como regressão; combinação de critérios, resultado vazio, filtros de status e recorrência e a regra de correspondência do código exigem execuções adicionais. |
| [RF47](Analise%20de%20requisitos.md#rf47) | [CT-RF47](Cenario_Teste/CT-RF47_Cadastro_Despesa_Fixa.md) | Exploratório / regra a confirmar | A validar — regra ou contexto pendente | Sem defeito confirmado | Reproduzir capturando as duas requisições de criação e conferir a quantidade de registros após recarga; confirmar a regra do código. |
| [RF48](Analise%20de%20requisitos.md#rf48) | [CT-RF48](Cenario_Teste/CT-RF48_Exclusao_Despesa_Fixa.md) | Funcional manual / regressão | Aprovado conforme a gravação | Nenhum no fluxo avaliado | Usar como regressão; Cancelar, despesa com vínculos, natureza da exclusão e persistência após recarga exigem execuções adicionais. |
| [RF49](Analise%20de%20requisitos.md#rf49) | [CT-RF49](Cenario_Teste/CT-RF49_Edicao_Despesa_Fixa.md) | Funcional manual / regressão | Aprovado conforme a gravação | Nenhum no fluxo avaliado | Usar como regressão; edição de nome, valor e status, Cancelar, pré-preenchimento da recorrência e persistência após recarga exigem execuções adicionais. |
| [RF50](Analise%20de%20requisitos.md#rf50) | [CT-RF50](Cenario_Teste/CT-RF50_Relatorio_Matriculas.md) | Funcional manual / regressão | Aprovado conforme a gravação | Nenhum no fluxo avaliado | Usar como regressão; conferir com a lista de matrículas e exercitar filtros e período sem registros. |
| [RF51](Analise%20de%20requisitos.md#rf51) | [CT-RF51](Cenario_Teste/CT-RF51_Relatorio_Contas_Receber.md) | Funcional manual / manifestação observada | Reprovado nas evidências | [BUG-022](Relatorio-de-Bugs.md#bug-022), em triagem | Comparar com o módulo Contas a Receber e reexecutar com valores conhecidos, Detalhado e outros status. |
| [RF52](Analise%20de%20requisitos.md#rf52) | [CT-RF52](Cenario_Teste/CT-RF52_Relatorio_Contas_Pagar_Pagas.md) | Exploratório / regra a confirmar | A validar — regra ou contexto pendente | Sem defeito confirmado | Conferir as contas pagas do período no módulo e reexecutar com um período que contenha pagamentos. |
| [RF53](Analise%20de%20requisitos.md#rf53) | [CT-RF53](Cenario_Teste/CT-RF53_Relatorio_Avaliacoes_Vazio.md) | Funcional manual / manifestação observada | Reprovado nas evidências | [BUG-023](Relatorio-de-Bugs.md#bug-023), em triagem | Investigar a geração com logs do servidor e retestar com e sem registros no período, comparando com os relatórios que abrem. |
| [RF54](Analise%20de%20requisitos.md#rf54) | [CT-RF54](Cenario_Teste/CT-RF54_Relatorio_Clientes_Vazio.md) | Funcional manual / manifestação observada | Reprovado nas evidências | [BUG-023](Relatorio-de-Bugs.md#bug-023), em triagem | Investigar a geração com logs do servidor e retestar com e sem registros no período, comparando com os relatórios que abrem. |
| [RF55](Analise%20de%20requisitos.md#rf55) | [CT-RF55](Cenario_Teste/CT-RF55_Relatorio_Colaboradores_Vazio.md) | Funcional manual / manifestação observada | Reprovado nas evidências | [BUG-023](Relatorio-de-Bugs.md#bug-023), em triagem | Investigar a geração com logs do servidor e retestar com e sem registros no período, comparando com os relatórios que abrem. |
| [RF56](Analise%20de%20requisitos.md#rf56) | [CT-RF56](Cenario_Teste/CT-RF56_Relatorio_Caixas_Vazio.md) | Funcional manual / manifestação observada | Reprovado nas evidências | [BUG-023](Relatorio-de-Bugs.md#bug-023), em triagem | Investigar a geração com logs do servidor e retestar com e sem registros no período, comparando com os relatórios que abrem. |
| [RF57](Analise%20de%20requisitos.md#rf57) | [CT-RF57](Cenario_Teste/CT-RF57_Exclusao_Grupo.md) | Funcional manual / análise de evidências | Reprovado nas evidências | [BUG-024](Relatorio-de-Bugs.md#bug-024), em triagem | Investigar o HTTP 500 com logs do servidor e os vínculos do grupo de código 1, em conjunto com o BUG-016; corrigir e retestar os cenários permitido e impedido. |
| [RF58](Analise%20de%20requisitos.md#rf58) | [CT-RF58](Cenario_Teste/CT-RF58_Edicao_Grupo.md) | Funcional manual / análise de evidências | Reprovado nas evidências | [BUG-025](Relatorio-de-Bugs.md#bug-025), em triagem | Investigar a rotina de edição quanto ao campo status; corrigir e retestar a edição de cada campo isoladamente. |
| [RF59](Analise%20de%20requisitos.md#rf59) | [CT-RF59](Cenario_Teste/CT-RF59_Cadastro_Anamnese.md) | Funcional manual / análise de evidências | Reprovado nas evidências | [BUG-032](Relatorio-de-Bugs.md#bug-032), em triagem | Investigar as rotinas de aplicar e rascunho com acesso a logs do servidor; corrigir e retestar o cadastro completo de uma anamnese. |

---

## 🔄 8. Procedimento de execução e reteste

### CT-RF01

1. Registrar data, URL, versão disponível e navegador da execução.
2. Acessar a página de login sem autenticação e preparar Network e Console.
3. Executar o [CT-RF01](Cenario_Teste/CT-RF01_Esqueci-senha.md), observando a interface e os registros após o clique.
4. Comparar o comportamento com os critérios do RF01 e registrar o resultado obtido.
5. Salvar evidências visuais e de rede, inclusive quando não houver requisições.
6. Após a correção, repetir o caso e verificar se o fluxo abre e permite prosseguir. Uma abertura local de formulário não exige, por si só, requisição ao servidor.
7. Atualizar o relatório de testes e o BUG-001 com as novas evidências e o resultado do reteste.

### CT-RF02_ERRO

1. Registrar data, URL, versão, navegador, resolução, zoom e permissões da conta de teste.
2. Autenticar-se e preparar Elements, Network e Console; acessar Perfil pelo menu do usuário.
3. Comparar nome e demais dados apresentados com o cadastro conhecido, verificando ausência de conteúdo fictício.
4. Conferir os rótulos e campos das seções Usuário, Documentos e Endereço, inclusive interação com campos editáveis.
5. Conferir português, padrão visual, dimensionamento das imagens e ausência de transbordamento horizontal nas resoluções selecionadas.
6. Inspecionar se os campos geram os controles esperados no DOM. Correlacionar eventuais falhas de rede ou console com a interface, sem presumir a causa apenas por atributos vazios.
7. Salvar captura e registros; comparar com os critérios do RF02 e atualizar o resultado do caso e o BUG-002. Não alterar dados da conta para comprovar apenas a renderização.

### CT-RF03

1. Registrar data, URL, versão, navegador e empresa, confirmando as permissões da conta e os IDs reais das opções.
2. Preparar a base conhecida e os conjuntos esperados. Incluir clientes que atendam apenas a parte dos critérios para detectar uso indevido de lógica OR ou filtros ignorados.
3. Preparar Network e Console. Executar a reprodução do [CT-RF03](Cenario_Teste/CT-RF03_FILTRO_TelaClientes.md), com Código e Nome vazios e Ativo + Inadimplente + Plano Hendreu + Marcelo Longo Zandonadi.
4. Clicar em Buscar, registrar as seleções e conferir os atributos de cada cliente retornado com a base de referência. Verificar também a ausência de clientes esperados, considerando outras páginas, se houver paginação.
5. Alternar somente a Situação para Adimplente e repetir a busca e a conferência. Preparar dados que tornem verificável a diferença entre os conjuntos.
6. Se a busca ocorrer no servidor, conferir os parâmetros conforme o contrato. Se ocorrer localmente, verificar a aplicação de todos os critérios sobre dados suficientes. Não aprovar pela presença de HTTP 200 ou pelo tamanho da resposta.
7. Executar as nove variações da [matriz de reteste](Cenario_Teste/CT-RF03_FILTRO_TelaClientes.md#matriz-de-reteste-proposta): Ativo + plano; Inativo + Plano Hendreu; Ativo + Inadimplente; Adimplente + personal; quatro filtros combinados; alternância da situação; conjunto vazio; Código/Nome combinados; limpeza das restrições.
8. Na busca sem correspondências, conferir a mensagem **"Nenhum cliente encontrado"** e a ausência de linhas anteriores. Ao limpar filtros, conferir a remoção das restrições correspondentes.
9. Registrar o resultado de cada variação e as evidências de interface e integração sem tokens. Atualizar o relatório dos testes e o BUG-003 somente com os resultados efetivamente obtidos.

---

### CT-RF04_loginComSucesso

1. Registrar data, URL, versão, navegador, resolução e zoom; usar conta de teste autorizada com acesso ao painel.
2. Acessar `/login` sem sessão autenticada e preparar a captura de rede e navegação.
3. Preencher Login e Senha válidos, mantendo **Manter conectado** desmarcado, e conferir a senha mascarada.
4. Clicar em **Entrar** e acompanhar a conclusão da autenticação.
5. Conferir a URL `/dashboard`, o menu de navegação e o resumo da academia visíveis. Correlacionar as chamadas de autenticação com o resultado visual; HTTP 200 isoladamente não aprova o caso.
6. Registrar o resultado e as evidências sem senha ou tokens. Este procedimento é destinado à próxima execução; a aprovação atual se baseia no Jam de 13/11/2026.

---

### CT-RF05 a CT-RF20 — próximos testes

1. Confirmar versão e ambiente; preparar dados conhecidos conforme as pré-condições do cenário.
2. Executar os passos e o BDD do caso; registrar o resultado efetivo e o Jam da nova execução.
3. Comparar os critérios com interface, arquivo gerado ou cadastro de referência, conforme o fluxo. HTTP 200 isoladamente não aprova um caso.
4. Para CT-RF08/11/13/16, registrar primeiro a decisão de produto sobre a regra pendente. Não converter uma dúvida em defeito sem demonstrar a divergência.
5. Retestar os casos reprovados após correção. CT-RF09 e CT-RF10 compartilham BUG-005 e precisam de conferências próprias para encerrar o mesmo defeito.
6. Executar CT-RF05/06/17/18/20 como regressão nas próximas versões; ampliações de cobertura permanecem planejadas até terem evidência própria.
7. Atualizar cenário, requisito, relatório e defeito com a data e evidência da versão testada, preservando os registros históricos.

---

<a id="ct-rf21"></a>

### CT-RF21 — reteste após correção

1. Identificar a versão disponibilizada e confirmar as regras de vínculo do aluno e data/hora.
2. Cadastrar avaliação com aluno selecionado pela busca, personal habilitado e horário permitido; conferir sucesso e registro após nova consulta.
3. Repetir os dados históricos em ambiente de teste e exigir cadastro ou validação específica, sem HTTP 500.
4. Comparar aluno inexistente, entrada manual sem seleção e horário passado/futuro; documentar cada resultado separadamente.
5. Conferir ausência de registros parciais ou duplicados e anexar nova evidência antes de encerrar BUG-010.

Todas essas variações permanecem planejadas e não são contadas como execuções nesta inclusão.

---

### CT-RF22 a CT-RF28 — próximos testes

1. CT-RF22 / BUG-011: confirmar código manual ou automático; reproduzir foco, digitação, correção e manutenção após Tab.
2. CT-RF23: excluir registro de teste, conferir totais e preservação dos demais; recarregar para conferir persistência.
3. CT-RF24 / BUG-012: abrir explicitamente edição, comparar IDs e total antes/depois, salvar o nome e conferir ausência de duplicação. Se era criação, reavaliar o defeito.
4. CT-RF25: criar com imagem válida, reabrir e recarregar para conferir associação. Formatos e tamanhos inválidos exigem execuções separadas.
5. CT-RF26 / BUG-013: salvar todos os campos vazios, depois uma combinação por vez; conferir mensagens, foco, ausência de requisição indevida e inexistência de registro vazio.
6. CT-RF27 / BUG-014: selecionar vídeo controlado no campo Imagem; registrar extensão, MIME, tamanho, feedback, rede e ausência de vínculo.
7. CT-RF28 / BUG-015: selecionar imagem controlada no campo Vídeo; registrar extensão, MIME, tamanho, feedback, rede e ausência de vínculo.
8. Registrar versão e evidência; verificações planejadas não recebem resultado de execução.

### CT-RF29 a CT-RF33 — próximos testes

1. CT-RF29 / BUG-016: registrar a listagem e os contadores, acionar a exclusão de um registro permitido, confirmar no diálogo e conferir mensagem, status da chamada e presença do registro. Repetir com um registro de exclusão impedida.
2. CT-RF30 / BUG-017: conferir a coluna IMAGEM e o status das requisições de arquivo; abrir uma URL de imagem diretamente no navegador e registrar status e corpo; repetir após busca e troca de tema.
3. CT-RF31: cadastrar com nome e tipo válidos, conferir registro, código atribuído, rodapé e cartões; recarregar para conferir persistência. Testar código informado manualmente em execução separada.
4. CT-RF32: abrir a edição, alterar o tipo de membro, salvar e conferir listagem e cartões; recarregar para conferir persistência. Anexar imagem e verificar a associação após reabrir.
5. CT-RF33: filtrar por tipo sem registros, por tipo com registros e por código; executar um caso com código e tipo contraditórios, cujo retorno esperado é o conjunto vazio; limpar os critérios e conferir o retorno da listagem completa.
6. Registrar versão e evidência; verificações planejadas não recebem resultado de execução.

### CT-RF35 — próximos testes

1. CT-RF35 / BUG-019: registrar a listagem e os cartões; abrir Novo Objetivo, informar nome e descrição simples e salvar; conferir mensagem, status da chamada, registro na listagem, cartões e persistência após recarga.
2. Repetir com os dados históricos (descrição com `#@`) para comparar; confirmar no payload e na resposta o que o servidor recusa, com a captura de rede preparada antes do envio.
3. Salvar com nome e descrição vazios, com nome duplicado e com texto longo; conferir validação por campo e ausência de registro vazio ou parcial.
4. Tentar informar o Código manualmente e confirmar com o produto se o campo é automático (ver CT-RF22 / BUG-011 e CT-RF31).
5. Conferir que um único clique em Salvar gera uma única requisição de gravação.
6. Com ao menos um objetivo cadastrado, filtrar por código e nome, incluindo um resultado vazio, e conferir a mensagem "Nenhum objetivo encontrado" ou equivalente.
7. Registrar versão e evidência; verificações planejadas não recebem resultado de execução.

### CT-RF38 — próximos testes

1. CT-RF38: registrar a listagem, os códigos e os cartões; filtrar por nome e por código existentes e limpar os filtros; abrir Nova Categoria, informar o nome e tentar digitar no campo Código; salvar e conferir mensagem, código atribuído, listagem e cartões; recarregar para conferir persistência.
2. Filtrar pelo código atribuído e conferir que apenas a nova categoria é exibida; testar código inexistente, não numérico e a combinação contraditória de código e nome, cujo retorno esperado é o conjunto vazio.
3. Salvar com nome vazio, nome duplicado e texto longo; conferir validação por campo e ausência de registro vazio ou duplicado.
4. Confirmar com o produto a regra do campo Código (automático ou bloqueado) e se o filtro deve consultar o servidor.
5. Registrar versão e evidência; verificações planejadas não recebem resultado de execução.

### CT-RF39 a CT-RF41 — próximos testes

1. CT-RF39: cadastrar modalidade com nome e descrição simples e status Ativo; conferir mensagem, registro e status na listagem; recarregar para conferir persistência; testar nome vazio, duplicado e limites de tamanho.
2. CT-RF40: acionar a lixeira de uma turma ativa e de uma modalidade com turmas vinculadas; conferir confirmação, mensagem, listagem sob os filtros "Ativo" e "Inativo", efeito sobre as turmas e persistência; confirmar a regra de exclusão com o produto.
3. CT-RF41 / BUG-020: enviar o formulário de Turma vazio, depois preenchido sem a modalidade, uma combinação por vez; conferir mensagens, foco e rede (nenhuma requisição de criação indevida); testar horário de término igual ou anterior ao de início; enviar a turma válida e conferir criação e persistência.
4. Registrar versão e evidência; verificações planejadas não recebem resultado de execução.

### CT-RF42 a CT-RF45 — próximos testes

1. CT-RF42: Confirmar a regra de saque e reexecutar com saldo conhecido, capturando corpo e resposta; testar valor acima do saldo e valor inválido.
2. CT-RF43: Usar como regressão; outros métodos, dados inválidos, link gerado e presença da cobrança em Transações recentes exigem execuções adicionais.
3. CT-RF44: Confirmar a faixa do campo de dias e a mensagem de salvamento; reexecutar com recarga, Cancelar e valores limite.
4. CT-RF45 / BUG-021: Reproduzir com conta de movimentação conhecida, comparar períodos e capturar corpo e resposta de recebiveis, transacoes e pagarme.
5. Registrar versão e evidência; verificações planejadas não recebem resultado de execução.

### CT-RF46 a CT-RF49 — próximos testes

1. CT-RF46: Usar como regressão; combinação de critérios, resultado vazio, filtros de status e recorrência e a regra de correspondência do código exigem execuções adicionais.
2. CT-RF47: Reproduzir capturando as duas requisições de criação e conferir a quantidade de registros após recarga; confirmar a regra do código.
3. CT-RF48: Usar como regressão; Cancelar, despesa com vínculos, natureza da exclusão e persistência após recarga exigem execuções adicionais.
4. CT-RF49: Usar como regressão; edição de nome, valor e status, Cancelar, pré-preenchimento da recorrência e persistência após recarga exigem execuções adicionais.
5. Registrar versão e evidência; verificações planejadas não recebem resultado de execução.

### CT-RF50 a CT-RF56 — próximos testes

1. CT-RF50: Usar como regressão; conferir com a lista de matrículas e exercitar filtros e período sem registros.
2. CT-RF51 / BUG-022: Comparar com o módulo Contas a Receber e reexecutar com valores conhecidos, Detalhado e outros status.
3. CT-RF52: Conferir as contas pagas do período no módulo e reexecutar com um período que contenha pagamentos.
4. CT-RF53 / BUG-023: Investigar a geração com logs do servidor e retestar com e sem registros no período, comparando com os relatórios que abrem.
5. CT-RF54 / BUG-023: Investigar a geração com logs do servidor e retestar com e sem registros no período, comparando com os relatórios que abrem.
6. CT-RF55 / BUG-023: Investigar a geração com logs do servidor e retestar com e sem registros no período, comparando com os relatórios que abrem.
7. CT-RF56 / BUG-023: Investigar a geração com logs do servidor e retestar com e sem registros no período, comparando com os relatórios que abrem.
8. Registrar versão e evidência; verificações planejadas não recebem resultado de execução.

### CT-RF57 — próximos testes

1. CT-RF57 / BUG-024: Investigar o HTTP 500 com logs do servidor e os vínculos do grupo de código 1, em conjunto com o BUG-016 (mesmo endpoint e mensagem para grupos musculares); corrigir e retestar os cenários permitido e impedido.
2. Confirmar o texto do diálogo de erro apresentado após a falha, não capturado visualmente nesta revisão.
3. Verificar a persistência do registro após recarga da página e documentar o cadastro de grupo observado na mesma gravação em cenário próprio.

### CT-RF58 — próximos testes

1. CT-RF58 / BUG-025: Investigar a rotina de edição do grupo (`/api/edita/grupo/{id}`) quanto ao tratamento do campo status; corrigir e retestar a edição de cada campo isoladamente, incluindo a reativação (Inativo → Ativo).
2. Verificar se o mesmo padrão ocorre em outros grupos e na entidade grupo muscular.
3. Investigar o descompasso observado entre o cabeçalho HTTP `data` e o campo `updated_at` da resposta, sem relação confirmada com o defeito de status.

### CT-RF59 — próximos testes

1. CT-RF59 / BUG-032: Investigar as rotinas de servidor de `/api/anamnese/aplicar/{id}` e `/api/anamnese/rascunho/{id}` com acesso a logs, em conjunto com o BUG-016 e o BUG-024 (mesma mensagem genérica); corrigir e retestar o cadastro completo de uma anamnese.
2. Confirmar se os dois modelos de anamnese exercitados (`modelo_id` 3 e 5) têm alguma particularidade de configuração relevante para o erro.
3. Verificar se as tentativas de salvar rascunho afetaram o mesmo registro ou criaram registros distintos no backend.

---

## 🚦 9. Critérios de entrada, saída e aceitação

**Entrada:** ambiente acessível, opção visível e ferramentas de captura disponíveis. Para Perfil, sessão válida e conta de teste com dados conhecidos. Para Clientes, sessão válida, empresa identificada, regras dos filtros confirmadas e base com resultados esperados por combinação. Para o reteste, correção disponibilizada em uma versão identificável.

**Saída da execução:** caso executado e resultado documentado com evidências. A execução reprovada pode ser encerrada com o defeito aberto.

**Entrada e aprovação do login:** página acessível, conta de teste com credenciais válidas e acesso ao painel, sem sessão autenticada no início. Aprovar o CT-RF04_loginComSucesso quando o envio autenticar o usuário, navegar para `/dashboard` e exibir o menu e resumo da academia, com senha mascarada no formulário. A aprovação se limita a esse fluxo positivo.

**Aceitação da correção:** todos os critérios do respectivo caso atendidos e reteste documentado. BUG-001 a BUG-010 permanecem abertos até a confirmação de suas correções. BUG-011–BUG-031 aguardam triagem e confirmação funcional antes do encaminhamento de correção. A aprovação do CT-RF01 não comprova a recuperação completa da senha; a do CT-RF02_ERRO não comprova persistência de alterações no perfil. Para CT-RF03, cada combinação deve incluir todos os clientes esperados e excluir os incompatíveis, com a matriz executada e o estado vazio validado.

---

## ⏱️ 10. Cronograma e dependências

| Atividade | Situação | Data ou condição |
| --- | --- | --- |
| Análise documental do CT-RF01 | Registrada | 10/11/2026. |
| Análise documental de Perfil e Clientes | Registrada | 12/11/2026. |
| Padronização dos documentos | Realizada | 13/11/2026. |
| Análise do Jam e inclusão do CT-RF04_loginComSucesso | Realizada; aprovado conforme a gravação | 13/11/2026, sem nova execução no sistema. |
| Inclusão documental de CT-RF05–CT-RF20 e cópia dos 16 vídeos | Realizada | 14/11/2026; revisão das evidências já consultadas, sem nova execução. |
| Inclusão documental de CT-RF21 / RF21 / BUG-010 | Realizada | 15/11/2026; relato original, quadros e diagnósticos do Jam, sem nova execução. |
| Integração de CT-RF22–CT-RF25 / RF22–RF25 | Realizada | 15/11/2026; sem nova execução; BUG-011/012 em triagem. |
| Integração de CT-RF26–CT-RF28 / RF26–RF28 | Realizada | 15/11/2026; sem nova execução; BUG-013–BUG-015 em triagem. |
| Integração de CT-RF29–CT-RF33 / RF29–RF33 | Realizada | 15/11/2026; sem nova execução; BUG-016 e BUG-017 em triagem. |
| Integração de CT-RF35 / RF35 | Realizada | 15/11/2026; sem nova execução; BUG-019 em triagem. |
| Integração de CT-RF38 / RF38 | Realizada | 15/11/2026; sem nova execução; sem defeito no fluxo gravado. |
| Integração de CT-RF39–CT-RF41 / RF39–RF41 | Realizada | 15/11/2026; sem nova execução; BUG-020 em triagem. |
| Integração de CT-RF42–CT-RF56 / RF42–RF56 | Realizada | 15/11/2026; sem nova execução; BUG-021 a BUG-023 em triagem. |
| Integração de CT-RF57 / RF57 | Realizada | 15/11/2026; sem nova execução; BUG-024 em triagem. |
| Integração de CT-RF58 / RF58 | Realizada | 15/11/2026; sem nova execução; BUG-025 em triagem. |
| Integração de CT-RF59 / RF59 | Realizada | 15/11/2026; sem nova execução; BUG-032 em triagem. |
| Confirmação da regra de saque, da faixa do campo de dias, da duplicidade de criação e dos relatórios sem dados | Pendente | RF42, RF44, RF47 e RF52; depende do responsável pelo produto. |
| Confirmação da regra de exclusão e da obrigatoriedade da modalidade | Pendente | RF40 e RF41; depende do responsável pelo produto. |
| Confirmação de código, operação de edição e imagem persistida | Pendente | RF22, RF24 e RF25; depende de regra e nova evidência. |
| Demonstração da lógica combinada de filtros e do estado neutro de imagem | Pendente | RF33 e RF30; depende de caso com critérios contraditórios e de definição do produto. |
| Confirmação das regras de CT-RF08/11/13/16 | Pendente | Responsável pelo produto; sem data definida. |
| Investigação e correção dos defeitos | Pendente | Depende da equipe responsável pela aplicação; sem data definida. |
| Execução dos retestes | Pendente | Após correção em versão identificável e preparação dos dados. |
| Atualização dos resultados e encerramento | Pendente | Após reteste e atendimento aos critérios de aceitação. |

## 🐞 11. Gestão de defeitos

Os defeitos são registrados no [relatório de bugs](Relatorio-de-Bugs.md), com identificação, severidade, prioridade, pré-condições, reprodução, resultado esperado e obtido, impacto e evidências. Hipóteses técnicas permanecem identificadas até a confirmação no código.

Há dez defeitos abertos (BUG-001 a BUG-010) e vinte e dois em triagem (BUG-011 a BUG-032). Os dois casos de contagem e filtro financeiro (CT-RF09 e CT-RF10) compartilham BUG-005 e os quatro relatórios vazios (CT-RF53 a CT-RF56) compartilham BUG-023; por isso trinta e seis casos reprovados correspondem a trinta e dois defeitos. CT-RF08, CT-RF11, CT-RF13, CT-RF16, CT-RF25, CT-RF40, CT-RF42, CT-RF44, CT-RF47 e CT-RF52 permanecem a validar, sem defeito confirmado. O endpoint e a mensagem genérica do BUG-024 (exclusão de grupo) coincidem com os do BUG-016 (exclusão de grupo muscular) e do BUG-031 (exclusão de colaborador), o que sugere causa comum a confirmar na correção. O BUG-025 (edição de grupo não persiste o status), observado na mesma gravação do BUG-024, é um defeito de natureza distinta — sucesso retornado sem persistência — e não guarda relação de causa confirmada com os BUG-016/024. O BUG-032 (cadastro de anamnese) repete a mesma mensagem genérica dos BUG-016/024/031 em ambas as rotas de gravação (aplicar e rascunho), em dois modelos e três respostas diferentes, sem causa determinada. BUG-026 a BUG-030 (validações de Colaboradores) registram atualização aceita com HTTP 200 e sem validação visível, pendentes de confirmação do corpo da requisição. Após a correção, atualizar o caso, o relatório dos testes e o defeito com as evidências da versão retestada. As severidades e prioridades dos novos defeitos são propostas para triagem.

---

## ⚠️ 12. Riscos e limitações do ambiente

| ID | Risco | Impacto | Mitigação |
|---|---|---|---|
| R01 | Fluxo de recuperação não abre | Impede testar as etapas seguintes | Registrar BUG-001; retestar a abertura após a correção |
| R02 | Captura de rede desativada ou filtrada | Ausência aparente de requisições pode levar a diagnóstico incorreto | Confirmar captura ativa, remover filtros e correlacionar rede com o comportamento visual |
| R03 | Evidências obtidas em versões diferentes | Resultados podem não ser reproduzíveis na versão escolhida | Registrar URL e versão em cada execução |
| R04 | Campos do perfil não renderizados | Impede visualizar e interagir com os dados | Registrar BUG-002 e retestar após correção |
| R05 | Cadastro real da conta não disponível para comparação | Limita a validação dos valores exibidos | Preparar conta de teste com dados conhecidos |
| R06 | Domínios, resolução ou zoom diferentes entre evidências | Pode alterar comportamento e aparência | Manter os ambientes identificados por caso e registrar condições do reteste |
| R07 | Atributos e vínculos dos clientes desconhecidos | Impede comprovar a compatibilidade de cada resultado com os filtros | Preparar base de referência e conferir todos os critérios por cliente |
| R08 | Contrato, valores ou IDs dos filtros não confirmados | Pode gerar teste com parâmetros inválidos e diagnóstico incorreto | Validar contrato, regras e correspondência entre rótulos e IDs antes do reteste |
| R09 | Filtragem local sobre dados parciais | Pode omitir clientes válidos de outras páginas | Confirmar a arquitetura e conferir completude considerando eventual paginação |
| R10 | Jam indisponível e rede descrita apenas no relato | Limita a conferência independente do payload e da cronologia do CT-RF03 | Preservar a origem informada e coletar nova evidência de rede sem autenticação no reteste |
| R11 | Regras de encargos, indicadores ou remoção não definidas | Pode gerar falso defeito ou falsa aprovação | Confirmar decisões de produto para CT-RF08/11/13/16 antes de conclusão definitiva |
| R12 | Tratar revisão de vídeo como nova execução | Superestima a cobertura e pode fechar defeitos sem reteste | Manter a origem e os limites por cenário; exigir nova evidência para reteste |

---

## 📁 13. Entregáveis e documentos associados

Os entregáveis são a análise RF01–RF35, RF38–RF56, RF57, RF58 e RF59, este plano, os 57 cenários BDD, as evidências disponíveis e os relatórios atualizados. CT-RF21 possui relato original, link do Jam, quadros, cronologia, requisição/resposta sem autenticação e metadados locais; o vídeo permanece no Jam. Os vídeos e demais evidências anteriores citados nos documentos de 14/11/2026 não estavam nesta cópia do repositório em 15/11/2026; consultar o índice de evidências para a disponibilidade. Dezessete casos estão aprovados no alcance das evidências; trinta reprovados aguardam reteste, incluindo CT-RF22/24/26/27/28/29/30/35/41/45/51/53/54/55/56/57/58/59 em triagem, e dez a validar dependem de regra/contexto ou persistência. CT-RF23–25, CT-RF35 e CT-RF38–CT-RF56 possuem pasta local com resumo, cronologia e origem (CT-RF35 e CT-RF38–CT-RF56 incluem também capturas extraídas do Jam e hashes; CT-RF50–CT-RF56 incluem os PDFs baixados); os vídeos permanecem no Jam. CT-RF29–CT-RF33, CT-RF57, CT-RF58 e CT-RF59 têm como fonte gravações únicas, cujos painéis foram lidos diretamente; as pastas locais de evidências desses casos ainda não foram criadas.

- [Análise de requisitos](Analise%20de%20requisitos.md)
- [Caso CT-RF01](Cenario_Teste/CT-RF01_Esqueci-senha.md)
- [Caso CT-RF02_ERRO](Cenario_Teste/CT-RF02_ERRO.md)
- [Caso CT-RF03](Cenario_Teste/CT-RF03_FILTRO_TelaClientes.md)
- [Caso CT-RF04_loginComSucesso](Cenario_Teste/CT-RF04_loginComSucesso.md)
- [Evidências do login com sucesso](Evidencias/CT-RF04_loginComSucesso/README.md)
- [Evidências e limites do CT-RF03](Evidencias/CT-RF03_Filtros_Clientes/README.md)
- [Relatório dos testes](Relatorio%20dos%20testes.md)
- [Relatório de bugs](Relatorio-de-Bugs.md)

- [Caso CT-RF35](Cenario_Teste/CT-RF35_Cadastro_Objetivo_Treino.md)
- [Evidências do CT-RF35](Evidencias/CT-RF35_Cadastro_Objetivo_Treino/README.md)
- [Caso CT-RF38](Cenario_Teste/CT-RF38_Cadastro_Categoria_Codigo_Automatico.md)
- [Evidências do CT-RF38](Evidencias/CT-RF38_Cadastro_Categoria_Codigo_Automatico/README.md)
- [Caso CT-RF39](Cenario_Teste/CT-RF39_Cadastro_Modalidade.md) e [evidências](Evidencias/CT-RF39_Cadastro_Modalidade/README.md)
- [Caso CT-RF40](Cenario_Teste/CT-RF40_Exclusao_Turmas_Modalidades.md) e [evidências](Evidencias/CT-RF40_Exclusao_Turmas_Modalidades/README.md)
- [Caso CT-RF41](Cenario_Teste/CT-RF41_Cadastro_Turma_Sem_Modalidade.md) e [evidências](Evidencias/CT-RF41_Cadastro_Turma_Sem_Modalidade/README.md)
- [Caso CT-RF42](Cenario_Teste/CT-RF42_Solicitacao_Saque_PagarMe.md) e [evidências](Evidencias/CT-RF42_Solicitacao_Saque_PagarMe/README.md)
- [Caso CT-RF43](Cenario_Teste/CT-RF43_Criacao_Cobranca_PagarMe.md) e [evidências](Evidencias/CT-RF43_Criacao_Cobranca_PagarMe/README.md)
- [Caso CT-RF44](Cenario_Teste/CT-RF44_Configuracoes_Home_Salvamento.md) e [evidências](Evidencias/CT-RF44_Configuracoes_Home_Salvamento/README.md)
- [Caso CT-RF45](Cenario_Teste/CT-RF45_Painel_PagarMe_Periodo.md) e [evidências](Evidencias/CT-RF45_Painel_PagarMe_Periodo/README.md)
- [Caso CT-RF46](Cenario_Teste/CT-RF46_Filtros_Despesas_Fixas.md) e [evidências](Evidencias/CT-RF46_Filtros_Despesas_Fixas/README.md)
- [Caso CT-RF47](Cenario_Teste/CT-RF47_Cadastro_Despesa_Fixa.md) e [evidências](Evidencias/CT-RF47_Cadastro_Despesa_Fixa/README.md)
- [Caso CT-RF48](Cenario_Teste/CT-RF48_Exclusao_Despesa_Fixa.md) e [evidências](Evidencias/CT-RF48_Exclusao_Despesa_Fixa/README.md)
- [Caso CT-RF49](Cenario_Teste/CT-RF49_Edicao_Despesa_Fixa.md) e [evidências](Evidencias/CT-RF49_Edicao_Despesa_Fixa/README.md)
- [Caso CT-RF50](Cenario_Teste/CT-RF50_Relatorio_Matriculas.md) e [evidências](Evidencias/CT-RF50_Relatorio_Matriculas/README.md)
- [Caso CT-RF51](Cenario_Teste/CT-RF51_Relatorio_Contas_Receber.md) e [evidências](Evidencias/CT-RF51_Relatorio_Contas_Receber/README.md)
- [Caso CT-RF52](Cenario_Teste/CT-RF52_Relatorio_Contas_Pagar_Pagas.md) e [evidências](Evidencias/CT-RF52_Relatorio_Contas_Pagar_Pagas/README.md)
- [Caso CT-RF53](Cenario_Teste/CT-RF53_Relatorio_Avaliacoes_Vazio.md) e [evidências](Evidencias/CT-RF53_Relatorio_Avaliacoes_Vazio/README.md)
- [Caso CT-RF54](Cenario_Teste/CT-RF54_Relatorio_Clientes_Vazio.md) e [evidências](Evidencias/CT-RF54_Relatorio_Clientes_Vazio/README.md)
- [Caso CT-RF55](Cenario_Teste/CT-RF55_Relatorio_Colaboradores_Vazio.md) e [evidências](Evidencias/CT-RF55_Relatorio_Colaboradores_Vazio/README.md)
- [Caso CT-RF56](Cenario_Teste/CT-RF56_Relatorio_Caixas_Vazio.md) e [evidências](Evidencias/CT-RF56_Relatorio_Caixas_Vazio/README.md)
- [Caso CT-RF57](Cenario_Teste/CT-RF57_Exclusao_Grupo.md)
- [Caso CT-RF58](Cenario_Teste/CT-RF58_Edicao_Grupo.md)
- [Caso CT-RF59](Cenario_Teste/CT-RF59_Cadastro_Anamnese.md)
- [Caso CT-RF60](Cenario_Teste/CT-RF60_Gestao_Modelos_Anamnese.md)
- [Caso CT-RF65](Cenario_Teste/CT-RF65_Data_Nascimento_Futura_Colaborador.md)
- [Caso CT-RF66](Cenario_Teste/CT-RF66_Data_Nascimento_Obrigatoria_Colaborador.md)
- [Caso CT-RF67](Cenario_Teste/CT-RF67_CREF_Formato_Colaborador.md)
- [Caso CT-RF68](Cenario_Teste/CT-RF68_Edicao_Colaborador_Campo_Obrigatorio_Vazio.md)
- [Caso CT-RF69](Cenario_Teste/CT-RF69_Funcao_Duplicada_Colaborador.md)
- [Caso CT-RF70](Cenario_Teste/CT-RF70_Exclusao_Colaborador_Erro_500.md)
- [Índice dos 64 cenários](Cenario_Teste/README.md)
- [Índice das evidências e dos Jams](Evidencias/README.md)
- [Manifesto de integridade dos novos arquivos](Evidencias/manifesto_sha256.json)

---

## Inclusão CT-RF65 a CT-RF70 — Colaboradores

| Caso | Técnica | Resultado | Reteste mínimo |
| --- | --- | --- | --- |
| [CT-RF65](Cenario_Teste/CT-RF65_Data_Nascimento_Futura_Colaborador.md) | Valor limite / data futura | Reprovado — BUG-026 | Data passada, atual e futura; confirmar persistência. |
| [CT-RF66](Cenario_Teste/CT-RF66_Data_Nascimento_Obrigatoria_Colaborador.md) | Campo obrigatório | Reprovado — BUG-027 | Vazio, apagado, espaços e valor válido. |
| [CT-RF67](Cenario_Teste/CT-RF67_CREF_Formato_Colaborador.md) | Partição de equivalência / formato | Reprovado — BUG-028 | Exemplos válidos e inválidos após confirmar a regra do CREF. |
| [CT-RF68](Cenario_Teste/CT-RF68_Edicao_Colaborador_Campo_Obrigatorio_Vazio.md) | Obrigatoriedade campo a campo | Reprovado — BUG-029 | Cada obrigatório vazio isoladamente e em conjunto. |
| [CT-RF69](Cenario_Teste/CT-RF69_Funcao_Duplicada_Colaborador.md) | Duplicidade / repetição | Reprovado — BUG-030 | Clique duplo, repetição sequencial e concorrência. |
| [CT-RF70](Cenario_Teste/CT-RF70_Exclusao_Colaborador_Erro_500.md) | Exclusão permitida e impedida | Reprovado — BUG-031 | Registro sem vínculos e com cada vínculo conhecido. |

**Ambiente gravado:** `sifit.centrion.com.br`, backend `backendsifit.centrion.com.br`, Edge/Chromium 157 em Windows 11 conforme cabeçalhos; versão da aplicação e zoom não confirmados. As gravações ocorreram entre 22:06 e 22:13 BRT de 15/11/2026.

**Critério de saída:** seis casos retestados em versão identificada, sem persistência inválida ou duplicada e sem HTTP 500.

---

## Inclusão CT-RF60 — Modelos de Anamnese

| Caso | Técnica | Resultado | Reteste mínimo |
| --- | --- | --- | --- |
| [CT-RF60](Cenario_Teste/CT-RF60_Gestao_Modelos_Anamnese.md) | Fluxo exploratório / CRUD completo | Aprovado conforme a gravação | Repetir busca, filtro, cadastro com perguntas do banco, edição e exclusão em versão identificada, confirmando os corpos de requisição e resposta. |

**Ambiente gravado:** `sifit.centrion.com.br`, backend `backendsifit.centrion.com.br`, Chrome 157 em Windows 11 conforme cabeçalhos; versão da aplicação e zoom não confirmados. A gravação ocorreu às 23h34 BRT de 15/11/2026.

**Critério de saída:** caso retestado em versão identificada, com os corpos de requisição e resposta capturados, mantendo o resultado aprovado sem HTTP 4xx ou 5xx.

---

[← Início](../README.md) · [Cenários de teste](Cenario_Teste/) · [Evidências de Clientes](Evidencias/CT-RF03_Filtros_Clientes/README.md)
