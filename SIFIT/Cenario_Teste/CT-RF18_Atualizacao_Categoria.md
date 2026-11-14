# 🧪 Cenário 18: Atualização de categoria

**Caso de teste:** CT-RF18

**Módulo:** Categorias Crossfit / Edição

**Status:** Aprovado conforme a gravação.

**Gravação:** 14/11/2026, 00:43:20 BRT. **Revisão documental:** 14/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Salvar a atualização do nome de categoria. |
| Requisito | [RF18](../Analise%20de%20requisitos.md#rf18) |
| Tipo / prioridade | Funcional manual, análise de evidências / Média, proposta para triagem. |
| Defeito | Nenhum no fluxo avaliado |
| Encaminhamento | Sem reteste corretivo pendente; manter como regressão. |
| Fonte | [Jam — Teste de atualização funcionando](https://jam.dev/c/67664a98-2a4a-4134-91a9-7ca9b8aa9dbd) |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/categorias-exercicios-crossfit |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.51 / Windows 11 (x86). |
| Tela / arquivo de vídeo | 1920 × 957 informados no Jam; original 1918 × 956 pixels. |
| Duração | 11,67 s |
| Versão / zoom / classificação do ambiente | Não confirmados; registrar antes de nova execução. |
| Dados | Usar dados de teste conhecidos conforme as pré-condições abaixo; valores da gravação são referência histórica, sem copiar credenciais. |

## Pré-condições

- Sessão autenticada com permissão de edição.
- Categoria de teste editável e nome inicial conhecido.
- Antes de uma nova execução, identificar versão, permissões e dados de referência e preparar a captura de interface e rede.

## Cenário BDD

```gherkin
Cenário: Salvar a atualização do nome de categoria
  Dado que existe uma categoria de teste editável
  Quando alterar seu nome e clicar em "Salvar"
  Então o sistema deve atualizar o cadastro
  E apresentar o nome atualizado na listagem
```

## Passos para execução ou reteste

1. Abrir a edição da categoria Barbell teste da base de referência.
2. Alterar o nome para Barbell novo.
3. Clicar em Salvar e conferir o valor atualizado na lista; em nova execução, recarregar para conferir persistência.

Este procedimento orienta a próxima execução. A evidência atual cobre o trecho gravado e os limites descritos abaixo; passos complementares, como conferir downloads ou recarregar a sessão, não recebem resultado de execução nesta revisão.

## Resultado esperado

Persistir a alteração e atualizar a listagem.

## Resultado obtido na gravação

O modal fecha e a lista exibe Barbell novo.

**Momentos e registros:** 0:06: POST /api/categoria-exercicio-cross/atualizar com HTTP 200, seguido de GET /listar com HTTP 200. 0:08–0:11: nome atualizado na tabela.

**Conclusão:** Aprovado conforme a gravação. A aprovação se limita ao cenário visível; não significa validação de todas as variações do fluxo.

## Critérios de aceitação para nova execução

1. O editor carrega a categoria selecionada.
2. Salvar conclui a atualização e retorna à lista com o novo nome.
3. Persistência após recarga ou nova sessão é uma extensão de validação ainda não executada.

## Próxima ação e verificações complementares

Usar como regressão; acrescentar recarga e nova consulta para ampliar a verificação de persistência.

Nenhum defeito adicional foi criado para este cenário.

## Evidências e limites

- [Jam original — Teste de atualização funcionando](https://jam.dev/c/67664a98-2a4a-4134-91a9-7ca9b8aa9dbd).
- [Vídeo original](../Evidencias/CT-RF18_Atualizacao_Categoria/video.webm).
- [Resumo, origem e integridade](../Evidencias/CT-RF18_Atualizacao_Categoria/README.md).
- [Cronologia do Jam](../Evidencias/CT-RF18_Atualizacao_Categoria/linha_do_tempo.txt).

A atualização está demonstrada na própria gravação. Não houve novo teste de persistência após outra sessão ou novo login.

Análise documental das gravações já consultadas em 14/11/2026 (metadados, cronologia e quadros distribuídos pelo vídeo). Esta inclusão não executa novamente o sistema, não corrige a aplicação e não constitui reteste. Versão da aplicação, zoom e classificação do ambiente não foram confirmados.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
