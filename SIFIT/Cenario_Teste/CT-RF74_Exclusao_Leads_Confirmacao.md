# 🧪 Cenário 74: Excluir leads com confirmação

**Caso de teste:** CT-RF74  
**Módulo:** Prospecção  
**Status:** Aprovado conforme o resumo da gravação.  
**Gravação / análise original:** 16/11/2026, conforme o resumo. **Integração documental:** 16/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Cada confirmação deve excluir o lead selecionado e atualizar a listagem e o total de registros. |
| Requisito | [RF74](../Analise%20de%20requisitos.md#rf74), referência de QA proposta a partir do resumo. |
| Tipo / prioridade | Funcional manual / exclusão confirmada; Média, proposta. |
| Defeito | Nenhum identificado no fluxo resumido. |
| Fonte | [Evidências](../Evidencias/CT-RF76_Exclusao_Leads_Confirmacao/README.md) e [Jam](https://jam.dev/c/2ac5e5ed-b10f-4cc9-9f97-7ba65ca560f8). |

## Pré-condições

- Sessão autenticada com permissão de exclusão em Prospecção.
- Dois leads de teste disponíveis para remoção; na evidência, códigos 3 e 4.

## Cenário BDD

```gherkin
Cenário: Excluir leads com confirmação
  Dado que existem dois leads de teste na listagem
  Quando excluir o primeiro lead e confirmar
  Então somente esse lead deve ser removido e o total deve diminuir em um
  Quando excluir o segundo lead e confirmar
  Então o total deve diminuir novamente em um
```

## Passos observados

1. Acionar a exclusão do primeiro lead e confirmar.
2. Repetir a exclusão para o lead seguinte, também confirmando.

## Resultado esperado

Cada confirmação deve excluir o lead selecionado e atualizar a listagem e o total de registros.

## Resultado obtido

Os leads de códigos 3 e 4 deixam de aparecer após as confirmações. O total exibido diminui de 8 para 7 e depois para 6.

## Critérios de aceitação para regressão

1. Cada exclusão depende da confirmação do usuário.
2. Cada confirmação remove somente o lead selecionado.
3. A listagem e o total são atualizados após cada exclusão.
4. Em execução complementar, cancelar a confirmação deve preservar o registro.

Os critérios acima orientam a próxima execução; verificações complementares não recebem aprovação nesta revisão.

## Evidências e limites

- 00:01 e 00:04: POST /api/deletar-lead/1 retorna HTTP 200, seguido de GET /api/leads/1 com HTTP 200.
- A segunda exclusão envia id=4 e recebe verifica_erro=false.
- Quadros de 00:03.179 e 00:05.723 mostram os totais 7 e 6.

As duas exclusões foram agrupadas no mesmo caso porque pertencem ao mesmo cenário na gravação. O cancelamento da confirmação de exclusão não foi testado.
Análise da gravação e dos eventos capturados no Jam; não foi executado um novo teste no sistema.

Integração documental dos arquivos RESUMO.txt fornecidos em `C:\Users\Leonardo\Desktop\evidencias`, com data de gravação e análise informada de 16/11/2026. Os Jams não foram reabertos nesta integração; eventos de rede, horários e quadros abaixo são transcritos dos resumos, sem verificação independente. Não houve nova execução do SIFIT, reteste, consulta ao banco, logs ou código.

- Resumo preservado: [RESUMO.txt](../Evidencias/CT-RF76_Exclusao_Leads_Confirmacao/RESUMO.txt).
- Repetir com registros descartáveis e testar também o cancelamento da confirmação.

---

[← Início](../../README.md) · [RF74](../Analise%20de%20requisitos.md#rf74) · [Plano](../Plano%20de%20testes.md) · [Relatório](../Relatorio%20dos%20testes.md) · [Evidências](../Evidencias/CT-RF76_Exclusao_Leads_Confirmacao/README.md)
