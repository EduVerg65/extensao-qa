## Cenário 3: Pesquisa de clientes com filtros combinados

### Caso de Teste 03: Aplicação simultânea dos filtros da página Clientes.

| ID | Descrição |
| --- | --- |
| **CT-RF03** | Verificar se a busca apresenta exclusivamente os clientes que atendem simultaneamente aos filtros selecionados de Código, Nome, Status, Situação Financeira, Plano e Personal. |

| **Pré-condições** |
| --- |
| Estar autenticado no SIFIT, com acesso à página Clientes e à empresa correspondente à pesquisa. O relato informa `empresa_id: 1`. |
| Ter disponíveis as opções Ativo, Inativo, Adimplente, Inadimplente, Plano Hendreu e Marcelo Longo Zandonadi. Confirmar os identificadores reais antes do reteste. |
| Preparar uma base de teste com status, situação financeira, plano e personal conhecidos por cliente, incluindo registros que atendam a todas as condições e registros que atendam apenas a parte delas. |
| Registrar URL da página, versão da aplicação, navegador, resolução e zoom. Essas informações não foram confirmadas para esta execução. |
| Preparar Network (Rede) e Console antes da busca, habilitando a captura e limpando o histórico. Preservar evidências sem tokens ou credenciais. |

| **Passos** |
| --- |
| **DADO** que estamos na página Clientes com uma base de teste conhecida |
| **E** os campos Código e Nome estão vazios, sem restringir a pesquisa |
| **E** selecionamos Status **Ativo** |
| **E** selecionamos Situação **Inadimplente** |
| **E** selecionamos Plano **Plano Hendreu** |
| **E** selecionamos Personal **Marcelo Longo Zandonadi** |
| **QUANDO** clicarmos em **Buscar** |
| **ENTÃO** a tabela deve apresentar somente clientes que atendam às quatro condições simultaneamente, utilizando lógica **AND** |
| **E** cada registro deve ser conferido com a base de referência, incluindo os vínculos que não estejam visíveis na tabela |
| **QUANDO** alterarmos apenas a Situação para **Adimplente** e clicarmos novamente em **Buscar** |
| **ENTÃO** a tabela deve refletir a nova situação financeira, mantendo os demais critérios |
| **E** quando não houver correspondências, deve apresentar **"Nenhum cliente encontrado"** |

### Resultado esperado

A listagem deve corresponder à interseção de todos os critérios selecionados. Código e Nome, quando preenchidos, também devem restringir o resultado segundo as regras de correspondência definidas pelo produto. Campos sem restrição não devem excluir clientes. A tabela deve ser atualizada a cada busca e não deve manter resultados anteriores quando a nova pesquisa não tiver correspondências.

| **Resultado obtido** |
| --- |
| Segundo o relato, a busca com Ativo, Inadimplente, Plano Hendreu e Marcelo Longo Zandonadi continuou apresentando clientes de outros planos e registros incompatíveis com a seleção. |
| A alteração de Inadimplente para Adimplente manteve resultados praticamente iguais, apesar de os filtros permanecerem selecionados visualmente. |
| O relato da gravação informa três requisições, em aproximadamente 00:05, 00:20 e 00:28, para `POST https://backendsifit.centrion.com.br/api/clientesPorNome/1`, todas com HTTP 200 e respostas de aproximadamente 180,9 KB. |
| No corpo simplificado informado constam apenas `empresa_id` e `nome`; Status, Situação Financeira, Plano e Personal não aparecem. O token foi omitido. |
| As capturas mostram a interface com filtros selecionados e nomes de clientes na tabela, mas os valores dos filtros estão truncados e os vínculos de cada cliente não estão visíveis. Elas não comprovam isoladamente a incompatibilidade de cada registro. |

