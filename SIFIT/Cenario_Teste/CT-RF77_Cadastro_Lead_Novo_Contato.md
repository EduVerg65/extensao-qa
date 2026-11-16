# 🧪 Cenário 77: Cadastrar lead no estágio Novo Contato

**Caso de teste:** CT-RF77  
**Módulo:** Prospecção  
**Status:** Aprovado conforme o resumo da gravação.  
**Gravação / análise original:** 16/11/2026, conforme o resumo. **Integração documental:** 16/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | O lead deve ser criado no estágio Novo Contato e aparecer na listagem. |
| Requisito | [RF77](../Analise%20de%20requisitos.md#rf77), referência de QA proposta a partir do resumo. |
| Tipo / prioridade | Funcional manual / cadastro positivo; Média, proposta. |
| Defeito | Nenhum identificado no fluxo resumido. |
| Fonte | [Evidências](../Evidencias/CT-RF77_Cadastro_Lead_Novo_Contato/README.md) e [Jam](https://jam.dev/c/29447c6a-90f5-48b2-ac5d-d43cad44a782). |

## Pré-condições

- Sessão autenticada com permissão para adicionar leads.
- Dados de contato de teste disponíveis e estágio Novo Contato selecionável.

## Cenário BDD

```gherkin
Cenário: Cadastrar lead no estágio Novo Contato
  Dado que a janela Adicionar Lead está aberta
  Quando preencher os dados de contato e a observação
  E finalizar a seleção de estágio em "Novo Contato"
  E clicar em "Salvar Lead"
  Então o lead deve aparecer na listagem com o estágio Novo Contato
```

## Passos observados

1. Clicar em Adicionar Lead e preencher nome, e-mail, telefone e observação.
2. Alterar o estágio durante o preenchimento e finalizar com Novo Contato.
3. Clicar em Salvar Lead.

## Resultado esperado

O lead deve ser criado no estágio Novo Contato e aparecer na listagem.

## Resultado obtido

O lead de teste é criado com o estágio NOVO_CONTATO, recebe código 11 e aparece na listagem. O total passa de 6 para 7, e o indicador Novo Contato passa de 2 para 3.

## Critérios de aceitação para regressão

1. A seleção final envia o estágio NOVO_CONTATO.
2. O cadastro retorna um código e inclui o lead na listagem.
3. O total e o indicador Novo Contato aumentam em um.
4. Em execução complementar, reabrir o cadastro para conferir todos os campos.

Os critérios acima orientam a próxima execução; verificações complementares não recebem aprovação nesta revisão.

## Evidências e limites

- 00:14: seleção final de Novo Contato.
- 00:22: POST /api/salvar-lead/1 envia estagio=NOVO_CONTATO e retorna HTTP 200, verifica_erro=false e id=11.
- 00:23: GET /api/leads/1 retorna HTTP 200; quadro de 00:25.604 mostra o novo registro.

A classificação considera o cadastro mostrado; não houve reabertura do registro para revisar todos os campos.
Análise da gravação e dos eventos capturados no Jam; não foi executado um novo teste no sistema.

Integração documental dos arquivos RESUMO.txt fornecidos em `C:\Users\Leonardo\Desktop\evidencias`, com data de gravação e análise informada de 16/11/2026. Os Jams não foram reabertos nesta integração; eventos de rede, horários e quadros abaixo são transcritos dos resumos, sem verificação independente. Não houve nova execução do SIFIT, reteste, consulta ao banco, logs ou código.

- Resumo preservado: [RESUMO.txt](../Evidencias/CT-RF77_Cadastro_Lead_Novo_Contato/RESUMO.txt).
- Repetir o cadastro e conferir campos e estágio após reabertura.

---

[← Início](../../README.md) · [RF77](../Analise%20de%20requisitos.md#rf77) · [Plano](../Plano%20de%20testes.md) · [Relatório](../Relatorio%20dos%20testes.md) · [Evidências](../Evidencias/CT-RF77_Cadastro_Lead_Novo_Contato/README.md)
