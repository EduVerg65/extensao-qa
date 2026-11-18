# 🧪 Cenário 78: Cadastro de plano pelo modal Novo Plano

**Caso de teste:** CT-RF78

**Módulo:** Planos / Cadastro

**Status:** Aprovado conforme a gravação.

**Gravação:** 15/11/2026, 21:54 BRT. **Revisão documental:** 15/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Cadastrar um plano informando nome, grupo, status, cobrança, valor, equipe, dependentes e benefícios, e apresentá-lo na listagem. |
| Requisito | [RF78](../Analise%20de%20requisitos.md#rf78) — referência de QA; confirmação de produto pendente. |
| Tipo / prioridade | Funcional manual / regressão; Alta, proposta para triagem. |
| Defeito | Nenhum no fluxo avaliado |
| Encaminhamento | Sem reteste corretivo pendente; manter como regressão. Capturar a linha criada na listagem e testar campos obrigatórios e valores extremos. |
| Fonte | [Jam — Planos](https://jam.dev/c/233c5d21-e108-4a55-b6f6-8738cb3fc6a6) e [evidências locais](../Evidencias/CT-RF101_Cadastro_Plano/README.md). A mesma gravação é a fonte de [CT-RF77](CT-RF77_Filtros_Planos.md), [CT-RF76](CT-RF76_Tema_Notificacoes_Planos.md), [CT-RF79](CT-RF79_Contador_Ativos_Planos.md) e [CT-RF80](CT-RF80_Edicao_Plano.md). |

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
| Dados | Plano "rerererere", grupo Treino Personal, status Inativo, cobrança diária, parcelas 1, valor 44,44, personal Sim (função Personal Externo), 3 dependentes e benefício "sadas"; base com 40 planos antes. |

## Pré-condições

- Sessão autenticada com acesso à tela Planos.
- Base de planos conhecida (40 planos, 29 ativos e 9 alunos em planos no início da gravação), com grupos e funções cadastrados.
- Antes de uma nova execução, identificar versão, permissões e dados de referência e preparar a captura de interface e rede.

## Cenário BDD

```gherkin
Cenário: Cadastrar um plano
  Dado que o modal Novo Plano está preenchido
  Quando o usuário acionar Salvar Plano
  Então o plano deve ser criado
  E o contador de planos deve passar de 40 para 41
```

## Passos para execução ou reteste

1. Acessar Planos e acionar Novo Plano.
2. Preencher nome, grupo, status, cobrança, parcelas, valor, personal, dependentes e benefícios.
3. Acionar Salvar Plano e observar a requisição e a resposta.
4. Conferir o plano na listagem e o contador de planos.
5. Repetir com campos obrigatórios em branco.

Este procedimento orienta a próxima execução. A evidência atual cobre o trecho gravado e os limites descritos abaixo; passos complementares não recebem resultado de execução nesta revisão.

## Resultado esperado

Salvar cria o plano com resposta de sucesso e identificador, o contador de planos aumenta em uma unidade e a listagem passa a apresentá-lo.

## Resultado obtido na gravação

Salvar Plano gerou `POST plano/salvar/1` com HTTP 200 e `{"verifica_erro": false, "id": 66}`; o cartão Planos passou de 40 para 41 e a listagem foi recarregada. O comportamento do cartão Ativos é tratado no CT-RF79.

| Tempo | Registro |
| --- | --- |
| 0:22–0:24 | Novo Plano: modal com Dados do Plano, Contrato e Valores, Equipe e Dependentes e Benefícios; status inicial Ativo e valor 0,00. |
| 0:46 | Modal preenchido: nome "rerererere", grupo Treino Personal, status Inativo, cobrança Diária, parcelas 1, personal Sim, função Personal Externo e 3 dependentes. |
| 0:51 | Clique em Salvar Plano: `POST plano/salvar/1` com HTTP 200 e id 66. |
| 0:53 | Cartões: Planos 41 (antes 40). |

**Rede:** `POST /api/plano/salvar/1` (HTTP 200, 31 B) com `"nome": "rerererere"`, `"status": "inativo"`, `"valor": "44,44"` e `"qtd_dependentes": "3"`; resposta `{"verifica_erro": false, "id": 66}`; depois `GET planos/1` (8,3 KiB) e `POST matriculas/paginacao/1` (21,1 KiB).

**Conclusão:** Aprovado conforme a gravação. O plano foi criado (id 66) e o contador de planos acompanhou o cadastro. A aprovação se limita ao exemplo gravado; a linha do plano na listagem, os campos obrigatórios e o cartão Ativos (CT-RF79) não foram confirmados.

## Critérios de aceitação para nova execução

1. Salvar com dados válidos cria o plano e retorna o identificador.
2. O contador de planos acompanha o cadastro.
3. A listagem apresenta o plano criado com os dados informados.
4. Campos obrigatórios em branco são validados antes da gravação.
5. Os benefícios informados são gravados com o plano.

## Próxima ação e verificações complementares

Usar como regressão. Permanecem fora do cenário: localizar o plano 66 na listagem, campos obrigatórios em branco, valores extremos de valor e parcelas e a gravação dos benefícios.

## Evidências e limites

- [Jam original — Planos](https://jam.dev/c/233c5d21-e108-4a55-b6f6-8738cb3fc6a6).
- [Arquivos, origem e limites](../Evidencias/CT-RF101_Cadastro_Plano/README.md).
- [Modal Novo Plano em 0:24](../Evidencias/CT-RF101_Cadastro_Plano/modal_novo_plano_00-24.png), [Modal preenchido em 0:46](../Evidencias/CT-RF101_Cadastro_Plano/modal_preenchido_00-46.png), [Cartões em 0:53](../Evidencias/CT-RF101_Cadastro_Plano/cartoes_apos_cadastro_00-53.png), [Corpo da requisição plano/salvar (início do corpo).](../Evidencias/CT-RF101_Cadastro_Plano/requisicao_salvar.png), [Resposta de plano/salvar](../Evidencias/CT-RF101_Cadastro_Plano/resposta_salvar.png), [Lista de rede](../Evidencias/CT-RF101_Cadastro_Plano/rede_lista.jpg).
- [Linha do tempo](../Evidencias/CT-RF101_Cadastro_Plano/linha_do_tempo.txt).

Foram consultados os painéis Info, Console, Network e Actions do Jam e os quadros do vídeo. As capturas foram extraídas da reprodução do Jam. Não houve nova execução, inspeção do código, acesso ao banco ou correção da aplicação. O vídeo permanece no Jam.

Análise documental da gravação consultada em 15/11/2026. Esta inclusão não executa novamente o sistema e não constitui reteste. Versão da aplicação, zoom e classificação do ambiente não foram confirmados.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf78) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
