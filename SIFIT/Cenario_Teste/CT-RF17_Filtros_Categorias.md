# 🧪 Cenário 17: Filtros de categorias por código e nome

**Caso de teste:** CT-RF17

**Módulo:** Categorias Crossfit / Pesquisa

**Status:** Aprovado conforme a gravação.

**Gravação:** 14/11/2026, 00:41:02 BRT. **Revisão documental:** 14/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Filtrar categorias por código e nome. |
| Requisito | [RF17](../Analise%20de%20requisitos.md#rf17) |
| Tipo / prioridade | Funcional manual, análise de evidências / Média, proposta para triagem. |
| Defeito | Nenhum no fluxo avaliado |
| Encaminhamento | Sem reteste corretivo pendente; manter como regressão. |
| Fonte | [Jam — filtros corretos e funcionando](https://jam.dev/c/5e75e423-9c7e-43d7-aade-9b1a32c5e559) |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/categorias-exercicios-crossfit |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.51 / Windows 11 (x86). |
| Tela / arquivo de vídeo | 1920 × 957 informados no Jam; original 1918 × 956 pixels. |
| Duração | 17,91 s |
| Versão / zoom / classificação do ambiente | Não confirmados; registrar antes de nova execução. |
| Dados | Usar dados de teste conhecidos conforme as pré-condições abaixo; valores da gravação são referência histórica, sem copiar credenciais. |

## Pré-condições

- Sessão autenticada e acesso a Categorias Crossfit.
- Categorias conhecidas por código e nome para comparação.
- Antes de uma nova execução, identificar versão, permissões e dados de referência e preparar a captura de interface e rede.

## Cenário BDD

```gherkin
Cenário: Filtrar categorias por código e nome
  Dado que existem categorias conhecidas por código e nome
  Quando pesquisar um código ou o nome "barbell"
  Então a listagem deve apresentar os registros correspondentes
  E ao limpar a pesquisa deve restaurar o conjunto geral permitido
```

## Passos para execução ou reteste

1. Pesquisar por códigos conhecidos e conferir o resultado exibido.
2. Limpar a busca com a ação de recarregar/limpar e conferir a lista geral.
3. Pesquisar barbell no campo Nome e comparar as linhas com a base.

Este procedimento orienta a próxima execução. A evidência atual cobre o trecho gravado e os limites descritos abaixo; passos complementares, como conferir downloads ou recarregar a sessão, não recebem resultado de execução nesta revisão.

## Resultado esperado

Exibir apenas os registros correspondentes aos critérios e restaurar a lista ao limpar.

## Resultado obtido na gravação

A quantidade de linhas exibidas muda conforme o código informado; a limpeza retorna a lista e a busca por barbell mostra a categoria correspondente.

**Momentos e registros:** 0:00–0:09: buscas por código. 0:11: limpeza. 0:14–0:17: pesquisa por nome.

**Conclusão:** Aprovado conforme a gravação. A aprovação se limita ao cenário visível; não significa validação de todas as variações do fluxo.

## Critérios de aceitação para nova execução

1. Código restringe ao registro correspondente.
2. Nome restringe conforme a regra de correspondência definida.
3. Limpar a pesquisa restaura a listagem e a contagem.

## Próxima ação e verificações complementares

Usar como regressão; combinações, conjunto vazio, caracteres especiais e paginação exigem execuções adicionais.

Nenhum defeito adicional foi criado para este cenário.

## Evidências e limites

- [Jam original — filtros corretos e funcionando](https://jam.dev/c/5e75e423-9c7e-43d7-aade-9b1a32c5e559).
- [Vídeo original](../Evidencias/CT-RF17_Filtros_Categorias/video.webm).
- [Resumo, origem e integridade](../Evidencias/CT-RF17_Filtros_Categorias/README.md).
- [Cronologia do Jam](../Evidencias/CT-RF17_Filtros_Categorias/linha_do_tempo.txt).

Resultado válido para os exemplos gravados. Não cobre combinações de filtros, valores inválidos, caracteres especiais ou paginação.

Análise documental das gravações já consultadas em 14/11/2026 (metadados, cronologia e quadros distribuídos pelo vídeo). Esta inclusão não executa novamente o sistema, não corrige a aplicação e não constitui reteste. Versão da aplicação, zoom e classificação do ambiente não foram confirmados.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
