# 🧪 Cenário 73: Alternância de tema e painel de notificações em Planos

**Caso de teste:** CT-RF73

**Módulo:** Planos / Cabeçalho / Tema e notificações

**Status:** Aprovado conforme a gravação.

**Gravação:** 15/11/2026, 21:54 BRT. **Revisão documental:** 15/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Alternar o tema claro e escuro e abrir o painel de notificações no cabeçalho da tela Planos, gravando a escolha de tema no servidor. |
| Requisito | [RF73](../Analise%20de%20requisitos.md#rf73) — referência de QA; confirmação de produto pendente. |
| Tipo / prioridade | Funcional manual / regressão; Baixa, proposta para triagem. |
| Defeito | Nenhum no fluxo avaliado |
| Encaminhamento | Sem reteste corretivo pendente; manter como regressão. Confirmar a persistência do tema após recarga e o painel com notificações pendentes. |
| Fonte | [Jam — Planos](https://jam.dev/c/233c5d21-e108-4a55-b6f6-8738cb3fc6a6) e [evidências locais](../Evidencias/CT-RF73_Tema_Notificacoes_Planos/README.md). A mesma gravação é a fonte de [CT-RF72](CT-RF72_Filtros_Planos.md), [CT-RF74](CT-RF74_Cadastro_Plano.md), [CT-RF75](CT-RF75_Contador_Ativos_Planos.md) e [CT-RF76](CT-RF76_Edicao_Plano.md). |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/planos |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.78 / Windows (x86) 11. |
| Tela / arquivo de vídeo | 1920 × 855 informados no Jam. |
| Duração | 1 min 10 s |
| Rede | Classificada como rápida no Jam: 7,8 Mbps, latência de 50 ms. |
| Localização | Brasil. |
| Usuário exibido | Jair, conforme o canto superior direito da tela. |
| Versão / zoom / classificação do ambiente | Não confirmados; registrar antes de nova execução. |
| Dados | Usuário Jair; tema inicial claro; painel de notificações sem pendências. |

## Pré-condições

- Sessão autenticada com acesso à tela Planos.
- Base de planos conhecida (40 planos, 29 ativos e 9 alunos em planos no início da gravação), com grupos e funções cadastrados.
- Antes de uma nova execução, identificar versão, permissões e dados de referência e preparar a captura de interface e rede.

## Cenário BDD

```gherkin
Cenário: Alternar o tema e abrir as notificações em Planos
  Dado que o usuário está na tela Planos
  Quando alternar entre o tema claro e o escuro
  Então a interface deve mudar de tema e a escolha deve ser enviada ao servidor
  E ao acionar o sino o painel de Notificações deve abrir
```

## Passos para execução ou reteste

1. Acessar Planos e registrar o tema atual.
2. Acionar o tema escuro e, depois, o claro, observando a interface e a rede.
3. Acionar o sino e conferir o painel de Notificações.
4. Recarregar a página e conferir a persistência do tema.
5. Repetir com notificações pendentes.

Este procedimento orienta a próxima execução. A evidência atual cobre o trecho gravado e os limites descritos abaixo; passos complementares não recebem resultado de execução nesta revisão.

## Resultado esperado

A interface muda de tema a cada acionamento, a escolha é gravada no servidor e o painel de notificações abre com o estado correspondente.

## Resultado obtido na gravação

O tema escuro foi aplicado em 0:16 e o claro foi restaurado depois; cada troca gerou `POST usuario/tema` com HTTP 200 (cinco chamadas e um OPTIONS). O painel de Notificações abriu em 0:20 com as abas Tudo e Não lidas e a mensagem "Nada pendente por aqui. Você está em dia."

| Tempo | Registro |
| --- | --- |
| 0:14–0:18 | Cliques no alternador de tema: tema escuro ativo em 0:16 e claro novamente em seguida. |
| 0:19–0:20 | Clique no sino: painel "Notificações" aberto, com as abas Tudo e Não lidas e a mensagem de estado sem pendências. |

**Rede:** cinco `POST /api/usuario/tema` (HTTP 200, 23 B) e um `OPTIONS` (204).

**Conclusão:** Aprovado conforme a gravação. O tema muda e cada troca é enviada ao servidor com HTTP 200; o painel de notificações abre sem pendências. A aprovação se limita ao exemplo gravado.

## Critérios de aceitação para nova execução

1. Cada acionamento troca o tema sem perda de legibilidade.
2. Cada troca é gravada no servidor e permanece após recarregar.
3. O sino abre o painel de Notificações com as abas Tudo e Não lidas.
4. Sem pendências, o painel apresenta mensagem explícita.
5. Com pendências, o painel lista os itens.

## Próxima ação e verificações complementares

Usar como regressão. Permanecem fora do cenário: recarga com o tema escolhido e notificações pendentes. O contraste do tema escuro é tratado no [CT-RF14](CT-RF14_Contraste_TemaEscuro.md) e a mesma função no [CT-RF58](CT-RF58_Tema_Notificacoes_Prospeccao.md).

## Evidências e limites

- [Jam original — Planos](https://jam.dev/c/233c5d21-e108-4a55-b6f6-8738cb3fc6a6).
- [Arquivos, origem e limites](../Evidencias/CT-RF73_Tema_Notificacoes_Planos/README.md).
- [Tema escuro em 0:16](../Evidencias/CT-RF73_Tema_Notificacoes_Planos/tema_escuro_00-16.png), [Painel de Notificações em 0:19](../Evidencias/CT-RF73_Tema_Notificacoes_Planos/notificacoes_00-19.png), [Lista de rede](../Evidencias/CT-RF73_Tema_Notificacoes_Planos/rede_lista.jpg).
- [Linha do tempo](../Evidencias/CT-RF73_Tema_Notificacoes_Planos/linha_do_tempo.txt).

Foram consultados os painéis Info, Console, Network e Actions do Jam e os quadros do vídeo. As capturas foram extraídas da reprodução do Jam. Não houve nova execução, inspeção do código, acesso ao banco ou correção da aplicação. O vídeo permanece no Jam.

Análise documental da gravação consultada em 15/11/2026. Esta inclusão não executa novamente o sistema e não constitui reteste. Versão da aplicação, zoom e classificação do ambiente não foram confirmados.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf73) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
