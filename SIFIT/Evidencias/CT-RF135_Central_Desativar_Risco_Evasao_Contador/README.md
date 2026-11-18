# Evidência — CT-RF135: Desativar Risco de Evasão e conferir a persistência e o contador

- **Fonte:** [Jam original](https://jam.dev/c/b63ec55f-f8b6-41aa-af4c-d4cdd4515de8).
- **Autor exibido:** Pedro Figueiredo.
- **Gravação:** 16/11/2026, 21:28:33 BRT, com duração de 20,02 s.
- **Revisão:** 17/11/2026.
- **Caso:** [CT-RF135](../../Cenario_Teste/CT-RF135_Central_Desativar_Risco_Evasao_Contador.md).
- **Defeito:** [BUG-049](../../Relatorio-de-Bugs.md#bug-049), em triagem.
- **Ambiente:** https://sifit.centrion.com.br/inteligencia-automacao · Chrome 157.0.8103.79 / Windows 10 (x86) · vídeo de 1918 × 998.

## Resultado e origem

A desativação foi salva com HTTP 200. Após Atualizar, a lista confirmou `ativo: 0` e o contador marcou zero. A reativação também retornou sucesso e o cartão voltou a indicar o estado ativo, mas o resumo retornou `ativas: 0`. O contador permaneceu em zero no restante da gravação.

**Status:** Reprovado nas evidências.

## Arquivos

| Arquivo | Conteúdo | SHA-256 |
| --- | --- | --- |
| [evasao_inativa_00-11.jpg](evasao_inativa_00-11.jpg) | Risco de Evasão inativa e contador em zero após Atualizar. | `e1e205dd503410ed98cd69f0681f4aa08da5eb298de1a496ce63196099da0d2e` |
| [evasao_ativa_contador_zero_00-17.jpg](evasao_ativa_contador_zero_00-17.jpg) | Risco de Evasão ativa com contador ainda em zero. | `3661e03136cb0c84de2540c7960cd51bf3dc9b3c44d90175b7437d493a815c95` |
| [linha_do_tempo.txt](linha_do_tempo.txt) | Cronologia de ações, rede e quadros consultados no Jam. | — |
| [origem.url](origem.url) | Endereço original do Jam. | — |

## Limites

Esta pasta contém a cronologia e os recortes dos quadros consultados. A gravação integral fica no Jam.

A persistência foi confirmada por nova leitura para a desativação. Após a reativação, a gravação não contém outro clique em Atualizar. A ordem em que o servidor processou o salvamento e o resumo não foi determinada.
