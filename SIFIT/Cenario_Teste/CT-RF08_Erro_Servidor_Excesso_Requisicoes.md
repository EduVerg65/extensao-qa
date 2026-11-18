# 🧪 Cenário 8: Erro no servidor durante o carregamento do dashboard

**Caso de teste:** CT-RF08

**Módulo:** Página inicial / Dashboard / Integrações

**Status:** Reprovado nas evidências — múltiplas requisições retornam HTTP 500 e a interface apresenta um diálogo de erro.

**Gravação:** 15/11/2026, 17:23 BRT, conforme Info do Jam. **Revisão documental:** 15/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Verificar se o dashboard carrega seus dados sem falhas de servidor, sem disparar requisições redundantes e com tratamento adequado de erros parciais. |
| Requisito | [RF08](../Analise%20de%20requisitos.md#rf08) — referência de QA; confirmação de produto pendente. |
| Tipo / prioridade | Funcional manual, integração e análise de rede / Alta, proposta para triagem. |
| Defeito | [BUG-018](../Relatorio-de-Bugs.md#bug-018), em triagem. |
| Encaminhamento | Correlacionar cada HTTP 500 ao endpoint e componente, verificar repetição indevida, inspecionar logs do backend e retestar o carregamento completo. |
| Fonte | [Jam — Erro no servidor por excesso de requisições](https://jam.dev/c/eea58e17-b62f-432b-97b2-b14c14bed555) |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/dashboard |
| Navegador / sistema | Edge 157.0.8103.80 / Windows 11 (x86), conforme Info. |
| Tela / duração | 1912 × 960 informados no Jam / aproximadamente 4 s. |
| Rede | Fast · 10+ Mbps, latência de 50 ms, conforme Info. |
| Sessão | A verificação de token apresenta POST com HTTP 200; credenciais e tokens não foram reproduzidos. |
| Versão / zoom / classificação do ambiente | Não confirmados; registrar antes do reteste. |

## Pré-condições

- Sessão autenticada com acesso ao dashboard.
- Conta e empresa de teste com dados conhecidos para os componentes carregados.
- Captura de Network e Console ativa, sem filtros que ocultem requisições.
- Logs do backend disponíveis para correlação no reteste técnico.

## Cenário BDD

```gherkin
Cenário: Carregar o dashboard sem falhas de servidor ou requisições redundantes
  Dado que o usuário possui uma sessão válida
  Quando acessar o dashboard
  Então cada componente deve solicitar somente os dados necessários
  E as requisições devem receber respostas tratáveis sem erro HTTP 500
  E a interface deve carregar os dados ou identificar especificamente o componente indisponível
```

## Passos para execução ou reteste

1. Limpar a captura de rede e acessar diretamente o dashboard com uma sessão válida.
2. Registrar cada endpoint, método, horário, parâmetros e componente que originou a chamada.
3. Aguardar o término do carregamento e identificar chamadas repetidas com os mesmos parâmetros.
4. Conferir os status e corpos das respostas, além das mensagens da interface e do console.
5. Correlacionar os HTTP 500 aos logs do backend pelo horário ou identificador da requisição.
6. Recarregar uma única vez e comparar a quantidade e a sequência das chamadas.

## Resultado esperado

O dashboard deve carregar seus componentes com requisições necessárias e respostas bem-sucedidas. Uma falha parcial deve ser tratada sem impedir todo o painel, indicando especificamente o componente afetado e permitindo nova tentativa controlada.

## Resultado obtido na gravação

O quadro consultado mostra o dashboard com um diálogo central de erro. O texto integral do diálogo não ficou legível. A aba Network apresenta 23 eventos visíveis: a verificação de token retorna HTTP 200, diversas requisições GET e POST retornam HTTP 500 e chamadas OPTIONS retornam HTTP 204. Três marcadores HTTP 500 aparecem na linha temporal do player.

Os nomes completos dos endpoints aparecem truncados. A evidência confirma múltiplas falhas HTTP 500 durante o carregamento, mas não demonstra que a quantidade de requisições seja a causa, nem permite atribuir cada falha a um componente.

**Conclusão:** Reprovado nas evidências. A causa técnica e a hipótese de excesso ou repetição indevida permanecem em triagem.

## Critérios de aceitação para nova execução

1. A sessão válida é confirmada e a verificação do token não é repetida indevidamente.
2. Cada componente executa apenas as chamadas previstas pelo contrato.
3. Nenhuma requisição necessária ao dashboard retorna HTTP 500.
4. Falhas parciais apresentam mensagem específica e não inutilizam componentes independentes.
5. A quantidade e a sequência das chamadas permanecem estáveis após recarga controlada.
6. Os logs permitem correlacionar e explicar qualquer resposta não bem-sucedida.

## Próxima ação e verificações complementares

Inspecionar caminhos e corpos das requisições, identificar chamadas duplicadas e correlacionar os HTTP 500 aos logs do servidor. Verificar como hipóteses, sem atribuição antecipada de causa, falha simultânea em serviços, repetição causada pelo ciclo de renderização, retentativas não limitadas ou indisponibilidade do backend.

## Evidências e limites

- [Jam original](https://jam.dev/c/eea58e17-b62f-432b-97b2-b14c14bed555).
- [Resumo da evidência](../Evidencias/CT-RF34_Erro_Servidor_Excesso_Requisicoes/README.md).
- [Cronologia documental](../Evidencias/CT-RF34_Erro_Servidor_Excesso_Requisicoes/linha_do_tempo.txt).

Não foram confirmados os caminhos completos, parâmetros, corpos das requisições e respostas, ordem exata de todos os eventos, logs do servidor, persistência do erro ou causa raiz. O título do Jam menciona excesso de requisições, mas a relação causal não foi comprovada.

Não houve nova execução no SIFIT, reteste, inspeção de código ou acesso aos logs do backend. O vídeo e as capturas permanecem no Jam.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)

