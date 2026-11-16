# 🧪 Cenário 58: Edição de grupo — alteração de status não persiste

**Caso de teste:** CT-RF58

**Módulo:** Treinamento / Grupos

**Status:** Reprovado nas evidências.

**Gravação:** 15/11/2026, 21h03 BRT. **Revisão documental:** 15/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Editar um grupo pela listagem (nome, descrição, exibição na home, tipo de caixa e status) e confirmar que todos os campos alterados são persistidos pelo backend. |
| Requisito | [RF58](../Analise%20de%20requisitos.md#rf58) |
| Tipo / prioridade | Funcional manual, análise de evidências / Alta, proposta para triagem. |
| Defeito | [BUG-025](../Relatorio-de-Bugs.md#bug-025) |
| Encaminhamento | Investigar o tratamento do campo `status` em `/api/edita/grupo/{id}`; confirmar se o mesmo padrão ocorre em outras entidades; corrigir e retestar a edição de cada campo isoladamente. |
| Fonte | [Jam — Tela de Grupos](https://jam.dev/c/b1231a75-1a65-4bf0-b795-f52a8c7d3365) |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/grupos |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.78 / Windows (x86) 11. |
| Tela / arquivo de vídeo | 1920 × 911 informados no Jam. |
| Duração | 1 min 38 s |
| Rede | Classificada como rápida no Jam: mais de 10 Mbps, latência de 50 ms. |
| Localização | Brasil. |
| Servidor | Respostas com `x-powered-by: PHP/8.2.35`, `servidor: hcdn`, `plataforma: hospedagem`. |
| Versão / zoom / classificação do ambiente | Não confirmados; registrar antes de nova execução. |
| Dados | Usar dados de teste conhecidos conforme as pré-condições abaixo; valores da gravação são referência histórica, sem copiar credenciais. |

## Pré-condições

- Sessão autenticada com permissão para editar grupos.
- Existir na listagem um grupo de teste cuja edição seja permitida pelas regras do produto.
- Conhecer o estado atual de todos os campos do grupo antes da edição, para comparar cada campo isoladamente após salvar.
- Antes de uma nova execução, identificar versão, permissões e dados de referência e preparar a captura de interface e rede.

## Cenário BDD

```gherkin
Cenário: Editar o status de um grupo
  Dado que o usuário está autenticado na tela Grupos
  E existe o grupo código 11 ("Treino sla") na listagem, com status "Ativo"
  Quando abrir a edição do grupo e alterar o campo Status para "Inativo"
  E acionar o botão Salvar
  Então o sistema deve retornar sucesso
  E o status do grupo deve ser persistido como "Inativo" na próxima consulta
```

## Passos para execução ou reteste

1. Acessar a tela Grupos autenticado e abrir a edição do grupo de teste.
2. Alterar apenas o campo Status para "Inativo", mantendo os demais campos inalterados.
3. Acionar o botão Salvar e conferir a resposta da API no painel de rede.
4. Recarregar a página (ou reabrir a edição) e consultar novamente o registro para verificar se o status foi persistido.
5. Repetir o procedimento alterando outro campo isoladamente (por exemplo, a descrição), para comparar o comportamento entre campos.

Este procedimento orienta a próxima execução. A evidência atual cobre o trecho gravado e os limites descritos abaixo; a repetição controlada campo a campo não recebe resultado de execução nesta revisão.

## Resultado esperado

Ao salvar a edição de qualquer campo do grupo, o backend deve persistir o valor alterado; uma consulta subsequente ao registro deve refletir o novo valor, qualquer que seja o campo editado.

## Resultado obtido na gravação

Na mesma gravação, o grupo "Treino sla" (código 11) é editado duas vezes. Na primeira edição, apenas o campo Status é alterado de "Ativo" para "Inativo"; o servidor responde com sucesso, mas a consulta imediatamente seguinte ao mesmo registro mostra o status ainda como "Ativo" — a alteração não foi persistida. Na segunda edição, apenas o campo Descrição é alterado; essa alteração é persistida corretamente, confirmada na consulta seguinte. Isso indica que a falha é específica do campo `status` nessa rotina, e não uma falha geral de salvamento, sessão ou rede.

**Momentos e registros:**

| Tempo | Registro |
| --- | --- |
| 0:58 | Clicou no botão `<tipo="enviar" classe="gru-btn-salvar">` após selecionar Status = "Inativo" no formulário do grupo 11. |
| 0:58 (rede) | `POST https://backendsifit.centrion.com.br/api/edita/grupo/1` com `{"id":11,"nome":"Treino sla","mostrar_home":"nao","caixa":"interno","descricao":"Esse treino","status":"inativo"}` retorna **HTTP 200**, `{"verifica_erro": false}`. |
| mesmo instante | `GET /api/grupos/1` (lista) e `POST /api/seleciona/grupo/1` (detalhe) retornam o grupo id 11 ainda com `"status": "ativo"`, `"updated_at": "2026-11-16 12:02:46"`. |
| 1:00–1:09 | Reabre a edição; seleciona campos e apaga parte do texto da descrição (de "Esse treino" para "Ess"). |
| 1:10 | Clicou novamente no botão `gru-btn-salvar`. `POST /api/edita/grupo/1` com `{"id":11,"nome":"Treino sla","mostrar_home":"nao","caixa":"interno","descricao":"Ess","status":"ativo"}` retorna **HTTP 200**, `{"verifica_erro": false}`. |
| mesmo instante | Nova consulta (`GET /api/grupos/1` e `POST /api/seleciona/grupo/1`) confirma `"descricao": "Ess"` persistida; `"status": "ativo"` permanece (sem nova tentativa de alterá-lo nesta etapa). |
| 1:13 | Clicou no botão `gru-btn-action`, reabrindo o painel do grupo; a consulta confirma os mesmos dados. |
| 1:16 | Clicou no botão `gru-btn-cancelar`, fechando o painel sem nova alteração. |

**Resposta do servidor na tentativa de alterar o status (0:58):**

```json
{
  "verifica_erro": false
}
```

**Registro consultado logo em seguida (`seleciona/grupo/1`), ainda com o status antigo:**

```json
{
  "id": 11,
  "empresa_id": 1,
  "nome": "Treino sla",
  "descricao": "Esse treino",
  "mostrar_home": "nao",
  "caixa": "interno",
  "status": "ativo",
  "created_at": "2026-11-16 00:02:25",
  "updated_at": "2026-11-16 12:02:46"
}
```

**Cabeçalhos registrados:** `content-type: application/json; charset=utf-8`, `x-powered-by` não capturado nesta tela; primeira tentativa (alteração de status) em `Segunda-feira, 16 de novembro de 2026, 08:02:46 GMT`; segunda tentativa (alteração de descrição) em `08:02:58 GMT`. O campo `updated_at` do corpo da resposta registra `12:02:46` e `12:02:58` para os mesmos instantes — um descompasso de cerca de 4 horas em relação ao cabeçalho HTTP `data`, sem causa determinada nesta revisão; não foi relacionado ao defeito de status por falta de evidência suficiente.

**Conclusão:** Reprovado nas evidências. A edição do campo `status` retorna sucesso sem persistir o valor; a edição do campo `descricao`, na mesma sessão e no mesmo registro, persiste normalmente. A causa da falha isolada no campo `status` não foi determinada.

## Critérios de aceitação para nova execução

1. A edição de qualquer campo do grupo retorna sucesso somente quando o valor é efetivamente persistido.
2. O campo Status, especificamente, é persistido ao ser alterado e confirmado por consulta subsequente.
3. Uma resposta de sucesso (`verifica_erro: false`) nunca é retornada para uma alteração que não foi salva.
4. O resultado se mantém após recarga da página e nova consulta ao registro.
5. O comportamento é validado também para outros grupos e, se aplicável, para a entidade grupo muscular.

## Próxima ação e verificações complementares

Investigar a rotina de edição do grupo no backend (`/api/edita/grupo/{id}`), com foco em por que o campo `status` não é aplicado ao registro mesmo com resposta de sucesso — por exemplo, uma whitelist de campos editáveis que exclui `status`, ou uma rotina de atualização que ignora esse campo silenciosamente. Verificar se o mesmo ocorre ao tentar reativar um grupo (Inativo → Ativo) e em outras entidades com campo de status semelhante, inclusive grupo muscular, dado o padrão de nomenclatura de endpoints já observado em [BUG-016](../Relatorio-de-Bugs.md#bug-016) e [BUG-024](../Relatorio-de-Bugs.md#bug-024).

A gravação não permite distinguir entre uma falha de validação no backend, um campo ausente do contrato real da API (apesar de enviado pelo frontend) ou uma falha pontual de cache na consulta de releitura; não houve acesso a logs do servidor nem consulta direta ao banco de dados para confirmar o valor realmente gravado.

## Manifestações relacionadas na mesma gravação

Esta edição ocorre sobre o mesmo grupo ("Treino sla", código 11) cujo cadastro é mencionado em [CT-RF57](CT-RF57_Exclusao_Grupo.md) e cuja tentativa de exclusão (do grupo código 1, "Treino Livre") está documentada no mesmo cenário. Os três fluxos — cadastro, edição e exclusão — ocorrem na mesma gravação, mas são tratados em registros separados para não reunir causas distintas em um mesmo cenário.

## Evidências e limites

- [Jam original — Tela de Grupos](https://jam.dev/c/b1231a75-1a65-4bf0-b795-f52a8c7d3365).
- Painel Informações do Jam: URL, carimbo de data/hora, sistema, navegador, tamanho da janela e rede.
- Painel Rede do Jam: requisições de edição (`POST /api/edita/grupo/1`) e de releitura (`GET /api/grupos/1`, `POST /api/seleciona/grupo/1`) entre 0:58 e 1:16, com cabeçalhos e corpo de resposta.
- Painel Console do Jam, visão de atividade do usuário: cronologia de cliques e seleções entre 0:57 e 1:16.
- Quadros e registros de rede consultados: 0:57–0:58, 1:00–1:09, 1:10, 1:13 e 1:16.
- Pasta local de evidências: a criar em `Evidencias/CT-RF58_Edicao_Grupo/`; até lá, a fonte é o Jam indicado acima.

Não foram registradas mensagens de console JavaScript na visão consultada, apenas os eventos de interação e de rede. A causa da falta de persistência do campo `status` não foi determinada: não houve acesso a logs do servidor, ao código da rotina de edição, nem consulta ao banco de dados. A hipótese de o descompasso entre `data` (cabeçalho HTTP) e `updated_at` (corpo da resposta) ter relação com o defeito não foi confirmada nem descartada.

Análise documental da gravação consultada em 15/11/2026, com leitura direta dos painéis do Jam. Esta inclusão não executa novamente o sistema, não corrige a aplicação e não constitui reteste. Versão da aplicação, zoom e classificação do ambiente não foram confirmados.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
