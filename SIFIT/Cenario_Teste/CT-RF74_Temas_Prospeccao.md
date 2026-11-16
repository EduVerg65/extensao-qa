# 🧪 Cenário 74: Alternar entre os temas claro e escuro na Prospecção

**Caso de teste:** CT-RF74  
**Módulo:** Prospecção  
**Status:** Aprovado conforme o resumo da gravação.  
**Gravação / análise original:** 16/11/2026, conforme o resumo. **Integração documental:** 16/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | A tela deve acompanhar a seleção de tema, mantendo os dados da listagem. |
| Requisito | [RF74](../Analise%20de%20requisitos.md#rf74), referência de QA proposta a partir do resumo. |
| Tipo / prioridade | Interface manual / alternância de tema; Média, proposta. |
| Defeito | Nenhum identificado no fluxo resumido. |
| Fonte | [Evidências](../Evidencias/CT-RF74_Temas_Prospeccao/README.md) e [Jam](https://jam.dev/c/5dc9fc15-8e13-4f90-b21f-a49aedc6731e). |

## Pré-condições

- Sessão autenticada com acesso à Prospecção e controle de tema disponível.
- Listagem de leads carregada antes da alternância.

## Cenário BDD

```gherkin
Cenário: Alternar entre os temas claro e escuro na Prospecção
  Dado que a listagem de leads está carregada
  Quando selecionar o tema Claro e depois o tema Escuro
  Então a tela deve acompanhar cada seleção
  E os dados da listagem devem permanecer visíveis
```

## Passos observados

1. Selecionar o tema Claro.
2. Selecionar novamente o tema Escuro pelo controle de tema.

## Resultado esperado

A tela deve acompanhar a seleção de tema, mantendo os dados da listagem.

## Resultado obtido

A gravação mostra a tela passando de escura para clara e retornando ao tema escuro. A listagem permanece visível.

## Critérios de aceitação para regressão

1. Claro e Escuro são aplicados na sequência escolhida.
2. A listagem mantém os mesmos leads e dados durante a alternância.
3. No reteste, recarregar a página para avaliar separadamente a persistência da preferência.

Os critérios acima orientam a próxima execução; verificações complementares não recebem aprovação nesta revisão.

## Evidências e limites

- 00:00–00:01: alternância nos controles de tema.
- POST /api/usuario/tema retorna HTTP 200 nas duas alterações. A resposta consultada contém verifica_erro=false.
- Quadros de 00:00.813 e 00:01.354 mostram, respectivamente, os temas claro e escuro.

Classificação restrita à alternância visível nesta tela; a gravação não demonstra persistência após recarregar nem uma auditoria de contraste.
Análise da gravação e dos eventos capturados no Jam; não foi executado um novo teste no sistema.

Integração documental dos arquivos RESUMO.txt fornecidos em `C:\Users\Leonardo\Desktop\evidencias`, com data de gravação e análise informada de 16/11/2026. Os Jams não foram reabertos nesta integração; eventos de rede, horários e quadros abaixo são transcritos dos resumos, sem verificação independente. Não houve nova execução do SIFIT, reteste, consulta ao banco, logs ou código.

- Resumo preservado: [RESUMO.txt](../Evidencias/CT-RF74_Temas_Prospeccao/RESUMO.txt).
- Repetir a alternância com listagem conhecida; verificar persistência após recarga em execução complementar.

---

[← Início](../../README.md) · [RF74](../Analise%20de%20requisitos.md#rf74) · [Plano](../Plano%20de%20testes.md) · [Relatório](../Relatorio%20dos%20testes.md) · [Evidências](../Evidencias/CT-RF74_Temas_Prospeccao/README.md)
