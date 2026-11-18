# 🧪 Cenário 120: Bloquear número negativo no campo de dias de ausência

**Caso de teste:** CT-RF120

**Módulo:** Configurações / Home / Dias de ausência

**Status:** Reprovado nas evidências.

**Gravação:** 16/11/2026, 22:00:22 BRT. **Revisão documental:** 17/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Impedir o salvamento de valor negativo para dias de ausência e preservar a configuração anterior, conforme o critério do RF117. |
| Requisito | [RF120](../Analise%20de%20requisitos.md#rf120) — referência de QA. |
| Tipo / prioridade | Funcional manual / validação de campo · Média, proposta para triagem. |
| Defeito | [BUG-047](../Relatorio-de-Bugs.md#bug-047), em triagem |
| Encaminhamento | Aplicar validação na gravação da configuração e retestar com -1, um inteiro válido e o limite mínimo definido pelo produto. |
| Fonte | [Jam — PED-17 — Dias de ausência negativos](https://jam.dev/c/d5786f67-6e5f-44f5-bbba-fbd763a88740) e [evidências locais](../Evidencias/CT-RF126_Configuracoes_Dias_Ausencia_Negativo/README.md). Escopo complementar ao [CT-RF117](CT-RF117_Configuracoes_Home_Salvamento.md). |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/configuracoes |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.79 / Windows 10 (x86), conforme os metadados do Jam. |
| Tela / arquivo de vídeo | Tela 1536 × 799 informada no Jam. Vídeo em 1918 × 998. |
| Duração | 25,75 s |
| Localização | Brasil. |
| Versão / zoom / classificação do ambiente | A confirmar antes de nova execução. |
| Dados | Valor inicial 1100. Entrada negativa de teste: -1. |

## Pré-condições

- Sessão autenticada com acesso a Configurações > Home e valor inicial conhecido para dias de ausência.
- Identificar a versão e registrar os valores iniciais e as permissões no próximo teste.

## Cenário BDD

```gherkin
Cenário: Bloquear número negativo no campo de dias de ausência
  Dado que o campo de dias de ausência contém um valor salvo
  Quando o usuário informar -1 e tentar salvar
  Então a aplicação deve rejeitar o valor negativo e indicar o campo inválido
  E a configuração anterior deve permanecer após recarregar a tela
```

## Passos para execução ou reteste

1. Abrir Configurações > Home e registrar o valor original.
2. Preencher o campo com -1 e clicar em Salvar Configurações.
3. Conferir o feedback, a resposta e o valor após recarregar.
4. Restaurar o valor inicial no ambiente de teste se a aplicação tiver aceitado o negativo.

Este procedimento orienta a próxima execução. O resultado abaixo se limita ao trecho registrado no Jam.

## Resultado esperado

O sistema rejeita valores negativos, orienta a correção do campo e preserva o valor anterior após recarga.

## Resultado obtido na gravação

O POST com `dias_ausente=-1` retornou HTTP 200 com `verifica_erro: false`. Após recarregar, o campo exibiu -1 e o GET confirmou `dias_ausente: -1`. No fim, 1100 foi reenviado com HTTP 200.

| Tempo | Registro |
| --- | --- |
| 0:00–0:06 | Substitui 1100 por -1. |
| 0:06–0:07 | Salva a configuração. O retorno indica sucesso. |
| 0:09–0:13 | Recarrega. O campo permanece em -1. |
| 0:20–0:24 | Volta a informar 1100 e salva novamente. |

**Rede:**

- 0:06,91  POST `/api/configuracoes/alterar/1` (HTTP 200), com `dias_ausente=-1` e `verifica_erro: false`.
- 0:10,44  GET `/api/configuracoes/1` (HTTP 200), com `dias_ausente: -1`.
- 0:23,65  POST (HTTP 200), com `dias_ausente=1100`. O vídeo termina antes de nova consulta para confirmar a restauração.

**Conclusão:** Reprovado nas evidências. A evidência confirma a persistência de -1. O efeito sobre a classificação de clientes ausentes e a abrangência para outros negativos não foram exercitados.

## Critérios de aceitação para nova execução

1. O formulário ou a API bloqueia o salvamento de valor negativo.
2. A interface indica como corrigir a entrada inválida.
3. A recarga preserva o último valor válido.

## Próxima ação e verificações complementares

Aplicar validação na gravação da configuração e retestar com -1, um inteiro válido e o limite mínimo definido pelo produto.

## Evidências e limites

- [Jam original — PED-17 — Dias de ausência negativos](https://jam.dev/c/d5786f67-6e5f-44f5-bbba-fbd763a88740).
- [Arquivos, origem e limites](../Evidencias/CT-RF126_Configuracoes_Dias_Ausencia_Negativo/README.md).
- [Valor -1 antes de salvar](../Evidencias/CT-RF126_Configuracoes_Dias_Ausencia_Negativo/dias_negativo_antes_00-06.jpg), [Valor -1 após recarregar](../Evidencias/CT-RF126_Configuracoes_Dias_Ausencia_Negativo/dias_negativo_recarga_00-13.jpg).
- [Linha do tempo](../Evidencias/CT-RF126_Configuracoes_Dias_Ausencia_Negativo/linha_do_tempo.txt).

A revisão documental se baseia nos quadros do vídeo e nos eventos capturados pelo Jam. As verificações complementares ficam para uma nova rodada de testes.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf120) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
