# 🧪 Cenário 110: Cancelar cadastro de modelo de ficha preenchido

**Caso de teste:** CT-RF110

**Módulo:** Treinamento / Modelos de Ficha / Cancelamento de cadastro

**Status:** Aprovado conforme a gravação.

**Gravação:** 16/11/2026, 22:20:56 BRT. **Revisão documental:** 17/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Encerrar o formulário de cadastro sem salvar os dados preenchidos. |
| Requisito | [RF110](../Analise%20de%20requisitos.md#rf110) — referência de QA. Confirmação de produto pendente. |
| Tipo / prioridade | Funcional manual / cancelamento · Média, proposta para triagem. |
| Defeito | Nenhum no fluxo avaliado |
| Encaminhamento | Usar como regressão e reabrir o formulário após o cancelamento para conferir a limpeza dos campos. |
| Fonte | [Jam — Modelos de Ficha (PED-26)](https://jam.dev/c/a2a39e11-04f4-40aa-a97e-75a57a5f1b0f) e [evidências locais](../Evidencias/CT-RF110_Cancelar_Cadastro_Modelo_Ficha/README.md). |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/fichas-treino-modelo |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.79 / Windows 10 (x86), conforme os metadados do Jam. |
| Tela / arquivo de vídeo | 1536 × 799 informados no Jam. Vídeo em 1918 × 998. |
| Duração | 20,18 s |
| Localização | Brasil. |
| Versão / zoom / classificação do ambiente | A confirmar antes de nova execução. |
| Dados | Nome PEDRO-01 e um personal selecionado. Listagem inicial com 0 registros. |

## Pré-condições

- Sessão autenticada com acesso ao cadastro e um personal disponível para seleção.
- Identificar a versão e preparar a captura da listagem, do formulário ou dos filtros e dos eventos de rede pertinentes.

## Cenário BDD

```gherkin
Cenário: Cancelar cadastro de modelo de ficha preenchido
  Dado que o formulário Novo Modelo de Ficha está preenchido
  Quando o usuário clicar em Cancelar
  Então o formulário deve fechar e retornar à listagem
  E a listagem deve preservar os registros e a contagem anteriores
```

## Passos para execução ou reteste

1. Registrar a listagem e a contagem iniciais em Modelos de Ficha.
2. Abrir Novo Modelo de Ficha, preencher o nome e selecionar um personal.
3. Clicar em Cancelar e conferir a listagem, a contagem e os eventos de rede.
4. Em execução complementar, reabrir o formulário e verificar se os campos voltaram ao estado inicial.

Este procedimento orienta a próxima execução. O resultado abaixo se limita ao trecho registrado no Jam.

## Resultado esperado

Cancelar fecha o formulário e mantém a listagem e a contagem, sem criar o modelo informado.

## Resultado obtido na gravação

O formulário continha o nome PEDRO-01 e um personal selecionado. O clique em Cancelar fechou o formulário e a tela voltou à listagem com 0 registros. A captura não registrou requisições de rede no fluxo.

| Tempo | Registro |
| --- | --- |
| 0:03–0:13 | Abre o formulário, informa PEDRO-01 e seleciona um personal. |
| 0:15 | Aciona Cancelar. |
| 0:17–0:19 | Listagem visível com 0 registros. |

**Rede:** Nenhuma requisição de rede capturada durante a gravação, incluindo o clique em Cancelar.

**Conclusão:** Aprovado conforme a gravação. O formulário não foi reaberto depois do cancelamento. A listagem inicial e a final mostram 0 registros.

## Critérios de aceitação para nova execução

1. O botão Cancelar fecha o formulário preenchido.
2. O modelo informado não é incluído na listagem e a contagem permanece igual à inicial.
3. Uma nova abertura do formulário exibe os valores iniciais.

## Próxima ação e verificações complementares

Usar como regressão e reabrir o formulário após o cancelamento para conferir a limpeza dos campos.

## Evidências e limites

- [Jam original — PED-26](https://jam.dev/c/a2a39e11-04f4-40aa-a97e-75a57a5f1b0f).
- [Arquivos, origem e limites](../Evidencias/CT-RF110_Cancelar_Cadastro_Modelo_Ficha/README.md).
- [Formulário preenchido em 0:14](../Evidencias/CT-RF110_Cancelar_Cadastro_Modelo_Ficha/formulario_preenchido_00-14.jpg), [Listagem após cancelar em 0:17](../Evidencias/CT-RF110_Cancelar_Cadastro_Modelo_Ficha/listagem_apos_cancelar_00-17.jpg).
- [Linha do tempo](../Evidencias/CT-RF110_Cancelar_Cadastro_Modelo_Ficha/linha_do_tempo.txt).

Foram consultados os metadados, os eventos de rede e de interação e os quadros do vídeo. Os recortes estão na pasta de evidências. O vídeo permanece no Jam.

A revisão documental de 17/11/2026 registra a execução gravada. As verificações complementares ficam para uma nova rodada de testes.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf110) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
