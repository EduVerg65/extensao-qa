# 🧪 Cenário 41: Cadastro de turma sem modalidade selecionada, sem retorno visível

**Caso de teste:** CT-RF41

**Módulo:** SifitBox / Turmas recorrentes / Cadastro

**Status:** Reprovado nas evidências — sem feedback de validação visível; defeito em triagem.

**Gravação:** 15/11/2026, 18:51 BRT. **Revisão documental:** 15/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Cadastrar uma turma recorrente, ou informar de forma visível o dado que impede o envio, bloqueando o registro incompleto. |
| Requisito | [RF41](../Analise%20de%20requisitos.md#rf41) — referência de QA; confirmação de produto pendente. |
| Tipo / prioridade | Funcional manual / teste negativo; Média, proposta para triagem. |
| Defeito | [BUG-020](../Relatorio-de-Bugs.md#bug-020), em triagem. |
| Encaminhamento | Confirmar se a modalidade é obrigatória e como a validação deve ser exibida; reproduzir com captura de interface e rede e retestar após a definição. |
| Fonte | [Jam — SifitBox – Turmas](https://jam.dev/c/ee9a133b-d6b1-442d-b4b0-dd87595b7e70) e [evidências locais](../Evidencias/CT-RF41_Cadastro_Turma_Sem_Modalidade/README.md). A mesma gravação é a fonte de [CT-RF39](CT-RF39_Cadastro_Modalidade.md) e [CT-RF40](CT-RF40_Exclusao_Turmas_Modalidades.md). |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/sifitbox/turmas |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.78 / Windows (x86) 11. |
| Tela / arquivo de vídeo | 1920 × 911 informados no Jam. |
| Duração | 1 min 39 s |
| Rede | Classificada como rápida no Jam: 6,8 Mbps, latência de 50 ms. |
| Localização | Brasil. |
| Usuário exibido | Jair, conforme o canto superior direito da tela. |
| Versão / zoom / classificação do ambiente | Não confirmados; registrar antes de nova execução. |
| Dados | Formulário de Turma com nome "teste", horários 18:51 (início) e 18:51 ou 19:51 (término), dias Dom, Seg e Ter, 12 vagas, status Ativo e seletor Modalidade em branco. |

## Pré-condições

- Sessão autenticada com acesso a SifitBox – Turmas e à ação de cadastrar turma.
- Ao menos uma modalidade ativa para seleção; quatro turmas existentes registradas antes do envio.
- Regra de obrigatoriedade da modalidade e dos demais campos definida com o produto.
- Antes de uma nova execução, identificar versão, permissões e dados de referência e preparar a captura de interface e rede.

## Cenário BDD

```gherkin
Cenário: Tentar cadastrar uma turma sem selecionar a modalidade
  Dado que o formulário de Turma está preenchido, com a modalidade em branco
  Quando o usuário acionar o botão de envio de Turma
  Então o sistema deve bloquear o envio
  E indicar de forma visível o campo que precisa ser corrigido
  E não deve criar a turma

Cenário: Cadastrar uma turma com todos os dados válidos
  Dado que o formulário de Turma está preenchido com a modalidade selecionada
  Quando o usuário acionar o botão de envio de Turma
  Então o sistema deve criar a turma e apresentá-la na listagem
```

## Passos para execução ou reteste

1. Acessar SifitBox – Turmas e registrar a listagem de turmas e as modalidades disponíveis.
2. Acionar o botão de envio de Turma com o formulário vazio e observar mensagens e rede.
3. Preencher nome, horários, dias da semana, vagas e status, mantendo a modalidade em branco, e acionar o envio.
4. Conferir mensagens, foco, listagem e a ausência de requisição de criação.
5. Selecionar a modalidade, acionar o envio e conferir a turma na listagem e a persistência após recarga.

Este procedimento orienta a próxima execução. A evidência atual cobre o trecho gravado e os limites descritos abaixo; o segundo cenário (envio válido) não foi exercitado na gravação e não recebe resultado.

## Resultado esperado

O envio incompleto é bloqueado e o campo pendente é indicado de forma compreensível, sem criar registro; com todos os dados válidos, a turma é criada e listada.

## Resultado obtido na gravação

Nas tentativas gravadas, os cliques de envio não geram requisição de criação de turma e não apresentam mensagem de validação visível; o formulário permanece preenchido e a listagem de turmas não muda.

| Tempo | Registro |
| --- | --- |
| 0:17–0:20 | Cinco cliques em botão de envio com os formulários vazios; cursor sobre o botão Turma em 0:19. Nenhuma mensagem visível e nenhuma requisição. |
| 1:21–1:26 | Nome "teste" e horários preenchidos no formulário de Turma. |
| 1:28 | Clique em botão de envio; formulário de Turma com nome "teste", seletor Modalidade em branco, horários 18:51 e 18:51 e nenhum dia marcado; nenhuma mensagem visível. |
| 1:31–1:33 | Dias Dom, Seg e Ter marcados; clique em botão de envio com o cursor sobre o botão Turma (1:33). Formulário permanece preenchido; sem requisição de criação de turma. |
| 1:35 | Listagem de turmas com as mesmas quatro turmas; formulário de Turma ainda preenchido (horários 18:51 a 19:51). |

**Rede:** nas 35 entradas gravadas não há requisição de criação de turma. O único POST de criação é `POST /api/sifitbox/modalidades/salvar/1` (HTTP 201, [CT-RF39](CT-RF39_Cadastro_Modalidade.md)).

**Edição de turma na mesma gravação:** o lápis da turma de id 4 em 0:57 carrega o formulário (Turma Box Manual SIFIT 2026, Modalidade Manual SIFIT 2026, 09:00–10:00, Seg/Qua/Sex, 12 vagas, status Inativo), e o envio em torno de 1:05–1:06 gera `POST /api/sifitbox/turmas/atualizar/1` com HTTP 200; a resposta retorna a turma com `updated_at` 2026-11-15 21:51:03 e os mesmos dados. Não foi observada mensagem de confirmação.

**Conclusão:** Reprovado nas evidências por ausência de feedback visível nas tentativas de envio com formulário incompleto. A classificação não confirma que a modalidade seja obrigatória nem que a validação esteja ausente: uma validação nativa do navegador pode não aparecer em gravações de tela. A causa técnica não foi determinada.

## Critérios de aceitação para nova execução

1. O envio de Turma com campo obrigatório vazio é bloqueado e cada campo pendente recebe indicação compreensível.
2. Nenhum registro vazio ou incompleto é criado.
3. Com todos os dados válidos, a turma é criada, apresentada na listagem e mantida após recarga.
4. A ação de envio informa o resultado (sucesso ou impedimento) ao usuário.
5. O horário de término anterior ou igual ao de início recebe validação específica, conforme a regra do produto.

## Próxima ação e verificações complementares

Confirmar a regra e retestar com a captura de rede preparada. Permanecem fora do cenário gravado: envio válido, nome vazio, horário de término igual ou anterior ao de início, nenhum dia marcado, vagas inválidas e persistência após recarga. A ausência de validação visível é o mesmo padrão registrado em [CT-RF26](CT-RF26_Exercicio_Campos_Vazios.md) / [BUG-013](../Relatorio-de-Bugs.md#bug-013).

## Observação sobre os horários

Em 1:28 os horários estão em 18:51 e 18:51 (início igual ao término) e em 1:35 o término aparece como 19:51. A gravação não mostra qualquer mensagem sobre o intervalo de horário nem registra uma tentativa de envio específica com intervalo inválido; a validação do intervalo permanece a avaliar.

## Evidências e limites

- [Jam original — SifitBox – Turmas](https://jam.dev/c/ee9a133b-d6b1-442d-b4b0-dd87595b7e70).
- [Arquivos, origem e limites](../Evidencias/CT-RF41_Cadastro_Turma_Sem_Modalidade/README.md).
- [Formulário em 1:29](../Evidencias/CT-RF41_Cadastro_Turma_Sem_Modalidade/formulario_turma_01-29.png), [formulário em 1:33](../Evidencias/CT-RF41_Cadastro_Turma_Sem_Modalidade/formulario_turma_01-33.png), [listagens em 1:35](../Evidencias/CT-RF41_Cadastro_Turma_Sem_Modalidade/lista_apos_tentativa_01-35.png) e [edição da turma em 0:58](../Evidencias/CT-RF41_Cadastro_Turma_Sem_Modalidade/edicao_turma_00-58.png).
- [Requisição de atualização](../Evidencias/CT-RF41_Cadastro_Turma_Sem_Modalidade/requisicao_atualizar.png) e [resposta de atualização](../Evidencias/CT-RF41_Cadastro_Turma_Sem_Modalidade/resposta_atualizar.png).
- [Linha do tempo](../Evidencias/CT-RF41_Cadastro_Turma_Sem_Modalidade/linha_do_tempo.txt).

Foram consultados os painéis Info, Console (atividade do usuário e erros de rede), Network e Actions do Jam, o corpo da requisição e da resposta de atualização e os quadros do vídeo. As capturas foram extraídas da reprodução do Jam e mostram o botão de reprodução sobreposto. O botão acionado em 1:17 e em 1:28 não foi identificado com certeza nos quadros; o cursor sobre o botão Turma é visível em 0:19 e em 1:33. Não foram confirmados a obrigatoriedade da modalidade, a existência de validação nativa do navegador, o envio válido e a persistência. Não houve nova execução, inspeção do código, acesso ao banco ou correção da aplicação. O vídeo permanece no Jam.

Análise documental da gravação consultada em 15/11/2026. Esta inclusão não executa novamente o sistema e não constitui reteste. Versão da aplicação, zoom e classificação do ambiente não foram confirmados.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf41) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
