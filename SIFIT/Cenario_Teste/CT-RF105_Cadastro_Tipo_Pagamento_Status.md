# 🧪 Cenário 105: Cadastro de tipo de pagamento com status Ativo não é refletido

**Caso de teste:** CT-RF105

**Módulo:** Financeiro / Tipos de Pagamento / Cadastro

**Status:** Reprovado nas evidências — status Ativo escolhido não é enviado nem refletido; defeito em triagem.

**Gravação:** 15/11/2026, 22:03 BRT. **Revisão documental:** 15/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Cadastrar um tipo de pagamento informando nome, status, tipo, escolha de bandeira e pagamento pelo sistema, e conferir que o tipo aparece na listagem com os valores informados, inclusive o status. |
| Requisito | [RF105](../Analise%20de%20requisitos.md#rf105) — referência de QA; confirmação de produto pendente. |
| Tipo / prioridade | Funcional manual / cadastro e persistência; Média, proposta para triagem. |
| Defeito | [BUG-042](../Relatorio-de-Bugs.md#bug-042), em triagem. |
| Encaminhamento | Registrar o BUG-042 em triagem, confirmar com o produto se o status faz parte do tipo de pagamento e reproduzir verificando o corpo da requisição, a resposta da lista e a coluna Status. |
| Fonte | [Jam — Tipos de Pagamento](https://jam.dev/c/e8734e3d-3f8e-458b-8c7d-e85eea882e50) e [evidências locais](../Evidencias/CT-RF105_Cadastro_Tipo_Pagamento_Status/README.md). A mesma gravação é a fonte de [CT-RF104](CT-RF104_Filtros_Tipos_Pagamento.md), [CT-RF106](CT-RF106_Edicao_Tipo_Pagamento.md), [CT-RF107](CT-RF107_Exclusao_Tipo_Pagamento_Em_Uso.md) e [CT-RF108](CT-RF108_Tema_Notificacoes_Tipos_Pagamento.md). |

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
| Dados | Tipo "44444", Status "Ativo" (valor do modal), Tipo "Débito", Escolher Bandeira "Sim" e Pagamento Pelo Sistema "Sim" no corpo enviado; 16 tipos e Ativos 0 antes do cadastro. |

## Pré-condições

- Sessão autenticada com acesso à tela Tipos de Pagamento.
- Base de tipos de pagamento conhecida (16 tipos no início da gravação, todos exibidos como Inativo), com tipos usados em contas a receber e um tipo descartável para cadastro.
- Antes de uma nova execução, identificar versão, permissões e dados de referência e preparar a captura de interface e rede.

## Cenário BDD

```gherkin
Cenário: Cadastrar tipo de pagamento ativo
  Dado que o modal Tipo de Pagamento está aberto com o status Ativo
  Quando o usuário informar nome, tipo, escolha de bandeira e pagamento pelo sistema e acionar Salvar
  Então o tipo deve ser criado e listado com os valores informados
  E o cartão Ativos e a coluna Status devem refletir o status escolhido
```

## Passos para execução ou reteste

1. Acionar Novo e registrar os cartões e a listagem iniciais.
2. Informar o nome, manter o Status Ativo e escolher Tipo, Escolher Bandeira e Pagamento Pelo Sistema.
3. Acionar Salvar e capturar o corpo e a resposta da criação.
4. Conferir a listagem recarregada, a coluna Status do novo tipo e os cartões Total, Ativos e Inativos.
5. Reabrir o tipo e conferir o status gravado.

Este procedimento orienta a próxima execução. A evidência atual cobre o trecho gravado e os limites descritos abaixo; passos complementares não recebem resultado de execução nesta revisão.

## Resultado esperado

O tipo é criado, aparece na listagem com nome, tipo, via gateway e o status escolhido, e os cartões acompanham a inclusão (Total 17 e Ativos 1 para um tipo ativo).

## Resultado obtido na gravação

A criação foi concluída (`POST cria/tipo-pagamento/1`, HTTP 201, `verifica_erro` false) e os cartões passaram de Total 16 / Inativos 16 / Via gateway 5 para Total 17 / Inativos 17 / Via gateway 6, mas o cartão Ativos permaneceu em 0. O corpo enviado traz nome, tipo, via_gateway e escolher_bandeira, sem campo de status, e os registros devolvidos pela API não trazem status; o modal ofereceu Status "Ativo" e a listagem exibe todos os tipos como Inativo.

| Tempo | Registro |
| --- | --- |
| 0:19 | Modal Tipo de Pagamento: Nome "44444", Status "Ativo", Escolher Bandeira "Não", Tipo "Débito" e Pagamento Pelo Sistema "Não". |
| 0:20–0:24 | Cliques nos seletores do formulário; em 0:24 o quadro mostra Escolher Bandeira "Sim" e Pagamento Pelo Sistema ainda "Não" (o corpo enviado traz "sim" nos dois). |
| 0:25 | Clique em Salvar: `POST cria/tipo-pagamento/1` com HTTP 201 e novo `GET tipo-pagamento/1`. |
| 0:27 | Listagem recarregada: cartões Total 17, Ativos 0, Inativos 17 e Via gateway 6; todos os tipos visíveis com status Inativo. |

**Rede:** `POST /api/cria/tipo-pagamento/1` (HTTP 201, 23 B) com `"nome": "44444"`, `"tipo": "debito"`, `"via_gateway": "sim"` e `"escolher_bandeira": "sim"`, sem campo de status; resposta `{"verifica_erro": false}`. Os registros de `GET /api/tipo-pagamento/1` lidos (ids 1, 3, 4 e 5) trazem id, empresa_id, nome, tipo, via_gateway, escolher_bandeira, created_at e updated_at, sem campo de status.

**Conclusão:** Reprovado nas evidências. O cadastro é criado (HTTP 201), mas o status escolhido (Ativo) não é enviado nem devolvido pela API, todos os tipos aparecem como Inativo e o cartão Ativos fica em 0. A reprovação se apoia na expectativa de que o status oferecido no modal seja gravado e refletido; a regra não foi informada e o novo tipo não está visível nos quadros (fica abaixo da dobra).

## Critérios de aceitação para nova execução

1. O status escolhido no modal é enviado ao servidor e gravado.
2. A listagem apresenta o status real de cada tipo, e não um valor fixo.
3. O cartão Ativos conta os tipos ativos e Inativos os demais.
4. O novo tipo aparece na listagem com nome, tipo, via gateway e status informados.
5. Reabrir o tipo mostra os valores gravados.

## Próxima ação e verificações complementares

Registrar o BUG-042 em triagem, confirmar com o produto se o status faz parte do cadastro e reproduzir conferindo o corpo, a resposta da lista, a coluna Status e os cartões; retestar com status Ativo e Inativo.

## Observação sobre o modal de edição

Ao abrir o tipo Dinheiro (código 1) para edição, o modal exibiu Status "Ativo" enquanto a listagem exibia o mesmo tipo como Inativo (quadro de 0:34); a divergência é compatível com o seletor de Status ser apenas visual, sem valor de origem.

## Evidências e limites

- [Jam original — Tipos de Pagamento](https://jam.dev/c/e8734e3d-3f8e-458b-8c7d-e85eea882e50).
- [Arquivos, origem e limites](../Evidencias/CT-RF105_Cadastro_Tipo_Pagamento_Status/README.md).
- [Cartões antes do cadastro em 0:00](../Evidencias/CT-RF105_Cadastro_Tipo_Pagamento_Status/cartoes_antes_00-00.jpg), [Modal em 0:19](../Evidencias/CT-RF105_Cadastro_Tipo_Pagamento_Status/modal_cadastro_00-19.jpg), [Modal em 0:24](../Evidencias/CT-RF105_Cadastro_Tipo_Pagamento_Status/modal_selecoes_00-24.jpg), [Listagem em 0:27](../Evidencias/CT-RF105_Cadastro_Tipo_Pagamento_Status/lista_apos_cadastro_00-27.jpg), [Lista de rede](../Evidencias/CT-RF105_Cadastro_Tipo_Pagamento_Status/rede_lista.jpg).
- [Linha do tempo](../Evidencias/CT-RF105_Cadastro_Tipo_Pagamento_Status/linha_do_tempo.txt).

Foram consultados os painéis Info, Console, Network e Actions do Jam e os quadros do vídeo. As capturas foram extraídas da reprodução do Jam. Não houve nova execução, inspeção do código, acesso ao banco ou correção da aplicação. O vídeo permanece no Jam.

Análise documental da gravação consultada em 15/11/2026. Esta inclusão não executa novamente o sistema e não constitui reteste. Versão da aplicação, zoom e classificação do ambiente não foram confirmados.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf105) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
