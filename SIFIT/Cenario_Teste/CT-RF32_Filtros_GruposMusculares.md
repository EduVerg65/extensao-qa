# 🧪 Cenário 32: Filtros da tela Grupos Musculares

**Caso de teste:** CT-RF32

**Módulo:** Treinamento / Grupos Musculares

**Status:** Aprovado conforme a gravação.

**Gravação:** 15/11/2026, 15h56 BRT. **Revisão documental:** 15/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Filtrar a listagem por código e por tipo de membro, apresentando apenas os registros correspondentes e uma contagem coerente. |
| Requisito | [RF32](../Analise%20de%20requisitos.md#rf32) |
| Tipo / prioridade | Funcional manual, análise de evidências / Média, proposta para triagem. |
| Defeito | Nenhum no fluxo avaliado |
| Encaminhamento | Sem reteste corretivo pendente; manter como regressão. |
| Fonte | [Jam — Tela de Grupos Musculares](https://jam.dev/c/98008390-0040-475e-ba7b-7f1e72cc0b2e) |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/grupos-musculares |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.78 / Windows (x86) 11. |
| Tela / arquivo de vídeo | 1920 × 911 informados no Jam. |
| Duração | 2 min 3 s |
| Rede | Classificada como rápida no Jam: mais de 10 Mbps, latência de 50 ms. |
| Localização | Brasil. |
| Versão / zoom / classificação do ambiente | Não confirmados; registrar antes de nova execução. |
| Dados | Usar uma base conhecida, com a quantidade de registros por tipo de membro registrada antes da execução. |

## Pré-condições

- Sessão autenticada com acesso à tela Grupos Musculares.
- Base com registros conhecidos, incluindo ao menos um tipo de membro sem nenhum registro associado, para exercitar o resultado vazio.
- Antes de uma nova execução, identificar versão, permissões e dados de referência e preparar a captura de interface e rede.

## Cenário BDD

```gherkin
Cenário: Filtrar grupos musculares por código e por tipo de membro
  Dado que a tela Grupos Musculares apresenta a listagem completa
  Quando o usuário informar um critério de busca
  Então a listagem deve apresentar apenas os registros correspondentes
  E a contagem do rodapé deve corresponder aos registros apresentados
  E, quando não houver correspondência, o sistema deve informar o resultado vazio
```

## Passos para execução ou reteste

1. Acessar a tela Grupos Musculares e registrar a listagem completa e a contagem do rodapé.
2. Selecionar um tipo de membro sem registros associados e acionar a busca; conferir a mensagem de resultado vazio.
3. Selecionar um tipo de membro com registros e acionar a busca; conferir os registros e a contagem.
4. Informar um código existente no campo correspondente e acionar a busca; conferir o registro retornado.
5. Combinar código e tipo de membro em uma mesma busca e conferir o resultado.
6. Limpar os critérios e conferir o retorno da listagem completa.

Este procedimento orienta a próxima execução. A evidência atual cobre o trecho gravado e os limites descritos abaixo; passos complementares, como a limpeza dos critérios e a combinação com conjuntos maiores, não recebem resultado de execução nesta revisão.

## Resultado esperado

A listagem apresenta apenas os registros correspondentes aos critérios, a contagem do rodapé corresponde ao conjunto apresentado e o resultado vazio é informado de forma explícita.

## Resultado obtido na gravação

Os filtros exercitados retornaram conjuntos coerentes com os critérios, com a contagem do rodapé correspondente.

| Tempo | Critério | Resultado apresentado |
| --- | --- | --- |
| 0:15 | Tipo Membro "Aerobio", com quatro registros ainda não existentes e nenhum do tipo | "Nenhum grupo muscular encontrado" e rodapé "Mostrando 0 a 0 de 0 grupos". |
| 1:45 | Tipo Membro "Aerobio" | Uma linha: código 6, "Tríceps", "Aerobio". Rodapé "Mostrando 1 a 1 de 1 grupos". |
| 1:53–1:55 | Código "1" informado e botão de busca acionado | Ação registrada na cronologia; quadro do resultado não consultado. |
| 1:56–1:59 | Código corrigido para "2" e botão de busca acionado | Uma requisição de imagem registrada em 1:59. |
| 2:00 | Código "2" com Tipo Membro "Inferiores" | Uma linha: código 2, "Pernas", "Inferiores". Rodapé "Mostrando 1 a 1 de 1 grupos". |

**Conclusão:** Aprovado conforme a gravação. Os critérios exercitados retornam conjuntos coerentes, o rodapé acompanha o conjunto apresentado e o estado sem resultados é informado. A aprovação se limita aos exemplos gravados; não significa validação de todas as combinações.

## Critérios de aceitação para nova execução

1. A busca por tipo de membro retorna apenas registros daquele tipo.
2. A busca por código retorna o registro correspondente.
3. A contagem do rodapé corresponde aos registros apresentados.
4. A ausência de correspondência apresenta mensagem explícita, e não uma listagem vazia sem aviso.
5. A limpeza dos critérios restaura a listagem completa.

## Próxima ação e verificações complementares

Usar como regressão. Permanecem fora do cenário gravado: busca por nome, código inexistente, código inválido ou não numérico, caracteres especiais, combinações com conjuntos de mais de uma linha, paginação do resultado filtrado e limpeza dos critérios.

## Observação sobre a combinação de critérios

No quadro de 2:00 os campos Código "2" e Tipo Membro "Inferiores" estão preenchidos ao mesmo tempo e o resultado atende aos dois critérios. Isso é compatível com a aplicação combinada dos filtros, mas não a comprova: o único registro de código 2 também é do tipo selecionado, de modo que o mesmo resultado seria obtido aplicando apenas um dos critérios.

A verificação da lógica combinada exige um caso em que os critérios se contradigam — por exemplo, um código existente com um tipo de membro ao qual ele não pertence, cujo retorno esperado é o conjunto vazio. Esse caso não foi exercitado. A observação é relevante porque o comportamento de filtros combinados é justamente o ponto reprovado em [CT-RF09](CT-RF09_FILTRO_TelaClientes.md).

## Observação sobre os cartões de resumo

Nos quadros de 1:45 e 2:00 a listagem apresenta uma única linha, enquanto os cartões mantêm Grupos cadastrados 4, Superiores 0, Inferiores 3 e Aeróbio 1. Os cartões, portanto, não acompanham o filtro e representam o total da base, enquanto o rodapé acompanha o conjunto filtrado.

O comportamento é coerente entre os quadros conferidos e não configura divergência. O contrato de cada indicador, no entanto, não foi fornecido; a distinção entre indicadores globais e indicadores filtrados permanece como ponto a confirmar com o responsável pelo produto, do mesmo modo que em [CT-RF15](CT-RF15_Metricas_Financeiro.md).

## Evidências e limites

- [Jam original — Tela de Grupos Musculares](https://jam.dev/c/98008390-0040-475e-ba7b-7f1e72cc0b2e).
- Painel Console do Jam, visão de atividade do usuário: cronologia das seleções, digitação e acionamentos de busca.
- Quadros consultados: 0:15, 1:45 e 2:00.
- Pasta local de evidências: a criar em `Evidencias/CT-RF33_Filtros_GruposMusculares/`; até lá, a fonte é o Jam indicado acima.

A cronologia não registra as requisições de consulta com os respectivos códigos de status para este fluxo; as conclusões apoiam-se nos quadros e no rodapé de contagem. O resultado da busca pelo código "1" não teve quadro consultado e está registrado apenas como ação. A composição completa da base em cada momento não foi conferida registro a registro, nem houve consulta ao banco de dados. A limpeza dos critérios e o retorno à listagem completa não foram exercitados.

Análise documental da gravação consultada em 15/11/2026, com leitura direta dos painéis do Jam. Esta inclusão não executa novamente o sistema, não corrige a aplicação e não constitui reteste. Versão da aplicação, zoom e classificação do ambiente não foram confirmados.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
