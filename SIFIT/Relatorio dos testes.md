# Relatório dos testes — SIFIT

**Escopo:** CT-RF01 — Recuperação de senha; CT-RF02_ERRO — Perfil

**Datas das gravações do Jam:** CT-RF01 em 23/10/2026; CT-RF02_ERRO em 22/10/2026 às 21:45 BRT.

**Data da revisão documental:** 12/11/2026. Resultados do CT-RF01 preservados da revisão de 10/11/2026.

**Origem do resultado:** análise de evidências fornecidas; sem nova execução no sistema nesta revisão.

## Resumo do resultado

O caso **CT-RF01** foi classificado como **reprovado**: a opção "Esqueci minha senha" não inicia o fluxo de recuperação. O Jam mostra cliques repetidos e permanência na tela de login; a consulta aos registros da captura retorna **0 requisições de rede** e **0 mensagens de erro no console**.

O **CT-RF02_ERRO** também foi classificado como **reprovado**: o perfil apresenta conteúdo fictício, textos em inglês, seções sem campos visíveis e layout desconfigurado. A classificação se apoia no relato, na captura, no HTML fornecido e na consulta ao Jam. A causa técnica não foi confirmada no código.

| Casos avaliados | Aprovados | Reprovados | Retestes pendentes |
| --- | --- | --- | --- |
| 2 | 0 | 2 | 2 |

## Resultado por caso

| Caso | Requisito | Esperado | Obtido | Resultado | Defeito |
| --- | --- | --- | --- | --- | --- |
| [CT-RF01](Cenario_Teste/CT-RF01_Esqueci-senha.md) | [RF01](Analise%20de%20requisitos.md#rf01--iniciar-recuperação-de-senha) | Abrir formulário ou página para iniciar a recuperação de senha. | Tela de login permanece sem abertura do fluxo; nenhum registro de requisição no Jam. | Reprovado | [BUG-001](Relatorio-de-Bugs.md#bug-001--link-esqueci-minha-senha-não-executa-nenhuma-ação) |
| [CT-RF02_ERRO](Cenario_Teste/CT-RF02_ERRO.md) | [RF02](Analise%20de%20requisitos.md#rf02--exibir-perfil-do-usuário-autenticado) | Exibir dados da conta, campos visíveis, textos em português e layout organizado. | Conteúdo fictício, campos não exibidos, imagem desproporcional e rolagem horizontal. | Reprovado | [BUG-002](Relatorio-de-Bugs.md#bug-002--perfil-com-dados-fictícios-campos-ausentes-e-layout-desconfigurado) |

## Ambiente identificado

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

## Evidências e observações

| Evidência | Informação utilizada |
| --- | --- |
| [Jam — Erro no esqueci a senhas](https://jam.dev/c/0273b203-b999-493d-9919-2d143bc13301) | Eventos de clique entre aproximadamente 00:02 e 00:12, quadros do vídeo sem abertura do fluxo, 0 requisições registradas e 0 erros de console registrados. |
| [Google Drive — CT-RF01_Esqueci-senha](https://drive.google.com/file/d/1f6AqYunchDH4R9Yw1JpbyX9x28UQGcbo/view?usp=sharing) | Vídeo complementar fornecido pelo solicitante; metadados consultados, conteúdo não inspecionado nesta revisão. |
| [Captura — CT-RF02_ERRO](Evidencias/CT-RF02_ERRO/erro-na-tela.png) | Seções Usuário, Documentos e Endereço sem campos visíveis, imagem fora de proporção, “Edit profile” e About me com texto de demonstração. |
| [HTML — CT-RF02_ERRO](Evidencias/CT-RF02_ERRO/recorte-dom.html) | Recorte do DOM fornecido, incluindo “Hello Jesse”, “Jessica Jones” e tags de componentes sem controles nativos de entrada nos campos de cadastro. |
| [Jam — Tela de perfil do usuário com erro](https://jam.dev/c/c61241d5-bff5-4a0a-9684-991318f9b51c) | Info, Actions e quadro em 00:05 consultados. Navegações para `/profile` em 00:02 e 00:12; seções sem campos visíveis e barra horizontal no quadro consultado. |

A mensagem de credenciais incorretas já aparece no início do vídeo do Jam; não foi considerada uma resposta ao clique em "Esqueci minha senha". A ausência de requisição, isoladamente, não caracteriza defeito se a interface abrir um formulário local. Aqui, o resultado reprovado decorre de o fluxo não abrir.

No CT-RF02_ERRO, a permanência de tags como `<base-input>` no DOM é um indício a investigar, sem confirmação da causa. A captura estática não mostra toda a página ou a barra horizontal; o relato e o quadro do Jam complementam essa evidência. Não foi estabelecido diagnóstico de rede/console, não houve comparação individual com o cadastro real nem teste de salvamento. As contagens de rede e console do CT-RF01 não se aplicam ao CT-RF02_ERRO.

## Pendências e encaminhamento

- **BUG-001:** aberto, com severidade e prioridade altas; causa técnica ainda não confirmada no código.
- **Reteste de CT-RF01:** pendente após a correção, conforme o [plano de testes](Plano%20de%20testes.md).
- **BUG-002:** aberto, com severidade e prioridade propostas como altas; investigar renderização dos componentes, dados de demonstração e estilos do perfil.
- **Reteste de CT-RF02_ERRO:** pendente após a correção, com conta de teste de dados conhecidos e condições de layout registradas, conforme o [plano](Plano%20de%20testes.md).
- **Etapas seguintes:** não avaliadas nesta evidência, pois não foi possível iniciar a recuperação; detalhamento depende da definição das regras do fluxo.
