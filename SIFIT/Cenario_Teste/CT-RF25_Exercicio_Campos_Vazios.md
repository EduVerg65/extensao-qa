# 🧪 Cenário 25: Envio de exercício com campos vazios

**Caso de teste:** CT-RF25

**Módulo:** Exercícios / Validação do cadastro

**Status:** Reprovado conforme a gravação — o formulário permanece aberto sem mensagem de validação visível.

**Gravação:** 15/11/2026, 16:11 BRT, conforme Info do Jam. **Revisão documental:** 15/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Verificar se o sistema impede o cadastro de exercício com campos obrigatórios vazios e informa claramente quais dados devem ser preenchidos. |
| Requisito | [RF25](../Analise%20de%20requisitos.md#rf25) — referência de QA; confirmação de produto pendente. |
| Tipo / prioridade | Funcional manual, teste negativo / Alta. |
| Defeito | [BUG-013](../Relatorio-de-Bugs.md#bug-013), em triagem. |
| Encaminhamento | Exibir mensagens junto aos campos obrigatórios, manter os dados digitados e não criar o exercício. |
| Fonte | [Jam — Envio de exercício com campos vazios](https://jam.dev/c/bc07ca5f-d3a9-45f6-84cb-12c0b562a211) |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/exercicios |
| Navegador / sistema | Edge 157.0.8103.80 / Windows 11 (x86), conforme Info. |
| Tela / duração | 1912 × 960 informados no Jam / aproximadamente 4 s. |
| Rede | Fast · 10+ Mbps, latência de 50 ms, conforme Info. |
| Versão / zoom / classificação do ambiente | Não confirmados; registrar antes do reteste. |
| Dados | Código e nome não preenchidos; imagem e vídeo não selecionados. |

## Pré-condições

- Sessão autenticada com acesso a Exercícios e permissão para cadastrar.
- Formulário de novo exercício aberto.
- Nenhum valor preenchido nos campos obrigatórios.

## Cenário BDD

```gherkin
Cenário: Tentar salvar um exercício com campos obrigatórios vazios
  Dado que o usuário abriu o formulário de novo exercício
  E deixou os campos obrigatórios vazios
  Quando clicar em "Salvar"
  Então o sistema não deve criar o exercício
  E deve indicar de forma clara cada campo obrigatório não preenchido
```

## Passos para execução ou reteste

1. Acessar Exercícios e registrar o total inicial da biblioteca.
2. Abrir o formulário de novo exercício.
3. Manter código, nome e demais dados obrigatórios vazios.
4. Clicar em Salvar.
5. Verificar mensagens nos campos, notificação geral e foco no primeiro campo inválido.
6. Fechar ou recarregar a tela e confirmar que nenhum exercício vazio foi criado.

## Resultado esperado

O sistema deve bloquear o envio, destacar os campos obrigatórios vazios e apresentar mensagens de validação compreensíveis, sem criar ou alterar registros.

## Resultado obtido na gravação

A gravação mostra o formulário Exercício com os campos de código e nome sem preenchimento. Após a tentativa de salvar, o modal permanece aberto e não é observada mensagem de validação, destaque de campo inválido ou orientação ao usuário. A evidência não demonstra a criação de um registro vazio.

**Conclusão:** Reprovado por ausência de feedback visível ao tentar salvar o formulário inválido. A inexistência de persistência indevida deve ser confirmada no reteste.

## Critérios de aceitação para nova execução

1. O envio com campos obrigatórios vazios é bloqueado.
2. Cada campo obrigatório inválido recebe indicação visual e textual.
3. O foco é direcionado ao primeiro campo que exige correção.
4. Nenhum registro vazio é criado, inclusive após recarregar a página.

## Evidências e limites

- [Jam original](https://jam.dev/c/bc07ca5f-d3a9-45f6-84cb-12c0b562a211).
- A gravação tem aproximadamente 4 segundos e não apresenta confirmação de persistência, resposta de API detalhada ou consulta posterior à biblioteca.
- Não houve nova execução no SIFIT, inspeção de código ou reprodução independente.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)

