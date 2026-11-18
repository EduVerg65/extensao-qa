# 🧪 Cenário 118: Validar o salvamento com o campo de dias de ausência vazio

**Caso de teste:** CT-RF118

**Módulo:** Configurações / Home / Dias de ausência

**Status:** A validar — regra ou contexto pendente.

**Gravação:** 16/11/2026, 22:03:53 BRT. **Revisão documental:** 17/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Tratar explicitamente o campo Dias para contar cliente como ausente quando ele é enviado vazio, conforme a regra de obrigatoriedade e de valor padrão. |
| Requisito | [RF118](../Analise%20de%20requisitos.md#rf118) — referência de QA. |
| Tipo / prioridade | Exploratório / validação de campo · Média, proposta para triagem. |
| Defeito | Sem defeito confirmado |
| Encaminhamento | Confirmar com o produto a regra para vazio e zero. Repetir com vazio, zero explícito e os limites da faixa. |
| Fonte | [Jam — PED-20 — Dias de ausência vazio](https://jam.dev/c/4e96d4fa-65b5-459b-a795-854496e5753c) e [evidências locais](../Evidencias/CT-RF116_Configuracoes_Dias_Ausencia_Vazio/README.md). Escopo complementar ao [CT-RF117](CT-RF117_Configuracoes_Home_Salvamento.md). |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/configuracoes |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.79 / Windows 10 (x86), conforme os metadados do Jam. |
| Tela / arquivo de vídeo | Tela 1536 × 799 informada no Jam. Vídeo em 1918 × 998. |
| Duração | 21,47 s |
| Localização | Brasil. |
| Versão / zoom / classificação do ambiente | A confirmar antes de nova execução. |
| Dados | Valor inicial 1100. Campo esvaziado para o primeiro salvamento e preenchido novamente com 1100 no fim. |

## Pré-condições

- Sessão autenticada com permissão para alterar Configurações e um valor inicial conhecido para dias de ausência.
- Identificar a versão e registrar os valores iniciais e as permissões no próximo teste.

## Cenário BDD

```gherkin
Cenário: Validar o salvamento com o campo de dias de ausência vazio
  Dado que há um número de dias de ausência salvo
  Quando o usuário apagar o valor e acionar Salvar Configurações
  Então o sistema deve aplicar a regra do campo vazio e informar o resultado ao usuário
  E uma recarga deve apresentar o valor salvo conforme essa regra
```

## Passos para execução ou reteste

1. Abrir Configurações > Home e registrar o valor inicial do campo de dias.
2. Apagar todo o conteúdo e clicar em Salvar Configurações.
3. Registrar o feedback, o valor enviado e o valor exibido após recarregar.
4. Recolocar o valor inicial após a verificação, se necessário.

Este procedimento orienta a próxima execução. O resultado abaixo se limita ao trecho registrado no Jam.

## Resultado esperado

Se o campo for obrigatório, o sistema impede o salvamento e preserva o valor anterior. Se o campo for opcional, aplica o padrão definido e informa como tratou a entrada vazia.

## Resultado obtido na gravação

Com o campo vazio, Salvar Configurações enviou `dias_ausente=0` e recebeu HTTP 200 com `verifica_erro: false`. A recarga exibiu 0 e o GET confirmou `dias_ausente: 0`. No fim, foi reenviado 1100 com HTTP 200.

| Tempo | Registro |
| --- | --- |
| 0:00–0:06 | Campo inicia em 1100 e é esvaziado. |
| 0:07 | Clique em Salvar Configurações com o campo vazio. A interface exibe o estado de salvamento. |
| 0:10–0:13 | A página é recarregada e o valor 0 aparece no formulário e na rede. |
| 0:17–0:19 | O valor 1100 é informado e enviado para restaurar a configuração. |

**Rede:**

- 0:07,42  POST `/api/configuracoes/alterar/1` (HTTP 200), com `dias_ausente=0` e `verifica_erro: false` na resposta.
- 0:11,16  GET `/api/configuracoes/1` (HTTP 200), com `dias_ausente: 0`.
- 0:19,15  Segundo POST (HTTP 200), com `dias_ausente=1100`. A gravação termina sem nova leitura desse valor.

**Conclusão:** A validar — regra ou contexto pendente. A conversão de vazio para zero e a persistência estão confirmadas. A obrigatoriedade do campo, o significado de zero e o efeito sobre a contagem de clientes ausentes dependem da regra de produto. O CT-RF117 já registra a necessidade de confirmar a faixa.

## Critérios de aceitação para nova execução

1. O sistema aplica a regra acordada para o campo vazio e comunica o resultado.
2. O valor retornado após recarga corresponde ao tratamento definido.
3. Zero explícito e campo vazio são verificados separadamente.

## Próxima ação e verificações complementares

Confirmar com o produto a regra para vazio e zero. Repetir com vazio, zero explícito e os limites da faixa.

## Evidências e limites

- [Jam original — PED-20 — Dias de ausência vazio](https://jam.dev/c/4e96d4fa-65b5-459b-a795-854496e5753c).
- [Arquivos, origem e limites](../Evidencias/CT-RF116_Configuracoes_Dias_Ausencia_Vazio/README.md).
- [Campo de dias vazio antes do salvamento](../Evidencias/CT-RF116_Configuracoes_Dias_Ausencia_Vazio/dias_vazio_00-07.jpg), [Estado do campo de dias após a recarga](../Evidencias/CT-RF116_Configuracoes_Dias_Ausencia_Vazio/dias_apos_recarga_00-13.jpg).
- [Linha do tempo](../Evidencias/CT-RF116_Configuracoes_Dias_Ausencia_Vazio/linha_do_tempo.txt).

A revisão documental se baseia nos quadros do vídeo e nos eventos capturados pelo Jam. As verificações complementares ficam para uma nova rodada de testes.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf118) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
