# 🧪 Cenário 128: Abrir e fechar a configuração de Risco de Evasão

**Caso de teste:** CT-RF128

**Módulo:** Inteligência e Automação / Central / Risco de Evasão

**Status:** Aprovado conforme a gravação.

**Gravação:** 16/11/2026, 21:40:31 BRT. **Revisão documental:** 17/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Abrir o painel correto de Risco de Evasão, consultar as opções e fechá-lo sem gravar uma alteração. |
| Requisito | [RF128](../Analise%20de%20requisitos.md#rf128) — referência de QA. |
| Tipo / prioridade | Funcional manual / abertura e cancelamento · Média, proposta para triagem. |
| Defeito | Nenhum no fluxo avaliado |
| Encaminhamento | Usar como regressão de abertura e fechamento. Em um caso complementar, alterar uma opção de teste e conferir o descarte após cancelar. |
| Fonte | [Jam — PED-06 — Configuração de Risco de Evasão](https://jam.dev/c/d49b8ffc-a6e2-4e37-a618-c280b5e807db) e [evidências locais](../Evidencias/CT-RF128_Central_Configuracao_Risco_Evasao_Cancelar/README.md). |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/inteligencia-automacao |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.79 / Windows 10 (x86), conforme os metadados do Jam. |
| Tela / arquivo de vídeo | Tela 1536 × 799 informada no Jam. Vídeo em 1918 × 998. |
| Duração | 19,66 s |
| Localização | Brasil. |
| Versão / zoom / classificação do ambiente | A confirmar antes de nova execução. |
| Dados | A automação estava ativa, com frequência diária e canais WhatsApp + Painel no cartão inicial. |

## Pré-condições

- Sessão autenticada com acesso à Central de Automações e cartão Risco de Evasão disponível.
- Identificar a versão e registrar os valores iniciais e as permissões no próximo teste.

## Cenário BDD

```gherkin
Cenário: Abrir e fechar a configuração de Risco de Evasão
  Dado que a Central de Automações exibe o cartão Risco de Evasão
  Quando o usuário clicar em Configurar e depois em Cancelar
  Então o sistema deve abrir o painel de Risco de Evasão e permitir consultar suas opções
  E Cancelar deve fechar o painel e retornar à Central com o estado anterior
```

## Passos para execução ou reteste

1. Abrir a Central de Automações e conferir o estado do cartão Risco de Evasão.
2. Clicar em Configurar e conferir o título, a frequência, os canais e a prévia.
3. Rolar o painel e acionar Cancelar.
4. Conferir o fechamento e comparar o estado do cartão com o inicial.

Este procedimento orienta a próxima execução. O resultado abaixo se limita ao trecho registrado no Jam.

## Resultado esperado

Configurar abre o painel correto. Cancelar fecha a configuração e preserva o estado da automação.

## Resultado obtido na gravação

Abriu o painel Risco de Evasão com frequência, canais, destinatários, critérios, sensibilidade e prévia do relatório. Após Cancelar, voltou à Central, com o cartão ainda ativo. Nenhuma requisição de rede foi capturada.

| Tempo | Registro |
| --- | --- |
| 0:00–0:03 | Confere o cartão ativo e abre Configurar. |
| 0:04–0:14 | Consulta os grupos de opções e a prévia do relatório. |
| 0:15–0:17 | Aciona Cancelar. O painel fecha e o cartão continua ativo. |

**Rede:**

- O Jam registrou os cliques em Configurar (0:02,56) e Cancelar (0:15,25). Não houve eventos de rede capturados no trecho.

**Conclusão:** Aprovado conforme a gravação. A gravação percorre o painel sem editar opções. O descarte de valores alterados, o salvamento e a execução da automação ficaram fora deste cenário.

## Critérios de aceitação para nova execução

1. O botão Configurar abre Risco de Evasão.
2. As opções e a prévia estão acessíveis no painel.
3. Cancelar retorna à Central e preserva o estado exibido no cartão.

## Próxima ação e verificações complementares

Usar como regressão de abertura e fechamento. Em um caso complementar, alterar uma opção de teste e conferir o descarte após cancelar.

## Evidências e limites

- [Jam original — PED-06 — Configuração de Risco de Evasão](https://jam.dev/c/d49b8ffc-a6e2-4e37-a618-c280b5e807db).
- [Arquivos, origem e limites](../Evidencias/CT-RF128_Central_Configuracao_Risco_Evasao_Cancelar/README.md).
- [Painel de Risco de Evasão com as configurações iniciais](../Evidencias/CT-RF128_Central_Configuracao_Risco_Evasao_Cancelar/painel_evasao_00-04.jpg), [Central após cancelar, com Risco de Evasão ainda ativa](../Evidencias/CT-RF128_Central_Configuracao_Risco_Evasao_Cancelar/central_apos_cancelar_00-17.jpg).
- [Linha do tempo](../Evidencias/CT-RF128_Central_Configuracao_Risco_Evasao_Cancelar/linha_do_tempo.txt).

A revisão documental se baseia nos quadros do vídeo e nos eventos capturados pelo Jam. As verificações complementares ficam para uma nova rodada de testes.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf128) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
