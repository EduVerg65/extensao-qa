# 🧪 Cenário 83: Listagem de modelos de contrato aparece vazia com 15 modelos retornados

**Caso de teste:** CT-RF83

**Módulo:** Modelos de Contrato / Listagem

**Status:** Reprovado nas evidências — tabela vazia com 15 modelos retornados; defeito em triagem.

**Gravação:** 15/11/2026, 21:55 BRT. **Revisão documental:** 15/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Apresentar na tela a lista de modelos de contrato retornada pelo servidor, com código, nome e status. |
| Requisito | [RF83](../Analise%20de%20requisitos.md#rf83) — referência de QA; confirmação de produto pendente. |
| Tipo / prioridade | Funcional manual / manifestação observada; Alta, proposta para triagem. |
| Defeito | [BUG-040](../Relatorio-de-Bugs.md#bug-040), em triagem. |
| Encaminhamento | Reproduzir com o painel de rede aberto, conferir a resposta de modelos-contrato e o estado da tabela e investigar por que os registros não são renderizados; retestar após correção. |
| Fonte | [Jam — Modelos de Contrato](https://jam.dev/c/44dbbd39-6915-45d6-8dd1-5f30c1432ca0) e [evidências locais](../Evidencias/CT-RF98_Listagem_Modelos_Contrato_Vazia/README.md). A mesma gravação é a fonte de [CT-RF82](CT-RF82_Variaveis_Preview_Modelo_Contrato.md) e [CT-RF81](CT-RF81_Cadastro_Modelo_Contrato.md). |

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
| Dados | Lista devolvida pelo servidor com 15 modelos (ids 1 a 15, incluindo "teste eduardo"); tabela com colunas Código, Nome e Status. |

## Pré-condições

- Sessão autenticada com acesso à tela Modelos de Contrato.
- Modelos de contrato existentes conhecidos (15 após o cadastro da gravação) e variáveis disponíveis nos grupos Aluno, Plano, Academia e Contrato.
- Antes de uma nova execução, identificar versão, permissões e dados de referência e preparar a captura de interface e rede.

## Cenário BDD

```gherkin
Cenário: Apresentar os modelos de contrato na listagem
  Dado que o servidor retornou a lista de modelos de contrato
  Quando a tela Modelos Contrato for carregada
  Então a tabela deve apresentar uma linha por modelo com código, nome e status
  E o modelo recém-criado deve aparecer
```

## Passos para execução ou reteste

1. Acessar Modelos Contrato com o painel de rede aberto e registrar a resposta de modelos-contrato.
2. Conferir a tabela da tela com a resposta do servidor.
3. Criar um modelo e voltar à listagem.
4. Recarregar a página e conferir novamente.
5. Acionar a ordenação e o contador de registros, se existirem.

Este procedimento orienta a próxima execução. A evidência atual cobre o trecho gravado e os limites descritos abaixo; passos complementares não recebem resultado de execução nesta revisão.

## Resultado esperado

A tabela apresenta uma linha para cada modelo retornado pelo servidor, com código, nome e status, inclusive o recém-criado.

## Resultado obtido na gravação

O servidor devolveu 15 modelos em `GET modelos-contrato/1`, mas a tabela da tela Modelos Contrato apresentou apenas o cabeçalho (Código, Nome e Status), sem linhas e sem mensagem, tanto antes do cadastro (0:00) quanto depois (0:39 a 0:49).

| Tempo | Registro |
| --- | --- |
| 0:00 | Tela Modelos Contrato com a tabela vazia (apenas cabeçalho) e o botão Adicionar Modelo Contrato. |
| 0:38–0:40 | Após salvar, a lista é recarregada (`GET modelos-contrato/1`, 15 modelos) e a tabela continua sem linhas. |
| 0:42–0:43 | Cliques na tabela e no cabeçalho sem efeito visível. |
| 0:45–0:49 | Tabela ainda vazia, sem mensagem de estado vazio. |

**Rede:** `GET /api/modelos-contrato/1` (HTTP 200, 1,0 KiB) devolve lista com 15 objetos {"id", "nome", "status"}, de {"id": 1, "nome": "ASA", "status": "ATIVO"} a {"id": 15, "nome": "teste eduardo", "status": "ATIVO"}.

**Conclusão:** Reprovado nas evidências. A resposta do servidor contém 15 modelos, mas a tabela não os apresenta. A causa não foi determinada: pode ser falha de renderização, divergência no formato dos dados ou filtro implícito.

## Critérios de aceitação para nova execução

1. A tabela apresenta uma linha para cada modelo retornado pelo servidor.
2. O modelo recém-criado aparece na listagem sem recarregar manualmente.
3. Código, nome e status são exibidos corretamente.
4. Sem modelos, a tela apresenta mensagem explícita de estado vazio.
5. A listagem permanece correta após recarregar a página.

## Próxima ação e verificações complementares

Registrar o BUG-040 em triagem; reproduzir comparando a resposta de modelos-contrato com a tabela e investigar a renderização e o formato dos dados com a equipe de desenvolvimento.

## Evidências e limites

- [Jam original — Modelos de Contrato](https://jam.dev/c/44dbbd39-6915-45d6-8dd1-5f30c1432ca0).
- [Arquivos, origem e limites](../Evidencias/CT-RF98_Listagem_Modelos_Contrato_Vazia/README.md).
- [Tela Modelos Contrato em 0:39](../Evidencias/CT-RF98_Listagem_Modelos_Contrato_Vazia/lista_vazia_00-39.png), [Tela Modelos Contrato em 0:45](../Evidencias/CT-RF98_Listagem_Modelos_Contrato_Vazia/lista_vazia_00-45.png), [Tela Modelos Contrato em 0:49](../Evidencias/CT-RF98_Listagem_Modelos_Contrato_Vazia/lista_vazia_00-49.png), [Resposta de modelos-contrato](../Evidencias/CT-RF98_Listagem_Modelos_Contrato_Vazia/lista_servidor_resposta.png), [Lista de rede](../Evidencias/CT-RF98_Listagem_Modelos_Contrato_Vazia/rede_lista.jpg).
- [Linha do tempo](../Evidencias/CT-RF98_Listagem_Modelos_Contrato_Vazia/linha_do_tempo.txt).

Foram consultados os painéis Info, Console, Network e Actions do Jam e os quadros do vídeo. As capturas foram extraídas da reprodução do Jam. Não houve nova execução, inspeção do código, acesso ao banco ou correção da aplicação. O vídeo permanece no Jam.

Análise documental da gravação consultada em 15/11/2026. Esta inclusão não executa novamente o sistema e não constitui reteste. Versão da aplicação, zoom e classificação do ambiente não foram confirmados.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf83) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
