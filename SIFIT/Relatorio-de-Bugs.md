# 🐞 Relatório de Bugs — SIFIT

**Escopo:** CT-RF01 — Recuperação de senha; CT-RF02_ERRO — Perfil; CT-RF03 — Filtros da página Clientes

**Ambientes:** CT-RF01 em https://sifitalfa.centrion.com.br/login; CT-RF02_ERRO em https://sifit.centrion.com.br/profile. CT-RF03: URL do frontend não confirmada; backend informado em `https://backendsifit.centrion.com.br/api/clientesPorNome/1`.

**Datas das gravações do Jam:** CT-RF01 em 23/10/2026; CT-RF02_ERRO em 22/10/2026 às 21:45 BRT; CT-RF03 não confirmada.

**Atualização documental:** 12/11/2026

**Padronização documental:** 13/11/2026, sem alteração do status dos defeitos.

## 📋 Resumo dos defeitos

| ID | Funcionalidade afetada | Severidade / prioridade | Status | Caso relacionado |
| --- | --- | --- | --- | --- |
| [BUG-001](#bug-001--link-esqueci-minha-senha-não-executa-nenhuma-ação) | Recuperação de senha | Alta / Alta | Aberto | [CT-RF01](Cenario_Teste/CT-RF01_Esqueci-senha.md) |
| [BUG-002](#bug-002--perfil-com-dados-fictícios-campos-ausentes-e-layout-desconfigurado) | Perfil do usuário | Alta / Alta, propostas | Aberto | [CT-RF02_ERRO](Cenario_Teste/CT-RF02_ERRO.md) |
| [BUG-003](#bug-003--filtros-combinados-da-página-clientes-não-restringem-a-listagem) | Filtros de Clientes | Alta / Alta, propostas | Aberto | [CT-RF03](Cenario_Teste/CT-RF03_FILTRO_TelaClientes.md) |

Todos os defeitos aguardam correção e reteste. As causas técnicas permanecem não confirmadas; o BUG-003 se apoia no relato e nas capturas fornecidos, com os limites registrados no caso.

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

[← Início](../README.md) · [Cenários de teste](Cenario_Teste/) · [Evidências de Clientes](Evidencias/CT-RF03_Filtros_Clientes/README.md)
