# 🧪 Cenário 165: Validar dias negativos para travar a catraca

**Caso de teste:** CT-RF165

**Módulo:** Configurações / Biometria

**Status:** Reprovado nas evidências.

**Gravação:** 16/11/2026, 23:07:08 BRT. **Revisão documental:** 18/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Recusar um número negativo em Travar Catraca Após (dias) ou explicar a correção aplicada antes de confirmar o salvamento. |
| Requisito | [RF165](../Analise%20de%20requisitos.md#rf165) — referência de QA. |
| Tipo / prioridade | Funcional manual / validação e feedback · Baixa, proposta para triagem. |
| Defeito | [BUG-054](../Relatorio-de-Bugs.md#bug-054), em triagem |
| Encaminhamento | Confirmar a regra de validação do produto e retestar -1, 0 e um número positivo com conferência da resposta e da mensagem da interface. |
| Fonte | [Jam 9 — Validação de dias de bloqueio da catraca](https://jam.dev/c/f607bc49-184f-4d55-81ab-7db825af6021) e [evidências locais](../Evidencias/CT-RF165_Configuracoes_Biometria_Validar_Dias_Bloqueio/README.md). |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/configuracoes |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.79 / Windows 10 (x86), conforme os metadados do Jam. |
| Tela / arquivo de vídeo | Tela 1707 × 888 informada no Jam. Vídeo em 1918 × 998. |
| Duração | 15,68 s |
| Localização | Brasil. |
| Versão / zoom / classificação do ambiente | A confirmar antes de nova execução. |
| Dados | Valor de referência 0. Entrada negativa de teste -1. |

## Pré-condições

- Sessão autenticada em Biometria com permissão para editar dias de bloqueio no ambiente de teste.
- Identificar a versão e registrar os valores iniciais e as permissões no próximo teste.

## Cenário BDD

```gherkin
Cenário: Validar dias negativos para travar a catraca
  Dado que o campo Travar Catraca Após (dias) está em zero
  Quando o usuário informa -1 e aciona Salvar Configurações
  Então o sistema deve orientar a correção da entrada negativa
  E uma nova leitura deve preservar um valor válido
```

## Passos para execução ou reteste

1. Verificar o valor inicial de Travar Catraca Após (dias).
2. Informar -1 e acionar Salvar Configurações.
3. Conferir se a tela informa a recusa ou a correção aplicada.
4. Recarregar a aba e comparar o valor apresentado com a resposta de consulta.

Este procedimento orienta a próxima execução. O resultado abaixo se limita ao trecho registrado no Jam.

## Resultado esperado

A interface recusa a entrada negativa com mensagem de validação ou, conforme a regra do produto, informa o valor válido que foi aplicado.

## Resultado obtido na gravação

O POST enviou `dias_bloqueio: -1` e retornou HTTP 200 com `verifica_erro: false`. Depois de recarregar, o GET e o campo mostraram 0. A captura não registrou uma orientação específica sobre a entrada negativa.

| Tempo | Registro |
| --- | --- |
| 0:01–0:04 | Preenche -1 em Travar Catraca Após (dias) e salva. |
| 0:04,24 | O POST retorna sucesso com a entrada -1. |
| 0:07,46–0:12 | Após recarregar e abrir Biometria, a consulta e o campo mostram zero. |

**Rede:**

- 0:04,24  POST `/api/configuracoes/alterar/1` com `dias_bloqueio: -1` (HTTP 200, `verifica_erro: false`).
- 0:07,46  GET `/api/configuracoes/1` (HTTP 200), com `dias_bloqueio: 0`.

**Conclusão:** Reprovado nas evidências. A consulta devolveu 0. A gravação não determina se esse valor resultou de normalização ou se o sistema preservou o valor anterior.

## Critérios de aceitação para nova execução

1. O formulário orienta a correção da entrada negativa.
2. O retorno distingue um valor recusado ou ajustado de um valor aceito conforme informado.
3. A leitura posterior mantém um valor válido.

## Próxima ação e verificações complementares

Confirmar a regra de validação do produto e retestar -1, 0 e um número positivo com conferência da resposta e da mensagem da interface.

## Evidências e limites

- [Jam 9 — Validação de dias de bloqueio da catraca](https://jam.dev/c/f607bc49-184f-4d55-81ab-7db825af6021).
- [Arquivos, origem e limites](../Evidencias/CT-RF165_Configuracoes_Biometria_Validar_Dias_Bloqueio/README.md).
- [Travar Catraca Após (dias) em -1 antes de salvar](../Evidencias/CT-RF165_Configuracoes_Biometria_Validar_Dias_Bloqueio/dias_bloqueio_negativo_00-04.jpg), [Campo exibe 0 após recarregar e retornar a Biometria](../Evidencias/CT-RF165_Configuracoes_Biometria_Validar_Dias_Bloqueio/dias_bloqueio_zero_apos_recarregar_00-12.jpg).
- [Linha do tempo](../Evidencias/CT-RF165_Configuracoes_Biometria_Validar_Dias_Bloqueio/linha_do_tempo.txt).

A revisão documental se baseia nos quadros do vídeo e nos eventos capturados pelo Jam. As verificações complementares ficam para uma nova rodada de testes.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf165) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
