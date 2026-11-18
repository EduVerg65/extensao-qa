# 🧪 Cenário 82: Variáveis e pré-visualização do texto do modelo de contrato

**Caso de teste:** CT-RF82

**Módulo:** Modelos de Contrato / Editor / Variáveis e pré-visualização

**Status:** Aprovado conforme a gravação.

**Gravação:** 15/11/2026, 21:55 BRT. **Revisão documental:** 15/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Inserir variáveis no texto do contrato pelos chips e conferir a pré-visualização com os dados de exemplo. |
| Requisito | [RF82](../Analise%20de%20requisitos.md#rf82) — referência de QA; confirmação de produto pendente. |
| Tipo / prioridade | Funcional manual / regressão; Média, proposta para triagem. |
| Defeito | Nenhum no fluxo avaliado |
| Encaminhamento | Sem reteste corretivo pendente; manter como regressão. Conferir todas as variáveis de cada grupo e o comportamento com texto formatado. |
| Fonte | [Jam — Modelos de Contrato](https://jam.dev/c/44dbbd39-6915-45d6-8dd1-5f30c1432ca0) e [evidências locais](../Evidencias/CT-RF96_Variaveis_Preview_Modelo_Contrato/README.md). A mesma gravação é a fonte de [CT-RF81](CT-RF81_Cadastro_Modelo_Contrato.md) e [CT-RF83](CT-RF83_Listagem_Modelos_Contrato_Vazia.md). |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/modelos-contrato |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.78 / Windows (x86) 11. |
| Tela / arquivo de vídeo | 1920 × 855 informados no Jam. |
| Duração | 50 s |
| Rede | Classificada como rápida no Jam: 7,8 Mbps, latência de 50 ms. |
| Localização | Brasil. |
| Usuário exibido | Jair, conforme o canto superior direito da tela. |
| Versão / zoom / classificação do ambiente | Não confirmados; registrar antes de nova execução. |
| Dados | Texto "asdasdaasdasdasdasd" (com trecho em negrito) e variáveis {numero_contrato}, {nome_aluno} e {cpf_aluno}; pré-visualização com dados de exemplo. |

## Pré-condições

- Sessão autenticada com acesso à tela Modelos de Contrato.
- Modelos de contrato existentes conhecidos (15 após o cadastro da gravação) e variáveis disponíveis nos grupos Aluno, Plano, Academia e Contrato.
- Antes de uma nova execução, identificar versão, permissões e dados de referência e preparar a captura de interface e rede.

## Cenário BDD

```gherkin
Cenário: Inserir variáveis e atualizar a pré-visualização
  Dado que o editor de texto do modelo está aberto
  Quando o usuário clicar em variáveis disponíveis e acionar Atualizar preview
  Então as variáveis devem ser inseridas no texto
  E a pré-visualização deve substituí-las por dados de exemplo
```

## Passos para execução ou reteste

1. Acessar Adicionar Modelo Contrato e digitar um texto com trecho em negrito.
2. Clicar em variáveis de cada grupo (Aluno, Plano, Academia e Contrato) e conferir a inserção no texto.
3. Acionar Atualizar preview e conferir a substituição por dados de exemplo.
4. Acionar Ver todas as variáveis e conferir os grupos.
5. Salvar e conferir que as variáveis permanecem no texto.

Este procedimento orienta a próxima execução. A evidência atual cobre o trecho gravado e os limites descritos abaixo; passos complementares não recebem resultado de execução nesta revisão.

## Resultado esperado

Cada variável clicada é inserida no ponto do cursor e a pré-visualização apresenta os valores de exemplo correspondentes, preservando a formatação do texto.

## Resultado obtido na gravação

As variáveis {numero_contrato}, {nome_aluno} e {cpf_aluno} foram inseridas no texto e a pré-visualização passou a apresentar "2024/001 João da Silva 123.456.789-00" seguida do texto digitado, com o negrito preservado; "Ver todas as variáveis" expandiu os quatro grupos.

| Tempo | Registro |
| --- | --- |
| 0:09 | Formulário vazio com o painel Variáveis disponíveis (Dados do aluno, do plano, da academia e do contrato) e pré-visualização vazia. |
| 0:21 | Texto digitado no editor, com trecho em negrito; pré-visualização ainda sem atualização. |
| 0:26 | Variáveis {nome_aluno} e {cpf_aluno} inseridas; pré-visualização com o texto digitado. |
| 0:33 | Variáveis {numero_contrato}, {nome_aluno} e {cpf_aluno} no texto; pré-visualização com "2024/001 João da Silva 123.456.789-00". |
| 0:36 | "Ver todas as variáveis" expande os grupos de variáveis. |

**Rede:** a inserção de variáveis e a pré-visualização não geram requisição de rede; a pré-visualização é compatível com substituição na própria tela, sem confirmação.

**Conclusão:** Aprovado conforme a gravação. As variáveis são inseridas e a pré-visualização as substitui por dados de exemplo. A aprovação se limita às três variáveis exercitadas; as demais variáveis dos quatro grupos e o comportamento com formatação complexa não foram verificados.

## Critérios de aceitação para nova execução

1. Cada variável clicada é inserida no ponto do cursor do editor.
2. A pré-visualização substitui as variáveis por dados de exemplo coerentes.
3. A formatação do texto é preservada na pré-visualização.
4. Todas as variáveis dos quatro grupos funcionam.
5. As variáveis permanecem no texto após salvar.

## Próxima ação e verificações complementares

Usar como regressão. Permanecem fora do cenário: as demais variáveis dos grupos, variáveis digitadas manualmente, formatação complexa e o texto gravado após salvar.

## Evidências e limites

- [Jam original — Modelos de Contrato](https://jam.dev/c/44dbbd39-6915-45d6-8dd1-5f30c1432ca0).
- [Arquivos, origem e limites](../Evidencias/CT-RF96_Variaveis_Preview_Modelo_Contrato/README.md).
- [Formulário vazio em 0:09](../Evidencias/CT-RF96_Variaveis_Preview_Modelo_Contrato/formulario_vazio_00-09.png), [Texto digitado em 0:21](../Evidencias/CT-RF96_Variaveis_Preview_Modelo_Contrato/texto_digitado_00-21.png), [Variáveis inseridas e pré-visualização em 0:33.](../Evidencias/CT-RF96_Variaveis_Preview_Modelo_Contrato/variaveis_preview_00-33.png), [Painel com todas as variáveis em 0:36.](../Evidencias/CT-RF96_Variaveis_Preview_Modelo_Contrato/todas_variaveis_00-36.png), [Lista de rede](../Evidencias/CT-RF96_Variaveis_Preview_Modelo_Contrato/rede_lista.jpg).
- [Linha do tempo](../Evidencias/CT-RF96_Variaveis_Preview_Modelo_Contrato/linha_do_tempo.txt).

Foram consultados os painéis Info, Console, Network e Actions do Jam e os quadros do vídeo. As capturas foram extraídas da reprodução do Jam. Não houve nova execução, inspeção do código, acesso ao banco ou correção da aplicação. O vídeo permanece no Jam.

Análise documental da gravação consultada em 15/11/2026. Esta inclusão não executa novamente o sistema e não constitui reteste. Versão da aplicação, zoom e classificação do ambiente não foram confirmados.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf82) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
