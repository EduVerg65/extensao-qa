# 🧪 Cenário 40: Exclusão de turmas e modalidades em SifitBox – Turmas

**Caso de teste:** CT-RF40

**Módulo:** SifitBox / Turmas e Modalidades / Exclusão

**Status:** A validar — regra ou contexto pendente.

**Gravação:** 15/11/2026, 18:51 BRT. **Revisão documental:** 15/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Excluir turmas e modalidades pela lixeira da listagem, comunicando a regra aplicada e refletindo o resultado na listagem. |
| Requisito | [RF40](../Analise%20de%20requisitos.md#rf40) — referência de QA; confirmação de produto pendente. |
| Tipo / prioridade | Exploratório / regra a confirmar; Média, proposta para triagem. |
| Defeito | Sem defeito confirmado. |
| Encaminhamento | Confirmar com o produto se a exclusão é lógica (status "inativo"), se deve haver confirmação prévia e se registros inativos devem aparecer sob o filtro de status "Ativo". Registrar defeito apenas se houver divergência com a regra definida. |
| Fonte | [Jam — SifitBox – Turmas](https://jam.dev/c/ee9a133b-d6b1-442d-b4b0-dd87595b7e70) e [evidências locais](../Evidencias/CT-RF40_Exclusao_Turmas_Modalidades/README.md). A mesma gravação é a fonte de [CT-RF39](CT-RF39_Cadastro_Modalidade.md) e [CT-RF41](CT-RF41_Cadastro_Turma_Sem_Modalidade.md). |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/sifitbox/turmas |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.78 / Windows (x86) 11. |
| Tela / arquivo de vídeo | 1920 × 911 informados no Jam. |
| Duração | 1 min 39 s |
| Rede | Classificada como rápida no Jam: 6,8 Mbps, latência de 50 ms. |
| Localização | Brasil. |
| Usuário exibido | Jair, conforme o canto superior direito da tela. |
| Versão / zoom / classificação do ambiente | Não confirmados; registrar antes de nova execução. |
| Dados | Quatro turmas (ids 1 a 4) e três modalidades (ids 1 a 3), todas já com status "inativo" no retorno da API após as exclusões; a turma de id 4 e as três modalidades tiveram `updated_at` alterado durante a gravação. |

## Pré-condições

- Sessão autenticada com permissão para excluir turmas e modalidades.
- Registros de teste com status e vínculos conhecidos (turmas vinculadas a cada modalidade).
- Regra de exclusão (lógica ou física) e necessidade de confirmação definidas com o produto.
- Antes de uma nova execução, identificar versão, permissões e dados de referência e preparar a captura de interface e rede.

## Cenário BDD

```gherkin
Cenário: Excluir uma turma ou uma modalidade pela lixeira
  Dado que a listagem apresenta turmas e modalidades com a ação de lixeira
  Quando o usuário acionar a lixeira de um registro
  Então o sistema deve aplicar a regra de exclusão definida pelo produto
  E comunicar o resultado ao usuário
  E refletir o resultado na listagem conforme o filtro de status selecionado
```

## Passos para execução ou reteste

1. Registrar as turmas e modalidades, seus status e o filtro de status selecionado.
2. Acionar a lixeira de uma turma ativa; conferir se há confirmação, a mensagem e a requisição.
3. Conferir a listagem sob o filtro "Ativo" e sob o filtro "Inativo".
4. Repetir com uma modalidade que tenha turmas vinculadas e conferir o efeito sobre as turmas.
5. Acionar a lixeira de um registro já inativo e conferir o retorno.
6. Recarregar a página e consultar novamente as listagens.

Este procedimento orienta a próxima execução. A evidência atual cobre o trecho gravado e os limites descritos abaixo; passos complementares não recebem resultado de execução nesta revisão.

## Resultado esperado

O sistema aplica a regra de exclusão definida, informa o resultado e apresenta na listagem apenas os registros compatíveis com o filtro de status selecionado.

## Resultado obtido na gravação

Os cliques na lixeira geram requisições de exclusão com sucesso, mas os registros continuam na listagem com o status "inativo", sem diálogo de confirmação nos quadros consultados.

| Tempo | Registro |
| --- | --- |
| 0:00 | Listagens com quatro turmas e três modalidades; filtro de status "Ativo" em ambas. |
| 1:00 | Cursor sobre a lixeira da primeira turma; nenhum diálogo de confirmação visível. |
| 1:00–1:05 | Cliques em lixeiras: quatro `POST /api/sifitbox/turmas/excluir/1` e cinco `POST /api/sifitbox/modalidades/excluir/1`, todos com HTTP 200 e resposta `{"erro": false}`. |
| 1:05 | Listagens inalteradas: as quatro turmas e as três modalidades continuam exibidas, com o status "inativo". |

**Dados retornados após as exclusões:** as quatro turmas com `"status": "inativo"` (a de id 4 com `updated_at` 2026-11-15 21:50:58 e as demais de 2026-10-15) e as três modalidades com `"status": "inativo"` (`updated_at` 2026-11-15 21:51:00 e 21:51:01).

**Conclusão:** A validar. O sistema responde com sucesso e inativa os registros, o que é compatível com exclusão lógica, mas a regra do produto, a ausência de confirmação e a exibição de registros inativos sob o filtro "Ativo" não foram confirmadas; não se registra defeito antes dessa validação.

## Critérios de aceitação para nova execução

1. A lixeira aplica a regra de exclusão definida pelo produto, com confirmação prévia quando exigida.
2. A resposta e a interface informam o resultado de forma compreensível.
3. A listagem apresenta apenas registros compatíveis com o filtro de status selecionado.
4. Turmas vinculadas a uma modalidade excluída ou inativada recebem tratamento definido e comunicado.
5. A ação sobre um registro já inativo tem retorno coerente.
6. O resultado se mantém após recarga da página.

## Próxima ação e verificações complementares

Confirmar a regra com o responsável pelo produto e reexecutar. Permanecem fora do cenário gravado: filtro "Inativo", reativação, modalidade com turmas vinculadas, permissões, persistência após recarga e corpos das requisições de exclusão.

## Observações sobre a correspondência com CT-RF16

O comportamento de inativação por lixeira em Modalidades já foi observado em [CT-RF16](CT-RF16_Exclusao_Modalidade.md), também a validar. Esta gravação acrescenta as turmas ao mesmo padrão e o retorno `{"erro": false}` para exclusões repetidas de registros já inativos (as turmas de id 1 a 3 mantêm `updated_at` de 15/10/2026, o que sugere que já estavam inativas antes da gravação). Cinco exclusões de modalidades e quatro de turmas para três e quatro registros indicam ações repetidas sobre o mesmo registro; a correspondência exata entre cada clique e cada requisição não foi estabelecida.

## Evidências e limites

- [Jam original — SifitBox – Turmas](https://jam.dev/c/ee9a133b-d6b1-442d-b4b0-dd87595b7e70).
- [Arquivos, origem e limites](../Evidencias/CT-RF40_Exclusao_Turmas_Modalidades/README.md).
- [Lixeira em 1:00](../Evidencias/CT-RF40_Exclusao_Turmas_Modalidades/lixeira_01-00.png), [listagens após as exclusões em 1:05](../Evidencias/CT-RF40_Exclusao_Turmas_Modalidades/lista_apos_exclusoes_01-05.png), [exclusão de turma](../Evidencias/CT-RF40_Exclusao_Turmas_Modalidades/requisicao_excluir_turma.png), [exclusão de modalidade](../Evidencias/CT-RF40_Exclusao_Turmas_Modalidades/requisicao_excluir_modalidade.png) e [resposta](../Evidencias/CT-RF40_Exclusao_Turmas_Modalidades/resposta_excluir.png).
- [Linha do tempo](../Evidencias/CT-RF40_Exclusao_Turmas_Modalidades/linha_do_tempo.txt).

Foram consultados os painéis Info, Console, Network e Actions do Jam, os cabeçalhos e a resposta de exclusões, as listas retornadas e os quadros do vídeo. As capturas foram extraídas da reprodução do Jam e mostram o botão de reprodução sobreposto. Não foram inspecionados os corpos das requisições de exclusão, o filtro "Inativo", o efeito sobre turmas vinculadas nem a persistência após recarga. Não houve nova execução, inspeção do código, acesso ao banco ou correção da aplicação. O vídeo permanece no Jam.

Análise documental da gravação consultada em 15/11/2026. Esta inclusão não executa novamente o sistema e não constitui reteste. Versão da aplicação, zoom e classificação do ambiente não foram confirmados.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf40) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
