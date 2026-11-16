# 🧪 Cenário 78: Cadastrar lead no estágio Interessado

**Caso de teste:** CT-RF78  
**Módulo:** Prospecção  
**Status:** Aprovado conforme o resumo da gravação.  
**Gravação / análise original:** 16/11/2026, conforme o resumo. **Integração documental:** 16/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | O lead deve ser criado no estágio Interessado e aparecer na listagem. |
| Requisito | [RF78](../Analise%20de%20requisitos.md#rf78), referência de QA proposta a partir do resumo. |
| Tipo / prioridade | Funcional manual / cadastro positivo; Média, proposta. |
| Defeito | Nenhum identificado no fluxo resumido. |
| Fonte | [Evidências](../Evidencias/CT-RF78_Cadastro_Lead_Interessado/README.md) e [Jam](https://jam.dev/c/f8735cbf-4043-4467-b43f-3cad7eff0da8). |

## Pré-condições

- Sessão autenticada com permissão para adicionar leads.
- Dados de contato de teste disponíveis e estágio Interessado selecionável.

## Cenário BDD

```gherkin
Cenário: Cadastrar lead no estágio Interessado
  Dado que a janela Adicionar Lead está aberta
  Quando selecionar "Interessado" e preencher os dados do lead
  E clicar em "Salvar Lead"
  Então o novo lead deve aparecer na listagem no estágio Interessado
```

## Passos observados

1. Abrir Adicionar Lead e selecionar Interessado.
2. Preencher nome, e-mail, telefone e observação.
3. Clicar em Salvar Lead.

## Resultado esperado

O lead deve ser criado no estágio Interessado e aparecer na listagem.

## Resultado obtido

O cadastro retorna código 12 e o lead aparece na listagem com a identificação Interessado.

## Critérios de aceitação para regressão

1. O envio utiliza o estágio INTERESSADO.
2. O cadastro retorna um código e o lead é listado como Interessado.
3. Em execução complementar, reabrir o registro para conferir os campos salvos.

Os critérios acima orientam a próxima execução; verificações complementares não recebem aprovação nesta revisão.

## Evidências e limites

- 00:02: seleção de INTERESSADO.
- 00:17: POST /api/salvar-lead/1 envia estagio=INTERESSADO e retorna HTTP 200, verifica_erro=false e id=12.
- 00:17: GET /api/leads/1 retorna HTTP 200; quadro de 00:19.843 mostra o registro de código 12.

A gravação não demonstra reabertura ou alteração posterior do registro.
Análise da gravação e dos eventos capturados no Jam; não foi executado um novo teste no sistema.

Integração documental dos arquivos RESUMO.txt fornecidos em `C:\Users\Leonardo\Desktop\evidencias`, com data de gravação e análise informada de 16/11/2026. Os Jams não foram reabertos nesta integração; eventos de rede, horários e quadros abaixo são transcritos dos resumos, sem verificação independente. Não houve nova execução do SIFIT, reteste, consulta ao banco, logs ou código.

- Resumo preservado: [RESUMO.txt](../Evidencias/CT-RF78_Cadastro_Lead_Interessado/RESUMO.txt).
- Repetir o cadastro e conferir os dados após reabertura.

---

[← Início](../../README.md) · [RF78](../Analise%20de%20requisitos.md#rf78) · [Plano](../Plano%20de%20testes.md) · [Relatório](../Relatorio%20dos%20testes.md) · [Evidências](../Evidencias/CT-RF78_Cadastro_Lead_Interessado/README.md)
