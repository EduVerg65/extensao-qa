# 🧪 Cenário 66: Salvar colaborador sem data de nascimento obrigatória

**Caso de teste:** CT-RF66  
**Módulo:** Colaboradores / Edição  
**Status:** Reprovado nas evidências; reteste corretivo pendente.  
**Gravação:** 15/11/2026, 22:12 BRT. **Revisão documental:** 15/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Impedir a atualização quando a data de nascimento obrigatória estiver vazia e orientar a correção. |
| Requisito | [RF66](../Analise%20de%20requisitos.md#rf66), referência de QA proposta. |
| Tipo / prioridade | Funcional manual / teste negativo; Alta, proposta. |
| Defeito | [BUG-025](../Relatorio-de-Bugs.md#bug-025), em triagem. |
| Fonte | [Jam](https://jam.dev/c/04aa5ba0-ac7e-43b6-a7f3-91ae82417a85). |

## Cenário BDD

```gherkin
Cenário: Recusar edição sem data de nascimento obrigatória
  Dado que o usuário está editando um colaborador
  E o campo Data de nascimento é obrigatório
  Quando remover o valor do campo
  E clicar em "Salvar"
  Então o sistema deve bloquear a atualização
  E indicar que a data de nascimento deve ser informada
```

## Passos e resultado

1. Acessar `/alterar-colaborador/1`.
2. Limpar a data de nascimento.
3. Clicar em **Salvar**.

**Esperado:** envio bloqueado, mensagem por campo e dados anteriores preservados.  
**Obtido:** `POST /api/atualizar/colaborador/1` retornou **HTTP 200** e o fluxo navegou para a lista, sem validação visível. O corpo do POST não foi capturado; confirmar persistência no reteste.

## Critérios de aceitação para reteste

1. Campo vazio não gera atualização.
2. Mensagem e foco identificam a data obrigatória.
3. Espaços, valor apagado e valor inválido são tratados de forma consistente.
4. O valor anterior permanece após recarga.

## Evidências e limites

- [Jam original](https://jam.dev/c/04aa5ba0-ac7e-43b6-a7f3-91ae82417a85), com ações e rede consultadas.
- Não houve nova execução, acesso ao banco ou inspeção do código.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf66) · [Plano](../Plano%20de%20testes.md) · [Relatório](../Relatorio%20dos%20testes.md)
