# 🧪 Cenário 15: Edição de modalidade sem ação de salvar visível

**Caso de teste:** CT-RF15

**Módulo:** SifitBox / Modalidades

**Status:** Reprovado nas evidências.

**Gravação:** 14/11/2026, 00:38:19 BRT. **Revisão documental:** 14/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Permitir concluir e cancelar a edição de modalidade. |
| Requisito | [RF15](../Analise%20de%20requisitos.md#rf15) |
| Tipo / prioridade | Funcional manual, análise de evidências / Média, proposta para triagem. |
| Defeito | [BUG-008](../Relatorio-de-Bugs.md#bug-008) |
| Encaminhamento | Aberto; reteste pendente após correção. |
| Fonte | [Jam — Sem botão para editar modalidades](https://jam.dev/c/951efaf8-bf32-44b0-b640-a2935a6b554a) |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/sifitbox/turmas |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.51 / Windows 11 (x86). |
| Tela / arquivo de vídeo | 1920 × 957 informados no Jam; original 1918 × 956 pixels. |
| Duração | 14,73 s |
| Versão / zoom / classificação do ambiente | Não confirmados; registrar antes de nova execução. |
| Dados | Usar dados de teste conhecidos conforme as pré-condições abaixo; valores da gravação são referência histórica, sem copiar credenciais. |

## Pré-condições

- Sessão autenticada com permissão para editar modalidades.
- Modalidade de teste com nome, descrição e status conhecidos.
- Antes de uma nova execução, identificar versão, permissões e dados de referência e preparar a captura de interface e rede.

## Cenário BDD

```gherkin
Cenário: Permitir concluir e cancelar a edição de modalidade
  Dado que o usuário pode editar uma modalidade existente
  Quando clicar no lápis e alterar os campos
  Então a interface deve oferecer ações claras para salvar e cancelar
  E ao salvar deve confirmar e apresentar os valores persistidos
```

## Passos para execução ou reteste

1. Clicar no lápis de uma modalidade.
2. Verificar o preenchimento dos campos e alterar um valor de teste.
3. Localizar e usar a ação de salvar; conferir confirmação e recarregar a lista para validar persistência.

Este procedimento orienta a próxima execução. A evidência atual cobre o trecho gravado e os limites descritos abaixo; passos complementares, como conferir downloads ou recarregar a sessão, não recebem resultado de execução nesta revisão.

## Resultado esperado

Oferecer ações visíveis de salvar e cancelar e confirmar a atualização.

## Resultado obtido na gravação

Há ícones de lápis na lista. Ao clicar, os campos superiores são preenchidos para edição, mas não aparece uma ação clara para salvar ou concluir a alteração nos quadros analisados.

**Momentos e registros:** 0:03–0:13: cliques no lápis, campos preenchidos e alternância entre Ativo e Inativo. Nenhuma chamada de atualização foi capturada.

**Conclusão:** Reprovado nas evidências. O defeito associado descreve a manifestação observada, sem atribuir uma causa técnica não comprovada.

## Critérios de aceitação para nova execução

1. O lápis carrega os dados do registro selecionado.
2. Salvar e cancelar são ações visíveis e compreensíveis.
3. Salvar persiste os dados; cancelar preserva os valores anteriores.

## Próxima ação e verificações complementares

Verificar o fluxo de conclusão da edição e retestar persistência. A evidência reprova a clareza da ação de salvar; não afirma que o ícone de editar inexiste.

O [BUG-008](../Relatorio-de-Bugs.md#bug-008) permanece aberto. Severidade **Média** e prioridade **Média** são propostas para triagem; encerrar somente após evidências de reteste em uma versão identificada.

## Evidências e limites

- [Jam original — Sem botão para editar modalidades](https://jam.dev/c/951efaf8-bf32-44b0-b640-a2935a6b554a).
- [Vídeo original](../Evidencias/CT-RF15_Edicao_Modalidade/video.webm).
- [Resumo, origem e integridade](../Evidencias/CT-RF15_Edicao_Modalidade/README.md).
- [Cronologia do Jam](../Evidencias/CT-RF15_Edicao_Modalidade/linha_do_tempo.txt).

O título original diz “Sem botão para editar modalidades”, mas o lápis existe. A dificuldade demonstrada é concluir a edição; a gravação não prova ausência de toda alternativa de salvamento.

Análise documental das gravações já consultadas em 14/11/2026 (metadados, cronologia e quadros distribuídos pelo vídeo). Esta inclusão não executa novamente o sistema, não corrige a aplicação e não constitui reteste. Versão da aplicação, zoom e classificação do ambiente não foram confirmados.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
