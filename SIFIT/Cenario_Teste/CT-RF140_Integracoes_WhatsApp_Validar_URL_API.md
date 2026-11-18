# 🧪 Cenário 140: Validar uma URL da API sem formato de endereço

**Caso de teste:** CT-RF140

**Módulo:** Configurações / Integrações / WhatsApp

**Status:** A validar — regra ou contexto pendente.

**Gravação:** 16/11/2026, 23:39:06 BRT. **Revisão documental:** 17/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Verificar se a integração recusa uma URL em formato inválido e orienta a correção do campo. |
| Requisito | [RF140](../Analise%20de%20requisitos.md#rf140) — referência de QA. |
| Tipo / prioridade | Funcional manual / validação · Média, proposta para triagem. |
| Defeito | Sem defeito confirmado |
| Encaminhamento | Isolar a URL no reteste, mantendo a instância e a chave preenchidas, e confirmar o formato aceito com produto. |
| Fonte | [Jam 2 — Validação da URL da API](https://jam.dev/c/0d7c7274-c798-4e26-91a3-f8162b7ce932) e [evidências locais](../Evidencias/CT-RF140_Integracoes_WhatsApp_Validar_URL_API/README.md). |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/configuracoes |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.79 / Windows 10 (x86), conforme os metadados do Jam. |
| Tela / arquivo de vídeo | Tela 1536 × 799 informada no Jam. Vídeo em 1918 × 998. |
| Duração | 22,92 s |
| Localização | Brasil. |
| Versão / zoom / classificação do ambiente | A confirmar antes de nova execução. |
| Dados | Texto sem formato de URL no campo URL da API e Nome da Instância vazio durante a tentativa. |

## Pré-condições

- Sessão autenticada com acesso à integração de WhatsApp. No reteste, preencher os demais campos com dados autorizados.
- Identificar a versão e registrar os valores iniciais e as permissões no próximo teste.

## Cenário BDD

```gherkin
Cenário: Validar uma URL da API sem formato de endereço
  Dado que os demais campos da integração estão válidos e a URL da API tem formato inválido
  Quando o usuário aciona Salvar Configuração
  Então o formulário deve recusar a URL inválida e indicar o campo a corrigir
  E a configuração anterior deve permanecer armazenada
```

## Passos para execução ou reteste

1. Abrir o formulário com uma configuração de teste válida e anotar seu estado.
2. Alterar apenas a URL da API para texto sem formato de endereço.
3. Acionar Salvar Configuração e observar a mensagem e as requisições.
4. Reabrir a aba para verificar a persistência. Repetir com uma URL válida como controle.

Este procedimento orienta a próxima execução. O resultado abaixo se limita ao trecho registrado no Jam.

## Resultado esperado

Com os demais campos válidos, o sistema rejeita a URL fora do formato aceito, sinaliza o campo e mantém a configuração anterior.

## Resultado obtido na gravação

Foi inserido texto sem formato de URL e acionado Salvar Configuração. O Nome da Instância estava vazio. A captura não registrou POST de configuração ou uma mensagem específica da URL. Após recarregar e voltar a Integrações, o texto digitado já não aparecia no campo.

| Tempo | Registro |
| --- | --- |
| 0:00–0:07 | O usuário seleciona o campo URL da API e insere texto sem formato de endereço. |
| 0:10,57 | Aciona Salvar Configuração com o Nome da Instância vazio. |
| 0:13–0:16 | Recarrega a página, seleciona Integrações e a configuração é lida novamente. |

**Rede:**

- 0:10,57  Clique em Salvar Configuração. A captura não apresenta POST para `/api/empresa/whatsapp/1`.
- 0:15,97  GET `/api/empresa/whatsapp/1` (HTTP 200) ao reabrir a aba.

**Conclusão:** A validar — regra ou contexto pendente. O Nome da Instância vazio impede atribuir a ausência de POST à regra de URL. A gravação não demonstra qual validação bloqueou a tentativa.

## Critérios de aceitação para nova execução

1. A tentativa com apenas a URL inválida é recusada.
2. A interface identifica a URL como o campo a corrigir.
3. A leitura posterior preserva a configuração anterior.

## Próxima ação e verificações complementares

Isolar a URL no reteste, mantendo a instância e a chave preenchidas, e confirmar o formato aceito com produto.

## Evidências e limites

- [Jam 2 — Validação da URL da API](https://jam.dev/c/0d7c7274-c798-4e26-91a3-f8162b7ce932).
- [Arquivos, origem e limites](../Evidencias/CT-RF140_Integracoes_WhatsApp_Validar_URL_API/README.md).
- [Formulário após a tentativa de salvar, com valores de integração ocultos](../Evidencias/CT-RF140_Integracoes_WhatsApp_Validar_URL_API/tentativa_de_salvar_url_00-11.jpg), [Status visível após reabrir a aba Integrações](../Evidencias/CT-RF140_Integracoes_WhatsApp_Validar_URL_API/status_ao_reabrir_00-16.jpg).
- [Linha do tempo](../Evidencias/CT-RF140_Integracoes_WhatsApp_Validar_URL_API/linha_do_tempo.txt).

A revisão documental se baseia nos quadros do vídeo e nos eventos capturados pelo Jam. As verificações complementares ficam para uma nova rodada de testes.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf140) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
