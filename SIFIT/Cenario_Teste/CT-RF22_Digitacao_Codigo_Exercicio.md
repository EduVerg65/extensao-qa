# 🧪 Cenário 22: Campo Código do exercício não permite digitação

**Caso de teste:** CT-RF22

**Módulo:** Exercícios / Formulário Exercício

**Status:** Reprovado conforme o relato; reprodução independente pendente.

**Gravação:** 15/11/2026, 15:25 BRT, conforme a aba Info do Jam. **Revisão documental:** 15/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Verificar se o campo Código do formulário Exercício permite informar e editar um código válido. |
| Requisito | Comportamento esperado proposto para RF22: permitir preencher o código do exercício conforme as regras do produto; confirmar a regra de edição com o responsável funcional. RF22 ainda não está formalizado na análise de requisitos. |
| Tipo / prioridade | Funcional manual, análise documental / Média, proposta para triagem. |
| Defeito | Impedimento de digitação no campo Código, relatado pelo testador; sem identificador de bug atribuído nesta inclusão. |
| Encaminhamento | Confirmar a regra do campo, reproduzir o impedimento e retestar após correção. |
| Fonte | [Jam — Teste - Erro ao tentar colocar o código](https://jam.dev/c/2696db03-0a18-4c39-a75d-4987a43c04f0) e relato do testador. |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/exercicios |
| Interface identificada | Formulário intitulado Exercício, com campos Código e Nome, seções Imagem e Vídeo e ações Cancelar e Salvar. |
| Navegador / sistema | Edge 157.0.8103.80 / Windows 11 (x86), conforme Info do Jam. |
| Tela | 1912 × 960 informados no Jam. |
| Duração | Aproximadamente 5 s, conforme o player do Jam. |
| Versão / zoom / classificação do ambiente | Não confirmados; registrar antes de nova execução. |
| Dados | Código de teste válido e disponível conforme a regra do produto; valor efetivamente digitado na gravação não confirmado. |

## Pré-condições

- Sessão autenticada com acesso à página Exercícios e permissão para preencher o formulário.
- Formulário Exercício aberto, com o campo Código visível.
- Confirmar se o código é informado manualmente ou gerado pelo sistema e em quais operações pode ser editado.
- Preparar um código de teste compatível com a regra confirmada e registrar versão, permissões e ambiente antes do reteste.

## Cenário BDD

```gherkin
Cenário: Informar o código do exercício em um campo editável
  Dado que o usuário possui permissão para preencher o formulário Exercício
  E que a regra do produto permite informar o código manualmente
  Quando selecionar o campo "Código"
  E digitar um código válido
  Então o campo deve exibir e manter os caracteres informados
  E permitir corrigir o valor antes de salvar
```

## Passos para execução ou reteste

1. Acessar a página Exercícios com uma sessão autorizada.
2. Abrir o formulário Exercício na mesma operação do registro original; confirmar se era criação ou edição, pois esse contexto não foi verificado nesta revisão.
3. Clicar no campo Código e verificar se recebe foco.
4. Digitar o código de teste válido e observar se os caracteres aparecem e permanecem no campo.
5. Apagar um caractere e digitá-lo novamente para verificar a edição.
6. Sair do campo com Tab e verificar se o valor é mantido.
7. Registrar o resultado e capturar a interface, o console e a rede para apoiar a investigação.

Este procedimento orienta a próxima execução. Os passos de edição, navegação por Tab e captura técnica são verificações propostas, sem resultado de execução atribuído nesta revisão.

## Resultado esperado

Quando a regra permitir preenchimento manual, o campo Código deve aceitar um valor válido, exibir os caracteres digitados e permitir sua edição. Restrições de formato devem produzir orientação clara ao usuário.

Se o código for gerado automaticamente ou não puder ser editado nessa operação, o formulário deve comunicar essa condição de forma clara; confirmar essa regra antes de concluir o diagnóstico funcional.

## Resultado obtido no relato e na consulta ao Jam

O testador informa que não consegue digitar o código. O Jam tem o título "Teste - Erro ao tentar colocar o código"; a imagem inicial consultada mostra o formulário Exercício e o campo Código na página de exercícios.

**Momentos e registros:** imagem inicial do player e aba Info consultadas. Não foi possível confirmar a reprodução integral do vídeo, a sequência de teclas, o valor tentado ou o comportamento do foco. Console, requisições e respostas não foram analisados.

**Conclusão:** Reprovado conforme o relato quanto ao preenchimento manual esperado. A reprodução independente e a confirmação da regra do campo permanecem pendentes; a causa técnica não está determinada.

## Critérios de aceitação para nova execução

1. A regra de preenchimento manual ou geração automática do código está confirmada.
2. Quando editável, o campo recebe foco e aceita o código válido sem perder os caracteres.
3. O usuário consegue apagar e corrigir o valor antes de salvar.
4. Sair do campo mantém o valor válido informado.
5. Restrições de formato ou de edição são explicadas na interface.

## Próxima ação e verificações complementares

Reproduzir o impedimento na mesma operação e com as mesmas permissões. Investigar estado desabilitado ou somente leitura, validações e atualização do valor pelo formulário como hipóteses, sem atribuir causa antes da inspeção técnica.

Após a correção, executar os passos acima e, em ambiente autorizado para dados de teste, complementar com salvamento e reabertura para conferir a persistência do código. O salvamento não foi validado nesta revisão.

## Evidências e limites

- [Jam original — Teste - Erro ao tentar colocar o código](https://jam.dev/c/2696db03-0a18-4c39-a75d-4987a43c04f0).
- Relato do solicitante: "O erro é não conseguir digitar o código."
- Consulta à aba Info e à imagem inicial do player em 15/11/2026.

Não foram criadas cópias locais do vídeo ou arquivos de integridade. Esta análise não constitui nova execução ou reteste da aplicação. Não confirma causa técnica, erro de API, falha de salvamento ou impossibilidade de cadastrar o exercício por outros meios.

A numeração CT-RF22 segue a solicitação; CT-RF21 não foi criado ou renumerado nesta inclusão.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
