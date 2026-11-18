# 🧪 Cenário 145: Salvar mensagens de aniversário para WhatsApp e SMS

**Caso de teste:** CT-RF145

**Módulo:** Configurações / Aniversário

**Status:** Aprovado conforme a gravação.

**Gravação:** 16/11/2026, 23:21:59 BRT. **Revisão documental:** 17/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Confirmar que os canais WhatsApp e SMS e suas mensagens de aniversário persistem após salvar e reabrir a aba. |
| Requisito | [RF145](../Analise%20de%20requisitos.md#rf145) — referência de QA. |
| Tipo / prioridade | Funcional manual / persistência · Média, proposta para triagem. |
| Defeito | Nenhum no fluxo avaliado |
| Encaminhamento | Usar como regressão da configuração e retestar o disparo em um ambiente de teste com destinatários autorizados. |
| Fonte | Jam 1 — Mensagens de aniversário por WhatsApp e SMS (gravação restrita por conter dados de integração) e [evidências locais](../Evidencias/CT-RF145_Configuracoes_Aniversario_Salvar_WhatsApp_SMS/README.md). |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/configuracoes |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.79 / Windows 10 (x86), conforme os metadados do Jam. |
| Tela / arquivo de vídeo | Tela 1707 × 888 informada no Jam. Vídeo em 1918 × 998. |
| Duração | 32,65 s |
| Localização | Brasil. |
| Versão / zoom / classificação do ambiente | A confirmar antes de nova execução. |
| Dados | Envio automático habilitado e mensagens de teste WHATS e SMS. WhatsApp e SMS marcados no momento do salvamento. |

## Pré-condições

- Sessão autenticada com acesso à aba Aniversário e permissão para alterar as configurações de teste.
- Identificar a versão e registrar os valores iniciais e as permissões no próximo teste.

## Cenário BDD

```gherkin
Cenário: Salvar mensagens de aniversário para WhatsApp e SMS
  Dado que o envio de aniversário está habilitado e o usuário pode editar as mensagens
  Quando ele ativa os canais WhatsApp e SMS, preenche os dois textos e salva
  Então a configuração deve armazenar os canais e as mensagens informadas
  E a aba reaberta deve apresentar a configuração salva
```

## Passos para execução ou reteste

1. Abrir Aniversário com Envio automático habilitado.
2. Marcar WhatsApp e SMS e preencher mensagens de teste diferentes.
3. Salvar Configurações e aguardar a resposta.
4. Recarregar a página, reabrir a aba e conferir os canais e textos.

Este procedimento orienta a próxima execução. O resultado abaixo se limita ao trecho registrado no Jam.

## Resultado esperado

WhatsApp e SMS permanecem marcados e mostram suas respectivas mensagens após recarregar a página.

## Resultado obtido na gravação

O salvamento retornou HTTP 200 com `verifica_erro: false`. A consulta depois de recarregar confirmou os canais WhatsApp e SMS habilitados e os textos WHATS e SMS. Ao reabrir a aba, os dois canais e os textos salvos apareceram novamente.

| Tempo | Registro |
| --- | --- |
| 0:00–0:12 | Marca WhatsApp e SMS e preenche os textos de teste. |
| 0:21,45 | Aciona Salvar Configurações. |
| 0:24–0:25 | Desmarca os canais localmente. A gravação não registra um novo salvamento. |
| 0:27–0:32 | Recarrega e reabre Aniversário. Os canais e os textos salvos voltam a aparecer. |

**Rede:**

- 0:21,84  POST `/api/configuracoes/alterar/1` (HTTP 200, `verifica_erro: false`). O envio inclui as opções de WhatsApp e SMS habilitadas e as duas mensagens.
- 0:27,31  GET `/api/configuracoes/1` (HTTP 200), com `enviar_mensagens_aniversario_whats: sim`, `enviar_mensagens_aniversario_sms: sim` e os textos salvos.

**Conclusão:** Aprovado conforme a gravação. A gravação verifica a configuração. O disparo automático, a entrega e a substituição das variáveis das mensagens estão fora da evidência.

## Critérios de aceitação para nova execução

1. O salvamento aceita os dois canais e suas mensagens.
2. A nova leitura confirma as opções habilitadas e as mensagens editadas.
3. A interface mostra os valores salvos ao reabrir a aba.

## Próxima ação e verificações complementares

Usar como regressão da configuração e retestar o disparo em um ambiente de teste com destinatários autorizados.

## Evidências e limites

- Jam 1 — Mensagens de aniversário por WhatsApp e SMS (gravação restrita por conter dados de integração).
- [Arquivos, origem e limites](../Evidencias/CT-RF145_Configuracoes_Aniversario_Salvar_WhatsApp_SMS/README.md).
- [Canais WhatsApp e SMS marcados e respectivos textos antes de salvar](../Evidencias/CT-RF145_Configuracoes_Aniversario_Salvar_WhatsApp_SMS/mensagens_antes_de_salvar_00-21.jpg), [Canais e mensagens após recarregar e reabrir a aba](../Evidencias/CT-RF145_Configuracoes_Aniversario_Salvar_WhatsApp_SMS/mensagens_apos_reabrir_00-31.jpg).
- [Linha do tempo](../Evidencias/CT-RF145_Configuracoes_Aniversario_Salvar_WhatsApp_SMS/linha_do_tempo.txt).

A revisão documental se baseia nos quadros do vídeo e nos eventos capturados pelo Jam. As verificações complementares ficam para uma nova rodada de testes.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf145) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
