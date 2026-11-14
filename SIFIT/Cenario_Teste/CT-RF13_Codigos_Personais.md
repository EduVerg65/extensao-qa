# 🧪 Cenário 13: Códigos não sequenciais na lista de personais

**Caso de teste:** CT-RF13

**Módulo:** Página inicial / Personais

**Status:** A validar — regra ou contexto pendente.

**Gravação:** 14/11/2026, 00:34:25 BRT. **Revisão documental:** 14/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Identificar personais sem confundir códigos com contagem. |
| Requisito | [RF13](../Analise%20de%20requisitos.md#rf13) |
| Tipo / prioridade | Funcional manual, análise de evidências / Média, proposta para triagem. |
| Defeito | Sem defeito confirmado |
| Encaminhamento | Conclusão pendente de regra ou contexto; sem defeito confirmado. |
| Fonte | [Jam — erro na numeração dos personais](https://jam.dev/c/69330ca9-ef19-4ece-918f-31a460628016) |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/dashboard |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.51 / Windows 11 (x86). |
| Tela / arquivo de vídeo | 1920 × 957 informados no Jam; original 1918 × 956 pixels. |
| Duração | 13,89 s |
| Versão / zoom / classificação do ambiente | Não confirmados; registrar antes de nova execução. |
| Dados | Usar dados de teste conhecidos conforme as pré-condições abaixo; valores da gravação são referência histórica, sem copiar credenciais. |

## Pré-condições

- Sessão autenticada e acesso à listagem Personais.
- Confirmar se Código representa ID de cadastro ou posição na listagem.
- Antes de uma nova execução, identificar versão, permissões e dados de referência e preparar a captura de interface e rede.

## Cenário BDD

```gherkin
Cenário: Identificar personais sem confundir códigos com contagem
  Dado que o usuário consulta a lista de personais
  Quando comparar códigos, linhas e total
  Então o total deve refletir o conjunto de profissionais
  E a coluna de identificadores deve respeitar sua regra de cadastro ou numeração
```

## Passos para execução ou reteste

1. Abrir Personais pelo indicador da página inicial.
2. Contar as linhas e comparar com o total informado.
3. Conferir o significado e a unicidade dos códigos com o cadastro de referência.

Este procedimento orienta a próxima execução. A evidência atual cobre o trecho gravado e os limites descritos abaixo; passos complementares, como conferir downloads ou recarregar a sessão, não recebem resultado de execução nesta revisão.

## Resultado esperado

Se a coluna for um identificador de cadastro, lacunas são aceitáveis. Se deveria numerar linhas, a regra precisa ser esclarecida.

## Resultado obtido na gravação

A lista contém quatro personais e o total informado é quatro. A coluna Código apresenta identificadores não sequenciais, como #1, #2, #4 e #11.

**Momentos e registros:** 0:01–0:13: total 4 e quatro linhas. GET /api/colaboradores-personais/1 com HTTP 200.

**Conclusão:** A validar — regra ou contexto pendente. A definição ou confirmação da regra deve preceder aprovação ou reprovação definitiva.

## Critérios de aceitação para nova execução

1. Total confere com o número de registros considerando a paginação.
2. Identificadores são interpretados conforme sua regra, sem exigir sequência de IDs por suposição.
3. Se a intenção for numerar posições, o rótulo e a numeração deixam isso claro.

## Próxima ação e verificações complementares

Confirmar a semântica da coluna Código; quatro linhas e total quatro não sustentam um defeito de quantidade.

Nenhum defeito adicional foi criado para este cenário.

## Evidências e limites

- [Jam original — erro na numeração dos personais](https://jam.dev/c/69330ca9-ef19-4ece-918f-31a460628016).
- [Vídeo original](../Evidencias/CT-RF13_Codigos_Personais/video.webm).
- [Resumo, origem e integridade](../Evidencias/CT-RF13_Codigos_Personais/README.md).
- [Cronologia do Jam](../Evidencias/CT-RF13_Codigos_Personais/linha_do_tempo.txt).

Não foi demonstrada uma divergência entre o total e a quantidade listada. A numeração não sequencial por si só não confirma defeito.

Análise documental das gravações já consultadas em 14/11/2026 (metadados, cronologia e quadros distribuídos pelo vídeo). Esta inclusão não executa novamente o sistema, não corrige a aplicação e não constitui reteste. Versão da aplicação, zoom e classificação do ambiente não foram confirmados.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
