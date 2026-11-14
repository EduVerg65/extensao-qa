# 🧪 Cenário 05: Login com senha incorreta

**Caso de teste:** CT-RF05

**Módulo:** Autenticação / Login

**Status:** Aprovado conforme a gravação.

**Gravação:** 14/11/2026, 00:23:20 BRT. **Revisão documental:** 14/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Recusar autenticação com senha incorreta. |
| Requisito | [RF05](../Analise%20de%20requisitos.md#rf05) |
| Tipo / prioridade | Funcional manual, análise de evidências / Alta, proposta para triagem. |
| Defeito | Nenhum no fluxo avaliado |
| Encaminhamento | Sem reteste corretivo pendente; manter como regressão. |
| Fonte | [Jam — Teste senha incorreta](https://jam.dev/c/75f16436-7201-4de0-b191-1c4d0d63bfe8) |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/login |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.51 / Windows 11 (x86). |
| Tela / arquivo de vídeo | 1920 × 957 informados no Jam; original 1918 × 956 pixels. |
| Duração | 12,90 s |
| Versão / zoom / classificação do ambiente | Não confirmados; registrar antes de nova execução. |
| Dados | Usar dados de teste conhecidos conforme as pré-condições abaixo; valores da gravação são referência histórica, sem copiar credenciais. |

## Pré-condições

- Iniciar sem sessão autenticada na página de login.
- Dispor de conta de teste existente e senha propositalmente incorreta.
- Antes de uma nova execução, identificar versão, permissões e dados de referência e preparar a captura de interface e rede.

## Cenário BDD

```gherkin
Cenário: Recusar autenticação com senha incorreta
  Dado que o usuário está sem sessão na página de login
  E informa uma conta existente com senha incorreta
  Quando clicar em "Entrar"
  Então o sistema deve recusar a autenticação
  E manter o usuário no login com mensagem de credenciais inválidas
```

## Passos para execução ou reteste

1. Preencher Login com a conta de teste existente.
2. Informar uma senha incorreta, mantendo o valor mascarado.
3. Clicar em Entrar e observar a mensagem, a URL e a ausência de acesso ao painel.

Este procedimento orienta a próxima execução. A evidência atual cobre o trecho gravado e os limites descritos abaixo; passos complementares, como conferir downloads ou recarregar a sessão, não recebem resultado de execução nesta revisão.

## Resultado esperado

Recusar a autenticação e informar a falha sem abrir a área autenticada.

## Resultado obtido na gravação

Após o envio, a tela permanece no login e apresenta “O nome de usuário e senha não correspondem.”

**Momentos e registros:** 0:05–0:12: envio e mensagem de recusa. A linha do tempo registra POST /api/login com HTTP 200.

**Conclusão:** Aprovado conforme a gravação. A aprovação se limita ao cenário visível; não significa validação de todas as variações do fluxo.

## Critérios de aceitação para nova execução

1. Senha incorreta não permite acesso ao dashboard.
2. A interface apresenta mensagem compreensível de credenciais inválidas.
3. A conclusão considera mensagem e permanência no login, além do status HTTP.

## Próxima ação e verificações complementares

Usar como regressão de autenticação negativa; preparar conta conhecida e repetir após alterações no login.

Nenhum defeito adicional foi criado para este cenário.

## Evidências e limites

- [Jam original — Teste senha incorreta](https://jam.dev/c/75f16436-7201-4de0-b191-1c4d0d63bfe8).
- [Vídeo original](../Evidencias/CT-RF05_Login_SenhaIncorreta/video.webm).
- [Resumo, origem e integridade](../Evidencias/CT-RF05_Login_SenhaIncorreta/README.md).
- [Cronologia do Jam](../Evidencias/CT-RF05_Login_SenhaIncorreta/linha_do_tempo.txt).

HTTP 200 é o status da resposta da API; a recusa é demonstrada pela interface. O vídeo não valida bloqueio por tentativas ou outras regras de segurança.

Análise documental das gravações já consultadas em 14/11/2026 (metadados, cronologia e quadros distribuídos pelo vídeo). Esta inclusão não executa novamente o sistema, não corrige a aplicação e não constitui reteste. Versão da aplicação, zoom e classificação do ambiente não foram confirmados.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
