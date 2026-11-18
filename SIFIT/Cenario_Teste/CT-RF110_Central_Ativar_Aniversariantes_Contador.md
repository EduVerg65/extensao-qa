# 🧪 Cenário 110: Ativar Aniversariantes e conferir a persistência e o contador

**Caso de teste:** CT-RF110

**Módulo:** Inteligência e Automação / Central / Aniversariantes

**Status:** Reprovado nas evidências.

**Gravação:** 16/11/2026, 21:31:02 BRT. **Revisão documental:** 17/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Confirmar que a ativação de Aniversariantes permanece após Atualizar e que o contador acompanha a alteração salva. |
| Requisito | [RF110](../Analise%20de%20requisitos.md#rf110) — referência de QA. |
| Tipo / prioridade | Funcional manual / persistência e contador · Média, proposta para triagem. |
| Defeito | [BUG-049](../Relatorio-de-Bugs.md#bug-049), em triagem |
| Encaminhamento | Retestar a ativação e conferir se o contador passa a dois após o sucesso do salvamento, antes de Atualizar manualmente. |
| Fonte | [Jam — PED-03 — Ativar Aniversariantes](https://jam.dev/c/60c724da-6760-4238-91f5-2ddad8f42bb3) e [evidências locais](../Evidencias/CT-RF136_Central_Ativar_Aniversariantes_Contador/README.md). |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/inteligencia-automacao |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.79 / Windows 10 (x86), conforme os metadados do Jam. |
| Tela / arquivo de vídeo | Tela 1920 × 999 informada no Jam. Vídeo em 1918 × 998. |
| Duração | 19,17 s |
| Localização | Brasil. |
| Versão / zoom / classificação do ambiente | A confirmar antes de nova execução. |
| Dados | Contador inicial em um. Aniversariantes é ativada e depois volta ao estado inativo. |

## Pré-condições

- Sessão autenticada na Central. Aniversariantes inativa e Risco de Evasão ativa na configuração de teste.
- Identificar a versão e registrar os valores iniciais e as permissões no próximo teste.

## Cenário BDD

```gherkin
Cenário: Ativar Aniversariantes e conferir a persistência e o contador
  Dado que Aniversariantes está inativa e o resumo mostra uma automação ativa
  Quando o usuário ativar Aniversariantes e aguardar o resultado do salvamento
  Então o cartão deve mostrar a automação ativa e o contador deve passar a dois
  E Atualizar deve confirmar o estado ativo e o mesmo total
```

## Passos para execução ou reteste

1. Registrar o estado de Aniversariantes e o total de automações ativas.
2. Ativar a automação. Conferir o retorno do salvamento, o cartão e o contador.
3. Acionar Atualizar e conferir a persistência na lista e no resumo.
4. Restaurar o estado inativo e registrar o contador final.

Este procedimento orienta a próxima execução. O resultado abaixo se limita ao trecho registrado no Jam.

## Resultado esperado

A ativação é refletida no cartão e no resumo após salvar. Após Atualizar, o cartão continua ativo e o total permanece em dois.

## Resultado obtido na gravação

O POST de ativação retornou sucesso e o cartão passou a indicar o estado ativo, mas o resumo ainda retornou `ativas: 1`. O contador chegou a dois quando o usuário acionou Atualizar, e a listagem confirmou Aniversariantes com `ativo: 1`. Em seguida, a desativação de restauração retornou sucesso e o contador voltou a um.

| Tempo | Registro |
| --- | --- |
| 0:00–0:04 | Aniversariantes começa inativa e o resumo mostra uma automação ativa. |
| 0:04–0:08 | Ativa Aniversariantes. O cartão fica ativo, mas o contador ainda mostra um. |
| 0:09–0:12 | Aciona Atualizar. Aniversariantes permanece ativa e o contador passa a dois. |
| 0:13–0:16 | Desativa Aniversariantes para restaurar o estado inicial. O contador volta a um. |

**Rede:**

- 0:04,54  POST `/api/automacoes/salvar/1` (HTTP 200), com `tipo: aniversario`, `ativo: 1` e `verifica_erro: false` na resposta. O GET de resumo retornou `ativas: 1`.
- 0:09,31  Atualizar. GET `/api/automacoes/1` confirmou `ativo: 1` para Aniversariantes e o GET de resumo retornou `ativas: 2` (HTTP 200).
- 0:13,29  POST de restauração com `ativo: 0` (HTTP 200, `verifica_erro: false`), seguido de resumo com `ativas: 1`.

**Conclusão:** Reprovado nas evidências. O estado ativo persistiu após Atualizar. A divergência observada ocorreu entre o cartão e o resumo depois do salvamento da ativação. A gravação não confirma a causa no servidor.

## Critérios de aceitação para nova execução

1. O cartão indica o estado ativo após o salvamento.
2. O resumo passa a duas automações ativas depois de o salvamento concluir.
3. Após Atualizar, a automação permanece ativa e o resumo mantém o mesmo total.

## Próxima ação e verificações complementares

Retestar a ativação e conferir se o contador passa a dois após o sucesso do salvamento, antes de Atualizar manualmente.

## Evidências e limites

- [Jam original — PED-03 — Ativar Aniversariantes](https://jam.dev/c/60c724da-6760-4238-91f5-2ddad8f42bb3).
- [Arquivos, origem e limites](../Evidencias/CT-RF136_Central_Ativar_Aniversariantes_Contador/README.md).
- [Aniversariantes ativa com contador ainda em uma automação](../Evidencias/CT-RF136_Central_Ativar_Aniversariantes_Contador/aniversariantes_ativa_contador_um_00-07.jpg), [Aniversariantes ativa e contador em dois após Atualizar](../Evidencias/CT-RF136_Central_Ativar_Aniversariantes_Contador/aniversariantes_apos_atualizar_00-11.jpg).
- [Linha do tempo](../Evidencias/CT-RF136_Central_Ativar_Aniversariantes_Contador/linha_do_tempo.txt).

A revisão documental se baseia nos quadros do vídeo e nos eventos capturados pelo Jam. As verificações complementares ficam para uma nova rodada de testes.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf110) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
