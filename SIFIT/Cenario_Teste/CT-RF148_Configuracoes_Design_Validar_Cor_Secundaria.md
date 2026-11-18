# 🧪 Cenário 148: Rejeitar código hexadecimal inválido na Cor Secundária

**Caso de teste:** CT-RF148

**Módulo:** Configurações / Design

**Status:** Reprovado nas evidências.

**Gravação:** 16/11/2026, 23:26:21 BRT. **Revisão documental:** 17/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Verificar o bloqueio de código fora do formato hexadecimal no campo Cor Secundária e a preservação da cor já salva. |
| Requisito | [RF148](../Analise%20de%20requisitos.md#rf148) — referência de QA. |
| Tipo / prioridade | Funcional manual / validação · Média, proposta para triagem. |
| Defeito | [BUG-051](../Relatorio-de-Bugs.md#bug-051), em triagem |
| Encaminhamento | Retestar com códigos hexadecimais válidos e inválidos e conferir, após cada tentativa, a cor devolvida pela consulta. |
| Fonte | Jam 4 — Validação da Cor Secundária (gravação restrita por conter dados de integração) e [evidências locais](../Evidencias/CT-RF148_Configuracoes_Design_Validar_Cor_Secundaria/README.md). |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/configuracoes |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.79 / Windows 10 (x86), conforme os metadados do Jam. |
| Tela / arquivo de vídeo | Tela 1707 × 888 informada no Jam. Vídeo em 1918 × 998. |
| Duração | 19,35 s |
| Localização | Brasil. |
| Versão / zoom / classificação do ambiente | A confirmar antes de nova execução. |
| Dados | Cor Principal #663399 e Cor Secundária inicial #000. Valor inválido usado para a Cor Secundária #ZZZZZZ. |

## Pré-condições

- Sessão autenticada em Design e uma Cor Secundária válida salva como referência.
- Identificar a versão e registrar os valores iniciais e as permissões no próximo teste.

## Cenário BDD

```gherkin
Cenário: Rejeitar código hexadecimal inválido na Cor Secundária
  Dado que Design possui uma Cor Secundária válida salva
  Quando o usuário informa #ZZZZZZ como Cor Secundária e salva
  Então o sistema deve rejeitar o código e apontar o campo a corrigir
  E a consulta deve manter a última cor válida
```

## Passos para execução ou reteste

1. Abrir Design e registrar a Cor Secundária salva.
2. Trocar a Cor Secundária para #ZZZZZZ e salvar.
3. Conferir a resposta, recarregar e reabrir Design.
4. Comparar o valor persistido com a cor válida anterior.

Este procedimento orienta a próxima execução. O resultado abaixo se limita ao trecho registrado no Jam.

## Resultado esperado

A interface ou a API rejeita o código #ZZZZZZ com uma mensagem de validação e preserva a cor válida armazenada.

## Resultado obtido na gravação

As duas tentativas retornaram HTTP 200 com `verifica_erro: false`. O GET após recarregar devolveu `cor_secundaria: #ZZZZZZ` e o campo ainda mostrou esse valor ao reabrir a aba. Não houve indicação de rejeição na gravação. Ao reabrir, a amostra da Cor Secundária ficou sem a cor preta original.

| Tempo | Registro |
| --- | --- |
| 0:00–0:07 | Edita Cor Secundária de #000 para #ZZZZZZ. |
| 0:08–0:09 | Aciona Salvar Configurações duas vezes, com retorno de sucesso. |
| 0:12–0:18 | Recarrega e reabre Design. A consulta e o campo mostram #ZZZZZZ. |

**Rede:**

- 0:08,01 e 0:09,20  POST `/api/configuracoes/alterar/1` com `cor_secundaria: #ZZZZZZ` (HTTP 200, `verifica_erro: false`).
- 0:12,33  GET `/api/configuracoes/1` (HTTP 200), com `cor_secundaria: #ZZZZZZ`.

**Conclusão:** Reprovado nas evidências. O defeito foi confirmado pela leitura posterior. O efeito do código inválido nos ambientes online não foi avaliado.

## Critérios de aceitação para nova execução

1. O valor com caracteres fora da faixa hexadecimal é rejeitado.
2. A interface identifica Cor Secundária como o campo a corrigir.
3. O valor inválido não substitui a última configuração válida.

## Próxima ação e verificações complementares

Retestar com códigos hexadecimais válidos e inválidos e conferir, após cada tentativa, a cor devolvida pela consulta.

## Evidências e limites

- Jam 4 — Validação da Cor Secundária (gravação restrita por conter dados de integração).
- [Arquivos, origem e limites](../Evidencias/CT-RF148_Configuracoes_Design_Validar_Cor_Secundaria/README.md).
- [Cor Secundária inválida durante o fluxo de salvamento](../Evidencias/CT-RF148_Configuracoes_Design_Validar_Cor_Secundaria/cor_secundaria_invalida_00-08.jpg), [Mesmo valor inválido após recarregar e reabrir a aba](../Evidencias/CT-RF148_Configuracoes_Design_Validar_Cor_Secundaria/cor_secundaria_invalida_persistida_00-16.jpg).
- [Linha do tempo](../Evidencias/CT-RF148_Configuracoes_Design_Validar_Cor_Secundaria/linha_do_tempo.txt).

A revisão documental se baseia nos quadros do vídeo e nos eventos capturados pelo Jam. As verificações complementares ficam para uma nova rodada de testes.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf148) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
