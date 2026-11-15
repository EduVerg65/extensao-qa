# 🧪 Cenário 32: Edição do tipo de membro de um grupo muscular

**Caso de teste:** CT-RF32

**Módulo:** Treinamento / Grupos Musculares

**Status:** Aprovado conforme a gravação.

**Gravação:** 15/11/2026, 15h56 BRT. **Revisão documental:** 15/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Alterar o tipo de membro de um grupo muscular existente e refletir a mudança na listagem e nos cartões de resumo. |
| Requisito | [RF32](../Analise%20de%20requisitos.md#rf32) |
| Tipo / prioridade | Funcional manual, análise de evidências / Média, proposta para triagem. |
| Defeito | Nenhum no fluxo avaliado |
| Encaminhamento | Sem reteste corretivo pendente; manter como regressão. |
| Fonte | [Jam — Tela de Grupos Musculares](https://jam.dev/c/98008390-0040-475e-ba7b-7f1e72cc0b2e) |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/grupos-musculares |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.78 / Windows (x86) 11. |
| Tela / arquivo de vídeo | 1920 × 911 informados no Jam. |
| Duração | 2 min 3 s |
| Rede | Classificada como rápida no Jam: mais de 10 Mbps, latência de 50 ms. |
| Localização | Brasil. |
| Versão / zoom / classificação do ambiente | Não confirmados; registrar antes de nova execução. |
| Dados | Usar um grupo muscular de teste com tipo de membro conhecido; valores da gravação são referência histórica. |

## Pré-condições

- Sessão autenticada com permissão para editar grupos musculares.
- Existir um grupo muscular de teste com o tipo de membro registrado antes da alteração.
- Estado inicial dos cartões de resumo registrado antes da edição.
- Antes de uma nova execução, identificar versão, permissões e dados de referência e preparar a captura de interface e rede.

## Cenário BDD

```gherkin
Cenário: Alterar o tipo de membro de um grupo muscular
  Dado que existe um grupo muscular cadastrado com um tipo de membro
  Quando abrir a edição desse registro
  E selecionar um tipo de membro diferente
  E confirmar em "Salvar"
  Então a listagem deve apresentar o novo tipo de membro para o registro
  E os cartões de resumo devem refletir a alteração
```

## Passos para execução ou reteste

1. Acessar a tela Grupos Musculares e registrar a listagem e os cartões de resumo.
2. Acionar a ação de edição na linha do registro escolhido.
3. Conferir que o formulário abre preenchido com os dados atuais do registro.
4. Selecionar um tipo de membro diferente do atual.
5. Confirmar em "Salvar".
6. Conferir o tipo de membro na listagem e os cartões de resumo.
7. Recarregar a página e consultar novamente o registro para verificar a persistência.

Este procedimento orienta a próxima execução. A evidência atual cobre o trecho gravado e os limites descritos abaixo; passos complementares, como a recarga da página e a conferência no banco de dados, não recebem resultado de execução nesta revisão.

## Resultado esperado

A listagem apresenta o registro com o novo tipo de membro, e os cartões de resumo são recalculados, mantendo a soma coerente com o total de registros.

## Resultado obtido na gravação

A alteração foi aplicada e os cartões acompanharam a mudança.

**Caso documentado — registro de código 1:**

| Tempo | Registro |
| --- | --- |
| 1:02 | Formulário "Grupo Muscular" aberto em edição, preenchido com Código 1, Nome "Bicpes" e Tipo Membro "Superiores". O campo Imagem apresenta o arquivo `Gemini_Generated_Image_xks74hxks74hxks7.jpg` com miniatura de pré-visualização exibida corretamente. |
| 1:05 | O campo Tipo Membro passa a apresentar "Inferiores". |
| 1:06 | Acionamento do botão de envio do formulário. |
| 1:07 | Recarga da listagem, com novas requisições das imagens. |
| 1:08 | Listagem com o registro de código 1 em "Inferiores". |

**Cartões de resumo antes e depois:**

| Indicador | Antes (0:55) | Depois (1:08) |
| --- | --- | --- |
| Grupos cadastrados | 4 | 4 |
| Superiores | 3 | 2 |
| Inferiores | 1 | 2 |
| Aeróbio | 0 | 0 |

**Alterações seguintes observadas:** entre 1:11 e 1:38 ocorrem novas seleções de tipo de membro e envios do formulário. Em 1:45, o registro de código 6 ("Tríceps") aparece como "Aerobio" ao ser filtrado. Em 2:00, os cartões apresentam Grupos cadastrados 4, Superiores 0, Inferiores 3 e Aeróbio 1, somando os quatro registros existentes.

**Conclusão:** Aprovado conforme a gravação. A alteração do tipo de membro é aplicada, a listagem é atualizada e os cartões de resumo permanecem coerentes com os registros. A aprovação se limita ao cenário visível; não significa validação de todas as variações do fluxo.

## Critérios de aceitação para nova execução

1. O formulário de edição abre preenchido com os dados atuais do registro.
2. A alteração do tipo de membro é persistida e exibida na listagem.
3. Os cartões de resumo são recalculados e a soma dos tipos corresponde ao total de registros.
4. O resultado se mantém após recarga da página.

## Próxima ação e verificações complementares

Usar como regressão. Permanecem fora do cenário gravado: cancelamento da edição, alteração de nome, alteração simultânea de vários campos, validação de campos obrigatórios e verificação de persistência após nova sessão.

## Observação sobre a coerência dos cartões

Entre os quadros de 0:55 e 2:00 os cartões apresentam combinações diferentes — Superiores 3 / Inferiores 1 / Aeróbio 0 no primeiro, Superiores 0 / Inferiores 3 / Aeróbio 1 no último — com o total constante em 4. A variação corresponde às edições realizadas no intervalo e, em cada quadro conferido, a soma dos três tipos é igual ao total de registros. Não há divergência a reportar; o registro deste comportamento evita que a comparação direta entre quadros distantes seja lida como inconsistência.

## Observação sobre a imagem enviada na edição

O formulário de edição recebeu um arquivo de imagem, com miniatura exibida corretamente na pré-visualização. Após o envio, a coluna IMAGEM do registro continua apresentando o ícone de imagem quebrada, e o arquivo requisitado para esse registro mantém o mesmo nome observado antes da edição.

Esse comportamento é compatível tanto com a sobrescrita do arquivo sob o mesmo nome quanto com a não persistência da imagem enviada, e não distingue entre as duas hipóteses. Como todas as requisições de imagem da tela retornam HTTP 422, documentadas em [CT-RF30](CT-RF30_Imagens_GruposMusculares.md), a exibição não pode ser usada para confirmar o envio. A verificação depende de consulta ao servidor de arquivos e ao registro no banco de dados.

## Evidências e limites

- [Jam original — Tela de Grupos Musculares](https://jam.dev/c/98008390-0040-475e-ba7b-7f1e72cc0b2e).
- Painel Console do Jam, visão de atividade do usuário: cronologia de cliques e envios entre 0:57 e 1:38.
- Quadros consultados: 0:55, 1:02, 1:08, 1:45 e 2:00.
- Pasta local de evidências: a criar em `Evidencias/CT-RF32_Edicao_TipoMembro/`; até lá, a fonte é o Jam indicado acima.

A cronologia não registra uma requisição de atualização com o respectivo código de status para este fluxo; a conclusão apoia-se na comparação entre os quadros de 1:02 e 1:08 e nos cartões de resumo. O controle que abre o formulário de edição não foi identificado com certeza na cronologia, por isso o passo correspondente está descrito de forma genérica. A persistência após recarga não foi verificada, nem houve consulta ao banco de dados. As alterações posteriores a 1:08 não têm quadro de antes e depois individual; sustentam-se no quadro de 1:45 e nos cartões de 2:00.

Análise documental da gravação consultada em 15/11/2026, com leitura direta dos painéis do Jam. Esta inclusão não executa novamente o sistema, não corrige a aplicação e não constitui reteste. Versão da aplicação, zoom e classificação do ambiente não foram confirmados.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
