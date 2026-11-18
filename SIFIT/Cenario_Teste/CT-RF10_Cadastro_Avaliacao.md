# 🧪 Cenário 10: Cadastro de avaliação retorna HTTP 500

**Caso de teste:** CT-RF10

**Módulo:** Avaliações / Cadastrar Avaliação

**Status:** Reprovado nas evidências; reteste corretivo pendente.

**Gravação:** 15/11/2026, início às 15:07:51,265 BRT. **Revisão documental:** 15/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Cadastrar uma avaliação válida ou informar a validação específica para dados recusados, sem erro interno genérico. |
| Requisito | [RF10](../Analise%20de%20requisitos.md#rf10), proposto a partir da evidência. |
| Tipo / prioridade | Funcional manual, análise de evidências / Alta, proposta para triagem. |
| Defeito | [BUG-010](../Relatorio-de-Bugs.md#bug-010), aberto. |
| Fonte | [Jam — erro no cadastro da avaliação](https://jam.dev/c/2e5eca1f-7cd2-4ee3-854b-02ef4635955a). |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página / API | https://sifit.centrion.com.br/avaliacoes / https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.51 / Windows 11 (x86 informado pelo Jam). |
| Área de captura / duração | 1536 × 742 / 20,420 s. |
| Funcionário cadastrante | Jair, código 11. |
| Aluno | Código 3423 e nome digitado leonardp, sem confirmação pela busca. |
| Personal | Gabriella, identificador 7. |
| Data e hora da avaliação | 15/11/2026 às 06:00; horário anterior ao da tentativa. |
| Versão / zoom / classificação do ambiente | Não identificados; registrar no reteste. |

## Pré-condições

- Sessão autenticada com acesso ao módulo e à ação Cadastrar Avaliação.
- Personal disponível no formulário.
- No fluxo válido do reteste, aluno existente selecionado pela busca e data/hora permitidas segundo as regras confirmadas.
- Para reproduzir os dados históricos em ambiente de teste, verificar existência do aluno, vínculos e persistência da tentativa original.

## Cenário BDD

O BDD descreve o comportamento esperado; não representa aprovação ou nova execução.

~~~gherkin
Cenário: Cadastrar uma avaliação com dados válidos
  Dado que o usuário está autenticado e pode cadastrar avaliações
  E selecionou um aluno existente pela busca e um personal habilitado
  E informou data e hora permitidas
  Quando clicar em Salvar
  Então o sistema deve confirmar o cadastro
  E a avaliação deve estar disponível na listagem

Cenário: Tratar dados inválidos no cadastro de avaliação
  Dado que o cadastro contém um vínculo inválido ou data e hora proibidas
  Quando o usuário tentar salvar
  Então o sistema deve informar a validação específica
  E deve permitir corrigir os dados sem responder com erro interno HTTP 500
~~~

## Passos observados para reprodução

1. Abrir Avaliações e clicar em Cadastrar Avaliação.
2. Digitar leonardp no campo Nome e 3423 no campo Código, sem acionar a lupa.
3. Selecionar Gabriella no campo Personal.
4. Manter a data 15/11/2026 e preencher a hora 06:00.
5. Clicar em Salvar e observar a interface e a resposta de rede.

A data fixa pertence à evidência histórica. Uma execução com data futura é comparação separada, com resultado próprio.

## Resultado esperado

Cadastrar e confirmar a avaliação quando os dados forem válidos; para aluno inexistente, seleção incompleta ou horário proibido, informar a validação correspondente sem HTTP 500.

## Resultado obtido na gravação

- Em aproximadamente 00:12, o evento 16 registra POST /api/avaliacao/adicionar-agendamento/1 com HTTP 500 em 1363 ms.
- A resposta contém verifica_erro: true e mensagem “Erro interno inesperado.”.
- Em 00:14,748, a interface exibe “Erro” / “Erro ao cadastrar Avaliação.” e mantém o formulário ao fundo.
- O preflight OPTIONS retorna HTTP 204. O resumo do Jam informa zero mensagens de console capturadas.
- Há uma tentativa de salvamento registrada; recorrência e persistência não foram verificadas.

**Conclusão:** Reprovado pelo erro interno e pela ausência de confirmação no fluxo registrado. A validade do aluno e da data/hora não foi comprovada, mas uma rejeição de negócio deve ter tratamento controlado. Esses dados não determinam a causa raiz.

## Critérios de aceitação e matriz de reteste proposta

| Variação | Verificação esperada | Situação |
| --- | --- | --- |
| Aluno existente selecionado pela busca, personal habilitado e horário permitido | Cadastro confirmado e uma avaliação na listagem após nova consulta. | Pendente |
| Dados históricos do Jam em ambiente de teste | Cadastro ou validação específica conforme a regra, sem HTTP 500. | Pendente |
| Código inexistente / preenchimento manual sem vínculo confirmado | Tratamento controlado e orientação de correção. | Pendente |
| Data/hora passada e futura | Aplicar a regra confirmada e informar eventual impedimento. | Pendente |
| Tentativa rejeitada e envio válido | Sem registros parciais na rejeição e sem duplicidade no envio válido. | Pendente |

Identificar a versão corrigida, conferir persistência antes de reenviar e anexar nova evidência antes de encerrar BUG-010. As variações acima não entram na contagem de casos executados.

## Evidências e limites

- [Jam original](https://jam.dev/c/2e5eca1f-7cd2-4ee3-854b-02ef4635955a).

Foram conferidos detalhes, cronologia, evento de rede 16 e quadros do Jam. Não houve nova execução, inspeção do código, acesso ao banco ou correção da aplicação. O vídeo permanece no Jam. Causa raiz, elegibilidade do aluno, regra de agendamento retroativo e eventual gravação parcial permanecem não confirmadas.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf10) · [Plano](../Plano%20de%20testes.md#ct-rf10) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