| **Status e rastreabilidade** |
| --- |
| **Resultado:** Reprovado conforme o relato fornecido; sem nova execução no sistema nesta revisão. |
| **Defeito associado:** [BUG-003](../Relatorio-de-Bugs.md#bug-003--filtros-combinados-da-página-clientes-não-restringem-a-listagem). |
| **Severidade / prioridade:** Alta / Alta, propostas para triagem pelo impacto na confiabilidade da consulta. |
| **Revisão documental:** 12/11/2026. Data da gravação, versão da aplicação e URL do frontend não confirmadas. |
| **Reteste:** Pendente após a correção. Nenhuma correção ou validação do código foi realizada. |

### Análise técnica das requisições

Corpo simplificado transcrito do relato, sem autenticação; não é uma exportação HAR nem o corpo integral capturado:

```json
{
  "empresa_id": 1,
  "nome": ""
}
```

Os quatro critérios selecionados não aparecem nesse corpo. Isso sustenta a hipótese de falha na integração dos filtros com a busca, mas não confirma a causa. É necessário inspecionar o código e o contrato da API para determinar se a filtragem deve ocorrer no servidor, no frontend ou em ambos. A ausência desses parâmetros não comprova, isoladamente, um defeito no backend; uma filtragem local correta poderia aplicar as condições após receber os dados.

HTTP 200 comprova apenas o processamento bem-sucedido da requisição em termos de HTTP, sem demonstrar a aplicação dos filtros. Tamanhos de resposta semelhantes também não comprovam conteúdo idêntico. Os horários e volumes são os informados pelo solicitante; não foi possível consultar diretamente a gravação nesta revisão. Veja a [origem e os limites das evidências](../Evidencias/CT-RF03_Filtros_Clientes/README.md).

### Possível causa e correção recomendada

**Hipótese não confirmada:** a função de busca pode estar capturando/enviando somente Nome, sem encaminhar os demais critérios, ou pode estar deixando de aplicar a filtragem local necessária. O repositório consultado contém documentação de QA; o código da aplicação e o contrato do endpoint não foram analisados.

1. Revisar a função executada por **Buscar** e os vínculos dos campos com o estado da aplicação, incluindo Código e Nome.
2. Confirmar os valores efetivos de Status e Situação e a correspondência entre rótulos e IDs de Plano e Personal, sem presumir que os exemplos sejam os IDs reais.
3. Verificar se o endpoint atual aceita todos os filtros. Se a busca ocorrer no servidor, encaminhá-los conforme o contrato e ajustar a API se necessário.
4. Se a aplicação filtrar no frontend, confirmar que recebeu dados suficientes e todos os atributos necessários. Filtrar apenas uma página de um conjunto paginado não garante o resultado completo.
5. Aplicar as condições por lógica **AND** e atualizar a tabela com a resposta da busca atual. Para conjunto vazio, exibir **"Nenhum cliente encontrado"**.
6. Executar a matriz de reteste e registrar os critérios enviados/aplicados e a conferência de cada cliente retornado.

Exemplo **ilustrativo**, sujeito ao contrato real da API; os nomes de parâmetros, os valores e os IDs abaixo **não foram validados**. Os IDs `60` e `36` não devem ser usados como correspondências confirmadas de Plano Hendreu e Marcelo Longo Zandonadi:

```json
{
  "empresa_id": 1,
  "nome": "",
  "status": "ativo",
  "situacao": "inadimplente",
  "plano_id": 60,
  "personal_id": 36
}
```

### Critérios de aceitação

| Critério | Condição para aprovação |
| --- | --- |
| Aplicação simultânea | Todos os clientes retornados atendem a **todos** os filtros selecionados; atender apenas a parte deles não é suficiente. |
| Completude | Todos os clientes esperados na base de teste são encontrados, considerando as demais páginas, caso haja paginação. |
| Alteração de seleção | Alternar Adimplente/Inadimplente e executar Buscar atualiza o resultado conforme a base conhecida, preservando os demais filtros. |
| Campos opcionais | Código e Nome restringem a busca quando preenchidos, conforme as regras acordadas; limpar filtros remove as respectivas restrições. |
| Sem correspondência | Exibir **"Nenhum cliente encontrado"**, sem manter linhas da pesquisa anterior. |
| Integração verificável | Na busca no servidor, conferir os parâmetros conforme o contrato; na busca local, comprovar a aplicação das condições sobre dados suficientes. HTTP 200, isoladamente, não aprova o teste. |
| Evidência de reteste | Registrar seleções, dados de referência, resultado e evidências de rede/interface sem autenticação. Encerrar o defeito somente após validação. |

### Matriz de reteste proposta

As combinações abaixo estão **pendentes de execução**. Usar dados conhecidos para demonstrar tanto a inclusão dos clientes esperados quanto a exclusão dos incompatíveis.

| Variação | Filtros | Conferência esperada |
| --- | --- | --- |
| 1 | Ativo + Plano Hendreu | Apenas clientes ativos vinculados ao plano selecionado. |
| 2 | Inativo + Plano Hendreu | Apenas clientes inativos vinculados ao plano selecionado. |
| 3 | Ativo + Inadimplente | Apenas clientes com os dois critérios. |
| 4 | Adimplente + Marcelo Longo Zandonadi | Apenas adimplentes vinculados ao personal selecionado. |
| 5 | Ativo + Inadimplente + Plano Hendreu + Marcelo Longo Zandonadi | Apenas clientes que atendam às quatro condições. |
| 6 | Mesma combinação da variação 5, trocando para Adimplente | Clientes compatíveis com a nova situação e os outros três critérios. |
| 7 | Combinação preparada sem correspondências | Mensagem de conjunto vazio e nenhuma linha residual. |
| 8 | Código de cliente conhecido + demais filtros; depois Nome conhecido + demais filtros | O cliente somente aparece quando também atende aos demais critérios. Confirmar a regra de correspondência de Nome antes da execução. |
| 9 | Limpar as restrições e buscar novamente | Resultado geral esperado para a empresa e as permissões da conta. |

### Evidências

- [Jam — gravação fornecida](https://jam.dev/c/657627ec-e7e2-455d-a505-9b2a26f44bf1) — referência da execução relatada; acesso direto indisponível nesta revisão.
- [Índice das evidências e cronologia de rede informada](../Evidencias/CT-RF03_Filtros_Clientes/README.md).
- [Captura 1 — filtros, listagem e uma requisição HTTP 200](../Evidencias/CT-RF03_Filtros_Clientes/filtros-clientes-01.png).
- [Captura 2 — filtros, listagem e painel de rede sem requisições listadas](../Evidencias/CT-RF03_Filtros_Clientes/filtros-clientes-02.png).
