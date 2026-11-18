# 🧪 Cenário 47: Solicitação de saque no painel Pagar.me

**Caso de teste:** CT-RF47

**Módulo:** Financeiro / Pagar.me / Saque

**Status:** A validar — regra ou contexto pendente.

**Gravação:** 15/11/2026, 19:06 BRT. **Revisão documental:** 15/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Solicitar um saque informando o valor e apresentar ao usuário o resultado da solicitação. |
| Requisito | [RF47](../Analise%20de%20requisitos.md#rf47) — referência de QA; confirmação de produto pendente. |
| Tipo / prioridade | Exploratório / regra a confirmar; Alta, proposta para triagem. |
| Defeito | Sem defeito confirmado. |
| Encaminhamento | Confirmar a regra de saque com saldo indisponível, o retorno esperado ao usuário e capturar corpo e resposta da requisição em nova execução; registrar defeito apenas se houver divergência com a regra definida. |
| Fonte | [Jam — Pagar.me](https://jam.dev/c/e6e551ef-9196-4c79-b6a2-89747b1e8b33) e [evidências locais](../Evidencias/CT-RF42_Solicitacao_Saque_PagarMe/README.md). A mesma gravação é a fonte de [CT-RF48](CT-RF48_Criacao_Cobranca_PagarMe.md), [CT-RF117](CT-RF117_Configuracoes_Home_Salvamento.md) e [CT-RF49](CT-RF49_Painel_PagarMe_Periodo.md). |

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
| Dados | Painel Pagar.me com os indicadores Disponível para saque, Em processamento, Recebíveis futuros e Recebido no mês exibidos como "R$ --" ou "--"; valor de saque 1000 como referência histórica. |

## Pré-condições

- Sessão autenticada com acesso ao módulo Pagar.me e conta de pagamento configurada.
- Saldo disponível conhecido antes da solicitação.
- Regra de saque (saldo mínimo, valor máximo, mensagem de retorno) definida com o produto.
- Antes de uma nova execução, identificar versão, permissões e dados de referência e preparar a captura de interface e rede.

## Cenário BDD

```gherkin
Cenário: Solicitar um saque com saldo disponível
  Dado que o painel Pagar.me apresenta o saldo disponível para saque
  Quando o usuário acionar Solicitar saque, informar o valor e confirmar
  Então o sistema deve registrar a solicitação
  E informar o resultado ao usuário
  E atualizar o saldo apresentado

Cenário: Solicitar um saque sem saldo disponível
  Dado que o saldo disponível não está disponível ou é insuficiente
  Quando o usuário confirmar a solicitação
  Então o sistema deve informar o impedimento de forma específica
```

## Passos para execução ou reteste

1. Acessar o painel Pagar.me e registrar os indicadores de saldo.
2. Acionar Solicitar saque; conferir o saldo disponível no formulário.
3. Informar o valor e acionar Confirmar saque.
4. Conferir a mensagem apresentada, o fechamento do formulário, o saldo e a requisição correspondente.
5. Repetir com valor superior ao saldo e com valor inválido.

Este procedimento orienta a próxima execução. A evidência atual cobre o trecho gravado e os limites descritos abaixo; passos complementares não recebem resultado de execução nesta revisão.

## Resultado esperado

A solicitação é registrada e o usuário recebe retorno claro (sucesso ou impedimento), com o saldo atualizado quando aplicável.

## Resultado obtido na gravação

Ao confirmar o saque, a requisição é enviada com sucesso (HTTP 200), mas a interface não apresenta mensagem de resultado e o saldo continua como "R$ --".

| Tempo | Registro |
| --- | --- |
| 0:00 | Painel Pagar.me com Disponível para saque "R$ --", Em processamento "R$ --", Recebíveis futuros "--" e Recebido no mês "--". |
| 0:01–0:03 | Clique em Solicitar saque; formulário "Solicitar Saque" com Saldo disponível "R$ --" e Valor do saque (R$) 1000. |
| 0:03 | Clique em Confirmar Saque: `OPTIONS` HTTP 204 e `POST` de nome `sacar-saldo` com HTTP 200 (84 ms); corpo e resposta indisponíveis no Jam. |
| 0:05 | Formulário fechado; nenhuma mensagem, diálogo ou indicação de resultado visível; os indicadores permanecem "R$ --". |

**Conclusão:** A validar. O envio retorna HTTP 200, mas o resultado da solicitação não é visível ao usuário nos quadros consultados e o saldo disponível aparece indisponível; não se registra defeito antes de confirmar a regra e o conteúdo da resposta.

## Critérios de aceitação para nova execução

1. A solicitação de saque informa o resultado (sucesso ou impedimento) de forma compreensível.
2. Com saldo indisponível ou insuficiente, o sistema apresenta o impedimento antes ou depois do envio, sem aceitar silenciosamente.
3. O valor informado é validado (mínimo, máximo e formato).
4. O saldo e os indicadores são atualizados após uma solicitação bem-sucedida.
5. A solicitação não é duplicada por cliques repetidos.

## Próxima ação e verificações complementares

Confirmar a regra com o responsável pelo produto e reexecutar com saldo conhecido, capturando corpo e resposta. Permanecem fora do cenário gravado: saldo suficiente, valor acima do saldo, valor inválido, mensagem de sucesso e atualização do saldo.

## Observação sobre os indicadores

Os quatro indicadores do topo do painel aparecem como "R$ --" ou "--" durante toda a gravação, enquanto o cartão Recebimentos apresenta R$ 38.420,00; essa diferença é tratada em [CT-RF49](CT-RF49_Painel_PagarMe_Periodo.md).

## Evidências e limites

- [Jam original — Pagar.me](https://jam.dev/c/e6e551ef-9196-4c79-b6a2-89747b1e8b33).
- [Arquivos, origem e limites](../Evidencias/CT-RF42_Solicitacao_Saque_PagarMe/README.md).
- [Painel em 0:00](../Evidencias/CT-RF42_Solicitacao_Saque_PagarMe/painel_00-00.png), [Formulário em 0:04](../Evidencias/CT-RF42_Solicitacao_Saque_PagarMe/saque_formulario_00-04.png), [Painel após o envio em 0:05](../Evidencias/CT-RF42_Solicitacao_Saque_PagarMe/apos_saque_00-05.png), [Lista de rede](../Evidencias/CT-RF42_Solicitacao_Saque_PagarMe/rede_lista.png).
- [Linha do tempo](../Evidencias/CT-RF42_Solicitacao_Saque_PagarMe/linha_do_tempo.txt).

Foram consultados os painéis Info, Console, Network e Actions do Jam e os quadros do vídeo; o corpo da requisição e da resposta de saque aparece como indisponível. As capturas foram extraídas da reprodução do Jam e mostram o botão de reprodução sobreposto. Não foram confirmados o resultado do saque, a regra de saldo e a mensagem de retorno. Não houve nova execução, inspeção do código, acesso ao banco ou correção da aplicação. O vídeo permanece no Jam.

Análise documental da gravação consultada em 15/11/2026. Esta inclusão não executa novamente o sistema e não constitui reteste. Versão da aplicação, zoom e classificação do ambiente não foram confirmados.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf47) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
