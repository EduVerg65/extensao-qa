# Evidência — CT-RF127: Validar letras no campo de dias de ausência

- **Fonte:** [Jam original](https://jam.dev/c/c578ed7a-c11c-4cef-8a6c-84d0244f21a5).
- **Autor exibido:** Pedro Figueiredo.
- **Gravação:** 16/11/2026, 22:02:16 BRT, com duração de 24,48 s.
- **Revisão:** 17/11/2026.
- **Caso:** [CT-RF127](../../Cenario_Teste/CT-RF127_Configuracoes_Dias_Ausencia_Texto.md).
- **Defeito:** Sem defeito confirmado.
- **Ambiente:** https://sifit.centrion.com.br/configuracoes · Chrome 157.0.8103.79 / Windows 10 (x86) · vídeo de 1918 × 998.

## Resultado e origem

As teclas ABC foram registradas, mas as letras não apareceram no campo. Salvar Configurações enviou `dias_ausente=0` com o campo vazio. O POST retornou HTTP 200 com `verifica_erro: false`. Depois, 1100 foi reenviado com sucesso.

**Status:** A validar — regra ou contexto pendente.

## Arquivos

| Arquivo | Conteúdo | SHA-256 |
| --- | --- | --- |
| [dias_vazio_apos_texto_00-16.jpg](dias_vazio_apos_texto_00-16.jpg) | Campo numérico vazio depois da tentativa com letras. | `c117f918de461a316d5578b60dbb64e8fe8c0ed9b0b8adf01b9fc78ede028a9a` |
| [dias_reposto_00-22.jpg](dias_reposto_00-22.jpg) | Valor inicial 1100 informado novamente. | `7e09eb5e2789eca47b7f15dc26fa8188fac4a0b1cea305e5abe198db32e6b254` |
| [linha_do_tempo.txt](linha_do_tempo.txt) | Cronologia de ações, rede e quadros consultados no Jam. | — |
| [origem.url](origem.url) | Endereço original do Jam. | — |

## Limites

Esta pasta contém a cronologia e os recortes dos quadros consultados. A gravação integral fica no Jam.

A rejeição da digitação de letras foi observada. A regra para o campo vazio permanece pendente no CT-RF116. A persistência de zero nesta gravação não foi verificada após recarga.
