# 🧪 Cenário 138: Persistir a desativação do Pagamento Online

**Caso de teste:** CT-RF138

**Módulo:** Configurações / Pagamento

**Status:** Aprovado conforme a gravação.

**Gravação:** 16/11/2026, 23:23:27 BRT. **Revisão documental:** 17/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Confirmar que a opção Pagamento Online pode ser alterada para Não e mantém esse valor após recarregar. |
| Requisito | [RF138](../Analise%20de%20requisitos.md#rf138) — referência de QA. |
| Tipo / prioridade | Funcional manual / persistência · Média, proposta para triagem. |
| Defeito | Nenhum no fluxo avaliado |
| Encaminhamento | Usar como regressão para desativação e confirmar a reativação com nova leitura em reteste. |
| Fonte | [Jam 2 — Desativação do Pagamento Online](https://jam.dev/c/845de9b6-12f7-4002-a8ba-82e1a85affba) e [evidências locais](../Evidencias/CT-RF146_Configuracoes_Pagamento_Online_Desativar/README.md). |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/configuracoes |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.79 / Windows 10 (x86), conforme os metadados do Jam. |
| Tela / arquivo de vídeo | Tela 1707 × 888 informada no Jam. Vídeo em 1918 × 998. |
| Duração | 15,84 s |
| Localização | Brasil. |
| Versão / zoom / classificação do ambiente | A confirmar antes de nova execução. |
| Dados | Pagamento Online começa em Sim. A gravação altera para Não, verifica a persistência e solicita a restauração para Sim. |

## Pré-condições

- Sessão autenticada com acesso à aba Pagamento e uma configuração de teste com Pagamento Online habilitado.
- Identificar a versão e registrar os valores iniciais e as permissões no próximo teste.

## Cenário BDD

```gherkin
Cenário: Persistir a desativação do Pagamento Online
  Dado que Pagamento Online está em Sim
  Quando o usuário seleciona Não, salva e reabre a aba
  Então o formulário deve manter Não após a consulta da configuração
  E a API deve retornar o mesmo valor armazenado
```

## Passos para execução ou reteste

1. Verificar o valor inicial de Pagamento Online na aba Pagamento.
2. Selecionar Não, salvar e recarregar.
3. Reabrir Pagamento e conferir o seletor e a resposta de consulta.
4. Restaurar o valor inicial e verificar novamente a configuração.

Este procedimento orienta a próxima execução. O resultado abaixo se limita ao trecho registrado no Jam.

## Resultado esperado

Após salvar Não e recarregar, a consulta devolve `pagarme: nao` e o seletor indica Não.

## Resultado obtido na gravação

A alteração para Não retornou sucesso. Após recarregar, a consulta devolveu `pagarme: nao` e a aba Pagamento exibiu Não. No fim, o usuário selecionou Sim e enviou a restauração, que retornou sucesso.

| Tempo | Registro |
| --- | --- |
| 0:03–0:05 | Seleciona Não e salva as configurações. |
| 0:08–0:11 | Recarrega a página e volta a Pagamento. O seletor mostra Não. |
| 0:12–0:15 | Seleciona Sim e salva para restaurar o valor inicial. |

**Rede:**

- 0:05,49  POST `/api/configuracoes/alterar/1` com `pagarme: nao` (HTTP 200, `verifica_erro: false`).
- 0:08,46  GET `/api/configuracoes/1` (HTTP 200), com `pagarme: nao`.
- 0:14,43  POST com `pagarme: sim` para restauração (HTTP 200, `verifica_erro: false`).

**Conclusão:** Aprovado conforme a gravação. A aprovação cobre a persistência de Não. A gravação termina após o POST de restauração, sem nova leitura de Sim. Cobrança e validação do token não foram exercitadas.

## Critérios de aceitação para nova execução

1. Salvar Não retorna sucesso.
2. O GET posterior retorna `pagarme: nao`.
3. A aba indica Não após ser reaberta.

## Próxima ação e verificações complementares

Usar como regressão para desativação e confirmar a reativação com nova leitura em reteste.

## Evidências e limites

- [Jam 2 — Desativação do Pagamento Online](https://jam.dev/c/845de9b6-12f7-4002-a8ba-82e1a85affba).
- [Arquivos, origem e limites](../Evidencias/CT-RF146_Configuracoes_Pagamento_Online_Desativar/README.md).
- [Pagamento Online retorna como Não após reabrir a aba](../Evidencias/CT-RF146_Configuracoes_Pagamento_Online_Desativar/pagamento_nao_apos_reabrir_00-11.jpg), [Pagamento Online alterado para Sim antes do salvamento de restauração](../Evidencias/CT-RF146_Configuracoes_Pagamento_Online_Desativar/pagamento_sim_na_restauracao_00-14.jpg).
- [Linha do tempo](../Evidencias/CT-RF146_Configuracoes_Pagamento_Online_Desativar/linha_do_tempo.txt).

A revisão documental se baseia nos quadros do vídeo e nos eventos capturados pelo Jam. As verificações complementares ficam para uma nova rodada de testes.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf138) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
