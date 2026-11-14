# 🧪 Testes Manuais — SIFIT

Repositório de documentação de QA manual do **SIFIT**, sistema de gestão de academias. Reúne requisitos, plano, cenários BDD, resultados, defeitos e evidências com links do Jam.

**Atualização documental:** 14/11/2026. Incluídos CT-RF05–CT-RF20, seguindo a ordem dos 16 links fornecidos. Os quatro cenários e resultados anteriores foram preservados.

## 📊 Situação consolidada

| Cenários documentados | Aprovados | Reprovados | A validar | Bugs abertos | Casos com reteste corretivo pendente |
| :---: | :---: | :---: | :---: | :---: | :---: |
| 20 | 6 | 10 | 4 | 9 | 10 |

As classificações se baseiam nas fontes indicadas em cada cenário. CT-RF03 mantém a reprovação conforme o relato, com os limites da revisão original. CT-RF09 e CT-RF10 compartilham BUG-005; por isso dez casos reprovados correspondem a nove defeitos. Os quatro pontos a validar não entram na contagem de bugs.

## 📚 Documentos do projeto

| Documento | Conteúdo |
| --- | --- |
| [Análise de requisitos](SIFIT/Analise%20de%20requisitos.md) | RF01–RF20, critérios de aceitação, dúvidas de regra e rastreabilidade. |
| [Plano de testes](SIFIT/Plano%20de%20testes.md) | Escopo, ambientes, preparação, critérios, regressão e retestes. |
| [Índice dos cenários](SIFIT/Cenario_Teste/README.md) | 20 cenários com pré-condições, BDD, passos, esperado, obtido e encaminhamento. |
| [Relatório de bugs](SIFIT/Relatorio-de-Bugs.md) | BUG-001–BUG-009: reprodução, impacto, evidências, severidade/prioridade propostas e reteste. |
| [Relatório dos testes](SIFIT/Relatorio%20dos%20testes.md) | Resultados consolidados, cobertura, limites e pendências. |
| [Índice das evidências](SIFIT/Evidencias/README.md) | Jam por cenário e arquivos locais dos novos casos. |

## 🧱 Estrutura

```text
extensao-qa/
├── README.md
└── SIFIT/
    ├── Analise de requisitos.md
    ├── Plano de testes.md
    ├── Relatorio-de-Bugs.md
    ├── Relatorio dos testes.md
    ├── Cenario_Teste/
    │   ├── README.md
    │   ├── CT-RF01_Esqueci-senha.md
    │   ├── ... CT-RF02 a CT-RF19
    │   └── CT-RF20_Criacao_Categoria.md
    └── Evidencias/
        ├── README.md
        ├── catalogo.json
        ├── manifesto_sha256.json
        ├── CT-RF02_ERRO/
        ├── CT-RF03_Filtros_Clientes/
        ├── CT-RF04_loginComSucesso/
        ├── CT-RF05_Login_SenhaIncorreta/
        ├── ... CT-RF06 a CT-RF19
        └── CT-RF20_Criacao_Categoria/
```

## 📋 Cenários e resultados

