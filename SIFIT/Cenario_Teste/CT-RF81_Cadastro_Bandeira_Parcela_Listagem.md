# 🧪 Cenário 81: Cadastrar bandeira com parcela e conferir a listagem

**Caso de teste:** CT-RF81  
**Módulo:** Bandeiras de Cartão  
**Status:** Reprovado nas evidências resumidas.  
**Gravação / análise original:** 16/11/2026, conforme o resumo. **Integração documental:** 16/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | A bandeira deve ser criada com a configuração de parcela e aparecer na listagem após o salvamento. |
| Requisito | [RF81](../Analise%20de%20requisitos.md#rf81), referência de QA proposta a partir do resumo. |
| Tipo / prioridade | Funcional manual / cadastro e listagem; Alta, proposta. |
| Defeito | [BUG-035](../Relatorio-de-Bugs.md#bug-035), em triagem. |
| Fonte | [Evidências](../Evidencias/CT-RF81_Cadastro_Bandeira_Parcela_Listagem/README.md) e [Jam](https://jam.dev/c/2f0280fb-6b7f-4cf0-a45c-02f8c16b6c5e). |

## Pré-condições

- Sessão autenticada com permissão para cadastrar Bandeiras de Cartão.
- Ambiente de teste com possibilidade de cadastrar uma bandeira e sua configuração de parcela.

## Cenário BDD

```gherkin
Cenário: Cadastrar bandeira com parcela e conferir a listagem
  Dado que a janela Nova Bandeira está aberta
  Quando informar o nome "master" e taxas adicional e de débito de 1,11
  E adicionar a parcela número 2 com taxa 3,33
  E salvar a bandeira
  Então a bandeira criada deve aparecer na listagem
  E sua configuração de parcela deve estar associada ao mesmo cadastro
```

## Passos observados

1. Clicar em Nova Bandeira.
2. Informar nome master e taxas adicional e de débito de 1,11.
3. Adicionar a configuração de parcela número 2 com taxa 3,33 e confirmar a inclusão.
4. Clicar em Salvar e conferir a listagem.

## Resultado esperado

A bandeira deve ser criada com a configuração de parcela e aparecer na listagem após o salvamento.

## Resultado obtido

A API confirma a criação da bandeira de código 34 e da parcela, mas a consulta seguinte retorna [] e a interface continua exibindo Nenhuma bandeira encontrada. A criação da parcela tem retorno de sucesso; o fluxo completo apresenta erro na recuperação/exibição do cadastro.

## Critérios de aceitação para reteste

1. A criação da bandeira e da parcela é concluída de forma coerente.
2. A consulta posterior inclui a bandeira confirmada pela criação.
3. A listagem exibe o novo registro sem exigir um novo cadastro.
4. Reabrir e recarregar a bandeira permite conferir taxas e configuração de parcela.
5. Uma falha parcial deve produzir mensagem clara e permitir recuperação sem duplicidade.

Os critérios acima orientam a próxima execução; verificações complementares não recebem aprovação nesta revisão.

## Evidências e limites

- 00:11: POST /api/cria/bandeira/1 retorna HTTP 201, verifica_erro=false e id=34.
- 00:11: POST /api/cria/parcela-bandeira/1 envia bandeira_id=34, n_parcela=2 e taxa=3,33; retorna HTTP 201 e verifica_erro=false.
- 00:11: POST /api/bandeiras/1 retorna HTTP 200 com corpo [].
- Quadro de 00:13.191 mostra a listagem vazia após fechar a janela.

A causa da divergência e a persistência efetiva no banco não foram verificadas. A gravação comprova a diferença entre os retornos de criação e de listagem, sem permitir atribuir a causa ao frontend ou ao backend.
Análise da gravação e dos eventos capturados no Jam; não foi executado um novo teste no sistema.

Integração documental dos arquivos RESUMO.txt fornecidos em `C:\Users\Leonardo\Desktop\evidencias`, com data de gravação e análise informada de 16/11/2026. Os Jams não foram reabertos nesta integração; eventos de rede, horários e quadros abaixo são transcritos dos resumos, sem verificação independente. Não houve nova execução do SIFIT, reteste, consulta ao banco, logs ou código.

- Resumo preservado: [RESUMO.txt](../Evidencias/CT-RF81_Cadastro_Bandeira_Parcela_Listagem/RESUMO.txt).
- Investigar a divergência criação/consulta; retestar listagem, reabertura e recarga com e sem parcela.

---

[← Início](../../README.md) · [RF81](../Analise%20de%20requisitos.md#rf81) · [Plano](../Plano%20de%20testes.md) · [Relatório](../Relatorio%20dos%20testes.md) · [Evidências](../Evidencias/CT-RF81_Cadastro_Bandeira_Parcela_Listagem/README.md)
