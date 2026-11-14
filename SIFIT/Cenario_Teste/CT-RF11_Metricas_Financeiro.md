# 🧪 Cenário 11: Escopo das métricas financeiras durante a filtragem

**Caso de teste:** CT-RF11

**Módulo:** Financeiro / Indicadores

**Status:** A validar — regra ou contexto pendente.

**Gravação:** 14/11/2026, 00:31:44 BRT. **Revisão documental:** 14/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Explicitar o escopo dos indicadores financeiros. |
| Requisito | [RF11](../Analise%20de%20requisitos.md#rf11) |
| Tipo / prioridade | Funcional manual, análise de evidências / Média, proposta para triagem. |
| Defeito | Sem defeito confirmado |
| Encaminhamento | Conclusão pendente de regra ou contexto; sem defeito confirmado. |
| Fonte | [Jam — Erro nas métricas](https://jam.dev/c/4491c9e7-7e00-4063-91ce-8683e316df06) |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/dashboard |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.51 / Windows 11 (x86). |
| Tela / arquivo de vídeo | 1920 × 957 informados no Jam; original 1918 × 956 pixels. |
| Duração | 16,38 s |
| Versão / zoom / classificação do ambiente | Não confirmados; registrar antes de nova execução. |
| Dados | Usar dados de teste conhecidos conforme as pré-condições abaixo; valores da gravação são referência histórica, sem copiar credenciais. |

## Pré-condições

- Sessão autenticada e base com valores conhecidos por faixa e mês.
- Definir quais cartões são globais, mensais ou dependentes do filtro selecionado.
- Antes de uma nova execução, identificar versão, permissões e dados de referência e preparar a captura de interface e rede.

## Cenário BDD

```gherkin
Cenário: Explicitar o escopo dos indicadores financeiros
  Dado que o escopo de cada indicador financeiro está definido
  Quando alternar os filtros do "Financeiro em Aberto"
  Então cada cartão deve respeitar seu escopo global, mensal ou filtrado
  E a interface deve permitir compreender a referência dos valores
```

## Passos para execução ou reteste

1. Abrir Financeiro em Aberto e registrar os cartões e a lista em Todos.
2. Alternar Até 7 dias e +30 dias.
3. Comparar cada cartão com seu escopo definido e verificar se a interface identifica esse escopo.

Este procedimento orienta a próxima execução. A evidência atual cobre o trecho gravado e os limites descritos abaixo; passos complementares, como conferir downloads ou recarregar a sessão, não recebem resultado de execução nesta revisão.

## Resultado esperado

Indicar claramente quais métricas seguem o filtro e quais representam o total geral ou o mês.

## Resultado obtido na gravação

A lista alterna entre uma linha e estado vazio. O cartão de atraso muda de dois para zero alunos; outros totais, como Total em aberto de R$ 470,00 e Recuperado no mês de R$ 45,00, permanecem.

**Momentos e registros:** 0:01–0:12: troca dos filtros e comparação dos cartões. Foram capturadas chamadas financeiras com HTTP 200.

**Conclusão:** A validar — regra ou contexto pendente. A definição ou confirmação da regra deve preceder aprovação ou reprovação definitiva.

## Critérios de aceitação para nova execução

1. Cada indicador possui escopo e período identificados.
2. Indicadores filtrados acompanham a seleção.
3. Indicadores globais ou mensais podem permanecer constantes quando isso corresponde à regra definida.

## Próxima ação e verificações complementares

Confirmar os contratos dos cartões; a constância de totais globais não é suficiente para abrir outro defeito financeiro.

Nenhum defeito adicional foi criado para este cenário.

## Evidências e limites

- [Jam original — Erro nas métricas](https://jam.dev/c/4491c9e7-7e00-4063-91ce-8683e316df06).
- [Vídeo original](../Evidencias/CT-RF11_Metricas_Financeiro/video.webm).
- [Resumo, origem e integridade](../Evidencias/CT-RF11_Metricas_Financeiro/README.md).
- [Cronologia do Jam](../Evidencias/CT-RF11_Metricas_Financeiro/linha_do_tempo.txt).

Totais globais podem permanecer constantes por definição. Sem a regra de cada indicador, não é possível classificar toda permanência de valor como erro. A divergência de contagens está documentada nos itens 05 e 06.

Análise documental das gravações já consultadas em 14/11/2026 (metadados, cronologia e quadros distribuídos pelo vídeo). Esta inclusão não executa novamente o sistema, não corrige a aplicação e não constitui reteste. Versão da aplicação, zoom e classificação do ambiente não foram confirmados.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
