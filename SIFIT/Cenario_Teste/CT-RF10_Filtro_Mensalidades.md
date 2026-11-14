# 🧪 Cenário 10: Filtro Até 7 dias conta uma mensalidade e mostra lista vazia

**Caso de teste:** CT-RF10

**Módulo:** Financeiro / Financeiro em Aberto

**Status:** Reprovado nas evidências.

**Gravação:** 14/11/2026, 00:30:39 BRT. **Revisão documental:** 14/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Aplicar o filtro Até 7 dias com contagem consistente. |
| Requisito | [RF10](../Analise%20de%20requisitos.md#rf10) |
| Tipo / prioridade | Funcional manual, análise de evidências / Alta, proposta para triagem. |
| Defeito | [BUG-005](../Relatorio-de-Bugs.md#bug-005) |
| Encaminhamento | Aberto; reteste pendente após correção. |
| Fonte | [Jam — Erro no filtro de mensalidade](https://jam.dev/c/3f78cf16-2c3b-48bc-8622-23b829debbec) |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/dashboard |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.51 / Windows 11 (x86). |
| Tela / arquivo de vídeo | 1920 × 957 informados no Jam; original 1918 × 956 pixels. |
| Duração | 9,31 s |
| Versão / zoom / classificação do ambiente | Não confirmados; registrar antes de nova execução. |
| Dados | Usar dados de teste conhecidos conforme as pré-condições abaixo; valores da gravação são referência histórica, sem copiar credenciais. |

## Pré-condições

- Sessão autenticada e modal Financeiro em Aberto disponível.
- Mensalidade conhecida que pertença à faixa Até 7 dias conforme a regra do produto.
- Antes de uma nova execução, identificar versão, permissões e dados de referência e preparar a captura de interface e rede.

## Cenário BDD

```gherkin
Cenário: Aplicar o filtro Até 7 dias com contagem consistente
  Dado que existe uma mensalidade pertencente ao filtro "Até 7 dias"
  Quando selecionar esse filtro no financeiro
  Então a lista deve exibir o registro contabilizado
  E a mensagem de lista vazia só deve aparecer se o contador também representar zero registros
```

## Passos para execução ou reteste

1. Selecionar Até 7 dias no modal financeiro.
2. Aguardar o carregamento e comparar contador, linhas e estado vazio.
3. Conferir que os registros esperados estão acessíveis e que a mensagem vazia só aparece para conjunto vazio.

Este procedimento orienta a próxima execução. A evidência atual cobre o trecho gravado e os limites descritos abaixo; passos complementares, como conferir downloads ou recarregar a sessão, não recebem resultado de execução nesta revisão.

## Resultado esperado

O contador do filtro e os registros exibidos devem representar o mesmo conjunto.

## Resultado obtido na gravação

O filtro mantém o contador 1, enquanto a lista informa “Nenhuma mensalidade encontrada para o filtro atual”.

**Momentos e registros:** 0:00: clique em Até 7 dias 1 e POST /api/contas-receber/vencidas/1 com HTTP 200. 0:02–0:09: estado vazio.

**Conclusão:** Reprovado nas evidências. O defeito associado descreve a manifestação observada, sem atribuir uma causa técnica não comprovada.

## Critérios de aceitação para nova execução

1. Contador e lista usam o mesmo critério de período.
2. Uma mensalidade contabilizada no filtro pode ser consultada.
3. Conjunto vazio apresenta mensagem e contagem coerentes.

## Próxima ação e verificações complementares

Retestar em conjunto com CT-RF09 e conferir o contrato da faixa Até 7 dias antes de preparar a base.

O [BUG-005](../Relatorio-de-Bugs.md#bug-005) permanece aberto. Severidade **Alta** e prioridade **Alta** são propostas para triagem; encerrar somente após evidências de reteste em uma versão identificada.

## Evidências e limites

- [Jam original — Erro no filtro de mensalidade](https://jam.dev/c/3f78cf16-2c3b-48bc-8622-23b829debbec).
- [Vídeo original](../Evidencias/CT-RF10_Filtro_Mensalidades/video.webm).
- [Resumo, origem e integridade](../Evidencias/CT-RF10_Filtro_Mensalidades/README.md).
- [Cronologia do Jam](../Evidencias/CT-RF10_Filtro_Mensalidades/linha_do_tempo.txt).

A evidência confirma a divergência visual. A causa técnica não foi investigada. Relacionado ao CT-RF09.

Análise documental das gravações já consultadas em 14/11/2026 (metadados, cronologia e quadros distribuídos pelo vídeo). Esta inclusão não executa novamente o sistema, não corrige a aplicação e não constitui reteste. Versão da aplicação, zoom e classificação do ambiente não foram confirmados.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
