# 🧪 Cenário 98: Busca de colaborador por código existente

**Caso de teste:** CT-RF98  
**Módulo:** Colaboradores / Busca por código  
**Status:** Aprovado conforme a gravação.  
**Gravação:** 15/11/2026, 22:00 BRT. **Revisão documental:** 15/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Verificar se a busca por um código existente retorna o colaborador correspondente. |
| Requisito | [RF98](../Analise%20de%20requisitos.md#rf98), referência de QA proposta a partir da evidência. |
| Tipo / prioridade | Funcional manual / caminho positivo; Média, proposta. |
| Defeito | Nenhum identificado no fluxo avaliado. |
| Fonte | [Jam](https://jam.dev/c/415a6ea3-273b-40f7-b3e4-f2b767dc7dfd). |

## Pré-condições

- Sessão autenticada com acesso à listagem de colaboradores.
- Existir um colaborador com código conhecido no ambiente.

## Cenário BDD

```gherkin
Cenário: Localizar colaborador por código existente
  Dado que existe um colaborador com o código informado
  E o usuário está na listagem de colaboradores
  Quando preencher o filtro Código
  E clicar em "Buscar"
  Então o sistema deve exibir o colaborador associado ao código
  E não deve exibir registros de outros códigos
```

## Passos observados

1. Acessar a página **Colaboradores**.
2. Informar um código existente no campo **Código**.
3. Clicar em **Buscar**.
4. Conferir a linha retornada.

## Resultado esperado

Exibir somente o colaborador cujo código seja igual ao valor pesquisado.

## Resultado obtido

O sistema retornou o usuário correto para o código existente. A gravação identifica o resultado como: “busca por código existente, retorna usuário correto”.

## Critérios de aceitação para regressão

1. Código existente retorna exatamente o registro associado.
2. A linha mantém código, nome e demais informações do colaborador corretos.
3. Nenhum registro de código diferente é exibido.
4. Limpar o filtro restaura a listagem e a paginação padrão.

## Evidências e limites

- [Jam original](https://jam.dev/c/415a6ea3-273b-40f7-b3e4-f2b767dc7dfd), com 4 segundos, página `https://sifit.centrion.com.br/colaboradores`.
- Ambiente informado pelo Jam: Edge 157.0.8103.80, Windows 11, Brasil.
- A aprovação se limita ao exemplo gravado; não cobre códigos com zeros à esquerda, limites, caracteres inválidos ou combinação com o filtro por nome.
- Não houve nova execução, consulta ao banco ou inspeção do código.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf98) · [Plano](../Plano%20de%20testes.md) · [Relatório](../Relatorio%20dos%20testes.md)
