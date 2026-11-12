## Cenário 2: Exibição da tela de Perfil

### Caso de Teste 02: Carregamento dos dados e do layout do perfil.

| ID | Descrição |
| --- | --- |
| **CT-RF02_ERRO** | Verificar se a opção Perfil apresenta os dados do usuário autenticado e os campos de Usuário, Documentos e Endereço em um layout organizado, conforme o padrão visual do SIFIT. |

| **Pré-condições** |
| --- |
| Estar autenticado no SIFIT com uma conta de teste e ter acesso à opção Perfil. |
| Conhecer os dados cadastrados da conta para compará-los com os dados exibidos no reteste. Os dados reais da conta não foram fornecidos nesta revisão. |
| Registrar URL, versão, navegador, resolução e zoom; preparar Network e Console antes de acessar o perfil para investigar o carregamento. |

| **Passos** |
| --- |
| **DADO** que estamos autenticados no SIFIT |
| **E** a opção Perfil está disponível no menu do usuário |
| **QUANDO** acessarmos a opção Perfil |
| **ENTÃO** a página deve apresentar os dados correspondentes à conta autenticada |
| **E** deve exibir corretamente os rótulos e campos das seções Usuário, Documentos e Endereço |
| **E** deve apresentar os campos editáveis conforme as permissões da conta |
| **E** deve usar textos em português e o padrão visual do sistema |
| **E** deve manter imagens, alinhamentos e conteúdo dentro da área útil da tela, sem rolagem horizontal indevida |

| **Critérios de aceitação** |
| --- |
| Nome, identificação e demais valores exibidos devem corresponder à conta autenticada; conteúdo fictício de demonstração não deve aparecer. |
| Todos os campos previstos nas seções Usuário, Documentos e Endereço devem estar visíveis, com rótulos legíveis e valores correspondentes ao cadastro, quando existentes. Ausência legítima de um dado não deve impedir a renderização do campo. |
| Os campos editáveis devem permitir interação conforme as permissões da conta. A persistência de alterações exige teste específico e não foi avaliada nesta evidência. |
| Os textos da interface devem estar em português, incluindo ações e seções. |
| A foto deve respeitar os limites do componente; o layout deve manter alinhamento e navegação sem transbordamento horizontal nas resoluções definidas para o reteste. |

| **Resultado obtido** |
| --- |
| O relato e o HTML fornecidos apresentam conteúdo de demonstração: “Hello Jesse”, “Jessica Jones”, “Bucharest, Romania”, “Connect”, “Message”, “Show more” e “About me”. |
| A captura fornecida mostra os títulos Usuário, Documentos e Endereço sem os respectivos campos visíveis, uma imagem fora de proporção e o botão “Edit profile”. |
| O HTML mantém tags como `<base-input>`, `<base-header>`, `<base-button>` e `<card>`. Nos trechos fornecidos, os campos de cadastro estão representados por `<base-input modelvalue="">` sem elementos `<input>` internos. Há um `<textarea>` nativo em About me com texto de demonstração. |
| O Jam registra navegação para `https://sifit.centrion.com.br/profile` por volta de 00:02 e novamente em 00:12. O quadro consultado em 00:05 mostra seções sem campos visíveis e uma barra horizontal na parte inferior da página gravada. |
| A visualização e a edição dos dados do perfil ficam comprometidas. Não houve tentativa de salvar alterações nem comparação com o cadastro real nesta revisão. |

| **Status e rastreabilidade** |
| --- |
| **Resultado:** Reprovado conforme o relato, a captura, o HTML e a gravação consultada. |
| **Requisito:** [RF02 — Exibir perfil do usuário autenticado](../Analise%20de%20requisitos.md#rf02--exibir-perfil-do-usuário-autenticado). |
| **Defeito associado:** [BUG-002](../Relatorio-de-Bugs.md#bug-002--perfil-com-dados-fictícios-campos-ausentes-e-layout-desconfigurado). |
| **Severidade / prioridade:** Alta / Alta, propostas pelo impacto na visualização e na edição do perfil. |
| **Ambiente da gravação:** `https://sifit.centrion.com.br/profile`; a aba Info do Jam apresenta `/configuracoes`, enquanto Actions identifica o acesso a `/profile`. |
| **Navegador / sistema / janela:** Chrome 155.0.8059.85 / Windows 11 (x86) / 1536 × 742, conforme Info do Jam. |
| **Data da gravação:** 22/10/2026 às 21:45 BRT. **Duração:** aproximadamente 15 segundos. **Revisão documental:** 12/11/2026. |
| **Reteste:** Pendente após a correção; não houve nova execução no sistema nesta revisão. |

### Análise do HTML

O [recorte do DOM fornecido](../Evidencias/CT-RF02_ERRO/recorte-dom.html) preserva trechos relevantes para a análise; não é o HTML integral nem uma implementação corrigida.

| Evidência no HTML | Interpretação e limite |
| --- | --- |
| `<h1 class="display-2 text-white">Hello Jesse</h1>` e nome Jessica Jones | Conteúdo de demonstração presente no DOM. Não comprova exposição de dados de outra conta real. |
| `<base-input ... modelvalue=""></base-input>` | Os trechos não contêm o controle nativo esperado para digitação. A captura confirma a ausência visual dos campos. |
| `<base-header>`, `<base-button>` e `<card>` mantidos no DOM | Indício de componentes não resolvidos ou tratados como elementos personalizados. O registro/importação dos componentes e a configuração do compilador precisam ser inspecionados no código para confirmar a causa. |
| `img/theme/team-4-800x800.jpg` e `img/theme/profile-cover.jpg` | Referências a imagens do template; a captura mostra problema de dimensionamento. Apenas o HTML não identifica qual regra de estilo causa o transbordamento. |
| Atributos `modelvalue=""` | Não comprovam que a API deixou de retornar dados. Rede, estado da aplicação e vínculo com a conta precisam ser investigados. |

### Evidências

- [Captura — erro na tela](../Evidencias/CT-RF02_ERRO/erro-na-tela.png), copiada do arquivo fornecido e inspecionada visualmente.
- [HTML — recorte do DOM](../Evidencias/CT-RF02_ERRO/recorte-dom.html), extraído do conteúdo enviado na conversa, com omissões explicitadas em comentários.
- [Jam — Tela de perfil do usuário com erro](https://jam.dev/c/c61241d5-bff5-4a0a-9684-991318f9b51c), com Info, Actions e quadro do vídeo em 00:05 consultados. A descrição curta do Jam menciona login, mas o título, as navegações e o conteúdo observado se referem ao perfil.

A captura estática não mostra toda a página nem a barra horizontal; a análise de transbordamento também se apoia no relato e no quadro do Jam. Não foi estabelecido diagnóstico de rede ou console para este defeito. A consulta às evidências não equivale a uma nova execução ou a um reteste da aplicação.
