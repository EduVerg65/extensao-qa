# 🧪 Cenário 01: Recuperação de senha na plataforma

**Módulo:** Autenticação / Recuperação de senha

**Status:** Reprovado conforme as evidências; reteste pendente.

**Padronização documental:** 13/11/2026; análise original de 10/11/2026 preservada.

---

## Caso de Teste 01: Acionamento da opção "Esqueci minha senha".

| ID | Descrição |
| --- | --- |
| **CT-RF01** | Verificar se a opção "Esqueci minha senha" inicia o fluxo de recuperação de acesso na plataforma SIFIT. |

| **Pré-condições** |
| --- |
| Acessar a página de login do SIFIT sem estar autenticado. |
| A opção "Esqueci minha senha" deve estar visível. |
| Para verificar a rede, abrir as ferramentas de desenvolvedor na aba Network (Rede), habilitar a captura de todas as requisições e limpar os registros antes do clique. |
| Não é necessário informar credenciais para iniciar esse fluxo. |

| **Passos** |
| --- |
| **DADO** que estamos na página de login do SIFIT em https://sifitalfa.centrion.com.br/login |
| **E** a opção "Esqueci minha senha" está disponível |
| **E** estamos monitorando as requisições na aba Network (Rede) |
| **QUANDO** clicarmos na opção "Esqueci minha senha" |
| **ENTÃO** o sistema deve apresentar um formulário ou uma página para iniciar a recuperação da senha |
| **E** deve permitir que o usuário prossiga com a identificação da conta e a solicitação de redefinição |

| **Critérios de aceitação** |
| --- |
| O clique deve abrir o formulário ou a página de recuperação de senha, sem exigir autenticação prévia. |
| A interface deve apresentar os campos e as orientações necessários para prosseguir com a solicitação. |
| Se a abertura do fluxo depender de uma chamada ao servidor, a requisição correspondente deve ser disparada e tratada pela interface. |
| A ausência de requisição no clique, isoladamente, não reprova uma abertura local de formulário; a falha deste caso é a ausência de início do fluxo. |

| **Resultado obtido** |
| --- |
| Ao clicar em "Esqueci minha senha", o formulário de recuperação não é exibido e o usuário permanece na tela de login. |
| O Jam registra cliques repetidos entre aproximadamente 00:02 e 00:12, sem mudança para o fluxo de recuperação. |
| A consulta aos registros de rede do Jam retorna **0 requisições** na gravação. |
| A consulta aos erros do console do Jam retorna **0 mensagens**. Isso não determina a causa da falha. |

| **Status e rastreabilidade** |
| --- |
| **Resultado:** Reprovado, conforme as evidências da execução gravada. |
| **Requisito:** [RF01 — Iniciar recuperação de senha](../Analise%20de%20requisitos.md#rf01--iniciar-recuperação-de-senha). |
| **Defeito associado:** [BUG-001](../Relatorio-de-Bugs.md#bug-001--link-esqueci-minha-senha-não-executa-nenhuma-ação). |
| **Severidade / prioridade:** Alta / Alta. |
| **Data da gravação do Jam:** 23/10/2026. **Revisão documental:** 10/11/2026. |
| **Reteste:** Pendente após a correção; não foi realizada uma nova execução nesta revisão. |

| **Evidências** |
| --- |
| [Vídeo no Google Drive — CT-RF01_Esqueci-senha](https://drive.google.com/file/d/1f6AqYunchDH4R9Yw1JpbyX9x28UQGcbo/view?usp=sharing) |
| [Jam — Erro no esqueci a senhas](https://jam.dev/c/0273b203-b999-493d-9919-2d143bc13301) |

O comportamento visual e os registros de rede e console foram analisados no Jam. O vídeo do Drive foi identificado como evidência complementar; seu conteúdo não foi inspecionado nesta revisão.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório de bugs](../Relatorio-de-Bugs.md)
