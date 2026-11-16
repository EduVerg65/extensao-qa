# 🧪 Cenário 76: Edição de plano pelo modal Editar Plano

**Caso de teste:** CT-RF76

**Módulo:** Planos / Edição

**Status:** Aprovado conforme a gravação.

**Gravação:** 15/11/2026, 21:54 BRT. **Revisão documental:** 15/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Abrir um plano pelo botão de ação, alterar benefícios e salvar, gravando a alteração sem erro. |
| Requisito | [RF76](../Analise%20de%20requisitos.md#rf76) — referência de QA; confirmação de produto pendente. |
| Tipo / prioridade | Funcional manual / regressão; Média, proposta para triagem. |
| Defeito | Nenhum no fluxo avaliado |
| Encaminhamento | Sem reteste corretivo pendente; manter como regressão. Conferir a persistência após recarga, a edição dos demais campos e o texto do modal. |
| Fonte | [Jam — Planos](https://jam.dev/c/233c5d21-e108-4a55-b6f6-8738cb3fc6a6) e [evidências locais](../Evidencias/CT-RF76_Edicao_Plano/README.md). A mesma gravação é a fonte de [CT-RF72](CT-RF72_Filtros_Planos.md), [CT-RF73](CT-RF73_Tema_Notificacoes_Planos.md), [CT-RF74](CT-RF74_Cadastro_Plano.md) e [CT-RF75](CT-RF75_Contador_Ativos_Planos.md). |

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
| Dados | Plano de código 41 "Teste Final" (grupo Treino Livre, valor 1,00, inativo) com benefícios alterados para "asdasd". |

## Pré-condições

- Sessão autenticada com acesso à tela Planos.
- Base de planos conhecida (40 planos, 29 ativos e 9 alunos em planos no início da gravação), com grupos e funções cadastrados.
- Antes de uma nova execução, identificar versão, permissões e dados de referência e preparar a captura de interface e rede.

## Cenário BDD

```gherkin
Cenário: Editar um plano
  Dado que a listagem apresenta o plano de código 41
  Quando o usuário abrir o plano, alterar os benefícios e acionar Salvar Plano
  Então a alteração deve ser enviada ao servidor sem erro
  E a listagem deve ser atualizada
```

## Passos para execução ou reteste

1. Acessar Planos e localizar um plano descartável.
2. Acionar o botão de ação da linha e conferir os dados no modal Editar Plano.
3. Alterar benefícios (e, em outra execução, os demais campos) e acionar Salvar Plano.
4. Conferir a requisição, a resposta e a listagem.
5. Recarregar a página e conferir a persistência.

Este procedimento orienta a próxima execução. A evidência atual cobre o trecho gravado e os limites descritos abaixo; passos complementares não recebem resultado de execução nesta revisão.

## Resultado esperado

O modal apresenta os dados do plano, a alteração é enviada com HTTP 200 sem erro e a listagem é atualizada, com persistência após recarga.

## Resultado obtido na gravação

O botão de ação do plano 41 abriu o modal Editar Plano com os dados do plano; o benefício "asdasd" foi informado e Salvar Plano gerou `POST plano/update/1` com HTTP 200 e `{"verifica_erro": false}`; a listagem foi recarregada (`GET planos/1` e `POST matriculas/paginacao/1`).

| Tempo | Registro |
| --- | --- |
| 0:59 | Clique no botão de ação da linha: `POST seleciona-plano/1` (HTTP 200, 347 B) com o plano 41 "Teste Final", valor "1,00", status "inativo". |
| 1:02 | Modal "Editar Plano": nome "Teste Final", grupo Treino Livre, status Inativo, cobrança Período fixo, valor 1,00 e função Trenador da academia. |
| 1:03–1:05 | Benefício digitado; clique em Salvar Plano: `POST plano/update/1` com corpo contendo id 41 e benefícios [{"beneficio": "asdasd"}], HTTP 200 e `verifica_erro` false. |
| 1:08 | Listagem recarregada, com cartões Planos 41 e Ativos 31 (ver CT-RF75). |

**Rede:** `POST /api/seleciona-plano/1` (HTTP 200, 347 B), `POST /api/plano/update/1` (HTTP 200, 23 B) com corpo {"id": 41, "nome": "Teste Final", "status": "inativo", benefícios [{"beneficio": "asdasd"}]} e resposta {"verifica_erro": false}.

**Conclusão:** Aprovado conforme a gravação. O plano é aberto, atualizado com HTTP 200 e a listagem recarregada. A aprovação se limita aos benefícios; a persistência após recarga e a edição dos demais campos não foram verificadas.

## Critérios de aceitação para nova execução

1. O botão de ação abre o plano com os dados atuais.
2. A alteração de qualquer campo é enviada e gravada sem erro.
3. A listagem reflete a alteração.
4. A alteração permanece após recarregar.
5. O cartão Ativos não é alterado por edição sem mudança de status (CT-RF75).

## Próxima ação e verificações complementares

Usar como regressão. Permanecem fora do cenário: edição de nome, valor, status e demais campos, persistência após recarga e o efeito no cartão Ativos (CT-RF75).

## Evidências e limites

- [Jam original — Planos](https://jam.dev/c/233c5d21-e108-4a55-b6f6-8738cb3fc6a6).
- [Arquivos, origem e limites](../Evidencias/CT-RF76_Edicao_Plano/README.md).
- [Modal Editar Plano em 1:02](../Evidencias/CT-RF76_Edicao_Plano/editar_plano_01-02.png), [Resposta de seleciona-plano](../Evidencias/CT-RF76_Edicao_Plano/resposta_seleciona_plano.png), [Corpo da requisição plano/update](../Evidencias/CT-RF76_Edicao_Plano/requisicao_update.png), [Resposta de plano/update](../Evidencias/CT-RF76_Edicao_Plano/resposta_update.png), [Lista de rede](../Evidencias/CT-RF76_Edicao_Plano/rede_lista.jpg).
- [Linha do tempo](../Evidencias/CT-RF76_Edicao_Plano/linha_do_tempo.txt).

Foram consultados os painéis Info, Console, Network e Actions do Jam e os quadros do vídeo. As capturas foram extraídas da reprodução do Jam. Não houve nova execução, inspeção do código, acesso ao banco ou correção da aplicação. O vídeo permanece no Jam.

Análise documental da gravação consultada em 15/11/2026. Esta inclusão não executa novamente o sistema e não constitui reteste. Versão da aplicação, zoom e classificação do ambiente não foram confirmados.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf76) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
