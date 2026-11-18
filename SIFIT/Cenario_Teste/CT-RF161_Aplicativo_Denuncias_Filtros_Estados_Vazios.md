# 🧪 Cenário 161: Alternar o filtro de denúncias com a lista vazia

**Caso de teste:** CT-RF161

**Módulo:** Aplicativo / Denúncias

**Status:** Aprovado conforme a gravação.

**Gravação:** 16/11/2026, 22:44:19 BRT. **Revisão documental:** 18/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Conferir a troca entre todos os registros e apenas pendentes na seção Denúncias com a lista vazia. |
| Requisito | [RF161](../Analise%20de%20requisitos.md#rf161) — referência de QA. |
| Tipo / prioridade | Funcional manual / filtragem de lista vazia · Média, proposta para triagem. |
| Defeito | Nenhum no fluxo avaliado |
| Encaminhamento | Retestar com denúncias de teste em estados diferentes e conferir os registros exibidos em cada filtro. |
| Fonte | [Jam 5 — Filtros de denúncias sem registros](https://jam.dev/c/709cd210-f823-4348-805f-3cb61e7fb23f) e [evidências locais](../Evidencias/CT-RF161_Aplicativo_Denuncias_Filtros_Estados_Vazios/README.md). |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/aplicativo |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.79 / Windows 10 (x86), conforme os metadados do Jam. |
| Tela / arquivo de vídeo | Tela 1536 × 799 informada no Jam. Vídeo em 1918 × 998. |
| Duração | 10,89 s |
| Localização | Brasil. |
| Versão / zoom / classificação do ambiente | A confirmar antes de nova execução. |
| Dados | Nenhuma denúncia disponível no trecho. Filtros Ver todas e Só pendentes. |

## Pré-condições

- Sessão autenticada em Aplicativo com a seção Denúncias disponível.
- Identificar a versão e registrar os valores iniciais e as permissões no próximo teste.

## Cenário BDD

```gherkin
Cenário: Alternar o filtro de denúncias com a lista vazia
  Dado que a seção Denúncias está vazia
  Quando o usuário alterna o filtro entre todas e pendentes
  Então o aviso deve corresponder ao modo selecionado
  E o controle deve oferecer a ação para voltar ao outro modo
```

## Passos para execução ou reteste

1. Localizar Denúncias em Aplicativo com a lista vazia.
2. Selecionar Ver todas e conferir o aviso.
3. Selecionar Só pendentes e conferir a troca do aviso.
4. Repetir a alternância e verificar a consistência do comportamento.

Este procedimento orienta a próxima execução. O resultado abaixo se limita ao trecho registrado no Jam.

## Resultado esperado

A tela diferencia nenhuma denúncia registrada de nenhuma denúncia pendente ao alternar os filtros.

## Resultado obtido na gravação

Ver todas mostrou “Nenhuma denúncia registrada”. Só pendentes mostrou “Nenhuma denúncia pendente. Tudo tranquilo por aqui.” Os avisos voltaram a aparecer nas alternâncias seguintes.

| Tempo | Registro |
| --- | --- |
| 0:03–0:05 | Localiza Denúncias no painel Aplicativo. |
| 0:05,70 e 0:07,56 | Aciona Ver todas. A tela indica nenhuma denúncia registrada. |
| 0:06,67 e 0:08,28 | Aciona Só pendentes. A tela indica nenhuma denúncia pendente. |

**Rede:**

- Os eventos registram quatro cliques nos controles de filtro. A evidência deste fluxo é a alteração visual do aviso de lista vazia.

**Conclusão:** Aprovado conforme a gravação. A evidência cobre a interface sem denúncias. A filtragem com registros pendentes e tratados ficou fora da gravação.

## Critérios de aceitação para nova execução

1. O modo todas indica ausência de denúncias registradas.
2. O modo pendentes indica ausência de denúncias pendentes.
3. A alternância pode ser repetida durante a mesma sessão.

## Próxima ação e verificações complementares

Retestar com denúncias de teste em estados diferentes e conferir os registros exibidos em cada filtro.

## Evidências e limites

- [Jam 5 — Filtros de denúncias sem registros](https://jam.dev/c/709cd210-f823-4348-805f-3cb61e7fb23f).
- [Arquivos, origem e limites](../Evidencias/CT-RF161_Aplicativo_Denuncias_Filtros_Estados_Vazios/README.md).
- [Lista de denúncias em todas, com o respectivo estado vazio](../Evidencias/CT-RF161_Aplicativo_Denuncias_Filtros_Estados_Vazios/denuncias_todas_00-06.jpg), [Lista filtrada por pendentes, com o aviso correspondente](../Evidencias/CT-RF161_Aplicativo_Denuncias_Filtros_Estados_Vazios/denuncias_pendentes_00-09.jpg).
- [Linha do tempo](../Evidencias/CT-RF161_Aplicativo_Denuncias_Filtros_Estados_Vazios/linha_do_tempo.txt).

A revisão documental se baseia nos quadros do vídeo e nos eventos capturados pelo Jam. As verificações complementares ficam para uma nova rodada de testes.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf161) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
