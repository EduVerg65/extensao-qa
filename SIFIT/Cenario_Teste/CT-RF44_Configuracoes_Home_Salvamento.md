# 🧪 Cenário 44: Alteração e salvamento das Configurações (Home)

**Caso de teste:** CT-RF44

**Módulo:** Configurações / Home

**Status:** A validar — regra ou contexto pendente.

**Gravação:** 15/11/2026, 19:06 BRT. **Revisão documental:** 15/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Alterar as configurações gerais de acesso e presença e salvá-las, refletindo o resultado na interface. |
| Requisito | [RF44](../Analise%20de%20requisitos.md#rf44) — referência de QA; confirmação de produto pendente. |
| Tipo / prioridade | Exploratório / regra a confirmar; Média, proposta para triagem. |
| Defeito | Sem defeito confirmado. |
| Encaminhamento | Confirmar a faixa válida do campo "Dias para contar cliente como ausente" (valor inicial -120 e valor informado 1100), a confirmação de salvamento esperada e o efeito das opções sobre o menu lateral; registrar defeito apenas se houver divergência com a regra definida. |
| Fonte | [Jam — Pagar.me](https://jam.dev/c/e6e551ef-9196-4c79-b6a2-89747b1e8b33) e [evidências locais](../Evidencias/CT-RF44_Configuracoes_Home_Salvamento/README.md). A mesma gravação é a fonte de [CT-RF42](CT-RF42_Solicitacao_Saque_PagarMe.md), [CT-RF43](CT-RF43_Criacao_Cobranca_PagarMe.md) e [CT-RF45](CT-RF45_Painel_PagarMe_Periodo.md). |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/configuracoes |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.78 / Windows (x86) 11. |
| Tela / arquivo de vídeo | 1920 × 911 informados no Jam. |
| Duração | 1 min 11 s |
| Rede | Classificada como rápida no Jam: 6,8 Mbps, latência de 50 ms. |
| Localização | Brasil. |
| Usuário exibido | Jair, conforme o canto superior direito da tela. |
| Versão / zoom / classificação do ambiente | Não confirmados; registrar antes de nova execução. |
| Dados | Aba Home com Plano do SIFIT "Plano Premium"; opções alteradas de "Sim" para "Não" e Controle de Presença de "Check-in" para "Biometria"; campo de dias com o valor inicial -120 e o valor informado 1100. |

## Pré-condições

- Sessão autenticada com permissão para alterar as Configurações.
- Valores iniciais das configurações registrados antes da alteração.
- Regra de cada opção e do campo "Dias para contar cliente como ausente" definida com o produto.
- Antes de uma nova execução, identificar versão, permissões e dados de referência e preparar a captura de interface e rede.

## Cenário BDD

```gherkin
Cenário: Alterar e salvar as configurações da aba Home
  Dado que o usuário acessa Configurações na aba Home
  Quando alterar as opções e o valor numérico e acionar Salvar Configurações
  Então o sistema deve gravar as configurações
  E informar o resultado ao usuário
  E refletir as alterações nos cartões de resumo e no menu lateral
```

## Passos para execução ou reteste

1. Acessar Configurações, aba Home, e registrar os valores e os cartões de resumo.
2. Alterar as opções e o campo de dias; conferir os cartões de resumo.
3. Acionar Salvar Configurações.
4. Conferir a mensagem, o menu lateral e as demais abas.
5. Recarregar a página e conferir a persistência.

Este procedimento orienta a próxima execução. A evidência atual cobre o trecho gravado e os limites descritos abaixo; passos complementares não recebem resultado de execução nesta revisão.

## Resultado esperado

As alterações são salvas, o usuário recebe confirmação e a interface reflete as configurações salvas.

## Resultado obtido na gravação

As alterações foram aplicadas na interface e o menu lateral mudou após o envio, sem mensagem de confirmação visível nos quadros consultados.

| Tempo | Registro |
| --- | --- |
| 0:32 | Navegação para a tela Configurações; aba Home com os cartões Desktop "Sim", Presença "Check-in", Avaliação "Dobras" e SifitBox "Sim". |
| 0:33 | Plano do SIFIT "Plano Premium"; opções "Sim"; Multa por atraso 2.00; Juros ao dia 0.032; Dias para contar cliente como ausente **-120**. |
| 0:34–0:41 | Cliques nos seletores e digitação de 1100 no campo de dias; os cartões passam a Desktop "Não", Presença "Biometria" e SifitBox "Não", e os campos de multa e juros deixam de ser exibidos. |
| 0:45 | Clique em Salvar Configurações. |
| 0:46–0:48 | Menu lateral sem "Check-in" e "SifitBox" (aparece "Presenças"); campo de dias mantém 1100; nenhuma mensagem de confirmação visível. |
| 0:50–0:56 | Aba Biometria (Possui? "Não") e aba Avaliação (Cobrar Avaliação do Cliente "Sim", Tipo de avaliação "Dobras") exibidas. |

**Rede:** a lista de rede registra, após a navegação, chamadas de leitura (`GET`) e de gravação (`POST`) com HTTP 200 e `OPTIONS` HTTP 204; caminhos e corpos não conferidos.

**Conclusão:** A validar. As alterações são refletidas na interface e no menu, mas a confirmação do salvamento, a persistência, o valor inicial negativo (-120) e a aceitação de 1100 no campo de dias não foram confirmados contra a regra do produto.

## Critérios de aceitação para nova execução

1. O salvamento informa o resultado (sucesso ou erro) de forma compreensível.
2. As configurações salvas persistem após recarga da página.
3. O campo "Dias para contar cliente como ausente" rejeita valores fora da faixa definida (incluindo negativos).
4. O menu lateral e os cartões de resumo refletem as opções salvas.
5. Cancelar descarta as alterações não salvas.

## Próxima ação e verificações complementares

Confirmar com o produto a faixa do campo de dias e a mensagem de salvamento e reexecutar com recarga. Permanecem fora do cenário gravado: Cancelar, valores limite, as demais abas, persistência após recarga e permissões.

## Observação sobre o campo de dias

O campo "Dias para contar cliente como ausente" apresenta -120 como valor inicial e aceita 1100 sem mensagem de validação visível; sem a regra do produto, o comportamento é tratado como ponto a confirmar e não como defeito.

## Evidências e limites

- [Jam original — Pagar.me](https://jam.dev/c/e6e551ef-9196-4c79-b6a2-89747b1e8b33).
- [Arquivos, origem e limites](../Evidencias/CT-RF44_Configuracoes_Home_Salvamento/README.md).
- [Configurações em 0:33](../Evidencias/CT-RF44_Configuracoes_Home_Salvamento/config_00-33.png), [Configurações em 0:41](../Evidencias/CT-RF44_Configuracoes_Home_Salvamento/config_alterada_00-41.png), [Configurações em 0:46](../Evidencias/CT-RF44_Configuracoes_Home_Salvamento/config_salvar_00-46.png), [Aba Avaliação em 0:56](../Evidencias/CT-RF44_Configuracoes_Home_Salvamento/config_avaliacao_00-56.png).
- [Linha do tempo](../Evidencias/CT-RF44_Configuracoes_Home_Salvamento/linha_do_tempo.txt).

Foram consultados os painéis Info, Console, Network e Actions do Jam e os quadros do vídeo; corpos de requisição e de resposta de configurações não foram conferidos. As capturas foram extraídas da reprodução do Jam. A mensagem de salvamento, a persistência e as regras dos campos não foram confirmadas. Não houve nova execução, inspeção do código, acesso ao banco ou correção da aplicação. O vídeo permanece no Jam.

Análise documental da gravação consultada em 15/11/2026. Esta inclusão não executa novamente o sistema e não constitui reteste. Versão da aplicação, zoom e classificação do ambiente não foram confirmados.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf44) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
