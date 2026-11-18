# 🧪 Cenário 81: Cadastro de modelo de contrato

**Caso de teste:** CT-RF81

**Módulo:** Modelos de Contrato / Cadastro

**Status:** Aprovado conforme a gravação.

**Gravação:** 15/11/2026, 21:55 BRT. **Revisão documental:** 15/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Cadastrar um modelo de contrato informando título, status e texto, e conferir que o modelo é gravado. |
| Requisito | [RF81](../Analise%20de%20requisitos.md#rf81) — referência de QA; confirmação de produto pendente. |
| Tipo / prioridade | Funcional manual / regressão; Média, proposta para triagem. |
| Defeito | Nenhum no fluxo avaliado |
| Encaminhamento | Sem reteste corretivo pendente; manter como regressão. Capturar corpo e resposta da criação e conferir o texto gravado e os campos obrigatórios. |
| Fonte | [Jam — Modelos de Contrato](https://jam.dev/c/44dbbd39-6915-45d6-8dd1-5f30c1432ca0) e [evidências locais](../Evidencias/CT-RF97_Cadastro_Modelo_Contrato/README.md). A mesma gravação é a fonte de [CT-RF82](CT-RF82_Variaveis_Preview_Modelo_Contrato.md) e [CT-RF83](CT-RF83_Listagem_Modelos_Contrato_Vazia.md). |

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
| Dados | Modelo "teste eduardo", status Ativo, texto com variáveis; base com 14 modelos antes e 15 depois. |

## Pré-condições

- Sessão autenticada com acesso à tela Modelos de Contrato.
- Modelos de contrato existentes conhecidos (15 após o cadastro da gravação) e variáveis disponíveis nos grupos Aluno, Plano, Academia e Contrato.
- Antes de uma nova execução, identificar versão, permissões e dados de referência e preparar a captura de interface e rede.

## Cenário BDD

```gherkin
Cenário: Cadastrar um modelo de contrato
  Dado que o formulário Adicionar Modelo Contrato está preenchido com título, status e texto
  Quando o usuário acionar Salvar modelo
  Então o modelo deve ser criado
  E a lista de modelos retornada pelo servidor deve incluí-lo
```

## Passos para execução ou reteste

1. Acessar Adicionar Modelo Contrato e informar título, status e texto.
2. Acionar Salvar modelo e observar a requisição de criação.
3. Conferir a resposta e a lista de modelos retornada.
4. Conferir a listagem na tela e, após recarga, o modelo criado.
5. Repetir com título em branco e texto vazio.

Este procedimento orienta a próxima execução. A evidência atual cobre o trecho gravado e os limites descritos abaixo; passos complementares não recebem resultado de execução nesta revisão.

## Resultado esperado

Salvar cria o modelo com HTTP de sucesso, o servidor passa a incluí-lo na lista e a listagem na tela o apresenta.

## Resultado obtido na gravação

Salvar modelo gerou `POST modelo-contrato/salvar/1` com HTTP 201 (corpo e resposta indisponíveis no Jam) e a navegação para a listagem; a lista devolvida por `GET modelos-contrato/1` passou a conter {"id": 15, "nome": "teste eduardo", "status": "ATIVO"}. A apresentação do modelo na tela é tratada no CT-RF83.

| Tempo | Registro |
| --- | --- |
| 0:08–0:20 | Título "teste eduardo" informado, status Ativo e texto digitado no editor. |
| 0:37 | Clique em Salvar modelo: `POST modelo-contrato/salvar/1` com HTTP 201 e navegação para /modelos-contrato. |
| 0:38–0:40 | Nova carga da lista: `GET modelos-contrato/1` (1,0 KiB) devolve 15 modelos, o último com id 15 e nome "teste eduardo". |

**Rede:** `OPTIONS` (204) e `POST /api/modelo-contrato/salvar/1` (HTTP 201), com corpo e resposta indisponíveis; depois `GET /api/modelos-contrato/1` (HTTP 200, 1,0 KiB) com 15 modelos, o último {"id": 15, "nome": "teste eduardo", "status": "ATIVO"}.

**Conclusão:** Aprovado conforme a gravação. O servidor criou o modelo (HTTP 201) e o devolveu na lista com o id 15. A aprovação se limita à criação; o corpo da criação, o texto gravado e a apresentação do modelo na listagem (CT-RF83) não foram confirmados.

## Critérios de aceitação para nova execução

1. Salvar com dados válidos cria o modelo e retorna sucesso.
2. O modelo criado é devolvido pelo servidor na lista de modelos.
3. A listagem na tela apresenta o modelo criado.
4. Título e texto obrigatórios são validados antes da gravação.
5. O texto e as variáveis são gravados sem perda.

## Próxima ação e verificações complementares

Usar como regressão. Permanecem fora do cenário: campos obrigatórios em branco, conferência do texto gravado, modelo inativo e a apresentação na listagem (CT-RF83).

## Evidências e limites

- [Jam original — Modelos de Contrato](https://jam.dev/c/44dbbd39-6915-45d6-8dd1-5f30c1432ca0).
- [Arquivos, origem e limites](../Evidencias/CT-RF97_Cadastro_Modelo_Contrato/README.md).
- [Resposta de modelos-contrato](../Evidencias/CT-RF97_Cadastro_Modelo_Contrato/lista_servidor_resposta.png), [Lista de rede](../Evidencias/CT-RF97_Cadastro_Modelo_Contrato/rede_lista.jpg).
- [Linha do tempo](../Evidencias/CT-RF97_Cadastro_Modelo_Contrato/linha_do_tempo.txt).

Foram consultados os painéis Info, Console, Network e Actions do Jam e os quadros do vídeo. As capturas foram extraídas da reprodução do Jam. Não houve nova execução, inspeção do código, acesso ao banco ou correção da aplicação. O vídeo permanece no Jam.

Análise documental da gravação consultada em 15/11/2026. Esta inclusão não executa novamente o sistema e não constitui reteste. Versão da aplicação, zoom e classificação do ambiente não foram confirmados.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf81) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
