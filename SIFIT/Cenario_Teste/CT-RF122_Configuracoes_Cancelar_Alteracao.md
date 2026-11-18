# 🧪 Cenário 122: Cancelar uma alteração nas Configurações sem salvar

**Caso de teste:** CT-RF122

**Módulo:** Configurações / Home / Cancelamento

**Status:** Aprovado conforme a gravação.

**Gravação:** 16/11/2026, 22:05:00 BRT. **Revisão documental:** 17/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Descartar uma alteração feita no formulário de Configurações ao acionar Cancelar e preservar o valor salvo. |
| Requisito | [RF122](../Analise%20de%20requisitos.md#rf122) — referência de QA. |
| Tipo / prioridade | Funcional manual / cancelamento · Média, proposta para triagem. |
| Defeito | Nenhum no fluxo avaliado |
| Encaminhamento | Usar como regressão e repetir com múltiplos campos alterados na mesma aba. |
| Fonte | [Jam — PED-20 — Cancelar alteração](https://jam.dev/c/e8faa199-1177-4563-8b00-590606669a1d) e [evidências locais](../Evidencias/CT-RF117_Configuracoes_Cancelar_Alteracao/README.md). |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/configuracoes |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.79 / Windows 10 (x86), conforme os metadados do Jam. |
| Tela / arquivo de vídeo | Tela 1536 × 799 informada no Jam. Vídeo em 1918 × 998. |
| Duração | 20,02 s |
| Localização | Brasil. |
| Versão / zoom / classificação do ambiente | A confirmar antes de nova execução. |
| Dados | Campo Dias para contar cliente como ausente com 1100 antes da edição e 15 antes de Cancelar. |

## Pré-condições

- Sessão autenticada em Configurações > Home com um valor de dias de ausência já salvo.
- Identificar a versão e registrar os valores iniciais e as permissões no próximo teste.

## Cenário BDD

```gherkin
Cenário: Cancelar uma alteração nas Configurações sem salvar
  Dado que a aba Home de Configurações apresenta um valor salvo para dias de ausência
  Quando o usuário editar o campo e clicar em Cancelar
  Então o sistema deve sair da edição sem salvar a mudança
  E ao reabrir Configurações, o campo deve exibir o valor anterior
```

## Passos para execução ou reteste

1. Abrir Configurações > Home e anotar o valor salvo de dias de ausência.
2. Digitar um valor diferente e clicar em Cancelar.
3. Verificar a navegação para a Página Inicial e reabrir Configurações.
4. Conferir o campo e verificar se houve uma requisição de alteração.

Este procedimento orienta a próxima execução. O resultado abaixo se limita ao trecho registrado no Jam.

## Resultado esperado

Cancelar leva à Página Inicial e descarta a edição. Ao voltar a Configurações, o valor salvo permanece.

## Resultado obtido na gravação

O valor 1100 foi editado para 15. Cancelar levou à Página Inicial. Após voltar a Configurações, o campo mostrou 1100 e o GET retornou `dias_ausente: 1100`. A gravação não contém chamada a `/api/configuracoes/alterar/1`.

| Tempo | Registro |
| --- | --- |
| 0:01–0:07 | O campo inicialmente em 1100 é alterado para 15. |
| 0:08–0:10 | Clica em Cancelar e chega à Página Inicial. |
| 0:13–0:16 | Volta a Configurações. O formulário volta a exibir 1100. |

**Rede:**

- 0:08,37  Clique em Cancelar. Os eventos seguintes são de navegação e carga da Página Inicial.
- 0:14,14  GET `/api/configuracoes/1` (HTTP 200), com `dias_ausente: 1100`. Nenhum POST de alteração de Configurações no trecho.

**Conclusão:** Aprovado conforme a gravação. O cancelamento foi verificado para uma alteração no campo de dias de ausência na aba Home. Alterações simultâneas e as demais abas ficam para nova execução.

## Critérios de aceitação para nova execução

1. Cancelar encerra a edição e retorna à Página Inicial.
2. O valor temporário não é gravado.
3. A consulta e a interface apresentam o valor original ao reabrir.

## Próxima ação e verificações complementares

Usar como regressão e repetir com múltiplos campos alterados na mesma aba.

## Evidências e limites

- [Jam original — PED-20 — Cancelar alteração](https://jam.dev/c/e8faa199-1177-4563-8b00-590606669a1d).
- [Arquivos, origem e limites](../Evidencias/CT-RF117_Configuracoes_Cancelar_Alteracao/README.md).
- [Valor 15 no formulário antes de cancelar](../Evidencias/CT-RF117_Configuracoes_Cancelar_Alteracao/dias_editados_00-07.jpg), [Valor 1100 após voltar a Configurações](../Evidencias/CT-RF117_Configuracoes_Cancelar_Alteracao/dias_apos_cancelar_00-16.jpg).
- [Linha do tempo](../Evidencias/CT-RF117_Configuracoes_Cancelar_Alteracao/linha_do_tempo.txt).

A revisão documental se baseia nos quadros do vídeo e nos eventos capturados pelo Jam. As verificações complementares ficam para uma nova rodada de testes.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf122) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
