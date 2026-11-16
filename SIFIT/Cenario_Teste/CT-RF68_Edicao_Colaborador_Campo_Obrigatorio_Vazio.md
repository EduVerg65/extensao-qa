# 🧪 Cenário 68: Editar colaborador com campo obrigatório vazio

**Caso de teste:** CT-RF68  
**Módulo:** Colaboradores / Edição  
**Status:** Reprovado nas evidências; campo exato e reteste pendentes.  
**Gravação:** 15/11/2026, 22:09 BRT. **Revisão documental:** 15/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Bloquear a edição quando qualquer campo definido como obrigatório estiver vazio e indicar o impedimento. |
| Requisito | [RF68](../Analise%20de%20requisitos.md#rf68), referência de QA proposta. |
| Tipo / prioridade | Funcional manual / teste negativo; Alta, proposta. |
| Defeito | [BUG-027](../Relatorio-de-Bugs.md#bug-027), em triagem. |
| Fonte | [Jam](https://jam.dev/c/4219c1b3-085e-4218-b181-5cf448d64cea). |

## Cenário BDD

```gherkin
Cenário: Recusar edição com campo obrigatório vazio
  Dado que o usuário está editando um colaborador
  Quando deixar um campo obrigatório vazio
  E clicar em "Salvar"
  Então o sistema deve bloquear a atualização
  E identificar o campo que precisa ser preenchido
```

## Resultado observado

A gravação percorre visualização e edição, mantém campos de texto vazios, informa `Test` em uma observação e aciona **Salvar**. `POST /api/atualizar/colaborador/1` retorna **HTTP 200** e a lista é recarregada, sem validação visível.

**Esperado:** bloquear a atualização e indicar todos os campos obrigatórios vazios.  
**Obtido:** atualização aceita pelo endpoint. Os corpos do POST não foram capturados e o rótulo do campo vazio não pôde ser determinado apenas pelos eventos; deve ser registrado no reteste.

## Critérios de aceitação para reteste

1. Mapear formalmente todos os campos obrigatórios da edição.
2. Bloquear envio para cada campo obrigatório vazio, isoladamente e em conjunto.
3. Exibir mensagem próxima ao campo e preservar os dados anteriores.
4. Reabrir o cadastro e confirmar ausência de persistência parcial.

## Evidências e limites

- [Jam original](https://jam.dev/c/4219c1b3-085e-4218-b181-5cf448d64cea).
- O campo obrigatório específico não está identificável na cronologia capturada; isso não deve ser inferido.
- Não houve nova execução, acesso ao banco ou inspeção do código.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf68) · [Plano](../Plano%20de%20testes.md) · [Relatório](../Relatorio%20dos%20testes.md)
