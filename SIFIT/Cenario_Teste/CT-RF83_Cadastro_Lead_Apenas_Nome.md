# 🧪 Cenário 83: Validar cadastro de lead preenchendo apenas o nome

**Caso de teste:** CT-RF83  
**Módulo:** Prospecção  
**Status:** Reprovado conforme o relato; regra de obrigatoriedade a confirmar.  
**Gravação / análise original:** 16/11/2026, conforme o resumo. **Integração documental:** 16/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Segundo o cenário identificado como bug pelo autor, o cadastro incompleto deveria ser bloqueado e os campos obrigatórios deveriam ser indicados. |
| Requisito | [RF83](../Analise%20de%20requisitos.md#rf83), referência de QA proposta a partir do resumo. |
| Tipo / prioridade | Funcional manual / teste negativo, regra a confirmar; Alta, proposta. |
| Defeito | [BUG-037](../Relatorio-de-Bugs.md#bug-037), em triagem. |
| Fonte | [Evidências](../Evidencias/CT-RF83_Cadastro_Lead_Apenas_Nome/README.md) e [Jam](https://jam.dev/c/ef3df03c-16ce-4cb6-b0c7-d04514cab4f6). |

## Pré-condições

- Sessão autenticada com permissão para adicionar leads.
- Para concluir o reteste, confirmar com o produto quais campos são obrigatórios além do nome; essa regra não acompanha a evidência.

## Cenário BDD

```gherkin
Cenário: Validar cadastro de lead preenchendo apenas o nome
  Dado que a regra confirmada exige dados além do nome para cadastrar um lead
  E a janela Adicionar Lead está aberta
  Quando preencher somente o nome "Leo"
  E manter os demais campos vazios e clicar em "Salvar Lead"
  Então o sistema deve bloquear o cadastro incompleto
  E indicar os campos obrigatórios sem criar o lead
```

## Passos observados

1. Na janela Adicionar Lead, preencher somente o nome Leo.
2. Manter telefone, e-mail e observação visualmente vazios e o estágio padrão Novo Contato.
3. Clicar em Salvar Lead.

## Resultado esperado

Segundo o cenário identificado como bug pelo autor, o cadastro incompleto deveria ser bloqueado e os campos obrigatórios deveriam ser indicados.

## Resultado obtido

O sistema aceita o envio sem bloqueio visível, cria o lead de código 19 e atualiza a listagem. O total de leads passa de 14 para 15.

## Critérios de aceitação para reteste

1. Produto confirma e documenta os campos obrigatórios para o cadastro.
2. Se a regra exigir dados além do nome, o envio incompleto é bloqueado e cada campo faltante é indicado.
3. A validação confirmada é aplicada também no servidor, sem criar registro inválido.
4. Um envio completo conforme a regra permite cadastrar o lead.
5. Se apenas o nome for suficiente pela regra aprovada, reclassificar o caso e encerrar o relato como comportamento esperado.

Os critérios acima orientam a próxima execução; verificações complementares não recebem aprovação nesta revisão.

## Evidências e limites

- 00:02: nome Leo preenchido; os demais campos de contato permanecem visualmente vazios.
- 00:03: POST /api/salvar-lead/1 retorna HTTP 200, verifica_erro=false e id=19. O corpo enviado confirma telefone e observacao vazios.
- 00:03: GET /api/leads/1 retorna HTTP 200; quadro de 00:08.223 mostra o registro de código 19.

A classificação de erro acompanha o título do Jam. A regra formal dos campos obrigatórios não foi fornecida; é necessário validá-la para definir exatamente quais campos devem impedir o cadastro. O e-mail está mascarado nos dados de rede, e sua ausência foi avaliada visualmente.
Análise da gravação e dos eventos capturados no Jam; não foi executado um novo teste no sistema.

Integração documental dos arquivos RESUMO.txt fornecidos em `C:\Users\Leonardo\Desktop\evidencias`, com data de gravação e análise informada de 16/11/2026. Os Jams não foram reabertos nesta integração; eventos de rede, horários e quadros abaixo são transcritos dos resumos, sem verificação independente. Não houve nova execução do SIFIT, reteste, consulta ao banco, logs ou código.

- Resumo preservado: [RESUMO.txt](../Evidencias/CT-RF83_Cadastro_Lead_Apenas_Nome/RESUMO.txt).
- Confirmar obrigatoriedade com produto antes de definir correção; testar campos isolados, envio completo e ausência de criação inválida.

---

[← Início](../../README.md) · [RF83](../Analise%20de%20requisitos.md#rf83) · [Plano](../Plano%20de%20testes.md) · [Relatório](../Relatorio%20dos%20testes.md) · [Evidências](../Evidencias/CT-RF83_Cadastro_Lead_Apenas_Nome/README.md)
