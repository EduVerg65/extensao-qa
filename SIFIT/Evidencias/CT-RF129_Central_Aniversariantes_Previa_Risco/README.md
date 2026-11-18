# Evidência — CT-RF129: Abrir Aniversariantes e conferir a prévia da automação

- **Fonte:** [Jam original](https://jam.dev/c/c66d4d01-aee2-4037-a8fd-858da21a0a14).
- **Autor exibido:** Pedro Figueiredo.
- **Gravação:** 16/11/2026, 21:41:32 BRT, com duração de 20,88 s.
- **Revisão:** 17/11/2026.
- **Caso:** [CT-RF129](../../Cenario_Teste/CT-RF129_Central_Aniversariantes_Previa_Risco.md).
- **Defeito:** [BUG-048](../../Relatorio-de-Bugs.md#bug-048), em triagem.
- **Ambiente:** https://sifit.centrion.com.br/inteligencia-automacao · Chrome 157.0.8103.79 / Windows 10 (x86) · vídeo de 1918 × 998.

## Resultado e origem

O painel abriu com o título Aniversariantes, frequência diária e horário 08:00. A prévia exibiu um relatório com 24 alunos em risco, redução de frequência, pagamentos atrasados e falta de presença recente. Cancelar fechou o painel e o cartão continuou inativo.

**Status:** Reprovado nas evidências.

## Arquivos

| Arquivo | Conteúdo | SHA-256 |
| --- | --- | --- |
| [painel_aniversariantes_00-04.jpg](painel_aniversariantes_00-04.jpg) | Painel aberto com o título Aniversariantes. | `25a1859bafa491f0f9435e984522f69da6e9de882c6c153179e92d00b1d27530` |
| [previa_risco_em_aniversariantes_00-12.jpg](previa_risco_em_aniversariantes_00-12.jpg) | Prévia de risco exibida no painel Aniversariantes. | `07584d5aaa80d1cecc7c132f24a24750e27090524f79ca74e045eec0dccc7710` |
| [linha_do_tempo.txt](linha_do_tempo.txt) | Cronologia de ações, rede e quadros consultados no Jam. | — |
| [origem.url](origem.url) | Endereço original do Jam. | — |

## Limites

Esta pasta contém a cronologia e os recortes dos quadros consultados. A gravação integral fica no Jam.

A divergência foi observada na prévia do painel. O envio real, o conteúdo recebido e a persistência de alterações não foram exercitados.
