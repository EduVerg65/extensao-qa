# 🧪 Cenário 87: Filtro de leads por estágio e limpeza dos filtros

**Caso de teste:** CT-RF87

**Módulo:** Prospecção / Leads / Filtro por estágio

**Status:** Aprovado conforme a gravação.

**Gravação:** 15/11/2026, 21:52 BRT. **Revisão documental:** 15/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Filtrar a listagem de leads pelo seletor Estágio e restaurar a listagem completa com o botão Limpar. |
| Requisito | [RF87](../Analise%20de%20requisitos.md#rf87) — referência de QA; confirmação de produto pendente. |
| Tipo / prioridade | Funcional manual / regressão; Média, proposta para triagem. |
| Defeito | Nenhum no fluxo avaliado |
| Encaminhamento | Sem reteste corretivo pendente; manter como regressão. Confirmar os demais estágios e a combinação com a busca por texto. |
| Fonte | [Jam — Prospecção](https://jam.dev/c/308607ff-8abc-40af-8c7c-429ce506ed64) e [evidências locais](../Evidencias/CT-RF87_Filtro_Estagio_Leads/README.md). A mesma gravação é a fonte de [CT-RF85](CT-RF85_Tema_Notificacoes_Prospeccao.md), [CT-RF86](CT-RF86_Busca_Leads_Prospeccao.md), [CT-RF88](CT-RF88_Cadastro_Lead_Prospeccao.md), [CT-RF89](CT-RF89_Telefone_Lead_Sem_Validacao.md) e [CT-RF90](CT-RF90_Edicao_Lead_Prospeccao.md). |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/prospeccao |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.78 / Windows (x86) 11. |
| Tela / arquivo de vídeo | 1920 × 911 informados no Jam. |
| Duração | 1 min 2 s |
| Rede | Classificada como rápida no Jam: 5,4 Mbps, latência de 100 ms. |
| Localização | Brasil. |
| Usuário exibido | Jair, conforme o canto superior direito da tela. |
| Versão / zoom / classificação do ambiente | Não confirmados; registrar antes de nova execução. |
| Dados | Base com 7 leads (Novos Contatos 2 e Interessados 2); estágios exercitados: Novo Contato e Proposta. |

## Pré-condições

- Sessão autenticada com acesso à tela Prospecção.
- Base de leads conhecida, com códigos, nomes e estágios registrados antes da execução.
- Antes de uma nova execução, identificar versão, permissões e dados de referência e preparar a captura de interface e rede.

## Cenário BDD

```gherkin
Cenário: Filtrar leads por estágio
  Dado que a tela Prospecção apresenta a listagem completa de leads
  Quando o usuário selecionar um estágio no seletor Estágio
  Então a listagem deve apresentar apenas os leads do estágio escolhido
  E, ao acionar Limpar, a listagem completa deve voltar
```

## Passos para execução ou reteste

1. Acessar Prospecção e registrar a listagem completa e os cartões.
2. Selecionar cada estágio disponível e conferir as linhas e o estágio exibido em cada uma.
3. Combinar o estágio com um termo de busca.
4. Acionar Limpar e conferir que o seletor volta a Todos e a listagem é restaurada.
5. Selecionar um estágio sem leads e conferir a mensagem de resultado vazio.

Este procedimento orienta a próxima execução. A evidência atual cobre o trecho gravado e os limites descritos abaixo; passos complementares não recebem resultado de execução nesta revisão.

## Resultado esperado

Cada estágio selecionado apresenta apenas os leads correspondentes, o número de linhas coincide com o indicador do estágio e o botão Limpar restaura o seletor e a listagem completa.

## Resultado obtido na gravação

Com "Novo Contato" a listagem apresentou os dois leads dos códigos 7 e 8 (igual ao indicador Novos Contatos = 2); com "Proposta" apresentou um lead ("Teste A", código 4); após Limpar o seletor voltou a "Todos" e a listagem completa foi exibida.

| Tempo | Registro |
| --- | --- |
| 0:14–0:18 | Seletor Estágio acionado várias vezes; em 0:16 "Novo Contato" selecionado: listagem com os leads de códigos 7 e 8; indicador Novos Contatos 2. |
| 0:19–0:20 | Estágio "Proposta" selecionado em 0:19: listagem com um lead ("Teste A", código 4). |
| 0:21 | Clique em Limpar: seletor em "Todos" e listagem completa de 7 leads. |

**Rede:** a troca de estágio e o botão Limpar não geram requisição de rede; compatível com filtragem feita na própria tela, sem confirmação.

**Conclusão:** Aprovado conforme a gravação. O filtro por estágio retorna conjuntos coerentes com o indicador de Novos Contatos e o botão Limpar restaura a listagem completa. A aprovação se limita aos estágios gravados (Novo Contato e Proposta).

## Critérios de aceitação para nova execução

1. Cada estágio apresenta apenas os leads desse estágio.
2. O número de linhas de um estágio coincide com o indicador correspondente, quando existir.
3. O botão Limpar restaura o seletor para Todos e a listagem completa.
4. Um estágio sem leads apresenta mensagem explícita de resultado vazio.
5. O filtro combina corretamente com a busca por texto.

## Próxima ação e verificações complementares

Usar como regressão. Permanecem fora do cenário gravado: os demais estágios (como Interessado e Fechado, se existirem), estágio sem leads, combinação com busca por texto e persistência do filtro ao recarregar.

## Observação sobre os estágios disponíveis

O quadro de 0:19 e a cronologia mostram dez cliques no seletor, mas somente "Novo Contato" e "Proposta" foram conferidos em quadro; a lista completa de estágios do seletor não foi registrada.

## Evidências e limites

- [Jam original — Prospecção](https://jam.dev/c/308607ff-8abc-40af-8c7c-429ce506ed64).
- [Arquivos, origem e limites](../Evidencias/CT-RF87_Filtro_Estagio_Leads/README.md).
- [Filtro Novo Contato em 0:16](../Evidencias/CT-RF87_Filtro_Estagio_Leads/filtro_novo_contato_00-16.png), [Filtro Proposta em 0:19](../Evidencias/CT-RF87_Filtro_Estagio_Leads/filtro_proposta_00-19.png), [Listagem completa em 0:21 após Limpar](../Evidencias/CT-RF87_Filtro_Estagio_Leads/lista_apos_limpar_00-21.png), [Lista de rede](../Evidencias/CT-RF87_Filtro_Estagio_Leads/rede_lista.jpg).
- [Linha do tempo](../Evidencias/CT-RF87_Filtro_Estagio_Leads/linha_do_tempo.txt).

Foram consultados os painéis Info, Console, Network e Actions do Jam e os quadros do vídeo. As capturas foram extraídas da reprodução do Jam; quadros com o e-mail digitado no formulário não foram incluídos nem recortados com esse dado. Os demais estágios, a combinação com a busca por texto e o estágio sem leads não foram exercitados. Não houve nova execução, inspeção do código, acesso ao banco ou correção da aplicação. O vídeo permanece no Jam.

Análise documental da gravação consultada em 15/11/2026. Esta inclusão não executa novamente o sistema e não constitui reteste. Versão da aplicação, zoom e classificação do ambiente não foram confirmados.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf87) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
