# 🧪 Cenário 70: Cadastrar lead no estágio Fechado

**Caso de teste:** CT-RF70  
**Módulo:** Prospecção  
**Status:** Aprovado conforme o resumo da gravação.  
**Gravação / análise original:** 16/11/2026, conforme o resumo. **Integração documental:** 16/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | O lead deve ser criado no estágio Fechado e aparecer na listagem. |
| Requisito | [RF70](../Analise%20de%20requisitos.md#rf70), referência de QA proposta a partir do resumo. |
| Tipo / prioridade | Funcional manual / cadastro positivo; Média, proposta. |
| Defeito | Nenhum identificado no fluxo resumido. |
| Fonte | [Evidências](../Evidencias/CT-RF84_Cadastro_Lead_Fechado/README.md) e [Jam](https://jam.dev/c/775b9003-fdf7-4ad5-8882-15ba606b6674). |

## Pré-condições

- Sessão autenticada com permissão para adicionar leads.
- Dados de contato de teste disponíveis e estágio Fechado selecionável.

## Cenário BDD

```gherkin
Cenário: Cadastrar lead no estágio Fechado
  Dado que a janela Adicionar Lead está aberta
  Quando selecionar "Fechado" e preencher os dados do lead
  E clicar em "Salvar Lead"
  Então a janela deve fechar e o lead deve aparecer como Fechado
  E o total de leads deve aumentar em um
```

## Passos observados

1. Selecionar o estágio Fechado na janela Adicionar Lead.
2. Preencher nome, e-mail, telefone e observação.
3. Clicar em Salvar Lead.

## Resultado esperado

O lead deve ser criado no estágio Fechado e aparecer na listagem.

## Resultado obtido

A janela fecha após salvar, o total de leads passa de 12 para 13 e o registro testeFechado aparece com código 17 e identificação Fechado.

## Critérios de aceitação para regressão

1. O estágio selecionado é FECHADO.
2. Salvar fecha a janela e inclui o lead com identificação Fechado.
3. O total de leads aumenta em um.
4. Em execução complementar, reabrir o cadastro para conferir todos os campos.

Os critérios acima orientam a próxima execução; verificações complementares não recebem aprovação nesta revisão.

## Evidências e limites

- 00:01: seleção de FECHADO.
- 00:20: POST /api/salvar-lead/1 retorna HTTP 200, seguido de GET /api/leads/1 com HTTP 200.
- Quadro de 00:22.648 mostra o registro de código 17 no estágio Fechado.

O corpo da resposta de salvamento não está disponível no evento consultado; o resultado é sustentado pelo retorno HTTP e pelo registro visível na listagem.
Análise da gravação e dos eventos capturados no Jam; não foi executado um novo teste no sistema.

Integração documental dos arquivos RESUMO.txt fornecidos em `C:\Users\Leonardo\Desktop\evidencias`, com data de gravação e análise informada de 16/11/2026. Os Jams não foram reabertos nesta integração; eventos de rede, horários e quadros abaixo são transcritos dos resumos, sem verificação independente. Não houve nova execução do SIFIT, reteste, consulta ao banco, logs ou código.

- Resumo preservado: [RESUMO.txt](../Evidencias/CT-RF84_Cadastro_Lead_Fechado/RESUMO.txt).
- Repetir o cadastro e conferir os dados após reabertura; capturar o corpo da resposta de salvamento.

---

[← Início](../../README.md) · [RF70](../Analise%20de%20requisitos.md#rf70) · [Plano](../Plano%20de%20testes.md) · [Relatório](../Relatorio%20dos%20testes.md) · [Evidências](../Evidencias/CT-RF84_Cadastro_Lead_Fechado/README.md)