| Caso | Funcionalidade | Resultado nas evidências | Defeito | Fonte |
| --- | --- | --- | --- | --- |
| [CT-RF01](SIFIT/Cenario_Teste/CT-RF01_Esqueci-senha.md) | Início da recuperação de senha | Reprovado conforme as evidências | [BUG-001](SIFIT/Relatorio-de-Bugs.md#bug-001--link-esqueci-minha-senha-não-executa-nenhuma-ação) | [Jam](https://jam.dev/c/0273b203-b999-493d-9919-2d143bc13301) |
| [CT-RF02_ERRO](SIFIT/Cenario_Teste/CT-RF02_ERRO.md) | Dados, campos e layout do perfil | Reprovado conforme as evidências | [BUG-002](SIFIT/Relatorio-de-Bugs.md#bug-002--perfil-com-dados-fictícios-campos-ausentes-e-layout-desconfigurado) | [Jam](https://jam.dev/c/c61241d5-bff5-4a0a-9684-991318f9b51c) |
| [CT-RF03](SIFIT/Cenario_Teste/CT-RF03_FILTRO_TelaClientes.md) | Filtros combinados de Clientes | Reprovado conforme o relato | [BUG-003](SIFIT/Relatorio-de-Bugs.md#bug-003--filtros-combinados-da-página-clientes-não-restringem-a-listagem) | [Jam](https://jam.dev/c/657627ec-e7e2-455d-a505-9b2a26f44bf1) |
| [CT-RF04_loginComSucesso](SIFIT/Cenario_Teste/CT-RF04_loginComSucesso.md) | Login com credenciais válidas | Aprovado conforme a gravação | — | [Jam](https://jam.dev/c/5e4a28be-4e80-43d3-9587-1b113723cc38) |
| [CT-RF05](SIFIT/Cenario_Teste/CT-RF05_Login_SenhaIncorreta.md) | Login com senha incorreta | Aprovado conforme a gravação | — | [Jam](https://jam.dev/c/75f16436-7201-4de0-b191-1c4d0d63bfe8) |
| [CT-RF06](SIFIT/Cenario_Teste/CT-RF06_Login_UsuarioInexistente.md) | Login com usuário inexistente | Aprovado conforme a gravação | — | [Jam](https://jam.dev/c/b184e875-2cb1-4a01-b4dd-bc85b3741ff6) |
| [CT-RF07](SIFIT/Cenario_Teste/CT-RF07_Exportacao_Financeiro.md) | Exportação financeira sem retorno visível | Reprovado nas evidências | [BUG-004](SIFIT/Relatorio-de-Bugs.md#bug-004) | [Jam](https://jam.dev/c/1084cb18-cb3d-4b85-9c2f-ee431b59a06b) |
| [CT-RF08](SIFIT/Cenario_Teste/CT-RF08_Calculo_Cobranca.md) | Total atualizado da cobrança e valor da mensagem | A validar — regra ou contexto pendente | — | [Jam](https://jam.dev/c/79b712ae-d9e0-4600-862f-fd3a278285ff) |
| [CT-RF09](SIFIT/Cenario_Teste/CT-RF09_Contagem_Mensalidades.md) | Contagem de mensalidades diverge da lista | Reprovado nas evidências | [BUG-005](SIFIT/Relatorio-de-Bugs.md#bug-005) | [Jam](https://jam.dev/c/1874d0b3-5c7c-4f28-85be-91750e20cbe1) |
| [CT-RF10](SIFIT/Cenario_Teste/CT-RF10_Filtro_Mensalidades.md) | Filtro Até 7 dias conta uma mensalidade e mostra lista vazia | Reprovado nas evidências | [BUG-005](SIFIT/Relatorio-de-Bugs.md#bug-005) | [Jam](https://jam.dev/c/3f78cf16-2c3b-48bc-8622-23b829debbec) |
| [CT-RF11](SIFIT/Cenario_Teste/CT-RF11_Metricas_Financeiro.md) | Escopo das métricas financeiras durante a filtragem | A validar — regra ou contexto pendente | — | [Jam](https://jam.dev/c/4491c9e7-7e00-4063-91ce-8683e316df06) |
| [CT-RF12](SIFIT/Cenario_Teste/CT-RF12_Periodo_Dashboard.md) | Período invertido e atualização de indicadores pouco clara | Reprovado nas evidências | [BUG-006](SIFIT/Relatorio-de-Bugs.md#bug-006) | [Jam](https://jam.dev/c/93165ba3-3bfe-4dd5-9379-ab8db2d686ba) |
| [CT-RF13](SIFIT/Cenario_Teste/CT-RF13_Codigos_Personais.md) | Códigos não sequenciais na lista de personais | A validar — regra ou contexto pendente | — | [Jam](https://jam.dev/c/69330ca9-ef19-4ece-918f-31a460628016) |
| [CT-RF14](SIFIT/Cenario_Teste/CT-RF14_Contraste_TemaEscuro.md) | Baixa legibilidade no tema escuro de Box – Turmas | Reprovado nas evidências | [BUG-007](SIFIT/Relatorio-de-Bugs.md#bug-007) | [Jam](https://jam.dev/c/6889db07-bed1-472b-8ec2-00402919cd65) |
| [CT-RF15](SIFIT/Cenario_Teste/CT-RF15_Edicao_Modalidade.md) | Edição de modalidade sem ação de salvar visível | Reprovado nas evidências | [BUG-008](SIFIT/Relatorio-de-Bugs.md#bug-008) | [Jam](https://jam.dev/c/951efaf8-bf32-44b0-b640-a2935a6b554a) |
| [CT-RF16](SIFIT/Cenario_Teste/CT-RF16_Exclusao_Modalidade.md) | Ação de lixeira inativa modalidades e mantém registros na lista | A validar — regra ou contexto pendente | — | [Jam](https://jam.dev/c/0f55f76a-cd31-4cee-93da-23c13b1ba637) |
| [CT-RF17](SIFIT/Cenario_Teste/CT-RF17_Filtros_Categorias.md) | Filtros de categorias por código e nome | Aprovado conforme a gravação | — | [Jam](https://jam.dev/c/5e75e423-9c7e-43d7-aade-9b1a32c5e559) |
| [CT-RF18](SIFIT/Cenario_Teste/CT-RF18_Atualizacao_Categoria.md) | Atualização de categoria | Aprovado conforme a gravação | — | [Jam](https://jam.dev/c/67664a98-2a4a-4134-91a9-7ca9b8aa9dbd) |
| [CT-RF19](SIFIT/Cenario_Teste/CT-RF19_Exclusao_Categoria.md) | Exclusão de categoria retorna erro HTTP 500 | Reprovado nas evidências | [BUG-009](SIFIT/Relatorio-de-Bugs.md#bug-009) | [Jam](https://jam.dev/c/c5c78b3b-2865-4226-836f-bcb0a8fc612f) |
| [CT-RF20](SIFIT/Cenario_Teste/CT-RF20_Criacao_Categoria.md) | Criação de categoria | Aprovado conforme a gravação | — | [Jam](https://jam.dev/c/b48ab94e-517d-48d6-8e46-70b18c033b8b) |

## 🔬 Como este projeto funciona

1. Registrar o comportamento esperado e os critérios na análise de requisitos.
2. Preparar ambiente e dados conforme o plano de testes.
3. Executar e gravar o cenário; documentar o resultado obtido em separado do BDD esperado.
4. Vincular cenário, requisito, Jam, arquivos e defeito. Agrupar manifestações do mesmo defeito, preservando os cenários de reteste.
5. Após correção, repetir os cenários em uma versão identificada e atualizar caso, relatórios e defeito com nova evidência.

Esta atualização organiza gravações existentes e **não é uma nova execução ou reteste da aplicação**. Os critérios são referências de QA; as decisões de produto pendentes estão explícitas. As variações propostas ainda não executadas não entram nas contagens de testes realizados. Não há suíte automatizada ou código da aplicação neste repositório.

## 🎥 Consultar os vídeos e a origem

Cada novo cenário contém o link direto do Jam. Em sua pasta de evidências há `video.webm` original, `capa.png`, `resumo.txt`, `linha_do_tempo.txt`, `origem.url`, `metadados.json` e um README com o contexto. No GitHub, use o Jam para consultar a gravação ou baixe o WebM e abra em navegador compatível. A capa fornecida pelo Jam não substitui a demonstração do resultado no vídeo.

Foram copiados **16 vídeos, totalizando 39.490.598 bytes (39,49 MB)**; cada arquivo tem menos de 4 MB. Os hashes das cópias e do conjunto documental estão no [manifesto de integridade](SIFIT/Evidencias/manifesto_sha256.json). A numeração CT-RF05–CT-RF20 segue a ordem definida pelo solicitante; não há correspondência inferida com códigos da aplicação.

## 🔐 Ambientes e limites

CT-RF01 usa `sifitalfa.centrion.com.br`; CT-RF02 aponta para `/profile`, com divergência de rota na aba Info; o frontend de CT-RF03 permanece não confirmado. CT-RF04 e os 16 novos casos usam `sifit.centrion.com.br`. Os novos vídeos foram gravados em 14/11/2026 com Chrome 157.0.8103.51 / Windows 11. A versão da aplicação e o zoom não foram identificados; conferir antes de nova execução.

As quatro decisões pendentes são: composição da cobrança (CT-RF08), escopo das métricas (CT-RF11), significado dos códigos de personais (CT-RF13) e exclusão lógica de modalidades (CT-RF16). Os vídeos de login negativo têm senha mascarada; os documentos não reproduzem senhas, tokens ou corpos de autenticação.

## 📎 Referência de organização

A apresentação foi adaptada do [repositório de referência de testes manuais](https://github.com/Adnyslougansilva/extensao-qa), com conteúdo e rastreabilidade próprios do SIFIT.
