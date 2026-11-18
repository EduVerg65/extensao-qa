# 🧪 Cenário 145: Cancelar a edição da senha de Biometria

**Caso de teste:** CT-RF145

**Módulo:** Configurações / Biometria

**Status:** Aprovado conforme a gravação.

**Gravação:** 16/11/2026, 23:02:14 BRT. **Revisão documental:** 18/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Conferir que Cancelar descarta a edição de Senha sem alterar a configuração armazenada. |
| Requisito | [RF145](../Analise%20de%20requisitos.md#rf145) — referência de QA. |
| Tipo / prioridade | Funcional manual / cancelamento · Média, proposta para triagem. |
| Defeito | Nenhum no fluxo avaliado |
| Encaminhamento | Usar como regressão do cancelamento e repetir com outros campos de Biometria em um ambiente de teste. |
| Fonte | [Jam 6 — Cancelamento da edição no formulário de Biometria](https://jam.dev/c/ccac55df-d2c8-4b11-898b-d12d87aced72) e [evidências locais](../Evidencias/CT-RF162_Configuracoes_Biometria_Cancelar_Edicao_Senha/README.md). O mascaramento é acompanhado no [BUG-046](../Relatorio-de-Bugs.md#bug-046). |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/configuracoes |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.79 / Windows 10 (x86), conforme os metadados do Jam. |
| Tela / arquivo de vídeo | Tela 1707 × 888 informada no Jam. Vídeo em 1918 × 998. |
| Duração | 22,59 s |
| Localização | Brasil. |
| Versão / zoom / classificação do ambiente | A confirmar antes de nova execução. |
| Dados | Configuração de Biometria já preenchida. Os valores dos campos de conexão e de autenticação foram omitidos. |

## Pré-condições

- Sessão autenticada com permissão de edição e credenciais fictícias no ambiente de teste.
- Identificar a versão e registrar os valores iniciais e as permissões no próximo teste.

## Cenário BDD

```gherkin
Cenário: Cancelar a edição da senha de Biometria
  Dado que a configuração de Biometria possui uma senha cadastrada
  Quando o usuário altera o valor e aciona Cancelar
  Então a aplicação deve retornar à Página Inicial sem gravar a edição
  E a consulta de Configurações deve manter o dado anterior
```

## Passos para execução ou reteste

1. Abrir Biometria com uma credencial fictícia cadastrada.
2. Alterar Senha localmente e clicar em Cancelar.
3. Verificar o retorno à Página Inicial e a ausência de salvamento.
4. Reabrir Biometria e conferir o valor anterior com o estado registrado no começo.

Este procedimento orienta a próxima execução. O resultado abaixo se limita ao trecho registrado no Jam.

## Resultado esperado

Cancelar sai de Biometria e a edição de Senha é descartada.

## Resultado obtido na gravação

Após editar Senha e sair pelo botão Cancelar, a Página Inicial foi exibida. A captura não registrou POST de configuração. Ao voltar a Biometria, o valor anterior estava no campo.

| Tempo | Registro |
| --- | --- |
| 0:00–0:09 | Edita Senha no formulário de Biometria. |
| 0:09–0:10 | Aciona Cancelar e volta à Página Inicial. |
| 0:15–0:21 | Retorna a Configurações e abre Biometria com o valor anterior. |

**Rede:**

- A captura não mostra POST para `/api/configuracoes/alterar/1` no fluxo de cancelamento.
- 0:15,93  GET `/api/configuracoes/1` (HTTP 200) ao voltar a Configurações. Valores de conexão e autenticação omitidos.

**Conclusão:** Aprovado conforme a gravação. A aprovação cobre o cancelamento. O comportamento de mascaramento de Senha está documentado no BUG-046.

## Critérios de aceitação para nova execução

1. Cancelar navega à Página Inicial.
2. O POST de salvamento não ocorre.
3. A configuração anterior é exibida ao voltar.

## Próxima ação e verificações complementares

Usar como regressão do cancelamento e repetir com outros campos de Biometria em um ambiente de teste.

## Evidências e limites

- [Jam 6 — Cancelamento da edição no formulário de Biometria](https://jam.dev/c/ccac55df-d2c8-4b11-898b-d12d87aced72).
- [Arquivos, origem e limites](../Evidencias/CT-RF162_Configuracoes_Biometria_Cancelar_Edicao_Senha/README.md).
- [Formulário antes de Cancelar, com os dados de conexão ocultos](../Evidencias/CT-RF162_Configuracoes_Biometria_Cancelar_Edicao_Senha/formulario_senha_antes_cancelar_00-08.jpg), [Aba Biometria reaberta após o cancelamento, com os mesmos campos ocultos](../Evidencias/CT-RF162_Configuracoes_Biometria_Cancelar_Edicao_Senha/biometria_reaberta_00-20.jpg).
- [Linha do tempo](../Evidencias/CT-RF162_Configuracoes_Biometria_Cancelar_Edicao_Senha/linha_do_tempo.txt).

A revisão documental se baseia nos quadros do vídeo e nos eventos capturados pelo Jam. As verificações complementares ficam para uma nova rodada de testes.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf145) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
