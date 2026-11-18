# 🧪 Cenário 139: Salvar uma Cor Principal hexadecimal válida

**Caso de teste:** CT-RF139

**Módulo:** Configurações / Design

**Status:** Aprovado conforme a gravação.

**Gravação:** 16/11/2026, 23:25:27 BRT. **Revisão documental:** 17/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Confirmar que uma Cor Principal em formato hexadecimal válido é persistida e apresentada ao reabrir Design. |
| Requisito | [RF139](../Analise%20de%20requisitos.md#rf139) — referência de QA. |
| Tipo / prioridade | Funcional manual / persistência · Média, proposta para triagem. |
| Defeito | Nenhum no fluxo avaliado |
| Encaminhamento | Usar como regressão para códigos válidos e verificar a aplicação da cor nas telas que consomem o tema. |
| Fonte | [Jam 3 — Persistência da Cor Principal](https://jam.dev/c/c4f77e18-3b66-4c68-97e7-bd70a9bb70f9) e [evidências locais](../Evidencias/CT-RF147_Configuracoes_Design_Salvar_Cor_Principal/README.md). |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/configuracoes |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.79 / Windows 10 (x86), conforme os metadados do Jam. |
| Tela / arquivo de vídeo | Tela 1707 × 888 informada no Jam. Vídeo em 1918 × 998. |
| Duração | 25,55 s |
| Localização | Brasil. |
| Versão / zoom / classificação do ambiente | A confirmar antes de nova execução. |
| Dados | Cor Principal inicial #FFCE00. Novo valor de teste #663399 e Cor Secundária #000. |

## Pré-condições

- Sessão autenticada com acesso à aba Design. Registrar a Cor Principal inicial.
- Identificar a versão e registrar os valores iniciais e as permissões no próximo teste.

## Cenário BDD

```gherkin
Cenário: Salvar uma Cor Principal hexadecimal válida
  Dado que a aba Design exibe uma Cor Principal já configurada
  Quando o usuário troca a Cor Principal para #663399 e salva
  Então a nova cor deve ser armazenada
  E o valor e a amostra de cor devem corresponder ao reabrir Design
```

## Passos para execução ou reteste

1. Abrir Design e registrar os códigos existentes.
2. Substituir a Cor Principal por #663399 e salvar.
3. Recarregar e voltar a Design.
4. Comparar o valor no campo, a amostra e a nova consulta.

Este procedimento orienta a próxima execução. O resultado abaixo se limita ao trecho registrado no Jam.

## Resultado esperado

O salvamento aceita o código válido e a nova leitura e a aba Design mostram #663399.

## Resultado obtido na gravação

O POST retornou sucesso com a Cor Principal #663399. Após recarregar, o GET confirmou o código salvo e a aba Design apresentou o mesmo valor com a amostra roxa.

| Tempo | Registro |
| --- | --- |
| 0:00–0:16 | Edita Cor Principal de #FFCE00 para #663399. |
| 0:16,99 | Aciona Salvar Configurações. |
| 0:20–0:25 | Recarrega e volta a Design. O novo código e a amostra roxa aparecem. |

**Rede:**

- 0:17,00  POST `/api/configuracoes/alterar/1` com `cor_principal: #663399` (HTTP 200, `verifica_erro: false`).
- 0:20,69  GET `/api/configuracoes/1` (HTTP 200), com `cor_principal: #663399` e `cor_secundaria: #000`.

**Conclusão:** Aprovado conforme a gravação. O resultado cobre a Cor Principal e a amostra da aba Design. A aplicação da cor nos ambientes online não foi verificada.

## Critérios de aceitação para nova execução

1. O código válido é aceito pelo salvamento.
2. A consulta devolve o código salvo.
3. O campo e a amostra representam a nova cor ao reabrir.

## Próxima ação e verificações complementares

Usar como regressão para códigos válidos e verificar a aplicação da cor nas telas que consomem o tema.

## Evidências e limites

- [Jam 3 — Persistência da Cor Principal](https://jam.dev/c/c4f77e18-3b66-4c68-97e7-bd70a9bb70f9).
- [Arquivos, origem e limites](../Evidencias/CT-RF147_Configuracoes_Design_Salvar_Cor_Principal/README.md).
- [Cor Principal original antes da edição](../Evidencias/CT-RF147_Configuracoes_Design_Salvar_Cor_Principal/cor_principal_inicial_00-01.jpg), [Cor Principal atualizada após reabrir a aba Design](../Evidencias/CT-RF147_Configuracoes_Design_Salvar_Cor_Principal/cor_principal_apos_reabrir_00-24.jpg).
- [Linha do tempo](../Evidencias/CT-RF147_Configuracoes_Design_Salvar_Cor_Principal/linha_do_tempo.txt).

A revisão documental se baseia nos quadros do vídeo e nos eventos capturados pelo Jam. As verificações complementares ficam para uma nova rodada de testes.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf139) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
