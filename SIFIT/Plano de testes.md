# Plano de testes — SIFIT

**Atualização:** 12/11/2026

**Escopo:** CT-RF01 — Recuperação de senha; CT-RF02_ERRO — Perfil.

## Objetivo

Verificar o início da recuperação de acesso e a apresentação do perfil do usuário autenticado, mantendo a rastreabilidade entre requisitos, casos de teste, evidências e defeitos.

## Escopo

- Disponibilidade da opção na tela de login, antes da autenticação.
- Abertura do formulário ou da página de recuperação após o clique.
- Observação da interface, das requisições de rede e dos erros de console.
- Registro e reteste do BUG-001 após disponibilização da correção.
- Carregamento dos dados, renderização dos campos, idioma, dimensionamento das imagens e navegação na tela de Perfil.
- Registro e reteste do BUG-002 após disponibilização da correção, incluindo análise do DOM e comparação com os dados da conta de teste.

As etapas de envio da solicitação, entrega de mensagem, uso de token e definição de nova senha dependem da abertura do fluxo e da definição de suas regras. Não estão cobertas pela execução gravada.

A gravação de Perfil não valida o salvamento de alterações, as regras de obrigatoriedade ou todas as permissões. Esses fluxos exigem casos específicos após a definição das regras e a correção da apresentação.

## Ambiente e preparação

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

## Caso de teste e situação

| Requisito | Caso de teste | Tipo | Resultado nas evidências | Defeito | Próxima ação |
| --- | --- | --- | --- | --- | --- |
| [RF01](Analise%20de%20requisitos.md#rf01--iniciar-recuperação-de-senha) | [CT-RF01 — Acionar "Esqueci minha senha"](Cenario_Teste/CT-RF01_Esqueci-senha.md) | Funcional / fluxo positivo, com análise exploratória de rede | Reprovado | [BUG-001](Relatorio-de-Bugs.md#bug-001--link-esqueci-minha-senha-não-executa-nenhuma-ação) | Corrigir e retestar. |
| [RF02](Analise%20de%20requisitos.md#rf02--exibir-perfil-do-usuário-autenticado) | [CT-RF02_ERRO — Exibir Perfil](Cenario_Teste/CT-RF02_ERRO.md) | Funcional / interface, com análise do DOM e evidências | Reprovado | [BUG-002](Relatorio-de-Bugs.md#bug-002--perfil-com-dados-fictícios-campos-ausentes-e-layout-desconfigurado) | Corrigir e retestar. |

## Procedimento de execução e reteste

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

## Critérios de entrada e saída

**Entrada:** ambiente acessível, opção visível e ferramentas de captura disponíveis. Para Perfil, sessão válida e conta de teste com dados conhecidos. Para o reteste, correção disponibilizada em uma versão identificável.

**Saída da execução:** caso executado e resultado documentado com evidências. A execução reprovada pode ser encerrada com o defeito aberto.

**Aceitação da correção:** todos os critérios do respectivo caso atendidos e reteste documentado. BUG-001 e BUG-002 permanecem abertos até a confirmação de suas correções. A aprovação do CT-RF01 não comprova a recuperação completa da senha; a do CT-RF02_ERRO não comprova persistência de alterações no perfil.

## Riscos e Limitações do Ambiente

| ID | Risco | Impacto | Mitigação |
|---|---|---|---|
| R01 | Fluxo de recuperação não abre | Impede testar as etapas seguintes | Registrar BUG-001; retestar a abertura após a correção |
| R02 | Captura de rede desativada ou filtrada | Ausência aparente de requisições pode levar a diagnóstico incorreto | Confirmar captura ativa, remover filtros e correlacionar rede com o comportamento visual |
| R03 | Evidências obtidas em versões diferentes | Resultados podem não ser reproduzíveis na versão escolhida | Registrar URL e versão em cada execução |
| R04 | Campos do perfil não renderizados | Impede visualizar e interagir com os dados | Registrar BUG-002 e retestar após correção |
| R05 | Cadastro real da conta não disponível para comparação | Limita a validação dos valores exibidos | Preparar conta de teste com dados conhecidos |
| R06 | Domínios, resolução ou zoom diferentes entre evidências | Pode alterar comportamento e aparência | Manter os ambientes identificados por caso e registrar condições do reteste |

## Documentos associados

- [Análise de requisitos](Analise%20de%20requisitos.md)
- [Caso CT-RF01](Cenario_Teste/CT-RF01_Esqueci-senha.md)
- [Caso CT-RF02_ERRO](Cenario_Teste/CT-RF02_ERRO.md)
- [Relatório dos testes](Relatorio%20dos%20testes.md)
- [Relatório de bugs](Relatorio-de-Bugs.md)
