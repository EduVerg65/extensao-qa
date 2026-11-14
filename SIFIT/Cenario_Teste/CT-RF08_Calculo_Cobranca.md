# 🧪 Cenário 08: Total atualizado da cobrança e valor da mensagem

**Caso de teste:** CT-RF08

**Módulo:** Financeiro / Cobrança via WhatsApp

**Status:** A validar — regra ou contexto pendente.

**Gravação:** 14/11/2026, 00:27:14 BRT. **Revisão documental:** 14/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Apresentar a composição e o valor comunicado na cobrança. |
| Requisito | [RF08](../Analise%20de%20requisitos.md#rf08) |
| Tipo / prioridade | Funcional manual, análise de evidências / Alta, proposta para triagem. |
| Defeito | Sem defeito confirmado |
| Encaminhamento | Conclusão pendente de regra ou contexto; sem defeito confirmado. |
| Fonte | [Jam — Valor sendo calculado errado](https://jam.dev/c/79b712ae-d9e0-4600-862f-fd3a278285ff) |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/dashboard |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.51 / Windows 11 (x86). |
| Tela / arquivo de vídeo | 1920 × 957 informados no Jam; original 1918 × 956 pixels. |
| Duração | 28,45 s |
| Versão / zoom / classificação do ambiente | Não confirmados; registrar antes de nova execução. |
| Dados | Usar dados de teste conhecidos conforme as pré-condições abaixo; valores da gravação são referência histórica, sem copiar credenciais. |

## Pré-condições

- Sessão autenticada e mensalidade de teste com valor, vencimento e encargos conhecidos.
- Confirmar com o produto multa, juros, arredondamento e valor que deve constar na mensagem.
- Antes de uma nova execução, identificar versão, permissões e dados de referência e preparar a captura de interface e rede.

## Cenário BDD

```gherkin
Cenário: Apresentar a composição e o valor comunicado na cobrança
  Dado que existe uma mensalidade com encargos e regra de cálculo conhecidos
  Quando abrir "Cobrar via WhatsApp"
  Então o sistema deve apresentar a composição do total atualizado
  E o valor comunicado na mensagem deve seguir a regra definida pelo produto
```

## Passos para execução ou reteste

1. Abrir Cobrar via WhatsApp para uma mensalidade de referência.
2. Comparar valor original, multa, total atualizado e texto inicial da mensagem.
3. Calcular o total conforme a regra confirmada e registrar a composição, sem enviar mensagem.

Este procedimento orienta a próxima execução. A evidência atual cobre o trecho gravado e os limites descritos abaixo; passos complementares, como conferir downloads ou recarregar a sessão, não recebem resultado de execução nesta revisão.

## Resultado esperado

Exibir a composição do total, incluindo eventuais juros, e deixar claro qual valor será comunicado.

## Resultado obtido na gravação

O modal mostra valor original de R$ 350,00, multa de R$ 7,00 e total atualizado de R$ 377,83. A mensagem inicial cita R$ 350,00; o autor escreve que o valor deveria ser R$ 357,00.

**Momentos e registros:** 0:04–0:08: comparação dos valores. 0:14–0:24: anotação do autor no campo da mensagem.

**Conclusão:** A validar — regra ou contexto pendente. A definição ou confirmação da regra deve preceder aprovação ou reprovação definitiva.

## Critérios de aceitação para nova execução

1. Valor original, multa e eventuais juros são identificáveis.
2. Total confere com a fórmula e o arredondamento definidos.
3. O valor na mensagem segue uma regra explícita.

## Próxima ação e verificações complementares

Confirmar a origem dos R$ 20,83 além de principal e multa e a regra da mensagem; não registrar cálculo incorreto antes dessa validação.

Nenhum defeito adicional foi criado para este cenário.

## Evidências e limites

- [Jam original — Valor sendo calculado errado](https://jam.dev/c/79b712ae-d9e0-4600-862f-fd3a278285ff).
- [Vídeo original](../Evidencias/CT-RF08_Calculo_Cobranca/video.webm).
- [Resumo, origem e integridade](../Evidencias/CT-RF08_Calculo_Cobranca/README.md).
- [Cronologia do Jam](../Evidencias/CT-RF08_Calculo_Cobranca/linha_do_tempo.txt).

R$ 350,00 + R$ 7,00 = R$ 357,00, mas os R$ 20,83 restantes podem corresponder a juros. A regra de cálculo e as configurações não foram fornecidas; não é possível afirmar que o total está incorreto.

Análise documental das gravações já consultadas em 14/11/2026 (metadados, cronologia e quadros distribuídos pelo vídeo). Esta inclusão não executa novamente o sistema, não corrige a aplicação e não constitui reteste. Versão da aplicação, zoom e classificação do ambiente não foram confirmados.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
