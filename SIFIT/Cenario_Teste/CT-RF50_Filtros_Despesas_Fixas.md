# 🧪 Cenário 50: Filtros da tela Despesas Fixas por código e por nome

**Caso de teste:** CT-RF50

**Módulo:** Financeiro / Despesas Fixas / Filtros

**Status:** Aprovado conforme a gravação.

**Gravação:** 15/11/2026, 19:07 BRT. **Revisão documental:** 15/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Filtrar a listagem de despesas fixas por código e por nome, apresentando apenas os registros correspondentes e indicadores coerentes. |
| Requisito | [RF50](../Analise%20de%20requisitos.md#rf50) — referência de QA; confirmação de produto pendente. |
| Tipo / prioridade | Funcional manual / regressão; Média, proposta para triagem. |
| Defeito | Nenhum no fluxo avaliado |
| Encaminhamento | Sem reteste corretivo pendente; manter como regressão. Confirmar o contrato dos cartões e a combinação de critérios. |
| Fonte | [Jam — Despesas Fixas](https://jam.dev/c/a4bac99d-e436-4792-831e-8c3a875272bb) e [evidências locais](../Evidencias/CT-RF46_Filtros_Despesas_Fixas/README.md). A mesma gravação é a fonte de [CT-RF51](CT-RF51_Cadastro_Despesa_Fixa.md), [CT-RF52](CT-RF52_Exclusao_Despesa_Fixa.md) e [CT-RF53](CT-RF53_Edicao_Despesa_Fixa.md). |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/despesas-fixas |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.78 / Windows (x86) 11. |
| Tela / arquivo de vídeo | 1920 × 911 informados no Jam. |
| Duração | 52 s |
| Rede | Classificada como rápida no Jam: 6,8 Mbps, latência de 50 ms. |
| Localização | Brasil. |
| Usuário exibido | Jair, conforme o canto superior direito da tela. |
| Versão / zoom / classificação do ambiente | Não confirmados; registrar antes de nova execução. |
| Dados | Base com 16 despesas (15 ativas e 1 inativa), valor listado total R$ 8.060,00; filtros Código "1" (digitação de 10) e Nome "Teste". |

## Pré-condições

- Sessão autenticada com acesso à tela Despesas Fixas.
- Base conhecida, com códigos, nomes, status e recorrências registrados antes da execução.
- Antes de uma nova execução, identificar versão, permissões e dados de referência e preparar a captura de interface e rede.

## Cenário BDD

```gherkin
Cenário: Filtrar despesas fixas por código e por nome
  Dado que a tela Despesas Fixas apresenta a listagem completa
  Quando o usuário informar um critério de Código ou de Nome
  Então a listagem deve apresentar apenas as despesas correspondentes
  E o cartão Valor Listado deve corresponder às despesas apresentadas
  E, ao limpar o critério, a listagem completa deve voltar
```

## Passos para execução ou reteste

1. Acessar Despesas Fixas e registrar a listagem completa e os cartões.
2. Informar um código e conferir as linhas e o Valor Listado; limpar.
3. Informar um nome (parte do nome, com variação de maiúsculas) e conferir as linhas, o contador "registro(s)" e o Valor Listado; limpar.
4. Alternar os seletores Status e Recorrência e conferir a listagem.
5. Combinar critérios, incluindo uma combinação sem correspondência.

Este procedimento orienta a próxima execução. A evidência atual cobre o trecho gravado e os limites descritos abaixo; passos complementares não recebem resultado de execução nesta revisão.

## Resultado esperado

A listagem apresenta apenas os registros correspondentes aos critérios, os indicadores acompanham o conjunto exibido quando aplicável e a limpeza dos critérios restaura a listagem completa.

## Resultado obtido na gravação

Os filtros retornaram conjuntos coerentes com os critérios, e a listagem completa voltou ao limpar os campos.

| Tempo | Registro |
| --- | --- |
| 0:00 | Listagem completa com 16 despesas; cartões Despesas 16, Ativas 15, Inativas 1 e Valor Listado R$ 8.060,00. |
| 0:02–0:03 | Código "1" informado: lista as despesas de códigos 10 a 19 (por exemplo #10 Conta Gym, #11 Conta Gym, #12 Conta de água); Valor Listado R$ 7.626,00. |
| 0:07–0:11 | Nome "Teste" informado: duas linhas, #5 "Teste" e #7 "teste 323", ambas R$ 50,00; rodapé "2 registro(s)"; Valor Listado R$ 100,00; cartões Despesas, Ativas e Inativas mantêm 16, 15 e 1. |
| 0:13–0:19 | Cliques repetidos nos seletores Status e Recorrência; em 0:19 os critérios estão em "Todos" e "Todas" e a listagem completa é exibida (Valor Listado R$ 8.060,00). |
| 0:36–0:42 | Após o cadastro de uma despesa (CT-RF51), o filtro Nome "teste" retorna três linhas (#5, #7 e #23) com Valor Listado R$ 250,00. |

**Rede:** os filtros por código, nome, status e recorrência não geram requisição de rede; as duas chamadas de lista (2,6 KiB) ocorrem antes dos filtros, o que é compatível com filtragem feita na própria tela, sem confirmação.

**Conclusão:** Aprovado conforme a gravação. Os filtros por código e por nome retornam conjuntos coerentes, o cartão Valor Listado acompanha o conjunto filtrado e a listagem completa é restaurada. A aprovação se limita aos exemplos gravados; não significa validação de todas as combinações.

## Critérios de aceitação para nova execução

1. O filtro por código retorna as despesas cujo código corresponde ao critério.
2. O filtro por nome retorna as despesas cujo nome contém o critério, sem diferenciar maiúsculas de minúsculas.
3. O cartão Valor Listado e o rodapé acompanham o conjunto exibido.
4. A limpeza dos critérios restaura a listagem completa.
5. Combinações sem correspondência apresentam mensagem explícita de resultado vazio.

## Próxima ação e verificações complementares

Usar como regressão. Permanecem fora do cenário gravado: combinação de código e nome (incluindo critérios contraditórios), filtro por Status e por Recorrência com valores específicos, resultado vazio, caracteres especiais e paginação.

## Observação sobre os cartões de resumo

Com o filtro aplicado, apenas o cartão Valor Listado muda (R$ 7.626,00 e R$ 100,00), enquanto Despesas, Ativas e Inativas mantêm o total da base. O comportamento é coerente entre os quadros conferidos, mas o contrato de cada indicador não foi fornecido, do mesmo modo que em [CT-RF15](CT-RF15_Metricas_Financeiro.md) e [CT-RF32](CT-RF32_Filtros_GruposMusculares.md).

## Observação sobre o filtro de código

O critério de código "1" retorna os códigos 10 a 19, o que indica correspondência parcial (por prefixo ou conteúdo); a regra pretendida não foi fornecida. O resultado do critério "10" não teve quadro consultado.

## Evidências e limites

- [Jam original — Despesas Fixas](https://jam.dev/c/a4bac99d-e436-4792-831e-8c3a875272bb).
- [Arquivos, origem e limites](../Evidencias/CT-RF46_Filtros_Despesas_Fixas/README.md).
- [Filtro de código em 0:03](../Evidencias/CT-RF46_Filtros_Despesas_Fixas/filtro_codigo_00-03.png), [Filtro de nome em 0:11](../Evidencias/CT-RF46_Filtros_Despesas_Fixas/filtro_nome_00-11.png), [Listagem completa em 0:19](../Evidencias/CT-RF46_Filtros_Despesas_Fixas/lista_completa_00-19.png), [Filtro de nome "teste" em 0:42](../Evidencias/CT-RF46_Filtros_Despesas_Fixas/filtro_teste_00-42.png), [Lista de rede](../Evidencias/CT-RF46_Filtros_Despesas_Fixas/rede_lista.png).
- [Linha do tempo](../Evidencias/CT-RF46_Filtros_Despesas_Fixas/linha_do_tempo.txt).

Foram consultados os painéis Info, Console, Network e Actions do Jam e os quadros do vídeo. As capturas foram extraídas da reprodução do Jam. A listagem completa da base não foi conferida registro a registro, nem houve consulta ao banco; o resultado do critério de código "10" e a combinação de critérios não foram exercitados. Não houve nova execução, inspeção do código, acesso ao banco ou correção da aplicação. O vídeo permanece no Jam.

Análise documental da gravação consultada em 15/11/2026. Esta inclusão não executa novamente o sistema e não constitui reteste. Versão da aplicação, zoom e classificação do ambiente não foram confirmados.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf50) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
