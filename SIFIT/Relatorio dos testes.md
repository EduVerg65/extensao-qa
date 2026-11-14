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
