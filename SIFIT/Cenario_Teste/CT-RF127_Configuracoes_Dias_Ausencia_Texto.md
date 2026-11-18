# 🧪 Cenário 127: Validar letras no campo de dias de ausência

**Caso de teste:** CT-RF127

**Módulo:** Configurações / Home / Dias de ausência

**Status:** A validar — regra ou contexto pendente.

**Gravação:** 16/11/2026, 22:02:16 BRT. **Revisão documental:** 17/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Rejeitar letras no campo numérico de dias de ausência e tratar o valor vazio resultante conforme a regra de salvamento. |
| Requisito | [RF127](../Analise%20de%20requisitos.md#rf127) — referência de QA. |
| Tipo / prioridade | Exploratório / entrada não numérica · Média, proposta para triagem. |
| Defeito | Sem defeito confirmado |
| Encaminhamento | Confirmar a regra de vazio com o produto e repetir a digitação e a colagem de texto, conferindo também a recarga. |
| Fonte | [Jam — PED-18 — Dias de ausência com texto](https://jam.dev/c/c578ed7a-c11c-4cef-8a6c-84d0244f21a5) e [evidências locais](../Evidencias/CT-RF127_Configuracoes_Dias_Ausencia_Texto/README.md). Ver também [CT-RF116](CT-RF116_Configuracoes_Dias_Ausencia_Vazio.md). |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/configuracoes |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.79 / Windows 10 (x86), conforme os metadados do Jam. |
| Tela / arquivo de vídeo | Tela 1536 × 799 informada no Jam. Vídeo em 1918 × 998. |
| Duração | 24,48 s |
| Localização | Brasil. |
| Versão / zoom / classificação do ambiente | A confirmar antes de nova execução. |
| Dados | Valor inicial 1100. Após apagar os dígitos, foram registradas duas sequências de teclas ABC. |

## Pré-condições

- Sessão autenticada com permissão para editar Configurações e valor inicial conhecido no campo de dias de ausência.
- Identificar a versão e registrar os valores iniciais e as permissões no próximo teste.

## Cenário BDD

```gherkin
Cenário: Validar letras no campo de dias de ausência
  Dado que o campo numérico de dias de ausência contém um valor salvo
  Quando o usuário apagar o valor, digitar letras e tentar salvar
  Então o campo deve impedir a entrada de texto
  E o salvamento do campo vazio deve seguir a regra de obrigatoriedade ou de valor padrão
```

## Passos para execução ou reteste

1. Abrir Configurações > Home e registrar o valor original.
2. Apagar o conteúdo e digitar ABC. Conferir o texto exibido no campo.
3. Acionar Salvar Configurações e registrar a requisição e a resposta.
4. Recarregar para verificar a configuração e restaurar o valor inicial se necessário.

Este procedimento orienta a próxima execução. O resultado abaixo se limita ao trecho registrado no Jam.

## Resultado esperado

O campo permanece numérico. Se ficar vazio, aplica a regra de obrigatoriedade ou o padrão explícito aprovado pelo produto.

## Resultado obtido na gravação

As teclas ABC foram registradas, mas as letras não apareceram no campo. Salvar Configurações enviou `dias_ausente=0` com o campo vazio. O POST retornou HTTP 200 com `verifica_erro: false`. Depois, 1100 foi reenviado com sucesso.

| Tempo | Registro |
| --- | --- |
| 0:01–0:05 | Apaga 1100 e tenta digitar ABC duas vezes. |
| 0:07–0:16 | O campo permanece vazio. Nenhuma letra aparece. |
| 0:18 | Salva com o campo vazio. O envio registra 0. |
| 0:21–0:23 | Volta a informar 1100 e salva novamente. |

**Rede:**

- 0:18,40  POST `/api/configuracoes/alterar/1` (HTTP 200), com `dias_ausente=0` e `verifica_erro: false`.
- 0:22,90  POST (HTTP 200), com `dias_ausente=1100`. A gravação não contém GET de configuração após os envios.

**Conclusão:** A validar — regra ou contexto pendente. A rejeição da digitação de letras foi observada. A regra para o campo vazio permanece pendente no CT-RF116. A persistência de zero nesta gravação não foi verificada após recarga.

## Critérios de aceitação para nova execução

1. Letras não são aceitas como valor do campo numérico.
2. Se o campo permanecer vazio, o salvamento preserva o valor anterior ou aplica o padrão definido pelo produto.
3. A próxima consulta confirma o comportamento definido para a entrada vazia.

## Próxima ação e verificações complementares

Confirmar a regra de vazio com o produto e repetir a digitação e a colagem de texto, conferindo também a recarga.

## Evidências e limites

- [Jam original — PED-18 — Dias de ausência com texto](https://jam.dev/c/c578ed7a-c11c-4cef-8a6c-84d0244f21a5).
- [Arquivos, origem e limites](../Evidencias/CT-RF127_Configuracoes_Dias_Ausencia_Texto/README.md).
- [Campo numérico vazio depois da tentativa com letras](../Evidencias/CT-RF127_Configuracoes_Dias_Ausencia_Texto/dias_vazio_apos_texto_00-16.jpg), [Valor inicial 1100 informado novamente](../Evidencias/CT-RF127_Configuracoes_Dias_Ausencia_Texto/dias_reposto_00-22.jpg).
- [Linha do tempo](../Evidencias/CT-RF127_Configuracoes_Dias_Ausencia_Texto/linha_do_tempo.txt).

A revisão documental se baseia nos quadros do vídeo e nos eventos capturados pelo Jam. As verificações complementares ficam para uma nova rodada de testes.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf127) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
