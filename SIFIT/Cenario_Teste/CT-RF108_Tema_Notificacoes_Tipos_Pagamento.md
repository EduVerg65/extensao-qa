# 🧪 Cenário 108: Tema Claro/Escuro e notificações na tela Tipos de Pagamento

**Caso de teste:** CT-RF108

**Módulo:** Financeiro / Tipos de Pagamento / Tema e notificações

**Status:** Aprovado conforme a gravação.

**Gravação:** 15/11/2026, 22:03 BRT. **Revisão documental:** 15/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Alternar entre os temas Claro e Escuro e abrir o painel de notificações, com a tela aplicando o tema de forma consistente e o painel exibindo seu estado. |
| Requisito | [RF108](../Analise%20de%20requisitos.md#rf108) — referência de QA; confirmação de produto pendente. |
| Tipo / prioridade | Interface manual / tema e notificações; Baixa, proposta para triagem. |
| Defeito | Nenhum no fluxo avaliado |
| Encaminhamento | Usar como regressão visual; conferir também a listagem com mais de uma tela de dados, diálogos e modais no tema Escuro e a persistência do tema após recarga. |
| Fonte | [Jam — Tipos de Pagamento](https://jam.dev/c/e8734e3d-3f8e-458b-8c7d-e85eea882e50) e [evidências locais](../Evidencias/CT-RF108_Tema_Notificacoes_Tipos_Pagamento/README.md). A mesma gravação é a fonte de [CT-RF104](CT-RF104_Filtros_Tipos_Pagamento.md), [CT-RF105](CT-RF105_Cadastro_Tipo_Pagamento_Status.md), [CT-RF106](CT-RF106_Edicao_Tipo_Pagamento.md) e [CT-RF107](CT-RF107_Exclusao_Tipo_Pagamento_Em_Uso.md). |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/tipos-pagamento |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.78 / Windows (x86) 11. |
| Tela / arquivo de vídeo | 1920 × 855 informados no Jam. |
| Duração | 1 min |
| Rede | Classificada como rápida no Jam: 7,8 Mbps, latência de 50 ms. |
| Localização | Brasil. |
| Usuário exibido | Jair, conforme o canto superior direito da tela. |
| Versão / zoom / classificação do ambiente | Não confirmados; registrar antes de nova execução. |
| Dados | Tema alternado várias vezes durante a gravação; painel de notificações aberto no tema Escuro. |

## Pré-condições

- Sessão autenticada com acesso à tela Tipos de Pagamento.
- Base de tipos de pagamento conhecida (16 tipos no início da gravação, todos exibidos como Inativo), com tipos usados em contas a receber e um tipo descartável para cadastro.
- Antes de uma nova execução, identificar versão, permissões e dados de referência e preparar a captura de interface e rede.

## Cenário BDD

```gherkin
Cenário: Alternar o tema e abrir as notificações
  Dado que a tela Tipos de Pagamento está aberta
  Quando o usuário selecionar o tema Escuro e abrir o painel de notificações
  Então o fundo, os painéis e a listagem devem acompanhar o tema
  E o painel de notificações deve apresentar o estado das notificações
  Quando o usuário voltar ao tema Claro
  Então a tela deve retornar ao tema Claro
```

## Passos para execução ou reteste

1. Acessar Tipos de Pagamento e registrar o tema inicial.
2. Selecionar Escuro e conferir fundo, painéis, listagem e cartões.
3. Abrir o sino de notificações e registrar o conteúdo do painel.
4. Voltar a Claro e conferir a tela.
5. Recarregar a página e conferir se o tema escolhido persiste.

Este procedimento orienta a próxima execução. A evidência atual cobre o trecho gravado e os limites descritos abaixo; passos complementares não recebem resultado de execução nesta revisão.

## Resultado esperado

O tema Escuro é aplicado a toda a tela, o painel de notificações apresenta seu estado e o retorno a Claro restaura a tela.

## Resultado obtido na gravação

A tela aplicou o tema Escuro ao fundo, aos painéis, aos cartões e à listagem, com contraste legível; o painel de notificações exibiu "Nada pendente por aqui. Você está em dia." e o retorno a Claro restaurou a tela. Seis `POST usuario/tema` retornaram HTTP 200.

| Tempo | Registro |
| --- | --- |
| 0:41 | Tema Escuro aplicado: fundo, painéis, cartões e listagem escuros; Total 17 e Via gateway 5. |
| 0:45 | Tema Claro restaurado. |
| 0:49–0:50 | Dois cliques no sino; painel Notificações (abas Tudo e Não lidas) com "Nada pendente por aqui. Você está em dia." no tema Escuro. |
| 0:57 | Tema Claro após a última alternância. |

**Rede:** seis `POST /api/usuario/tema` (HTTP 200, 23 B cada) distribuídos ao longo da gravação.

**Conclusão:** Aprovado conforme a gravação. O tema foi aplicado de forma consistente e o painel de notificações exibiu seu estado vazio; a aprovação se limita ao exemplo gravado, sem medição de contraste.

## Critérios de aceitação para nova execução

1. O tema Escuro é aplicado ao fundo, aos painéis, aos cartões e à listagem.
2. O painel de notificações apresenta o estado das notificações.
3. O retorno a Claro restaura a tela.
4. O tema escolhido persiste após recarregar a página.
5. Diálogos e modais acompanham o tema.

## Próxima ação e verificações complementares

Usar como regressão visual; conferir diálogos e modais no tema Escuro e a persistência do tema após recarga.

## Evidências e limites

- [Jam original — Tipos de Pagamento](https://jam.dev/c/e8734e3d-3f8e-458b-8c7d-e85eea882e50).
- [Arquivos, origem e limites](../Evidencias/CT-RF108_Tema_Notificacoes_Tipos_Pagamento/README.md).
- [Tema Escuro em 0:41](../Evidencias/CT-RF108_Tema_Notificacoes_Tipos_Pagamento/tema_escuro_00-41.jpg), [Tema Claro em 0:45.](../Evidencias/CT-RF108_Tema_Notificacoes_Tipos_Pagamento/tema_claro_00-45.jpg), [Notificações em 0:50](../Evidencias/CT-RF108_Tema_Notificacoes_Tipos_Pagamento/notificacoes_escuro_00-50.jpg), [Tema Claro em 0:57.](../Evidencias/CT-RF108_Tema_Notificacoes_Tipos_Pagamento/tema_claro_00-57.jpg), [Lista de rede](../Evidencias/CT-RF108_Tema_Notificacoes_Tipos_Pagamento/rede_lista.jpg).
- [Linha do tempo](../Evidencias/CT-RF108_Tema_Notificacoes_Tipos_Pagamento/linha_do_tempo.txt).

Foram consultados os painéis Info, Console, Network e Actions do Jam e os quadros do vídeo. As capturas foram extraídas da reprodução do Jam. Não houve nova execução, inspeção do código, acesso ao banco ou correção da aplicação. O vídeo permanece no Jam.

Análise documental da gravação consultada em 15/11/2026. Esta inclusão não executa novamente o sistema e não constitui reteste. Versão da aplicação, zoom e classificação do ambiente não foram confirmados.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf108) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
