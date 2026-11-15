# Evidência — CT-RF24: Edição de exercício aumenta o total e mantém duas entradas

- **Fonte:** [Jam original](https://jam.dev/c/073f70d6-4052-4e0f-a4bb-e9f37305d618).
- **Autor exibido:** Bruno Madeira.
- **Gravação:** 15/11/2026, 15:38 BRT; duração aproximada de 9 s.
- **Revisão:** 15/11/2026.
- **Caso:** [CT-RF24](../../Cenario_Teste/CT-RF24_Edicao_Exercicio.md).
- **Ambiente:** https://sifit.centrion.com.br/exercicios; Edge 157.0.8103.80, Windows 11 (x86), janela 1912 × 960.

## Resultado e origem

O Jam está identificado como teste de edição. Nos quadros intermediários, o formulário Exercício está aberto com código 16, o nome é preenchido e a biblioteca ao fundo indica total 10. No quadro final, o formulário fecha, o total é 11 e a lista contém Levantamento de Peso e Levantamento de Peso 02. O aumento e a coexistência dos nomes divergem do resultado esperado para uma edição.

A aba Network apresenta POST com HTTP 200, GET de arquivo MP4 com HTTP 200, POST com HTTP 201 e outro POST com HTTP 200. O HTTP 201 é compatível com criação, mas isoladamente não confirma a causa: caminhos, corpos e contrato da API não foram inspecionados.

**Status:** Reprovado no trecho consultado; confirmar operação e identidade dos registros na reprodução.

## Arquivos e limites

Esta pasta contém documentação da consulta, cronologia e o endereço original. Não contém cópia do vídeo ou captura de tela; nenhum hash de vídeo foi gerado. A cronologia distingue observações de verificações futuras.

O acionamento inicial da edição e os identificadores das duas entradas não foram confirmados. A classificação considera o propósito declarado do Jam e a divergência visual; se a operação tiver sido criação, reavaliar a conclusão.

Não houve execução da aplicação ou inspeção de código nesta revisão.
