# 🧪 Cenário 120: Conferir a configuração de acesso ao sistema desktop

**Caso de teste:** CT-RF120

**Módulo:** Configurações / Home / Desktop

**Status:** Aprovado conforme a gravação.

**Gravação:** 16/11/2026, 22:10:20 BRT. **Revisão documental:** 17/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Persistir a opção Liberar acesso ao sistema desktop? e manter o cartão Desktop coerente com a opção salva. |
| Requisito | [RF120](../Analise%20de%20requisitos.md#rf120) — referência de QA. |
| Tipo / prioridade | Funcional manual / persistência e interface · Média, proposta para triagem. |
| Defeito | Nenhum no fluxo avaliado |
| Encaminhamento | Usar como regressão da persistência e do cartão. Validar o acesso no aplicativo desktop em um caso próprio. |
| Fonte | [Jam — PED-23 — Acesso desktop](https://jam.dev/c/466be253-ad9a-4856-b567-fb17e1fdd479) e [evidências locais](../Evidencias/CT-RF120_Configuracoes_Acesso_Desktop/README.md). |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/configuracoes |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.79 / Windows 10 (x86), conforme os metadados do Jam. |
| Tela / arquivo de vídeo | Tela 1536 × 799 informada no Jam. Vídeo em 1918 × 998. |
| Duração | 28,54 s |
| Localização | Brasil. |
| Versão / zoom / classificação do ambiente | A confirmar antes de nova execução. |
| Dados | Opção desktop inicialmente em Não. Alterada para Sim e restaurada para Não. |

## Pré-condições

- Sessão autenticada com permissão para alterar a configuração de acesso desktop.
- Identificar a versão e registrar os valores iniciais e as permissões no próximo teste.

## Cenário BDD

```gherkin
Cenário: Conferir a configuração de acesso ao sistema desktop
  Dado que a opção Liberar acesso ao sistema desktop? está em Não
  Quando o usuário selecionar Sim, salvar e recarregar
  Então o seletor e o cartão Desktop devem mostrar Sim
  E ao restaurar e salvar Não, o seletor e o cartão devem mostrar Não após nova recarga
```

## Passos para execução ou reteste

1. Registrar o seletor e o cartão Desktop em Configurações > Home.
2. Selecionar Sim, salvar e recarregar.
3. Conferir o seletor, o cartão e o campo `desktop` na consulta.
4. Restaurar Não, salvar, recarregar e conferir os mesmos dados.

Este procedimento orienta a próxima execução. O resultado abaixo se limita ao trecho registrado no Jam.

## Resultado esperado

O estado selecionado fica salvo em ambos os sentidos e o cartão Desktop mostra o valor carregado.

## Resultado obtido na gravação

Sim e Não foram salvos em sequência com HTTP 200 e `verifica_erro: false`. Após cada recarga, seletor, cartão Desktop e GET apresentaram o mesmo valor.

| Tempo | Registro |
| --- | --- |
| 0:00–0:08 | Altera o seletor de Não para Sim e salva. |
| 0:10–0:12 | Recarrega. Seletor e cartão exibem Sim. |
| 0:17–0:21 | Volta para Não e salva. |
| 0:22–0:24 | Recarrega. Seletor e cartão exibem Não. |

**Rede:**

- 0:08,01  POST `/api/configuracoes/alterar/1` (HTTP 200), com `desktop=sim`.
- 0:11,45  GET `/api/configuracoes/1` (HTTP 200), com `desktop: sim`.
- 0:20,58  Segundo POST (HTTP 200), com `desktop=nao`.
- 0:23,07  Segundo GET (HTTP 200), com `desktop: nao`.

**Conclusão:** Aprovado conforme a gravação. A aprovação cobre Configurações no navegador. A autenticação e o uso efetivo do cliente desktop não foram exercitados.

## Critérios de aceitação para nova execução

1. O seletor mantém o valor salvo após recarga.
2. O cartão Desktop corresponde ao valor do seletor em cada estado.
3. A consulta retorna o flag `desktop` gravado.

## Próxima ação e verificações complementares

Usar como regressão da persistência e do cartão. Validar o acesso no aplicativo desktop em um caso próprio.

## Evidências e limites

- [Jam original — PED-23 — Acesso desktop](https://jam.dev/c/466be253-ad9a-4856-b567-fb17e1fdd479).
- [Arquivos, origem e limites](../Evidencias/CT-RF120_Configuracoes_Acesso_Desktop/README.md).
- [Campo e cartão Desktop em Sim após a recarga](../Evidencias/CT-RF120_Configuracoes_Acesso_Desktop/desktop_sim_00-12.jpg), [Campo e cartão Desktop em Não após a segunda recarga](../Evidencias/CT-RF120_Configuracoes_Acesso_Desktop/desktop_nao_00-24.jpg).
- [Linha do tempo](../Evidencias/CT-RF120_Configuracoes_Acesso_Desktop/linha_do_tempo.txt).

A revisão documental se baseia nos quadros do vídeo e nos eventos capturados pelo Jam. As verificações complementares ficam para uma nova rodada de testes.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf120) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
