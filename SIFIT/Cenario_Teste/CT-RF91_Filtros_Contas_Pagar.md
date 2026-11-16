# 🧪 Cenário 91: Filtros da tela Contas a Pagar por nome, data e status

**Caso de teste:** CT-RF91

**Módulo:** Financeiro / Contas a Pagar / Filtros

**Status:** A validar — regra ou contexto pendente.

**Gravação:** 15/11/2026, 21:58 BRT. **Revisão documental:** 15/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Filtrar a listagem de contas a pagar por código, nome (fornecedor ou colaborador), tipo de data, período e status, apresentando apenas as contas correspondentes e indicadores coerentes. |
| Requisito | [RF91](../Analise%20de%20requisitos.md#rf91) — referência de QA; confirmação de produto pendente. |
| Tipo / prioridade | Exploratório / regra a confirmar; Média, proposta para triagem. |
| Defeito | Sem defeito confirmado. |
| Encaminhamento | Reexecutar com dados de controle (contas com datas de vencimento e de pagamento conhecidas) e conferir cada critério isoladamente e combinado; hoje o resultado vazio não pode ser conferido contra a base. |
| Fonte | [Jam — Contas a Pagar](https://jam.dev/c/5d0afaf4-5abd-4e85-923f-27448304a9ef) e [evidências locais](../Evidencias/CT-RF91_Filtros_Contas_Pagar/README.md). A mesma gravação é a fonte de [CT-RF92](CT-RF92_Cadastro_Conta_Colaborador_Sem_Colaborador.md), [CT-RF93](CT-RF93_Busca_Colaborador_Conta_Pagar.md), [CT-RF94](CT-RF94_Visualizacao_Conta_Pagar.md) e [CT-RF95](CT-RF95_Exclusao_Conta_Pagar.md). |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/contas-pagar |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.78 / Windows (x86) 11. |
| Tela / arquivo de vídeo | 1920 × 911 informados no Jam. |
| Duração | 1 min |
| Rede | Classificada como rápida no Jam: 7,8 Mbps, latência de 50 ms. |
| Localização | Brasil. |
| Usuário exibido | Jair, conforme o canto superior direito da tela. |
| Versão / zoom / classificação do ambiente | Não confirmados; registrar antes de nova execução. |
| Dados | Base com 2 contas listadas no início (códigos 27 e 28, pagas); filtros: Nome "teste", Tipo de Data "Pagamento", período 06/11/2026 a 06/11/2026 e Status "Pago". |

## Pré-condições

- Sessão autenticada com acesso à tela Contas a Pagar.
- Base de contas a pagar conhecida (contas de código 27 e 28 no início da gravação), com fornecedores, colaboradores, categorias e locais de pagamento cadastrados.
- Antes de uma nova execução, identificar versão, permissões e dados de referência e preparar a captura de interface e rede.

## Cenário BDD

```gherkin
Cenário: Filtrar contas a pagar
  Dado que a tela Contas a Pagar apresenta a listagem do período
  Quando o usuário informar nome, tipo de data, período e status e acionar Buscar
  Então a listagem deve apresentar apenas as contas que atendam a todos os critérios
  E os cartões Contas Listadas e Total a Pagar devem corresponder ao conjunto exibido
```

## Passos para execução ou reteste

1. Acessar Contas a Pagar e registrar a listagem e os cartões do período inicial.
2. Informar um nome (parte do fornecedor ou colaborador) e acionar Buscar.
3. Alternar Tipo de Data (Vencimento e Pagamento), informar o período e o status e acionar Buscar.
4. Combinar todos os critérios e conferir a listagem, o rodapé "Mostrando x a y de z contas" e os cartões.
5. Repetir com um critério sem correspondência e conferir a mensagem de resultado vazio.

Este procedimento orienta a próxima execução. A evidência atual cobre o trecho gravado e os limites descritos abaixo; passos complementares não recebem resultado de execução nesta revisão.

## Resultado esperado

A listagem apresenta apenas as contas que atendem a todos os critérios, os cartões acompanham o conjunto exibido e o resultado vazio é indicado de forma explícita.

## Resultado obtido na gravação

Com Nome "teste", Tipo de Data "Pagamento", período 06/11/2026 a 06/11/2026 e Status "Pago", a listagem ficou vazia ("Mostrando 0 a 0 de 0 contas") e os cartões foram a 0; a requisição de listagem devolveu 2 B. Não há dado de controle para confirmar se o vazio é o resultado correto.

| Tempo | Registro |
| --- | --- |
| 0:00–0:03 | Listagem inicial com duas contas pagas (códigos 27 e 28); cartões Total a Pagar 0, Valor Pago 0, Contas Listadas 2 e Contas Atrasadas 0; Nome "teste" digitado em 0:02, ainda sem busca. |
| 0:04–0:12 | Alternados Tipo de Data (Pagamento) e Status (Pago) e escolhido o período 06/11/2026 a 06/11/2026; clique em Buscar em 0:12. |
| 0:12 | Resultado: nenhuma conta listada, cartões em 0 e rodapé "Mostrando 0 a 0 de 0 contas". |

**Conclusão:** A validar — regra ou contexto pendente. O resultado vazio é compatível com os critérios (nenhuma das duas contas visíveis tem nome contendo "teste"), mas não houve controle de dados nem teste de cada critério isolado, e o corpo da busca principal não foi capturado.

## Critérios de aceitação para nova execução

1. Cada critério isolado (nome, tipo de data, período e status) filtra corretamente a listagem.
2. A combinação de critérios aplica todos eles simultaneamente.
3. Os cartões acompanham o conjunto exibido conforme o contrato definido.
4. O resultado vazio apresenta mensagem explícita.
5. Limpar os critérios restaura a listagem do período.

## Próxima ação e verificações complementares

Reexecutar com contas de controle (datas de vencimento e pagamento conhecidas), exercitando cada critério isolado, a troca de Tipo de Data e a combinação; conferir o corpo das requisições de listagem.

## Evidências e limites

- [Jam original — Contas a Pagar](https://jam.dev/c/5d0afaf4-5abd-4e85-923f-27448304a9ef).
- [Arquivos, origem e limites](../Evidencias/CT-RF91_Filtros_Contas_Pagar/README.md).
- [Filtro de nome digitado em 0:03](../Evidencias/CT-RF91_Filtros_Contas_Pagar/filtro_nome_00-03.png), [Filtros aplicados em 0:12](../Evidencias/CT-RF91_Filtros_Contas_Pagar/filtros_vazio_00-12.png), [Lista de rede](../Evidencias/CT-RF91_Filtros_Contas_Pagar/rede_lista.jpg).
- [Linha do tempo](../Evidencias/CT-RF91_Filtros_Contas_Pagar/linha_do_tempo.txt).

Foram consultados os painéis Info, Console, Network e Actions do Jam e os quadros do vídeo. As capturas foram extraídas da reprodução do Jam. Não houve nova execução, inspeção do código, acesso ao banco ou correção da aplicação. O vídeo permanece no Jam.

Análise documental da gravação consultada em 15/11/2026. Esta inclusão não executa novamente o sistema e não constitui reteste. Versão da aplicação, zoom e classificação do ambiente não foram confirmados.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf91) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
