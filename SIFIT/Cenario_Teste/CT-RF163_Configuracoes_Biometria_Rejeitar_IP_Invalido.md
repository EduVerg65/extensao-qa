# 🧪 Cenário 163: Rejeitar um valor sem formato de IP em Biometria

**Caso de teste:** CT-RF163

**Módulo:** Configurações / Biometria

**Status:** Reprovado nas evidências.

**Gravação:** 16/11/2026, 23:03:49 BRT. **Revisão documental:** 18/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Impedir que uma sequência numérica sem formato de endereço IP substitua o valor configurado para o aparelho. |
| Requisito | [RF163](../Analise%20de%20requisitos.md#rf163) — referência de QA. |
| Tipo / prioridade | Funcional manual / validação · Média, proposta para triagem. |
| Defeito | [BUG-053](../Relatorio-de-Bugs.md#bug-053), em triagem |
| Encaminhamento | Confirmar o formato aceito pelo produto e retestar com endereços válidos e entradas inválidas em um equipamento de teste. |
| Fonte | [Jam 7 — Validação de IP do aparelho](https://jam.dev/c/5b8eea1f-3c87-4497-8fb1-da49f09f9854) e [evidências locais](../Evidencias/CT-RF163_Configuracoes_Biometria_Rejeitar_IP_Invalido/README.md). |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/configuracoes |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.79 / Windows 10 (x86), conforme os metadados do Jam. |
| Tela / arquivo de vídeo | Tela 1707 × 888 informada no Jam. Vídeo em 1918 × 998. |
| Duração | 27,52 s |
| Localização | Brasil. |
| Versão / zoom / classificação do ambiente | A confirmar antes de nova execução. |
| Dados | Campo IP editado com nove dígitos sem separadores. Os valores de configuração foram omitidos. |

## Pré-condições

- Sessão autenticada em Biometria com permissão para alterar os dados de um aparelho de teste.
- Identificar a versão e registrar os valores iniciais e as permissões no próximo teste.

## Cenário BDD

```gherkin
Cenário: Rejeitar um valor sem formato de IP em Biometria
  Dado que Biometria tem um endereço IP de teste válido
  Quando o usuário substitui o endereço por uma sequência de nove dígitos sem separadores e salva
  Então o sistema deve sinalizar a entrada inválida
  E a consulta deve manter o endereço anterior
```

## Passos para execução ou reteste

1. Registrar o endereço de teste configurado em Biometria.
2. Substituir o campo IP por uma sequência numérica sem separadores.
3. Acionar Salvar Configurações e verificar a resposta.
4. Recarregar a aba e comparar a entrada consultada com a configuração anterior.

Este procedimento orienta a próxima execução. O resultado abaixo se limita ao trecho registrado no Jam.

## Resultado esperado

A aplicação recusa a entrada sem formato de IP, informa o campo a corrigir e mantém a configuração anterior.

## Resultado obtido na gravação

O salvamento retornou HTTP 200. Depois de recarregar, o GET devolveu a sequência numérica sem separadores em `ip_aparelho`. O formulário reaberto manteve essa entrada.

| Tempo | Registro |
| --- | --- |
| 0:00–0:14 | Edita o formulário e deixa o campo IP com uma sequência de dígitos sem separadores. |
| 0:14,61 | Salva o formulário e recebe HTTP 200. |
| 0:18,41–0:22 | Recarrega e volta a Biometria. A consulta e o campo mostram a entrada inválida. |

**Rede:**

- 0:14,61  POST `/api/configuracoes/alterar/1` (HTTP 200). A captura desse evento não inclui o corpo do POST.
- 0:18,41  GET `/api/configuracoes/1` (HTTP 200), com `ip_aparelho` composto por nove dígitos sem separadores.

**Conclusão:** Reprovado nas evidências. A leitura posterior comprova o valor armazenado. A gravação não verifica a tentativa de conexão ao aparelho.

## Critérios de aceitação para nova execução

1. A entrada sem formato de IP é rejeitada.
2. A interface identifica o campo que precisa de correção.
3. A consulta após a tentativa mantém o valor anterior.

## Próxima ação e verificações complementares

Confirmar o formato aceito pelo produto e retestar com endereços válidos e entradas inválidas em um equipamento de teste.

## Evidências e limites

- [Jam 7 — Validação de IP do aparelho](https://jam.dev/c/5b8eea1f-3c87-4497-8fb1-da49f09f9854).
- [Arquivos, origem e limites](../Evidencias/CT-RF163_Configuracoes_Biometria_Rejeitar_IP_Invalido/README.md).
- [Campo IP em edição antes de salvar, com dados de conexão ocultos](../Evidencias/CT-RF163_Configuracoes_Biometria_Rejeitar_IP_Invalido/campo_ip_antes_de_salvar_00-14.jpg), [Campo IP após recarregar, com os valores de integração ocultos](../Evidencias/CT-RF163_Configuracoes_Biometria_Rejeitar_IP_Invalido/campo_ip_apos_recarregar_00-22.jpg).
- [Linha do tempo](../Evidencias/CT-RF163_Configuracoes_Biometria_Rejeitar_IP_Invalido/linha_do_tempo.txt).

A revisão documental se baseia nos quadros do vídeo e nos eventos capturados pelo Jam. As verificações complementares ficam para uma nova rodada de testes.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf163) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
