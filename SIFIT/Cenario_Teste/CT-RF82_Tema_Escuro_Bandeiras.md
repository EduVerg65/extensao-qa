# 🧪 Cenário 82: Verificar aplicação dos temas na tela de Bandeiras

**Caso de teste:** CT-RF82  
**Módulo:** Bandeiras de Cartão  
**Status:** Reprovado nas evidências resumidas.  
**Gravação / análise original:** 16/11/2026, conforme o resumo. **Integração documental:** 16/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | O tema selecionado deve ser aplicado de forma consistente ao fundo, aos painéis e aos textos da tela. |
| Requisito | [RF82](../Analise%20de%20requisitos.md#rf82), referência de QA proposta a partir do resumo. |
| Tipo / prioridade | Interface manual / tema e legibilidade visual; Média, proposta. |
| Defeito | [BUG-036](../Relatorio-de-Bugs.md#bug-036), em triagem. |
| Fonte | [Evidências](../Evidencias/CT-RF82_Tema_Escuro_Bandeiras/README.md) e [Jam](https://jam.dev/c/ae4dc198-8a42-4451-898a-fb376596c744). |

## Pré-condições

- Sessão autenticada com acesso à tela Bandeiras de Cartão.
- Controle de tema disponível e listagem no estado vazio observado.

## Cenário BDD

```gherkin
Cenário: Verificar aplicação dos temas na tela de Bandeiras
  Dado que a tela Bandeiras de Cartão está aberta
  Quando selecionar o tema Escuro
  Então o fundo principal e os painéis devem acompanhar o tema
  E os textos da listagem vazia devem permanecer legíveis
  Quando alternar entre Claro e Escuro
  Então a aplicação do tema deve permanecer consistente
```

## Passos observados

1. Observar a tela com o tema Escuro selecionado.
2. Alternar para Claro, retornar a Escuro e selecionar Claro novamente.
3. Comparar o fundo da página com os painéis de busca e listagem.

## Resultado esperado

O tema selecionado deve ser aplicado de forma consistente ao fundo, aos painéis e aos textos da tela.

## Resultado obtido

No tema Escuro, os painéis ficam escuros, mas o fundo principal continua claro. Os textos da área vazia da listagem apresentam baixa legibilidade visual. A descrição do Jam relata: Fundo com falta de cores e modo escuro incompleto.

## Critérios de aceitação para reteste

1. O tema Escuro é aplicado ao fundo principal e aos painéis.
2. Os textos do estado vazio permanecem visualmente legíveis.
3. Alternar os temas mantém a consistência entre fundo, painéis e textos.
4. No reteste, conferir também a listagem preenchida.
5. Medições de contraste, se realizadas, devem registrar valores e o critério adotado separadamente.

Os critérios acima orientam a próxima execução; verificações complementares não recebem aprovação nesta revisão.

## Evidências e limites

- Quadro de 00:03.800 mostra o tema Escuro selecionado, painéis escuros e fundo principal claro.
- Quadros de 00:05.320 e 00:06.840 permitem comparar os temas Claro e Escuro.
- 00:04–00:07: alterações de tema chamam POST /api/usuario/tema e recebem HTTP 200.

O erro visual é observado na gravação. Não foram medidos índices de contraste nem feita auditoria formal de acessibilidade; a causa técnica não foi determinada.
Análise da gravação e dos eventos capturados no Jam; não foi executado um novo teste no sistema.

Integração documental dos arquivos RESUMO.txt fornecidos em `C:\Users\Leonardo\Desktop\evidencias`, com data de gravação e análise informada de 16/11/2026. Os Jams não foram reabertos nesta integração; eventos de rede, horários e quadros abaixo são transcritos dos resumos, sem verificação independente. Não houve nova execução do SIFIT, reteste, consulta ao banco, logs ou código.

- Resumo preservado: [RESUMO.txt](../Evidencias/CT-RF82_Tema_Escuro_Bandeiras/RESUMO.txt).
- Revisar os estilos da página e retestar Claro/Escuro com lista vazia e preenchida; medir contraste separadamente.

---

[← Início](../../README.md) · [RF82](../Analise%20de%20requisitos.md#rf82) · [Plano](../Plano%20de%20testes.md) · [Relatório](../Relatorio%20dos%20testes.md) · [Evidências](../Evidencias/CT-RF82_Tema_Escuro_Bandeiras/README.md)
