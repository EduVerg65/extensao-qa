# 🧪 Cenário 130: Verificar recursos marcados como Em desenvolvimento

**Caso de teste:** CT-RF130

**Módulo:** Inteligência e Automação / Central / Recursos indisponíveis

**Status:** Aprovado conforme a gravação.

**Gravação:** 16/11/2026, 21:45:30 BRT. **Revisão documental:** 17/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Identificar visualmente os recursos em desenvolvimento e impedir que os cartões iniciem um fluxo ainda indisponível. |
| Requisito | [RF130](../Analise%20de%20requisitos.md#rf130) — referência de QA. |
| Tipo / prioridade | Interface manual / estado indisponível · Média, proposta para triagem. |
| Defeito | Nenhum no fluxo avaliado |
| Encaminhamento | Usar como regressão do estado indisponível e conferir a navegação por teclado em execução complementar. |
| Fonte | [Jam — PED-08 — Recursos em desenvolvimento](https://jam.dev/c/0a7ae8fb-980d-4df2-8ef8-de78d6b11b8f) e [evidências locais](../Evidencias/CT-RF130_Central_Recursos_Em_Desenvolvimento/README.md). |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/inteligencia-automacao |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.79 / Windows 10 (x86), conforme os metadados do Jam. |
| Tela / arquivo de vídeo | Tela 1536 × 799 informada no Jam. Vídeo em 1918 × 998. |
| Duração | 30,42 s |
| Localização | Brasil. |
| Versão / zoom / classificação do ambiente | A confirmar antes de nova execução. |
| Dados | Avaliações vencendo, Frequência em queda, Financeiro diário e Cobranças automáticas. |

## Pré-condições

- Sessão autenticada com acesso à Central de Automações e seção Automações disponíveis visível.
- Identificar a versão e registrar os valores iniciais e as permissões no próximo teste.

## Cenário BDD

```gherkin
Cenário: Verificar recursos marcados como Em desenvolvimento
  Dado que a Central exibe cartões identificados como Em desenvolvimento
  Quando o usuário clicar nos cartões e nos selos
  Então a interface deve manter a indicação de indisponibilidade
  E nenhum painel de configuração ou fluxo de execução deve ser iniciado para esses recursos
```

## Passos para execução ou reteste

1. Abrir a Central e localizar Automações disponíveis.
2. Identificar o selo Em desenvolvimento nos quatro cartões.
3. Clicar em cada cartão e verificar mudanças de tela, abertura de painel ou execução.
4. Conferir se a seção e os selos permanecem visíveis.

Este procedimento orienta a próxima execução. O resultado abaixo se limita ao trecho registrado no Jam.

## Resultado esperado

Cada recurso apresenta Em desenvolvimento e permanece indisponível para configurar ou executar.

## Resultado obtido na gravação

Os quatro cartões apresentaram Em desenvolvimento. Os cliques nos títulos, nos selos e nas áreas dos cartões mantiveram a Central aberta, sem painel de configuração, navegação ou execução registrada.

| Tempo | Registro |
| --- | --- |
| 0:04–0:10 | Confere e clica em Avaliações vencendo. |
| 0:11–0:16 | Interage com Frequência em queda. |
| 0:19–0:22 | Interage com Financeiro diário. |
| 0:25–0:29 | Interage com Cobranças automáticas. Os cartões permanecem na mesma tela. |

**Rede:**

- Não houve requisição de rede capturada durante os cliques nos quatro cartões.

**Conclusão:** Aprovado conforme a gravação. A gravação cobre interações com mouse nos cartões nessa versão. A navegação por teclado e o comportamento após a futura liberação dos recursos não foram verificados.

## Critérios de aceitação para nova execução

1. Os quatro recursos indicam Em desenvolvimento.
2. Os cliques não iniciam um fluxo indisponível.
3. A Central mantém a seção e os estados exibidos.

## Próxima ação e verificações complementares

Usar como regressão do estado indisponível e conferir a navegação por teclado em execução complementar.

## Evidências e limites

- [Jam original — PED-08 — Recursos em desenvolvimento](https://jam.dev/c/0a7ae8fb-980d-4df2-8ef8-de78d6b11b8f).
- [Arquivos, origem e limites](../Evidencias/CT-RF130_Central_Recursos_Em_Desenvolvimento/README.md).
- [Quatro cartões identificados como Em desenvolvimento](../Evidencias/CT-RF130_Central_Recursos_Em_Desenvolvimento/cartoes_em_desenvolvimento_00-05.jpg), [Cartões permanecem sem painel aberto após os cliques](../Evidencias/CT-RF130_Central_Recursos_Em_Desenvolvimento/cartoes_apos_cliques_00-29.jpg).
- [Linha do tempo](../Evidencias/CT-RF130_Central_Recursos_Em_Desenvolvimento/linha_do_tempo.txt).

A revisão documental se baseia nos quadros do vídeo e nos eventos capturados pelo Jam. As verificações complementares ficam para uma nova rodada de testes.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf130) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
