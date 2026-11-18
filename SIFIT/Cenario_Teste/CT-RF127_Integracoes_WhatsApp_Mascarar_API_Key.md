# 🧪 Cenário 127: Mascarar a API Key no formulário de WhatsApp

**Caso de teste:** CT-RF127

**Módulo:** Configurações / Integrações / WhatsApp

**Status:** Aprovado conforme a gravação.

**Gravação:** 16/11/2026, 23:37:22 BRT. **Revisão documental:** 17/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Manter os caracteres da API Key ocultos durante a edição e ao reabrir a aba Integrações. |
| Requisito | [RF127](../Analise%20de%20requisitos.md#rf127) — referência de QA. |
| Tipo / prioridade | Funcional manual / interface · Média, proposta para triagem. |
| Defeito | Nenhum no fluxo avaliado |
| Encaminhamento | Usar como regressão de interface com uma chave de teste e conferir o mascaramento também pelo teclado. |
| Fonte | [Jam 1 — Mascaramento da API Key](https://jam.dev/c/ef0b67d5-1eea-49b7-84ea-bb306143df4a) e [evidências locais](../Evidencias/CT-RF139_Integracoes_WhatsApp_Mascarar_API_Key/README.md). |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/configuracoes |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.79 / Windows 10 (x86), conforme os metadados do Jam. |
| Tela / arquivo de vídeo | Tela 1536 × 799 informada no Jam. Vídeo em 1918 × 998. |
| Duração | 24,98 s |
| Localização | Brasil. |
| Versão / zoom / classificação do ambiente | A confirmar antes de nova execução. |
| Dados | Campo API Key já preenchido no início. Foram feitas edições locais sem acionar Salvar Configuração. |

## Pré-condições

- Sessão autenticada com acesso a Configurações → Integrações → WhatsApp e uma configuração de teste existente.
- Identificar a versão e registrar os valores iniciais e as permissões no próximo teste.

## Cenário BDD

```gherkin
Cenário: Mascarar a API Key no formulário de WhatsApp
  Dado que o formulário de WhatsApp está aberto e possui uma chave cadastrada
  Quando o usuário edita a API Key e reabre a aba Integrações
  Então o campo deve mascarar os caracteres durante a digitação e após a reabertura
  E a edição sem salvar deve permanecer fora da configuração armazenada
```

## Passos para execução ou reteste

1. Abrir o formulário de WhatsApp com uma chave de teste já cadastrada.
2. Editar o campo API Key e conferir o mascaramento com e sem foco.
3. Recarregar sem salvar e reabrir a aba Integrações.
4. Conferir novamente o mascaramento e os métodos das requisições.

Este procedimento orienta a próxima execução. O resultado abaixo se limita ao trecho registrado no Jam.

## Resultado esperado

A API Key aparece mascarada antes e durante a edição. Ao reabrir a aba, o campo continua mascarado e a digitação sem salvar não resulta em uma gravação.

## Resultado obtido na gravação

A máscara permaneceu ao editar a API Key e após recarregar a página e voltar à aba Integrações. Os eventos de digitação identificaram o controle como `input` do tipo `password`. Houve reconsulta da configuração, sem POST de salvamento no trecho.

| Tempo | Registro |
| --- | --- |
| 0:02–0:10 | O usuário edita a API Key, com os caracteres mascarados na tela. |
| 0:13–0:17 | Após recarregar a página, o usuário seleciona Integrações e a configuração é consultada novamente. |
| 0:17–0:23 | O campo API Key continua mascarado durante as novas interações. |

**Rede:**

- 0:16,93  GET `/api/empresa/whatsapp/1` (HTTP 200), ao retornar a Integrações.
- A captura não registra POST de salvamento da configuração durante o trecho.

**Conclusão:** Aprovado conforme a gravação. A aprovação cobre o mascaramento visual e a ausência de envio ao editar sem salvar. A gravação não verifica proteção em trânsito ou em armazenamento.

## Critérios de aceitação para nova execução

1. O valor aparece mascarado no formulário e durante a digitação.
2. Reabrir a aba mantém o campo mascarado.
3. A edição sem salvar não dispara o POST de configuração.

## Próxima ação e verificações complementares

Usar como regressão de interface com uma chave de teste e conferir o mascaramento também pelo teclado.

## Evidências e limites

- [Jam 1 — Mascaramento da API Key](https://jam.dev/c/ef0b67d5-1eea-49b7-84ea-bb306143df4a).
- [Arquivos, origem e limites](../Evidencias/CT-RF139_Integracoes_WhatsApp_Mascarar_API_Key/README.md).
- [Campo API Key durante a edição, com caracteres mascarados](../Evidencias/CT-RF139_Integracoes_WhatsApp_Mascarar_API_Key/api_key_durante_edicao_00-07.jpg), [Campo API Key ainda mascarado após reabrir a aba](../Evidencias/CT-RF139_Integracoes_WhatsApp_Mascarar_API_Key/api_key_ao_reabrir_00-21.jpg).
- [Linha do tempo](../Evidencias/CT-RF139_Integracoes_WhatsApp_Mascarar_API_Key/linha_do_tempo.txt).

A revisão documental se baseia nos quadros do vídeo e nos eventos capturados pelo Jam. As verificações complementares ficam para uma nova rodada de testes.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf127) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
