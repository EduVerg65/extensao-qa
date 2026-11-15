# Evidência — CT-RF34: Erro no servidor por excesso de requisições

- **Identificador:** RF34 / CT-RF34.
- **Fonte:** [Jam original](https://jam.dev/c/eea58e17-b62f-432b-97b2-b14c14bed555).
- **Título no Jam:** TESTE - ERRO NO SERVIDOR POR EXCESSO DE REQUISIÇÕES.
- **Autor exibido:** Bruno Madeira.
- **Gravação:** 15/11/2026, 17:23 BRT; duração aproximada de 4 s.
- **Revisão documental:** 15/11/2026.
- **Página gravada:** https://sifit.centrion.com.br/dashboard.
- **Ambiente:** Edge 157.0.8103.80, Windows 11 (x86), janela 1912 × 960; rede indicada como Fast · 10+ Mbps e latência de 50 ms.

## Resultado e origem

O quadro consultado mostra o dashboard do SIFIT com um diálogo central de erro. O texto integral do diálogo não ficou legível no quadro disponível, portanto não é reproduzido como mensagem confirmada.

A aba Network apresenta 23 eventos visíveis. A primeira entrada, relacionada à verificação de token, é um POST com HTTP 200. Diversas entradas GET e POST seguintes retornam HTTP 500; chamadas OPTIONS retornam HTTP 204. Três marcadores HTTP 500 também aparecem na linha temporal do player.

Os nomes completos dos endpoints aparecem truncados na listagem consultada. Por isso, a evidência confirma múltiplas falhas HTTP 500 durante o carregamento do dashboard, mas não permite atribuir cada erro a uma funcionalidade, afirmar que o volume foi a causa das falhas ou determinar a origem técnica do comportamento.

**Status documental:** Reprovado nas evidências — múltiplas requisições do dashboard retornam HTTP 500 e a interface apresenta um diálogo de erro.

## Arquivos e limites

Esta pasta contém o resumo da consulta, a cronologia documental e o endereço original do Jam. O vídeo e as capturas permanecem no Jam e não foram copiados para o repositório; nenhum hash do vídeo foi gerado.

Não foram confirmados os caminhos completos, parâmetros, corpos das requisições e respostas, ordem exata de todos os eventos, logs do servidor, persistência do erro ou causa raiz. O título atribui o problema ao excesso de requisições, mas essa relação causal não foi demonstrada apenas pela listagem consultada.

Não houve nova execução no SIFIT, reteste, inspeção de código, acesso aos logs do backend ou revisão integral quadro a quadro.

