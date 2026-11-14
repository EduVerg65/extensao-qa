# 🧪 Cenário 07: Exportação financeira sem retorno visível

**Caso de teste:** CT-RF07

**Módulo:** Financeiro / Financeiro em Aberto

**Status:** Reprovado nas evidências.

**Gravação:** 14/11/2026, 00:25:37 BRT. **Revisão documental:** 14/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Oferecer retorno ao solicitar exportação financeira. |
| Requisito | [RF07](../Analise%20de%20requisitos.md#rf07) |
| Tipo / prioridade | Funcional manual, análise de evidências / Média, proposta para triagem. |
| Defeito | [BUG-004](../Relatorio-de-Bugs.md#bug-004) |
| Encaminhamento | Aberto; reteste pendente após correção. |
| Fonte | [Jam — botão de exporta sem função](https://jam.dev/c/1084cb18-cb3d-4b85-9c2f-ee431b59a06b) |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/dashboard |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.51 / Windows 11 (x86). |
| Tela / arquivo de vídeo | 1920 × 957 informados no Jam; original 1918 × 956 pixels. |
| Duração | 6,49 s |
| Versão / zoom / classificação do ambiente | Não confirmados; registrar antes de nova execução. |
| Dados | Usar dados de teste conhecidos conforme as pré-condições abaixo; valores da gravação são referência histórica, sem copiar credenciais. |

## Pré-condições

- Sessão autenticada com permissão para consultar e exportar o financeiro.
- Modal Financeiro em Aberto aberto e registros disponíveis.
- Antes de uma nova execução, identificar versão, permissões e dados de referência e preparar a captura de interface e rede.

## Cenário BDD

```gherkin
Cenário: Oferecer retorno ao solicitar exportação financeira
  Dado que o usuário está no modal "Financeiro em Aberto"
  E possui permissão de exportação
  Quando clicar em "Exportar"
  Então o sistema deve informar o processamento ou resultado da solicitação
  E disponibilizar o arquivo ou uma mensagem de falha compreensível
```

## Passos para execução ou reteste

1. Abrir Financeiro em Aberto a partir da página inicial.
2. Clicar uma vez em Exportar e aguardar a conclusão.
3. Verificar retorno visual e o arquivo no histórico de downloads; repetir somente para conferir comportamento.

Este procedimento orienta a próxima execução. A evidência atual cobre o trecho gravado e os limites descritos abaixo; passos complementares, como conferir downloads ou recarregar a sessão, não recebem resultado de execução nesta revisão.

## Resultado esperado

Iniciar a exportação e apresentar um retorno claro ao usuário.

## Resultado obtido na gravação

Vários cliques em Exportar não produzem mudança ou confirmação visível durante a gravação.

**Momentos e registros:** 0:02–0:03: cinco cliques em Exportar. Nenhuma requisição de rede ou mensagem de console foi capturada nesse Jam.

**Conclusão:** Reprovado nas evidências. O defeito associado descreve a manifestação observada, sem atribuir uma causa técnica não comprovada.

## Critérios de aceitação para nova execução

1. O clique oferece retorno perceptível de processamento, conclusão ou falha.
2. O arquivo disponibilizado corresponde ao escopo de exportação definido pelo produto.
3. A validação do download inclui o histórico e a abertura do arquivo, ainda pendentes na evidência atual.

## Próxima ação e verificações complementares

Investigar o retorno do botão; no reteste capturar o histórico de downloads e abrir o arquivo antes de concluir se a exportação foi gerada.

O [BUG-004](../Relatorio-de-Bugs.md#bug-004) permanece aberto. Severidade **Média** e prioridade **Média** são propostas para triagem; encerrar somente após evidências de reteste em uma versão identificada.

## Evidências e limites

- [Jam original — botão de exporta sem função](https://jam.dev/c/1084cb18-cb3d-4b85-9c2f-ee431b59a06b).
- [Vídeo original](../Evidencias/CT-RF07_Exportacao_Financeiro/video.webm).
- [Resumo, origem e integridade](../Evidencias/CT-RF07_Exportacao_Financeiro/README.md).
- [Cronologia do Jam](../Evidencias/CT-RF07_Exportacao_Financeiro/linha_do_tempo.txt).

O vídeo não mostra o diretório de downloads; portanto, não comprova sozinho que nenhum arquivo foi gerado. A ausência de requisição também não exclui uma exportação feita no próprio navegador.

Análise documental das gravações já consultadas em 14/11/2026 (metadados, cronologia e quadros distribuídos pelo vídeo). Esta inclusão não executa novamente o sistema, não corrige a aplicação e não constitui reteste. Versão da aplicação, zoom e classificação do ambiente não foram confirmados.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
