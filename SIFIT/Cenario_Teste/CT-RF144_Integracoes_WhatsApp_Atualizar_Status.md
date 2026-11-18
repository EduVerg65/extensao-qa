# 🧪 Cenário 144: Consultar novamente o status da integração de WhatsApp

**Caso de teste:** CT-RF144

**Módulo:** Configurações / Integrações / WhatsApp

**Status:** Aprovado conforme a gravação.

**Gravação:** 16/11/2026, 23:45:52 BRT. **Revisão documental:** 17/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Verificar se Atualizar Status reconsulta o serviço e devolve o estado atual da integração. |
| Requisito | [RF144](../Analise%20de%20requisitos.md#rf144) — referência de QA. |
| Tipo / prioridade | Funcional manual / consulta · Média, proposta para triagem. |
| Defeito | [BUG-050](../Relatorio-de-Bugs.md#bug-050) na tentativa posterior de conexão |
| Encaminhamento | Usar como regressão de consulta e retestar a transição de estado e a atualização visual do resumo com um provedor de teste. |
| Fonte | Jam 6 — Atualização manual de status (gravação restrita por conter dados de integração) e [evidências locais](../Evidencias/CT-RF144_Integracoes_WhatsApp_Atualizar_Status/README.md). O fluxo de conexão está no [CT-RF143](CT-RF143_Integracoes_WhatsApp_Conectar_Evolution.md). |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/configuracoes |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.79 / Windows 10 (x86), conforme os metadados do Jam. |
| Tela / arquivo de vídeo | Tela 1536 × 799 informada no Jam. Vídeo em 1918 × 998. |
| Duração | 18,67 s |
| Localização | Brasil. |
| Versão / zoom / classificação do ambiente | A confirmar antes de nova execução. |
| Dados | Integração desconectada durante as consultas. O horário de última verificação é lido da resposta. |

## Pré-condições

- Sessão autenticada em Integrações → WhatsApp com o cartão Atualizar Status disponível e integração desconectada.
- Identificar a versão e registrar os valores iniciais e as permissões no próximo teste.

## Cenário BDD

```gherkin
Cenário: Consultar novamente o status da integração de WhatsApp
  Dado que a integração de WhatsApp está desconectada
  Quando o usuário aciona Atualizar no cartão Atualizar Status
  Então a aplicação deve consultar o status e receber o estado atual da conexão
  E as consultas sucessivas devem devolver a última verificação informada pelo serviço
```

## Passos para execução ou reteste

1. Abrir as ferramentas do painel de WhatsApp e localizar Atualizar Status.
2. Acionar Atualizar e verificar a resposta da consulta de status.
3. Repetir o comando e comparar `status`, `conectado` e `ultima_verificacao`.
4. Conferir a apresentação do status no painel e registrar o horário retornado.

Este procedimento orienta a próxima execução. O resultado abaixo se limita ao trecho registrado no Jam.

## Resultado esperado

Cada clique aciona uma consulta de status. Na condição desconectada, o serviço retorna esse estado e o horário de última verificação.

## Resultado obtido na gravação

Sete cliques dispararam sete GETs bem-sucedidos. As respostas mantiveram `status: desconectado` e `conectado: false`, e `ultima_verificacao` avançou de 02:45:19 para 02:45:27 conforme os valores da API. Uma ação posterior, Conectar WhatsApp, exibiu “Erro ao conectar” e também apresentou a divergência registrada no BUG-050.

| Tempo | Registro |
| --- | --- |
| 0:04–0:08 | Aciona Atualizar cinco vezes. A consulta retorna desconectado em todas elas. |
| 0:13–0:14 | Aciona Atualizar mais duas vezes. O horário da última verificação avança na resposta. |
| 0:14–0:18 | Aciona Conectar WhatsApp em uma ação posterior. A tela mostra “Erro ao conectar”. |

**Rede:**

- 0:04,86–0:13,81  Sete GETs `/api/empresa/whatsapp/status/1` (HTTP 200), `status: desconectado` e `conectado: false`. O campo `ultima_verificacao` avançou nas respostas.
- 0:14,84  POST `/api/empresa/whatsapp/conectar/1` (HTTP 200), com mensagem “Erro ao conectar” e `verifica_erro: false`. Esse evento pertence à ação de conexão.

**Conclusão:** Aprovado conforme a gravação. A aprovação cobre o comando de consulta e a resposta em estado desconectado. A gravação não mostra a atualização visual do cartão de resumo após os cliques. A conexão posterior tem evidência vinculada ao BUG-050.

## Critérios de aceitação para nova execução

1. Cada clique registrado dispara a consulta de status.
2. A resposta da consulta devolve o estado da conexão e a última verificação.
3. Quando a integração permanece desconectada, a consulta continua retornando esse estado.

## Próxima ação e verificações complementares

Usar como regressão de consulta e retestar a transição de estado e a atualização visual do resumo com um provedor de teste.

## Evidências e limites

- Jam 6 — Atualização manual de status (gravação restrita por conter dados de integração).
- [Arquivos, origem e limites](../Evidencias/CT-RF144_Integracoes_WhatsApp_Atualizar_Status/README.md).
- [Cartão Atualizar Status durante a sequência de consultas](../Evidencias/CT-RF144_Integracoes_WhatsApp_Atualizar_Status/atualizar_status_00-06.jpg), [Mensagem exibida após a tentativa adicional de conexão](../Evidencias/CT-RF144_Integracoes_WhatsApp_Atualizar_Status/erro_ao_conectar_00-16.jpg).
- [Linha do tempo](../Evidencias/CT-RF144_Integracoes_WhatsApp_Atualizar_Status/linha_do_tempo.txt).

A revisão documental se baseia nos quadros do vídeo e nos eventos capturados pelo Jam. As verificações complementares ficam para uma nova rodada de testes.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf144) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
