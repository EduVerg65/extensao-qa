# 🧪 Cenário 72: Telefone do lead aceita 30 dígitos sem validação

**Caso de teste:** CT-RF72

**Módulo:** Prospecção / Leads / Validação do telefone

**Status:** Reprovado nas evidências — telefone de 30 dígitos aceito e gravado; defeito em triagem.

**Gravação:** 15/11/2026, 21:52 BRT. **Revisão documental:** 15/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Validar o campo Telefone do formulário de lead, que apresenta o formato "(00) 00000-0000", impedindo valores com tamanho ou formato inválidos. |
| Requisito | [RF72](../Analise%20de%20requisitos.md#rf72) — referência de QA; confirmação de produto pendente. |
| Tipo / prioridade | Funcional manual / teste negativo; Média, proposta para triagem. |
| Defeito | [BUG-038](../Relatorio-de-Bugs.md#bug-038), em triagem. |
| Encaminhamento | Confirmar a regra do campo (tamanho, máscara e caracteres aceitos), reproduzir com a validação visível e retestar o envio válido e inválido e a persistência. |
| Fonte | [Jam — Prospecção](https://jam.dev/c/308607ff-8abc-40af-8c7c-429ce506ed64) e [evidências locais](../Evidencias/CT-RF89_Telefone_Lead_Sem_Validacao/README.md). A mesma gravação é a fonte de [CT-RF62](CT-RF62_Tema_Notificacoes_Prospeccao.md), [CT-RF63](CT-RF63_Busca_Leads_Prospeccao.md), [CT-RF64](CT-RF64_Filtro_Estagio_Leads.md), [CT-RF71](CT-RF71_Cadastro_Lead_Prospeccao.md) e [CT-RF75](CT-RF75_Edicao_Lead_Prospeccao.md). |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/prospeccao |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.78 / Windows (x86) 11. |
| Tela / arquivo de vídeo | 1920 × 911 informados no Jam. |
| Duração | 1 min 2 s |
| Rede | Classificada como rápida no Jam: 5,4 Mbps, latência de 100 ms. |
| Localização | Brasil. |
| Usuário exibido | Jair, conforme o canto superior direito da tela. |
| Versão / zoom / classificação do ambiente | Não confirmados; registrar antes de nova execução. |
| Dados | Telefone digitado em duas etapas: 44999999999 (0:33) e 5757534534534534534 (0:37), resultando em 30 dígitos; demais campos de teste (nome "teste", estágio Interessado). |

## Pré-condições

- Sessão autenticada com acesso à tela Prospecção.
- Base de leads conhecida, com códigos, nomes e estágios registrados antes da execução.
- Antes de uma nova execução, identificar versão, permissões e dados de referência e preparar a captura de interface e rede.

## Cenário BDD

```gherkin
Cenário: Rejeitar telefone com tamanho inválido
  Dado que o formulário de lead apresenta o campo Telefone com o formato (00) 00000-0000
  Quando o usuário informar um telefone com 30 dígitos e acionar Salvar Lead
  Então o sistema deve impedir o envio e informar o formato esperado
  E nenhum lead deve ser criado com o telefone inválido
```

## Passos para execução ou reteste

1. Acionar Adicionar Lead e preencher nome e estágio.
2. Informar no campo Telefone um valor com mais de 11 dígitos (por exemplo, 30 dígitos) e outro com letras.
3. Acionar Salvar Lead e observar a mensagem de validação e a rede.
4. Conferir a listagem e o registro criado (Visualizar Lead).
5. Repetir com telefones de 8, 10 e 11 dígitos para confirmar o formato aceito.

Este procedimento orienta a próxima execução. A evidência atual cobre o trecho gravado e os limites descritos abaixo; passos complementares não recebem resultado de execução nesta revisão.

## Resultado esperado

O campo limita o tamanho ou aplica máscara compatível com o formato exibido, e um telefone com 30 dígitos é rejeitado com mensagem clara, sem criação do lead.

## Resultado obtido na gravação

O campo aceitou 30 dígitos (44999999999 e 5757534534534534534 digitados em duas etapas, sem máscara aplicada), o lead foi criado (código 10) e o valor de 30 dígitos retornou na consulta do lead (buscar-lead). Nenhuma mensagem de validação foi apresentada.

| Tempo | Registro |
| --- | --- |
| 0:30–0:33 | Campo Telefone informado com 44999999999 (11 dígitos); placeholder "(00) 00000-0000" visível no formulário. |
| 0:35–0:37 | Mais 19 dígitos (5757534534534534534) digitados no mesmo campo; em 0:47 o campo apresenta o valor longo, sem máscara e truncado pela largura do campo. |
| 0:38 | Salvar Lead: criação aceita (HTTP 200, id 10) com o telefone de 30 dígitos no corpo; sem mensagem de validação. |
| 0:45–0:47 | Consulta do lead 10 (buscar-lead, HTTP 200): resposta com o telefone de 30 dígitos; o modal Visualizar Lead apresenta o valor longo. |

**Rede:** o corpo de `POST /api/salvar-lead/1` contém `"telefone"` com 30 dígitos e a resposta de `POST /api/buscar-lead/1` devolve o mesmo valor, o que indica gravação sem validação no cliente e, provavelmente, no servidor; a regra do campo não foi informada.

**Conclusão:** Reprovado nas evidências. O campo Telefone exibe o formato "(00) 00000-0000", mas aceitou e gravou um valor de 30 dígitos sem máscara e sem mensagem. A reprovação depende da regra do campo, que não foi informada; se o campo for livre, o placeholder induz ao erro.

## Critérios de aceitação para nova execução

1. O campo Telefone limita o tamanho e os caracteres ao formato definido pelo produto.
2. Um telefone com tamanho ou caracteres inválidos é rejeitado antes da gravação, com mensagem clara.
3. A máscara exibida no placeholder é aplicada durante a digitação.
4. O servidor valida o telefone independentemente da interface.
5. O telefone válido é gravado e exibido no formato definido.

## Próxima ação e verificações complementares

Registrar o BUG-038 em triagem e reproduzir com telefones de 8, 10, 11 e 30 dígitos e com letras, capturando a mensagem de validação, o corpo e a resposta; confirmar a regra com o produto e verificar a validação no servidor.

## Observação sobre a digitação em duas etapas

O Console do Jam registra dois momentos de digitação (0:33 e 0:37) em campos identificados por seletores diferentes ("+2 more" e "+3 more"), e o corpo da requisição mostra um único telefone de 30 dígitos; a leitura assume que os dois trechos foram digitados no mesmo campo, o que o quadro de 0:47 é compatível, mas não prova.

## Evidências e limites

- [Jam original — Prospecção](https://jam.dev/c/308607ff-8abc-40af-8c7c-429ce506ed64).
- [Arquivos, origem e limites](../Evidencias/CT-RF89_Telefone_Lead_Sem_Validacao/README.md).
- [Campo Telefone em 0:47](../Evidencias/CT-RF89_Telefone_Lead_Sem_Validacao/telefone_30_digitos_00-47.png), [Corpo da requisição salvar-lead com o telefone de 30 dígitos (e-mail mascarado pelo Jam).](../Evidencias/CT-RF89_Telefone_Lead_Sem_Validacao/requisicao_salvar.png), [Resposta de buscar-lead](../Evidencias/CT-RF89_Telefone_Lead_Sem_Validacao/resposta_buscar.png), [Lista de rede](../Evidencias/CT-RF89_Telefone_Lead_Sem_Validacao/rede_lista.jpg).
- [Linha do tempo](../Evidencias/CT-RF89_Telefone_Lead_Sem_Validacao/linha_do_tempo.txt).

Foram consultados os painéis Info, Console, Network e Actions do Jam e os quadros do vídeo. As capturas foram extraídas da reprodução do Jam; quadros com o e-mail digitado no formulário não foram incluídos nem recortados com esse dado. O recorte do campo Telefone omite os demais campos do formulário. A regra do campo, a validação no servidor e o comportamento com letras ou tamanhos menores não foram exercitados. Não houve nova execução, inspeção do código, acesso ao banco ou correção da aplicação. O vídeo permanece no Jam.

Análise documental da gravação consultada em 15/11/2026. Esta inclusão não executa novamente o sistema e não constitui reteste. Versão da aplicação, zoom e classificação do ambiente não foram confirmados.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf72) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
