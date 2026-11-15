# 🧪 Cenário 29: Exclusão de grupo muscular

**Caso de teste:** CT-RF29

**Módulo:** Treinamento / Grupos Musculares

**Status:** Reprovado nas evidências.

**Gravação:** 15/11/2026, 15h56 BRT. **Revisão documental:** 15/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Excluir um grupo muscular pela listagem ou informar, de forma tratável, por que a exclusão não pode ser concluída. |
| Requisito | [RF29](../Analise%20de%20requisitos.md#rf29) |
| Tipo / prioridade | Funcional manual, análise de evidências / Alta, proposta para triagem. |
| Defeito | [BUG-011](../Relatorio-de-Bugs.md#bug-011) |
| Encaminhamento | Investigar o HTTP 500 com logs do servidor e vínculos do registro; corrigir e retestar os cenários permitido e impedido. |
| Fonte | [Jam — Tela de Grupos Musculares](https://jam.dev/c/98008390-0040-475e-ba7b-7f1e72cc0b2e) |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/grupos-musculares |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.78 / Windows (x86) 11. |
| Tela / arquivo de vídeo | 1920 × 911 informados no Jam. |
| Duração | 2 min 3 s |
| Rede | Classificada como rápida no Jam: mais de 10 Mbps, latência de 50 ms. |
| Localização | Brasil. |
| Servidor | Respostas com `x-powered-by: PHP/8.2.35`, `servidor: hcdn`, `plataforma: hospedagem`. |
| Versão / zoom / classificação do ambiente | Não confirmados; registrar antes de nova execução. |
| Dados | Usar dados de teste conhecidos conforme as pré-condições abaixo; valores da gravação são referência histórica, sem copiar credenciais. |

## Pré-condições

- Sessão autenticada com permissão para excluir grupos musculares.
- Existir na listagem um grupo muscular de teste cuja exclusão seja permitida pelas regras do produto.
- Conhecer previamente os vínculos do registro escolhido (exercícios ou fichas associadas), para distinguir impedimento de regra de falha do servidor.
- Antes de uma nova execução, identificar versão, permissões e dados de referência e preparar a captura de interface e rede.

## Cenário BDD

```gherkin
Cenário: Excluir um grupo muscular pela listagem
  Dado que o usuário está autenticado na tela Grupos Musculares
  E existe o grupo muscular de código 1 na listagem
  Quando acionar o ícone de exclusão na linha do grupo
  E confirmar a exclusão no diálogo "Deseja deletar o Grupo?"
  Então o sistema deve concluir a exclusão e atualizar a listagem e os contadores
  E não deve retornar erro interno do servidor
```

## Passos para execução ou reteste

1. Acessar a tela Grupos Musculares autenticado e registrar o estado inicial da listagem e dos contadores.
2. Acionar o ícone de lixeira na linha do grupo muscular de teste.
3. Confirmar a ação no diálogo "Deseja deletar o Grupo?".
4. Conferir a mensagem apresentada, a listagem, os contadores e a requisição correspondente no painel de rede.
5. Recarregar a página e consultar novamente o registro para verificar a persistência do resultado.

Este procedimento orienta a próxima execução. A evidência atual cobre o trecho gravado e os limites descritos abaixo; passos complementares, como a recarga da página e a consulta ao banco, não recebem resultado de execução nesta revisão.

## Resultado esperado

Concluir a exclusão permitida, remover o registro da listagem e atualizar os contadores; ou, quando houver impedimento de regra, apresentar uma mensagem específica e tratável, sem erro interno do servidor.

## Resultado obtido na gravação

Após a confirmação, o sistema apresenta o diálogo "Erro" com o texto "Erro ao deletar Grupo" e o botão "Fechar". O registro permanece na listagem e os contadores não se alteram. A requisição de exclusão retorna HTTP 500.

**Momentos e registros:**

| Tempo | Registro |
| --- | --- |
| 1:17 | Clique no ícone de exclusão da linha (`i.bi bi-lixo`). |
| 1:18 | Diálogo "Deseja deletar o Grupo?" com as ações "Cancelar" e "Confirmar". Listagem com quatro registros e contadores Grupos cadastrados 4. |
| 1:19 | `POST https://backendsifit.centrion.com.br/api/deleta/grupo-muscular/1` retorna **HTTP 500** em 990 ms. |
| 1:21 | Diálogo "Erro" / "Erro ao deletar Grupo" / "Fechar". A listagem mantém os quatro registros. |
| 1:22–1:23 | Nova tentativa pelo mesmo fluxo. |
| 1:23 | Segundo `POST /api/deleta/grupo-muscular/1` retorna **HTTP 500** em 184 ms. |

**Resposta do servidor nas duas tentativas:**

```json
{
  "verifica_erro": true,
  "mensagem": "Erro interno inesperado."
}
```

**Cabeçalhos registrados:** `content-type: application/json; charset=utf-8`, `content-length: 64`, `x-powered-by: PHP/8.2.35`. Primeira tentativa em `Dom, 15 de nov de 2026 18:55:46 GMT`, `x-hcdn-request-id: d7f7c4b73412a500c5bdb50eb9be6ec1-asc-edge11`; segunda em `18:55:49 GMT`, `x-hcdn-request-id: c467f11f867c2cdb2c23ce6029e59251-asc-edge11`.

**Conclusão:** Reprovado nas evidências. O erro e o endpoint estão registrados; a causa do HTTP 500 não foi determinada.

## Critérios de aceitação para nova execução

1. A ação de exclusão apresenta confirmação explícita antes de efetivar a operação.
2. Para um registro cuja exclusão é permitida, a requisição retorna sucesso, o registro deixa a listagem e os contadores são atualizados.
3. Para um registro com vínculo impeditivo, o sistema apresenta mensagem específica sobre o impedimento, sem HTTP 500.
4. Nenhum cenário de exclusão retorna erro interno do servidor.
5. O resultado se mantém após recarga da página e nova consulta.

## Próxima ação e verificações complementares

Investigar o HTTP 500 com os logs do servidor e os vínculos do grupo muscular de código 1; corrigir e retestar os cenários permitido e impedido. Verificar se o registro permanece íntegro após a falha, já que duas tentativas foram enviadas para o mesmo recurso.

A gravação não permite distinguir entre falha de infraestrutura, exceção não tratada na aplicação e restrição de integridade referencial não capturada. A mensagem "Erro ao deletar Grupo" é genérica e não informa a causa ao usuário.

## Manifestações relacionadas na mesma gravação

A gravação cobre outros fluxos da tela Grupos Musculares, documentados em cenários próprios para não reunir causas distintas em um mesmo registro:

- [CT-RF30 — Carregamento das imagens dos grupos musculares](CT-RF30_Imagens_GruposMusculares.md): requisições de imagem com HTTP 422 durante toda a gravação.
- [CT-RF31 — Cadastro de grupo muscular](CT-RF31_Cadastro_GrupoMuscular.md): inclusão concluída antes da tentativa de exclusão.
- [CT-RF32 — Edição do tipo de membro](CT-RF32_Edicao_TipoMembro.md): alterações que explicam a variação dos cartões de resumo entre os quadros.
- [CT-RF33 — Filtros da tela Grupos Musculares](CT-RF33_Filtros_GruposMusculares.md): consultas por tipo de membro e por código.

A listagem apresentada nos quadros deste cenário já reflete o cadastro e as edições acima; isso não altera o resultado da exclusão.

## Evidências e limites

- [Jam original — Tela de Grupos Musculares](https://jam.dev/c/98008390-0040-475e-ba7b-7f1e72cc0b2e).
- Painel Informações do Jam: URL, carimbo de data/hora, sistema, navegador, tamanho da janela e rede.
- Painel Rede do Jam: lista filtrada por erros, cabeçalhos e corpo de resposta das duas requisições de exclusão.
- Painel Console do Jam, visão de atividade do usuário: cronologia completa de cliques, digitação e erros de rede entre 0:00 e 2:03.
- Quadros consultados: 0:20, 0:55, 1:18, 1:21, 1:45 e 2:00.
- Pasta local de evidências: a criar em `Evidencias/CT-RF29_Exclusao_GrupoMuscular/`; até lá, a fonte é o Jam indicado acima.

Não foram registradas mensagens de console JavaScript na visão consultada, apenas os erros de rede. A causa do HTTP 500 não foi determinada: não houve acesso a logs do servidor, ao corpo completo da resposta além dos 64 bytes retornados, nem consulta ao banco de dados. A persistência do registro após a falha não foi confirmada por recarga de página. O cenário de exclusão com impedimento de regra não foi exercitado.

Análise documental da gravação consultada em 15/11/2026, com leitura direta dos painéis do Jam. Esta inclusão não executa novamente o sistema, não corrige a aplicação e não constitui reteste. Versão da aplicação, zoom e classificação do ambiente não foram confirmados.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
