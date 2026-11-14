# 🧪 Cenário 16: Ação de lixeira inativa modalidades e mantém registros na lista

**Caso de teste:** CT-RF16

**Módulo:** SifitBox / Modalidades

**Status:** A validar — regra ou contexto pendente.

**Gravação:** 14/11/2026, 00:39:31 BRT. **Revisão documental:** 14/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Comunicar e aplicar a regra de remoção de modalidade. |
| Requisito | [RF16](../Analise%20de%20requisitos.md#rf16) |
| Tipo / prioridade | Funcional manual, análise de evidências / Média, proposta para triagem. |
| Defeito | Sem defeito confirmado |
| Encaminhamento | Conclusão pendente de regra ou contexto; sem defeito confirmado. |
| Fonte | [Jam — Botões apenas para desativar e não excluir! Apenas inativa e não exclui.](https://jam.dev/c/0f55f76a-cd31-4cee-93da-23c13b1ba637) |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/sifitbox/turmas |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.51 / Windows 11 (x86). |
| Tela / arquivo de vídeo | 1920 × 957 informados no Jam; original 1918 × 956 pixels. |
| Duração | 18,61 s |
| Versão / zoom / classificação do ambiente | Não confirmados; registrar antes de nova execução. |
| Dados | Usar dados de teste conhecidos conforme as pré-condições abaixo; valores da gravação são referência histórica, sem copiar credenciais. |

## Pré-condições

- Sessão autenticada e modalidade descartável na base de teste.
- Confirmar se a ação realiza exclusão lógica, inativação ou exclusão definitiva e como trata vínculos.
- Antes de uma nova execução, identificar versão, permissões e dados de referência e preparar a captura de interface e rede.

## Cenário BDD

```gherkin
Cenário: Comunicar e aplicar a regra de remoção de modalidade
  Dado que a regra da ação de lixeira está definida para modalidades
  Quando solicitar a remoção de uma modalidade de teste
  Então o sistema deve informar o efeito de excluir ou inativar
  E o estado e a listagem resultantes devem corresponder a essa regra
```

## Passos para execução ou reteste

1. Registrar o status e os vínculos da modalidade de teste.
2. Acionar a lixeira conforme a regra e eventual confirmação definida pelo produto.
3. Verificar o estado final e os filtros da lista; não repetir a ação para exigir exclusão física sem regra confirmada.

Este procedimento orienta a próxima execução. A evidência atual cobre o trecho gravado e os limites descritos abaixo; passos complementares, como conferir downloads ou recarregar a sessão, não recebem resultado de execução nesta revisão.

## Resultado esperado

O nome, o ícone e a confirmação da ação devem informar se o efeito é desativar ou excluir definitivamente.

## Resultado obtido na gravação

As modalidades passam a aparecer como inativas e continuam na listagem, mesmo após novos cliques. A linha do tempo registra chamadas a /api/sifitbox/modalidades/excluir/1 e recargas das listas com HTTP 200.

**Momentos e registros:** 0:02–0:15: ações de lixeira e novas consultas. 0:10–0:18: registros inativos ainda presentes.

**Conclusão:** A validar — regra ou contexto pendente. A definição ou confirmação da regra deve preceder aprovação ou reprovação definitiva.

## Critérios de aceitação para nova execução

1. Nome, ícone e confirmação da ação comunicam seu efeito.
2. O estado final corresponde à regra de inativação ou exclusão acordada.
3. Vínculos e filtros têm tratamento definido; manter registros inativos pode ser comportamento válido.

## Próxima ação e verificações complementares

Confirmar a exclusão lógica e a nomenclatura da ação; registrar defeito apenas se houver divergência com a regra definida.

Nenhum defeito adicional foi criado para este cenário.

## Evidências e limites

- [Jam original — Botões apenas para desativar e não excluir! Apenas inativa e não exclui.](https://jam.dev/c/0f55f76a-cd31-4cee-93da-23c13b1ba637).
- [Vídeo original](../Evidencias/CT-RF16_Exclusao_Modalidade/video.webm).
- [Resumo, origem e integridade](../Evidencias/CT-RF16_Exclusao_Modalidade/README.md).
- [Cronologia do Jam](../Evidencias/CT-RF16_Exclusao_Modalidade/linha_do_tempo.txt).

A inativação pode ser uma exclusão lógica prevista pelo sistema. É necessário confirmar a regra do produto antes de exigir exclusão definitiva. Nenhuma exclusão foi executada nesta revisão.

Análise documental das gravações já consultadas em 14/11/2026 (metadados, cronologia e quadros distribuídos pelo vídeo). Esta inclusão não executa novamente o sistema, não corrige a aplicação e não constitui reteste. Versão da aplicação, zoom e classificação do ambiente não foram confirmados.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
