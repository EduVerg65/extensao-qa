# 🧪 Cenário 142: Persistir a opção Ativo da integração de WhatsApp

**Caso de teste:** CT-RF142

**Módulo:** Configurações / Integrações / WhatsApp

**Status:** Aprovado conforme a gravação.

**Gravação:** 16/11/2026, 23:42:47 BRT. **Revisão documental:** 17/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Confirmar que a configuração grava e reconsulta os estados marcado e desmarcado da opção Ativo. |
| Requisito | [RF142](../Analise%20de%20requisitos.md#rf142) — referência de QA. |
| Tipo / prioridade | Funcional manual / persistência · Média, proposta para triagem. |
| Defeito | Nenhum no fluxo avaliado |
| Encaminhamento | Usar como regressão de persistência e validar o efeito de Ativo sobre automações em um teste dedicado. |
| Fonte | Jam 4 — Persistência da opção Ativo (gravação restrita por conter dados de integração) e [evidências locais](../Evidencias/CT-RF142_Integracoes_WhatsApp_Persistir_Ativo/README.md). |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/configuracoes |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.79 / Windows 10 (x86), conforme os metadados do Jam. |
| Tela / arquivo de vídeo | Tela 1536 × 799 informada no Jam. Vídeo em 1918 × 998. |
| Duração | 29,40 s |
| Localização | Brasil. |
| Versão / zoom / classificação do ambiente | A confirmar antes de nova execução. |
| Dados | Integração desconectada no início. Com a instância preenchida, alterna-se a opção Ativo e restaura-se o estado inicial. |

## Pré-condições

- Sessão autenticada em Integrações → WhatsApp com formulário de teste preenchido.
- Identificar a versão e registrar os valores iniciais e as permissões no próximo teste.

## Cenário BDD

```gherkin
Cenário: Persistir a opção Ativo da integração de WhatsApp
  Dado que a integração de WhatsApp possui configuração preenchida e a opção Ativo está desmarcada
  Quando o usuário marca a opção, salva, desmarca e salva novamente
  Então a nova leitura deve refletir cada estado gravado
  E o estado de conexão deve continuar sendo apresentado separadamente de Ativo
```

## Passos para execução ou reteste

1. Abrir a integração com os campos de teste preenchidos e anotar a opção Ativo.
2. Marcar Ativo, salvar e comparar a resposta do GET com o formulário.
3. Desmarcar Ativo, salvar e comparar novamente o valor consultado.
4. Restaurar o estado inicial se necessário.

Este procedimento orienta a próxima execução. O resultado abaixo se limita ao trecho registrado no Jam.

## Resultado esperado

Marcar e desmarcar Ativo altera o valor persistido da opção e a interface reflete o valor retornado pelo GET após cada salvamento.

## Resultado obtido na gravação

As tentativas iniciais com a instância vazia não geraram POST. Após recarregar o formulário com a instância preenchida, o salvamento de Ativo enviou `ativo: 1` e a reconsulta devolveu `ativo: true`. Ao desmarcar e salvar, o POST enviou `ativo: 0` e a nova leitura trouxe `ativo: false`. A conexão permaneceu desconectada.

| Tempo | Registro |
| --- | --- |
| 0:02–0:11 | Alterna Ativo em tentativas iniciais com o Nome da Instância vazio. |
| 0:13–0:16 | Recarrega e reabre Integrações. A configuração começa com Ativo desmarcado. |
| 0:18–0:22 | Com a instância preenchida, marca Ativo e salva. A reconsulta confirma ativo. |
| 0:24–0:29 | Desmarca, salva e confirma a volta ao estado inicial. |

**Rede:**

- 0:15,70  GET `/api/empresa/whatsapp/1` (HTTP 200), `ativo: false`.
- 0:19,82–0:19,95  POST com `ativo: 1` e `verifica_erro: false`, seguido de GET com `ativo: true` (HTTP 200).
- 0:25,23–0:25,54  POST com `ativo: 0` e `verifica_erro: false`, seguido de GET com `ativo: false` (HTTP 200).

**Conclusão:** Aprovado conforme a gravação. A aprovação é restrita à persistência da opção. A execução de automações e o envio de mensagens não foram exercitados.

## Critérios de aceitação para nova execução

1. A consulta posterior ao salvamento retorna `ativo: true` ao marcar.
2. A consulta posterior ao salvamento retorna `ativo: false` ao desmarcar.
3. O formulário reflete o estado salvo em ambas as consultas.

## Próxima ação e verificações complementares

Usar como regressão de persistência e validar o efeito de Ativo sobre automações em um teste dedicado.

## Evidências e limites

- Jam 4 — Persistência da opção Ativo (gravação restrita por conter dados de integração).
- [Arquivos, origem e limites](../Evidencias/CT-RF142_Integracoes_WhatsApp_Persistir_Ativo/README.md).
- [Opção Ativo marcada após a confirmação pela API](../Evidencias/CT-RF142_Integracoes_WhatsApp_Persistir_Ativo/opcao_ativo_marcada_00-22.jpg), [Opção Ativo desmarcada após a gravação final](../Evidencias/CT-RF142_Integracoes_WhatsApp_Persistir_Ativo/opcao_ativo_desmarcada_00-29.jpg).
- [Linha do tempo](../Evidencias/CT-RF142_Integracoes_WhatsApp_Persistir_Ativo/linha_do_tempo.txt).

A revisão documental se baseia nos quadros do vídeo e nos eventos capturados pelo Jam. As verificações complementares ficam para uma nova rodada de testes.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf142) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
