# 🧪 Cenário 154: Limpar os filtros de Modelos de Ficha

**Caso de teste:** CT-RF154

**Módulo:** Configurações / Modelo Ficha / Limpeza de filtros

**Status:** Aprovado conforme a gravação.

**Gravação:** 16/11/2026, 22:29:07 BRT. **Revisão documental:** 17/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Remover os valores digitados em Código, Título e Criador para preparar uma nova consulta. |
| Requisito | [RF154](../Analise%20de%20requisitos.md#rf154) — referência de QA. Confirmação de produto pendente. |
| Tipo / prioridade | Interface manual / limpeza de filtros · Baixa, proposta para triagem. |
| Defeito | Nenhum no fluxo avaliado |
| Encaminhamento | Usar como regressão de interface e conferir o uso dos campos com teclado e mouse. |
| Fonte | [Jam — Modelos de Ficha (PED-30)](https://jam.dev/c/297eec2b-7be4-498b-a0e6-e962ed93cc00) e [evidências locais](../Evidencias/CT-RF114_Limpeza_Filtros_Modelos_Ficha/README.md). |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/fichas-treino-modelo |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.79 / Windows 10 (x86), conforme os metadados do Jam. |
| Tela / arquivo de vídeo | 1536 × 799 informados no Jam. Vídeo em 1918 × 998. |
| Duração | 14,95 s |
| Localização | Brasil. |
| Versão / zoom / classificação do ambiente | A confirmar antes de nova execução. |
| Dados | Código 989898, Título PEDRO-01 e Criador PEDRO-01 no início. |

## Pré-condições

- Sessão autenticada e tela Modelos de Ficha aberta com os três filtros preenchidos.
- Identificar a versão e preparar a captura da listagem, do formulário ou dos filtros e dos eventos de rede pertinentes.

## Cenário BDD

```gherkin
Cenário: Limpar os filtros de Modelos de Ficha
  Dado que Código, Título e Criador estão preenchidos
  Quando o usuário apagar manualmente os valores dos três campos
  Então os três filtros devem ficar vazios e voltar a exibir as indicações de preenchimento
  E o botão de busca deve permanecer disponível
```

## Passos para execução ou reteste

1. Preencher Código, Título e Criador e registrar os valores iniciais.
2. Apagar o conteúdo de Criador e Título.
3. Apagar Código e conferir os três campos e o botão Buscar.

Este procedimento orienta a próxima execução. O resultado abaixo se limita ao trecho registrado no Jam.

## Resultado esperado

Os três campos voltam a ficar vazios, com seus textos de indicação, e a ação de busca continua disponível.

## Resultado obtido na gravação

O usuário apagou manualmente Criador, Título e Código. Os três campos voltaram a mostrar suas indicações de preenchimento e o botão de busca permaneceu disponível. Não houve requisição capturada durante a limpeza. Os cliques posteriores iniciaram a consulta com todos os filtros vazios.

| Tempo | Registro |
| --- | --- |
| 0:00–0:04 | A tela mostra Código 989898, Título PEDRO-01 e Criador PEDRO-01. |
| 0:05–0:09 | O usuário limpa Criador e Título. |
| 0:10–0:11 | Código também é apagado. Os três campos exibem suas indicações antes da nova busca. |

**Rede:** Nenhuma requisição durante a limpeza. Os dois GET ocorreram após os cliques de busca com os campos vazios.

**Conclusão:** Aprovado conforme a gravação. Este cenário cobre a limpeza dos campos. A recuperação dos resultados em uma base populada faz parte do cenário de nova busca.

## Critérios de aceitação para nova execução

1. Criador, Título e Código podem ser esvaziados manualmente.
2. Os três campos exibem novamente suas indicações de preenchimento.
3. O botão de busca permanece disponível após a limpeza.

## Próxima ação e verificações complementares

Usar como regressão de interface e conferir o uso dos campos com teclado e mouse.

## Evidências e limites

- [Jam original — PED-30](https://jam.dev/c/297eec2b-7be4-498b-a0e6-e962ed93cc00).
- [Arquivos, origem e limites](../Evidencias/CT-RF114_Limpeza_Filtros_Modelos_Ficha/README.md).
- [Filtros preenchidos em 0:03](../Evidencias/CT-RF114_Limpeza_Filtros_Modelos_Ficha/filtros_preenchidos_00-03.jpg), [Filtros limpos em 0:11](../Evidencias/CT-RF114_Limpeza_Filtros_Modelos_Ficha/filtros_limpos_00-11.jpg).
- [Linha do tempo](../Evidencias/CT-RF114_Limpeza_Filtros_Modelos_Ficha/linha_do_tempo.txt).

Foram consultados os metadados, os eventos de rede e de interação e os quadros do vídeo. Os recortes estão na pasta de evidências. O vídeo permanece no Jam.

A revisão documental de 17/11/2026 registra a execução gravada. As verificações complementares ficam para uma nova rodada de testes.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf154) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
