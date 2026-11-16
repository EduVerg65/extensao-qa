# 🧪 Cenário 58: Alternância de tema e painel de notificações em Prospecção

**Caso de teste:** CT-RF58

**Módulo:** Prospecção / Cabeçalho / Tema e notificações

**Status:** Aprovado conforme a gravação.

**Gravação:** 15/11/2026, 21:52 BRT. **Revisão documental:** 15/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Alternar o tema claro e escuro e abrir o painel de notificações no cabeçalho da tela Prospecção, preservando a escolha de tema no servidor. |
| Requisito | [RF58](../Analise%20de%20requisitos.md#rf58) — referência de QA; confirmação de produto pendente. |
| Tipo / prioridade | Funcional manual / regressão; Baixa, proposta para triagem. |
| Defeito | Nenhum no fluxo avaliado |
| Encaminhamento | Sem reteste corretivo pendente; manter como regressão. Confirmar a persistência do tema após recarga e o conteúdo do painel com notificações. |
| Fonte | [Jam — Prospecção](https://jam.dev/c/308607ff-8abc-40af-8c7c-429ce506ed64) e [evidências locais](../Evidencias/CT-RF58_Tema_Notificacoes_Prospeccao/README.md). A mesma gravação é a fonte de [CT-RF59](CT-RF59_Busca_Leads_Prospeccao.md), [CT-RF60](CT-RF60_Filtro_Estagio_Leads.md), [CT-RF61](CT-RF61_Cadastro_Lead_Prospeccao.md), [CT-RF62](CT-RF62_Telefone_Lead_Sem_Validacao.md) e [CT-RF63](CT-RF63_Edicao_Lead_Prospeccao.md). |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/prospeccao |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.78 / Windows (x86) 11. |
| Tela / arquivo de vídeo | 1920 × 911 informados no Jam. |
| Duração | 1 min 2 s |
| Rede | Classificada como rápida no Jam: 5,4 Mbps, latência de 100 ms. |
| Localização | Brasil. |
| Usuário exibido | Jair, conforme o canto superior direito da tela. |
| Versão / zoom / classificação do ambiente | Não confirmados; registrar antes de nova execução. |
| Dados | Usuário Jair; tema inicial claro; painel de notificações sem pendências ("Nada pendente por aqui. Você está em dia."). |

## Pré-condições

- Sessão autenticada com acesso à tela Prospecção.
- Base de leads conhecida, com códigos, nomes e estágios registrados antes da execução.
- Antes de uma nova execução, identificar versão, permissões e dados de referência e preparar a captura de interface e rede.

## Cenário BDD

```gherkin
Cenário: Alternar o tema e abrir as notificações em Prospecção
  Dado que o usuário está na tela Prospecção
  Quando alternar entre o tema claro e o escuro
  Então a interface deve mudar de tema e a escolha deve ser enviada ao servidor
  E ao acionar o sino o painel de Notificações deve abrir com as abas Tudo e Não lidas
```

## Passos para execução ou reteste

1. Acessar Prospecção e registrar o tema atual.
2. Acionar o tema escuro e, depois, o claro, observando a interface e a rede.
3. Acionar o sino e conferir o painel de Notificações, as abas Tudo e Não lidas e o estado sem pendências.
4. Fechar o painel e recarregar a página para conferir a persistência do tema.
5. Repetir com notificações pendentes e marcar como lidas.

Este procedimento orienta a próxima execução. A evidência atual cobre o trecho gravado e os limites descritos abaixo; passos complementares não recebem resultado de execução nesta revisão.

## Resultado esperado

A interface muda de tema a cada acionamento, a escolha é gravada no servidor e o painel de notificações abre com as abas e a mensagem correspondente ao estado.

## Resultado obtido na gravação

O tema escuro foi aplicado em 0:01 e o tema claro voltou a ser exibido em 0:03; cada acionamento gerou um POST usuario/tema com HTTP 200. O painel de Notificações abriu em 0:03 com as abas Tudo e Não lidas e a mensagem "Nada pendente por aqui. Você está em dia."

| Tempo | Registro |
| --- | --- |
| 0:00–0:01 | Cliques no alternador de tema: a interface passa ao tema escuro (botão Escuro ativo no quadro de 0:01). |
| 0:02–0:03 | Clique no sino: painel "Notificações" aberto, com as abas Tudo e Não lidas, o link "Marcar como lidas" e a mensagem "Nada pendente por aqui. Você está em dia."; o tema está novamente claro. |
| 0:04 | Dois cliques no ícone de perfil; o resultado não foi conferido em quadro. |

**Rede:** quatro `POST /api/usuario/tema` (HTTP 200, 23 B) e um `OPTIONS` (204) no início da gravação; o painel de notificações não gera requisição.

**Conclusão:** Aprovado conforme a gravação. O tema muda e a escolha é enviada ao servidor com HTTP 200; o painel de notificações abre com o estado sem pendências. A aprovação se limita ao exemplo gravado; a persistência após recarga e o painel com notificações pendentes não foram verificados.

## Critérios de aceitação para nova execução

1. Cada acionamento do alternador troca o tema da interface sem perda de legibilidade.
2. Cada troca de tema é gravada no servidor e permanece após recarregar a página.
3. O sino abre o painel de Notificações com as abas Tudo e Não lidas.
4. Sem pendências, o painel apresenta mensagem explícita de estado vazio.
5. Com pendências, o painel lista os itens e permite marcá-los como lidos.

## Próxima ação e verificações complementares

Usar como regressão. Permanecem fora do cenário gravado: recarga da página com o tema escolhido, notificações pendentes, aba Não lidas com itens e a ação "Marcar como lidas". O contraste do tema escuro é tratado no [CT-RF14](CT-RF14_Contraste_TemaEscuro.md).

## Observação sobre o ícone de perfil

Os dois cliques no ícone de perfil em 0:04 não têm resultado visível em quadro nem requisição associada; o comportamento esperado do ícone não foi informado e não entra no veredito.

## Evidências e limites

- [Jam original — Prospecção](https://jam.dev/c/308607ff-8abc-40af-8c7c-429ce506ed64).
- [Arquivos, origem e limites](../Evidencias/CT-RF58_Tema_Notificacoes_Prospeccao/README.md).
- [Tema escuro em 0:01](../Evidencias/CT-RF58_Tema_Notificacoes_Prospeccao/tema_escuro_00-01.png), [Painel de Notificações em 0:03](../Evidencias/CT-RF58_Tema_Notificacoes_Prospeccao/notificacoes_00-03.png), [Lista de rede](../Evidencias/CT-RF58_Tema_Notificacoes_Prospeccao/rede_lista.jpg).
- [Linha do tempo](../Evidencias/CT-RF58_Tema_Notificacoes_Prospeccao/linha_do_tempo.txt).

Foram consultados os painéis Info, Console, Network e Actions do Jam e os quadros do vídeo. As capturas foram extraídas da reprodução do Jam; quadros com o e-mail digitado no formulário não foram incluídos nem recortados com esse dado. A persistência do tema após recarga e o painel com notificações pendentes não foram exercitados. Não houve nova execução, inspeção do código, acesso ao banco ou correção da aplicação. O vídeo permanece no Jam.

Análise documental da gravação consultada em 15/11/2026. Esta inclusão não executa novamente o sistema e não constitui reteste. Versão da aplicação, zoom e classificação do ambiente não foram confirmados.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf58) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
