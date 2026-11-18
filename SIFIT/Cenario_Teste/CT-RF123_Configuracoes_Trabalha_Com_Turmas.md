# 🧪 Cenário 123: Alterar e persistir a opção Trabalha com turmas?

**Caso de teste:** CT-RF123

**Módulo:** Configurações / Home / Turmas

**Status:** Aprovado conforme a gravação.

**Gravação:** 16/11/2026, 22:06:12 BRT. **Revisão documental:** 17/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Salvar os estados Sim e Não da opção Trabalha com turmas? e refletir a escolha após recarregar a página. |
| Requisito | [RF123](../Analise%20de%20requisitos.md#rf123) — referência de QA. |
| Tipo / prioridade | Funcional manual / persistência · Média, proposta para triagem. |
| Defeito | Nenhum no fluxo avaliado |
| Encaminhamento | Usar como regressão para persistência de ambos os estados. Verificar separadamente os efeitos sobre o módulo de turmas. |
| Fonte | [Jam — PED-21 — Trabalha com turmas](https://jam.dev/c/a51c33a5-537a-40fd-a55d-990b70ac0696) e [evidências locais](../Evidencias/CT-RF118_Configuracoes_Trabalha_Com_Turmas/README.md). |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/configuracoes |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.79 / Windows 10 (x86), conforme os metadados do Jam. |
| Tela / arquivo de vídeo | Tela 1536 × 799 informada no Jam. Vídeo em 1918 × 998. |
| Duração | 25,33 s |
| Localização | Brasil. |
| Versão / zoom / classificação do ambiente | A confirmar antes de nova execução. |
| Dados | Trabalha com turmas? inicialmente em Sim. Alterado para Não e depois restaurado para Sim. |

## Pré-condições

- Sessão autenticada em Configurações > Home com permissão para alterar a opção e valor inicial identificado.
- Identificar a versão e registrar os valores iniciais e as permissões no próximo teste.

## Cenário BDD

```gherkin
Cenário: Alterar e persistir a opção Trabalha com turmas?
  Dado que a opção Trabalha com turmas? tem um valor salvo
  Quando o usuário selecionar o outro valor, salvar e recarregar a página
  Então o sistema deve carregar a opção com o novo valor
  E ao salvar e recarregar o valor original, o sistema deve restaurá-lo
```

## Passos para execução ou reteste

1. Registrar o valor atual em Configurações > Home.
2. Selecionar Não, salvar e recarregar a página.
3. Conferir o seletor e o campo `usa_turmas` na consulta.
4. Restaurar Sim, salvar, recarregar e confirmar o valor.

Este procedimento orienta a próxima execução. O resultado abaixo se limita ao trecho registrado no Jam.

## Resultado esperado

Cada valor salvo permanece no seletor após recarga e a consulta devolve o mesmo valor para `usa_turmas`.

## Resultado obtido na gravação

O seletor mudou de Sim para Não e depois voltou a Sim. Os dois salvamentos retornaram HTTP 200 com `verifica_erro: false`. Após cada recarga, o seletor e o GET apresentaram o estado salvo.

| Tempo | Registro |
| --- | --- |
| 0:00–0:08 | Começa em Sim, troca para Não e salva. |
| 0:10–0:12 | Recarrega. O formulário apresenta Não. |
| 0:16–0:19 | Seleciona Sim e salva novamente. |
| 0:20–0:22 | Recarrega. O formulário volta a apresentar Sim. |

**Rede:**

- 0:08,18  POST `/api/configuracoes/alterar/1` (HTTP 200), com `usa_turmas=nao`.
- 0:11,53  GET `/api/configuracoes/1` (HTTP 200), com `usa_turmas: nao`.
- 0:18,52  Segundo POST (HTTP 200), com `usa_turmas=sim`.
- 0:20,88  Segundo GET (HTTP 200), com `usa_turmas: sim`.

**Conclusão:** Aprovado conforme a gravação. A evidência cobre o seletor nas Configurações e o valor retornado após recarga. Os efeitos sobre criação de turmas e sobre o menu Turmas exigem casos específicos.

## Critérios de aceitação para nova execução

1. Salvar Não atualiza a configuração.
2. Salvar Sim atualiza a configuração.
3. Após cada recarga, seletor e resposta da API refletem o valor salvo.

## Próxima ação e verificações complementares

Usar como regressão para persistência de ambos os estados. Verificar separadamente os efeitos sobre o módulo de turmas.

## Evidências e limites

- [Jam original — PED-21 — Trabalha com turmas](https://jam.dev/c/a51c33a5-537a-40fd-a55d-990b70ac0696).
- [Arquivos, origem e limites](../Evidencias/CT-RF118_Configuracoes_Trabalha_Com_Turmas/README.md).
- [Trabalha com turmas? em Não após a recarga](../Evidencias/CT-RF118_Configuracoes_Trabalha_Com_Turmas/turmas_nao_00-12.jpg), [Trabalha com turmas? em Sim após a segunda recarga](../Evidencias/CT-RF118_Configuracoes_Trabalha_Com_Turmas/turmas_sim_00-22.jpg).
- [Linha do tempo](../Evidencias/CT-RF118_Configuracoes_Trabalha_Com_Turmas/linha_do_tempo.txt).

A revisão documental se baseia nos quadros do vídeo e nos eventos capturados pelo Jam. As verificações complementares ficam para uma nova rodada de testes.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf123) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
