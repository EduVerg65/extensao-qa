# 🧪 Cenário 154: Desabilitar o envio automático de aniversário

**Caso de teste:** CT-RF154

**Módulo:** Configurações / Aniversário

**Status:** Aprovado conforme a gravação.

**Gravação:** 16/11/2026, 23:15:01 BRT. **Revisão documental:** 18/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Confirmar que o valor Desabilitado de Envio automático permanece salvo após recarregar e reabrir Aniversário. |
| Requisito | [RF154](../Analise%20de%20requisitos.md#rf154) — referência de QA. |
| Tipo / prioridade | Funcional manual / persistência · Média, proposta para triagem. |
| Defeito | Nenhum no fluxo avaliado |
| Encaminhamento | Usar como regressão da preferência e conferir o efeito no agendamento com canais e destinatários de teste. |
| Fonte | [Jam 4 — Desativação do envio automático de aniversário](https://jam.dev/c/ee8a2ba9-164c-42bb-8efe-927dd6c534d5) e [evidências locais](../Evidencias/CT-RF154_Configuracoes_Aniversario_Desabilitar_Envio_Automatico/README.md). |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/configuracoes |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.79 / Windows 10 (x86), conforme os metadados do Jam. |
| Tela / arquivo de vídeo | Tela 1707 × 888 informada no Jam. Vídeo em 1918 × 998. |
| Duração | 19,89 s |
| Localização | Brasil. |
| Versão / zoom / classificação do ambiente | A confirmar antes de nova execução. |
| Dados | Valor inicial Habilitado. Alteração para Desabilitado, com envio de restauração para Habilitado ao final. |

## Pré-condições

- Sessão autenticada com permissão para editar Configurações → Aniversário. Registrar o valor inicial com a base de teste.
- Identificar a versão e registrar os valores iniciais e as permissões no próximo teste.

## Cenário BDD

```gherkin
Cenário: Desabilitar o envio automático de aniversário
  Dado que o seletor Envio automático está em Habilitado
  Quando o usuário seleciona Desabilitado, salva e recarrega a página
  Então a consulta deve devolver o valor salvo
  E o seletor deve exibir Desabilitado ao reabrir Aniversário
```

## Passos para execução ou reteste

1. Abrir Configurações → Aniversário e registrar Habilitado como valor inicial.
2. Selecionar Desabilitado em Envio automático e salvar.
3. Recarregar e reabrir Aniversário para comparar a interface com a consulta.
4. Restaurar Habilitado, salvar e consultar novamente em uma execução completa.

Este procedimento orienta a próxima execução. O resultado abaixo se limita ao trecho registrado no Jam.

## Resultado esperado

Salvar Desabilitado retorna sucesso. A consulta posterior devolve `enviar_mensagens_aniversario: nao` e Aniversário mantém Desabilitado no seletor.

## Resultado obtido na gravação

O salvamento de Desabilitado retornou HTTP 200 com `verifica_erro: false`. Após recarregar, a consulta devolveu `enviar_mensagens_aniversario: nao` e o seletor mostrou Desabilitado. O POST de restauração para Habilitado retornou sucesso.

| Tempo | Registro |
| --- | --- |
| 0:07,29 | Salva o novo valor Desabilitado. |
| 0:10,82 | Após recarregar, o GET devolve `enviar_mensagens_aniversario: nao`. |
| 0:13,12 | Reabre Aniversário e confirma Desabilitado na interface. |
| 0:18,02 | Envia a restauração para Habilitado e recebe sucesso. |

**Rede:**

- 0:07,29  POST `/api/configuracoes/alterar/1` com `enviar_mensagens_aniversario: nao` (HTTP 200, `verifica_erro: false`).
- 0:10,82  GET `/api/configuracoes/1` (HTTP 200) com `enviar_mensagens_aniversario: nao`.
- 0:18,02  POST de restauração com `enviar_mensagens_aniversario: sim` (HTTP 200, `verifica_erro: false`). A captura termina sem novo GET após a restauração.

**Conclusão:** Aprovado conforme a gravação. Os canais estavam desmarcados na gravação. O disparo de mensagens e a interação com canais já habilitados não foram exercitados.

## Critérios de aceitação para nova execução

1. O salvamento de Desabilitado retorna sucesso.
2. O GET após recarregar devolve `enviar_mensagens_aniversario: nao`.
3. O seletor mantém Desabilitado após reabrir a aba.

## Próxima ação e verificações complementares

Usar como regressão da preferência e conferir o efeito no agendamento com canais e destinatários de teste.

## Evidências e limites

- [Jam 4 — Desativação do envio automático de aniversário](https://jam.dev/c/ee8a2ba9-164c-42bb-8efe-927dd6c534d5).
- [Arquivos, origem e limites](../Evidencias/CT-RF154_Configuracoes_Aniversario_Desabilitar_Envio_Automatico/README.md).
- [Envio automático em Habilitado antes da edição](../Evidencias/CT-RF154_Configuracoes_Aniversario_Desabilitar_Envio_Automatico/envio_habilitado_00-01.jpg), [Envio automático em Desabilitado após recarregar e reabrir Aniversário](../Evidencias/CT-RF154_Configuracoes_Aniversario_Desabilitar_Envio_Automatico/envio_desabilitado_00-15.jpg).
- [Linha do tempo](../Evidencias/CT-RF154_Configuracoes_Aniversario_Desabilitar_Envio_Automatico/linha_do_tempo.txt).

A revisão documental se baseia nos quadros do vídeo e nos eventos capturados pelo Jam. As verificações complementares ficam para uma nova rodada de testes.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf154) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
