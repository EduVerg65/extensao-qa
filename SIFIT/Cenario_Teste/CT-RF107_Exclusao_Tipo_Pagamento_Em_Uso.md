# 🧪 Cenário 107: Exclusão de tipo de pagamento em uso retorna HTTP 404 com erro SQL

**Caso de teste:** CT-RF107

**Módulo:** Financeiro / Tipos de Pagamento / Exclusão

**Status:** Reprovado nas evidências — exclusão de tipo em uso retorna HTTP 404 com erro SQL; defeito em triagem.

**Gravação:** 15/11/2026, 22:03 BRT. **Revisão documental:** 15/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Excluir um tipo de pagamento pela listagem com confirmação; quando o tipo estiver em uso por contas a receber, a exclusão deve ser impedida com mensagem clara ao usuário e sem expor detalhes internos do banco. |
| Requisito | [RF107](../Analise%20de%20requisitos.md#rf107) — referência de QA; confirmação de produto pendente. |
| Tipo / prioridade | Funcional manual / teste negativo; Média, proposta para triagem. |
| Defeito | [BUG-043](../Relatorio-de-Bugs.md#bug-043), em triagem. |
| Encaminhamento | Registrar o BUG-043 em triagem, confirmar a regra de exclusão de tipos em uso e reproduzir com um tipo em uso e outro sem uso, conferindo o código HTTP, a resposta e a mensagem da tela. |
| Fonte | [Jam — Tipos de Pagamento](https://jam.dev/c/e8734e3d-3f8e-458b-8c7d-e85eea882e50) e [evidências locais](../Evidencias/CT-RF107_Exclusao_Tipo_Pagamento_Em_Uso/README.md). A mesma gravação é a fonte de [CT-RF104](CT-RF104_Filtros_Tipos_Pagamento.md), [CT-RF105](CT-RF105_Cadastro_Tipo_Pagamento_Status.md), [CT-RF106](CT-RF106_Edicao_Tipo_Pagamento.md) e [CT-RF108](CT-RF108_Tema_Notificacoes_Tipos_Pagamento.md). |

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
| Dados | Tipos Dinheiro (código 1) e Cheque (código 3), usados por contas a receber (referência na restrição de chave estrangeira); nenhum tipo sem uso foi excluído na gravação. |

## Pré-condições

- Sessão autenticada com acesso à tela Tipos de Pagamento.
- Base de tipos de pagamento conhecida (16 tipos no início da gravação, todos exibidos como Inativo), com tipos usados em contas a receber e um tipo descartável para cadastro.
- Antes de uma nova execução, identificar versão, permissões e dados de referência e preparar a captura de interface e rede.

## Cenário BDD

```gherkin
Cenário: Excluir um tipo de pagamento em uso
  Dado que o tipo de pagamento é referenciado por contas a receber
  Quando o usuário acionar o ícone de exclusão e confirmar o diálogo
  Então a exclusão deve ser impedida com mensagem clara sobre o uso do tipo
  E a resposta do servidor não deve expor detalhes internos do banco
```

## Passos para execução ou reteste

1. Acionar o ícone de exclusão da linha de um tipo em uso e confirmar o diálogo.
2. Registrar o código HTTP, o corpo da resposta e a mensagem da tela.
3. Repetir com um segundo tipo em uso.
4. Repetir com um tipo sem uso e conferir a remoção da listagem e dos cartões.
5. Conferir se a listagem permanece íntegra após a falha.

Este procedimento orienta a próxima execução. A evidência atual cobre o trecho gravado e os limites descritos abaixo; passos complementares não recebem resultado de execução nesta revisão.

## Resultado esperado

Um tipo em uso não é excluído e o usuário recebe mensagem clara; a resposta do servidor não expõe detalhes internos e usa um código HTTP compatível; um tipo sem uso é removido.

## Resultado obtido na gravação

Os dois `POST deleta/tipo-pagamento/1` (ids 1 e 3) retornaram HTTP 404 com `verifica_erro` true e o texto integral do erro SQL (violação de chave estrangeira com `contas_receber`, nome do esquema do banco e da restrição). A tela exibiu apenas o diálogo "Erro / Erro ao deletar tipo de pagamento", sem informar que o tipo está em uso, e a listagem permaneceu com 17 tipos.

| Tempo | Registro |
| --- | --- |
| 0:36–0:37 | Clique no ícone de exclusão do código 1; diálogo "Deseja deletar o Tipo de Pagamento?" com Cancelar e Confirmar. |
| 0:40 | Confirmar: `POST deleta/tipo-pagamento/1` retorna HTTP 404 (359 B); diálogo "Erro — Erro ao deletar tipo de pagamento". |
| 0:41 | Fechar o diálogo; listagem sem alteração (Total 17). |
| 0:42–0:43 | Segundo ícone de exclusão (código 3) e novo diálogo de confirmação. |
| 0:43–0:45 | Confirmar: novo `POST deleta/tipo-pagamento/1` com HTTP 404; listagem permanece com Total 17. |

**Rede:** `POST /api/deleta/tipo-pagamento/1` (HTTP 404, 359 B) com `{"id": 1}` e, depois, `{"id": 3}`; resposta `{"verifica_erro": true, "erro": "SQLSTATE[23000]: Integrity constraint violation: 1451 Cannot delete or update a parent row: a foreign key constraint fails (...)"}`, com o nome do esquema do banco, da tabela `contas_receber` e da restrição `fk_contas_receber_tipo_pagamentos1`.

**Conclusão:** Reprovado nas evidências. A exclusão de tipos em uso falha com HTTP 404, a resposta da API expõe o erro SQL completo (esquema, tabela e restrição) e a tela mostra apenas uma mensagem genérica. A reprovação se apoia nas expectativas de resposta com código compatível, mensagem clara ao usuário e ausência de detalhes internos; a regra de exclusão de tipos em uso não foi informada.

## Critérios de aceitação para nova execução

1. A exclusão de um tipo em uso é impedida com mensagem clara que informe o uso.
2. A resposta do servidor não expõe nomes de esquema, tabela ou restrição do banco.
3. O código HTTP é compatível com o conflito (por exemplo 409) e não 404.
4. A listagem e os cartões permanecem íntegros após a falha.
5. Um tipo sem uso é excluído e removido da listagem.

## Próxima ação e verificações complementares

Registrar o BUG-043 em triagem, confirmar a regra de exclusão e reproduzir com tipo em uso e sem uso conferindo código HTTP, resposta e mensagem.

## Observação sobre a exposição de dados internos

O texto do erro inclui o nome do esquema do banco, da tabela e da restrição; o registro apenas descreve a presença desses dados na resposta, sem reproduzi-los além do necessário. A sensibilidade da informação e o canal de tratamento ficam a critério da triagem.

## Evidências e limites

- [Jam original — Tipos de Pagamento](https://jam.dev/c/e8734e3d-3f8e-458b-8c7d-e85eea882e50).
- [Arquivos, origem e limites](../Evidencias/CT-RF107_Exclusao_Tipo_Pagamento_Em_Uso/README.md).
- [Diálogo de confirmação em 0:37](../Evidencias/CT-RF107_Exclusao_Tipo_Pagamento_Em_Uso/dialogo_confirmar_00-37.jpg), [Diálogo de erro em 0:40](../Evidencias/CT-RF107_Exclusao_Tipo_Pagamento_Em_Uso/erro_exclusao_00-40.jpg), [Diálogo de confirmação em 0:43](../Evidencias/CT-RF107_Exclusao_Tipo_Pagamento_Em_Uso/dialogo_segundo_00-43.jpg), [Listagem em 0:45](../Evidencias/CT-RF107_Exclusao_Tipo_Pagamento_Em_Uso/lista_apos_erro_00-45.jpg), [Lista de rede](../Evidencias/CT-RF107_Exclusao_Tipo_Pagamento_Em_Uso/rede_lista.jpg).
- [Linha do tempo](../Evidencias/CT-RF107_Exclusao_Tipo_Pagamento_Em_Uso/linha_do_tempo.txt).

Foram consultados os painéis Info, Console, Network e Actions do Jam e os quadros do vídeo. As capturas foram extraídas da reprodução do Jam. Não houve nova execução, inspeção do código, acesso ao banco ou correção da aplicação. O vídeo permanece no Jam.

Análise documental da gravação consultada em 15/11/2026. Esta inclusão não executa novamente o sistema e não constitui reteste. Versão da aplicação, zoom e classificação do ambiente não foram confirmados.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf107) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
