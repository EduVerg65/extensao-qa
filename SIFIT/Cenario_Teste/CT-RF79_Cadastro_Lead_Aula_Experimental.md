# 🧪 Cenário 79: Cadastrar lead no estágio Fez Aula Experimental

**Caso de teste:** CT-RF79  
**Módulo:** Prospecção  
**Status:** Aprovado conforme o resumo da gravação.  
**Gravação / análise original:** 16/11/2026, conforme o resumo. **Integração documental:** 16/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | O lead deve ser criado com o estágio Fez Aula Experimental e aparecer na listagem. |
| Requisito | [RF79](../Analise%20de%20requisitos.md#rf79), referência de QA proposta a partir do resumo. |
| Tipo / prioridade | Funcional manual / cadastro positivo; Média, proposta. |
| Defeito | Nenhum identificado no fluxo resumido. |
| Fonte | [Evidências](../Evidencias/CT-RF79_Cadastro_Lead_Aula_Experimental/README.md) e [Jam](https://jam.dev/c/bef3d877-056b-4274-87c3-da37869c54fd). |

## Pré-condições

- Sessão autenticada com permissão para adicionar leads.
- Dados de contato de teste disponíveis e estágio Fez Aula Experimental selecionável.

## Cenário BDD

```gherkin
Cenário: Cadastrar lead no estágio Fez Aula Experimental
  Dado que a janela Adicionar Lead está aberta
  Quando preencher os dados e selecionar "Fez Aula Experimental"
  E clicar em "Salvar Lead"
  Então o lead deve ser listado nesse estágio
  E o total de leads deve aumentar em um
```

## Passos observados

1. Abrir Adicionar Lead e preencher os dados de contato.
2. Selecionar Fez Aula Experimental e preencher a observação.
3. Clicar em Salvar Lead.

## Resultado esperado

O lead deve ser criado com o estágio Fez Aula Experimental e aparecer na listagem.

## Resultado obtido

O lead é criado com código 14 e estágio FEZ_AULA_EXP. A linha correspondente aparece ao final, e o total de leads passa de 9 para 10.

## Critérios de aceitação para regressão

1. O cadastro utiliza o estágio FEZ_AULA_EXP.
2. O novo lead aparece na listagem com o estágio escolhido.
3. O total de leads aumenta em um.
4. Em execução complementar, reabrir o registro para conferir os campos salvos.

Os critérios acima orientam a próxima execução; verificações complementares não recebem aprovação nesta revisão.

## Evidências e limites

- 00:04: seleção de FEZ_AULA_EXP.
- 00:16: POST /api/salvar-lead/1 retorna HTTP 200, verifica_erro=false e id=14.
- 00:16: GET /api/leads/1 retorna HTTP 200; quadro de 00:17.747 mostra o lead no estágio escolhido.

A gravação valida o cadastro no estágio indicado; não demonstra agendamento ou realização de uma aula.
Análise da gravação e dos eventos capturados no Jam; não foi executado um novo teste no sistema.

Integração documental dos arquivos RESUMO.txt fornecidos em `C:\Users\Leonardo\Desktop\evidencias`, com data de gravação e análise informada de 16/11/2026. Os Jams não foram reabertos nesta integração; eventos de rede, horários e quadros abaixo são transcritos dos resumos, sem verificação independente. Não houve nova execução do SIFIT, reteste, consulta ao banco, logs ou código.

- Resumo preservado: [RESUMO.txt](../Evidencias/CT-RF79_Cadastro_Lead_Aula_Experimental/RESUMO.txt).
- Repetir o cadastro e conferir estágio, total e dados após reabertura.

---

[← Início](../../README.md) · [RF79](../Analise%20de%20requisitos.md#rf79) · [Plano](../Plano%20de%20testes.md) · [Relatório](../Relatorio%20dos%20testes.md) · [Evidências](../Evidencias/CT-RF79_Cadastro_Lead_Aula_Experimental/README.md)
