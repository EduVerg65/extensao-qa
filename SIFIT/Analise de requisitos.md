# Análise de requisitos — SIFIT

**Módulo:** Autenticação / Recuperação de senha

**Atualização:** 10/11/2026

Esta análise documenta o comportamento esperado para a opção "Esqueci minha senha", com base no relato e nas evidências fornecidas. Os critérios abaixo constituem a referência de QA para este fluxo; não representam validação de uma especificação formal pelo responsável pelo produto.

## RF01 — Iniciar recuperação de senha

| Campo | Descrição |
| --- | --- |
| **Requisito funcional** | O sistema deve permitir que um usuário não autenticado inicie a recuperação de senha pela opção "Esqueci minha senha" na tela de login. |
| **Ator** | Usuário sem acesso à sua senha. |
| **Pré-condição** | Página de login acessível e opção de recuperação visível. |
| **Gatilho** | Clique em "Esqueci minha senha". |
| **Comportamento esperado** | Exibir formulário ou página com os campos e as orientações necessários para iniciar a solicitação de redefinição. |
| **Pós-condição esperada** | Usuário consegue prosseguir com a identificação da conta e a solicitação de recuperação. |
| **Prioridade** | Alta, pois a falha impede o início da recuperação autônoma de acesso. |
| **Situação observada** | Não atendido na gravação: cliques sem abertura do fluxo e nenhum registro de requisição no Jam. |

### Critérios de aceitação

1. A opção deve estar disponível antes da autenticação.
2. O clique deve iniciar o fluxo de recuperação por formulário ou página própria.
3. Os campos e as orientações para a próxima etapa devem ser apresentados ao usuário.
4. Quando uma etapa depender do servidor, a interface deve realizar a requisição correspondente e apresentar o retorno ou a falha ao usuário.

A abertura de um formulário local pode ocorrer sem requisição de rede. Neste defeito, a ausência de requisições acompanha a ausência de qualquer abertura do fluxo; não comprova, por si só, uma falha no servidor.

### Pontos a definir para a recuperação completa

O identificador da conta, o canal de recuperação, o contrato da API, as mensagens de retorno, a validade de eventual token e as regras de redefinição precisam ser confirmados com o responsável pelo sistema antes de detalhar os testes das etapas seguintes. Não há comprovação de envio de e-mail, geração de token ou alteração de senha nas evidências analisadas.

## Rastreabilidade

| Requisito | Cenário / caso | Defeito | Resultado | Evidências |
| --- | --- | --- | --- | --- |
| RF01 | [Cenário 1 / CT-RF01](Cenario_Teste/CT-RF01_Esqueci-senha.md) | [BUG-001](Relatorio-de-Bugs.md#bug-001--link-esqueci-minha-senha-não-executa-nenhuma-ação) | Reprovado nas evidências; reteste pendente | [Drive](https://drive.google.com/file/d/1f6AqYunchDH4R9Yw1JpbyX9x28UQGcbo/view?usp=sharing) e [Jam](https://jam.dev/c/0273b203-b999-493d-9919-2d143bc13301) |

## Base da análise

- **Relato:** a opção "Esqueci minha senha" não funciona e não dispara requisição ao ser acionada.
- **Jam:** gravação criada em 23/10/2026, com 14 segundos, em https://sifitalfa.centrion.com.br/login; cliques repetidos, permanência na tela de login, 0 requisições registradas e 0 erros de console registrados.
- **Drive:** arquivo de vídeo identificado como `CT-RF01_Esqueci-senha`, mantido como evidência complementar; conteúdo não inspecionado nesta revisão.
- **Limite:** não houve inspeção do código da aplicação nem nova execução no sistema em 10/11/2026.
