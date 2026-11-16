# 🧪 Cenário 70: Exclusão de colaborador retorna HTTP 500

**Caso de teste:** CT-RF70  
**Módulo:** Colaboradores / Exclusão  
**Status:** Reprovado nas evidências; reteste corretivo pendente.  
**Gravação:** 15/11/2026, 22:06 BRT. **Revisão documental:** 15/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Excluir colaborador quando permitido ou explicar de forma tratável o impedimento, sem erro interno genérico. |
| Requisito | [RF70](../Analise%20de%20requisitos.md#rf70), referência de QA proposta. |
| Tipo / prioridade | Funcional manual / fluxo destrutivo controlado; Alta, proposta. |
| Defeito | [BUG-029](../Relatorio-de-Bugs.md#bug-029), em triagem. |
| Fonte | [Jam](https://jam.dev/c/05be297b-22d9-4d26-beff-937526bcd816). |

## Cenário BDD

```gherkin
Cenário: Excluir colaborador
  Dado que o usuário possui permissão para excluir colaboradores
  E os vínculos do registro são conhecidos
  Quando confirmar a exclusão
  Então o sistema deve excluir o registro permitido
  Ou explicar especificamente o vínculo que impede a operação
  E não deve responder com erro interno HTTP 500
```

## Passos e resultado

1. Acionar a exclusão de um colaborador.
2. Clicar em **Confirmar**.
3. Conferir a resposta e a permanência do registro.

**Esperado:** exclusão concluída ou impedimento de negócio explicado.  
**Obtido:** `POST /api/deleta/colaborador/1`, com payload contendo `id: 3`, retornou **HTTP 500** e `{"verifica_erro":true,"mensagem":"Erro interno inesperado."}`. A interface exibiu erro com opção **Fechar**.

## Critérios de aceitação para reteste

1. Registro sem vínculos impeditivos é excluído e removido da lista.
2. Registro com vínculos recebe mensagem específica e permanece íntegro.
3. Nenhum cenário de negócio retorna HTTP 500.
4. Logs permitem correlacionar o erro e a operação não deixa exclusão parcial.

## Evidências e limites

- [Jam original](https://jam.dev/c/05be297b-22d9-4d26-beff-937526bcd816).
- O Jam confirma endpoint, payload, HTTP 500 e corpo da resposta; não identifica o vínculo ou a causa raiz.
- Não houve acesso aos logs, ao banco, ao código ou nova execução.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf70) · [Plano](../Plano%20de%20testes.md) · [Relatório](../Relatorio%20dos%20testes.md)
