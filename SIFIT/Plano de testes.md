# 🧪 Plano de Testes — SIFIT

**Atualização:** 13/11/2026 — inclusão do login com sucesso.

**Padronização documental:** 13/11/2026, com resultados e pendências preservados.

**Escopo:** CT-RF01 — Recuperação de senha; CT-RF02_ERRO — Perfil; CT-RF03 — Filtros da página Clientes; CT-RF04_loginComSucesso — Login.

## 📌 1. Identificação

| Item | Definição |
| --- | --- |
| Projeto | SIFIT — Sistema de gestão de academias. |
| Tipo de teste | Funcional manual, com análise exploratória e de evidências. |
| Versão avaliada | Não confirmada; registrar por caso no reteste. |
| Funcionalidades | Recuperação de senha, Perfil, filtros da página Clientes e login com credenciais válidas. |
| Situação | Quatro casos documentados: um aprovado conforme o Jam e três reprovados; três defeitos abertos com retestes pendentes. |

---

## 🎯 2. Objetivo

Verificar o login com credenciais válidas e acesso ao dashboard, o início da recuperação de acesso, a apresentação do perfil do usuário autenticado e a aplicação simultânea dos filtros de Clientes, mantendo a rastreabilidade entre requisitos, casos de teste, evidências e defeitos.

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

## 📋 7. Casos de teste e situação

