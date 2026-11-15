# 🧪 Cenário 43: Criação de cobrança no painel Pagar.me

**Caso de teste:** CT-RF43

**Módulo:** Financeiro / Pagar.me / Cobrança

**Status:** Aprovado conforme a gravação.

**Gravação:** 15/11/2026, 19:06 BRT. **Revisão documental:** 15/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Criar uma cobrança informando descrição, valor e método de pagamento e confirmar o resultado ao usuário. |
| Requisito | [RF43](../Analise%20de%20requisitos.md#rf43) — referência de QA; confirmação de produto pendente. |
| Tipo / prioridade | Funcional manual / regressão; Média, proposta para triagem. |
| Defeito | Nenhum no fluxo avaliado |
| Encaminhamento | Sem reteste corretivo pendente; manter como regressão. Confirmar o comportamento de valores altos e descrições numéricas. |
| Fonte | [Jam — Pagar.me](https://jam.dev/c/e6e551ef-9196-4c79-b6a2-89747b1e8b33) e [evidências locais](../Evidencias/CT-RF43_Criacao_Cobranca_PagarMe/README.md). A mesma gravação é a fonte de [CT-RF42](CT-RF42_Solicitacao_Saque_PagarMe.md), [CT-RF44](CT-RF44_Configuracoes_Home_Salvamento.md) e [CT-RF45](CT-RF45_Painel_PagarMe_Periodo.md). |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/pagarme |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.78 / Windows (x86) 11. |
| Tela / arquivo de vídeo | 1920 × 911 informados no Jam. |
| Duração | 1 min 11 s |
| Rede | Classificada como rápida no Jam: 6,8 Mbps, latência de 50 ms. |
| Localização | Brasil. |
| Usuário exibido | Jair, conforme o canto superior direito da tela. |
| Versão / zoom / classificação do ambiente | Não confirmados; registrar antes de nova execução. |
| Dados | Descrição "11111", valor 11111 e método PIX como referência histórica. |

## Pré-condições

- Sessão autenticada com acesso ao módulo Pagar.me e à ação Nova cobrança.
- Conta de pagamento configurada para o método escolhido.
- Descrição e valor de teste autorizados, sem cobrança real indevida.
- Antes de uma nova execução, identificar versão, permissões e dados de referência e preparar a captura de interface e rede.

## Cenário BDD

```gherkin
Cenário: Criar uma cobrança pelo método PIX
  Dado que o usuário acessa Nova cobrança nas Ações rápidas do painel Pagar.me
  Quando informar a descrição, o valor e o método de pagamento
  E acionar Criar Cobrança
  Então o sistema deve criar a cobrança
  E informar o sucesso ao usuário
```

## Passos para execução ou reteste

1. Acessar o painel Pagar.me e acionar Nova cobrança em Ações rápidas.
2. Informar a descrição e o valor e escolher o método de pagamento.
3. Acionar Criar Cobrança.
4. Conferir a mensagem, a requisição e a presença da cobrança em Transações recentes.
5. Repetir com outros métodos e com dados inválidos.

Este procedimento orienta a próxima execução. A evidência atual cobre o trecho gravado e os limites descritos abaixo; passos complementares não recebem resultado de execução nesta revisão.

## Resultado esperado

A cobrança é criada e o sistema informa o sucesso de forma visível.

## Resultado obtido na gravação

A cobrança foi criada e o sistema apresentou a mensagem "Cobrança criada com sucesso!".

| Tempo | Registro |
| --- | --- |
| 0:22–0:26 | Clique em Nova cobrança nas Ações rápidas; formulário "Nova Cobrança" ("Criar link de pagamento via Pagar.me"). |
| 0:28–0:29 | Descrição "11111" e Valor (R$) 11111 digitados; método "PIX" selecionado. |
| 0:30 | Clique em Criar Cobrança: `OPTIONS` HTTP 204 e `POST` de nome `criar-cobranca` com HTTP 200 (56 ms); corpo e resposta indisponíveis no Jam. |
| 0:31 | Diálogo de sucesso com o texto "Cobrança criada com sucesso!" e botão de fechar. |

**Conclusão:** Aprovado conforme a gravação. A criação retorna HTTP 200 e o sistema informa o sucesso. A aprovação se limita ao exemplo gravado; não significa validação de todos os métodos de pagamento, valores e descrições.

## Critérios de aceitação para nova execução

1. O formulário permite informar descrição, valor e método de pagamento.
2. A criação retorna sucesso e a interface apresenta mensagem compreensível.
3. A cobrança passa a constar nos registros do módulo (por exemplo, Transações recentes) conforme a regra do produto.
4. Dados inválidos ou ausentes recebem validação específica.
5. A cobrança não é duplicada por cliques repetidos.

## Próxima ação e verificações complementares

Usar como regressão. Permanecem fora do cenário gravado: outros métodos (cartão, boleto), valor zero ou negativo, descrição vazia, visualização do link criado, duplicidade e a presença da cobrança em Transações recentes.

## Observação sobre o resultado visível

Após o diálogo de sucesso, o painel continua exibindo "Ver todas as transações" sem linhas em Transações recentes e os indicadores como "R$ --"; a gravação não mostra o link ou o código da cobrança criada. Esses pontos não foram avaliados como falha, pois a regra do produto não foi fornecida.

## Evidências e limites

- [Jam original — Pagar.me](https://jam.dev/c/e6e551ef-9196-4c79-b6a2-89747b1e8b33).
- [Arquivos, origem e limites](../Evidencias/CT-RF43_Criacao_Cobranca_PagarMe/README.md).
- [Formulário em 0:29](../Evidencias/CT-RF43_Criacao_Cobranca_PagarMe/nova_cobranca_00-29.png), [Mensagem em 0:31](../Evidencias/CT-RF43_Criacao_Cobranca_PagarMe/cobranca_sucesso_00-31.png), [Lista de rede](../Evidencias/CT-RF43_Criacao_Cobranca_PagarMe/rede_lista.png).
- [Linha do tempo](../Evidencias/CT-RF43_Criacao_Cobranca_PagarMe/linha_do_tempo.txt).

Foram consultados os painéis Info, Console, Network e Actions do Jam e os quadros do vídeo; o corpo da requisição e da resposta aparece como indisponível. As capturas foram extraídas da reprodução do Jam. Não foram verificados a presença da cobrança nos registros e o link gerado. Não houve nova execução, inspeção do código, acesso ao banco ou correção da aplicação. O vídeo permanece no Jam.

Análise documental da gravação consultada em 15/11/2026. Esta inclusão não executa novamente o sistema e não constitui reteste. Versão da aplicação, zoom e classificação do ambiente não foram confirmados.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf43) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
