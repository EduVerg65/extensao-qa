# 📊 Relatório de Testes — SIFIT

**Escopo:** CT-RF01 — Recuperação de senha; CT-RF02_ERRO — Perfil; CT-RF03 — Filtros da página Clientes; CT-RF04_loginComSucesso — Login.

**Datas das gravações do Jam:** CT-RF01 em 23/10/2026; CT-RF02_ERRO em 22/10/2026 às 21:45 BRT; CT-RF03 não confirmada; CT-RF04_loginComSucesso em 13/11/2026.

**Data da revisão documental:** 13/11/2026, com inclusão do login. Resultados anteriores preservados das revisões de 10/11 e 12/11/2026.

**Origem do resultado:** análise de evidências fornecidas; sem nova execução no sistema nesta revisão.

**Padronização documental:** 13/11/2026, preservando as datas e os resultados das análises anteriores.

---

## 📊 1. Resumo dos resultados

O caso **CT-RF01** foi classificado como **reprovado**: a opção "Esqueci minha senha" não inicia o fluxo de recuperação. O Jam mostra cliques repetidos e permanência na tela de login; a consulta aos registros da captura retorna **0 requisições de rede** e **0 mensagens de erro no console**.

O **CT-RF02_ERRO** também foi classificado como **reprovado**: o perfil apresenta conteúdo fictício, textos em inglês, seções sem campos visíveis e layout desconfigurado. A classificação se apoia no relato, na captura, no HTML fornecido e na consulta ao Jam. A causa técnica não foi confirmada no código.

O **CT-RF03** foi classificado como **reprovado conforme o relato**: a busca com filtros combinados mantém clientes incompatíveis e resultados praticamente iguais ao alternar a situação financeira. As capturas foram fornecidas como apoio; não mostram todos os valores completos nem os vínculos de cada cliente. O conteúdo do Jam não pôde ser consultado diretamente nesta revisão, e a causa não foi confirmada no código.

O **CT-RF04_loginComSucesso** foi classificado como **aprovado conforme a gravação**: o usuário preenche credenciais válidas, clica em Entrar e acessa `/dashboard`. As chamadas de login e verificação da sessão retornam HTTP 200; os quadros mostram o menu e o resumo da academia após a autenticação. Não houve nova execução no sistema.

| Casos documentados | Aprovados | Reprovados | Bugs abertos | Retestes pendentes |
| :---: | :---: | :---: | :---: | :---: |
| 4 | 1 | 3 | 3 | 3 |

As contagens representam os casos documentados com base nas fontes indicadas, sem novas execuções nesta revisão. As nove variações planejadas para o reteste do CT-RF03 não foram executadas e não são contabilizadas como testes adicionais realizados.

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

---

## 🐞 3. Resumo dos bugs reportados

| ID | Funcionalidade | Severidade | Prioridade | Status |
| --- | --- | --- | --- | --- |
| [BUG-001](Relatorio-de-Bugs.md#bug-001--link-esqueci-minha-senha-não-executa-nenhuma-ação) | Início da recuperação de senha | Alta | Alta | Aberto; reteste pendente. |
| [BUG-002](Relatorio-de-Bugs.md#bug-002--perfil-com-dados-fictícios-campos-ausentes-e-layout-desconfigurado) | Dados e layout do perfil | Alta, proposta | Alta, proposta | Aberto; reteste pendente. |
| [BUG-003](Relatorio-de-Bugs.md#bug-003--filtros-combinados-da-página-clientes-não-restringem-a-listagem) | Filtros combinados de Clientes | Alta, proposta | Alta, proposta | Aberto; reteste pendente. |
| [BUG-004](Relatorio-de-Bugs.md#bug-004) | Exportar não oferece retorno visível no financeiro | Média, proposta | Média, proposta | Aberto; reteste pendente. |

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

---

[← Início](../README.md) · [Cenários de teste](Cenario_Teste/) · [Evidências de Clientes](Evidencias/CT-RF03_Filtros_Clientes/README.md)
