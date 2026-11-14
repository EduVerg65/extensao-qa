# 🧪 Cenário 09: Contagem de mensalidades diverge da lista

**Caso de teste:** CT-RF09

**Módulo:** Financeiro / Financeiro em Aberto

**Status:** Reprovado nas evidências.

**Gravação:** 14/11/2026, 00:28:41 BRT. **Revisão documental:** 14/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Manter contagem e paginação coerentes com as mensalidades. |
| Requisito | [RF09](../Analise%20de%20requisitos.md#rf09) |
| Tipo / prioridade | Funcional manual, análise de evidências / Alta, proposta para triagem. |
| Defeito | [BUG-005](../Relatorio-de-Bugs.md#bug-005) |
| Encaminhamento | Aberto; reteste pendente após correção. |
| Fonte | [Jam — Informa que tem 3 mensalidades e tem apenas 1.](https://jam.dev/c/1874d0b3-5c7c-4f28-85be-91750e20cbe1) |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/dashboard |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.51 / Windows 11 (x86). |
| Tela / arquivo de vídeo | 1920 × 957 informados no Jam; original 1918 × 956 pixels. |
| Duração | 20,44 s |
| Versão / zoom / classificação do ambiente | Não confirmados; registrar antes de nova execução. |
| Dados | Usar dados de teste conhecidos conforme as pré-condições abaixo; valores da gravação são referência histórica, sem copiar credenciais. |

## Pré-condições

- Sessão autenticada com acesso ao financeiro.
- Base de referência com mensalidades conhecidas e distribuídas entre as faixas de vencimento.
- Antes de uma nova execução, identificar versão, permissões e dados de referência e preparar a captura de interface e rede.

## Cenário BDD

```gherkin
Cenário: Manter contagem e paginação coerentes com as mensalidades
  Dado que existem mensalidades conhecidas no "Financeiro em Aberto"
  Quando selecionar "Todos" ou "+30 dias"
  Então o contador e a paginação devem representar o mesmo conjunto da lista
  E todas as mensalidades contabilizadas devem estar acessíveis
```

## Passos para execução ou reteste

1. Abrir Financeiro em Aberto e selecionar Todos.
2. Comparar o contador com as linhas e o total do rodapé; percorrer páginas quando disponíveis.
3. Selecionar +30 dias e repetir a conferência da quantidade e dos registros acessíveis.

Este procedimento orienta a próxima execução. A evidência atual cobre o trecho gravado e os limites descritos abaixo; passos complementares, como conferir downloads ou recarregar a sessão, não recebem resultado de execução nesta revisão.

## Resultado esperado

Manter a contagem, a listagem e a paginação coerentes e permitir consultar todos os registros contabilizados.

## Resultado obtido na gravação

Todos informa três mensalidades, mas aparece uma linha. No filtro +30 dias, o contador indica dois registros e apenas uma linha permanece disponível.

**Momentos e registros:** 0:01–0:05: Todos 3 com uma linha e rodapé 1–1 de 3. 0:10–0:19: +30 dias 2 com uma linha.

**Conclusão:** Reprovado nas evidências. O defeito associado descreve a manifestação observada, sem atribuir uma causa técnica não comprovada.

## Critérios de aceitação para nova execução

1. Contador, total do rodapé e conjunto listado são consistentes.
2. Todos os registros contados podem ser consultados, considerando a paginação.
3. A troca de filtro recalcula a contagem e os registros com os mesmos critérios.

## Próxima ação e verificações complementares

Retestar com o CT-RF10; os dois cenários documentam manifestações do BUG-005, sem criar um defeito duplicado.

O [BUG-005](../Relatorio-de-Bugs.md#bug-005) permanece aberto. Severidade **Alta** e prioridade **Alta** são propostas para triagem; encerrar somente após evidências de reteste em uma versão identificada.

## Evidências e limites

- [Jam original — Informa que tem 3 mensalidades e tem apenas 1.](https://jam.dev/c/1874d0b3-5c7c-4f28-85be-91750e20cbe1).
- [Vídeo original](../Evidencias/CT-RF09_Contagem_Mensalidades/video.webm).
- [Resumo, origem e integridade](../Evidencias/CT-RF09_Contagem_Mensalidades/README.md).
- [Cronologia do Jam](../Evidencias/CT-RF09_Contagem_Mensalidades/linha_do_tempo.txt).

Não foram inspecionados os corpos das respostas ou o banco. Os casos CT-RF09, CT-RF10 e CT-RF11 tratam de aspectos relacionados do mesmo modal.

Análise documental das gravações já consultadas em 14/11/2026 (metadados, cronologia e quadros distribuídos pelo vídeo). Esta inclusão não executa novamente o sistema, não corrige a aplicação e não constitui reteste. Versão da aplicação, zoom e classificação do ambiente não foram confirmados.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
