# 🧪 Cenário 45: Painel Pagar.me mantém Recebimentos e gráfico ao trocar o período

**Caso de teste:** CT-RF45

**Módulo:** Financeiro / Pagar.me / Painel

**Status:** Reprovado nas evidências — recebimentos e gráfico não mudam com o período; defeito em triagem.

**Gravação:** 15/11/2026, 19:06 BRT. **Revisão documental:** 15/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Apresentar recebimentos e meios de pagamento correspondentes ao período selecionado e indicadores de saldo coerentes com os dados do painel. |
| Requisito | [RF45](../Analise%20de%20requisitos.md#rf45) — referência de QA; confirmação de produto pendente. |
| Tipo / prioridade | Funcional manual / manifestação observada; Média, proposta para triagem. |
| Defeito | [BUG-021](../Relatorio-de-Bugs.md#bug-021), em triagem. |
| Encaminhamento | Confirmar se o painel utiliza dados reais ou de demonstração, investigar a atualização por período e a origem dos indicadores "R$ --"; retestar com conta de pagamento com movimentação conhecida. |
| Fonte | [Jam — Pagar.me](https://jam.dev/c/e6e551ef-9196-4c79-b6a2-89747b1e8b33) e [evidências locais](../Evidencias/CT-RF45_Painel_PagarMe_Periodo/README.md). A mesma gravação é a fonte de [CT-RF42](CT-RF42_Solicitacao_Saque_PagarMe.md), [CT-RF43](CT-RF43_Criacao_Cobranca_PagarMe.md) e [CT-RF44](CT-RF44_Configuracoes_Home_Salvamento.md). |

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
| Dados | Painel Pagar.me com o seletor de período em "Últimos 30 dias" e depois em "Últimos 7 dias"; cartão Recebimentos com R$ 38.420,00 (variação positiva vs período anterior); indicadores de saldo em "R$ --". |

## Pré-condições

- Sessão autenticada com acesso ao módulo Pagar.me.
- Conta de pagamento com movimentação conhecida nos últimos 30 e 7 dias.
- Regra de apuração de Recebimentos, Meios de pagamento e variação definida com o produto.
- Antes de uma nova execução, identificar versão, permissões e dados de referência e preparar a captura de interface e rede.

## Cenário BDD

```gherkin
Cenário: Atualizar Recebimentos ao trocar o período
  Dado que o painel apresenta o cartão Recebimentos para os últimos 30 dias
  Quando o usuário selecionar os últimos 7 dias
  Então o valor, o gráfico e a variação devem corresponder ao novo período
  E o eixo do gráfico deve apresentar as datas do período selecionado
```

## Passos para execução ou reteste

1. Acessar o painel Pagar.me e registrar Recebimentos, o gráfico, o eixo de datas e os meios de pagamento no período padrão.
2. Selecionar outro período no seletor do cartão Recebimentos.
3. Conferir o valor, a variação, o gráfico, o eixo e os meios de pagamento.
4. Comparar com os dados reais da conta no mesmo período.
5. Conferir a coerência com os indicadores de saldo.

Este procedimento orienta a próxima execução. A evidência atual cobre o trecho gravado e os limites descritos abaixo; passos complementares não recebem resultado de execução nesta revisão.

## Resultado esperado

Ao trocar o período, o valor, a variação, o gráfico e o eixo de datas passam a representar o novo período, de forma coerente com os demais indicadores.

## Resultado obtido na gravação

Com o seletor em "Últimos 7 dias" (0:25), o cartão Recebimentos permanece em R$ 38.420,00 e o gráfico é idêntico ao do período "Últimos 30 dias"; os indicadores de saldo permanecem "R$ --".

| Tempo | Registro |
| --- | --- |
| 0:00 | Painel com seletor "Últimos 30 dias"; Recebimentos R$ 38.420,00 (variação positiva vs período anterior); gráfico de linha com eixo de datas em formato dd/mm; Meios de pagamento: Cartão de crédito 62%, PIX 23%, Boleto 10%, Recorrência 3% e Outros 2%, com total R$ 38.420,00. |
| 0:00–0:20 | Indicadores Disponível para saque, Em processamento, Recebíveis futuros e Recebido no mês em "R$ --" / "--"; Transações recentes sem linhas. |
| 0:15–0:25 | Série de `POST` de nomes `ver-saldo`, `pagarme`, `recebiveis` e `transacoes` (HTTP 200), repetida a cada interação; corpos indisponíveis. |
| 0:25 | Seletor em "Últimos 7 dias" (o clique não consta na cronologia); Recebimentos permanece R$ 38.420,00, com o mesmo gráfico e o mesmo eixo de datas. |
| 0:29–0:31 | Painel inalterado durante a criação de cobrança (ver CT-RF43). |

**Conclusão:** Reprovado nas evidências. O valor de Recebimentos, o gráfico e os meios de pagamento não mudam entre os períodos "Últimos 30 dias" e "Últimos 7 dias", e os indicadores de saldo permanecem indisponíveis. A causa não foi determinada: pode tratar-se de dados de demonstração ou de falha de atualização.

## Critérios de aceitação para nova execução

1. O seletor de período atualiza o valor de Recebimentos, a variação, o gráfico e o eixo de datas.
2. O eixo do gráfico apresenta datas compatíveis com o período selecionado e com a data atual.
3. Os meios de pagamento correspondem ao período e ao total apresentado.
4. Os indicadores de saldo apresentam valores quando a conta tem saldo, ou mensagem explícita de indisponibilidade.
5. Valores de demonstração, se existirem, são identificados como tal.

## Próxima ação e verificações complementares

Reproduzir com uma conta com movimentação conhecida, capturando corpo e resposta de `recebiveis`, `transacoes` e `pagarme`, e comparar os períodos. Permanecem fora do cenário gravado: períodos adicionais, conta sem movimentação e a origem de "R$ --".

## Observação sobre as datas do gráfico

O eixo do gráfico apresenta datas em formato dd/mm que, na leitura aproximada do quadro, vão de 01/05 a 31/05, enquanto a gravação é de 15/11/2026 com o período "Últimos 30 dias". A leitura é limitada pela resolução do quadro e deve ser confirmada na reprodução; o ponto reforça a hipótese de dados estáticos.

## Evidências e limites

- [Jam original — Pagar.me](https://jam.dev/c/e6e551ef-9196-4c79-b6a2-89747b1e8b33).
- [Arquivos, origem e limites](../Evidencias/CT-RF45_Painel_PagarMe_Periodo/README.md).
- [Painel em 0:00](../Evidencias/CT-RF45_Painel_PagarMe_Periodo/painel_00-00.png), [Painel em 0:25](../Evidencias/CT-RF45_Painel_PagarMe_Periodo/painel_periodo_7dias_00-25.png), [Lista de rede](../Evidencias/CT-RF45_Painel_PagarMe_Periodo/rede_lista.png).
- [Linha do tempo](../Evidencias/CT-RF45_Painel_PagarMe_Periodo/linha_do_tempo.txt).

Foram consultados os painéis Info, Console, Network e Actions do Jam e os quadros do vídeo; os corpos de requisição e de resposta não foram capturados. As capturas foram extraídas da reprodução do Jam. A leitura do eixo de datas é aproximada. Não foi confirmado se o painel usa dados reais ou de demonstração. Não houve nova execução, inspeção do código, acesso ao banco ou correção da aplicação. O vídeo permanece no Jam.

Análise documental da gravação consultada em 15/11/2026. Esta inclusão não executa novamente o sistema e não constitui reteste. Versão da aplicação, zoom e classificação do ambiente não foram confirmados.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf45) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
