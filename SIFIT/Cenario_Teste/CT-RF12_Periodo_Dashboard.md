# 🧪 Cenário 12: Período invertido e atualização de indicadores pouco clara

**Caso de teste:** CT-RF12

**Módulo:** Página inicial / Período

**Status:** Reprovado nas evidências.

**Gravação:** 14/11/2026, 00:32:47 BRT. **Revisão documental:** 14/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Validar a ordem das datas do período. |
| Requisito | [RF12](../Analise%20de%20requisitos.md#rf12) |
| Tipo / prioridade | Funcional manual, análise de evidências / Média, proposta para triagem. |
| Defeito | [BUG-006](../Relatorio-de-Bugs.md#bug-006) |
| Encaminhamento | Aberto; reteste pendente após correção. |
| Fonte | [Jam — Botões de datas sem função e sem atualização](https://jam.dev/c/93165ba3-3bfe-4dd5-9379-ab8db2d686ba) |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/dashboard |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.51 / Windows 11 (x86). |
| Tela / arquivo de vídeo | 1920 × 957 informados no Jam; original 1918 × 956 pixels. |
| Duração | 18,58 s |
| Versão / zoom / classificação do ambiente | Não confirmados; registrar antes de nova execução. |
| Dados | Usar dados de teste conhecidos conforme as pré-condições abaixo; valores da gravação são referência histórica, sem copiar credenciais. |

## Pré-condições

- Sessão autenticada com acesso ao seletor de período da página inicial.
- Registrar as regras de aplicação do filtro e preparar um intervalo válido de controle.
- Antes de uma nova execução, identificar versão, permissões e dados de referência e preparar a captura de interface e rede.

## Cenário BDD

```gherkin
Cenário: Validar a ordem das datas do período
  Dado que o usuário está no seletor de período da página inicial
  Quando informar uma data inicial posterior à data final
  Então o sistema deve impedir a aplicação desse intervalo ou corrigi-lo de forma explícita
  E orientar o usuário a informar um período válido
```

## Passos para execução ou reteste

1. Alterar a data final para 10/11/2026 na base de referência da gravação.
2. Alterar a inicial para 19/11/2026, posterior à data final.
3. Verificar a validação e tentar aplicar; depois selecionar um período válido e conferir os dados de referência.

Este procedimento orienta a próxima execução. A evidência atual cobre o trecho gravado e os limites descritos abaixo; passos complementares, como conferir downloads ou recarregar a sessão, não recebem resultado de execução nesta revisão.

## Resultado esperado

Validar a ordem das datas, orientar o usuário e aplicar um período válido com retorno perceptível.

## Resultado obtido na gravação

O seletor chega a exibir 19/11/2026–10/11/2026, com início posterior ao fim, sem uma validação visível. Os indicadores permanecem com os mesmos valores nos quadros conferidos.

**Momentos e registros:** 0:04–0:08: seleção das datas. 0:10: intervalo invertido visível. No começo foram capturadas várias chamadas POST /api/dados-principais-home/1 com HTTP 200.

**Conclusão:** Reprovado nas evidências. O defeito associado descreve a manifestação observada, sem atribuir uma causa técnica não comprovada.

## Critérios de aceitação para nova execução

1. Data inicial posterior à final recebe validação clara.
2. Somente intervalos válidos são aplicados.
3. O efeito de um período válido é conferido com dados conhecidos; valores constantes não provam erro de cálculo.

## Próxima ação e verificações complementares

Corrigir e retestar a validação do intervalo; avaliar a atualização dos indicadores em base controlada como verificação complementar.

O [BUG-006](../Relatorio-de-Bugs.md#bug-006) permanece aberto. Severidade **Média** e prioridade **Média** são propostas para triagem; encerrar somente após evidências de reteste em uma versão identificada.

## Evidências e limites

- [Jam original — Botões de datas sem função e sem atualização](https://jam.dev/c/93165ba3-3bfe-4dd5-9379-ab8db2d686ba).
- [Vídeo original](../Evidencias/CT-RF12_Periodo_Dashboard/video.webm).
- [Resumo, origem e integridade](../Evidencias/CT-RF12_Periodo_Dashboard/README.md).
- [Cronologia do Jam](../Evidencias/CT-RF12_Periodo_Dashboard/linha_do_tempo.txt).

A captura comprova o intervalo invertido. Indicadores constantes, isoladamente, não demonstram falha no cálculo; os botões de seta geraram requisições, portanto não se pode dizer que todos estavam sem função.

Análise documental das gravações já consultadas em 14/11/2026 (metadados, cronologia e quadros distribuídos pelo vídeo). Esta inclusão não executa novamente o sistema, não corrige a aplicação e não constitui reteste. Versão da aplicação, zoom e classificação do ambiente não foram confirmados.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
