# 🧪 Cenário 152: Alterar o tipo de avaliação para Bioimpedância

**Caso de teste:** CT-RF152

**Módulo:** Configurações / Avaliação

**Status:** Aprovado conforme a gravação.

**Gravação:** 16/11/2026, 23:11:02 BRT. **Revisão documental:** 18/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Confirmar que o valor Bioimpedância de Tipo de avaliação permanece salvo após recarregar e reabrir Avaliação. |
| Requisito | [RF152](../Analise%20de%20requisitos.md#rf152) — referência de QA. |
| Tipo / prioridade | Funcional manual / persistência e interface · Média, proposta para triagem. |
| Defeito | Nenhum no fluxo avaliado |
| Encaminhamento | Usar como regressão da configuração e validar os campos do cadastro ao escolher cada tipo. |
| Fonte | Jam 2 — Alteração do tipo para Bioimpedância (gravação restrita por conter dados de integração) e [evidências locais](../Evidencias/CT-RF152_Configuracoes_Avaliacao_Tipo_Bioimpedancia/README.md). |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/configuracoes |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.79 / Windows 10 (x86), conforme os metadados do Jam. |
| Tela / arquivo de vídeo | Tela 1707 × 888 informada no Jam. Vídeo em 1918 × 998. |
| Duração | 18,94 s |
| Localização | Brasil. |
| Versão / zoom / classificação do ambiente | A confirmar antes de nova execução. |
| Dados | Valor inicial Dobras. Alteração para Bioimpedância, com envio de restauração para Dobras ao final. |

## Pré-condições

- Sessão autenticada com permissão para editar Configurações → Avaliação. Registrar o valor inicial com a base de teste.
- Identificar a versão e registrar os valores iniciais e as permissões no próximo teste.

## Cenário BDD

```gherkin
Cenário: Alterar o tipo de avaliação para Bioimpedância
  Dado que o seletor Tipo de avaliação está em Dobras
  Quando o usuário seleciona Bioimpedância, salva e recarrega a página
  Então a consulta deve devolver o valor salvo
  E o seletor deve exibir Bioimpedância ao reabrir Avaliação
```

## Passos para execução ou reteste

1. Abrir Configurações → Avaliação e registrar Dobras como valor inicial.
2. Selecionar Bioimpedância em Tipo de avaliação e salvar.
3. Recarregar e reabrir Avaliação para comparar a interface com a consulta.
4. Restaurar Dobras, salvar e consultar novamente em uma execução completa.

Este procedimento orienta a próxima execução. O resultado abaixo se limita ao trecho registrado no Jam.

## Resultado esperado

Salvar Bioimpedância retorna sucesso. A consulta posterior devolve `tipo_avaliacao: BIOIMPEDANCIA` e Avaliação mantém Bioimpedância no seletor. O cartão Avaliação reflete o mesmo tipo.

## Resultado obtido na gravação

O salvamento de Bioimpedância retornou HTTP 200 com `verifica_erro: false`. Após recarregar, a consulta devolveu `tipo_avaliacao: BIOIMPEDANCIA` e o seletor mostrou Bioimpedância. O cartão de resumo Avaliação também exibiu Bioimpedância. O POST de restauração para Dobras retornou sucesso.

| Tempo | Registro |
| --- | --- |
| 0:05,78 | Salva o novo valor Bioimpedância. |
| 0:08,21 | Após recarregar, o GET devolve `tipo_avaliacao: BIOIMPEDANCIA`. |
| 0:10,63 | Reabre Avaliação e confirma Bioimpedância na interface. |
| 0:17,35 | Envia a restauração para Dobras e recebe sucesso. |

**Rede:**

- 0:05,78  POST `/api/configuracoes/alterar/1` com `tipo_avaliacao: BIOIMPEDANCIA` (HTTP 200, `verifica_erro: false`).
- 0:08,21  GET `/api/configuracoes/1` (HTTP 200) com `tipo_avaliacao: BIOIMPEDANCIA`.
- 0:17,35  POST de restauração com `tipo_avaliacao: DOBRAS` (HTTP 200, `verifica_erro: false`). A captura termina sem novo GET após a restauração.

**Conclusão:** Aprovado conforme a gravação. O tipo foi conferido no formulário e no cartão de resumo de Configurações. A gravação não cobre a criação de uma avaliação nesse tipo.

## Critérios de aceitação para nova execução

1. O salvamento de Bioimpedância retorna sucesso.
2. O GET após recarregar devolve `tipo_avaliacao: BIOIMPEDANCIA`.
3. Bioimpedância aparece no campo Tipo de avaliação e no cartão de resumo Avaliação.

## Próxima ação e verificações complementares

Usar como regressão da configuração e validar os campos do cadastro ao escolher cada tipo.

## Evidências e limites

- Jam 2 — Alteração do tipo para Bioimpedância (gravação restrita por conter dados de integração).
- [Arquivos, origem e limites](../Evidencias/CT-RF152_Configuracoes_Avaliacao_Tipo_Bioimpedancia/README.md).
- [Tipo Dobras no formulário e no cartão de resumo antes da alteração](../Evidencias/CT-RF152_Configuracoes_Avaliacao_Tipo_Bioimpedancia/tipo_dobras_00-01.jpg), [Bioimpedância no formulário e no cartão após reabrir Avaliação](../Evidencias/CT-RF152_Configuracoes_Avaliacao_Tipo_Bioimpedancia/tipo_bioimpedancia_00-12.jpg).
- [Linha do tempo](../Evidencias/CT-RF152_Configuracoes_Avaliacao_Tipo_Bioimpedancia/linha_do_tempo.txt).

A revisão documental se baseia nos quadros do vídeo e nos eventos capturados pelo Jam. As verificações complementares ficam para uma nova rodada de testes.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf152) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
