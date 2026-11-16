# 🧪 Cenário 80: Cadastrar lead no estágio Proposta

**Caso de teste:** CT-RF80  
**Módulo:** Prospecção  
**Status:** Aprovado conforme o resumo da gravação.  
**Gravação / análise original:** 16/11/2026, conforme o resumo. **Integração documental:** 16/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | O lead deve ser criado no estágio Proposta e aparecer na listagem. |
| Requisito | [RF80](../Analise%20de%20requisitos.md#rf80), referência de QA proposta a partir do resumo. |
| Tipo / prioridade | Funcional manual / cadastro positivo; Média, proposta. |
| Defeito | Nenhum identificado no fluxo resumido. |
| Fonte | [Evidências](../Evidencias/CT-RF80_Cadastro_Lead_Proposta/README.md) e [Jam](https://jam.dev/c/84f94285-ae5f-4f95-b640-a9b107565aa6). |

## Pré-condições

- Sessão autenticada com permissão para adicionar leads.
- Dados de contato de teste disponíveis e estágio Proposta selecionável.

## Cenário BDD

```gherkin
Cenário: Cadastrar lead no estágio Proposta
  Dado que a janela Adicionar Lead está aberta
  Quando preencher os dados e selecionar "Proposta"
  E clicar em "Salvar Lead"
  Então o lead deve ser listado no estágio Proposta
  E o total de leads deve aumentar em um
```

## Passos observados

1. Abrir Adicionar Lead e preencher os dados do lead e a observação.
2. Selecionar o estágio Proposta.
3. Clicar em Salvar Lead.

## Resultado esperado

O lead deve ser criado no estágio Proposta e aparecer na listagem.

## Resultado obtido

O cadastro retorna código 15 e o registro aparece na listagem com estágio Proposta. O total de leads passa de 10 para 11.

## Critérios de aceitação para regressão

1. O envio utiliza o estágio PROPOSTA.
2. O cadastro retorna um código e o lead é listado como Proposta.
3. O total de leads aumenta em um.
4. Em execução complementar, reabrir o registro para conferir os campos salvos.

Os critérios acima orientam a próxima execução; verificações complementares não recebem aprovação nesta revisão.

## Evidências e limites

- 00:14: seleção de PROPOSTA.
- 00:25: POST /api/salvar-lead/1 envia estagio=PROPOSTA e retorna HTTP 200, verifica_erro=false e id=15.
- 00:25: GET /api/leads/1 retorna HTTP 200; quadro de 00:27.559 mostra o registro de código 15.

O teste demonstra a classificação do lead no estágio Proposta; não demonstra emissão de proposta comercial.
Análise da gravação e dos eventos capturados no Jam; não foi executado um novo teste no sistema.

Integração documental dos arquivos RESUMO.txt fornecidos em `C:\Users\Leonardo\Desktop\evidencias`, com data de gravação e análise informada de 16/11/2026. Os Jams não foram reabertos nesta integração; eventos de rede, horários e quadros abaixo são transcritos dos resumos, sem verificação independente. Não houve nova execução do SIFIT, reteste, consulta ao banco, logs ou código.

- Resumo preservado: [RESUMO.txt](../Evidencias/CT-RF80_Cadastro_Lead_Proposta/RESUMO.txt).
- Repetir o cadastro e conferir estágio e dados após reabertura.

---

[← Início](../../README.md) · [RF80](../Analise%20de%20requisitos.md#rf80) · [Plano](../Plano%20de%20testes.md) · [Relatório](../Relatorio%20dos%20testes.md) · [Evidências](../Evidencias/CT-RF80_Cadastro_Lead_Proposta/README.md)
