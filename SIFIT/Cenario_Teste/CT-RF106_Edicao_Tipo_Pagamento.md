# 🧪 Cenário 106: Edição de tipo de pagamento pela lupa da listagem

**Caso de teste:** CT-RF106

**Módulo:** Financeiro / Tipos de Pagamento / Edição

**Status:** Aprovado conforme a gravação.

**Gravação:** 15/11/2026, 22:03 BRT. **Revisão documental:** 15/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Abrir um tipo de pagamento pela lupa da listagem, alterar a opção Pagamento Pelo Sistema e salvar, com a listagem e o cartão Via gateway refletindo a alteração. |
| Requisito | [RF106](../Analise%20de%20requisitos.md#rf106) — referência de QA; confirmação de produto pendente. |
| Tipo / prioridade | Funcional manual / regressão; Média, proposta para triagem. |
| Defeito | Nenhum no fluxo avaliado |
| Encaminhamento | Usar como regressão; persistência após recarga, edição de nome e tipo e a coluna Status exigem execuções adicionais. |
| Fonte | [Jam — Tipos de Pagamento](https://jam.dev/c/e8734e3d-3f8e-458b-8c7d-e85eea882e50) e [evidências locais](../Evidencias/CT-RF106_Edicao_Tipo_Pagamento/README.md). A mesma gravação é a fonte de [CT-RF104](CT-RF104_Filtros_Tipos_Pagamento.md), [CT-RF105](CT-RF105_Cadastro_Tipo_Pagamento_Status.md), [CT-RF107](CT-RF107_Exclusao_Tipo_Pagamento_Em_Uso.md) e [CT-RF108](CT-RF108_Tema_Notificacoes_Tipos_Pagamento.md). |

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
| Dados | Tipo Dinheiro (código 1; Crédito; Pagamento Pelo Sistema Sim → Não; Escolher Bandeira Sim); Via gateway 6 antes e 5 depois. |

## Pré-condições

- Sessão autenticada com acesso à tela Tipos de Pagamento.
- Base de tipos de pagamento conhecida (16 tipos no início da gravação, todos exibidos como Inativo), com tipos usados em contas a receber e um tipo descartável para cadastro.
- Antes de uma nova execução, identificar versão, permissões e dados de referência e preparar a captura de interface e rede.

## Cenário BDD

```gherkin
Cenário: Editar um tipo de pagamento
  Dado que a listagem de tipos de pagamento está aberta
  Quando o usuário abrir o tipo Dinheiro pela lupa, alterar Pagamento Pelo Sistema para Não e acionar Salvar
  Então a alteração deve ser gravada sem erro
  E a listagem e o cartão Via gateway devem refletir a alteração
```

## Passos para execução ou reteste

1. Acionar a lupa da linha do tipo Dinheiro (código 1) e conferir os campos carregados.
2. Alterar Pagamento Pelo Sistema de Sim para Não.
3. Acionar Salvar e capturar a requisição e a resposta.
4. Conferir a listagem recarregada e o cartão Via gateway.
5. Recarregar a página e reabrir o tipo.

Este procedimento orienta a próxima execução. A evidência atual cobre o trecho gravado e os limites descritos abaixo; passos complementares não recebem resultado de execução nesta revisão.

## Resultado esperado

O tipo é aberto com os dados gravados, a alteração é salva sem erro, e a listagem e o cartão Via gateway refletem o novo valor.

## Resultado obtido na gravação

A lupa abriu o tipo Dinheiro (`POST seleciona/tipo-pagamento/1` com `{"id": 1}`, HTTP 200, 174 B); a alteração de Pagamento Pelo Sistema para Não foi salva (`POST edita/tipo-pagamento/1`, HTTP 200, `verifica_erro` false), a lista foi recarregada e o tipo Dinheiro passou a exibir "Não" em Via gateway, com o cartão Via gateway de 6 para 5.

| Tempo | Registro |
| --- | --- |
| 0:32 | Clique na lupa da linha do código 1 (Dinheiro); `POST seleciona/tipo-pagamento/1` devolve o tipo (tipo "credito", via_gateway "sim"). |
| 0:33–0:34 | Alteração de Pagamento Pelo Sistema para Não; clique em Salvar. |
| 0:34 | Botão em "Salvando..." no modal; `POST edita/tipo-pagamento/1` com HTTP 200 e `verifica_erro` false. |
| 0:45 | Listagem recarregada: Dinheiro com Via gateway "Não"; Total 17 e Via gateway 5. |

**Rede:** `POST /api/seleciona/tipo-pagamento/1` (HTTP 200, 174 B) com `{"id": 1}`; `POST /api/edita/tipo-pagamento/1` (HTTP 200, 23 B) com `"id": 1`, `"nome": "Dinheiro"`, `"tipo": "credito"`, `"via_gateway": "nao"` e `"escolher_bandeira": "sim"`; resposta `{"verifica_erro": false}`.

**Conclusão:** Aprovado conforme a gravação. O fluxo gravado concluiu a edição sem erro e a listagem refletiu a alteração; a aprovação se limita ao exemplo gravado.

## Critérios de aceitação para nova execução

1. O tipo selecionado é aberto com os valores gravados.
2. A alteração é gravada sem mensagem de erro.
3. A listagem e o cartão Via gateway refletem a alteração.
4. A alteração persiste após recarregar a página.
5. A edição de nome e de tipo também é gravada.

## Próxima ação e verificações complementares

Usar como regressão; verificar persistência após recarga, edição de nome e tipo e a coluna Status.

## Evidências e limites

- [Jam original — Tipos de Pagamento](https://jam.dev/c/e8734e3d-3f8e-458b-8c7d-e85eea882e50).
- [Arquivos, origem e limites](../Evidencias/CT-RF106_Edicao_Tipo_Pagamento/README.md).
- [Modal de edição em 0:34](../Evidencias/CT-RF106_Edicao_Tipo_Pagamento/edicao_salvando_00-34.jpg), [Listagem em 0:45](../Evidencias/CT-RF106_Edicao_Tipo_Pagamento/lista_apos_edicao_00-45.jpg), [Lista de rede](../Evidencias/CT-RF106_Edicao_Tipo_Pagamento/rede_lista.jpg).
- [Linha do tempo](../Evidencias/CT-RF106_Edicao_Tipo_Pagamento/linha_do_tempo.txt).

Foram consultados os painéis Info, Console, Network e Actions do Jam e os quadros do vídeo. As capturas foram extraídas da reprodução do Jam. Não houve nova execução, inspeção do código, acesso ao banco ou correção da aplicação. O vídeo permanece no Jam.

Análise documental da gravação consultada em 15/11/2026. Esta inclusão não executa novamente o sistema e não constitui reteste. Versão da aplicação, zoom e classificação do ambiente não foram confirmados.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf106) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
