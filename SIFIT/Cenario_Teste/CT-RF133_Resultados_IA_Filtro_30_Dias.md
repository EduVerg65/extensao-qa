# 🧪 Cenário 133: Filtrar Resultados da Inteligência pelos últimos 30 dias

**Caso de teste:** CT-RF133

**Módulo:** Inteligência / Resultados IA / Filtros de período

**Status:** Aprovado conforme a gravação.

**Gravação:** 16/11/2026, 21:49:48 BRT. **Revisão documental:** 17/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Atualizar os indicadores e a linha do tempo ao selecionar 30 dias e confirmar o resultado ao voltar ao mesmo filtro. |
| Requisito | [RF133](../Analise%20de%20requisitos.md#rf133) — referência de QA. |
| Tipo / prioridade | Funcional manual / filtragem · Média, proposta para triagem. |
| Defeito | Nenhum no fluxo avaliado |
| Encaminhamento | Usar como regressão e retestar com registros preparados no limite de 30 dias. |
| Fonte | [Jam — PED-11 — Últimos 30 dias](https://jam.dev/c/2756d5c1-a823-482b-bf8d-878357b8b087) e [evidências locais](../Evidencias/CT-RF133_Resultados_IA_Filtro_30_Dias/README.md). A comparação com 90 dias está no [CT-RF122](CT-RF122_Resultados_IA_Filtro_90_Dias.md). |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/inteligencia/resultados |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.79 / Windows 10 (x86), conforme os metadados do Jam. |
| Tela / arquivo de vídeo | Tela 1536 × 799 informada no Jam. Vídeo em 1918 × 998. |
| Duração | 20,07 s |
| Localização | Brasil. |
| Versão / zoom / classificação do ambiente | A confirmar antes de nova execução. |
| Dados | Últimos 7 dias mostrou três automações, três relatórios e dois aniversariantes. Últimos 30 dias mostrou doze, doze e seis. |

## Pré-condições

- Sessão autenticada com acesso a Resultados IA e automações registradas em períodos que diferenciem 7 e 30 dias.
- Identificar a versão e registrar os valores iniciais e as permissões no próximo teste.

## Cenário BDD

```gherkin
Cenário: Filtrar Resultados da Inteligência pelos últimos 30 dias
  Dado que Resultados IA tem resultados distintos em Últimos 7 dias e Últimos 30 dias
  Quando o usuário selecionar Últimos 30 dias
  Então o filtro deve ficar destacado e carregar os dados do período
  E ao voltar a 30 dias, a mesma base deve produzir os mesmos totais
```

## Passos para execução ou reteste

1. Abrir Resultados IA e registrar os resultados dos últimos 7 dias.
2. Selecionar Últimos 30 dias e conferir a mudança nos cartões e na linha do tempo.
3. Voltar a Últimos 7 dias e registrar os resultados.
4. Selecionar 30 dias novamente e conferir a consistência entre interface e API.

Este procedimento orienta a próxima execução. O resultado abaixo se limita ao trecho registrado no Jam.

## Resultado esperado

O período de 30 dias é destacado, cartões e linha do tempo mudam de acordo com a resposta, e reaplicar o filtro repete os resultados em uma base estável.

## Resultado obtido na gravação

Ao selecionar 30 dias, automações e relatórios passaram de 3 para 12 e aniversariantes de 2 para 6. O GET retornou `dias: 30` e 12 itens na linha do tempo, frente a 3 em 7 dias. O retorno a 7 dias e a seleção seguinte de 30 repetiram os estados observados.

| Tempo | Registro |
| --- | --- |
| 0:03–0:08 | Carrega os últimos 7 dias, consulta Hoje e retorna a 7 dias. |
| 0:08–0:15 | Seleciona 30 dias e confere 12 automações, 12 relatórios e 6 aniversariantes. |
| 0:16–0:19 | Volta a 7 e seleciona 30 novamente. Os indicadores acompanham as duas trocas. |

**Rede:**

- 0:07,44  GET `/api/inteligencia/resultados/1?periodo=7` (HTTP 200), com três itens na linha do tempo.
- 0:08,81  GET com `periodo=30` (HTTP 200), com `dias: 30` e doze itens na linha do tempo.
- 0:16,71  GET com `periodo=7` (HTTP 200).
- 0:17,70  Segundo GET com `periodo=30` (HTTP 200), com os mesmos totais da primeira consulta.

**Conclusão:** Aprovado conforme a gravação. O teste confirma troca de filtro e consistência com a API. Os limites de data e a regra dos cartões que ficaram constantes exigem dados de controle.

## Critérios de aceitação para nova execução

1. Últimos 30 dias permanece destacado após o carregamento.
2. Cartões e linha do tempo correspondem à resposta de 30 dias.
3. Alternar para 7 e retornar a 30 atualiza e restaura os resultados esperados.

## Próxima ação e verificações complementares

Usar como regressão e retestar com registros preparados no limite de 30 dias.

## Evidências e limites

- [Jam original — PED-11 — Últimos 30 dias](https://jam.dev/c/2756d5c1-a823-482b-bf8d-878357b8b087).
- [Arquivos, origem e limites](../Evidencias/CT-RF133_Resultados_IA_Filtro_30_Dias/README.md).
- [Últimos 7 dias com três automações e dois aniversariantes](../Evidencias/CT-RF133_Resultados_IA_Filtro_30_Dias/resultados_7_dias_00-08.jpg), [Últimos 30 dias com doze automações e seis aniversariantes](../Evidencias/CT-RF133_Resultados_IA_Filtro_30_Dias/resultados_30_dias_00-18.jpg).
- [Linha do tempo](../Evidencias/CT-RF133_Resultados_IA_Filtro_30_Dias/linha_do_tempo.txt).

A revisão documental se baseia nos quadros do vídeo e nos eventos capturados pelo Jam. As verificações complementares ficam para uma nova rodada de testes.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf133) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
