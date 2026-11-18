# 🧪 Cenário 23: Edição de exercício aumenta o total e mantém duas entradas

**Caso de teste:** CT-RF23

**Módulo:** Exercícios / Edição

**Status:** Reprovado no trecho consultado; confirmar operação e identidade dos registros na reprodução.

**Gravação:** 15/11/2026, 15:38 BRT, conforme Info do Jam. **Revisão documental:** 15/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Editar o nome de um exercício existente preservando sua identidade e a quantidade de registros. |
| Requisito | [RF23](../Analise%20de%20requisitos.md#rf23) — referência de QA; confirmação de produto pendente. |
| Tipo / prioridade | Funcional manual, análise de evidências / Média, proposta para triagem. |
| Defeito | [BUG-012](../Relatorio-de-Bugs.md#bug-012) — em triagem; confirmação pendente. |
| Encaminhamento | Reproduzir a partir da ação explícita de edição e comparar os identificadores antes e depois. Investigar eventual envio para criação como hipótese, sem atribuir causa técnica antes de verificar código e contrato da API. |
| Fonte | [Jam — Edição de exercício aumenta o total e mantém duas entradas](https://jam.dev/c/073f70d6-4052-4e0f-a4bb-e9f37305d618) |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/exercicios |
| Backend observado na rede | https://backendsifit.centrion.com.br |
| Navegador / sistema | Edge 157.0.8103.80 / Windows 11 (x86), conforme Info. |
| Tela / duração | 1912 × 960 informados no Jam / aproximadamente 9 s. |
| Versão / zoom / classificação do ambiente | Não confirmados; registrar antes de nova execução. |
| Dados | Utilizar registros e arquivos de teste autorizados; os valores da gravação são referência histórica. |

## Pré-condições

- Sessão autenticada com acesso a Exercícios e permissão para a operação.
- Exercício de teste existente, com identificador e nome original registrados antes da edição.
- Antes de nova execução, identificar versão, ambiente, permissões e dados de referência.

## Cenário BDD

```gherkin
Cenário: Editar o nome de um exercício existente preservando sua identidade e a quantidade de registros
  Dado que o usuário possui permissão para a operação em Exercícios
  E que os dados de teste estão preparados
  Quando abrir a edição e alterar o nome do exercício
  E clicar em "Salvar"
  Então o mesmo registro deve apresentar o nome atualizado
  E a quantidade de exercícios deve permanecer igual
```

## Passos para execução ou reteste

1. Registrar identificador, nome e total do exercício de teste.
2. Abrir explicitamente a ação de edição desse registro.
3. Alterar o nome para um nome de teste distinguível, como Levantamento de Peso 02.
4. Clicar em Salvar.
5. Conferir o nome atualizado, a identidade do registro e a manutenção do total.
6. Verificar se a lista criou uma segunda entrada em vez de atualizar a original.

Este procedimento orienta a próxima execução. Verificações complementares não visíveis nos quadros consultados não recebem resultado de execução nesta revisão.

## Resultado esperado

Salvar a edição deve atualizar o mesmo exercício, sem criar um registro adicional e sem aumentar o total da biblioteca.

## Resultado obtido na gravação

O Jam está identificado como teste de edição. Nos quadros intermediários, o formulário Exercício está aberto com código 16, o nome é preenchido e a biblioteca ao fundo indica total 10. No quadro final, o formulário fecha, o total é 11 e a lista contém Levantamento de Peso e Levantamento de Peso 02. O aumento e a coexistência dos nomes divergem do resultado esperado para uma edição.

**Momentos e registros:** quadros do player, metadados Info e listagem Network consultados. A aba Network apresenta POST com HTTP 200, GET de arquivo MP4 com HTTP 200, POST com HTTP 201 e outro POST com HTTP 200. O HTTP 201 é compatível com criação, mas isoladamente não confirma a causa: caminhos, corpos e contrato da API não foram inspecionados.

**Conclusão:** Reprovado no trecho consultado; confirmar operação e identidade dos registros na reprodução.

## Critérios de aceitação para nova execução

1. A ação de edição abre o exercício correto com seus dados atuais.
2. Salvar altera o nome do mesmo identificador.
3. O total permanece igual e não surge um registro adicional.
4. Os dados não alterados permanecem associados ao exercício.

## Próxima ação e verificações complementares

Reproduzir a partir da ação explícita de edição e comparar os identificadores antes e depois. Investigar eventual envio para criação como hipótese, sem atribuir causa técnica antes de verificar código e contrato da API.

## Evidências e limites

- [Jam original](https://jam.dev/c/073f70d6-4052-4e0f-a4bb-e9f37305d618).
- [Resumo e origem da evidência](../Evidencias/CT-RF24_Edicao_Exercicio/README.md).
- [Cronologia documental](../Evidencias/CT-RF24_Edicao_Exercicio/linha_do_tempo.txt).

O acionamento inicial da edição e os identificadores das duas entradas não foram confirmados. A classificação considera o propósito declarado do Jam e a divergência visual; se a operação tiver sido criação, reavaliar a conclusão.

A análise utiliza quadros consultados e a listagem de rede; não corresponde a uma revisão quadro a quadro de todo o vídeo. Não houve nova execução no SIFIT, reteste ou inspeção do código. Vídeo original e capturas não foram copiados para o repositório; não há hash do vídeo nesta inclusão. Não foram reproduzidos credenciais, tokens ou corpos de autenticação.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)

