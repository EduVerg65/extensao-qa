# 🧪 Cenário 77: Filtros da tela Planos por código e nome

**Caso de teste:** CT-RF77

**Módulo:** Planos / Filtros

**Status:** Aprovado conforme a gravação.

**Gravação:** 15/11/2026, 21:54 BRT. **Revisão documental:** 15/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Filtrar a listagem de planos por código e por nome e restaurar a listagem completa ao limpar os campos. |
| Requisito | [RF77](../Analise%20de%20requisitos.md#rf77) — referência de QA; confirmação de produto pendente. |
| Tipo / prioridade | Funcional manual / regressão; Média, proposta para triagem. |
| Defeito | Nenhum no fluxo avaliado |
| Encaminhamento | Sem reteste corretivo pendente; manter como regressão. Confirmar o filtro por Status, a combinação de critérios e o resultado vazio. |
| Fonte | [Jam — Planos](https://jam.dev/c/233c5d21-e108-4a55-b6f6-8738cb3fc6a6) e [evidências locais](../Evidencias/CT-RF99_Filtros_Planos/README.md). A mesma gravação é a fonte de [CT-RF76](CT-RF76_Tema_Notificacoes_Planos.md), [CT-RF78](CT-RF78_Cadastro_Plano.md), [CT-RF79](CT-RF79_Contador_Ativos_Planos.md) e [CT-RF80](CT-RF80_Edicao_Plano.md). |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/planos |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.78 / Windows (x86) 11. |
| Tela / arquivo de vídeo | 1920 × 855 informados no Jam. |
| Duração | 1 min 10 s |
| Rede | Classificada como rápida no Jam: 7,8 Mbps, latência de 50 ms. |
| Localização | Brasil. |
| Usuário exibido | Jair, conforme o canto superior direito da tela. |
| Versão / zoom / classificação do ambiente | Não confirmados; registrar antes de nova execução. |
| Dados | Base com 40 planos; critérios exercitados: Código "7" e Nome "a". |

## Pré-condições

- Sessão autenticada com acesso à tela Planos.
- Base de planos conhecida (40 planos, 29 ativos e 9 alunos em planos no início da gravação), com grupos e funções cadastrados.
- Antes de uma nova execução, identificar versão, permissões e dados de referência e preparar a captura de interface e rede.

## Cenário BDD

```gherkin
Cenário: Filtrar planos por código e por nome
  Dado que a tela Planos apresenta a listagem completa
  Quando o usuário informar um critério de Código ou de Nome
  Então a listagem deve apresentar apenas os planos correspondentes
  E, ao limpar o critério, a listagem completa deve voltar
```

## Passos para execução ou reteste

1. Acessar Planos e registrar a listagem e os cartões.
2. Informar um código e conferir as linhas.
3. Informar parte de um nome (sem diferenciar maiúsculas) e conferir as linhas.
4. Alternar o seletor Status e acionar Buscar.
5. Limpar os campos e conferir a listagem completa.

Este procedimento orienta a próxima execução. A evidência atual cobre o trecho gravado e os limites descritos abaixo; passos complementares não recebem resultado de execução nesta revisão.

## Resultado esperado

A listagem apresenta apenas os planos que atendem aos critérios e volta ao conjunto completo ao limpar os campos.

## Resultado obtido na gravação

Com o Código "7" a listagem apresentou os planos de códigos 37, 7 e 67 (códigos que contêm 7); com o Nome "a" a listagem apresentou planos de nomes "aba" e "Aba"; ao limpar, a listagem completa de 40 planos voltou; Buscar recarregou a listagem.

| Tempo | Registro |
| --- | --- |
| 0:00–0:04 | Nome "a" digitado: listagem com planos de códigos 36, 37 e 38 (nomes aba/Aba) entre os apresentados; cartões Planos 40, Ativos 29, Alunos em Planos 9. |
| 0:05–0:07 | Código "7" informado: listagem com os planos 37 (aba), 7 (Barato) e 67 (Aba 10). |
| 0:12–0:13 | Buscar acionado: a tabela passa por carregamento (esqueleto) e a listagem é recarregada (`GET planos/1`). |

**Conclusão:** Aprovado conforme a gravação. Os filtros por código e por nome retornam conjuntos coerentes com os critérios e a listagem completa é restaurada. A aprovação se limita aos exemplos gravados; o filtro por Status, a combinação de critérios e o resultado vazio não foram verificados.

## Critérios de aceitação para nova execução

1. O filtro por código retorna os planos cujo código contenha o critério.
2. O filtro por nome retorna os planos cujo nome contenha o critério, sem diferenciar maiúsculas.
3. O seletor Status filtra a listagem conforme a opção.
4. Limpar os campos restaura a listagem completa.
5. Critérios sem correspondência apresentam mensagem explícita.

## Próxima ação e verificações complementares

Usar como regressão. Permanecem fora do cenário: filtro por Status com valores específicos, combinação de critérios e resultado vazio.

## Evidências e limites

- [Jam original — Planos](https://jam.dev/c/233c5d21-e108-4a55-b6f6-8738cb3fc6a6).
- [Arquivos, origem e limites](../Evidencias/CT-RF99_Filtros_Planos/README.md).
- [Filtro de nome "a" em 0:03](../Evidencias/CT-RF99_Filtros_Planos/filtro_nome_00-03.png), [Filtro de código "7" em 0:06](../Evidencias/CT-RF99_Filtros_Planos/filtro_codigo_00-06.png), [Buscar acionado em 0:13](../Evidencias/CT-RF99_Filtros_Planos/buscar_carregando_00-13.png), [Lista de rede](../Evidencias/CT-RF99_Filtros_Planos/rede_lista.jpg).
- [Linha do tempo](../Evidencias/CT-RF99_Filtros_Planos/linha_do_tempo.txt).

Foram consultados os painéis Info, Console, Network e Actions do Jam e os quadros do vídeo. As capturas foram extraídas da reprodução do Jam. Não houve nova execução, inspeção do código, acesso ao banco ou correção da aplicação. O vídeo permanece no Jam.

Análise documental da gravação consultada em 15/11/2026. Esta inclusão não executa novamente o sistema e não constitui reteste. Versão da aplicação, zoom e classificação do ambiente não foram confirmados.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf77) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
