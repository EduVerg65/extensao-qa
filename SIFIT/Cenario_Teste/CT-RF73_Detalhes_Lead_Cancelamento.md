# 🧪 Cenário 73: Consultar os detalhes de um lead e cancelar a edição

**Caso de teste:** CT-RF73  
**Módulo:** Prospecção  
**Status:** Aprovado conforme o resumo da gravação.  
**Gravação / análise original:** 16/11/2026, conforme o resumo. **Integração documental:** 16/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | O sistema deve carregar os dados do lead e fechar a janela ao cancelar, sem enviar uma gravação da alteração. |
| Requisito | [RF73](../Analise%20de%20requisitos.md#rf73), referência de QA proposta a partir do resumo. |
| Tipo / prioridade | Funcional manual / consulta e cancelamento; Média, proposta. |
| Defeito | Nenhum identificado no fluxo resumido. |
| Fonte | [Evidências](../Evidencias/CT-RF75_Detalhes_Lead_Cancelamento/README.md) e [Jam](https://jam.dev/c/7ef0ee0b-497e-48b8-a57d-cd914558d303). |

## Pré-condições

- Sessão autenticada com acesso à Prospecção.
- Lead existente com dados conhecidos; na evidência, código 3.

## Cenário BDD

```gherkin
Cenário: Consultar os detalhes de um lead e cancelar a edição
  Dado que existe um lead na listagem
  Quando abrir seus detalhes pela lupa
  Então os dados desse lead devem ser carregados
  Quando alterar o telefone e clicar em "Cancelar"
  Então a janela deve fechar sem enviar salvamento
```

## Passos observados

1. Acionar a lupa do lead de código 3.
2. Conferir os dados exibidos na janela Visualizar Lead.
3. Digitar uma alteração no telefone e clicar em Cancelar.

## Resultado esperado

O sistema deve carregar os dados do lead e fechar a janela ao cancelar, sem enviar uma gravação da alteração.

## Resultado obtido

Os dados do lead de código 3 são carregados, incluindo estágio Fechado, contato e observação. Após a alteração no telefone, Cancelar fecha a janela e retorna à listagem. Não há chamada de salvamento na linha do tempo.

## Critérios de aceitação para regressão

1. A consulta carrega os dados do lead selecionado.
2. Cancelar fecha a janela e retorna à listagem.
3. Cancelar não envia requisição de salvamento.
4. Em execução complementar, reabrir o lead e conferir que o telefone original foi preservado.

Os critérios acima orientam a próxima execução; verificações complementares não recebem aprovação nesta revisão.

## Evidências e limites

- 00:00: POST /api/buscar-lead/1 e GET /api/planos/1 retornam HTTP 200.
- 00:04: digitação no telefone.
- 00:05: clique em Cancelar; quadro de 00:07.471 mostra a listagem.

Não houve reabertura do registro para confirmar o valor persistido do telefone. O sucesso se refere à consulta e ao cancelamento observados.
Análise da gravação e dos eventos capturados no Jam; não foi executado um novo teste no sistema.

Integração documental dos arquivos RESUMO.txt fornecidos em `C:\Users\Leonardo\Desktop\evidencias`, com data de gravação e análise informada de 16/11/2026. Os Jams não foram reabertos nesta integração; eventos de rede, horários e quadros abaixo são transcritos dos resumos, sem verificação independente. Não houve nova execução do SIFIT, reteste, consulta ao banco, logs ou código.

- Resumo preservado: [RESUMO.txt](../Evidencias/CT-RF75_Detalhes_Lead_Cancelamento/RESUMO.txt).
- Reabrir o lead após cancelar e comparar o telefone com o valor original.

---

[← Início](../../README.md) · [RF73](../Analise%20de%20requisitos.md#rf73) · [Plano](../Plano%20de%20testes.md) · [Relatório](../Relatorio%20dos%20testes.md) · [Evidências](../Evidencias/CT-RF75_Detalhes_Lead_Cancelamento/README.md)
