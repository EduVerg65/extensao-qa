# 🐞 Relatório de Bugs — SIFIT

**Escopo:** defeitos de 73 casos documentados (CT-RF01–CT-RF35, CT-RF38–CT-RF56 e CT-RF85–CT-RF103): recuperação, Perfil, Clientes, financeiro, página inicial e dashboard, tema, modalidades, categorias, avaliações, exercícios, grupos musculares, objetivos de treino, SifitBox – Turmas, Pagar.me, configurações, despesas fixas, relatórios, prospecção de leads, contas a pagar, modelos de contrato e planos.

**Ambientes:** CT-RF01 em https://sifitalfa.centrion.com.br/login; CT-RF02_ERRO em https://sifit.centrion.com.br/profile. CT-RF03: URL do frontend não confirmada; backend informado em `https://backendsifit.centrion.com.br/api/clientesPorNome/1`.

**Datas das gravações do Jam:** CT-RF01 em 23/10/2026; CT-RF02_ERRO em 22/10/2026 às 21:45 BRT; CT-RF03 não confirmada.

**Atualização documental:** 15/11/2026 — 27 defeitos registrados: 10 abertos (BUG-001 a BUG-010) e 17 em triagem (BUG-011 a BUG-041). BUG-019 registra o HTTP 500 no cadastro de objetivo de treino e BUG-020 a ausência de retorno visível no cadastro de turma sem modalidade, ambos sem causa técnica confirmada. As análises anteriores foram preservadas.

**Padronização documental:** 13/11/2026, sem alteração do status dos defeitos.

**Caso aprovado incluído em 13/11/2026:** [CT-RF04_loginComSucesso](Cenario_Teste/CT-RF04_loginComSucesso.md), vinculado ao RF04, não gerou defeito para o fluxo avaliado. O [Jam de login](https://jam.dev/c/5e4a28be-4e80-43d3-9587-1b113723cc38) mostra acesso ao dashboard após autenticação. Essa aprovação não altera os três bugs existentes; resultados e limites constam no [relatório dos testes](Relatorio%20dos%20testes.md).

**Gravação de CT-RF99–CT-RF103:** 15/11/2026, Planos, 21:54 BRT, Chrome 157.0.8103.78 / Windows 11; uma única gravação; evidência e limites no BUG-041.

**Gravação de CT-RF96–CT-RF98:** 15/11/2026, Modelos de Contrato, 21:55 BRT, Chrome 157.0.8103.78 / Windows 11; uma única gravação; evidência e limites no BUG-040.

**Gravação de CT-RF91–CT-RF95:** 15/11/2026, Contas a Pagar, 21:58 BRT, Chrome 157.0.8103.78 / Windows 11; uma única gravação; evidência e limites no BUG-039.

**Gravação de CT-RF85–CT-RF90:** 15/11/2026, Prospecção, 21:52 BRT, Chrome 157.0.8103.78 / Windows 11; uma única gravação; evidência e limites no BUG-038.

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
| [BUG-038](#bug-038) | Telefone do lead aceita 30 dígitos sem máscara nem validação | Média / Média, propostas | Em triagem — regra do campo e validação no servidor não confirmadas | [CT-RF89](Cenario_Teste/CT-RF89_Telefone_Lead_Sem_Validacao.md) |
| [BUG-039](#bug-039) | Conta a pagar a colaborador é cadastrada sem colaborador informado | Alta / Alta, propostas | Em triagem — regra de obrigatoriedade e validação no servidor não confirmadas | [CT-RF92](Cenario_Teste/CT-RF92_Cadastro_Conta_Colaborador_Sem_Colaborador.md) |
| [BUG-040](#bug-040) | Listagem de modelos de contrato aparece vazia com 15 modelos retornados | Alta / Alta, propostas | Em triagem — causa de renderização não confirmada | [CT-RF98](Cenario_Teste/CT-RF98_Listagem_Modelos_Contrato_Vazia.md) |
| [BUG-041](#bug-041) | Cartão Ativos de Planos aumenta ao cadastrar e editar planos inativos | Média / Média, propostas | Em triagem — regra de cálculo do cartão não confirmada | [CT-RF102](Cenario_Teste/CT-RF102_Contador_Ativos_Planos.md) |

BUG-001–BUG-010 aguardam correção e reteste. BUG-011–BUG-041 aguardam confirmação das premissas e triagem antes do encaminhamento de correção. As causas técnicas permanecem não confirmadas; o BUG-003 se apoia no relato e nas capturas fornecidos, com os limites registrados no caso.

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

Esses treze pontos não entram na contagem de 27 defeitos registrados. BUG-011–BUG-041 são contabilizados separadamente como registros em triagem, com premissas, persistência ou validações técnicas ainda pendentes. O relato de numeração de personais não demonstrou diferença entre total e linhas; a inativação de modalidades pode ser exclusão lógica; encargos e métricas exigem regras explícitas.


**Exclusão de exercício:** CT-RF23 está aprovado no trecho consultado, com remoção e total 11 para 10; não gerou defeito adicional. Persistência e efeitos sobre vínculos permanecem como verificações complementares.

---

[← Início](../README.md) · [Cenários de teste](Cenario_Teste/) · [Evidências de Clientes](Evidencias/CT-RF03_Filtros_Clientes/README.md)
