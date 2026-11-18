# 🧪 Cenário 107: Desativar Risco de Evasão e conferir a persistência e o contador

**Caso de teste:** CT-RF107

**Módulo:** Inteligência e Automação / Central / Risco de Evasão

**Status:** Reprovado nas evidências.

**Gravação:** 16/11/2026, 21:28:33 BRT. **Revisão documental:** 17/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Confirmar que a desativação de Risco de Evasão persiste após Atualizar e que o resumo acompanha a desativação e a restauração do estado ativo. |
| Requisito | [RF107](../Analise%20de%20requisitos.md#rf107) — referência de QA. |
| Tipo / prioridade | Funcional manual / persistência e contador · Média, proposta para triagem. |
| Defeito | [BUG-049](../Relatorio-de-Bugs.md#bug-049), em triagem |
| Encaminhamento | Retestar desativação e reativação. Conferir se o contador passa a um após o sucesso do salvamento, antes de Atualizar manualmente. |
| Fonte | [Jam — PED-02 — Desativar Risco de Evasão](https://jam.dev/c/b63ec55f-f8b6-41aa-af4c-d4cdd4515de8) e [evidências locais](../Evidencias/CT-RF135_Central_Desativar_Risco_Evasao_Contador/README.md). |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/inteligencia-automacao |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.79 / Windows 10 (x86), conforme os metadados do Jam. |
| Tela / arquivo de vídeo | Tela 1920 × 999 informada no Jam. Vídeo em 1918 × 998. |
| Duração | 20,02 s |
| Localização | Brasil. |
| Versão / zoom / classificação do ambiente | A confirmar antes de nova execução. |
| Dados | Risco de Evasão ativa no início. Desativada para o teste e reativada na etapa de restauração. |

## Pré-condições

- Sessão autenticada na Central, com Risco de Evasão como a única automação ativa no cenário de teste.
- Identificar a versão e registrar os valores iniciais e as permissões no próximo teste.

## Cenário BDD

```gherkin
Cenário: Desativar Risco de Evasão e conferir a persistência e o contador
  Dado que Risco de Evasão está ativa e o resumo mostra uma automação ativa
  Quando o usuário desativar a automação, acionar Atualizar e depois reativá-la
  Então o estado inativo deve persistir após Atualizar
  E o contador deve refletir o estado confirmado pelo salvamento em ambas as alterações
```

## Passos para execução ou reteste

1. Registrar o estado inicial do cartão e o contador de automações ativas.
2. Desativar Risco de Evasão e aguardar a resposta do salvamento.
3. Acionar Atualizar e conferir a persistência do estado inativo.
4. Reativar a automação e comparar o cartão e o contador após o sucesso do salvamento.

Este procedimento orienta a próxima execução. O resultado abaixo se limita ao trecho registrado no Jam.

## Resultado esperado

A automação permanece inativa após Atualizar com o contador em zero. Ao reativar com sucesso, o cartão volta a indicar o estado ativo e o contador volta a um.

## Resultado obtido na gravação

A desativação foi salva com HTTP 200. Após Atualizar, a lista confirmou `ativo: 0` e o contador marcou zero. A reativação também retornou sucesso e o cartão voltou a indicar o estado ativo, mas o resumo retornou `ativas: 0`. O contador permaneceu em zero no restante da gravação.

| Tempo | Registro |
| --- | --- |
| 0:00–0:05 | Risco de Evasão começa ativa e o resumo mostra uma automação. |
| 0:05–0:11 | Desativa Risco de Evasão e aciona Atualizar. O estado inativo e o contador zero se mantêm. |
| 0:12–0:20 | Reativa a automação. O cartão fica ativo, mas o resumo continua mostrando zero. |

**Rede:**

- 0:05,41  POST `/api/automacoes/salvar/1` (HTTP 200), com `tipo: risco_evasao`, `ativo: 0` e `verifica_erro: false` na resposta. O GET de resumo retornou `ativas: 0`.
- 0:09,30  Atualizar. GET `/api/automacoes/1` com `ativo: 0` para Risco de Evasão e GET de resumo com `ativas: 0` (HTTP 200).
- 0:12,74  POST com `ativo: 1` (HTTP 200, `verifica_erro: false`). O GET de resumo associado retornou `ativas: 0`.

**Conclusão:** Reprovado nas evidências. A persistência foi confirmada por nova leitura para a desativação. Após a reativação, a gravação não contém outro clique em Atualizar. A ordem em que o servidor processou o salvamento e o resumo não foi determinada.

## Critérios de aceitação para nova execução

1. A desativação é salva e permanece após Atualizar.
2. O contador chega a zero quando nenhuma automação está ativa.
3. Após reativar com sucesso, o cartão e o contador refletem o novo estado.

## Próxima ação e verificações complementares

Retestar desativação e reativação. Conferir se o contador passa a um após o sucesso do salvamento, antes de Atualizar manualmente.

## Evidências e limites

- [Jam original — PED-02 — Desativar Risco de Evasão](https://jam.dev/c/b63ec55f-f8b6-41aa-af4c-d4cdd4515de8).
- [Arquivos, origem e limites](../Evidencias/CT-RF135_Central_Desativar_Risco_Evasao_Contador/README.md).
- [Risco de Evasão inativa e contador em zero após Atualizar](../Evidencias/CT-RF135_Central_Desativar_Risco_Evasao_Contador/evasao_inativa_00-11.jpg), [Risco de Evasão ativa com contador ainda em zero](../Evidencias/CT-RF135_Central_Desativar_Risco_Evasao_Contador/evasao_ativa_contador_zero_00-17.jpg).
- [Linha do tempo](../Evidencias/CT-RF135_Central_Desativar_Risco_Evasao_Contador/linha_do_tempo.txt).

A revisão documental se baseia nos quadros do vídeo e nos eventos capturados pelo Jam. As verificações complementares ficam para uma nova rodada de testes.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf107) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
