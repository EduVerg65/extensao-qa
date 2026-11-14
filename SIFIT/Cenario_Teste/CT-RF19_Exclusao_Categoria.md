# 🧪 Cenário 19: Exclusão de categoria retorna erro HTTP 500

**Caso de teste:** CT-RF19

**Módulo:** Categorias Crossfit / Exclusão

**Status:** Reprovado nas evidências.

**Gravação:** 14/11/2026, 00:43:59 BRT. **Revisão documental:** 14/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Excluir categoria permitida ou explicar o impedimento. |
| Requisito | [RF19](../Analise%20de%20requisitos.md#rf19) |
| Tipo / prioridade | Funcional manual, análise de evidências / Média, proposta para triagem. |
| Defeito | [BUG-009](../Relatorio-de-Bugs.md#bug-009) |
| Encaminhamento | Aberto; reteste pendente após correção. |
| Fonte | [Jam — Erro a o deletar categoria](https://jam.dev/c/c5c78b3b-2865-4226-836f-bcb0a8fc612f) |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/categorias-exercicios-crossfit |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.51 / Windows 11 (x86). |
| Tela / arquivo de vídeo | 1920 × 957 informados no Jam; original 1918 × 956 pixels. |
| Duração | 8,30 s |
| Versão / zoom / classificação do ambiente | Não confirmados; registrar antes de nova execução. |
| Dados | Usar dados de teste conhecidos conforme as pré-condições abaixo; valores da gravação são referência histórica, sem copiar credenciais. |

## Pré-condições

- Sessão autenticada com permissão para excluir categorias.
- Categoria descartável e vínculos conhecidos; confirmar os impedimentos de exclusão previstos.
- Antes de uma nova execução, identificar versão, permissões e dados de referência e preparar a captura de interface e rede.

## Cenário BDD

```gherkin
Cenário: Excluir categoria permitida ou explicar o impedimento
  Dado que o usuário solicita excluir uma categoria de teste
  Quando confirmar a exclusão
  Então o sistema deve concluir a operação permitida
  Ou explicar de forma tratável o impedimento previsto
  E não deve encerrar a operação apenas com um erro interno genérico
```

## Passos para execução ou reteste

1. Acionar a lixeira da categoria de teste.
2. Confirmar a exclusão no diálogo.
3. Conferir retorno visual, status da chamada e presença do registro após a operação.

Este procedimento orienta a próxima execução. A evidência atual cobre o trecho gravado e os limites descritos abaixo; passos complementares, como conferir downloads ou recarregar a sessão, não recebem resultado de execução nesta revisão.

## Resultado esperado

Concluir a exclusão permitida ou explicar de forma tratável por que o registro não pode ser excluído.

## Resultado obtido na gravação

Após a confirmação, aparece o diálogo “Erro” / “Erro ao deletar categoria”. A categoria permanece na lista.

**Momentos e registros:** 0:02: POST /api/categoria-exercicio-cross/excluir retorna HTTP 500. 0:03–0:05: mensagem de erro.

**Conclusão:** Reprovado nas evidências. O defeito associado descreve a manifestação observada, sem atribuir uma causa técnica não comprovada.

## Critérios de aceitação para nova execução

1. Exclusão permitida remove ou altera o registro conforme a regra definida.
2. Impedimentos por vínculos são informados de forma compreensível e sem falha interna genérica.
3. A listagem e o retorno da operação refletem o resultado efetivo.

## Próxima ação e verificações complementares

Investigar o HTTP 500 com logs do servidor e vínculos da categoria; corrigir e retestar cenários permitido e impedido.

O [BUG-009](../Relatorio-de-Bugs.md#bug-009) permanece aberto. Severidade **Média** e prioridade **Alta** são propostas para triagem; encerrar somente após evidências de reteste em uma versão identificada.

## Evidências e limites

- [Jam original — Erro a o deletar categoria](https://jam.dev/c/c5c78b3b-2865-4226-836f-bcb0a8fc612f).
- [Vídeo original](../Evidencias/CT-RF19_Exclusao_Categoria/video.webm).
- [Resumo, origem e integridade](../Evidencias/CT-RF19_Exclusao_Categoria/README.md).
- [Cronologia do Jam](../Evidencias/CT-RF19_Exclusao_Categoria/linha_do_tempo.txt).

O erro e o endpoint estão registrados. Sem o corpo completo da resposta, logs do servidor ou banco, a causa do HTTP 500 não foi determinada.

Análise documental das gravações já consultadas em 14/11/2026 (metadados, cronologia e quadros distribuídos pelo vídeo). Esta inclusão não executa novamente o sistema, não corrige a aplicação e não constitui reteste. Versão da aplicação, zoom e classificação do ambiente não foram confirmados.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
