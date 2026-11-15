# 🧪 Cenário 30: Carregamento das imagens dos grupos musculares

**Caso de teste:** CT-RF30

**Módulo:** Treinamento / Grupos Musculares

**Status:** Reprovado nas evidências.

**Gravação:** 15/11/2026, 15h56 BRT. **Revisão documental:** 15/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Apresentar na listagem a imagem cadastrada de cada grupo muscular. |
| Requisito | [RF30](../Analise%20de%20requisitos.md#rf30) |
| Tipo / prioridade | Funcional manual, análise de evidências / Média, proposta para triagem. |
| Defeito | [BUG-012](../Relatorio-de-Bugs.md#bug-012) |
| Encaminhamento | Verificar a existência dos arquivos no servidor, o caminho gravado para cada registro e a regra que responde HTTP 422 a uma requisição de imagem. |
| Fonte | [Jam — Tela de Grupos Musculares](https://jam.dev/c/98008390-0040-475e-ba7b-7f1e72cc0b2e) |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/grupos-musculares |
| Origem dos arquivos | https://sifit.centrion.com.br/img/grupos_musculares/imagens/ |
| Navegador / sistema | Chrome 157.0.8103.78 / Windows (x86) 11. |
| Tela / arquivo de vídeo | 1920 × 911 informados no Jam. |
| Duração | 2 min 3 s |
| Rede | Classificada como rápida no Jam: mais de 10 Mbps, latência de 50 ms. |
| Localização | Brasil. |
| Versão / zoom / classificação do ambiente | Não confirmados; registrar antes de nova execução. |
| Dados | Usar registros de teste com imagem reconhecidamente cadastrada; valores da gravação são referência histórica. |

## Pré-condições

- Sessão autenticada com acesso à tela Grupos Musculares.
- Existir ao menos um grupo muscular com imagem cadastrada e com o arquivo correspondente conhecido no servidor.
- Antes de uma nova execução, registrar o caminho esperado dos arquivos e preparar a captura de interface e rede.

## Cenário BDD

```gherkin
Cenário: Exibir as imagens dos grupos musculares na listagem
  Dado que existem grupos musculares com imagem cadastrada
  Quando a tela Grupos Musculares for carregada
  Então a coluna IMAGEM deve apresentar a imagem de cada registro
  E as requisições dos arquivos devem ser concluídas com sucesso
```

## Passos para execução ou reteste

1. Acessar a tela Grupos Musculares autenticado, com o painel de rede aberto.
2. Observar a coluna IMAGEM de cada linha da listagem.
3. Conferir no painel de rede o status das requisições para `/img/grupos_musculares/imagens/`.
4. Abrir diretamente no navegador a URL de um dos arquivos e registrar o status e o corpo da resposta.
5. Repetir a conferência após uma busca e após a troca de tema, para verificar se o comportamento é constante.

Este procedimento orienta a próxima execução. A evidência atual cobre o trecho gravado e os limites descritos abaixo; passos complementares, como o acesso direto à URL do arquivo e a conferência no servidor, não recebem resultado de execução nesta revisão.

## Resultado esperado

A coluna IMAGEM apresenta a imagem de cada grupo muscular, e as requisições dos arquivos são concluídas com sucesso.

## Resultado obtido na gravação

A coluna IMAGEM exibe o ícone de imagem quebrada em todas as linhas, do início ao fim da gravação. As requisições dos arquivos retornam **HTTP 422**, com ocorrências também de `net::ERR_ABORTED`.

**Arquivos requisitados:**

| Arquivo | Status observado |
| --- | --- |
| `/img/grupos_musculares/imagens/6ad0c27c20a04.png` | 422 |
| `/img/grupos_musculares/imagens/6abbd0a11ec04.png` | 422, com ocorrências de `net::ERR_ABORTED` |
| `/img/grupos_musculares/imagens/655226c71114f.png` | 422 |
| `/img/grupos_musculares/imagens/6afa0017749b3.jpg` | 422, com ocorrência de `net::ERR_ABORTED` |

**Momentos e registros:** ocorrências de HTTP 422 em 0:06, 0:16, 0:53, 0:57, 1:07, 1:09, 1:12, 1:33, 1:35, 1:39, 1:47 e 1:59. Três ocorrências de `net::ERR_ABORTED` em 0:53, 0:57 e 1:12. As requisições partem da própria página, com `Referenciador: https://sifit.centrion.com.br/grupos-musculares`, `Sec-Fetch-Dest: imagem` e `Accept` de tipos de imagem.

**Quadros consultados:** 0:20, 0:55, 1:18, 1:21, 1:45 e 2:00. Em todos, a coluna IMAGEM apresenta o ícone de imagem quebrada, tanto no tema escuro quanto no tema claro.

**Conclusão:** Reprovado nas evidências. A falha é constante durante toda a gravação e independe do filtro aplicado ou do tema selecionado. A causa não foi determinada.

## Critérios de aceitação para nova execução

1. Cada grupo muscular com imagem cadastrada apresenta a imagem na coluna IMAGEM.
2. As requisições dos arquivos de imagem são concluídas com sucesso.
3. Registros sem imagem apresentam um estado neutro definido pelo produto, e não um ícone de arquivo quebrado.
4. O comportamento se mantém após busca, troca de página e troca de tema.

## Próxima ação e verificações complementares

Verificar se os arquivos existem no caminho `/img/grupos_musculares/imagens/`, se o nome gravado em cada registro corresponde a um arquivo presente e qual regra do servidor responde HTTP 422 a uma requisição de imagem. O código 422 não é o retorno usual para um arquivo ausente ou sem permissão, o que sugere tratamento por aplicação e não entrega direta de arquivo estático; isso é uma hipótese a confirmar, não um diagnóstico.

Verificar também o comportamento para registros criados sem imagem informada. O quadro de 0:48 mostra o formulário de inclusão com o campo Imagem em "Nenhum arquivo escolhido"; ainda assim, a partir de 0:53 passa a ser requisitado um quarto arquivo, `6afa0017749b3.jpg`, com o mesmo 422. Nos trechos em que a listagem é filtrada e exibe apenas o registro incluído, esse é o único arquivo requisitado (1:33, 1:35 e 1:39), o que o associa a esse registro. A associação decorre da correlação entre os filtros e as requisições, sem confirmação no banco de dados. Se confirmada, indica que o sistema passa a referenciar um arquivo de imagem para registros criados sem imagem, e que esse arquivo não é entregue.

## Evidências e limites

- [Jam original — Tela de Grupos Musculares](https://jam.dev/c/98008390-0040-475e-ba7b-7f1e72cc0b2e).
- Painel Rede do Jam: lista filtrada por erros, com as requisições de imagem e seus status.
- Painel Console do Jam, visão de atividade do usuário: cronologia dos erros de rede entre 0:00 e 2:03.
- Quadros consultados: 0:20, 0:55, 1:18, 1:21, 1:45 e 2:00.
- Pasta local de evidências: a criar em `Evidencias/CT-RF30_Imagens_GruposMusculares/`; até lá, a fonte é o Jam indicado acima.

Os códigos de status foram lidos na coluna Status da lista de rede. O painel de detalhe da ferramenta repetiu cabeçalhos de resposta e `x-hcdn-request-id` entre linhas distintas durante a consulta, de modo que os cabeçalhos de resposta das requisições de imagem não foram considerados confiáveis nesta revisão e não são reproduzidos aqui.

Não foi verificada a existência dos arquivos no servidor, nem o conteúdo do campo de imagem de cada registro no banco de dados, nem o resultado do acesso direto às URLs fora da página. Não foram registradas mensagens de console JavaScript na visão consultada, apenas os erros de rede. O cenário de registro sem imagem cadastrada não foi exercitado.

Análise documental da gravação consultada em 15/11/2026, com leitura direta dos painéis do Jam. Esta inclusão não executa novamente o sistema, não corrige a aplicação e não constitui reteste. Versão da aplicação, zoom e classificação do ambiente não foram confirmados.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
