# 🧪 Cenário 119: Conferir a configuração Academia marcada como Box?

**Caso de teste:** CT-RF119

**Módulo:** Configurações / Home / SifitBox

**Status:** Aprovado conforme a gravação.

**Gravação:** 16/11/2026, 22:08:35 BRT. **Revisão documental:** 17/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Persistir a configuração Academia marcada como Box? e refletir o estado no cartão SifitBox e no menu Principal. |
| Requisito | [RF119](../Analise%20de%20requisitos.md#rf119) — referência de QA. |
| Tipo / prioridade | Funcional manual / persistência e interface · Média, proposta para triagem. |
| Defeito | Nenhum no fluxo avaliado |
| Encaminhamento | Usar como regressão da configuração e da navegação. Conferir as permissões internas em um cenário dedicado. |
| Fonte | [Jam — PED-22 — Academia marcada como Box](https://jam.dev/c/16dc862d-c3f9-4392-9037-526818e86cd6) e [evidências locais](../Evidencias/CT-RF119_Configuracoes_Academia_Marcada_Box/README.md). |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/configuracoes |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.79 / Windows 10 (x86), conforme os metadados do Jam. |
| Tela / arquivo de vídeo | Tela 1536 × 799 informada no Jam. Vídeo em 1918 × 998. |
| Duração | 33,63 s |
| Localização | Brasil. |
| Versão / zoom / classificação do ambiente | A confirmar antes de nova execução. |
| Dados | Academia marcada como Box? inicialmente em Não. Alterada para Sim e restaurada para Não. |

## Pré-condições

- Sessão autenticada em Configurações > Home, com permissão para alterar o estado de Box e acesso ao menu Principal.
- Identificar a versão e registrar os valores iniciais e as permissões no próximo teste.

## Cenário BDD

```gherkin
Cenário: Conferir a configuração Academia marcada como Box?
  Dado que a opção Academia marcada como Box? está em Não
  Quando o usuário selecionar Sim, salvar e recarregar a página
  Então o formulário e o cartão SifitBox devem indicar Sim e o item SifitBox deve aparecer no menu Principal
  E ao voltar para Não, salvar e recarregar, o cartão deve indicar Não e o menu deve ocultar o item
```

## Passos para execução ou reteste

1. Em Configurações > Home, registrar o seletor, o cartão SifitBox e o menu Principal.
2. Selecionar Sim, salvar e recarregar a página.
3. Conferir o seletor, o cartão, o item no menu e o valor retornado.
4. Voltar para Não, salvar, recarregar e conferir os mesmos elementos.

Este procedimento orienta a próxima execução. O resultado abaixo se limita ao trecho registrado no Jam.

## Resultado esperado

O seletor e o cartão SifitBox acompanham o estado persistido. O item SifitBox aparece no menu Principal em Sim e deixa de aparecer em Não.

## Resultado obtido na gravação

Após salvar Sim e recarregar, o seletor e o cartão exibiram Sim e SifitBox apareceu no menu Principal. Depois de salvar Não e recarregar, seletor e cartão voltaram a Não e o item deixou de aparecer. A API retornou os mesmos estados de `sifitbox`.

| Tempo | Registro |
| --- | --- |
| 0:00–0:11 | Altera a opção inicial Não para Sim e salva. |
| 0:15–0:17 | Recarrega. Seletor e cartão mostram Sim, e o item aparece no menu. |
| 0:23–0:25 | Volta a Não e salva. |
| 0:28–0:30 | Recarrega. Seletor e cartão mostram Não, e o menu Principal deixa de exibir SifitBox. |

**Rede:**

- 0:11,48  POST `/api/configuracoes/alterar/1` (HTTP 200), com `sifitbox=sim`.
- 0:15,75  GET `/api/configuracoes/1` (HTTP 200), com `sifitbox: sim`.
- 0:25,14  Segundo POST (HTTP 200), com `sifitbox=nao`.
- 0:28,45  Segundo GET (HTTP 200), com `sifitbox: nao`.

**Conclusão:** Aprovado conforme a gravação. Foram verificadas persistência e visibilidade do item no menu. Operações e permissões internas do SifitBox não foram exercitadas.

## Critérios de aceitação para nova execução

1. O seletor carrega Sim e Não conforme a escolha persistida.
2. O cartão SifitBox acompanha cada valor.
3. O menu Principal exibe o item em Sim e o oculta em Não.

## Próxima ação e verificações complementares

Usar como regressão da configuração e da navegação. Conferir as permissões internas em um cenário dedicado.

## Evidências e limites

- [Jam original — PED-22 — Academia marcada como Box](https://jam.dev/c/16dc862d-c3f9-4392-9037-526818e86cd6).
- [Arquivos, origem e limites](../Evidencias/CT-RF119_Configuracoes_Academia_Marcada_Box/README.md).
- [Box em Sim após a recarga, com cartão e item no menu](../Evidencias/CT-RF119_Configuracoes_Academia_Marcada_Box/sifitbox_sim_00-17.jpg), [Box em Não após a recarga, com cartão e menu atualizados](../Evidencias/CT-RF119_Configuracoes_Academia_Marcada_Box/sifitbox_nao_00-29.jpg).
- [Linha do tempo](../Evidencias/CT-RF119_Configuracoes_Academia_Marcada_Box/linha_do_tempo.txt).

A revisão documental se baseia nos quadros do vídeo e nos eventos capturados pelo Jam. As verificações complementares ficam para uma nova rodada de testes.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf119) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
