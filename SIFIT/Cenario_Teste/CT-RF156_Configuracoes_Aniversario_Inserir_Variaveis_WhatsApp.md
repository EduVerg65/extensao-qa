# 🧪 Cenário 156: Inserir variáveis na mensagem de aniversário do WhatsApp

**Caso de teste:** CT-RF156

**Módulo:** Configurações / Aniversário

**Status:** Aprovado conforme a gravação.

**Gravação:** 16/11/2026, 23:20:07 BRT. **Revisão documental:** 18/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Verificar que as variáveis selecionadas no painel aparecem no campo WhatsApp e que Cancelar descarta essa edição. |
| Requisito | [RF156](../Analise%20de%20requisitos.md#rf156) — referência de QA. |
| Tipo / prioridade | Funcional manual / edição e cancelamento · Média, proposta para triagem. |
| Defeito | Nenhum no fluxo avaliado |
| Encaminhamento | Usar como regressão do editor e testar a substituição dos marcadores em um envio controlado com dados de teste. |
| Fonte | [Jam 6 — Inserção de variáveis na mensagem de WhatsApp](https://jam.dev/c/fb2c4949-c68d-4f90-b47c-44da9dbe58a3) e [evidências locais](../Evidencias/CT-RF156_Configuracoes_Aniversario_Inserir_Variaveis_WhatsApp/README.md). O cancelamento de uma edição de texto está no [CT-RF155](CT-RF155_Configuracoes_Aniversario_Cancelar_Mensagem_WhatsApp.md). |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/configuracoes |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.79 / Windows 10 (x86), conforme os metadados do Jam. |
| Tela / arquivo de vídeo | Tela 1707 × 888 informada no Jam. Vídeo em 1918 × 998. |
| Duração | 32,14 s |
| Localização | Brasil. |
| Versão / zoom / classificação do ambiente | A confirmar antes de nova execução. |
| Dados | Mensagem anterior cadastrada, canal WhatsApp desmarcado e variáveis de nome, primeiro nome, data de aniversário e idade disponíveis. |

## Pré-condições

- Sessão autenticada em Configurações → Aniversário com acesso ao campo WhatsApp e ao painel Variáveis disponíveis.
- Identificar a versão e registrar os valores iniciais e as permissões no próximo teste.

## Cenário BDD

```gherkin
Cenário: Inserir variáveis na mensagem de aniversário do WhatsApp
  Dado que o campo WhatsApp está disponível para edição e há variáveis de aluno no painel
  Quando o usuário informa um texto de teste e seleciona as variáveis de nome, primeiro nome, aniversário e idade
  Então o campo deve mostrar os marcadores selecionados na ordem da seleção
  E Cancelar deve descartar o texto temporário
```

## Passos para execução ou reteste

1. Abrir Aniversário, marcar WhatsApp localmente e registrar o texto anterior.
2. Substituir o texto por uma mensagem de teste e selecionar as quatro variáveis no painel.
3. Conferir a presença e a ordem dos marcadores no campo da mensagem.
4. Cancelar, reabrir a aba e conferir o retorno do texto anterior.

Este procedimento orienta a próxima execução. O resultado abaixo se limita ao trecho registrado no Jam.

## Resultado esperado

O editor exibe os quatro marcadores na ordem escolhida. Após Cancelar, ao reabrir e marcar WhatsApp, aparece a mensagem anterior.

## Resultado obtido na gravação

Os cliques acrescentaram `{nome_aluno}`, `{primeiro_nome}`, `{data_aniversario}` e `{idade}` ao texto editado. Cancelar voltou à Página Inicial. Após reabrir Aniversário e marcar WhatsApp, a mensagem anterior reapareceu. O trecho não registra POST de salvamento.

| Tempo | Registro |
| --- | --- |
| 0:01–0:09 | Marca WhatsApp, seleciona o texto anterior e digita um texto de teste. |
| 0:11,04–0:13,18 | Seleciona as quatro variáveis de aluno e visualiza os marcadores no campo. |
| 0:17,95 | Clica em Cancelar e retorna à Página Inicial. |
| 0:24–0:30 | Reabre Configurações e Aniversário e marca WhatsApp para conferir a mensagem anterior. |

**Rede:**

- Os eventos do Jam registram cliques em `{nome_aluno}`, `{primeiro_nome}`, `{data_aniversario}` e `{idade}`. A captura não mostra POST para `/api/configuracoes/alterar/1`.
- 0:25,05  GET `/api/configuracoes/1` (HTTP 200), com o canal desmarcado e a mensagem anterior.

**Conclusão:** Aprovado conforme a gravação. O caso verifica a inserção dos marcadores no editor e o descarte da edição. A substituição por dados reais e o envio não foram exercitados.

## Critérios de aceitação para nova execução

1. Cada clique insere o marcador correspondente no campo WhatsApp.
2. Os marcadores permanecem na ordem em que foram selecionados.
3. A edição temporária é descartada com Cancelar.

## Próxima ação e verificações complementares

Usar como regressão do editor e testar a substituição dos marcadores em um envio controlado com dados de teste.

## Evidências e limites

- [Jam 6 — Inserção de variáveis na mensagem de WhatsApp](https://jam.dev/c/fb2c4949-c68d-4f90-b47c-44da9dbe58a3).
- [Arquivos, origem e limites](../Evidencias/CT-RF156_Configuracoes_Aniversario_Inserir_Variaveis_WhatsApp/README.md).
- [Variáveis selecionadas no painel aparecem no campo da mensagem](../Evidencias/CT-RF156_Configuracoes_Aniversario_Inserir_Variaveis_WhatsApp/variaveis_inseridas_00-16.jpg), [Modelo anterior reaparece após cancelar e voltar ao formulário](../Evidencias/CT-RF156_Configuracoes_Aniversario_Inserir_Variaveis_WhatsApp/mensagem_apos_cancelar_00-29.jpg).
- [Linha do tempo](../Evidencias/CT-RF156_Configuracoes_Aniversario_Inserir_Variaveis_WhatsApp/linha_do_tempo.txt).

A revisão documental se baseia nos quadros do vídeo e nos eventos capturados pelo Jam. As verificações complementares ficam para uma nova rodada de testes.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf156) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
