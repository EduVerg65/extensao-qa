# 🧪 Cenário 164: Persistir a alteração da porta do aparelho de Biometria

**Caso de teste:** CT-RF164

**Módulo:** Configurações / Biometria

**Status:** Aprovado conforme a gravação.

**Gravação:** 16/11/2026, 23:05:55 BRT. **Revisão documental:** 18/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Confirmar que a alteração de Porta é gravada e reaparece ao consultar novamente a configuração de Biometria. |
| Requisito | [RF164](../Analise%20de%20requisitos.md#rf164) — referência de QA. |
| Tipo / prioridade | Funcional manual / persistência · Média, proposta para triagem. |
| Defeito | Nenhum no fluxo avaliado |
| Encaminhamento | Usar como regressão da configuração e confirmar a conectividade e a restauração em ambiente de teste. |
| Fonte | Jam 8 — Persistência da porta do aparelho (gravação restrita por conter dados de integração ou dados de alunos) e [evidências locais](../Evidencias/CT-RF164_Configuracoes_Biometria_Persistir_Porta/README.md). |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/configuracoes |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.79 / Windows 10 (x86), conforme os metadados do Jam. |
| Tela / arquivo de vídeo | Tela 1707 × 888 informada no Jam. Vídeo em 1918 × 998. |
| Duração | 20,40 s |
| Localização | Brasil. |
| Versão / zoom / classificação do ambiente | A confirmar antes de nova execução. |
| Dados | Porta inicial e porta de teste distintas. Os valores de conexão foram omitidos. |

## Pré-condições

- Sessão autenticada com permissão para alterar a porta de um aparelho de teste.
- Identificar a versão e registrar os valores iniciais e as permissões no próximo teste.

## Cenário BDD

```gherkin
Cenário: Persistir a alteração da porta do aparelho de Biometria
  Dado que a integração de Biometria tem uma porta cadastrada
  Quando o usuário altera a porta, salva e reabre a aba
  Então o campo deve exibir a nova porta consultada
  E o formulário deve permitir enviar a restauração do valor inicial
```

## Passos para execução ou reteste

1. Anotar a porta de teste inicial sem incluí-la em material público.
2. Alterar Porta para outro número válido e salvar.
3. Recarregar e reabrir Biometria para comparar o campo e a consulta.
4. Restaurar o valor inicial e consultar novamente em uma execução completa.

Este procedimento orienta a próxima execução. O resultado abaixo se limita ao trecho registrado no Jam.

## Resultado esperado

O salvamento aceita o número de porta de teste. A consulta após recarregar devolve o mesmo valor enviado.

## Resultado obtido na gravação

O POST retornou HTTP 200 com `verifica_erro: false`. Após recarregar, `porta_aparelho` no GET correspondia ao valor enviado e o campo Porta mostrava o novo valor. A gravação termina após o POST de restauração, também com sucesso.

| Tempo | Registro |
| --- | --- |
| 0:01–0:06 | Altera Porta e salva. |
| 0:09,67–0:13 | Recarrega, abre Biometria e confere Porta. |
| 0:17–0:19 | Volta ao valor inicial e envia a restauração. |

**Rede:**

- 0:06,63  POST `/api/configuracoes/alterar/1` (HTTP 200, `verifica_erro: false`), com a nova porta.
- 0:09,67  GET `/api/configuracoes/1` (HTTP 200), com `porta_aparelho` igual ao valor enviado.
- 0:18,67  POST de restauração (HTTP 200, `verifica_erro: false`). A captura termina sem GET após a restauração.

**Conclusão:** Aprovado conforme a gravação. A gravação cobre a persistência da primeira alteração. A conectividade e a nova leitura após a restauração ficaram fora do trecho.

## Critérios de aceitação para nova execução

1. A alteração retorna sucesso.
2. A leitura após recarregar equivale ao valor enviado.
3. A interface mostra o valor consultado.

## Próxima ação e verificações complementares

Usar como regressão da configuração e confirmar a conectividade e a restauração em ambiente de teste.

## Evidências e limites

- Jam 8 — Persistência da porta do aparelho (gravação restrita por conter dados de integração ou dados de alunos).
- [Arquivos, origem e limites](../Evidencias/CT-RF164_Configuracoes_Biometria_Persistir_Porta/README.md).
- [Campo Porta editado antes do salvamento, com dados de conexão ocultos](../Evidencias/CT-RF164_Configuracoes_Biometria_Persistir_Porta/salvar_porta_00-06.jpg), [Campo Porta ao reabrir Biometria, com dados de conexão ocultos](../Evidencias/CT-RF164_Configuracoes_Biometria_Persistir_Porta/porta_apos_recarregar_00-14.jpg).
- [Linha do tempo](../Evidencias/CT-RF164_Configuracoes_Biometria_Persistir_Porta/linha_do_tempo.txt).

A revisão documental se baseia nos quadros do vídeo e nos eventos capturados pelo Jam. As verificações complementares ficam para uma nova rodada de testes.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf164) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
