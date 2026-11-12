# 🧪 Documentação de QA — SIFIT

Documentação de testes manuais do sistema **SIFIT**, com os casos **CT-RF01 — Esqueci minha senha** e **CT-RF02_ERRO — Perfil**.

## 📌 Sobre o sistema

O SIFIT é um sistema de gestão de academias. Esta documentação reúne o planejamento, os casos de teste, os resultados e os defeitos identificados.

## 🎯 Objetivo

Documentar os requisitos, o planejamento, os resultados e as evidências da recuperação de senha e da apresentação do perfil do usuário autenticado.

## 🧱 Estrutura do repositório

| Documento | Conteúdo |
| --- | --- |
| [Análise de requisitos](SIFIT/Analise%20de%20requisitos.md) | RF01 e RF02, critérios de aceitação e rastreabilidade. |
| [Plano de testes](SIFIT/Plano%20de%20testes.md) | Escopo, ambiente, execução, reteste e riscos. |
| [Cenário de recuperação de senha](SIFIT/Cenario_Teste/CT-RF01_Esqueci-senha.md) | Caso CT-RF01 em BDD, resultado obtido e evidências. |
| [Cenário de Perfil](SIFIT/Cenario_Teste/CT-RF02_ERRO.md) | Caso CT-RF02_ERRO em BDD, resultado e análise do HTML. |
| [Evidências de Perfil](SIFIT/Evidencias/CT-RF02_ERRO/) | Captura da tela e recorte do DOM fornecido. |
| [Relatório dos testes](SIFIT/Relatorio%20dos%20testes.md) | Resultado da análise das evidências e pendências de reteste. |
| [Relatório de bugs](SIFIT/Relatorio-de-Bugs.md) | BUG-001 — Recuperação de senha; BUG-002 — Perfil desconfigurado. |

## 🔬 Metodologia

**Técnicas aplicadas**

- Teste funcional — validação da abertura da recuperação de senha e da apresentação dos dados do perfil.
- Análise exploratória — observação da interface, dos eventos, da rede e do console.
- Análise de evidências — conferência das gravações e dos registros disponíveis no Jam, da captura e do HTML fornecidos.

**Formatos**

- BDD (Gherkin) para cenários
- Tabelas e checklists para casos de teste

**Processo**
Análise de requisitos → Planejamento → Execução → Registro de defeitos → Relatório

## 🛠️ Ferramentas

| Ferramenta | Uso |
|---|---|
| Jam | Gravação de evidências em vídeo |
| DevTools (Network / Console) | Observação de requisições e erros no navegador |
| Google Drive | Armazenamento das evidências fornecidas |
| Markdown / GitHub | Documentação e versionamento |

## 🔐 Ambiente

O CT-RF01 registra https://sifitalfa.centrion.com.br/login e começa sem autenticação, sem exigir credenciais para acionar a opção. O CT-RF02_ERRO registra navegações para https://sifit.centrion.com.br/profile com usuário autenticado; a aba Info do Jam apresenta `/configuracoes`. Os ambientes não devem ser tratados como equivalentes sem confirmação.

## 📊 Status

🚧 Em andamento

O caso **CT-RF01**, associado ao **RF01**, está **reprovado conforme a gravação analisada**: "Esqueci minha senha" não abre o fluxo de recuperação e o Jam não registra requisições. O **BUG-001** permanece aberto, com reteste pendente após a correção. Esta atualização documental não inclui nova execução no sistema.

O **CT-RF02_ERRO**, associado ao **RF02**, está **reprovado conforme as evidências analisadas**: o perfil exibe conteúdo fictício, campos ausentes visualmente e layout desconfigurado. O **BUG-002** permanece aberto, com reteste pendente. A revisão de 12/11/2026 inclui a captura, o recorte do HTML e a consulta ao Jam; a causa técnica ainda precisa ser confirmada no código.
