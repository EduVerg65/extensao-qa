# 🧪 Cenário 93: Busca de colaborador no cadastro de conta a pagar

**Caso de teste:** CT-RF93

**Módulo:** Financeiro / Contas a Pagar / Busca de colaborador

**Status:** A validar — regra ou contexto pendente.

**Gravação:** 15/11/2026, 21:58 BRT. **Revisão documental:** 15/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Buscar um colaborador pelo nome no modal Buscar Colaborador do cadastro de conta e selecioná-lo para preencher o favorecido. |
| Requisito | [RF93](../Analise%20de%20requisitos.md#rf93) — referência de QA; confirmação de produto pendente. |
| Tipo / prioridade | Exploratório / regra a confirmar; Média, proposta para triagem. |
| Defeito | Sem defeito confirmado. |
| Encaminhamento | Reexecutar com o nome de um colaborador cadastrado, conferir a tabela de resultados e a seleção, e registrar a mensagem de resultado vazio esperada. |
| Fonte | [Jam — Contas a Pagar](https://jam.dev/c/5d0afaf4-5abd-4e85-923f-27448304a9ef) e [evidências locais](../Evidencias/CT-RF93_Busca_Colaborador_Conta_Pagar/README.md). A mesma gravação é a fonte de [CT-RF91](CT-RF91_Filtros_Contas_Pagar.md), [CT-RF92](CT-RF92_Cadastro_Conta_Colaborador_Sem_Colaborador.md), [CT-RF94](CT-RF94_Visualizacao_Conta_Pagar.md) e [CT-RF95](CT-RF95_Exclusao_Conta_Pagar.md). |

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
| Dados | Termo digitado "sds" (sem colaborador correspondente conhecido); base de colaboradores não registrada. |

## Pré-condições

- Sessão autenticada com acesso à tela Contas a Pagar.
- Base de contas a pagar conhecida (contas de código 27 e 28 no início da gravação), com fornecedores, colaboradores, categorias e locais de pagamento cadastrados.
- Antes de uma nova execução, identificar versão, permissões e dados de referência e preparar a captura de interface e rede.

## Cenário BDD

```gherkin
Cenário: Buscar e selecionar um colaborador
  Dado que o modal Buscar Colaborador está aberto
  Quando o usuário informar o nome de um colaborador e acionar Pesquisar
  Então a tabela deve listar os colaboradores correspondentes com código e nome
  E, sem correspondência, deve apresentar mensagem de resultado vazio
```

## Passos para execução ou reteste

1. Acionar Nova Conta, escolher o tipo Pagto. Colaborador e acionar a lupa Pesquisar.
2. Informar o nome de um colaborador cadastrado e acionar Pesquisar.
3. Selecionar o colaborador e conferir o preenchimento dos campos Código e Colaborador.
4. Informar um nome sem correspondência e conferir a mensagem.
5. Fechar o modal e conferir que o formulário permanece intacto.

Este procedimento orienta a próxima execução. A evidência atual cobre o trecho gravado e os limites descritos abaixo; passos complementares não recebem resultado de execução nesta revisão.

## Resultado esperado

A tabela lista os colaboradores correspondentes; ao selecionar um deles, o formulário recebe código e nome; sem correspondência, uma mensagem de resultado vazio é apresentada.

## Resultado obtido na gravação

Com o termo "sds" a busca (`POST colaboradores/pornome/1`, HTTP 200, 2 B) devolveu lista vazia e o modal apresentou apenas o cabeçalho Código / Nome, sem mensagem de resultado vazio no quadro consultado. A seleção de um colaborador existente não foi exercitada.

| Tempo | Registro |
| --- | --- |
| 0:24 | Clique na lupa Pesquisar: abre o modal Buscar Colaborador. |
| 0:25–0:27 | Termo "sds" digitado e Pesquisar acionado; `POST colaboradores/pornome/1` devolve 2 B. |
| 0:26 | Modal com campo "Nome do colaborador", botões Buscar e Fechar e tabela Código / Nome sem linhas nem mensagem. |

**Rede:** `POST /api/colaboradores/pornome/1` (HTTP 200, 2 B) com o termo digitado; a resposta de 2 B é compatível com lista vazia.

**Conclusão:** A validar — regra ou contexto pendente. A busca sem correspondência devolve lista vazia sem mensagem visível; a busca com resultado e a seleção do colaborador não foram exercitadas.

## Critérios de aceitação para nova execução

1. A busca lista os colaboradores cujo nome contenha o termo.
2. A seleção preenche Código e Colaborador no formulário.
3. Sem correspondência, o modal apresenta mensagem explícita.
4. O modal pode ser fechado sem alterar o formulário.
5. O colaborador selecionado é gravado na conta.

## Próxima ação e verificações complementares

Reexecutar com um nome existente para conferir listagem e seleção e confirmar com o produto a mensagem de resultado vazio.

## Evidências e limites

- [Jam original — Contas a Pagar](https://jam.dev/c/5d0afaf4-5abd-4e85-923f-27448304a9ef).
- [Arquivos, origem e limites](../Evidencias/CT-RF93_Busca_Colaborador_Conta_Pagar/README.md).
- [Modal Buscar Colaborador em 0:26](../Evidencias/CT-RF93_Busca_Colaborador_Conta_Pagar/modal_buscar_colaborador_00-26.png), [Lista de rede](../Evidencias/CT-RF93_Busca_Colaborador_Conta_Pagar/rede_lista.jpg).
- [Linha do tempo](../Evidencias/CT-RF93_Busca_Colaborador_Conta_Pagar/linha_do_tempo.txt).

Foram consultados os painéis Info, Console, Network e Actions do Jam e os quadros do vídeo. As capturas foram extraídas da reprodução do Jam. Não houve nova execução, inspeção do código, acesso ao banco ou correção da aplicação. O vídeo permanece no Jam.

Análise documental da gravação consultada em 15/11/2026. Esta inclusão não executa novamente o sistema e não constitui reteste. Versão da aplicação, zoom e classificação do ambiente não foram confirmados.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf93) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
