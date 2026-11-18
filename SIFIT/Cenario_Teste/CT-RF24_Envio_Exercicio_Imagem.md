# 🧪 Cenário 24: Envio de exercício com imagem

**Caso de teste:** CT-RF24

**Módulo:** Exercícios / Cadastro com imagem

**Status:** A validar — criação visível; persistência e associação da imagem não confirmadas.

**Gravação:** 15/11/2026, 15:35 BRT, conforme Info do Jam. **Revisão documental:** 15/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Cadastrar um exercício com imagem válida e verificar a associação do arquivo ao registro. |
| Requisito | [RF24](../Analise%20de%20requisitos.md#rf24) — referência de QA; confirmação de produto pendente. |
| Tipo / prioridade | Funcional manual, análise de evidências / Média, proposta para triagem. |
| Defeito | Sem defeito confirmado; validação da imagem salva pendente. |
| Encaminhamento | Reabrir o exercício criado e conferir a imagem salva. Testar formatos e tamanhos inválidos em casos separados; essas variações não recebem resultado nesta análise. |
| Fonte | [Jam — Envio de exercício com imagem](https://jam.dev/c/25c37a9b-e9bd-4e0c-adf1-4da528ae1d58) |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/exercicios |
| Backend observado na rede | https://backendsifit.centrion.com.br |
| Navegador / sistema | Edge 157.0.8103.80 / Windows 11 (x86), conforme Info. |
| Tela / duração | 1912 × 960 informados no Jam / aproximadamente 5 s. |
| Versão / zoom / classificação do ambiente | Não confirmados; registrar antes de nova execução. |
| Dados | Utilizar registros e arquivos de teste autorizados; os valores da gravação são referência histórica. |

## Pré-condições

- Sessão autenticada com acesso a Exercícios e permissão para a operação.
- Imagem de teste disponível, em formato e tamanho aceitos pela interface, sem dados pessoais.
- Antes de nova execução, identificar versão, ambiente, permissões e dados de referência.

## Cenário BDD

```gherkin
Cenário: Cadastrar um exercício com imagem válida e verificar a associação do arquivo ao registro
  Dado que o usuário possui permissão para a operação em Exercícios
  E que os dados de teste estão preparados
  Quando preencher o formulário de um novo exercício
  E selecionar uma imagem válida
  E clicar em "Salvar"
  Então o exercício deve aparecer na biblioteca
  E a imagem deve permanecer associada ao exercício ao reabrir o cadastro
```

## Passos para execução ou reteste

1. Registrar o total inicial da biblioteca e abrir o formulário de novo exercício.
2. Preencher os campos necessários com dados válidos de teste.
3. Selecionar uma imagem aceita e verificar a prévia.
4. Clicar em Salvar e conferir o exercício na biblioteca e o total atualizado.
5. Reabrir o exercício e verificar se a imagem corresponde ao arquivo enviado.
6. Recarregar a página e conferir a persistência da associação.

Este procedimento orienta a próxima execução. Verificações complementares não visíveis nos quadros consultados não recebem resultado de execução nesta revisão.

## Resultado esperado

O sistema deve cadastrar o exercício, atualizar a biblioteca e manter a imagem vinculada ao registro, disponível após reabrir o cadastro.

## Resultado obtido na gravação

O quadro inicial consultado mostra o formulário Exercício preenchido com nome braço forte e uma miniatura na seção Imagem; a biblioteca ao fundo indica total 9. O quadro final mostra o formulário fechado, braço forte na lista e total 10. Esses quadros sustentam a criação com imagem selecionada, mas não demonstram a reabertura ou a visualização da imagem salva.

**Momentos e registros:** quadros do player, metadados Info e listagem Network consultados. A aba Network apresenta duas entradas POST com HTTP 201, uma OPTIONS com HTTP 204 e uma POST com HTTP 200 no domínio backendsifit.centrion.com.br. Sem inspecionar caminhos e corpos, não é possível atribuir cada requisição ao cadastro, ao upload ou à atualização da lista.

**Conclusão:** A validar — criação visível; persistência e associação da imagem não confirmadas.

## Critérios de aceitação para nova execução

1. Uma imagem válida pode ser selecionada e sua prévia aparece.
2. Salvar cria um único exercício e atualiza o total.
3. Reabrir o cadastro exibe a imagem correspondente ao arquivo enviado.
4. A associação permanece após recarregar a página.

## Próxima ação e verificações complementares

Reabrir o exercício criado e conferir a imagem salva. Testar formatos e tamanhos inválidos em casos separados; essas variações não recebem resultado nesta análise.

## Evidências e limites

- [Jam original](https://jam.dev/c/25c37a9b-e9bd-4e0c-adf1-4da528ae1d58).
- [Resumo e origem da evidência](../Evidencias/CT-RF25_Envio_Exercicio_Imagem/README.md).
- [Cronologia documental](../Evidencias/CT-RF25_Envio_Exercicio_Imagem/linha_do_tempo.txt).

Não foram confirmados nome, formato, tamanho ou conteúdo integral do arquivo, nem a persistência da imagem, sua recuperação ou a ausência de duplicação após nova submissão.

A análise utiliza quadros consultados e a listagem de rede; não corresponde a uma revisão quadro a quadro de todo o vídeo. Não houve nova execução no SIFIT, reteste ou inspeção do código. Vídeo original e capturas não foram copiados para o repositório; não há hash do vídeo nesta inclusão. Não foram reproduzidos credenciais, tokens ou corpos de autenticação.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)

