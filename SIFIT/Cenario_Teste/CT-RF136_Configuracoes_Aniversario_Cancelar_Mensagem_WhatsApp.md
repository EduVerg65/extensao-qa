# 🧪 Cenário 136: Cancelar a edição da mensagem de aniversário do WhatsApp

**Caso de teste:** CT-RF136

**Módulo:** Configurações / Aniversário

**Status:** Aprovado conforme a gravação.

**Gravação:** 16/11/2026, 23:17:29 BRT. **Revisão documental:** 18/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Verificar que Cancelar descarta a edição do texto e a seleção temporária do canal WhatsApp. |
| Requisito | [RF136](../Analise%20de%20requisitos.md#rf136) — referência de QA. |
| Tipo / prioridade | Funcional manual / cancelamento · Média, proposta para triagem. |
| Defeito | Nenhum no fluxo avaliado |
| Encaminhamento | Usar como regressão do cancelamento e repetir com os demais canais da aba. |
| Fonte | [Jam 5 — Cancelamento da edição da mensagem de WhatsApp](https://jam.dev/c/a58b851c-77c2-4a49-be3b-8a5c007d2bcb) e [evidências locais](../Evidencias/CT-RF155_Configuracoes_Aniversario_Cancelar_Mensagem_WhatsApp/README.md). O cancelamento na aba Home está no [CT-RF122](CT-RF122_Configuracoes_Cancelar_Alteracao.md). |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/configuracoes |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.79 / Windows 10 (x86), conforme os metadados do Jam. |
| Tela / arquivo de vídeo | Tela 1707 × 888 informada no Jam. Vídeo em 1918 × 998. |
| Duração | 20,95 s |
| Localização | Brasil. |
| Versão / zoom / classificação do ambiente | A confirmar antes de nova execução. |
| Dados | Envio automático habilitado e canal WhatsApp desmarcado na configuração salva. A mensagem anterior já estava disponível. |

## Pré-condições

- Sessão autenticada em Configurações → Aniversário com uma mensagem de WhatsApp cadastrada e o canal desmarcado.
- Identificar a versão e registrar os valores iniciais e as permissões no próximo teste.

## Cenário BDD

```gherkin
Cenário: Cancelar a edição da mensagem de aniversário do WhatsApp
  Dado que existe uma mensagem de WhatsApp cadastrada e o canal está desmarcado
  Quando o usuário marca o canal, altera o texto e clica em Cancelar
  Então a configuração salva deve manter a seleção e o texto anteriores
  E o sistema deve voltar à Página Inicial
```

## Passos para execução ou reteste

1. Abrir Aniversário e registrar o estado do canal e o texto cadastrado.
2. Marcar WhatsApp e alterar o texto localmente.
3. Clicar em Cancelar e conferir o retorno à Página Inicial.
4. Reabrir Aniversário e verificar o estado do canal. Marcá-lo apenas para conferir o texto.

Este procedimento orienta a próxima execução. O resultado abaixo se limita ao trecho registrado no Jam.

## Resultado esperado

Cancelar retorna à Página Inicial. Ao voltar, o canal segue desmarcado e, ao marcá-lo localmente, o texto anterior reaparece.

## Resultado obtido na gravação

Cancelar retornou à Página Inicial. Ao abrir Configurações e voltar a Aniversário, o canal estava desmarcado. Quando foi marcado novamente, apareceu a mensagem anterior. A tentativa de edição ficou sem POST de salvamento.

| Tempo | Registro |
| --- | --- |
| 0:01–0:09 | Marca WhatsApp e substitui o texto no formulário. |
| 0:10,18 | Clica em Cancelar e retorna à Página Inicial. |
| 0:14–0:16 | Reabre Configurações → Aniversário. WhatsApp está desmarcado. |
| 0:18–0:20 | Marca WhatsApp para conferir o texto original. |

**Rede:**

- A captura não mostra POST para `/api/configuracoes/alterar/1` no fluxo de edição e cancelamento.
- 0:14,74  GET `/api/configuracoes/1` (HTTP 200) na volta a Configurações. O canal retorna com `enviar_mensagens_aniversario_whats: nao` e o texto anterior.

**Conclusão:** Aprovado conforme a gravação. O resultado cobre o cancelamento antes de salvar na aba Aniversário. O envio da mensagem não foi exercitado.

## Critérios de aceitação para nova execução

1. Cancelar volta à Página Inicial sem POST de salvamento.
2. O canal permanece desmarcado após a consulta.
3. A mensagem anterior reaparece ao marcar o canal no formulário.

## Próxima ação e verificações complementares

Usar como regressão do cancelamento e repetir com os demais canais da aba.

## Evidências e limites

- [Jam 5 — Cancelamento da edição da mensagem de WhatsApp](https://jam.dev/c/a58b851c-77c2-4a49-be3b-8a5c007d2bcb).
- [Arquivos, origem e limites](../Evidencias/CT-RF155_Configuracoes_Aniversario_Cancelar_Mensagem_WhatsApp/README.md).
- [Texto temporário no campo WhatsApp antes de Cancelar](../Evidencias/CT-RF155_Configuracoes_Aniversario_Cancelar_Mensagem_WhatsApp/mensagem_editada_antes_de_cancelar_00-09.jpg), [Texto anterior exibido após retornar e selecionar WhatsApp novamente](../Evidencias/CT-RF155_Configuracoes_Aniversario_Cancelar_Mensagem_WhatsApp/mensagem_anterior_apos_reabrir_00-20.jpg).
- [Linha do tempo](../Evidencias/CT-RF155_Configuracoes_Aniversario_Cancelar_Mensagem_WhatsApp/linha_do_tempo.txt).

A revisão documental se baseia nos quadros do vídeo e nos eventos capturados pelo Jam. As verificações complementares ficam para uma nova rodada de testes.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf136) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
