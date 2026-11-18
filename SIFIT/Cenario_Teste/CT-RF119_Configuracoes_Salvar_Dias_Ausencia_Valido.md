# 🧪 Cenário 119: Salvar um valor válido de dias de ausência

**Caso de teste:** CT-RF119

**Módulo:** Configurações / Home / Dias de ausência

**Status:** Aprovado conforme a gravação.

**Gravação:** 16/11/2026, 21:59:22 BRT. **Revisão documental:** 17/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Salvar um valor inteiro positivo de dias de ausência e confirmar a persistência após recarregar Configurações. |
| Requisito | [RF119](../Analise%20de%20requisitos.md#rf119) — referência de QA. |
| Tipo / prioridade | Funcional manual / salvamento e persistência · Média, proposta para triagem. |
| Defeito | Nenhum no fluxo avaliado |
| Encaminhamento | Usar como regressão de salvamento. Verificar os limites do campo e o impacto na listagem de clientes ausentes. |
| Fonte | [Jam — PED-16 — Salvar dias de ausência](https://jam.dev/c/12d6bba7-a67e-4882-86a5-4dd08d194af2) e [evidências locais](../Evidencias/CT-RF125_Configuracoes_Salvar_Dias_Ausencia_Valido/README.md). |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/configuracoes |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.79 / Windows 10 (x86), conforme os metadados do Jam. |
| Tela / arquivo de vídeo | Tela 1536 × 799 informada no Jam. Vídeo em 1918 × 998. |
| Duração | 29,34 s |
| Localização | Brasil. |
| Versão / zoom / classificação do ambiente | A confirmar antes de nova execução. |
| Dados | Valor inicial 1100. Valor testado 15. O valor inicial foi restaurado no fim. |

## Pré-condições

- Sessão autenticada com permissão para editar Configurações e valor inicial conhecido.
- Identificar a versão e registrar os valores iniciais e as permissões no próximo teste.

## Cenário BDD

```gherkin
Cenário: Salvar um valor válido de dias de ausência
  Dado que o campo de dias de ausência tem um valor salvo
  Quando o usuário preencher um inteiro positivo aceito e salvar Configurações
  Então a operação deve ser concluída com o valor informado
  E a próxima recarga deve exibir o mesmo valor
```

## Passos para execução ou reteste

1. Abrir Configurações > Home e anotar o valor inicialmente salvo.
2. Preencher o campo com 15 e clicar em Salvar Configurações.
3. Recarregar e conferir o campo e a consulta de Configurações.
4. Restaurar e salvar o valor inicial e confirmar após nova recarga.

Este procedimento orienta a próxima execução. O resultado abaixo se limita ao trecho registrado no Jam.

## Resultado esperado

O valor 15 é salvo e exibido após recarregar. Ao restaurar o valor inicial, a próxima leitura apresenta o valor restaurado.

## Resultado obtido na gravação

O POST com 15 retornou HTTP 200 e `verifica_erro: false`. A recarga exibiu 15 e o GET devolveu `dias_ausente: 15`. O valor inicial 1100 foi reenviado e confirmado na recarga seguinte.

| Tempo | Registro |
| --- | --- |
| 0:00–0:09 | Substitui o valor inicial 1100 por 15. |
| 0:09–0:16 | Salva e recarrega. A interface apresenta 15. |
| 0:18–0:22 | Volta a informar 1100 e salva. |
| 0:24–0:27 | Recarrega e confirma o retorno de 1100. |

**Rede:**

- 0:10,10  POST `/api/configuracoes/alterar/1` (HTTP 200), com `dias_ausente=15` e `verifica_erro: false`.
- 0:13,46  GET `/api/configuracoes/1` (HTTP 200), com `dias_ausente: 15`.
- 0:21,62  POST (HTTP 200), com `dias_ausente=1100`.
- 0:25,01  GET (HTTP 200), com `dias_ausente: 1100`.

**Conclusão:** Aprovado conforme a gravação. A evidência confirma persistência para o valor testado e restauração do valor original observado. A faixa completa e o efeito na contagem de clientes ausentes exigem outros casos.

## Critérios de aceitação para nova execução

1. Um valor válido é enviado e confirmado pela API.
2. Depois da recarga, o formulário apresenta o valor informado.
3. O valor inicial pode ser restaurado e lido após nova recarga.

## Próxima ação e verificações complementares

Usar como regressão de salvamento. Verificar os limites do campo e o impacto na listagem de clientes ausentes.

## Evidências e limites

- [Jam original — PED-16 — Salvar dias de ausência](https://jam.dev/c/12d6bba7-a67e-4882-86a5-4dd08d194af2).
- [Arquivos, origem e limites](../Evidencias/CT-RF125_Configuracoes_Salvar_Dias_Ausencia_Valido/README.md).
- [Valor 15 após a primeira recarga](../Evidencias/CT-RF125_Configuracoes_Salvar_Dias_Ausencia_Valido/dias_15_apos_recarga_00-16.jpg), [Valor original 1100 após a segunda recarga](../Evidencias/CT-RF125_Configuracoes_Salvar_Dias_Ausencia_Valido/dias_1100_apos_recarga_00-27.jpg).
- [Linha do tempo](../Evidencias/CT-RF125_Configuracoes_Salvar_Dias_Ausencia_Valido/linha_do_tempo.txt).

A revisão documental se baseia nos quadros do vídeo e nos eventos capturados pelo Jam. As verificações complementares ficam para uma nova rodada de testes.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf119) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
