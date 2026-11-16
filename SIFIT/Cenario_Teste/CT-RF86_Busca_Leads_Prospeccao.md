# 🧪 Cenário 86: Busca de leads por texto na tela Prospecção

**Caso de teste:** CT-RF86

**Módulo:** Prospecção / Leads / Busca

**Status:** Aprovado conforme a gravação.

**Gravação:** 15/11/2026, 21:52 BRT. **Revisão documental:** 15/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Filtrar a listagem de leads pelo campo Buscar lead (nome, e-mail, telefone ou código), apresentando apenas os registros correspondentes e restaurando a listagem ao limpar. |
| Requisito | [RF86](../Analise%20de%20requisitos.md#rf86) — referência de QA; confirmação de produto pendente. |
| Tipo / prioridade | Funcional manual / regressão; Média, proposta para triagem. |
| Defeito | Nenhum no fluxo avaliado |
| Encaminhamento | Sem reteste corretivo pendente; manter como regressão. Confirmar a regra de correspondência (nome, e-mail, telefone e código) e o resultado vazio. |
| Fonte | [Jam — Prospecção](https://jam.dev/c/308607ff-8abc-40af-8c7c-429ce506ed64) e [evidências locais](../Evidencias/CT-RF86_Busca_Leads_Prospeccao/README.md). A mesma gravação é a fonte de [CT-RF85](CT-RF85_Tema_Notificacoes_Prospeccao.md), [CT-RF87](CT-RF87_Filtro_Estagio_Leads.md), [CT-RF88](CT-RF88_Cadastro_Lead_Prospeccao.md), [CT-RF89](CT-RF89_Telefone_Lead_Sem_Validacao.md) e [CT-RF90](CT-RF90_Edicao_Lead_Prospeccao.md). |

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
| Dados | Base com 7 leads (códigos 3 a 9) antes do cadastro e 8 leads (código 10 incluído) depois; termos digitados: sequência de correções em 0:12 (aas, S, D, F) e "tes" em 0:43. |

## Pré-condições

- Sessão autenticada com acesso à tela Prospecção.
- Base de leads conhecida, com códigos, nomes e estágios registrados antes da execução.
- Antes de uma nova execução, identificar versão, permissões e dados de referência e preparar a captura de interface e rede.

## Cenário BDD

```gherkin
Cenário: Buscar leads por texto
  Dado que a tela Prospecção apresenta a listagem de leads
  Quando o usuário digitar um termo no campo Buscar lead
  Então a listagem deve apresentar apenas os leads correspondentes ao termo
  E, ao apagar o termo, a listagem completa deve voltar
```

## Passos para execução ou reteste

1. Acessar Prospecção e registrar a listagem completa e os cartões.
2. Digitar parte de um nome e conferir as linhas apresentadas.
3. Digitar um e-mail, um telefone e um código e conferir as linhas.
4. Digitar um termo sem correspondência e conferir a mensagem de resultado vazio.
5. Apagar o termo e conferir a restauração da listagem.

Este procedimento orienta a próxima execução. A evidência atual cobre o trecho gravado e os limites descritos abaixo; passos complementares não recebem resultado de execução nesta revisão.

## Resultado esperado

A listagem apresenta apenas os leads cujo nome, e-mail, telefone ou código corresponda ao termo, sem diferenciar maiúsculas de minúsculas, e volta ao conjunto completo ao limpar o campo.

## Resultado obtido na gravação

Com termos digitados no campo, a listagem foi reduzida a subconjuntos coerentes: dois leads (códigos 3 e 7) em 0:12 e, com o termo "tes", os leads "Teste A" (código 4) e "teste" (código 10) em 0:44. A listagem completa voltou com o campo vazio em 0:13.

| Tempo | Registro |
| --- | --- |
| 0:05–0:12 | Termos digitados no campo Buscar lead, com várias correções; em 0:12 a listagem apresenta dois leads (códigos 3 e 7) de 7; os cartões Leads, Novos Contatos e Interessados mantêm 7, 2 e 2. |
| 0:13 | Campo apagado: a listagem completa de 7 leads é exibida. |
| 0:43–0:44 | Termo "tes" informado (após o cadastro do CT-RF88): duas linhas, "Teste A" (código 4) e "teste" (código 10); cartões Leads 8, Novos Contatos 2 e Interessados 3. |

**Rede:** a busca por texto não gera requisição de rede; a única chamada de lista ocorre antes e depois do cadastro, o que é compatível com filtragem feita na própria tela, sem confirmação.

**Conclusão:** Aprovado conforme a gravação. A busca por texto retorna subconjuntos coerentes com o termo digitado e a listagem completa é restaurada. A aprovação se limita aos exemplos gravados; o termo digitado em 0:12 não foi identificado com certeza e a regra de correspondência não foi confirmada.

## Critérios de aceitação para nova execução

1. O campo Buscar lead filtra por nome, e-mail, telefone e código conforme o rótulo do campo.
2. A busca não diferencia maiúsculas de minúsculas.
3. Os cartões acompanham ou não o filtro de acordo com o contrato definido.
4. Ao apagar o termo, a listagem completa é restaurada.
5. Um termo sem correspondência apresenta mensagem explícita de resultado vazio.

## Próxima ação e verificações complementares

Usar como regressão. Permanecem fora do cenário gravado: busca por e-mail, telefone e código, termo sem correspondência, caracteres especiais e a combinação com o filtro de estágio.

## Observação sobre os cartões de resumo

Com a busca aplicada, os cartões Leads, Novos Contatos e Interessados mantêm o total da base (7 e 2/2 em 0:12; 8 e 2/3 em 0:44). O contrato dos indicadores não foi fornecido, do mesmo modo que em [CT-RF11](CT-RF11_Metricas_Financeiro.md) e [CT-RF46](CT-RF46_Filtros_Despesas_Fixas.md).

## Observação sobre o termo de 0:12

A digitação em 0:12 inclui várias correções (aas, S, D, F) e o quadro consultado não permite afirmar o termo vigente; o veredito se apoia no número e nos códigos dos leads apresentados, e não na regra de correspondência.

## Evidências e limites

- [Jam original — Prospecção](https://jam.dev/c/308607ff-8abc-40af-8c7c-429ce506ed64).
- [Arquivos, origem e limites](../Evidencias/CT-RF86_Busca_Leads_Prospeccao/README.md).
- [Busca em 0:12](../Evidencias/CT-RF86_Busca_Leads_Prospeccao/busca_texto_00-12.png), [Busca "tes" em 0:44](../Evidencias/CT-RF86_Busca_Leads_Prospeccao/busca_tes_00-44.png), [Lista de rede](../Evidencias/CT-RF86_Busca_Leads_Prospeccao/rede_lista.jpg).
- [Linha do tempo](../Evidencias/CT-RF86_Busca_Leads_Prospeccao/linha_do_tempo.txt).

Foram consultados os painéis Info, Console, Network e Actions do Jam e os quadros do vídeo. As capturas foram extraídas da reprodução do Jam; quadros com o e-mail digitado no formulário não foram incluídos nem recortados com esse dado. A regra de correspondência, a busca por e-mail, telefone e código e o resultado vazio não foram exercitados. Não houve nova execução, inspeção do código, acesso ao banco ou correção da aplicação. O vídeo permanece no Jam.

Análise documental da gravação consultada em 15/11/2026. Esta inclusão não executa novamente o sistema e não constitui reteste. Versão da aplicação, zoom e classificação do ambiente não foram confirmados.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf86) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
