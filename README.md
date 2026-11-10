# 🧪 Documentação de QA — SIFIT

Documentação de testes manuais do sistema **SIFIT**, iniciada pelo caso **CT-RF01 — Esqueci minha senha**.

## 📌 Sobre o sistema

O SIFIT é um sistema de gestão de academias. Esta documentação reúne o planejamento, os casos de teste, os resultados e os defeitos identificados.

## 🎯 Objetivo

Documentar os requisitos, o planejamento, o resultado e as evidências do **CT-RF01**, que verifica o início da recuperação de senha pela opção "Esqueci minha senha".

## 🧱 Estrutura do repositório

| Documento | Conteúdo |
| --- | --- |
| [Análise de requisitos](SIFIT/Analise%20de%20requisitos.md) | RF01, critérios de aceitação e rastreabilidade da recuperação de senha. |
| [Plano de testes](SIFIT/Plano%20de%20testes.md) | Escopo, ambiente, execução, reteste e riscos. |
| [Cenário de recuperação de senha](SIFIT/Cenario_Teste/CT-RF01_Esqueci-senha.md) | Caso CT-RF01 em BDD, resultado obtido e evidências. |
| [Relatório dos testes](SIFIT/Relatorio%20dos%20testes.md) | Resultado da análise das evidências e pendências de reteste. |
| [Relatório de bugs](SIFIT/Relatorio-de-Bugs.md) | BUG-001 — Falha ao iniciar a recuperação de senha. |

## 🔬 Metodologia

**Técnicas aplicadas**

- Teste funcional — validação da abertura do fluxo de recuperação de senha.
- Análise exploratória — observação da interface, dos eventos, da rede e do console.
- Análise de evidências — conferência da gravação e dos registros disponíveis no Jam.

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

Página registrada na evidência: https://sifitalfa.centrion.com.br/login.
O CT-RF01 começa sem autenticação e não exige credenciais para acionar a opção.

## 📊 Status

🚧 Em andamento

O caso **CT-RF01**, associado ao **RF01**, está **reprovado conforme a gravação analisada**: "Esqueci minha senha" não abre o fluxo de recuperação e o Jam não registra requisições. O **BUG-001** permanece aberto, com reteste pendente após a correção. Esta atualização documental não inclui nova execução no sistema.
