# 🧪 Cenário 71: Busca de colaborador por nome mantém o filtro na paginação

**Caso de teste:** CT-RF71  
**Módulo:** Colaboradores / Busca por nome  
**Status:** Reprovado nas evidências; reteste corretivo pendente.  
**Gravação:** 15/11/2026, 22:01 BRT. **Revisão documental:** 15/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Garantir que a busca por nome retorne somente colaboradores correspondentes em todas as páginas do resultado. |
| Requisito | [RF71](../Analise%20de%20requisitos.md#rf71), referência de QA proposta a partir da evidência. |
| Tipo / prioridade | Funcional manual / filtro e paginação; Média / Alta, propostas. |
| Defeito | [BUG-033](../Relatorio-de-Bugs.md#bug-033), em triagem. |
| Fonte | [Jam](https://jam.dev/c/b35516e3-c571-47ea-b233-28f00d1fca4c). |

## Pré-condições

- Sessão autenticada com acesso à listagem de colaboradores.
- Existirem colaboradores correspondentes e não correspondentes ao nome pesquisado.
- A consulta possuir mais de uma página ou permitir avançar a paginação.

## Cenário BDD

```gherkin
Cenário: Manter o filtro por nome ao navegar entre páginas
  Dado que o usuário está na listagem de colaboradores
  Quando informar um nome no filtro
  E clicar em "Buscar"
  E avançar para a próxima página do resultado
  Então todas as linhas exibidas devem corresponder ao nome pesquisado
  E nenhum colaborador fora do filtro deve ser apresentado
```

## Passos observados

1. Acessar a página **Colaboradores**.
2. Informar um nome no campo de busca por nome.
3. Clicar em **Buscar**.
4. Conferir os resultados correspondentes.
5. Avançar para a próxima página.
6. Conferir novamente os nomes exibidos.

## Resultado esperado

O critério informado deve permanecer aplicado durante toda a paginação, e cada página deve conter somente colaboradores cujo nome corresponda à busca.

## Resultado obtido

A busca retorna nomes correspondentes inicialmente, porém a página seguinte também apresenta nomes fora do filtro desejado. A gravação identifica o comportamento como: “busca por nome, retorna os nomes correspondentes e outros nomes fora do filtro desejado na próxima página”.

## Critérios de aceitação para reteste

1. O filtro por nome é enviado ou preservado em toda troca de página.
2. Todas as páginas contêm apenas registros compatíveis com o termo pesquisado.
3. O total e a quantidade de páginas representam somente o conjunto filtrado.
4. Alterar ou limpar o termo reinicia a paginação de forma coerente.
5. Busca sem correspondência exibe estado vazio, sem registros residuais.

## Evidências e limites

- [Jam original](https://jam.dev/c/b35516e3-c571-47ea-b233-28f00d1fca4c), com 8 segundos, página `https://sifit.centrion.com.br/colaboradores`.
- Ambiente informado pelo Jam: Edge 157.0.8103.80, Windows 11, Brasil.
- A evidência confirma visualmente registros fora do filtro após a paginação; parâmetros e respostas de rede não foram inspecionados nesta revisão.
- Não houve nova execução, acesso ao banco, logs ou código; a causa técnica não foi determinada.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf71) · [Plano](../Plano%20de%20testes.md) · [Relatório](../Relatorio%20dos%20testes.md)
