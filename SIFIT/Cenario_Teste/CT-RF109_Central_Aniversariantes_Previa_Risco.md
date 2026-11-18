# 🧪 Cenário 109: Abrir Aniversariantes e conferir a prévia da automação

**Caso de teste:** CT-RF109

**Módulo:** Inteligência e Automação / Central / Aniversariantes

**Status:** Reprovado nas evidências.

**Gravação:** 16/11/2026, 21:41:32 BRT. **Revisão documental:** 17/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Abrir a configuração de Aniversariantes e apresentar uma prévia coerente com a automação selecionada. |
| Requisito | [RF109](../Analise%20de%20requisitos.md#rf109) — referência de QA. |
| Tipo / prioridade | Funcional manual / conteúdo da configuração · Média, proposta para triagem. |
| Defeito | [BUG-048](../Relatorio-de-Bugs.md#bug-048), em triagem |
| Encaminhamento | Corrigir o conteúdo da prévia e retestar separadamente Aniversariantes e Risco de Evasão. |
| Fonte | [Jam — PED-07 — Configuração de Aniversariantes](https://jam.dev/c/c66d4d01-aee2-4037-a8fd-858da21a0a14) e [evidências locais](../Evidencias/CT-RF129_Central_Aniversariantes_Previa_Risco/README.md). |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/inteligencia-automacao |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.79 / Windows 10 (x86), conforme os metadados do Jam. |
| Tela / arquivo de vídeo | Tela 1536 × 799 informada no Jam. Vídeo em 1918 × 998. |
| Duração | 20,88 s |
| Localização | Brasil. |
| Versão / zoom / classificação do ambiente | A confirmar antes de nova execução. |
| Dados | Cartão Aniversariantes inativo, com frequência diária e canal WhatsApp. |

## Pré-condições

- Sessão autenticada com acesso à Central de Automações e cartão Aniversariantes disponível.
- Identificar a versão e registrar os valores iniciais e as permissões no próximo teste.

## Cenário BDD

```gherkin
Cenário: Abrir Aniversariantes e conferir a prévia da automação
  Dado que o cartão Aniversariantes está disponível na Central de Automações
  Quando o usuário abrir Configurar e consultar a prévia do relatório
  Então o sistema deve exibir o painel de Aniversariantes
  E a prévia deve representar o conteúdo dessa automação
```

## Passos para execução ou reteste

1. Na Central, localizar Aniversariantes e acionar Configurar.
2. Conferir o título, frequência, horário e canais exibidos.
3. Rolar até Preview do relatório e comparar o conteúdo com a automação selecionada.
4. Acionar Cancelar e conferir o retorno à Central.

Este procedimento orienta a próxima execução. O resultado abaixo se limita ao trecho registrado no Jam.

## Resultado esperado

O painel de Aniversariantes abre e a prévia apresenta conteúdo de aniversários, coerente com a automação selecionada.

## Resultado obtido na gravação

O painel abriu com o título Aniversariantes, frequência diária e horário 08:00. A prévia exibiu um relatório com 24 alunos em risco, redução de frequência, pagamentos atrasados e falta de presença recente. Cancelar fechou o painel e o cartão continuou inativo.

| Tempo | Registro |
| --- | --- |
| 0:00–0:04 | Abre Configurar no cartão Aniversariantes e confere o título. |
| 0:06–0:13 | Rola até critérios e prévia. O relatório de exemplo apresenta indicadores de risco de evasão. |
| 0:18–0:20 | Cancela e volta à Central. O cartão segue inativo. |

**Rede:**

- O Jam registrou Configurar às 0:03,41 e Cancelar às 0:18,18. Não houve requisições capturadas.

**Conclusão:** Reprovado nas evidências. A divergência foi observada na prévia do painel. O envio real, o conteúdo recebido e a persistência de alterações não foram exercitados.

## Critérios de aceitação para nova execução

1. Configurar abre o painel com o título da automação selecionada.
2. A prévia de Aniversariantes apresenta conteúdo compatível com aniversários.
3. Cancelar fecha o painel e preserva o estado do cartão.

## Próxima ação e verificações complementares

Corrigir o conteúdo da prévia e retestar separadamente Aniversariantes e Risco de Evasão.

## Evidências e limites

- [Jam original — PED-07 — Configuração de Aniversariantes](https://jam.dev/c/c66d4d01-aee2-4037-a8fd-858da21a0a14).
- [Arquivos, origem e limites](../Evidencias/CT-RF129_Central_Aniversariantes_Previa_Risco/README.md).
- [Painel aberto com o título Aniversariantes](../Evidencias/CT-RF129_Central_Aniversariantes_Previa_Risco/painel_aniversariantes_00-04.jpg), [Prévia de risco exibida no painel Aniversariantes](../Evidencias/CT-RF129_Central_Aniversariantes_Previa_Risco/previa_risco_em_aniversariantes_00-12.jpg).
- [Linha do tempo](../Evidencias/CT-RF129_Central_Aniversariantes_Previa_Risco/linha_do_tempo.txt).

A revisão documental se baseia nos quadros do vídeo e nos eventos capturados pelo Jam. As verificações complementares ficam para uma nova rodada de testes.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf109) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
