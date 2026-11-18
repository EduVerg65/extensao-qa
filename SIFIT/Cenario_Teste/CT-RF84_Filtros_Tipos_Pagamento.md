# 🧪 Cenário 84: Filtros de busca da tela Tipos de Pagamento

**Caso de teste:** CT-RF84

**Módulo:** Comercial / Tipos de Pagamento / Filtros

**Status:** A validar — regra ou contexto pendente.

**Gravação:** 15/11/2026, 22:03 BRT. **Revisão documental:** 15/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Filtrar a listagem de tipos de pagamento por código, nome, status e tipo, apresentando apenas os tipos correspondentes e cartões coerentes. |
| Requisito | [RF84](../Analise%20de%20requisitos.md#rf84) — referência de QA; confirmação de produto pendente. |
| Tipo / prioridade | Exploratório / regra a confirmar; Média, proposta para triagem. |
| Defeito | Sem defeito confirmado. |
| Encaminhamento | Reexecutar com critérios conhecidos (nome existente, status e tipo isolados e combinados), capturar o corpo das requisições e a listagem a cada critério e confirmar com o produto se a filtragem é local ou no servidor. |
| Fonte | [Jam — Tipos de Pagamento](https://jam.dev/c/e8734e3d-3f8e-458b-8c7d-e85eea882e50) e [evidências locais](../Evidencias/CT-RF104_Filtros_Tipos_Pagamento/README.md). A mesma gravação é a fonte de [CT-RF85](CT-RF85_Cadastro_Tipo_Pagamento_Status.md), [CT-RF86](CT-RF86_Edicao_Tipo_Pagamento.md), [CT-RF87](CT-RF87_Exclusao_Tipo_Pagamento_Em_Uso.md) e [CT-RF88](CT-RF88_Tema_Notificacoes_Tipos_Pagamento.md). |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/tipos-pagamento |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.78 / Windows (x86) 11. |
| Tela / arquivo de vídeo | 1920 × 855 informados no Jam. |
| Duração | 1 min |
| Rede | Classificada como rápida no Jam: 7,8 Mbps, latência de 50 ms. |
| Localização | Brasil. |
| Usuário exibido | Jair, conforme o canto superior direito da tela. |
| Versão / zoom / classificação do ambiente | Não confirmados; registrar antes de nova execução. |
| Dados | 16 tipos listados no início, todos com status Inativo; Nome digitado "de" (0:01) e "4" (0:28), ambos apagados; seletores Status e Tipo acionados cerca de 17 vezes entre 0:03 e 0:14, sem registro do valor escolhido. |

## Pré-condições

- Sessão autenticada com acesso à tela Tipos de Pagamento.
- Base de tipos de pagamento conhecida (16 tipos no início da gravação, todos exibidos como Inativo), com tipos usados em contas a receber e um tipo descartável para cadastro.
- Antes de uma nova execução, identificar versão, permissões e dados de referência e preparar a captura de interface e rede.

## Cenário BDD

```gherkin
Cenário: Filtrar tipos de pagamento
  Dado que a tela Tipos de Pagamento apresenta a listagem completa
  Quando o usuário informar código, nome, status e tipo e acionar Buscar
  Então a listagem deve apresentar apenas os tipos que atendam aos critérios
  E os cartões Total, Ativos, Inativos e Via gateway devem corresponder ao conjunto exibido
```

## Passos para execução ou reteste

1. Acessar Tipos de Pagamento e registrar a listagem e os cartões iniciais.
2. Informar um nome (parte de um tipo existente) e acionar Buscar.
3. Escolher cada valor do filtro Status (Todos, Ativo e Inativo) e do filtro Tipo (Todos, Crédito e Débito) isoladamente e acionar Buscar.
4. Combinar nome, status e tipo e conferir a listagem e os cartões.
5. Repetir com um critério sem correspondência e conferir a mensagem de resultado vazio.

Este procedimento orienta a próxima execução. A evidência atual cobre o trecho gravado e os limites descritos abaixo; passos complementares não recebem resultado de execução nesta revisão.

## Resultado esperado

A listagem apresenta apenas os tipos que atendem aos critérios, os cartões acompanham o conjunto exibido e o resultado vazio é indicado de forma explícita.

## Resultado obtido na gravação

Em 0:14, com o ponteiro sobre Buscar e os filtros Status e Tipo em "Todos", a listagem continuou com os 16 tipos e os cartões em Total 16, Ativos 0, Inativos 16 e Via gateway 5. O Nome "de" foi digitado e apagado em 3 segundos, e "4" foi digitado e apagado sem acionar Buscar. Nenhuma requisição de listagem acompanhou os cliques em Buscar ou nos seletores; os únicos `GET tipo-pagamento/1` ocorreram na carga, após o cadastro e após a edição.

| Tempo | Registro |
| --- | --- |
| 0:00 | Listagem inicial com 16 tipos (Dinheiro, Cheque, Boletos, Cartão de Crédito...), todos com status Inativo; cartões Total 16, Ativos 0, Inativos 16 e Via gateway 5. |
| 0:01–0:03 | Nome "de" digitado e apagado; sem Buscar. |
| 0:03–0:14 | Cerca de 17 cliques nos seletores Status e Tipo; o valor escolhido a cada clique não aparece nos quadros consultados. |
| 0:14 | Clique em Buscar com os filtros em "Todos"; a listagem permanece com 16 tipos e nenhuma requisição de listagem é emitida. |
| 0:28–0:29 | Nome "4" digitado e apagado, sem Buscar. |

**Conclusão:** A validar — regra ou contexto pendente. Não houve resultado filtrado que permita avaliar a regra: a gravação não registra os valores escolhidos nos seletores e não há requisição de listagem após Buscar; a filtragem local não foi confirmada.

## Critérios de aceitação para nova execução

1. Cada critério isolado (código, nome, status e tipo) filtra corretamente a listagem.
2. A combinação de critérios aplica todos eles simultaneamente.
3. Os cartões acompanham o conjunto exibido conforme o contrato definido.
4. O resultado vazio apresenta mensagem explícita.
5. Limpar os critérios restaura a listagem completa.

## Próxima ação e verificações complementares

Reexecutar com critérios conhecidos, registrando o valor escolhido em cada seletor, a listagem resultante e as requisições de rede; confirmar com o produto se a filtragem é local ou no servidor.

## Evidências e limites

- [Jam original — Tipos de Pagamento](https://jam.dev/c/e8734e3d-3f8e-458b-8c7d-e85eea882e50).
- [Arquivos, origem e limites](../Evidencias/CT-RF104_Filtros_Tipos_Pagamento/README.md).
- [Listagem inicial em 0:00](../Evidencias/CT-RF104_Filtros_Tipos_Pagamento/lista_inicial_00-00.jpg), [Filtros em 0:14](../Evidencias/CT-RF104_Filtros_Tipos_Pagamento/filtros_buscar_00-14.jpg), [Lista de rede](../Evidencias/CT-RF104_Filtros_Tipos_Pagamento/rede_lista.jpg).
- [Linha do tempo](../Evidencias/CT-RF104_Filtros_Tipos_Pagamento/linha_do_tempo.txt).

Foram consultados os painéis Info, Console, Network e Actions do Jam e os quadros do vídeo. As capturas foram extraídas da reprodução do Jam. Não houve nova execução, inspeção do código, acesso ao banco ou correção da aplicação. O vídeo permanece no Jam.

Análise documental da gravação consultada em 15/11/2026. Esta inclusão não executa novamente o sistema e não constitui reteste. Versão da aplicação, zoom e classificação do ambiente não foram confirmados.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf84) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
