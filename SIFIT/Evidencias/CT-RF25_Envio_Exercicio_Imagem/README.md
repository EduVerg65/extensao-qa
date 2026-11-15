# Evidência — CT-RF25: Envio de exercício com imagem

- **Fonte:** [Jam original](https://jam.dev/c/25c37a9b-e9bd-4e0c-adf1-4da528ae1d58).
- **Autor exibido:** Bruno Madeira.
- **Gravação:** 15/11/2026, 15:35 BRT; duração aproximada de 5 s.
- **Revisão:** 15/11/2026.
- **Caso:** [CT-RF25](../../Cenario_Teste/CT-RF25_Envio_Exercicio_Imagem.md).
- **Ambiente:** https://sifit.centrion.com.br/exercicios; Edge 157.0.8103.80, Windows 11 (x86), janela 1912 × 960.

## Resultado e origem

O quadro inicial consultado mostra o formulário Exercício preenchido com nome braço forte e uma miniatura na seção Imagem; a biblioteca ao fundo indica total 9. O quadro final mostra o formulário fechado, braço forte na lista e total 10. Esses quadros sustentam a criação com imagem selecionada, mas não demonstram a reabertura ou a visualização da imagem salva.

A aba Network apresenta duas entradas POST com HTTP 201, uma OPTIONS com HTTP 204 e uma POST com HTTP 200 no domínio backendsifit.centrion.com.br. Sem inspecionar caminhos e corpos, não é possível atribuir cada requisição ao cadastro, ao upload ou à atualização da lista.

**Status:** A validar — criação visível; persistência e associação da imagem não confirmadas.

## Arquivos e limites

Esta pasta contém documentação da consulta, cronologia e o endereço original. Não contém cópia do vídeo ou captura de tela; nenhum hash de vídeo foi gerado. A cronologia distingue observações de verificações futuras.

Não foram confirmados nome, formato, tamanho ou conteúdo integral do arquivo, nem a persistência da imagem, sua recuperação ou a ausência de duplicação após nova submissão.

Não houve execução da aplicação ou inspeção de código nesta revisão.
