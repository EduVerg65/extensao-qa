# 🧪 Cenário 103: Edição de pergunta de anamnese retorna HTTP 500

**Caso de teste:** CT-RF103

**Módulo:** Saúde / Perguntas (Anamnese)

**Status:** Reprovado nas evidências.

**Gravação:** 16/11/2026, 15h57 BRT. **Revisão documental:** 16/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Pesquisar e filtrar perguntas de anamnese, cadastrar uma nova pergunta e editá-la (tipo de resposta e status), confirmando que o backend processa cada operação sem erro. |
| Requisito | [RF103](../Analise%20de%20requisitos.md#rf103--editar-pergunta-de-anamnese-sem-erro-de-servidor) |
| Tipo / prioridade | Funcional manual, análise de evidências / Alta. |
| Defeito | [BUG-044](../Relatorio-de-Bugs.md#bug-044), em triagem. |
| Encaminhamento | Investigar a rotina de `alterar` de perguntas de anamnese com acesso a logs; não liberar a edição do tipo de resposta até a causa ser confirmada. |
| Fonte | [Jam — Perguntas Anamnese](https://jam.dev/c/84b116fb-4640-4b1e-9148-9a169b8aa2b0) |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/perguntas-anamnese |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.78 / Windows 11. |
| Duração | 1 min 30 s |
| Localização | Brasil. |
| Servidor | Respostas com `plataforma: hospedagem`, `servidor: hcdn`, `x-powered-by: PHP/8.2.35`. |
| Versão / zoom / classificação do ambiente | Não confirmados; registrar antes de nova execução. |
| Dados | Usar dados de teste conhecidos conforme as pré-condições abaixo; valores da gravação (nome, texto e tipo de resposta da pergunta) são referência histórica, sem copiar credenciais. |

## Pré-condições

- Sessão autenticada com permissão para gerenciar perguntas de anamnese.
- Existir ao menos uma pergunta de anamnese já cadastrada, para exercitar o filtro por código, nome e status.
- Antes de uma nova execução, identificar versão, permissões e dados de referência e preparar a captura de interface e rede.

## Cenário BDD

```gherkin
Cenário: Editar o tipo de resposta de uma pergunta de anamnese
  Dado que o usuário está autenticado na tela Perguntas Anamnese
  E uma pergunta foi cadastrada com um tipo de resposta
  Quando reabrir a pergunta pela ação de editar
  E alterar o tipo de resposta ou o status
  E acionar "Salvar"
  Então o sistema deve persistir a alteração e retornar sucesso
  E refletir o resultado na listagem de perguntas
```

## Passos para execução ou reteste

1. Acessar a tela Perguntas Anamnese autenticado.
2. Filtrar pelos campos Código e Nome da pergunta e pelo seletor de Status, conferindo o comportamento do filtro.
3. Acionar "Buscar" com um termo digitado e, em seguida, "Nova Pergunta".
4. Preencher o nome, o texto da pergunta, selecionar o tipo de resposta e preencher os campos numéricos das opções, e salvar.
5. Reabrir a pergunta recém-criada pela ação de editar.
6. Alterar o tipo de resposta (por exemplo, de "2 opções" para "3 opções") e salvar.
7. Repetir a alteração do tipo de resposta e, em seguida, apenas do status, salvando a cada tentativa.
8. Cancelar a edição caso as tentativas anteriores não sejam concluídas com sucesso.

Este procedimento orienta a próxima execução. A evidência atual cobre o trecho gravado e os limites descritos abaixo; a repetição controlada deste fluxo não recebe resultado de execução nesta revisão.

## Resultado esperado

Ao editar o tipo de resposta ou o status de uma pergunta de anamnese cadastrada, o backend deve processar a alteração e retornar sucesso, refletindo o resultado atualizado na listagem, sem erro de servidor.

## Resultado obtido na gravação

Ao longo da gravação, o usuário testa os filtros de código, nome e status da listagem de perguntas (sem gerar requisição de rede própria), pesquisa pelo botão "Buscar", cadastra uma nova pergunta ("Pergunta", tipo de resposta "2opcoes_complemento", status INATIVO) e, em seguida, tenta editar essa mesma pergunta por quatro vezes seguidas, alternando o tipo de resposta entre "3opcoes" e "2opcoes" e o status entre INATIVO e ATIVO. **As quatro tentativas de edição retornam HTTP 500**, todas com o mesmo corpo genérico `{"verifica_erro": true, "mensagem": "Erro interno inesperado."}`, no mesmo padrão já registrado nos BUG-016, BUG-024 e BUG-032. Após a quarta tentativa, o usuário cancela a edição sem conseguir salvar nenhuma alteração. A pergunta permanece cadastrada com o tipo de resposta e o status originais da criação. O cadastro inicial da pergunta, a busca/seleção da listagem e a alternância de tema (claro/escuro) são concluídos com sucesso (HTTP 200 ou 201), isolando o defeito à operação de edição (`alterar`).

**Momentos e registros:**

| Tempo | Registro |
| --- | --- |
| 0:01–0:16 | Testa os campos de filtro Código, Nome da pergunta e o seletor de Status, sem gerar requisição de rede. |
| 0:18–0:21 | Digita um termo de busca e aciona "Buscar". |
| 0:25 | Aciona "Nova Pergunta". |
| 0:26–0:49 | Preenche o nome ("Pergunta"), o texto da pergunta ("Pergunta isso"), seleciona o tipo de resposta e preenche os campos numéricos das opções. |
| 0:51 (rede) | Aciona "Salvar". `POST /api/pergunta-anamnese/salvar/1` retorna **HTTP 200/201** (duplicado em uma única ação), com corpo `{"nome": "Pergunta", "pergunta": "Pergunta isso", "resposta": "2opcoes_complemento", "numero": 12, "status": "INATIVO"}` — nova pergunta cadastrada com o id 11. |
| 0:57 | Aciona a busca/seleção da listagem novamente (`POST /api/pergunta-anamnese/selecionar/1`, HTTP 200/201). |
| 1:00 (rede) | Reabre a pergunta 11 pela edição e aciona "Salvar" com `resposta: "3opcoes"`, status INATIVO. `POST /api/pergunta-anamnese/alterar/1` retorna **HTTP 500**. |
| 1:03–1:04 (rede) | Fecha o aviso de erro e aciona "Salvar" novamente, com os mesmos valores (`resposta: "3opcoes"`, INATIVO). `POST /api/pergunta-anamnese/alterar/1` retorna **HTTP 500** outra vez. |
| 1:06–1:08 (rede) | Fecha o aviso, altera o tipo de resposta para `"2opcoes"` e aciona "Salvar". `POST /api/pergunta-anamnese/alterar/1` retorna **HTTP 500**. |
| 1:09–1:12 (rede) | Fecha o aviso, altera o status para ATIVO (mantendo `resposta: "2opcoes"`) e aciona "Salvar". `POST /api/pergunta-anamnese/alterar/1` retorna **HTTP 500** pela quarta vez. |
| 1:13–1:14 | Fecha o aviso de erro e aciona "Cancelar", descartando a edição sem nenhuma alteração salva. |
| 1:15–1:20 | Testa novamente o filtro de Status e aciona um ícone de ação sobre um cartão da listagem, sem gerar nova requisição de rede identificada. |
| 1:21–1:28 (rede) | Alterna o tema claro/escuro. Três requisições `POST /api/usuario/tema` retornam **HTTP 200**. |

**Requisições de edição, todas com resposta HTTP 500 (1:00, 1:04, 1:08 e 1:12):**

```
POST https://backendsifit.centrion.com.br/api/pergunta-anamnese/alterar/1
Corpo (1:00 e 1:04): {"id": 11, "nome": "Pergunta", "pergunta": "Pergunta isso", "resposta": "3opcoes", "numero": 12, "status": "INATIVO"}
Corpo (1:08): {"id": 11, "nome": "Pergunta", "pergunta": "Pergunta isso", "resposta": "2opcoes", "numero": 12, "status": "INATIVO"}
Corpo (1:12): {"id": 11, "nome": "Pergunta", "pergunta": "Pergunta isso", "resposta": "2opcoes", "numero": 12, "status": "ATIVO"}
Resposta (quatro ocorrências): HTTP 500 — {"verifica_erro": true, "mensagem": "Erro interno inesperado."}
```

**Cabeçalhos registrados:** `plataforma: hospedagem`, `servidor: hcdn`, `x-powered-by: PHP/8.2.35`; cada uma das quatro respostas de erro tem `x-hcdn-request-id` e horário próprios, confirmando que são quatro requisições distintas e não uma duplicação de exibição.

**Conclusão:** Reprovado nas evidências. O cadastro de uma nova pergunta de anamnese é concluído com sucesso, mas a edição dessa mesma pergunta — alterando o tipo de resposta, isoladamente ou em conjunto com o status — falha com HTTP 500 em todas as quatro tentativas registradas, impedindo qualquer atualização da pergunta após o cadastro.

## Critérios de aceitação para reteste

1. O filtro de código, nome e status na listagem de perguntas aplica-se de forma consistente, sem gerar erro.
2. Uma nova pergunta é cadastrada com nome, texto, tipo de resposta e status, e passa a constar na listagem.
3. Uma pergunta cadastrada pode ter o tipo de resposta alterado e salvo, sem erro de servidor, preservando a alteração.
4. Uma pergunta cadastrada pode ter o status alterado e salvo, isoladamente ou em conjunto com o tipo de resposta, sem erro de servidor.
5. Nenhuma das operações acima deve retornar erro HTTP 4xx ou 5xx em uso normal.

## Ponto a confirmar

O cadastro da pergunta (`POST /api/pergunta-anamnese/salvar/1`) foi registrado duas vezes para uma única ação de "Salvar" do usuário — uma com HTTP 200 e outra com HTTP 201 — padrão de duplicação por clique já observado em outros módulos (por exemplo, CT-RF51, despesas fixas). Isso não impede o cadastro, mas fica registrado para confirmação com a equipe de desenvolvimento, junto da causa do HTTP 500 na edição. Como as quatro tentativas de edição falharam com o mesmo erro genérico independentemente do valor de `resposta` (`"3opcoes"` ou `"2opcoes"`) ou do `status`, a falha parece estar na rotina de alteração em si (possivelmente ao tentar ajustar as opções/complementos associados ao tipo de resposta anterior, `"2opcoes_complemento"`, definido na criação), e não em um valor específico enviado — isso deve ser confirmado com acesso a logs e ao código da rotina de `alterar`.

## Evidências e limites

- [Jam original — Perguntas Anamnese](https://jam.dev/c/84b116fb-4640-4b1e-9148-9a169b8aa2b0).
- Painel Informações do Jam: URL, carimbo de data/hora, sistema, navegador e duração.
- Painel Rede do Jam: dezenove requisições identificadas, incluindo as quatro requisições de edição (`alterar/1`) com HTTP 500, entre 0:51 e 1:28.
- Painel Console do Jam: as quatro requisições de erro aparecem registradas em "Erros de rede", nos mesmos instantes (1:00, 1:04, 1:08 e 1:12) observados no painel Rede, sem outra mensagem de erro JavaScript.
- Painel Ações do Jam: cronologia completa de cliques, digitações e navegações entre 0:00 e 1:30.
- Quadros e registros de rede consultados: 0:51, 1:00, 1:04, 1:08, 1:12 e 1:21–1:28.
- Pasta local de evidências: a criar em `Evidencias/CT-RF62_Edicao_Pergunta_Anamnese/`; até lá, a fonte é o Jam indicado acima.

Não foi possível confirmar, pela gravação, o significado exato do campo `numero` no corpo das requisições, nem a contagem final de perguntas (ativas/inativas/com complemento) após as tentativas de edição, já que nenhuma delas foi persistida. Não houve nova execução, acesso a logs, ao código ou ao banco, nem reteste.

Análise documental da gravação consultada em 16/11/2026, com leitura direta dos painéis do Jam. Esta inclusão não executa novamente o sistema, não corrige a aplicação e não constitui reteste. Versão da aplicação, zoom e classificação do ambiente não foram confirmados.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
