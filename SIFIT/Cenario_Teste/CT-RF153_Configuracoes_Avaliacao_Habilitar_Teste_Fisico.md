# 🧪 Cenário 153: Habilitar Teste Físico nas configurações de avaliação

**Caso de teste:** CT-RF153

**Módulo:** Configurações / Avaliação

**Status:** Aprovado conforme a gravação.

**Gravação:** 16/11/2026, 23:12:07 BRT. **Revisão documental:** 18/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Confirmar que o valor Sim de Teste Físico permanece salvo após recarregar e reabrir Avaliação. |
| Requisito | [RF153](../Analise%20de%20requisitos.md#rf153) — referência de QA. |
| Tipo / prioridade | Funcional manual / persistência · Média, proposta para triagem. |
| Defeito | Nenhum no fluxo avaliado |
| Encaminhamento | Usar como regressão do salvamento e verificar o comportamento da avaliação nos dois estados do seletor. |
| Fonte | [Jam 3 — Habilitação de Teste Físico](https://jam.dev/c/86466f6e-b180-439f-ab1d-dde2484595a3) e [evidências locais](../Evidencias/CT-RF153_Configuracoes_Avaliacao_Habilitar_Teste_Fisico/README.md). |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/configuracoes |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.79 / Windows 10 (x86), conforme os metadados do Jam. |
| Tela / arquivo de vídeo | Tela 1707 × 888 informada no Jam. Vídeo em 1918 × 998. |
| Duração | 17,30 s |
| Localização | Brasil. |
| Versão / zoom / classificação do ambiente | A confirmar antes de nova execução. |
| Dados | Valor inicial Não. Alteração para Sim, com envio de restauração para Não ao final. |

## Pré-condições

- Sessão autenticada com permissão para editar Configurações → Avaliação. Registrar o valor inicial com a base de teste.
- Identificar a versão e registrar os valores iniciais e as permissões no próximo teste.

## Cenário BDD

```gherkin
Cenário: Habilitar Teste Físico nas configurações de avaliação
  Dado que o seletor Teste Físico está em Não
  Quando o usuário seleciona Sim, salva e recarrega a página
  Então a consulta deve devolver o valor salvo
  E o seletor deve exibir Sim ao reabrir Avaliação
```

## Passos para execução ou reteste

1. Abrir Configurações → Avaliação e registrar Não como valor inicial.
2. Selecionar Sim em Teste Físico e salvar.
3. Recarregar e reabrir Avaliação para comparar a interface com a consulta.
4. Restaurar Não, salvar e consultar novamente em uma execução completa.

Este procedimento orienta a próxima execução. O resultado abaixo se limita ao trecho registrado no Jam.

## Resultado esperado

Salvar Sim retorna sucesso. A consulta posterior devolve `teste_fisico: SIM` e Avaliação mantém Sim no seletor.

## Resultado obtido na gravação

O salvamento de Sim retornou HTTP 200 com `verifica_erro: false`. Após recarregar, a consulta devolveu `teste_fisico: SIM` e o seletor mostrou Sim. O POST de restauração para Não retornou sucesso.

| Tempo | Registro |
| --- | --- |
| 0:05,38 | Salva o novo valor Sim. |
| 0:08,42 | Após recarregar, o GET devolve `teste_fisico: SIM`. |
| 0:10,29 | Reabre Avaliação e confirma Sim na interface. |
| 0:15,64 | Envia a restauração para Não e recebe sucesso. |

**Rede:**

- 0:05,38  POST `/api/configuracoes/alterar/1` com `teste_fisico: SIM` (HTTP 200, `verifica_erro: false`).
- 0:08,42  GET `/api/configuracoes/1` (HTTP 200) com `teste_fisico: SIM`.
- 0:15,64  POST de restauração com `teste_fisico: NAO` (HTTP 200, `verifica_erro: false`). A captura termina sem novo GET após a restauração.

**Conclusão:** Aprovado conforme a gravação. A gravação cobre a alteração e a leitura da preferência. A disponibilidade do teste no cadastro de avaliação fica para verificação separada.

## Critérios de aceitação para nova execução

1. O salvamento de Sim retorna sucesso.
2. O GET após recarregar devolve `teste_fisico: SIM`.
3. O seletor mantém Sim após reabrir a aba.

## Próxima ação e verificações complementares

Usar como regressão do salvamento e verificar o comportamento da avaliação nos dois estados do seletor.

## Evidências e limites

- [Jam 3 — Habilitação de Teste Físico](https://jam.dev/c/86466f6e-b180-439f-ab1d-dde2484595a3).
- [Arquivos, origem e limites](../Evidencias/CT-RF153_Configuracoes_Avaliacao_Habilitar_Teste_Fisico/README.md).
- [Teste Físico em Não antes da alteração](../Evidencias/CT-RF153_Configuracoes_Avaliacao_Habilitar_Teste_Fisico/teste_fisico_nao_00-01.jpg), [Teste Físico em Sim depois de reabrir Avaliação](../Evidencias/CT-RF153_Configuracoes_Avaliacao_Habilitar_Teste_Fisico/teste_fisico_sim_00-12.jpg).
- [Linha do tempo](../Evidencias/CT-RF153_Configuracoes_Avaliacao_Habilitar_Teste_Fisico/linha_do_tempo.txt).

A revisão documental se baseia nos quadros do vídeo e nos eventos capturados pelo Jam. As verificações complementares ficam para uma nova rodada de testes.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf153) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
