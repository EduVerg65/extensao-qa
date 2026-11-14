# 🧪 Cenário 06: Login com usuário inexistente

**Caso de teste:** CT-RF06

**Módulo:** Autenticação / Login

**Status:** Aprovado conforme a gravação.

**Gravação:** 14/11/2026, 00:23:57 BRT. **Revisão documental:** 14/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Recusar autenticação com usuário inexistente. |
| Requisito | [RF06](../Analise%20de%20requisitos.md#rf06) |
| Tipo / prioridade | Funcional manual, análise de evidências / Alta, proposta para triagem. |
| Defeito | Nenhum no fluxo avaliado |
| Encaminhamento | Sem reteste corretivo pendente; manter como regressão. |
| Fonte | [Jam — Teste Usuário que não existe](https://jam.dev/c/b184e875-2cb1-4a01-b4dd-bc85b3741ff6) |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/login |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.51 / Windows 11 (x86). |
| Tela / arquivo de vídeo | 1920 × 957 informados no Jam; original 1918 × 956 pixels. |
| Duração | 12,39 s |
| Versão / zoom / classificação do ambiente | Não confirmados; registrar antes de nova execução. |
| Dados | Usar dados de teste conhecidos conforme as pré-condições abaixo; valores da gravação são referência histórica, sem copiar credenciais. |

## Pré-condições

- Iniciar sem sessão autenticada.
- Preparar um identificador cuja inexistência seja conhecida na base de teste.
- Antes de uma nova execução, identificar versão, permissões e dados de referência e preparar a captura de interface e rede.

## Cenário BDD

```gherkin
Cenário: Recusar autenticação com usuário inexistente
  Dado que o usuário está na página de login sem sessão
  E informa um identificador inexistente na base de teste
  Quando preencher a senha e clicar em "Entrar"
  Então o sistema deve recusar a autenticação
  E permanecer no login com mensagem genérica de credenciais inválidas
```

## Passos para execução ou reteste

1. Preencher Login com identificador inexistente na base de referência.
2. Informar uma senha de teste, sem expor seu valor.
3. Clicar em Entrar e verificar que não há acesso à área autenticada.

Este procedimento orienta a próxima execução. A evidência atual cobre o trecho gravado e os limites descritos abaixo; passos complementares, como conferir downloads ou recarregar a sessão, não recebem resultado de execução nesta revisão.

## Resultado esperado

Recusar o acesso para credenciais inválidas.

## Resultado obtido na gravação

A gravação termina na página de login com a mensagem genérica de credenciais inválidas, sem acesso ao painel.

**Momentos e registros:** 0:08–0:12: POST /api/login retorna HTTP 200 e a interface permanece no login.

**Conclusão:** Aprovado conforme a gravação. A aprovação se limita ao cenário visível; não significa validação de todas as variações do fluxo.

## Critérios de aceitação para nova execução

1. Identificador inexistente não permite abrir a área autenticada.
2. A tentativa recebe retorno compreensível sem revelar se a conta existe.
3. Em nova execução, a inexistência do identificador é conferida na base de referência.

## Próxima ação e verificações complementares

Repetir com identificador de inexistência comprovada; a classificação atual refere-se à recusa visível do cenário declarado pelo autor.

Nenhum defeito adicional foi criado para este cenário.

## Evidências e limites

- [Jam original — Teste Usuário que não existe](https://jam.dev/c/b184e875-2cb1-4a01-b4dd-bc85b3741ff6).
- [Vídeo original](../Evidencias/CT-RF06_Login_UsuarioInexistente/video.webm).
- [Resumo, origem e integridade](../Evidencias/CT-RF06_Login_UsuarioInexistente/README.md).
- [Cronologia do Jam](../Evidencias/CT-RF06_Login_UsuarioInexistente/linha_do_tempo.txt).

A inexistência do usuário é o cenário declarado no título; não foi conferida no banco. A mensagem já está visível no início do vídeo e permanece após a nova tentativa.

Análise documental das gravações já consultadas em 14/11/2026 (metadados, cronologia e quadros distribuídos pelo vídeo). Esta inclusão não executa novamente o sistema, não corrige a aplicação e não constitui reteste. Versão da aplicação, zoom e classificação do ambiente não foram confirmados.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
