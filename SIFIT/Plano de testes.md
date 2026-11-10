# Plano de testes — SIFIT

**Atualização:** 10/11/2026

**Escopo:** CT-RF01 — Recuperação de senha.

## Objetivo

Verificar se a opção "Esqueci minha senha" inicia o fluxo de recuperação de acesso e manter a rastreabilidade entre requisito, caso de teste, evidências e defeito.

## Escopo

- Disponibilidade da opção na tela de login, antes da autenticação.
- Abertura do formulário ou da página de recuperação após o clique.
- Observação da interface, das requisições de rede e dos erros de console.
- Registro e reteste do BUG-001 após disponibilização da correção.

As etapas de envio da solicitação, entrega de mensagem, uso de token e definição de nova senha dependem da abertura do fluxo e da definição de suas regras. Não estão cobertas pela execução gravada.

## Ambiente e preparação

| Item | Definição |
| --- | --- |
| URL da evidência atual | https://sifitalfa.centrion.com.br/login |
| Ambiente | Homologação; confirmar a mesma versão no reteste. |
| Navegador / sistema da gravação | Chrome 155.0.8059.85 / Windows 11, conforme metadados do Jam. |
| Estado da sessão | Usuário não autenticado. |
| Credenciais | Não são necessárias para acionar a opção. |
| Ferramentas | Navegador, DevTools (Network e Console) e Jam para evidências. |
| Preparação da rede no reteste | Habilitar captura de todas as requisições, remover filtros, limpar o histórico e preservar registros se houver navegação. |

## Caso de teste e situação

| Requisito | Caso de teste | Tipo | Resultado nas evidências | Defeito | Próxima ação |
| --- | --- | --- | --- | --- | --- |
| [RF01](Analise%20de%20requisitos.md#rf01--iniciar-recuperação-de-senha) | [CT-RF01 — Acionar "Esqueci minha senha"](Cenario_Teste/CT-RF01_Esqueci-senha.md) | Funcional / fluxo positivo, com análise exploratória de rede | Reprovado | [BUG-001](Relatorio-de-Bugs.md#bug-001--link-esqueci-minha-senha-não-executa-nenhuma-ação) | Corrigir e retestar. |

## Procedimento de execução e reteste

1. Registrar data, URL, versão disponível e navegador da execução.
2. Acessar a página de login sem autenticação e preparar Network e Console.
3. Executar o [CT-RF01](Cenario_Teste/CT-RF01_Esqueci-senha.md), observando a interface e os registros após o clique.
4. Comparar o comportamento com os critérios do RF01 e registrar o resultado obtido.
5. Salvar evidências visuais e de rede, inclusive quando não houver requisições.
6. Após a correção, repetir o caso e verificar se o fluxo abre e permite prosseguir. Uma abertura local de formulário não exige, por si só, requisição ao servidor.
7. Atualizar o relatório de testes e o BUG-001 com as novas evidências e o resultado do reteste.

## Critérios de entrada e saída

**Entrada:** ambiente acessível, opção visível e ferramentas de captura disponíveis. Para o reteste, correção disponibilizada em uma versão identificável.

**Saída da execução:** caso executado e resultado documentado com evidências. A execução reprovada pode ser encerrada com o defeito aberto.

**Aceitação da correção:** todos os critérios do CT-RF01 atendidos e reteste documentado. O BUG-001 permanece aberto até essa confirmação. A aprovação deste caso não comprova a recuperação completa da senha.

## Riscos e Limitações do Ambiente

| ID | Risco | Impacto | Mitigação |
|---|---|---|---|
| R01 | Fluxo de recuperação não abre | Impede testar as etapas seguintes | Registrar BUG-001; retestar a abertura após a correção |
| R02 | Captura de rede desativada ou filtrada | Ausência aparente de requisições pode levar a diagnóstico incorreto | Confirmar captura ativa, remover filtros e correlacionar rede com o comportamento visual |
| R03 | Evidências obtidas em versões diferentes | Resultados podem não ser reproduzíveis na versão escolhida | Registrar URL e versão em cada execução |

## Documentos associados

- [Análise de requisitos](Analise%20de%20requisitos.md)
- [Caso CT-RF01](Cenario_Teste/CT-RF01_Esqueci-senha.md)
- [Relatório dos testes](Relatorio%20dos%20testes.md)
- [Relatório de bugs](Relatorio-de-Bugs.md)
