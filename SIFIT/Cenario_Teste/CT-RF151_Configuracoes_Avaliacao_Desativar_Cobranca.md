# 🧪 Cenário 151: Desativar a cobrança da avaliação do cliente

**Caso de teste:** CT-RF151

**Módulo:** Configurações / Avaliação

**Status:** Aprovado conforme a gravação.

**Gravação:** 16/11/2026, 23:10:04 BRT. **Revisão documental:** 18/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Confirmar que o valor Não de Cobrar Avaliação do Cliente permanece salvo após recarregar e reabrir Avaliação. |
| Requisito | [RF151](../Analise%20de%20requisitos.md#rf151) — referência de QA. |
| Tipo / prioridade | Funcional manual / persistência · Média, proposta para triagem. |
| Defeito | Nenhum no fluxo avaliado |
| Encaminhamento | Usar como regressão da preferência e confirmar a regra de cobrança em um fluxo de avaliação de teste. |
| Fonte | Jam 1 — Desativação da cobrança da avaliação (gravação restrita por conter dados de integração) e [evidências locais](../Evidencias/CT-RF151_Configuracoes_Avaliacao_Desativar_Cobranca/README.md). |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/configuracoes |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.79 / Windows 10 (x86), conforme os metadados do Jam. |
| Tela / arquivo de vídeo | Tela 1707 × 888 informada no Jam. Vídeo em 1918 × 998. |
| Duração | 18,34 s |
| Localização | Brasil. |
| Versão / zoom / classificação do ambiente | A confirmar antes de nova execução. |
| Dados | Valor inicial Sim. Alteração para Não, com envio de restauração para Sim ao final. |

## Pré-condições

- Sessão autenticada com permissão para editar Configurações → Avaliação. Registrar o valor inicial com a base de teste.
- Identificar a versão e registrar os valores iniciais e as permissões no próximo teste.

## Cenário BDD

```gherkin
Cenário: Desativar a cobrança da avaliação do cliente
  Dado que a opção “Cobrar Avaliação do Cliente?” está em Sim
  Quando o usuário seleciona Não, salva e recarrega a página
  Então a consulta deve devolver o valor salvo
  E o seletor deve exibir Não ao reabrir Avaliação
```

## Passos para execução ou reteste

1. Abrir Configurações → Avaliação e registrar Sim como valor inicial.
2. Selecionar Não em “Cobrar Avaliação do Cliente?” e salvar.
3. Recarregar e reabrir Avaliação para comparar a interface com a consulta.
4. Restaurar Sim, salvar e consultar novamente em uma execução completa.

Este procedimento orienta a próxima execução. O resultado abaixo se limita ao trecho registrado no Jam.

## Resultado esperado

Salvar Não retorna sucesso. A consulta posterior devolve `cobrar_avaliacao: nao` e Avaliação mantém Não no seletor.

## Resultado obtido na gravação

O salvamento de Não retornou HTTP 200 com `verifica_erro: false`. Após recarregar, a consulta devolveu `cobrar_avaliacao: nao` e o seletor mostrou Não. O POST de restauração para Sim retornou sucesso.

| Tempo | Registro |
| --- | --- |
| 0:05,77 | Salva o novo valor Não. |
| 0:08,78 | Após recarregar, o GET devolve `cobrar_avaliacao: nao`. |
| 0:10,14 | Reabre Avaliação e confirma Não na interface. |
| 0:16,63 | Envia a restauração para Sim e recebe sucesso. |

**Rede:**

- 0:05,77  POST `/api/configuracoes/alterar/1` com `cobrar_avaliacao: nao` (HTTP 200, `verifica_erro: false`).
- 0:08,78  GET `/api/configuracoes/1` (HTTP 200) com `cobrar_avaliacao: nao`.
- 0:16,63  POST de restauração com `cobrar_avaliacao: sim` (HTTP 200, `verifica_erro: false`). A captura termina sem novo GET após a restauração.

**Conclusão:** Aprovado conforme a gravação. A evidência cobre a preferência salva. A geração de cobranças e o reflexo no cadastro de avaliação ficam para nova execução.

## Critérios de aceitação para nova execução

1. O salvamento de Não retorna sucesso.
2. O GET após recarregar devolve `cobrar_avaliacao: nao`.
3. O seletor mantém Não após reabrir a aba.

## Próxima ação e verificações complementares

Usar como regressão da preferência e confirmar a regra de cobrança em um fluxo de avaliação de teste.

## Evidências e limites

- Jam 1 — Desativação da cobrança da avaliação (gravação restrita por conter dados de integração).
- [Arquivos, origem e limites](../Evidencias/CT-RF151_Configuracoes_Avaliacao_Desativar_Cobranca/README.md).
- [Cobrar Avaliação do Cliente em Sim antes da alteração](../Evidencias/CT-RF151_Configuracoes_Avaliacao_Desativar_Cobranca/cobrar_avaliacao_sim_00-01.jpg), [Cobrar Avaliação do Cliente em Não após reabrir a aba](../Evidencias/CT-RF151_Configuracoes_Avaliacao_Desativar_Cobranca/cobrar_avaliacao_nao_00-12.jpg).
- [Linha do tempo](../Evidencias/CT-RF151_Configuracoes_Avaliacao_Desativar_Cobranca/linha_do_tempo.txt).

A revisão documental se baseia nos quadros do vídeo e nos eventos capturados pelo Jam. As verificações complementares ficam para uma nova rodada de testes.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf151) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
