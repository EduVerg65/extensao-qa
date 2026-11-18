# 🧪 Cenário 124: Navegar pelas abas de Configurações com a senha da biometria protegida

**Caso de teste:** CT-RF124

**Módulo:** Configurações / Navegação e Biometria

**Status:** Reprovado nas evidências.

**Gravação:** 16/11/2026, 21:57:29 BRT. **Revisão documental:** 17/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Abrir as abas de Configurações e manter o valor da senha de integração de biometria mascarado por padrão. |
| Requisito | [RF124](../Analise%20de%20requisitos.md#rf124) — referência de QA. |
| Tipo / prioridade | Funcional manual / navegação e proteção de credencial · Alta, proposta para triagem. |
| Defeito | [BUG-046](../Relatorio-de-Bugs.md#bug-046), em triagem |
| Encaminhamento | Corrigir o mascaramento por padrão e retestar com credenciais fictícias, incluindo a troca de abas e a recarga. |
| Fonte | Jam — PED-15 (gravação restrita por conter dados de integração) e [evidências locais](../Evidencias/CT-RF124_Configuracoes_Abas_Biometria_Senha/README.md). |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/configuracoes |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.79 / Windows 10 (x86), conforme os metadados do Jam. |
| Tela / arquivo de vídeo | Tela 1536 × 799 informada no Jam. Vídeo em 1918 × 998. |
| Duração | 25,22 s |
| Localização | Brasil. |
| Versão / zoom / classificação do ambiente | A confirmar antes de nova execução. |
| Dados | Abas Home, Biometria, Avaliação, Aniversário, Pagamento, Integrações e Design. |

## Pré-condições

- Sessão autenticada com acesso às Configurações. Ambiente de teste com integração de biometria configurada com credencial fictícia.
- Identificar a versão e registrar os valores iniciais e as permissões no próximo teste.

## Cenário BDD

```gherkin
Cenário: Navegar pelas abas de Configurações com a senha da biometria protegida
  Dado que Configurações tem as abas habilitadas e uma integração de biometria configurada
  Quando o usuário abrir Biometria e navegar pelas demais abas
  Então cada aba deve carregar o painel correspondente
  E a senha de integração deve permanecer mascarada na abertura padrão de Biometria
```

## Passos para execução ou reteste

1. Abrir Configurações e registrar a aba Home.
2. Abrir Biometria e conferir o painel e o mascaramento do campo Senha com dados fictícios.
3. Visitar Avaliação, Aniversário, Pagamento, Integrações e Design.
4. Voltar a Home e conferir se o painel esperado está ativo.

Este procedimento orienta a próxima execução. O resultado abaixo se limita ao trecho registrado no Jam.

## Resultado esperado

Todas as abas carregam o painel selecionado. O valor da senha configurada vem mascarado ao abrir Biometria.

## Resultado obtido na gravação

As abas percorridas carregaram seus painéis e foi possível retornar a Home. Ao abrir Biometria, o campo Senha exibiu o valor configurado em texto legível, sem ação para revelar a senha.

| Tempo | Registro |
| --- | --- |
| 0:03–0:04 | Abre Biometria. O painel é carregado e mostra a senha sem mascaramento. |
| 0:05–0:13 | Abre Avaliação, Aniversário e Pagamento. Os painéis correspondentes aparecem. |
| 0:15–0:20 | Abre Integrações e depois Design. |
| 0:23 | Volta a Home. |

**Rede:**

- 0:15,55  A abertura de Integrações gerou OPTIONS (HTTP 204) e a consulta do estado da integração retornou HTTP 200.
- O defeito de exibição foi observado na interface. A revisão não reproduz dados de integração.

**Conclusão:** Reprovado nas evidências. O defeito foi observado na interface de uma sessão autenticada. O alcance por perfil, a exposição em respostas de API e a validade do valor exibido não foram testados. As evidências versionadas mostram apenas os cabeçalhos das abas.

## Critérios de aceitação para nova execução

1. Cada aba exibe o painel correspondente e a navegação permite retornar a Home.
2. O campo Senha em Biometria é mascarado por padrão ao abrir a aba.
3. Voltar a Biometria ou recarregar a página mantém a proteção visual.

## Próxima ação e verificações complementares

Corrigir o mascaramento por padrão e retestar com credenciais fictícias, incluindo a troca de abas e a recarga.

## Evidências e limites

- Jam — PED-15 (gravação restrita por conter dados de integração).
- [Arquivos, origem e limites](../Evidencias/CT-RF124_Configuracoes_Abas_Biometria_Senha/README.md).
- [Cabeçalho da aba Biometria, recortado acima dos dados de integração](../Evidencias/CT-RF124_Configuracoes_Abas_Biometria_Senha/aba_biometria_00-04.jpg), [Cabeçalho da aba Integrações, recortado acima dos dados de conexão](../Evidencias/CT-RF124_Configuracoes_Abas_Biometria_Senha/aba_integracoes_00-17.jpg).
- [Linha do tempo](../Evidencias/CT-RF124_Configuracoes_Abas_Biometria_Senha/linha_do_tempo.txt).

A revisão documental se baseia nos quadros do vídeo e nos eventos capturados pelo Jam. As verificações complementares ficam para uma nova rodada de testes.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf124) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
