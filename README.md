# 🧪 Testes Manuais — SIFIT

Repositório de documentação de testes manuais do **SIFIT**, sistema de gestão de academias. Reúne requisitos, planejamento, cenários em BDD, relatórios de bugs e evidências dos fluxos avaliados.

## 🎯 Objetivo

- Organizar a documentação de QA por requisito e funcionalidade.
- Registrar o comportamento esperado e os resultados observados nas evidências.
- Relacionar cada cenário ao defeito identificado e ao reteste necessário.

---

## 🧱 Estrutura do repositório

```text
extensao-qa/
├── README.md
└── SIFIT/
    ├── Analise de requisitos.md
    ├── Plano de testes.md
    ├── Relatorio-de-Bugs.md
    ├── Relatorio dos testes.md
    ├── Cenario_Teste/
    │   ├── CT-RF01_Esqueci-senha.md
    │   ├── CT-RF02_ERRO.md
    │   ├── CT-RF03_FILTRO_TelaClientes.md
    │   └── CT-RF04_loginComSucesso.md
    └── Evidencias/
        ├── CT-RF02_ERRO/
        ├── CT-RF03_Filtros_Clientes/
        └── CT-RF04_loginComSucesso/
```

### 📚 Documentos

| Etapa | Documento | Conteúdo |
| --- | --- | --- |
| 1 | [Análise de requisitos](SIFIT/Analise%20de%20requisitos.md) | RF01 a RF04, critérios de aceitação e rastreabilidade. |
| 2 | [Plano de testes](SIFIT/Plano%20de%20testes.md) | Escopo, técnicas, ambientes, critérios e procedimentos de reteste. |
| 3 | [Cenários de teste](SIFIT/Cenario_Teste/) | Pré-condições, passos em BDD e resultados por funcionalidade. |
| 4 | [Relatório de bugs](SIFIT/Relatorio-de-Bugs.md) | Reprodução, impacto, comportamento esperado e obtido, evidências e encaminhamento. |
| 5 | [Relatório dos testes](SIFIT/Relatorio%20dos%20testes.md) | Resumo dos resultados, cobertura e pendências. |

---

## 📋 Funcionalidades documentadas

| Requisito | Caso de teste | Funcionalidade | Defeito |
| --- | --- | --- | --- |
| RF01 | [CT-RF01](SIFIT/Cenario_Teste/CT-RF01_Esqueci-senha.md) | Início da recuperação de senha. | [BUG-001](SIFIT/Relatorio-de-Bugs.md#bug-001--link-esqueci-minha-senha-não-executa-nenhuma-ação) |
| RF02 | [CT-RF02_ERRO](SIFIT/Cenario_Teste/CT-RF02_ERRO.md) | Dados, campos e layout do perfil autenticado. | [BUG-002](SIFIT/Relatorio-de-Bugs.md#bug-002--perfil-com-dados-fictícios-campos-ausentes-e-layout-desconfigurado) |
| RF03 | [CT-RF03](SIFIT/Cenario_Teste/CT-RF03_FILTRO_TelaClientes.md) | Pesquisa de clientes com filtros combinados. | [BUG-003](SIFIT/Relatorio-de-Bugs.md#bug-003--filtros-combinados-da-página-clientes-não-restringem-a-listagem) |
| RF04 | [CT-RF04_loginComSucesso](SIFIT/Cenario_Teste/CT-RF04_loginComSucesso.md) | Login com credenciais válidas e acesso ao dashboard. | Nenhum identificado no fluxo avaliado; aprovado conforme o Jam. |

## 🔬 Metodologia

- **Técnicas:** testes funcionais, análise exploratória e conferência de evidências de interface, DOM, rede e console, conforme a disponibilidade de cada caso.
- **Formatos:** cenários em BDD (Dado / Quando / Então), tabelas, critérios de aceitação e matriz de reteste.
- **Processo:** análise de requisitos → planejamento → execução registrada → documentação de defeitos → relatório → reteste após a correção.

As variações da matriz de reteste são atividades planejadas e permanecem pendentes de execução.

## 🛠️ Ferramentas

| Ferramenta | Uso na documentação |
| --- | --- |
| Jam | Referência de gravações, ações e registros disponíveis por caso. |
| DevTools | Inspeção de interface, DOM, requisições e console. |
| Capturas de tela | Registro visual dos problemas relatados. |
| Google Drive | Referência do vídeo complementar de recuperação de senha. |
| Markdown e GitHub | Organização e versionamento dos documentos. |

---

## 🔐 Ambientes e evidências

| Caso | Ambiente registrado | Evidências |
| --- | --- | --- |
| CT-RF01 | `https://sifitalfa.centrion.com.br/login`, sem autenticação. | Jam e vídeo complementar no Drive, vinculados no cenário. |
| CT-RF02_ERRO | `https://sifit.centrion.com.br/profile`, com autenticação; Info do Jam apresenta `/configuracoes`. | [Captura e recorte do DOM](SIFIT/Evidencias/CT-RF02_ERRO/), além do Jam vinculado no cenário. |
| CT-RF03 | Página Clientes; URL do frontend não confirmada. | [Capturas, origem e limites do relato](SIFIT/Evidencias/CT-RF03_Filtros_Clientes/README.md), com referência ao Jam. |
| CT-RF04_loginComSucesso | `https://sifit.centrion.com.br/login` → `/dashboard`; Chrome 157.0.8103.51 / Windows 11. | [Resumo das evidências](SIFIT/Evidencias/CT-RF04_loginComSucesso/README.md) e [Jam — Login com sucesso](https://jam.dev/c/5e4a28be-4e80-43d3-9587-1b113723cc38). |

Os ambientes e as condições de execução devem ser conferidos por caso. As limitações de cada fonte estão registradas nos cenários e nos relatórios.

## 📊 Status do projeto

🚧 **Documentação em andamento — correções e retestes pendentes.**

| Casos documentados | Aprovados | Reprovados¹ | Bugs abertos | Retestes pendentes |
| :---: | :---: | :---: | :---: | :---: |
| 4 | 1 | 3 | 3 | 3 |

¹ CT-RF01 e CT-RF02_ERRO estão reprovados conforme as evidências analisadas. CT-RF03 está reprovado conforme o relato fornecido, apoiado por capturas; o conteúdo do Jam desse caso não foi consultado diretamente na revisão registrada.

**Atualização documental:** 13/11/2026. Incluído CT-RF04_loginComSucesso, aprovado conforme ações, rede e quadros do Jam gravado em 13/11/2026. Resultados anteriores preservados, sem nova execução da aplicação nesta atualização.

## 📎 Referência de organização

A apresentação foi adaptada do [repositório de referência de testes manuais](https://github.com/Adnyslougansilva/extensao-qa), com conteúdo e rastreabilidade próprios do SIFIT.
