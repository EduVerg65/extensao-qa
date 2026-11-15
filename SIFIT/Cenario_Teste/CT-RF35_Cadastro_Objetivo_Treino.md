# 🧪 Cenário 35: Cadastro de objetivo de treino retorna HTTP 500

**Caso de teste:** CT-RF35

**Módulo:** Treinamento / Objetivos Treino

**Status:** Reprovado nas evidências; reteste corretivo pendente.

**Gravação:** 15/11/2026, 18:13 BRT. **Revisão documental:** 15/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Cadastrar um objetivo de treino pela tela Objetivos Treino e apresentá-lo na listagem, ou informar a validação específica para dados recusados, sem erro interno genérico. |
| Requisito | [RF35](../Analise%20de%20requisitos.md#rf35), proposto a partir da evidência. |
| Tipo / prioridade | Funcional manual, análise de evidências / Alta, proposta para triagem. |
| Defeito | [BUG-018](../Relatorio-de-Bugs.md#bug-018), em triagem. |
| Encaminhamento | Investigar o HTTP 500 com logs do servidor; confirmar se o campo Código é automático; retestar com dados válidos e recusados e conferir a persistência. |
| Fonte | [Jam — Objetivos Treino](https://jam.dev/c/1d474477-2411-4a81-b85c-74207402b783) e [evidências locais](../Evidencias/CT-RF35_Cadastro_Objetivo_Treino/README.md). |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/objetivos-treino |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.78 / Windows (x86) 11. |
| Tela / arquivo de vídeo | 1920 × 911 informados no Jam; vídeo de 1516 × 720. |
| Duração | 1 min 12 s |
| Rede | Classificada como rápida no Jam: 8,8 Mbps, latência de 100 ms. |
| Localização | Brasil. |
| Servidor | Resposta com `x-powered-by: PHP/8.2.35`, `server: hcdn`, `platform: hostinger`. |
| Usuário exibido | Jair, conforme o canto superior direito da tela. |
| Versão / zoom / classificação do ambiente | Não confirmados; registrar antes de nova execução. |
| Dados | Base sem objetivos cadastrados (cartões Objetivos 0, Exibidos 0 e Com Descrição 0). Nome "Gustavo" e descrição "Gustavo 45254#@v" como referência histórica; usar dados de teste autorizados em nova execução. |

## Pré-condições

- Sessão autenticada com acesso à tela Objetivos Treino e à ação Novo Objetivo.
- Nome de objetivo de teste disponível, sem conflito com registros existentes.
- Estado inicial da listagem e dos cartões de resumo registrado antes da inclusão.
- Confirmar com o produto se o campo Código é atribuído automaticamente e se a descrição aceita caracteres especiais.
- Antes de uma nova execução, identificar versão, permissões e dados de referência e preparar a captura de interface e rede.

## Cenário BDD

O BDD descreve o comportamento esperado; não representa aprovação ou nova execução.

```gherkin
Cenário: Cadastrar um objetivo de treino com dados válidos
  Dado que o usuário está autenticado na tela Objetivos Treino
  E a listagem apresenta o estado inicial conhecido
  Quando abrir o formulário "Novo Objetivo"
  E informar um nome e uma descrição válidos
  E clicar em "Salvar"
  Então o sistema deve criar o objetivo
  E apresentar o novo registro na listagem
  E atualizar os cartões de resumo

Cenário: Tratar dados recusados no cadastro de objetivo
  Dado que o cadastro contém um dado que o sistema não aceita
  Quando o usuário tentar salvar
  Então o sistema deve informar a validação específica
  E deve permitir corrigir os dados sem responder com erro interno HTTP 500
```

## Passos observados para reprodução

1. Acessar Objetivos Treino e registrar a listagem e os cartões.
2. Clicar em Novo Objetivo para abrir o formulário "Objetivo", com os campos Código, Nome e Descrição.
3. Informar o nome Gustavo no campo Nome e Gustavo 45254#@v no campo Descrição.
4. Clicar em Salvar e observar a interface e a resposta de rede.
5. Fechar o diálogo de erro e conferir a listagem.

Este procedimento orienta a próxima execução. Os valores acima pertencem à evidência histórica; variações de nome e descrição são comparações separadas, com resultado próprio.

## Resultado esperado

Cadastrar e confirmar o objetivo quando os dados forem válidos, apresentá-lo na listagem e atualizar os cartões; para dado recusado, informar a validação correspondente, sem HTTP 500.

## Resultado obtido na gravação

Ao clicar em Salvar, o sistema apresenta o diálogo "Erro" com o texto "Erro ao salvar objetivo". O formulário permanece ao fundo e, depois, a listagem continua sem registros. As requisições de gravação retornam HTTP 500.

**Momentos e registros:**

| Tempo | Registro |
| --- | --- |
| 0:00 | Tela Objetivos Treino: filtros Código e Nome, botões Buscar e Novo Objetivo; cartões Objetivos 0, Exibidos 0 e Com Descrição 0; "Nenhum objetivo cadastrado" e "0 registro(s)". |
| 0:02–0:10 | Alternância do tema (ícone de sol) e abertura do painel Notificações, com a mensagem "Nenhuma pendente por aqui. Você está em dia."; quatro POST de nome `tema` com HTTP 200. |
| 0:15–0:41 | Digitação nos filtros Código (4152, 14526, 15165) e Nome (Gustavo e variações), com acionamento de Buscar e da lupa. A listagem permanece vazia; ver observação sobre a busca. |
| 0:42 | Clique em Novo Objetivo; formulário "Objetivo" com Código, Nome e Descrição. |
| 0:44–0:52 | Digitação registrada no formulário ("15", "165", "9-561+651"); nos quadros de 0:46 e 0:52 o campo Código permanece vazio; ver observação sobre o Código. |
| 0:54–1:00 | Nome "Gustavo" e descrição "Gustavo 45254#@v". |
| 1:01 | Clique em Salvar (`button#submit-button`, `type="submit"`); `POST https://backendsifit.centrion.com.br/api/objetivo-treino/salvar/1` retorna **HTTP 500**. |
| 1:02 | Segunda ocorrência de POST 500 para o mesmo endpoint, sem novo clique em Salvar registrado na cronologia. |
| 1:04 | Diálogo "Erro" / "Erro ao salvar objetivo", com formulário ao fundo. |
| 1:05 | Clique no botão do diálogo de erro. |
| 1:06 | Clique em botão do formulário com `type="button"` (provavelmente Cancelar); o formulário se fecha. |
| 1:11 | Listagem sem registros: cartões em 0 e "Nenhum objetivo cadastrado". |

**Rede (nove entradas, todas no domínio `backendsifit.centrion.com.br`):** quatro POST `tema` com HTTP 200 (23 B); dois GET com HTTP 200 (2 B); POST com HTTP 500 (60 B, 1077 ms); OPTIONS com HTTP 204 (218 ms); POST com HTTP 500 (856 ms).

**Cabeçalhos de resposta da última entrada (POST de 856 ms):** `POST /api/objetivo-treino/salvar/1`, `content-type: application/json; charset=utf-8`, `content-length: 64`, `date: Sun, 15 Nov 2026 21:12:42 GMT`, `x-hcdn-request-id: dfcc75d79c00e3202a38d84598b45e4b-asc-edge13`. Autenticação omitida.

**Corpo da requisição e da resposta:** o Jam informa "body unavailable" para a requisição e para a resposta; o conteúdo do payload e a mensagem retornada pelo servidor não foram capturados.

**Conclusão:** Reprovado pelo erro interno e pela ausência de confirmação no fluxo registrado. A validade dos dados não foi comprovada, mas uma rejeição de negócio deve ter tratamento controlado. A gravação não determina a causa raiz.

## Critérios de aceitação e matriz de reteste proposta

| Variação | Verificação esperada | Situação |
| --- | --- | --- |
| Nome e descrição simples, sem caracteres especiais | Cadastro confirmado e um objetivo na listagem após nova consulta. | Pendente |
| Dados históricos do Jam em ambiente de teste (nome e descrição com `#@`) | Cadastro ou validação específica conforme a regra, sem HTTP 500. | Pendente |
| Descrição vazia e nome vazio | Validação por campo e ausência de registro vazio. | Pendente |
| Código informado manualmente | Aceitar e manter o valor, ou indicar que o campo é automático. | Pendente |
| Nome duplicado e limites de tamanho | Aplicar a regra confirmada e informar o impedimento. | Pendente |
| Um clique em Salvar | Uma única requisição de gravação e ausência de duplicidade no envio válido. | Pendente |

Identificar a versão corrigida, conferir a persistência antes de reenviar e anexar nova evidência antes de encerrar o BUG-018. As variações acima não entram na contagem de casos executados.

## Próxima ação e verificações complementares

Investigar o HTTP 500 com os logs do servidor, correlacionando o endpoint com 21:12:42 GMT de 15/11/2026 e o request ID registrado. Verificar o tratamento de caracteres especiais na descrição, o vínculo com a empresa informada no sufixo `/1` (significado não confirmado) e a razão das duas ocorrências de HTTP 500. Não houve inspeção do código, consulta ao banco, nova execução ou correção da aplicação.

## Observação sobre o campo Código

No formulário, o campo Código aparece focado nos quadros de 0:46 e 0:52 e permanece vazio, embora a cronologia registre digitação entre 0:44 e 0:52. Isso é compatível com um campo atribuído automaticamente pelo sistema, como se interpretou em [CT-RF31](CT-RF31_Cadastro_GrupoMuscular.md#observações-sobre-o-campo-código), mas também com o impedimento relatado em [CT-RF22](CT-RF22_Digitacao_Codigo_Exercicio.md) / [BUG-011](../Relatorio-de-Bugs.md#bug-011). A evidência não distingue as duas hipóteses: não foram confirmados o foco real, as teclas recebidas nem a regra do produto. Por isso o ponto permanece **a validar** e não gera defeito próprio.

## Observação sobre a busca e a lista vazia

Durante os filtros (0:15–0:41), a listagem não muda e mantém a mensagem "Nenhum objetivo cadastrado", a mesma exibida no início da gravação, sem filtro. Como a base estava vazia, os filtros por código e nome não puderam ser avaliados: qualquer critério produziria o mesmo resultado. A lista de rede também não registra uma requisição de consulta associada aos acionamentos de Buscar; as duas chamadas GET de 2 B podem corresponder ao carregamento inicial das listas, sem confirmação dos caminhos. Se a mensagem deve distinguir "nenhum cadastrado" de "nenhum encontrado para o filtro" é um ponto a confirmar com o responsável pelo produto, como em [CT-RF33](CT-RF33_Filtros_GruposMusculares.md).

## Evidências e limites

- [Jam original — Objetivos Treino](https://jam.dev/c/1d474477-2411-4a81-b85c-74207402b783).
- [Arquivos, origem e limites](../Evidencias/CT-RF35_Cadastro_Objetivo_Treino/README.md).
- [Formulário com o Código vazio em 0:46](../Evidencias/CT-RF35_Cadastro_Objetivo_Treino/formulario_codigo_vazio_00-46.png), [formulário preenchido em 1:00](../Evidencias/CT-RF35_Cadastro_Objetivo_Treino/formulario_preenchido_01-00.png), [diálogo de erro em 1:04](../Evidencias/CT-RF35_Cadastro_Objetivo_Treino/erro_01-04.png), [listagem vazia em 1:11](../Evidencias/CT-RF35_Cadastro_Objetivo_Treino/lista_vazia_01-11.png) e [lista de rede](../Evidencias/CT-RF35_Cadastro_Objetivo_Treino/rede_lista.png).
- [Linha do tempo](../Evidencias/CT-RF35_Cadastro_Objetivo_Treino/linha_do_tempo.txt).

Foram consultados os painéis Info, Console (atividade do usuário e erros de rede), Network e Actions do Jam, os cabeçalhos da requisição final e os quadros do vídeo. As capturas foram extraídas da reprodução do Jam e mostram o botão de reprodução sobreposto. O texto do diálogo de erro está parcialmente coberto pelo player; a leitura "Erro ao salvar objetivo" é aproximada. Não houve nova execução, inspeção do código, acesso ao banco ou correção da aplicação. O vídeo permanece no Jam. Causa raiz, persistência de registros parciais e regra do campo Código permanecem não confirmadas. O título automático do Jam ("Adjusting theme settings and viewing notifications") não descreve o fluxo de cadastro e não foi utilizado.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf35) · [Plano](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
