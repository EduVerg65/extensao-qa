# 🧪 Cenário 160: Alternar o filtro de postagens e abrir a lista completa

**Caso de teste:** CT-RF160

**Módulo:** Aplicativo / Postagens

**Status:** Aprovado conforme a gravação.

**Gravação:** 16/11/2026, 22:43:07 BRT. **Revisão documental:** 18/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Verificar que a lista e o diálogo Todas as postagens mostram o estado vazio correspondente ao filtro selecionado. |
| Requisito | [RF160](../Analise%20de%20requisitos.md#rf160) — referência de QA. |
| Tipo / prioridade | Funcional manual / filtragem de lista vazia · Média, proposta para triagem. |
| Defeito | Nenhum no fluxo avaliado |
| Encaminhamento | Repetir com postagens pendentes e aprovadas para conferir a seleção de registros e o total do diálogo. |
| Fonte | Jam 4 — Filtros e lista completa de postagens (gravação restrita por conter dados de integração ou dados de alunos) e [evidências locais](../Evidencias/CT-RF160_Aplicativo_Postagens_Filtros_Estados_Vazios/README.md). |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/aplicativo |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.79 / Windows 10 (x86), conforme os metadados do Jam. |
| Tela / arquivo de vídeo | Tela 1536 × 799 informada no Jam. Vídeo em 1918 × 998. |
| Duração | 20,67 s |
| Localização | Brasil. |
| Versão / zoom / classificação do ambiente | A confirmar antes de nova execução. |
| Dados | Nenhuma postagem disponível na gravação. Controles Só pendentes, Ver todas e Ver todas as postagens. |

## Pré-condições

- Sessão autenticada em Aplicativo com a seção Postagens disponível e lista sem registros.
- Identificar a versão e registrar os valores iniciais e as permissões no próximo teste.

## Cenário BDD

```gherkin
Cenário: Alternar o filtro de postagens e abrir a lista completa
  Dado que a seção Postagens está vazia
  Quando o usuário alterna o filtro e abre Todas as postagens
  Então a lista e o diálogo devem informar a ausência de registros para o modo ativo
  E o filtro atual deve ser preservado ao abrir o diálogo
```

## Passos para execução ou reteste

1. Verificar a seção Postagens com base vazia.
2. Alternar para Só pendentes e conferir o aviso.
3. Selecionar Ver todas e abrir a lista completa.
4. Fechar, repetir a abertura no modo pendentes e comparar o aviso do diálogo.

Este procedimento orienta a próxima execução. O resultado abaixo se limita ao trecho registrado no Jam.

## Resultado esperado

O modo todas informa ausência de postagens cadastradas. O modo pendentes informa ausência de postagens aguardando aprovação. O diálogo reflete o modo da lista.

## Resultado obtido na gravação

A lista alternou entre os dois avisos e o diálogo abriu com o filtro ativo nas duas tentativas. Em ambas, o total exibido no diálogo era zero. Fechar retornou ao painel.

| Tempo | Registro |
| --- | --- |
| 0:06,89–0:08,79 | Alterna Só pendentes e Ver todas no painel. |
| 0:11,30–0:13,83 | Abre o diálogo no modo todas e fecha. |
| 0:15,20–0:18,66 | Seleciona pendentes, abre o diálogo e fecha. |

**Rede:**

- A gravação registra os cliques e a troca dos avisos na interface. O trecho não contém uma nova consulta de postagens associada a esses cliques.

**Conclusão:** Aprovado conforme a gravação. A aprovação se limita à base vazia e à troca dos avisos. A filtragem de registros com estados diferentes exige massa de teste.

## Critérios de aceitação para nova execução

1. Os dois modos exibem textos de lista vazia coerentes com o filtro.
2. Todas as postagens abre e mostra o mesmo modo aplicado no painel.
3. O diálogo fecha e retorna ao painel.

## Próxima ação e verificações complementares

Repetir com postagens pendentes e aprovadas para conferir a seleção de registros e o total do diálogo.

## Evidências e limites

- Jam 4 — Filtros e lista completa de postagens (gravação restrita por conter dados de integração ou dados de alunos).
- [Arquivos, origem e limites](../Evidencias/CT-RF160_Aplicativo_Postagens_Filtros_Estados_Vazios/README.md).
- [Diálogo em todas as postagens com o aviso de lista vazia](../Evidencias/CT-RF160_Aplicativo_Postagens_Filtros_Estados_Vazios/postagens_todas_00-12.jpg), [Diálogo filtrado pelas pendentes e sem postagens aguardando aprovação](../Evidencias/CT-RF160_Aplicativo_Postagens_Filtros_Estados_Vazios/postagens_pendentes_00-18.jpg).
- [Linha do tempo](../Evidencias/CT-RF160_Aplicativo_Postagens_Filtros_Estados_Vazios/linha_do_tempo.txt).

A revisão documental se baseia nos quadros do vídeo e nos eventos capturados pelo Jam. As verificações complementares ficam para uma nova rodada de testes.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf160) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
