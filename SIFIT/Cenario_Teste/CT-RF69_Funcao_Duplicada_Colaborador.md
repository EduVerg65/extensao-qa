# 🧪 Cenário 69: Adicionar a mesma função repetidamente ao colaborador

**Caso de teste:** CT-RF69  
**Módulo:** Colaboradores / Funções  
**Status:** Reprovado nas evidências; reteste corretivo pendente.  
**Gravação:** 15/11/2026, 22:07 BRT. **Revisão documental:** 15/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Impedir associações duplicadas da mesma função ao mesmo colaborador. |
| Requisito | [RF69](../Analise%20de%20requisitos.md#rf69), referência de QA proposta. |
| Tipo / prioridade | Funcional manual / integridade e duplicidade; Média, proposta. |
| Defeito | [BUG-028](../Relatorio-de-Bugs.md#bug-028), em triagem. |
| Fonte | [Jam](https://jam.dev/c/ba2400f9-dbb0-45bc-a509-187249dbe9da). |

## Cenário BDD

```gherkin
Cenário: Impedir função duplicada para o mesmo colaborador
  Dado que o colaborador já possui a função Personal Interno
  Quando o usuário tentar adicionar novamente a mesma função
  Então o sistema deve impedir a duplicidade
  E informar que a função já está associada
  E deve manter apenas uma associação ativa
```

## Resultado observado

O colaborador 4 iniciou com uma associação `Personal Interno` (`funcao_id: 2`). Duas ações em **Adicionar** enviaram `POST /api/funcao-colaborador/salvar/1`, ambas com **HTTP 201** e resposta `true`. As consultas seguintes retornaram duas e depois três associações iguais, com ids 51, 154 e 155.

**Esperado:** uma única associação ou mensagem de duplicidade.  
**Obtido:** três associações da mesma função ao mesmo colaborador.

## Critérios de aceitação para reteste

1. A combinação colaborador/função é única entre associações ativas.
2. A tentativa duplicada não cria nova linha e recebe mensagem específica.
3. Cliques repetidos e requisições concorrentes não geram duplicidade.
4. A regra é protegida no servidor e, quando aplicável, por restrição de integridade.

## Evidências e limites

- [Jam original](https://jam.dev/c/ba2400f9-dbb0-45bc-a509-187249dbe9da).
- Endpoints, payloads e respostas foram registrados nos eventos públicos do Jam.
- Não houve consulta direta ao banco, inspeção do código, nova execução ou correção.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf69) · [Plano](../Plano%20de%20testes.md) · [Relatório](../Relatorio%20dos%20testes.md)
