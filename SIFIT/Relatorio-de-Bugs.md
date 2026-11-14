# 🐞 Relatório de Bugs — SIFIT

**Escopo:** defeitos dos cenários CT-RF01–CT-RF20: recuperação, Perfil, Clientes, financeiro, período, tema, modalidades e categorias. Casos aprovados e pontos a validar permanecem no relatório dos testes.

**Ambientes:** CT-RF01 em https://sifitalfa.centrion.com.br/login; CT-RF02_ERRO em https://sifit.centrion.com.br/profile. CT-RF03: URL do frontend não confirmada; backend informado em `https://backendsifit.centrion.com.br/api/clientesPorNome/1`.

**Datas das gravações do Jam:** CT-RF01 em 23/10/2026; CT-RF02_ERRO em 22/10/2026 às 21:45 BRT; CT-RF03 não confirmada.

**Atualização documental:** 14/11/2026 — nove defeitos abertos (BUG-001 a BUG-009); seis registros novos. As análises anteriores de BUG-001 a BUG-003 foram preservadas.

**Padronização documental:** 13/11/2026, sem alteração do status dos defeitos.

**Caso aprovado incluído em 13/11/2026:** [CT-RF04_loginComSucesso](Cenario_Teste/CT-RF04_loginComSucesso.md), vinculado ao RF04, não gerou defeito para o fluxo avaliado. O [Jam de login](https://jam.dev/c/5e4a28be-4e80-43d3-9587-1b113723cc38) mostra acesso ao dashboard após autenticação. Essa aprovação não altera os três bugs existentes; resultados e limites constam no [relatório dos testes](Relatorio%20dos%20testes.md).

**Novas gravações:** 14/11/2026, Chrome 157.0.8103.51 / Windows 11, no domínio `sifit.centrion.com.br`. Cada cenário registra página, horário e limites. A inclusão é documental, sem nova execução ou reteste.

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

## Pontos a validar — sem defeito confirmado

| Caso | Questão pendente | Evidência |
| --- | --- | --- |
| [CT-RF08](Cenario_Teste/CT-RF08_Calculo_Cobranca.md) | Confirmar a origem dos R$ 20,83 além de principal e multa e a regra da mensagem; não registrar cálculo incorreto antes dessa validação. | [Jam](https://jam.dev/c/79b712ae-d9e0-4600-862f-fd3a278285ff) e [Evidências](Evidencias/CT-RF08_Calculo_Cobranca/README.md) |
| [CT-RF11](Cenario_Teste/CT-RF11_Metricas_Financeiro.md) | Confirmar os contratos dos cartões; a constância de totais globais não é suficiente para abrir outro defeito financeiro. | [Jam](https://jam.dev/c/4491c9e7-7e00-4063-91ce-8683e316df06) e [Evidências](Evidencias/CT-RF11_Metricas_Financeiro/README.md) |
| [CT-RF13](Cenario_Teste/CT-RF13_Codigos_Personais.md) | Confirmar a semântica da coluna Código; quatro linhas e total quatro não sustentam um defeito de quantidade. | [Jam](https://jam.dev/c/69330ca9-ef19-4ece-918f-31a460628016) e [Evidências](Evidencias/CT-RF13_Codigos_Personais/README.md) |
| [CT-RF16](Cenario_Teste/CT-RF16_Exclusao_Modalidade.md) | Confirmar a exclusão lógica e a nomenclatura da ação; registrar defeito apenas se houver divergência com a regra definida. | [Jam](https://jam.dev/c/0f55f76a-cd31-4cee-93da-23c13b1ba637) e [Evidências](Evidencias/CT-RF16_Exclusao_Modalidade/README.md) |

Esses quatro pontos não entram na contagem de nove bugs. O relato de numeração de personais não demonstrou diferença entre total e linhas; a inativação de modalidades pode ser exclusão lógica; encargos e métricas exigem regras explícitas.

---

[← Início](../README.md) · [Cenários de teste](Cenario_Teste/) · [Evidências de Clientes](Evidencias/CT-RF03_Filtros_Clientes/README.md)
