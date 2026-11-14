# 🧪 Cenário 20: Criação de categoria

**Caso de teste:** CT-RF20

**Módulo:** Categorias Crossfit / Cadastro

**Status:** Aprovado conforme a gravação.

**Gravação:** 14/11/2026, 00:45:17 BRT. **Revisão documental:** 14/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Cadastrar e listar uma nova categoria. |
| Requisito | [RF20](../Analise%20de%20requisitos.md#rf20) |
| Tipo / prioridade | Funcional manual, análise de evidências / Média, proposta para triagem. |
| Defeito | Nenhum no fluxo avaliado |
| Encaminhamento | Sem reteste corretivo pendente; manter como regressão. |
| Fonte | [Jam — Teste criação de nova categorias](https://jam.dev/c/b48ab94e-517d-48d6-8e46-70b18c033b8b) |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/categorias-exercicios-crossfit |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.51 / Windows 11 (x86). |
| Tela / arquivo de vídeo | 1920 × 957 informados no Jam; original 1918 × 956 pixels. |
| Duração | 15,07 s |
| Versão / zoom / classificação do ambiente | Não confirmados; registrar antes de nova execução. |
| Dados | Usar dados de teste conhecidos conforme as pré-condições abaixo; valores da gravação são referência histórica, sem copiar credenciais. |

## Pré-condições

- Sessão autenticada com permissão para cadastrar categorias.
- Nome de categoria de teste disponível segundo as regras do produto.
- Antes de uma nova execução, identificar versão, permissões e dados de referência e preparar a captura de interface e rede.

## Cenário BDD

```gherkin
Cenário: Cadastrar e listar uma nova categoria
  Dado que o usuário possui permissão para cadastrar categorias
  Quando abrir "Nova Categoria" e informar um nome válido
  E clicar em "Salvar"
  Então o sistema deve criar a categoria
  E apresentar o novo registro e a contagem atualizada
```

## Passos para execução ou reteste

1. Clicar em Nova Categoria.
2. Preencher o nome cardio leve na base de referência.
3. Clicar em Salvar e conferir o novo registro e o contador da lista.

Este procedimento orienta a próxima execução. A evidência atual cobre o trecho gravado e os limites descritos abaixo; passos complementares, como conferir downloads ou recarregar a sessão, não recebem resultado de execução nesta revisão.

## Resultado esperado

Criar a categoria e apresentar o novo registro na listagem.

## Resultado obtido na gravação

O modal fecha, o contador passa de sete para oito e a lista passa a incluir cardio leve.

**Momentos e registros:** 0:10: POST /api/categoria-exercicio-cross/criar retorna HTTP 201, seguido de GET /listar com HTTP 200. 0:11–0:15: novo registro visível.

**Conclusão:** Aprovado conforme a gravação. A aprovação se limita ao cenário visível; não significa validação de todas as variações do fluxo.

## Critérios de aceitação para nova execução

1. O formulário permite informar um nome válido.
2. Salvar cria o registro e fecha o formulário com retorno de sucesso.
3. A lista exibe a nova categoria e o total atualizado.

## Próxima ação e verificações complementares

Usar como regressão; campos vazios, nomes duplicados e limites de tamanho permanecem fora do cenário gravado.

Nenhum defeito adicional foi criado para este cenário.

## Evidências e limites

- [Jam original — Teste criação de nova categorias](https://jam.dev/c/b48ab94e-517d-48d6-8e46-70b18c033b8b).
- [Vídeo original](../Evidencias/CT-RF20_Criacao_Categoria/video.webm).
- [Resumo, origem e integridade](../Evidencias/CT-RF20_Criacao_Categoria/README.md).
- [Cronologia do Jam](../Evidencias/CT-RF20_Criacao_Categoria/linha_do_tempo.txt).

O teste demonstra criação no cenário gravado. Não cobre campos vazios, duplicidade ou validações de tamanho.

Análise documental das gravações já consultadas em 14/11/2026 (metadados, cronologia e quadros distribuídos pelo vídeo). Esta inclusão não executa novamente o sistema, não corrige a aplicação e não constitui reteste. Versão da aplicação, zoom e classificação do ambiente não foram confirmados.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
