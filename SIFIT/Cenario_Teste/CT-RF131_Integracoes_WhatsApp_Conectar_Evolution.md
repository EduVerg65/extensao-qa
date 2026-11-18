# 🧪 Cenário 131: Tratar falha ao conectar WhatsApp via Evolution API

**Caso de teste:** CT-RF131

**Módulo:** Configurações / Integrações / WhatsApp

**Status:** Reprovado nas evidências.

**Gravação:** 16/11/2026, 23:44:10 BRT. **Revisão documental:** 17/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Verificar a consistência entre a resposta da API e a mensagem da tela quando a tentativa de conexão com WhatsApp falha. |
| Requisito | [RF131](../Analise%20de%20requisitos.md#rf131) — referência de QA. |
| Tipo / prioridade | Funcional manual / tratamento de erro · Média, proposta para triagem. |
| Defeito | [BUG-050](../Relatorio-de-Bugs.md#bug-050), em triagem |
| Encaminhamento | Retestar com falha controlada e configuração válida de controle, conferindo o contrato da resposta e o estado final apresentado. |
| Fonte | [Jam 5 — Tentativas de conexão pela Evolution API](https://jam.dev/c/087b5e4f-7d73-4be3-979d-9a39f474b836) e [evidências locais](../Evidencias/CT-RF143_Integracoes_WhatsApp_Conectar_Evolution/README.md). |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/configuracoes |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.79 / Windows 10 (x86), conforme os metadados do Jam. |
| Tela / arquivo de vídeo | Tela 1536 × 799 informada no Jam. Vídeo em 1918 × 998. |
| Duração | 20,55 s |
| Localização | Brasil. |
| Versão / zoom / classificação do ambiente | A confirmar antes de nova execução. |
| Dados | Configuração Evolution API existente. Foram registradas tentativas antes e depois do salvamento da opção Ativo. |

## Pré-condições

- Sessão autenticada na integração de WhatsApp com um provedor de teste. Preparar uma falha controlada com a equipe responsável pelo ambiente.
- Identificar a versão e registrar os valores iniciais e as permissões no próximo teste.

## Cenário BDD

```gherkin
Cenário: Tratar falha ao conectar WhatsApp via Evolution API
  Dado que a integração Evolution API está configurada e o provedor devolve uma falha controlada
  Quando o usuário aciona Conectar WhatsApp
  Então a API e a interface devem indicar a falha de forma consistente
  E a tela deve preservar a indicação de que não há sessão conectada
```

## Passos para execução ou reteste

1. Abrir Configurações → Integrações → WhatsApp com um provedor de teste.
2. Em ambiente autorizado, preparar uma resposta de falha controlada do provedor.
3. Acionar Conectar WhatsApp e registrar a mensagem, a flag de erro e a indicação de conexão.
4. Repetir a tentativa após salvar a opção Ativo e comparar os resultados.

Este procedimento orienta a próxima execução. O resultado abaixo se limita ao trecho registrado no Jam.

## Resultado esperado

Se a tentativa falhar, os indicadores e a mensagem da API representam a falha. A interface informa o erro sem apresentar um QR Code utilizável nem indicar uma conexão estabelecida.

## Resultado obtido na gravação

A tela exibiu “Falha ao conectar na Evolution API” nas duas tentativas e não apresentou QR Code utilizável. Em ambas, o POST retornou HTTP 200 com `verifica_erro: false`, `status: conectando` e `conectado: false`. A resposta continha a mensagem de falha, em desacordo com a flag `verifica_erro`.

| Tempo | Registro |
| --- | --- |
| 0:02–0:07 | Primeira tentativa de conexão. A tela exibe “Falha ao conectar na Evolution API”. |
| 0:07–0:09 | Marca Ativo e salva. A configuração é consultada novamente. |
| 0:12–0:20 | Segunda tentativa de conexão com a opção salva. A mensagem de falha reaparece. |

**Rede:**

- 0:02,48 e 0:12,94  POST `/api/empresa/whatsapp/conectar/1` (HTTP 200). As duas respostas indicaram falha na mensagem com `verifica_erro: false`, `status: conectando` e `conectado: false`.
- 0:08,59–0:08,72  O POST de configuração confirmou o salvamento de Ativo. O GET trouxe `ativo: true` e `status: desconectado` antes da segunda tentativa.

**Conclusão:** Reprovado nas evidências. Os parâmetros do provedor não foram validados. A causa da falha de conexão e o caminho de sucesso exigem testes controlados. O defeito registrado é a divergência da flag de erro.

## Critérios de aceitação para nova execução

1. A tentativa com falha é indicada como falha no contrato da API e na interface.
2. O estado informado permanece coerente com a ausência de sessão conectada.
3. O retorno de falha não disponibiliza QR Code como se a tentativa tivesse sido bem-sucedida.

## Próxima ação e verificações complementares

Retestar com falha controlada e configuração válida de controle, conferindo o contrato da resposta e o estado final apresentado.

## Evidências e limites

- [Jam 5 — Tentativas de conexão pela Evolution API](https://jam.dev/c/087b5e4f-7d73-4be3-979d-9a39f474b836).
- [Arquivos, origem e limites](../Evidencias/CT-RF143_Integracoes_WhatsApp_Conectar_Evolution/README.md).
- [Ação Conectar WhatsApp antes da primeira tentativa](../Evidencias/CT-RF143_Integracoes_WhatsApp_Conectar_Evolution/conectar_whatsapp_00-01.jpg), [Mensagem de falha exibida pela interface](../Evidencias/CT-RF143_Integracoes_WhatsApp_Conectar_Evolution/falha_evolution_00-16.jpg).
- [Linha do tempo](../Evidencias/CT-RF143_Integracoes_WhatsApp_Conectar_Evolution/linha_do_tempo.txt).

A revisão documental se baseia nos quadros do vídeo e nos eventos capturados pelo Jam. As verificações complementares ficam para uma nova rodada de testes.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf131) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
