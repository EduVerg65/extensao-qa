# 🧪 Cenário 141: Bloquear o salvamento com Nome da Instância vazio

**Caso de teste:** CT-RF141

**Módulo:** Configurações / Integrações / WhatsApp

**Status:** Aprovado conforme a gravação.

**Gravação:** 16/11/2026, 23:41:03 BRT. **Revisão documental:** 17/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Verificar que Nome da Instância preenchido pode ser salvo e que a tentativa com o campo vazio preserva o valor existente. |
| Requisito | [RF141](../Analise%20de%20requisitos.md#rf141) — referência de QA. |
| Tipo / prioridade | Funcional manual / validação · Média, proposta para triagem. |
| Defeito | Nenhum no fluxo avaliado |
| Encaminhamento | Usar como regressão e verificar tratamento de espaços em branco e mensagem de campo obrigatório. |
| Fonte | Jam 3 — Obrigatoriedade do Nome da Instância (gravação restrita por conter dados de integração) e [evidências locais](../Evidencias/CT-RF141_Integracoes_WhatsApp_Instancia_Obrigatoria/README.md). |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/configuracoes |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.79 / Windows 10 (x86), conforme os metadados do Jam. |
| Tela / arquivo de vídeo | Tela 1536 × 799 informada no Jam. Vídeo em 1918 × 998. |
| Duração | 28,69 s |
| Localização | Brasil. |
| Versão / zoom / classificação do ambiente | A confirmar antes de nova execução. |
| Dados | O usuário preenche o nome de teste, salva, apaga o nome para os testes negativos e recarrega a página. |

## Pré-condições

- Sessão autenticada com acesso à integração de WhatsApp e aos dados de teste necessários ao salvamento.
- Identificar a versão e registrar os valores iniciais e as permissões no próximo teste.

## Cenário BDD

```gherkin
Cenário: Bloquear o salvamento com Nome da Instância vazio
  Dado que a configuração de WhatsApp está salva com uma instância preenchida
  Quando o usuário apaga o Nome da Instância e tenta salvar
  Então a configuração não deve ser gravada com a instância vazia
  E o nome previamente salvo deve voltar ao reabrir o formulário
```

## Passos para execução ou reteste

1. Preencher Nome da Instância com um valor de teste e salvar.
2. Limpar apenas Nome da Instância e acionar Salvar Configuração.
3. Recarregar a página e retornar a Integrações.
4. Conferir o nome restaurado e as requisições das duas tentativas.

Este procedimento orienta a próxima execução. O resultado abaixo se limita ao trecho registrado no Jam.

## Resultado esperado

O formulário permite salvar com o campo preenchido. A tentativa com o campo vazio não altera a configuração armazenada.

## Resultado obtido na gravação

Com a instância preenchida, o POST retornou sucesso e o GET trouxe o valor salvo. Ao limpar o campo, as tentativas seguintes não produziram POST na captura. Após recarregar e reabrir Integrações, o nome salvo voltou a aparecer. Uma nova tentativa com o nome vazio também não registrou envio.

| Tempo | Registro |
| --- | --- |
| 0:01–0:05 | Preenche Nome da Instância, salva e a tela volta a exibir o valor gravado. |
| 0:09–0:18 | Limpa o nome e tenta salvar quatro vezes. O campo continua vazio no formulário. |
| 0:19–0:24 | Recarrega e volta a Integrações. O campo exibe o nome salvo. |
| 0:25–0:27 | Limpa novamente e repete a tentativa de salvar. |

**Rede:**

- 0:05,02  POST `/api/empresa/whatsapp/1` (HTTP 200, `verifica_erro: false`) com o nome preenchido. O GET subsequente trouxe a configuração salva.
- 0:11,79–0:17,64 e 0:27,17  As tentativas com o campo vazio ocorreram sem POST de configuração na captura.
- 0:22,40  GET `/api/empresa/whatsapp/1` (HTTP 200) ao reabrir Integrações, com o nome salvo anteriormente.

**Conclusão:** Aprovado conforme a gravação. A evidência confirma o bloqueio e a persistência do valor anterior. A regra para espaços e o texto da orientação de validação ficam para reteste.

## Critérios de aceitação para nova execução

1. Com o controle positivo, o nome preenchido persiste após a consulta.
2. O campo vazio bloqueia o salvamento.
3. Reabrir a aba mantém o nome gravado antes da tentativa.

## Próxima ação e verificações complementares

Usar como regressão e verificar tratamento de espaços em branco e mensagem de campo obrigatório.

## Evidências e limites

- Jam 3 — Obrigatoriedade do Nome da Instância (gravação restrita por conter dados de integração).
- [Arquivos, origem e limites](../Evidencias/CT-RF141_Integracoes_WhatsApp_Instancia_Obrigatoria/README.md).
- [Campo Nome da Instância vazio e ação Salvar Configuração](../Evidencias/CT-RF141_Integracoes_WhatsApp_Instancia_Obrigatoria/instancia_vazia_00-14.jpg), [Nome da Instância preenchido novamente pelo valor salvo](../Evidencias/CT-RF141_Integracoes_WhatsApp_Instancia_Obrigatoria/instancia_apos_reabrir_00-24.jpg).
- [Linha do tempo](../Evidencias/CT-RF141_Integracoes_WhatsApp_Instancia_Obrigatoria/linha_do_tempo.txt).

A revisão documental se baseia nos quadros do vídeo e nos eventos capturados pelo Jam. As verificações complementares ficam para uma nova rodada de testes.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf141) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
