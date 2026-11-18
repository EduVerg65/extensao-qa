# 🧪 Cenário 159: Criar uma notificação e conferir a prévia e a listagem

**Caso de teste:** CT-RF159

**Módulo:** Aplicativo / Notificações

**Status:** Aprovado conforme a gravação.

**Gravação:** 16/11/2026, 22:41:22 BRT. **Revisão documental:** 18/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Comparar a mensagem digitada com a prévia e verificar que a criação retorna sucesso e inclui o aviso na lista. |
| Requisito | [RF159](../Analise%20de%20requisitos.md#rf159) — referência de QA. |
| Tipo / prioridade | Funcional manual / criação e consulta · Média, proposta para triagem. |
| Defeito | Nenhum no fluxo avaliado |
| Encaminhamento | Usar como regressão da criação e validar o recebimento em um dispositivo de teste em uma execução dedicada. |
| Fonte | Jam 3 — Criação de notificação com prévia (gravação restrita por conter dados de integração ou dados de alunos) e [evidências locais](../Evidencias/CT-RF159_Aplicativo_Criar_Notificacao_Preview/README.md). |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/aplicativo |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.79 / Windows 10 (x86), conforme os metadados do Jam. |
| Tela / arquivo de vídeo | Tela 1536 × 799 informada no Jam. Vídeo em 1918 × 998. |
| Duração | 32,86 s |
| Localização | Brasil. |
| Versão / zoom / classificação do ambiente | A confirmar antes de nova execução. |
| Dados | Mensagem TESTE DE MENSAGEM e público exibido como Todos os alunos. |

## Pré-condições

- Sessão autorizada em um ambiente de teste com contatos de teste e acesso a Criar Notificação.
- Identificar a versão e registrar os valores iniciais e as permissões no próximo teste.

## Cenário BDD

```gherkin
Cenário: Criar uma notificação e conferir a prévia e a listagem
  Dado que o usuário pode criar notificações no ambiente de teste
  Quando ele preenche a mensagem, confere a prévia e aciona Enviar aviso
  Então a API deve confirmar a criação e a listagem deve incluir o aviso
  E a mensagem da prévia e a da lista devem corresponder ao texto digitado
```

## Passos para execução ou reteste

1. Abrir Criar Notificação no ambiente de teste.
2. Preencher uma mensagem de teste e comparar com a prévia.
3. Acionar Enviar aviso e aguardar a resposta.
4. Conferir a presença e o texto da nova notificação na lista.

Este procedimento orienta a próxima execução. O resultado abaixo se limita ao trecho registrado no Jam.

## Resultado esperado

A prévia acompanha o texto. O envio retorna sucesso e inclui o aviso na lista de notificações.

## Resultado obtido na gravação

A prévia mostrou TESTE DE MENSAGEM. Ao acionar Enviar aviso, a API retornou HTTP 201 com `verifica_erro: false`. A lista foi consultada novamente e exibiu o aviso de teste no topo.

| Tempo | Registro |
| --- | --- |
| 0:02,21 | Abre Criar Notificação. |
| 0:06–0:18 | Preenche o texto e confere a prévia. |
| 0:23,39–0:23,86 | Aciona Enviar aviso e a criação é confirmada. |
| 0:25–0:31 | Confere o novo aviso no topo da lista. |

**Rede:**

- 0:23,86  POST `/api/notificacoes/criar/1` (HTTP 201, `verifica_erro: false`).
- 0:23,86  GET `/api/notificacoes/listar/1` (HTTP 200), com a nova mensagem de teste.

**Conclusão:** Aprovado conforme a gravação. O resultado cobre a criação, a prévia e a listagem. A entrega efetiva no aplicativo dos alunos não foi verificada.

## Critérios de aceitação para nova execução

1. A prévia exibe o texto digitado.
2. A criação retorna sucesso.
3. A consulta após a criação inclui o novo aviso.

## Próxima ação e verificações complementares

Usar como regressão da criação e validar o recebimento em um dispositivo de teste em uma execução dedicada.

## Evidências e limites

- Jam 3 — Criação de notificação com prévia (gravação restrita por conter dados de integração ou dados de alunos).
- [Arquivos, origem e limites](../Evidencias/CT-RF159_Aplicativo_Criar_Notificacao_Preview/README.md).
- [Mensagem de teste no formulário e na prévia para celular](../Evidencias/CT-RF159_Aplicativo_Criar_Notificacao_Preview/mensagem_e_previa_00-18.jpg), [Novo aviso de teste no início da listagem](../Evidencias/CT-RF159_Aplicativo_Criar_Notificacao_Preview/notificacao_criada_00-26.jpg).
- [Linha do tempo](../Evidencias/CT-RF159_Aplicativo_Criar_Notificacao_Preview/linha_do_tempo.txt).

A revisão documental se baseia nos quadros do vídeo e nos eventos capturados pelo Jam. As verificações complementares ficam para uma nova rodada de testes.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf159) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
