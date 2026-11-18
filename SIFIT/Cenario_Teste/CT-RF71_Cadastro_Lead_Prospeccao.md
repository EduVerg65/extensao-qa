# 🧪 Cenário 71: Cadastro de lead com duas requisições de criação

**Caso de teste:** CT-RF71

**Módulo:** Prospecção / Leads / Cadastro

**Status:** A validar — regra ou contexto pendente.

**Gravação:** 15/11/2026, 21:52 BRT. **Revisão documental:** 15/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Cadastrar um lead informando nome, estágio, e-mail, telefone e observação e apresentá-lo na listagem, com uma única gravação. |
| Requisito | [RF71](../Analise%20de%20requisitos.md#rf71) — referência de QA; confirmação de produto pendente. |
| Tipo / prioridade | Exploratório / regra a confirmar; Média, proposta para triagem. |
| Defeito | Sem defeito confirmado. |
| Encaminhamento | Confirmar se o segundo POST de criação gerou um registro adicional ou foi descartado, capturando corpos e respostas das duas chamadas em nova execução; registrar defeito apenas se houver duplicidade confirmada. |
| Fonte | [Jam — Prospecção](https://jam.dev/c/308607ff-8abc-40af-8c7c-429ce506ed64) e [evidências locais](../Evidencias/CT-RF88_Cadastro_Lead_Prospeccao/README.md). A mesma gravação é a fonte de [CT-RF62](CT-RF62_Tema_Notificacoes_Prospeccao.md), [CT-RF63](CT-RF63_Busca_Leads_Prospeccao.md), [CT-RF64](CT-RF64_Filtro_Estagio_Leads.md), [CT-RF72](CT-RF72_Telefone_Lead_Sem_Validacao.md) e [CT-RF75](CT-RF75_Edicao_Lead_Prospeccao.md). |

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
| Dados | Lead "teste", estágio Interessado, e-mail com valor omitido pelo Jam, telefone de teste e observação "sdasdad"; base com 7 leads antes do cadastro. |

## Pré-condições

- Sessão autenticada com acesso à tela Prospecção.
- Base de leads conhecida, com códigos, nomes e estágios registrados antes da execução.
- Antes de uma nova execução, identificar versão, permissões e dados de referência e preparar a captura de interface e rede.

## Cenário BDD

```gherkin
Cenário: Cadastrar um lead com uma única gravação
  Dado que o usuário abriu o formulário Adicionar Lead
  Quando informar nome, estágio, e-mail, telefone e observação e acionar Salvar Lead uma vez
  Então o lead deve ser criado uma única vez
  E deve aparecer na listagem com o estágio informado e os cartões atualizados
```

## Passos para execução ou reteste

1. Acessar Prospecção com o painel de rede aberto e registrar a listagem e os cartões.
2. Acionar Adicionar Lead e conferir o estágio inicial (Novo Contato) e o código "Novo".
3. Informar nome, estágio, e-mail, telefone e observação e acionar Salvar Lead uma única vez.
4. Contar as requisições de criação e conferir corpo e resposta de cada uma.
5. Conferir a listagem, os cartões e, após recarga, a ausência de registros duplicados.

Este procedimento orienta a próxima execução. A evidência atual cobre o trecho gravado e os limites descritos abaixo; passos complementares não recebem resultado de execução nesta revisão.

## Resultado esperado

Um clique em Salvar Lead gera uma única requisição de criação, o lead aparece uma vez na listagem com o estágio informado, e os cartões Leads e do estágio acompanham o novo registro.

## Resultado obtido na gravação

Um clique em Salvar Lead (0:38) gerou dois `POST /api/salvar-lead/1` com HTTP 200; a primeira resposta devolveu `{"verifica_erro": false, "id": 10}` e a listagem apresentou um único lead novo (código 10, estágio Interessado), com Leads 7 → 8 e Interessados 2 → 3. Corpo e resposta da segunda chamada não foram capturados.

| Tempo | Registro |
| --- | --- |
| 0:22–0:24 | Clique em Adicionar Lead: formulário com estágio atual "Novo Contato", código "Novo", campos Nome, Estágio do Lead, E-mail, Telefone e Observação. |
| 0:25–0:37 | Preenchimento: nome "teste", estágio Interessado, e-mail (valor omitido), telefone e observação "sdasdad". |
| 0:38 | Clique em Salvar Lead: primeiro POST salvar-lead/1 (HTTP 200, id 10); segundo POST salvar-lead/1 (HTTP 200) precedido de OPTIONS; corpo e resposta do segundo indisponíveis. |
| 0:39 | Modal fechado; listagem com 8 leads, incluindo o código 10 "teste" (Interessado, data 16/11/2026); cartões Leads 8, Novos Contatos 2 e Interessados 3. |

**Rede:** `POST /api/salvar-lead/1` (HTTP 200, 31 B) com corpo {"nome": "teste", "estagio": "INTERESSADO", "observacao": "sdasdad", e-mail e telefone} e resposta `{"verifica_erro": false, "id": 10}`; em seguida `OPTIONS` (204) e novo `POST /api/salvar-lead/1` (HTTP 200), sem corpo capturado; depois `GET /api/leads/1` (HTTP 200, 1,9 KiB).

**Conclusão:** A validar. O lead foi criado e apareceu na listagem, mas um único clique gerou duas requisições de criação com HTTP 200. Foi visível apenas um registro novo (código 10), o que é compatível com o descarte do segundo envio ou com falha silenciosa da segunda resposta; não há duplicidade confirmada, e por isso não há defeito registrado.

## Critérios de aceitação para nova execução

1. Um clique em Salvar Lead gera uma única requisição de criação.
2. O lead é gravado uma única vez e aparece na listagem com o estágio informado.
3. Os cartões Leads e do estágio acompanham o novo registro.
4. O botão é protegido contra segundo envio enquanto a requisição está em andamento.
5. Após recarga, a listagem contém um único lead com os dados informados.

## Próxima ação e verificações complementares

Reexecutar capturando corpo e resposta das duas requisições e recarregar a listagem para confirmar a ausência de duplicidade; registrar defeito apenas se houver registro adicional ou erro silencioso. Os campos obrigatórios (nome em branco, e-mail inválido) não foram exercitados.

## Observação sobre o padrão de duas requisições

O mesmo padrão (um clique, dois `POST` de criação com HTTP 200 e um registro visível) foi observado no [CT-RF51](CT-RF51_Cadastro_Despesa_Fixa.md); a comparação sugere comportamento comum do envio nos formulários, sem confirmação no código.

## Observação sobre o telefone

O telefone informado tem 30 dígitos e foi aceito na gravação; o ponto é tratado no [CT-RF72](CT-RF72_Telefone_Lead_Sem_Validacao.md).

## Evidências e limites

- [Jam original — Prospecção](https://jam.dev/c/308607ff-8abc-40af-8c7c-429ce506ed64).
- [Arquivos, origem e limites](../Evidencias/CT-RF88_Cadastro_Lead_Prospeccao/README.md).
- [Formulário Adicionar Lead em 0:24](../Evidencias/CT-RF88_Cadastro_Lead_Prospeccao/modal_adicionar_00-24.png), [Listagem em 0:39](../Evidencias/CT-RF88_Cadastro_Lead_Prospeccao/lista_apos_cadastro_00-39.png), [Corpo da requisição salvar-lead (e-mail mascarado pelo Jam).](../Evidencias/CT-RF88_Cadastro_Lead_Prospeccao/requisicao_salvar.png), [Resposta da primeira requisição salvar-lead](../Evidencias/CT-RF88_Cadastro_Lead_Prospeccao/resposta_salvar.png), [Lista de rede](../Evidencias/CT-RF88_Cadastro_Lead_Prospeccao/rede_lista.jpg).
- [Linha do tempo](../Evidencias/CT-RF88_Cadastro_Lead_Prospeccao/linha_do_tempo.txt).

Foram consultados os painéis Info, Console, Network e Actions do Jam e os quadros do vídeo. As capturas foram extraídas da reprodução do Jam; quadros com o e-mail digitado no formulário não foram incluídos nem recortados com esse dado. O corpo e a resposta da segunda requisição de criação e a persistência após recarga não foram verificados. Não houve nova execução, inspeção do código, acesso ao banco ou correção da aplicação. O vídeo permanece no Jam.

Análise documental da gravação consultada em 15/11/2026. Esta inclusão não executa novamente o sistema e não constitui reteste. Versão da aplicação, zoom e classificação do ambiente não foram confirmados.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf71) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
