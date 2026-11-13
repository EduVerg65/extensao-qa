# 🧪 Cenário 04: Login com sucesso

**Caso de teste:** CT-RF04_loginComSucesso

**Módulo:** Autenticação / Login

**Status:** Aprovado conforme a execução gravada no Jam.

**Data da gravação e da análise documental:** 13/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| ID | **CT-RF04_loginComSucesso**. |
| Objetivo | Verificar se credenciais válidas permitem autenticar o usuário e acessar o dashboard do SIFIT. |
| Requisito | [RF04 — Autenticar usuário com credenciais válidas](../Analise%20de%20requisitos.md#rf04--autenticar-usuário-com-credenciais-válidas). |
| Tipo / prioridade | Funcional manual, fluxo positivo / Alta, por validar o acesso ao sistema. |
| Defeito associado | Nenhum identificado para o fluxo de login avaliado. |
| Evidência | [Jam — Login com sucesso](https://jam.dev/c/5e4a28be-4e80-43d3-9587-1b113723cc38). |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página inicial | https://sifit.centrion.com.br/login |
| Destino esperado e observado | https://sifit.centrion.com.br/dashboard |
| Backend | https://backendsifit.centrion.com.br |
| Navegador | Chrome 157.0.8103.51. |
| Sistema / janela | Windows 11 (x86) / 1536 × 742, conforme metadados do Jam. |
| Autor da gravação | Leonardo Barbosa. |
| Duração | Aproximadamente 12 segundos. |
| Versão da aplicação / zoom / classificação do ambiente | Não informados nas evidências consultadas. |
| Login e senha | Credenciais válidas da conta utilizada na gravação; valores omitidos neste documento. Em nova execução, utilizar conta de teste autorizada. |
| Manter conectado | Opção desmarcada nos quadros consultados; persistência entre sessões não avaliada. |

## Pré-condições

- Página de login acessível, com os campos **Login**, **Senha** e o botão **Entrar** disponíveis.
- Conta ativa, credenciais válidas e permissão para acessar o dashboard.
- Para repetir o caso, iniciar sem sessão autenticada e preparar a captura de navegação e rede antes de enviar o formulário.

## Cenário BDD

```gherkin
Cenário: Acessar o dashboard com credenciais válidas
  Dado que o usuário está na página de login do SIFIT
  E possui uma conta ativa com acesso ao dashboard
  Quando preencher o campo "Login" com um identificador válido
  E preencher o campo "Senha" com a senha correspondente
  E clicar em "Entrar"
  Então o sistema deve autenticar o usuário
  E redirecionar para "https://sifit.centrion.com.br/dashboard"
  E apresentar o menu de navegação e o resumo da academia
```

## Passos e resultados

| Passo | Ação | Resultado esperado | Resultado observado no Jam |
| --- | --- | --- | --- |
| 1 | Acessar `/login`. | Formulário de autenticação disponível. | Tela com Login, Senha e Entrar visível no início. |
| 2 | Preencher Login e Senha com credenciais válidas. | Campos preenchidos e senha mascarada. | Login preenchido e senha mascarada nos quadros de aproximadamente 00:03 e 00:05. |
| 3 | Clicar em **Entrar**. | Sistema processa a autenticação e permite o acesso. | Clique em aproximadamente 00:06; `POST /api/login` e `POST /api/verifica-token-logado` retornam HTTP 200. |
| 4 | Conferir destino e conteúdo após o envio. | URL `/dashboard`, menu e resumo da academia visíveis. | Navegação para `/dashboard` em aproximadamente 00:06; painel aparece em 00:07 e apresenta cartões preenchidos nos quadros de 00:09 e 00:11. |

## Resultado esperado

O usuário deve ser autenticado com credenciais válidas e acessar o dashboard, com o menu de navegação e o resumo da academia visíveis.

## Resultado obtido

Após o clique em **Entrar**, as duas chamadas de autenticação registram HTTP 200 e o navegador acessa `/dashboard`. O vídeo mostra o menu lateral, o resumo da academia e cartões como **Clientes Ativos**, **Clientes Ausentes** e **Sem Matrículas**. As requisições de carregamento do painel listadas na cronologia também retornam HTTP 200.

**Conclusão:** aprovado para o fluxo positivo registrado. A classificação combina navegação, conteúdo visual e registros de rede; HTTP 200 isoladamente não seria suficiente para aprovar o caso.

## Critérios de aceitação

| Critério | Evidência | Situação |
| --- | --- | --- |
| Formulário permite informar Login e Senha. | Quadros anteriores ao envio. | Atendido. |
| Senha permanece mascarada na interface. | Quadro de aproximadamente 00:05. | Atendido na gravação. |
| Credenciais válidas permitem concluir a autenticação. | Chamadas HTTP 200 e acesso visual ao painel após Entrar. | Atendido. |
| Usuário é direcionado para `/dashboard`. | Evento de navegação em aproximadamente 00:06. | Atendido. |
| Menu de navegação e resumo da academia são apresentados. | Quadros de aproximadamente 00:09 e 00:11. | Atendido. |

## Evidências e limites

- [Jam — gravação de login com sucesso](https://jam.dev/c/5e4a28be-4e80-43d3-9587-1b113723cc38).
- [Resumo das evidências e cronologia](../Evidencias/CT-RF04_loginComSucesso/README.md).

Foram consultados os metadados, a cronologia de ações e requisições e o mosaico de seis quadros do vídeo. Não houve nova execução na aplicação nem criação de teste automatizado; o repositório contém documentação de testes manuais.

A gravação não valida credenciais inválidas, campos vazios, bloqueio de conta, logout, expiração da sessão, persistência de **Manter conectado**, permissões de outros perfis ou exatidão dos dados dos cartões. O nome exibido no cabeçalho não foi comparado com o cadastro da conta. Corpos de autenticação, tokens e senha não foram consultados nem reproduzidos. Uma nova execução do fluxo positivo pode ser usada como regressão, com versão e dados de teste identificados.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
