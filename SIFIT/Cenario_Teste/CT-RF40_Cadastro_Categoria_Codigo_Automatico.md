# 🧪 Cenário 40: Cadastro de categoria com código automático e consulta pelo código

**Caso de teste:** CT-RF40

**Módulo:** Categorias Crossfit / Cadastro e filtros

**Status:** Aprovado conforme a gravação.

**Gravação:** 15/11/2026, 18:41 BRT. **Revisão documental:** 15/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Cadastrar uma categoria informando apenas o nome, com o código atribuído pelo sistema, e localizar o novo registro pelos filtros de código e de nome. |
| Requisito | [RF40](../Analise%20de%20requisitos.md#rf40) |
| Tipo / prioridade | Funcional manual, análise de evidências / Média, proposta para triagem. |
| Defeito | Nenhum no fluxo avaliado |
| Encaminhamento | Sem reteste corretivo pendente; manter como regressão. Confirmar com o produto a regra do campo Código. |
| Fonte | [Jam — Categorias Crossfit](https://jam.dev/c/be1dbd05-217d-44c3-8a3d-240b7f6344e1) e [evidências locais](../Evidencias/CT-RF38_Cadastro_Categoria_Codigo_Automatico/README.md). |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/categorias-exercicios-crossfit |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.78 / Windows (x86) 11. |
| Tela / arquivo de vídeo | 1920 × 911 informados no Jam; vídeo de 1516 × 720. |
| Duração | 37 s |
| Rede | Classificada como rápida no Jam: 8,8 Mbps, latência de 100 ms. |
| Localização | Brasil. |
| Usuário exibido | Jair, conforme o canto superior direito da tela. |
| Versão / zoom / classificação do ambiente | Não confirmados; registrar antes de nova execução. |
| Dados | Base com oito categorias (códigos 1 a 8). Nome de teste "teste"; texto "qwdas" digitado no campo Código como valor de referência histórica. |

## Pré-condições

- Sessão autenticada com acesso a Categorias Crossfit e à ação Nova Categoria.
- Base conhecida, com a quantidade de categorias e os códigos registrados antes da inclusão.
- Nome de categoria de teste disponível, sem conflito com registros existentes.
- Antes de uma nova execução, identificar versão, permissões e dados de referência e preparar a captura de interface e rede.

## Cenário BDD

```gherkin
Cenário: Cadastrar uma categoria com código atribuído pelo sistema
  Dado que a listagem de Categorias Crossfit apresenta as categorias existentes
  Quando o usuário abrir o formulário "Cadastrar Categoria"
  E informar apenas o nome da categoria
  E confirmar em "Salvar"
  Então o sistema deve criar a categoria com um código próprio
  E apresentar o novo registro na listagem
  E atualizar os cartões de resumo

Cenário: Localizar a categoria criada pelo filtro de código
  Dado que a nova categoria consta na listagem
  Quando o usuário informar o código atribuído no filtro Código
  Então a listagem deve apresentar apenas a categoria correspondente
  E o cartão Exibidas deve corresponder aos registros apresentados
```

## Passos para execução ou reteste

1. Acessar Categorias Crossfit e registrar a listagem, os códigos e os cartões Categorias, Exibidas e Atualizadas.
2. Filtrar por nome (parte do nome de uma categoria existente) e conferir a listagem e o cartão Exibidas; limpar o filtro.
3. Filtrar por um código existente e conferir o registro retornado; limpar o filtro.
4. Abrir Nova Categoria, informar o nome e tentar digitar um texto no campo Código.
5. Clicar em Salvar; conferir a mensagem, o novo registro, o código atribuído e os cartões.
6. Filtrar pelo código atribuído e conferir que a categoria criada é a única exibida; limpar o filtro.

Este procedimento orienta a próxima execução. A evidência atual cobre o trecho gravado e os limites descritos abaixo; passos complementares, como a recarga da página, não recebem resultado de execução nesta revisão.

## Resultado esperado

A categoria é criada com um código atribuído pelo sistema, passa a constar na listagem, os cartões refletem a inclusão e os filtros retornam apenas os registros correspondentes aos critérios.

## Resultado obtido na gravação

O cadastro foi concluído com sucesso e a nova categoria foi localizada pelo filtro de código.

| Tempo | Registro |
| --- | --- |
| 0:00 | Listagem com oito categorias (códigos 1 a 8); cartões Categorias 8, Exibidas 8 e Atualizadas 8. |
| 0:01–0:03 | Filtro Nome "bar": uma linha, código 1 "Barbell novo"; cartão Exibidas 1 e Categorias 8. Em seguida o campo é limpo. |
| 0:06–0:10 | Filtro Código "8": uma linha, código 8 "cardio leve"; cartão Exibidas 1. O valor "9" é digitado e apagado, e a listagem completa volta a ser exibida em 0:11. |
| 0:13–0:20 | Alternância do tema (Escuro em 0:13 e Claro em 0:14), abertura do painel de notificações e cliques no menu do usuário; dois POST `tema` com HTTP 200. |
| 0:21–0:22 | Clique em Nova Categoria; formulário "Cadastrar Categoria" com os campos Código e Nome. |
| 0:24–0:27 | Nome "teste" preenchido; o texto "qwdas" é digitado no Código em 0:25 e o campo permanece vazio em 0:27. |
| 0:27 | Clique em Salvar: `OPTIONS` HTTP 204 e `POST /api/categoria-exercicio-cross/criar` com HTTP 201 em 68 ms. |
| 0:28 | Listagem com nove categorias; o novo registro é o código 9 "teste", criado e atualizado em 15/11/2026; cartões Categorias 9, Exibidas 9 e Atualizadas 9. Um `GET listar` com HTTP 200 (910 B) atualiza a tabela. |
| 0:31–0:32 | Filtro Código "9": uma linha, código 9 "teste"; cartão Exibidas 1 e Categorias 9. |
| 0:33–0:36 | Campo Código limpo e listagem completa, com nove registros. |

**Requisição e resposta de criação:** o corpo enviado contém apenas `{"nome": "teste"}`, sem o campo código nem o texto "qwdas". A resposta é `{"verifica_erro": false, "mensagem": "Categoria criada com sucesso!"}`, com `content-length: 70`, `x-powered-by: PHP/8.2.35` e `date: Sun, 15 Nov 2026 21:41:24 GMT`.

**Conclusão:** Aprovado conforme a gravação. O cadastro cria a categoria apenas com o nome, o código 9 é atribuído em sequência ao oito já existente e os filtros por nome e por código retornam os registros esperados nos exemplos gravados. A aprovação se limita aos exemplos gravados; não significa validação de todas as combinações.

## Critérios de aceitação para nova execução

1. O formulário permite informar o nome e cria a categoria ao salvar, com mensagem de sucesso.
2. O código é atribuído pelo sistema, sem depender de valor digitado pelo usuário, e não duplica um código existente.
3. A listagem e os cartões de resumo refletem a inclusão.
4. O filtro por nome e o filtro por código retornam apenas os registros correspondentes, com o cartão Exibidas coerente.
5. A limpeza dos filtros restaura a listagem completa.
6. O registro permanece após recarga da página.

## Próxima ação e verificações complementares

Usar como regressão. Permanecem fora do cenário gravado: nome vazio, nome duplicado, limites de tamanho e caracteres especiais, código inexistente ou não numérico no filtro, filtro de nome e de código combinados com critérios contraditórios, resultado vazio, paginação e persistência após recarga.

## Observação sobre o campo Código

O campo Código do formulário não retém o texto digitado (quadro de 0:27), e o corpo da requisição de criação não o contém; o registro recebe o código 9, seguinte ao último existente. O conjunto é compatível com um código atribuído automaticamente pelo sistema, como se interpretou em [CT-RF30](CT-RF30_Cadastro_GrupoMuscular.md#observações-sobre-o-campo-código) e [CT-RF33](CT-RF33_Cadastro_Objetivo_Treino.md#observação-sobre-o-campo-código). Também seria compatível com um campo bloqueado a digitação, o que se relaciona ao relato de [CT-RF21](CT-RF21_Digitacao_Codigo_Exercicio.md) / [BUG-011](../Relatorio-de-Bugs.md#bug-011). A regra do produto não foi fornecida; o ponto permanece a confirmar e não gera defeito. A ausência de mensagem ou de indicação de que o campo é automático não foi avaliada como falha de usabilidade nesta revisão.

## Observação sobre os filtros e a rede

Na lista de rede há cinco entradas: dois POST `tema` (HTTP 200), `OPTIONS` e `POST criar` (HTTP 204 e 201) e um `GET listar` (HTTP 200). Os filtros por nome e por código (0:01–0:12 e 0:31–0:36) não geram entrada de rede, o que é compatível com filtragem feita na própria tela sobre a listagem carregada; não foi confirmado, pois a captura do Jam pode não incluir o carregamento inicial da página. Se o filtro deve consultar o servidor, e como se comporta com bases maiores ou paginadas, permanece a confirmar com o responsável pelo produto, como em [CT-RF09](CT-RF09_FILTRO_TelaClientes.md).

## Observação sobre os cartões de resumo

Após a inclusão os três cartões passam de 8 para 9 (Categorias, Exibidas e Atualizadas), e com o filtro aplicado apenas Exibidas muda (1), enquanto Categorias e Atualizadas mantêm o total da base. O comportamento é coerente entre os quadros conferidos; o contrato de cada indicador, em especial o de Atualizadas, não foi fornecido e permanece a confirmar, como em [CT-RF15](CT-RF15_Metricas_Financeiro.md).

## Evidências e limites

- [Jam original — Categorias Crossfit](https://jam.dev/c/be1dbd05-217d-44c3-8a3d-240b7f6344e1).
- [Arquivos, origem e limites](../Evidencias/CT-RF38_Cadastro_Categoria_Codigo_Automatico/README.md).
- [Filtro por nome em 0:02](../Evidencias/CT-RF38_Cadastro_Categoria_Codigo_Automatico/filtro_nome_00-02.png), [filtro por código em 0:08](../Evidencias/CT-RF38_Cadastro_Categoria_Codigo_Automatico/filtro_codigo_00-08.png), [formulário com o Código vazio em 0:27](../Evidencias/CT-RF38_Cadastro_Categoria_Codigo_Automatico/formulario_codigo_vazio_00-27.png), [listagem após o cadastro em 0:28](../Evidencias/CT-RF38_Cadastro_Categoria_Codigo_Automatico/lista_apos_cadastro_00-28.png) e [filtro pelo código 9 em 0:32](../Evidencias/CT-RF38_Cadastro_Categoria_Codigo_Automatico/filtro_codigo_9_00-32.png).
- [Lista de rede](../Evidencias/CT-RF38_Cadastro_Categoria_Codigo_Automatico/rede_lista.png), [requisição de criação](../Evidencias/CT-RF38_Cadastro_Categoria_Codigo_Automatico/requisicao_criar.png) e [resposta de criação](../Evidencias/CT-RF38_Cadastro_Categoria_Codigo_Automatico/resposta_criar.png).
- [Linha do tempo](../Evidencias/CT-RF38_Cadastro_Categoria_Codigo_Automatico/linha_do_tempo.txt).

Foram consultados os painéis Info, Console (atividade do usuário), Network e Actions do Jam, os cabeçalhos, o corpo da requisição e da resposta de criação e os quadros do vídeo. As capturas foram extraídas da reprodução do Jam e mostram o botão de reprodução sobreposto. A listagem completa da base em cada momento não foi conferida registro a registro, nem houve consulta ao banco de dados. A persistência após recarga, a regra do campo Código e o contrato dos cartões não foram verificados. Não houve nova execução, inspeção do código ou correção da aplicação. O vídeo permanece no Jam. O título automático do Jam não foi utilizado.

Análise documental da gravação consultada em 15/11/2026. Esta inclusão não executa novamente o sistema, não corrige a aplicação e não constitui reteste. Versão da aplicação, zoom e classificação do ambiente não foram confirmados.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf40) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
