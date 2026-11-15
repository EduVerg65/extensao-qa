# 🧪 Cenário 23: Exclusão de exercício

**Caso de teste:** CT-RF23

**Módulo:** Exercícios / Exclusão

**Status:** Aprovado no trecho consultado.

**Gravação:** 15/11/2026, 15:40 BRT, conforme Info do Jam. **Revisão documental:** 15/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Excluir um exercício permitido e atualizar a biblioteca e seus totais. |
| Requisito | [RF23](../Analise%20de%20requisitos.md#rf23) — referência de QA; confirmação de produto pendente. |
| Tipo / prioridade | Funcional manual, análise de evidências / Média, proposta para triagem. |
| Defeito | Nenhum confirmado no trecho consultado. |
| Encaminhamento | Manter como regressão. Em nova execução, recarregar a página para conferir persistência e testar separadamente as regras para exercícios vinculados. |
| Fonte | [Jam — Exclusão de exercício](https://jam.dev/c/32adfca3-489f-4a4b-a08d-933c1d1a3c32) |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/exercicios |
| Backend observado na rede | https://backendsifit.centrion.com.br |
| Navegador / sistema | Edge 157.0.8103.80 / Windows 11 (x86), conforme Info. |
| Tela / duração | 1912 × 960 informados no Jam / aproximadamente 6 s. |
| Versão / zoom / classificação do ambiente | Não confirmados; registrar antes de nova execução. |
| Dados | Utilizar registros e arquivos de teste autorizados; os valores da gravação são referência histórica. |

## Pré-condições

- Sessão autenticada com acesso a Exercícios e permissão para a operação.
- Exercício de teste existente, sem impedimento conhecido para exclusão.
- Antes de nova execução, identificar versão, ambiente, permissões e dados de referência.

## Cenário BDD

```gherkin
Cenário: Excluir um exercício permitido e atualizar a biblioteca e seus totais
  Dado que o usuário possui permissão para a operação em Exercícios
  E que os dados de teste estão preparados
  Quando acionar a exclusão do exercício de teste
  Então o exercício deve deixar de aparecer na biblioteca
  E o total deve diminuir em uma unidade
```

## Passos para execução ou reteste

1. Identificar o exercício de teste e registrar o total da biblioteca e do grupo.
2. Acionar a opção de exclusão do exercício.
3. Confirmar a operação, se o sistema solicitar.
4. Conferir a ausência do registro e a atualização dos totais.

Este procedimento orienta a próxima execução. Verificações complementares não visíveis nos quadros consultados não recebem resultado de execução nesta revisão.

## Resultado esperado

O sistema deve remover o exercício permitido da biblioteca e atualizar os totais. Se houver impedimento, deve explicá-lo sem indicar sucesso indevido.

## Resultado obtido na gravação

No quadro de aproximadamente 0:02, a biblioteca apresenta total 11 e o exercício Levantamento de Peso. No quadro final, em aproximadamente 0:06, esse registro não aparece e o total é 10. A lista continua contendo Levantamento de Peso 02, registro distinto.

**Momentos e registros:** quadros do player, metadados Info e listagem Network consultados. A aba Network apresenta três entradas POST com HTTP 200 e uma OPTIONS com HTTP 204 no domínio backendsifit.centrion.com.br. Os caminhos e corpos não foram inspecionados; não se atribui uma operação específica a cada entrada.

**Conclusão:** Aprovado no trecho consultado.

## Critérios de aceitação para nova execução

1. O registro selecionado deixa de aparecer na biblioteca.
2. O total diminui em uma unidade e os demais exercícios são preservados.
3. Uma restrição de exclusão, quando aplicável, é apresentada claramente.

## Próxima ação e verificações complementares

Manter como regressão. Em nova execução, recarregar a página para conferir persistência e testar separadamente as regras para exercícios vinculados.

## Evidências e limites

- [Jam original](https://jam.dev/c/32adfca3-489f-4a4b-a08d-933c1d1a3c32).
- [Resumo e origem da evidência](../Evidencias/CT-RF23_Exclusao_Exercicio/README.md).
- [Cronologia documental](../Evidencias/CT-RF23_Exclusao_Exercicio/linha_do_tempo.txt).

Não foram confirmados o diálogo de confirmação, a persistência após recarregar ou os efeitos sobre fichas de treino vinculadas.

A análise utiliza quadros consultados e a listagem de rede; não corresponde a uma revisão quadro a quadro de todo o vídeo. Não houve nova execução no SIFIT, reteste ou inspeção do código. Vídeo original e capturas não foram copiados para o repositório; não há hash do vídeo nesta inclusão. Não foram reproduzidos credenciais, tokens ou corpos de autenticação.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)

