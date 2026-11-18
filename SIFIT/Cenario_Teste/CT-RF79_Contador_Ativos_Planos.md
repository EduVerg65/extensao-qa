# 🧪 Cenário 79: Cartão Ativos de Planos aumenta ao cadastrar e editar planos inativos

**Caso de teste:** CT-RF79

**Módulo:** Planos / Cartões de resumo

**Status:** Reprovado nas evidências — cartão Ativos aumenta com planos inativos; defeito em triagem.

**Gravação:** 15/11/2026, 21:54 BRT. **Revisão documental:** 15/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Manter o cartão Ativos coerente com o status dos planos: planos inativos não devem ser contados como ativos. |
| Requisito | [RF79](../Analise%20de%20requisitos.md#rf79) — referência de QA; confirmação de produto pendente. |
| Tipo / prioridade | Funcional manual / manifestação observada; Média, proposta para triagem. |
| Defeito | [BUG-041](../Relatorio-de-Bugs.md#bug-041), em triagem. |
| Encaminhamento | Reproduzir criando e editando um plano inativo com a base e o contrato do cartão conhecidos, conferindo o cartão antes e depois e a lista de planos por status; retestar após correção. |
| Fonte | [Jam — Planos](https://jam.dev/c/233c5d21-e108-4a55-b6f6-8738cb3fc6a6) e [evidências locais](../Evidencias/CT-RF102_Contador_Ativos_Planos/README.md). A mesma gravação é a fonte de [CT-RF77](CT-RF77_Filtros_Planos.md), [CT-RF76](CT-RF76_Tema_Notificacoes_Planos.md), [CT-RF78](CT-RF78_Cadastro_Plano.md) e [CT-RF80](CT-RF80_Edicao_Plano.md). |

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
| Dados | Cartões antes da operação: Planos 40, Ativos 29; plano criado "rerererere" com status inativo (cartões depois: Planos 41, Ativos 30); plano 41 "Teste Final" inativo editado (cartões depois: Planos 41, Ativos 31). |

## Pré-condições

- Sessão autenticada com acesso à tela Planos.
- Base de planos conhecida (40 planos, 29 ativos e 9 alunos em planos no início da gravação), com grupos e funções cadastrados.
- Antes de uma nova execução, identificar versão, permissões e dados de referência e preparar a captura de interface e rede.

## Cenário BDD

```gherkin
Cenário: Manter o cartão Ativos coerente com o status
  Dado que o cartão Ativos apresenta o total de planos ativos
  Quando o usuário cadastrar um plano com status Inativo ou editar um plano inativo
  Então o cartão Ativos não deve aumentar
  E o cartão Planos deve acompanhar apenas o total de registros
```

## Passos para execução ou reteste

1. Acessar Planos e registrar os cartões Planos e Ativos e a quantidade de planos ativos na listagem.
2. Cadastrar um plano com status Inativo e conferir os cartões.
3. Editar o plano inativo sem alterar o status e conferir os cartões.
4. Comparar o cartão Ativos com a contagem de planos ativos da listagem.
5. Repetir com um plano ativo e com a alteração de status.

Este procedimento orienta a próxima execução. A evidência atual cobre o trecho gravado e os limites descritos abaixo; passos complementares não recebem resultado de execução nesta revisão.

## Resultado esperado

O cartão Ativos aumenta apenas quando um plano passa a ficar ativo; cadastrar ou editar um plano inativo não altera o cartão Ativos, e o cartão Planos acompanha o total de registros.

## Resultado obtido na gravação

O plano cadastrado com `status` "inativo" elevou Planos de 40 para 41 e Ativos de 29 para 30; a edição do plano 41, que permaneceu "inativo" na requisição de atualização, elevou Ativos de 30 para 31.

| Tempo | Registro |
| --- | --- |
| 0:03 | Cartões antes da operação: Planos 40, Ativos 29, Alunos em Planos 9. |
| 0:51–0:53 | Plano "rerererere" cadastrado com status Inativo (corpo `"status": "inativo"`): Planos 41 e Ativos 30. |
| 1:01–1:08 | Plano 41 "Teste Final" (status `inativo`) editado e salvo sem alterar o status: Planos 41 e Ativos 31. |

**Rede:** `POST /api/plano/salvar/1` com `"status": "inativo"` (id 66) e `POST /api/plano/update/1` com `"status": "inativo"` (id 41); `POST /api/seleciona-plano/1` devolve o plano 41 com `"status": "inativo"`.

**Conclusão:** Reprovado nas evidências. O cartão Ativos aumentou a cada operação com planos de status inativo (de 29 para 31), o que contraria o rótulo do cartão. A regra de cálculo do cartão não foi informada; se o cartão contar outra coisa, o rótulo deve ser revisto.

## Critérios de aceitação para nova execução

1. O cartão Ativos conta apenas planos com status ativo.
2. Cadastrar um plano inativo não altera o cartão Ativos.
3. Editar um plano sem alterar o status não altera o cartão Ativos.
4. O cartão Planos acompanha o total de registros.
5. O cartão é recalculado de forma consistente após recarregar a página.

## Próxima ação e verificações complementares

Registrar o BUG-041 em triagem; reproduzir com a base e o contrato do cartão conhecidos, comparando o cartão com a contagem por status da listagem, e investigar a origem do cálculo.

## Evidências e limites

- [Jam original — Planos](https://jam.dev/c/233c5d21-e108-4a55-b6f6-8738cb3fc6a6).
- [Arquivos, origem e limites](../Evidencias/CT-RF102_Contador_Ativos_Planos/README.md).
- [Cartões em 0:03](../Evidencias/CT-RF102_Contador_Ativos_Planos/cartoes_antes_00-03.png), [Cartões em 0:53](../Evidencias/CT-RF102_Contador_Ativos_Planos/cartoes_apos_cadastro_00-53.png), [Cartões em 1:08](../Evidencias/CT-RF102_Contador_Ativos_Planos/cartoes_apos_edicao_01-08.png), [Corpo da requisição plano/salvar](../Evidencias/CT-RF102_Contador_Ativos_Planos/requisicao_salvar.png), [Lista de rede](../Evidencias/CT-RF102_Contador_Ativos_Planos/rede_lista.jpg).
- [Linha do tempo](../Evidencias/CT-RF102_Contador_Ativos_Planos/linha_do_tempo.txt).

Foram consultados os painéis Info, Console, Network e Actions do Jam e os quadros do vídeo. As capturas foram extraídas da reprodução do Jam. Não houve nova execução, inspeção do código, acesso ao banco ou correção da aplicação. O vídeo permanece no Jam.

Análise documental da gravação consultada em 15/11/2026. Esta inclusão não executa novamente o sistema e não constitui reteste. Versão da aplicação, zoom e classificação do ambiente não foram confirmados.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf79) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
