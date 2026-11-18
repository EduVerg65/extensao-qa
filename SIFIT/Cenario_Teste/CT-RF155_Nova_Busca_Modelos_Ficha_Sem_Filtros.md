# 🧪 Cenário 155: Pesquisar novamente modelos de ficha sem filtros

**Caso de teste:** CT-RF155

**Módulo:** Configurações / Modelo Ficha / Busca sem filtros

**Status:** A validar — regra ou contexto pendente.

**Gravação:** 16/11/2026, 22:29:07 BRT. **Revisão documental:** 17/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Recuperar a listagem padrão após uma pesquisa restritiva e a remoção de todos os filtros. |
| Requisito | [RF155](../Analise%20de%20requisitos.md#rf155) — referência de QA. Confirmação de produto pendente. |
| Tipo / prioridade | Funcional manual / recuperação da listagem · Média, proposta para triagem. |
| Defeito | Sem defeito confirmado |
| Encaminhamento | Reexecutar com listagem padrão populada, pesquisa restritiva e comparação dos registros após a nova busca. |
| Fonte | [Jam — Modelos de Ficha (PED-30)](https://jam.dev/c/297eec2b-7be4-498b-a0e6-e962ed93cc00) e [evidências locais](../Evidencias/CT-RF115_Nova_Busca_Modelos_Ficha_Sem_Filtros/README.md). A limpeza dos campos está documentada em [CT-RF154](CT-RF154_Limpeza_Filtros_Modelos_Ficha.md). |

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
| Dados | Os três campos estavam vazios após a limpeza registrada no CT-RF154. O Jam mostra 0 registros antes e depois da pesquisa. |

## Pré-condições

- Sessão autenticada, listagem padrão com registros de referência e busca anterior que restrinja o resultado.
- Identificar a versão e preparar a captura da listagem, do formulário ou dos filtros e dos eventos de rede pertinentes.

## Cenário BDD

```gherkin
Cenário: Pesquisar novamente modelos de ficha sem filtros
  Dado que a listagem padrão contém modelos e uma busca anterior restringiu os resultados
  Quando o usuário limpar todos os campos e acionar Buscar novamente
  Então a listagem deve voltar a apresentar os modelos disponíveis sem os filtros anteriores
  E a contagem da listagem deve refletir o resultado sem filtros
```

## Passos para execução ou reteste

1. Registrar IDs e contagem da listagem padrão com modelos cadastrados.
2. Aplicar um filtro que reduza os resultados, preferencialmente a 0 registros.
3. Limpar Código, Título e Criador. Acionar Buscar e aguardar o fim do carregamento.
4. Comparar os registros e a contagem com a listagem padrão e capturar a requisição e a resposta.

Este procedimento orienta a próxima execução. O resultado abaixo se limita ao trecho registrado no Jam.

## Resultado esperado

Após a nova pesquisa, os registros padrão reaparecem, a contagem é atualizada e os campos permanecem em branco.

## Resultado obtido na gravação

Com os três campos vazios, Buscar foi acionado duas vezes. As duas consultas retornaram HTTP 200 com `[]`. A interface exibiu o carregamento durante a busca e terminou com “Nenhum modelo de ficha encontrado” e 0 registros.

| Tempo | Registro |
| --- | --- |
| 0:11 | Primeiro clique em Buscar com os três filtros vazios. A listagem exibe o carregamento e o GET retorna HTTP 200 com `[]`. |
| 0:13 | Segundo clique em Buscar. O novo GET retorna HTTP 200 com `[]`. |
| 0:14 | A interface volta ao estado vazio, com 0 registros. |

**Rede:** Em 0:11 e 0:13, dois GET `/api/fichas-modelo/1`, ambos com HTTP 200 e corpo `[]` (2 B cada).

**Conclusão:** A validar — regra ou contexto pendente. A gravação não mostra uma listagem padrão populada. O estado vazio é compatível com os retornos, mas a recuperação de registros ocultados por uma pesquisa anterior ficou a validar.

## Critérios de aceitação para nova execução

1. Buscar com os três campos vazios atualiza a listagem e conclui o carregamento.
2. Em base populada, os registros disponíveis antes da busca restritiva reaparecem na consulta sem filtros.
3. A contagem e os campos refletem a consulta sem filtros.

## Próxima ação e verificações complementares

Reexecutar com listagem padrão populada, pesquisa restritiva e comparação dos registros após a nova busca.

## Evidências e limites

- [Jam original — PED-30](https://jam.dev/c/297eec2b-7be4-498b-a0e6-e962ed93cc00).
- [Arquivos, origem e limites](../Evidencias/CT-RF115_Nova_Busca_Modelos_Ficha_Sem_Filtros/README.md).
- [Listagem carregando em 0:11](../Evidencias/CT-RF115_Nova_Busca_Modelos_Ficha_Sem_Filtros/busca_sem_filtros_carregando_00-11.jpg), [Resultado da busca sem filtros em 0:14](../Evidencias/CT-RF115_Nova_Busca_Modelos_Ficha_Sem_Filtros/busca_sem_filtros_resultado_00-14.jpg).
- [Linha do tempo](../Evidencias/CT-RF115_Nova_Busca_Modelos_Ficha_Sem_Filtros/linha_do_tempo.txt).

Foram consultados os metadados, os eventos de rede e de interação e os quadros do vídeo. Os recortes estão na pasta de evidências. O vídeo permanece no Jam.

A revisão documental de 17/11/2026 registra a execução gravada. As verificações complementares ficam para uma nova rodada de testes.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf155) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
