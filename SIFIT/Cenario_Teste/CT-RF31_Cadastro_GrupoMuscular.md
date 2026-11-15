# 🧪 Cenário 31: Cadastro de grupo muscular

**Caso de teste:** CT-RF31

**Módulo:** Treinamento / Grupos Musculares

**Status:** Aprovado conforme a gravação.

**Gravação:** 15/11/2026, 15h56 BRT. **Revisão documental:** 15/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Cadastrar um grupo muscular e apresentá-lo na listagem, com os contadores atualizados. |
| Requisito | [RF31](../Analise%20de%20requisitos.md#rf31) |
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
| Dados | Usar nome de grupo muscular de teste disponível segundo as regras do produto; valores da gravação são referência histórica. |

## Pré-condições

- Sessão autenticada com permissão para cadastrar grupos musculares.
- Nome de grupo muscular de teste disponível, sem conflito com registros existentes.
- Estado inicial da listagem e dos contadores registrado antes da inclusão.
- Antes de uma nova execução, identificar versão, permissões e dados de referência e preparar a captura de interface e rede.

## Cenário BDD

```gherkin
Cenário: Cadastrar um grupo muscular
  Dado que o usuário possui permissão para cadastrar grupos musculares
  Quando abrir o formulário de inclusão
  E informar um nome válido e o tipo de membro
  E confirmar em "Salvar"
  Então o sistema deve criar o grupo muscular
  E apresentar o novo registro na listagem
  E atualizar os contadores do resumo
```

## Passos para execução ou reteste

1. Acessar a tela Grupos Musculares e registrar a listagem e os contadores iniciais.
2. Abrir o formulário de inclusão pelo botão de adicionar.
3. Informar o nome e selecionar o tipo de membro.
4. Clicar em "Salvar".
5. Conferir o novo registro na listagem, o código atribuído e os contadores do resumo.
6. Recarregar a página e consultar novamente o registro para verificar a persistência.

Este procedimento orienta a próxima execução. A evidência atual cobre o trecho gravado e os limites descritos abaixo; passos complementares, como a recarga da página e a conferência no banco de dados, não recebem resultado de execução nesta revisão.

## Resultado esperado

O grupo muscular é criado, passa a constar na listagem e os contadores do resumo refletem a inclusão.

## Resultado obtido na gravação

O registro foi criado e apareceu na listagem com os contadores atualizados.

**Momentos e registros:**

| Tempo | Registro |
| --- | --- |
| 0:17–0:18 | Abertura do formulário "Grupo Muscular", com os campos Código, Nome, Tipo Membro e Imagem. |
| 0:19–0:38 | Preenchimento do formulário, com digitação e correções sucessivas no campo de nome. |
| 0:40–0:41 | Seleção do Tipo Membro. |
| 0:48 | Formulário com Nome "Tríceps", Tipo Membro "Superiores", Código em branco e Imagem em "Nenhum arquivo escolhido". Listagem ao fundo com três registros e "Mostrando 1 a 3 de 3 grupos". |
| 0:53 | Acionamento do botão de envio do formulário. |
| 0:55 | Listagem com quatro registros, incluindo o grupo "Tríceps" com código 6 e tipo "Superiores". Rodapé em "Mostrando 1 a 4 de 4 grupos". Cartões: Grupos cadastrados 4, Superiores 3, Inferiores 1, Aeróbio 0. |

**Estado antes e depois:**

| Indicador | Antes (0:48) | Depois (0:55) |
| --- | --- | --- |
| Grupos cadastrados | 3 | 4 |
| Superiores | 2 | 3 |
| Inferiores | 1 | 1 |
| Aeróbio | 0 | 0 |
| Registros na listagem | 3 | 4 |

**Conclusão:** Aprovado conforme a gravação. A aprovação se limita ao cenário visível; não significa validação de todas as variações do fluxo.

## Critérios de aceitação para nova execução

1. O formulário permite informar nome e tipo de membro.
2. O envio cria o registro e encerra o formulário.
3. A listagem passa a exibir o novo grupo muscular, com o rodapé de contagem coerente.
4. Os cartões de resumo refletem a inclusão, inclusive o cartão do tipo de membro escolhido.
5. O registro permanece após recarga da página.

## Próxima ação e verificações complementares

Usar como regressão. Permanecem fora do cenário gravado: campos obrigatórios em branco, nomes duplicados, limites de tamanho, caracteres especiais e cancelamento do formulário.

## Observações sobre o campo Código

No quadro de 0:48 o campo Código está em branco no momento do envio, e o registro criado recebeu o código 6. A cronologia registra digitação em campos do formulário entre 0:22 e 0:38, com apagamentos em 0:30; o conteúdo final de cada campo individual não é reconstituível pela cronologia, apenas pelo quadro de 0:48.

A listagem apresenta os códigos 1, 2, 5 e 6, portanto não sequenciais. O comportamento é compatível com atribuição automática de identificador pelo sistema, com lacunas decorrentes de exclusões anteriores. Isso é uma leitura da evidência e não foi confirmado na regra do produto nem no banco de dados; também não foi testado o envio com um código informado manualmente.

## Observação sobre a imagem do registro criado

O formulário foi enviado com "Nenhum arquivo escolhido" no campo Imagem. Ainda assim, a partir de 0:53 a página passa a requisitar um quarto arquivo de imagem, que retorna HTTP 422. Essa manifestação está documentada em [CT-RF30](CT-RF30_Imagens_GruposMusculares.md) e não afeta o resultado deste cenário, já que o registro foi criado e listado normalmente.

## Evidências e limites

- [Jam original — Tela de Grupos Musculares](https://jam.dev/c/98008390-0040-475e-ba7b-7f1e72cc0b2e).
- Painel Console do Jam, visão de atividade do usuário: cronologia de cliques e digitação entre 0:17 e 0:53.
- Quadros consultados: 0:20, 0:48 e 0:55.
- Pasta local de evidências: a criar em `Evidencias/CT-RF31_Cadastro_GrupoMuscular/`; até lá, a fonte é o Jam indicado acima.

A cronologia não registra uma requisição de criação com o respectivo código de status para este fluxo; a conclusão de que o registro foi criado apoia-se na mudança observada entre os quadros de 0:48 e 0:55. A persistência após recarga não foi verificada, nem houve consulta ao banco de dados. Não foi avaliado o comportamento com dados inválidos, campos obrigatórios em branco ou nome duplicado. A mensagem de confirmação apresentada após o envio, se houver, não foi capturada nos quadros consultados.

Análise documental da gravação consultada em 15/11/2026, com leitura direta dos painéis do Jam. Esta inclusão não executa novamente o sistema, não corrige a aplicação e não constitui reteste. Versão da aplicação, zoom e classificação do ambiente não foram confirmados.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
