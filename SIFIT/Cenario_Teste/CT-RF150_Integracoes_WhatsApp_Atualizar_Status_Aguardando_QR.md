# 🧪 Cenário 150: Atualizar a verificação do WhatsApp enquanto aguarda QR Code

**Caso de teste:** CT-RF150

**Módulo:** Configurações / Integrações / WhatsApp

**Status:** Aprovado conforme a gravação.

**Gravação:** 16/11/2026, 23:36:13 BRT. **Revisão documental:** 17/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Confirmar a atualização visual da última verificação quando o serviço ainda informa que a integração está aguardando QR Code. |
| Requisito | [RF150](../Analise%20de%20requisitos.md#rf150) — referência de QA. |
| Tipo / prioridade | Funcional manual / consulta e interface · Média, proposta para triagem. |
| Defeito | Nenhum no fluxo avaliado |
| Encaminhamento | Usar como regressão da atualização visual e cobrir, com provedor de teste, a mudança de aguardando QR Code para conectado. |
| Fonte | Jam 6 — Atualização de status enquanto aguarda QR Code (gravação restrita por conter dados de integração) e [evidências locais](../Evidencias/CT-RF150_Integracoes_WhatsApp_Atualizar_Status_Aguardando_QR/README.md). A consulta em estado desconectado está no [CT-RF144](CT-RF144_Integracoes_WhatsApp_Atualizar_Status.md). |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/configuracoes |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.79 / Windows 10 (x86), conforme os metadados do Jam. |
| Tela / arquivo de vídeo | Tela 1536 × 799 informada no Jam. Vídeo em 1918 × 998. |
| Duração | 25,37 s |
| Localização | Brasil. |
| Versão / zoom / classificação do ambiente | A confirmar antes de nova execução. |
| Dados | Status inicial Aguardando QR Code. Horários da aplicação passam de 02:32 para 02:35. |

## Pré-condições

- Sessão autenticada na integração de WhatsApp com status Aguardando QR Code e ação Atualizar disponível.
- Identificar a versão e registrar os valores iniciais e as permissões no próximo teste.

## Cenário BDD

```gherkin
Cenário: Atualizar a verificação do WhatsApp enquanto aguarda QR Code
  Dado que o resumo mostra Aguardando QR Code e um horário de verificação anterior
  Quando o usuário aciona Atualizar e consulta o resumo
  Então o painel deve exibir o horário da nova verificação
  E a indicação Aguardando QR Code deve continuar enquanto a API retornar conectando
```

## Passos para execução ou reteste

1. Abrir Integrações → WhatsApp e anotar o status e a última verificação.
2. Acionar Atualizar na seção Ferramentas.
3. Retornar ao resumo de conexão.
4. Comparar o estado e o horário apresentados com a resposta da consulta.

Este procedimento orienta a próxima execução. O resultado abaixo se limita ao trecho registrado no Jam.

## Resultado esperado

Atualizar consulta o status. Se o resultado permanece conectando, a tela mantém Aguardando QR Code e apresenta a nova verificação.

## Resultado obtido na gravação

Antes da consulta, a tela mostrava 02:32 em Última Verificação. A API devolveu `status: conectando`, `conectado: false` e o horário 02:35:45. Ao retornar ao resumo, o painel indicava 02:35 e continuava em Aguardando QR Code.

| Tempo | Registro |
| --- | --- |
| 0:00–0:04 | Resumo exibe Aguardando QR Code e Última Verificação às 02:32. |
| 0:17,88 | Aciona Atualizar no cartão Atualizar Status. |
| 0:21–0:25 | Retorna ao resumo, que exibe Aguardando QR Code e Última Verificação às 02:35. |

**Rede:**

- 0:17,88  GET `/api/empresa/whatsapp/status/1` (HTTP 200), com `status: conectando`, `conectado: false` e `ultima_verificacao: 2026-11-17 02:35:45`.

**Conclusão:** Aprovado conforme a gravação. O horário citado é o exibido pelo SIFIT e pela API. A gravação cobre a consulta em espera. Pareamento e mudança para conectado não foram exercitados.

## Critérios de aceitação para nova execução

1. A ação emite a consulta de status.
2. Com `status: conectando`, a tela mantém Aguardando QR Code.
3. O resumo atualiza o horário de verificação conforme a resposta.

## Próxima ação e verificações complementares

Usar como regressão da atualização visual e cobrir, com provedor de teste, a mudança de aguardando QR Code para conectado.

## Evidências e limites

- Jam 6 — Atualização de status enquanto aguarda QR Code (gravação restrita por conter dados de integração).
- [Arquivos, origem e limites](../Evidencias/CT-RF150_Integracoes_WhatsApp_Atualizar_Status_Aguardando_QR/README.md).
- [Status Aguardando QR Code e horário de verificação antes da consulta](../Evidencias/CT-RF150_Integracoes_WhatsApp_Atualizar_Status_Aguardando_QR/status_e_verificacao_antes_00-01.jpg), [Mesmo status e novo horário de verificação depois de Atualizar](../Evidencias/CT-RF150_Integracoes_WhatsApp_Atualizar_Status_Aguardando_QR/status_e_verificacao_apos_00-22.jpg).
- [Linha do tempo](../Evidencias/CT-RF150_Integracoes_WhatsApp_Atualizar_Status_Aguardando_QR/linha_do_tempo.txt).

A revisão documental se baseia nos quadros do vídeo e nos eventos capturados pelo Jam. As verificações complementares ficam para uma nova rodada de testes.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf150) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
