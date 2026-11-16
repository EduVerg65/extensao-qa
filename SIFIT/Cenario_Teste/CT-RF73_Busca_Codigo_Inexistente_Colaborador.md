# 🧪 Cenário 73: Busca de colaborador por código inexistente

**Caso de teste:** CT-RF73  
**Módulo:** Colaboradores / Busca por código  
**Status:** Reprovado nas evidências; reteste corretivo pendente.  
**Gravação:** 15/11/2026, 21:58 BRT. **Revisão documental:** 15/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Exibir um estado vazio claro ao pesquisar um código de colaborador inexistente, sem criar linha vazia na tabela. |
| Requisito | [RF73](../Analise%20de%20requisitos.md#rf73), referência de QA proposta a partir da evidência. |
| Tipo / prioridade | Funcional manual / teste negativo; Média / Alta, propostas. |
| Defeito | [BUG-033](../Relatorio-de-Bugs.md#bug-033), em triagem. |
| Fonte | [Jam](https://jam.dev/c/cdbb3d76-3d6a-4d36-adf9-edd935b5a449). |

## Pré-condições

- Sessão autenticada com acesso à listagem de colaboradores.
- Código escolhido não associado a nenhum colaborador no ambiente.

## Cenário BDD

```gherkin
Cenário: Pesquisar código de colaborador inexistente
  Dado que nenhum colaborador possui o código informado
  Quando o usuário preencher o filtro Código
  E clicar em "Buscar"
  Então o sistema deve exibir um estado de nenhum resultado
  E não deve renderizar linhas vazias ou ações sem registro associado
```

## Passos observados

1. Acessar a página **Colaboradores**.
2. Informar um código inexistente no campo **Código**.
3. Clicar em **Buscar**.
4. Conferir a tabela de resultados.

## Resultado esperado

Apresentar lista vazia com mensagem clara de que nenhum colaborador foi encontrado, sem linha ou ações de registro.

## Resultado obtido

A busca por código inexistente retorna uma linha vazia na tabela. A gravação identifica o resultado como: “busca por código inexistente retorna linha vazia com bug”.

## Critérios de aceitação para reteste

1. Código inexistente produz conjunto vazio.
2. Uma mensagem de “nenhum colaborador encontrado” é exibida.
3. Nenhuma linha, ícone de ação ou dado parcial é renderizado.
4. Contadores e paginação representam zero resultados.
5. Uma busca válida posterior substitui corretamente o estado vazio.

## Evidências e limites

- [Jam original](https://jam.dev/c/cdbb3d76-3d6a-4d36-adf9-edd935b5a449), com 4 segundos, página `https://sifit.centrion.com.br/colaboradores`.
- Ambiente informado pelo Jam: Edge 157.0.8103.80, Windows 11, Brasil.
- A evidência confirma visualmente a linha vazia; resposta da API, valor exato pesquisado e causa técnica não foram confirmados nesta revisão.
- Não houve nova execução, acesso ao banco, logs ou código.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf73) · [Plano](../Plano%20de%20testes.md) · [Relatório](../Relatorio%20dos%20testes.md)
