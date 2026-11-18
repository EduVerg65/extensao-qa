# 🧪 Cenário 158: Impedir o envio de uma notificação sem mensagem

**Caso de teste:** CT-RF158

**Módulo:** Aplicativo / Notificações

**Status:** Aprovado conforme a gravação.

**Gravação:** 16/11/2026, 22:40:04 BRT. **Revisão documental:** 18/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Manter Enviar aviso desabilitado enquanto a mensagem estiver vazia. |
| Requisito | [RF158](../Analise%20de%20requisitos.md#rf158) — referência de QA. |
| Tipo / prioridade | Funcional manual / validação · Média, proposta para triagem. |
| Defeito | Nenhum no fluxo avaliado |
| Encaminhamento | Usar como regressão do formulário vazio e repetir com entrada composta apenas de espaços. |
| Fonte | Jam 2 — Validação de mensagem obrigatória (gravação restrita por conter dados de integração ou dados de alunos) e [evidências locais](../Evidencias/CT-RF158_Aplicativo_Bloquear_Notificacao_Vazia/README.md). |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/aplicativo |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.79 / Windows 10 (x86), conforme os metadados do Jam. |
| Tela / arquivo de vídeo | Tela 1536 × 799 informada no Jam. Vídeo em 1918 × 998. |
| Duração | 13,11 s |
| Localização | Brasil. |
| Versão / zoom / classificação do ambiente | A confirmar antes de nova execução. |
| Dados | Formulário Criar Notificação com destinatários Todos os alunos e contador de mensagem em zero. |

## Pré-condições

- Sessão autenticada com acesso a Aplicativo e permissão para abrir a criação.
- Identificar a versão e registrar os valores iniciais e as permissões no próximo teste.

## Cenário BDD

```gherkin
Cenário: Impedir o envio de uma notificação sem mensagem
  Dado que o formulário de notificação está aberto com a mensagem vazia
  Quando o usuário tenta acionar Enviar aviso
  Então a ação deve ficar indisponível e a criação deve ser bloqueada
  E Cancelar deve fechar o formulário
```

## Passos para execução ou reteste

1. Abrir Criar Notificação com o campo Mensagem vazio.
2. Conferir o contador e o estado de Enviar aviso.
3. Tentar acionar o botão e conferir se há requisição de criação.
4. Cancelar e retornar à lista.

Este procedimento orienta a próxima execução. O resultado abaixo se limita ao trecho registrado no Jam.

## Resultado esperado

O botão Enviar aviso permanece desabilitado, sem requisição de criação. Cancelar retorna à lista.

## Resultado obtido na gravação

O formulário abriu com contador em zero. Os cliques na região de Enviar aviso não iniciaram a criação. O botão permaneceu desabilitado e Cancelar fechou o formulário.

| Tempo | Registro |
| --- | --- |
| 0:03,09 | Abre Criar Notificação. |
| 0:05–0:10 | Tenta acionar Enviar aviso com a mensagem em branco. |
| 0:11,70 | Clica em Cancelar. |

**Rede:**

- Os cliques na área do botão durante o formulário vazio não geraram POST para `/api/notificacoes/criar/1` na captura.

**Conclusão:** Aprovado conforme a gravação. A evidência cobre o campo totalmente vazio. Espaços em branco e limites de comprimento ficam para nova execução.

## Critérios de aceitação para nova execução

1. O contador permanece em zero com o campo vazio.
2. O botão fica desabilitado e o endpoint de criação não é chamado.
3. Cancelar fecha o diálogo.

## Próxima ação e verificações complementares

Usar como regressão do formulário vazio e repetir com entrada composta apenas de espaços.

## Evidências e limites

- Jam 2 — Validação de mensagem obrigatória (gravação restrita por conter dados de integração ou dados de alunos).
- [Arquivos, origem e limites](../Evidencias/CT-RF158_Aplicativo_Bloquear_Notificacao_Vazia/README.md).
- [Formulário vazio, contador em zero e ação Enviar aviso desabilitada](../Evidencias/CT-RF158_Aplicativo_Bloquear_Notificacao_Vazia/notificacao_sem_mensagem_00-05.jpg), [Ação Enviar aviso permanece desabilitada durante a tentativa](../Evidencias/CT-RF158_Aplicativo_Bloquear_Notificacao_Vazia/acao_enviar_desabilitada_00-09.jpg).
- [Linha do tempo](../Evidencias/CT-RF158_Aplicativo_Bloquear_Notificacao_Vazia/linha_do_tempo.txt).

A revisão documental se baseia nos quadros do vídeo e nos eventos capturados pelo Jam. As verificações complementares ficam para uma nova rodada de testes.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf158) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
