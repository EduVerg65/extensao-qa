# 🧪 Cenário 157: Consultar os detalhes de uma notificação

**Caso de teste:** CT-RF157

**Módulo:** Aplicativo / Notificações

**Status:** Aprovado conforme a gravação.

**Gravação:** 16/11/2026, 22:39:05 BRT. **Revisão documental:** 18/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Abrir a notificação selecionada e conferir a mensagem, o público indicado e a prévia. |
| Requisito | [RF157](../Analise%20de%20requisitos.md#rf157) — referência de QA. |
| Tipo / prioridade | Funcional manual / consulta · Média, proposta para triagem. |
| Defeito | Nenhum no fluxo avaliado |
| Encaminhamento | Usar como regressão da consulta e comparar dois avisos de teste diferentes para conferir o vínculo com a linha selecionada. |
| Fonte | [Jam 1 — Consulta de notificação existente](https://jam.dev/c/32edc5de-4ad3-48ca-9e19-1db449bebcc5) e [evidências locais](../Evidencias/CT-RF157_Aplicativo_Consultar_Notificacao/README.md). |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/aplicativo |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.79 / Windows 10 (x86), conforme os metadados do Jam. |
| Tela / arquivo de vídeo | Tela 1536 × 799 informada no Jam. Vídeo em 1918 × 998. |
| Duração | 16,97 s |
| Localização | Brasil. |
| Versão / zoom / classificação do ambiente | A confirmar antes de nova execução. |
| Dados | Notificação existente na listagem e destinada a Todos os alunos. Conteúdo da notificação e identificadores omitidos das evidências. |

## Pré-condições

- Sessão autenticada com acesso a Aplicativo e ao menos uma notificação de teste na lista.
- Identificar a versão e registrar os valores iniciais e as permissões no próximo teste.

## Cenário BDD

```gherkin
Cenário: Consultar os detalhes de uma notificação
  Dado que a lista de notificações contém o aviso a consultar
  Quando o usuário clica na ação de consulta da linha
  Então o diálogo deve apresentar a mensagem do aviso selecionado e sua prévia
  E Fechar deve retornar à listagem
```

## Passos para execução ou reteste

1. Localizar uma notificação de teste na lista.
2. Acionar a lupa da linha e aguardar o diálogo.
3. Conferir o texto, o público informado e a prévia.
4. Clicar em Fechar e conferir o retorno à lista.

Este procedimento orienta a próxima execução. O resultado abaixo se limita ao trecho registrado no Jam.

## Resultado esperado

O diálogo Notificação abre com os dados da linha selecionada, mostra a prévia e pode ser fechado.

## Resultado obtido na gravação

A consulta retornou HTTP 200 e abriu Notificação com Todos os alunos. O texto exibido correspondia ao aviso selecionado e reapareceu na prévia. Fechar voltou à lista.

| Tempo | Registro |
| --- | --- |
| 0:06,96 | Aciona a lupa da linha e abre os detalhes. |
| 0:09–0:14 | Confere o público, a mensagem e a prévia. |
| 0:15,34 | Aciona Fechar e volta à lista. |

**Rede:**

- 0:06,96  POST `/api/notificacoes/buscar/1` (HTTP 200), com devolução da notificação correspondente à consulta.

**Conclusão:** Aprovado conforme a gravação. O caso verifica a consulta no painel. A gravação não demonstra recebimento no celular.

## Critérios de aceitação para nova execução

1. A ação consulta o registro da linha selecionada.
2. O diálogo exibe a mensagem e a prévia correspondentes.
3. Fechar encerra apenas a consulta.

## Próxima ação e verificações complementares

Usar como regressão da consulta e comparar dois avisos de teste diferentes para conferir o vínculo com a linha selecionada.

## Evidências e limites

- [Jam 1 — Consulta de notificação existente](https://jam.dev/c/32edc5de-4ad3-48ca-9e19-1db449bebcc5).
- [Arquivos, origem e limites](../Evidencias/CT-RF157_Aplicativo_Consultar_Notificacao/README.md).
- [Diálogo Notificação com destinatários e conteúdo da mensagem ocultado](../Evidencias/CT-RF157_Aplicativo_Consultar_Notificacao/detalhes_notificacao_00-10.jpg), [Ação Fechar no diálogo de consulta](../Evidencias/CT-RF157_Aplicativo_Consultar_Notificacao/acao_fechar_00-15.jpg).
- [Linha do tempo](../Evidencias/CT-RF157_Aplicativo_Consultar_Notificacao/linha_do_tempo.txt).

A revisão documental se baseia nos quadros do vídeo e nos eventos capturados pelo Jam. As verificações complementares ficam para uma nova rodada de testes.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf157) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
