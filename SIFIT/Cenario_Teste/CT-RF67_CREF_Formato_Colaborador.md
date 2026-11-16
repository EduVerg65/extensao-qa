# 🧪 Cenário 67: Campo CREF aceita texto livre

**Caso de teste:** CT-RF67  
**Módulo:** Colaboradores / Edição / CREF  
**Status:** Reprovado nas evidências; regra exata e reteste pendentes.  
**Gravação:** 15/11/2026, 22:11 BRT. **Revisão documental:** 15/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Validar o CREF conforme formato definido pelo produto e impedir texto incompatível com essa regra. |
| Requisito | [RF67](../Analise%20de%20requisitos.md#rf67), referência de QA proposta; formato oficial deve ser confirmado. |
| Tipo / prioridade | Funcional manual / validação de campo; Média, proposta. |
| Defeito | [BUG-028](../Relatorio-de-Bugs.md#bug-028), em triagem. |
| Fonte | [Jam](https://jam.dev/c/243d9699-4bee-495d-ae65-9a02e42813b3). |

## Cenário BDD

```gherkin
Cenário: Recusar CREF fora do formato permitido
  Dado que o usuário está editando um colaborador sujeito a CREF
  Quando informar um texto que não atende ao formato definido
  E clicar em "Salvar"
  Então o sistema deve bloquear a atualização
  E explicar o formato aceito
```

## Passos e resultado

1. Acessar a edição do colaborador.
2. Informar `TESTEE` no campo CREF.
3. Clicar em **Salvar**.

**Esperado:** validar o formato acordado e recusar valor incompatível, com orientação.  
**Obtido:** o campo aceitou `TESTEE`; `POST /api/atualizar/colaborador/1` retornou **HTTP 200** e não houve validação visível. O corpo do POST não foi capturado.

## Critérios de aceitação para reteste

1. Confirmar com produto o formato, UF, quantidade de dígitos e casos em que CREF é obrigatório.
2. Aceitar exemplos válidos e recusar texto livre, tamanho e caracteres inválidos.
3. Validar no cliente e no servidor, sem persistir valor recusado.
4. Informar o formato esperado sem expor dados pessoais reais.

## Evidências e limites

- [Jam original](https://jam.dev/c/243d9699-4bee-495d-ae65-9a02e42813b3).
- A conclusão depende da confirmação formal do formato de CREF adotado pelo produto.
- Não houve nova execução, consulta ao banco ou inspeção do código.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf67) · [Plano](../Plano%20de%20testes.md) · [Relatório](../Relatorio%20dos%20testes.md)
