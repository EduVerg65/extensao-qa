# 🧪 Cenário 156: Cadastrar um modelo de ficha com nome e personal

**Caso de teste:** CT-RF156

**Módulo:** Configurações / Modelo Ficha / Cadastro

**Status:** Reprovado nas evidências.

**Gravação:** 16/11/2026, 22:18:52 BRT. **Revisão documental:** 17/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Cadastrar um novo modelo de ficha com nome e personal e disponibilizá-lo na listagem. |
| Requisito | [RF156](../Analise%20de%20requisitos.md#rf156) — referência de QA. |
| Tipo / prioridade | Funcional manual / cadastro · Alta, proposta para triagem. |
| Defeito | [BUG-045](../Relatorio-de-Bugs.md#bug-045), em triagem |
| Encaminhamento | Reproduzir com dados de teste distintos, investigar a falha do endpoint e conferir a listagem e o vínculo após a correção. |
| Fonte | [Jam — PED-24 — Cadastro de modelo de ficha](https://jam.dev/c/04e2cae2-f3f2-43ff-8361-b3b9d9f50d35) e [evidências locais](../Evidencias/CT-RF121_Cadastro_Modelo_Ficha_Erro_500/README.md). Ver também [CT-RF149](CT-RF149_Modelo_Ficha_Sem_Nome.md) e [CT-RF150](CT-RF150_Cancelar_Cadastro_Modelo_Ficha.md). |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/fichas-treino-modelo |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.79 / Windows 10 (x86), conforme os metadados do Jam. |
| Tela / arquivo de vídeo | Tela 1536 × 799 informada no Jam. Vídeo em 1918 × 998. |
| Duração | 21,55 s |
| Localização | Brasil. |
| Versão / zoom / classificação do ambiente | A confirmar antes de nova execução. |
| Dados | Nome do modelo Pedro-01 e um personal selecionado. A listagem inicial mostrava 0 registros. |

## Pré-condições

- Sessão autenticada com acesso a Modelos de Ficha, permissão para cadastrar e um personal disponível no formulário.
- Identificar a versão e registrar os valores iniciais e as permissões no próximo teste.

## Cenário BDD

```gherkin
Cenário: Cadastrar um modelo de ficha com nome e personal
  Dado que o usuário tem acesso ao formulário Novo Modelo de Ficha e um personal está disponível
  Quando o usuário preencher o nome, selecionar o personal e clicar em Criar Modelo
  Então o sistema deve criar o modelo e confirmar o resultado
  E o modelo deve ficar disponível na listagem com o personal selecionado
```

## Passos para execução ou reteste

1. Abrir Modelos de Ficha e acionar o botão de adição.
2. Preencher o nome do modelo e selecionar um personal disponível.
3. Clicar em Criar Modelo e registrar o retorno da interface e da API.
4. Em reteste, recarregar a listagem para conferir o registro e o vínculo com o personal.

Este procedimento orienta a próxima execução. O resultado abaixo se limita ao trecho registrado no Jam.

## Resultado esperado

O cadastro é concluído com o personal selecionado, a interface confirma a criação e o novo modelo pode ser localizado após recarga.

## Resultado obtido na gravação

O envio com Pedro-01 e um personal selecionado produziu HTTP 500 em `POST /api/adicionar-ficha/1`. O servidor retornou `verifica_erro: true` e “Erro interno inesperado.” A interface exibiu “Erro ao salvar modelo.” e a gravação não mostrou confirmação de criação.

| Tempo | Registro |
| --- | --- |
| 0:00–0:03 | Listagem inicialmente vazia. Usuário abre Novo Modelo de Ficha. |
| 0:04–0:16 | Informa Pedro-01 e seleciona um personal. |
| 0:17–0:19 | Aciona Criar Modelo. A chamada retorna HTTP 500 e a interface exibe o diálogo de erro. |
| 0:20 | Aciona Fechar no diálogo. |

**Rede:**

- 0:17,62  POST `/api/adicionar-ficha/1` (HTTP 500). O corpo registra `tipo_ficha: modelo`, `nome_ficha` e `nome_modelo` com Pedro-01 e `prescritor_id` preenchido.
- A resposta traz `verifica_erro: true` e `mensagem: "Erro interno inesperado."`.

**Conclusão:** Reprovado nas evidências. Uma tentativa foi registrada. A gravação não confirma causa técnica, persistência parcial ou abrangência para outros nomes e personais. Os CT-RF149 e CT-RF150 cobrem, respectivamente, a validação de nome vazio e o cancelamento.

## Critérios de aceitação para nova execução

1. O formulário envia o nome e o personal escolhidos.
2. A operação termina com sucesso e a interface confirma o cadastro.
3. Após recarga, a listagem encontra o modelo com o personal selecionado.

## Próxima ação e verificações complementares

Reproduzir com dados de teste distintos, investigar a falha do endpoint e conferir a listagem e o vínculo após a correção.

## Evidências e limites

- [Jam original — PED-24 — Cadastro de modelo de ficha](https://jam.dev/c/04e2cae2-f3f2-43ff-8361-b3b9d9f50d35).
- [Arquivos, origem e limites](../Evidencias/CT-RF121_Cadastro_Modelo_Ficha_Erro_500/README.md).
- [Formulário preenchido antes de Criar Modelo](../Evidencias/CT-RF121_Cadastro_Modelo_Ficha_Erro_500/modelo_preenchido_00-16.jpg), [Aviso Erro ao salvar modelo após o HTTP 500](../Evidencias/CT-RF121_Cadastro_Modelo_Ficha_Erro_500/erro_salvar_modelo_00-19.jpg).
- [Linha do tempo](../Evidencias/CT-RF121_Cadastro_Modelo_Ficha_Erro_500/linha_do_tempo.txt).

A revisão documental se baseia nos quadros do vídeo e nos eventos capturados pelo Jam. As verificações complementares ficam para uma nova rodada de testes.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf156) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