| Requisito | Caso de teste | Tipo | Resultado nas evidências | Defeito | Próxima ação |
| --- | --- | --- | --- | --- | --- |
| [RF01](Analise%20de%20requisitos.md#rf01--iniciar-recuperação-de-senha) | [CT-RF01 — Acionar "Esqueci minha senha"](Cenario_Teste/CT-RF01_Esqueci-senha.md) | Funcional / fluxo positivo, com análise exploratória de rede | Reprovado | [BUG-001](Relatorio-de-Bugs.md#bug-001--link-esqueci-minha-senha-não-executa-nenhuma-ação) | Corrigir e retestar. |
| [RF02](Analise%20de%20requisitos.md#rf02--exibir-perfil-do-usuário-autenticado) | [CT-RF02_ERRO — Exibir Perfil](Cenario_Teste/CT-RF02_ERRO.md) | Funcional / interface, com análise do DOM e evidências | Reprovado | [BUG-002](Relatorio-de-Bugs.md#bug-002--perfil-com-dados-fictícios-campos-ausentes-e-layout-desconfigurado) | Corrigir e retestar. |
| [RF03](Analise%20de%20requisitos.md#rf03--pesquisar-clientes-com-filtros-combinados) | [CT-RF03 — Filtrar Clientes](Cenario_Teste/CT-RF03_FILTRO_TelaClientes.md) | Funcional / filtros combinados, com análise de integração e evidências | Reprovado conforme o relato; sem nova execução | [BUG-003](Relatorio-de-Bugs.md#bug-003--filtros-combinados-da-página-clientes-não-restringem-a-listagem) | Investigar a causa, corrigir e executar a matriz de reteste. |
| [RF04](Analise%20de%20requisitos.md#rf04--autenticar-usuário-com-credenciais-válidas) | [CT-RF04_loginComSucesso](Cenario_Teste/CT-RF04_loginComSucesso.md) | Funcional / fluxo positivo de autenticação | Aprovado conforme a gravação; sem nova execução | Nenhum identificado no fluxo avaliado | Utilizar como regressão em futuras versões. |
| [RF05](Analise%20de%20requisitos.md#rf05) | [CT-RF05](Cenario_Teste/CT-RF05_Login_SenhaIncorreta.md) | Funcional manual / regressão | Aprovado conforme a gravação | Nenhum no fluxo avaliado | Usar como regressão de autenticação negativa; preparar conta conhecida e repetir após alterações no login. |

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

## 🚦 9. Critérios de entrada, saída e aceitação

**Entrada:** ambiente acessível, opção visível e ferramentas de captura disponíveis. Para Perfil, sessão válida e conta de teste com dados conhecidos. Para Clientes, sessão válida, empresa identificada, regras dos filtros confirmadas e base com resultados esperados por combinação. Para o reteste, correção disponibilizada em uma versão identificável.

**Saída da execução:** caso executado e resultado documentado com evidências. A execução reprovada pode ser encerrada com o defeito aberto.

**Entrada e aprovação do login:** página acessível, conta de teste com credenciais válidas e acesso ao painel, sem sessão autenticada no início. Aprovar o CT-RF04_loginComSucesso quando o envio autenticar o usuário, navegar para `/dashboard` e exibir o menu e resumo da academia, com senha mascarada no formulário. A aprovação se limita a esse fluxo positivo.

**Aceitação da correção:** todos os critérios do respectivo caso atendidos e reteste documentado. BUG-001, BUG-002 e BUG-003 permanecem abertos até a confirmação de suas correções. A aprovação do CT-RF01 não comprova a recuperação completa da senha; a do CT-RF02_ERRO não comprova persistência de alterações no perfil. Para CT-RF03, cada combinação deve incluir todos os clientes esperados e excluir os incompatíveis, com a matriz executada e o estado vazio validado.

---

## ⏱️ 10. Cronograma e dependências

| Atividade | Situação | Data ou condição |
| --- | --- | --- |
| Análise documental do CT-RF01 | Registrada | 10/11/2026. |
| Análise documental de Perfil e Clientes | Registrada | 12/11/2026. |
| Padronização dos documentos | Realizada | 13/11/2026. |
| Análise do Jam e inclusão do CT-RF04_loginComSucesso | Realizada; aprovado conforme a gravação | 13/11/2026, sem nova execução no sistema. |
| Investigação e correção dos defeitos | Pendente | Depende da equipe responsável pela aplicação; sem data definida. |
| Execução dos retestes | Pendente | Após correção em versão identificável e preparação dos dados. |
| Atualização dos resultados e encerramento | Pendente | Após reteste e atendimento aos critérios de aceitação. |

## 🐞 11. Gestão de defeitos

Os defeitos são registrados no [relatório de bugs](Relatorio-de-Bugs.md), com identificação, severidade, prioridade, pré-condições, reprodução, resultado esperado e obtido, impacto e evidências. Hipóteses técnicas permanecem identificadas até a confirmação no código.

BUG-001, BUG-002 e BUG-003 permanecem abertos. Após a correção, atualizar o caso, o relatório dos testes e o defeito com as evidências da versão retestada.

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

---

## 📁 13. Entregáveis e documentos associados

Os entregáveis são a análise de requisitos, este plano, os quatro cenários, as evidências disponíveis e os relatórios de bugs e resultados. O login possui evidência de aprovação no Jam; as evidências de aprovação dos demais casos serão acrescentadas após os retestes.

- [Análise de requisitos](Analise%20de%20requisitos.md)
- [Caso CT-RF01](Cenario_Teste/CT-RF01_Esqueci-senha.md)
- [Caso CT-RF02_ERRO](Cenario_Teste/CT-RF02_ERRO.md)
- [Caso CT-RF03](Cenario_Teste/CT-RF03_FILTRO_TelaClientes.md)
- [Caso CT-RF04_loginComSucesso](Cenario_Teste/CT-RF04_loginComSucesso.md)
- [Evidências do login com sucesso](Evidencias/CT-RF04_loginComSucesso/README.md)
- [Evidências e limites do CT-RF03](Evidencias/CT-RF03_Filtros_Clientes/README.md)
- [Relatório dos testes](Relatorio%20dos%20testes.md)
- [Relatório de bugs](Relatorio-de-Bugs.md)

---

[← Início](../README.md) · [Cenários de teste](Cenario_Teste/) · [Evidências de Clientes](Evidencias/CT-RF03_Filtros_Clientes/README.md)
