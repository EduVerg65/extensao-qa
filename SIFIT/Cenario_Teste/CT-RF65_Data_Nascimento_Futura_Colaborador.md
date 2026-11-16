# 🧪 Cenário 65: Salvar colaborador com data de nascimento futura

**Caso de teste:** CT-RF65  
**Módulo:** Colaboradores / Edição  
**Status:** Reprovado nas evidências; reteste corretivo pendente.  
**Gravação:** 15/11/2026, 22:13 BRT. **Revisão documental:** 15/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Impedir o salvamento de colaborador com data de nascimento posterior à data atual e apresentar validação compreensível. |
| Requisito | [RF65](../Analise%20de%20requisitos.md#rf65), referência de QA proposta a partir da evidência. |
| Tipo / prioridade | Funcional manual / teste negativo; Alta, proposta para triagem. |
| Defeito | [BUG-026](../Relatorio-de-Bugs.md#bug-026), em triagem. |
| Fonte | [Jam](https://jam.dev/c/6dd75961-8e8f-4c8e-939a-19595a1f8a32). |

## Pré-condições

- Sessão autenticada com permissão para editar colaboradores.
- Colaborador de teste existente e data atual conhecida no ambiente.
- Captura de interface e rede habilitada.

## Cenário BDD

```gherkin
Cenário: Recusar data de nascimento futura
  Dado que o usuário está editando um colaborador
  Quando informar uma data de nascimento posterior à data atual
  E clicar em "Salvar"
  Então o sistema deve bloquear a atualização
  E informar que a data de nascimento não pode estar no futuro
  E deve manter os dados anteriores do colaborador
```

## Passos observados

1. Acessar a edição do colaborador de id 1.
2. Informar `18/05/2222` no campo de data de nascimento.
3. Clicar em **Salvar**.
4. Conferir a resposta e a persistência.

## Resultado esperado

Bloquear o envio, destacar o campo e explicar que a data de nascimento não pode ser futura.

## Resultado obtido

O sistema enviou `POST /api/atualizar/colaborador/1`, recebeu **HTTP 200** e navegou para `/colaboradores`. Não houve validação visível. O corpo da atualização não foi capturado, portanto a persistência da data deve ser confirmada no reteste.

## Critérios de aceitação para reteste

1. Datas posteriores à data atual são recusadas antes da persistência.
2. A mensagem identifica o campo e o motivo do impedimento.
3. A data limite válida é aceita conforme a regra do produto.
4. A data anterior permanece inalterada após tentativa inválida e recarga.

## Evidências e limites

- Jam original e eventos de interação/rede consultados diretamente.
- A gravação registra a digitação, o clique em Salvar e HTTP 200; não registra o corpo do POST.
- Não houve nova execução, consulta ao banco, inspeção do código ou confirmação de causa raiz.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf65) · [Plano](../Plano%20de%20testes.md) · [Relatório](../Relatorio%20dos%20testes.md)
