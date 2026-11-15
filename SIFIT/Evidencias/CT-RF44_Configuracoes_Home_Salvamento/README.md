# Evidência — CT-RF44: Alteração e salvamento das Configurações (Home)

- **Fonte:** [Jam original](https://jam.dev/c/e6e551ef-9196-4c79-b6a2-89747b1e8b33).
- **Autor exibido:** Gustavo Pelissari Oenning.
- **Gravação:** 15/11/2026, 19:06 BRT; duração de 1 min 11 s.
- **Revisão:** 15/11/2026.
- **Caso:** [CT-RF44](../../Cenario_Teste/CT-RF44_Configuracoes_Home_Salvamento.md).
- **Defeito:** nenhum confirmado; ponto a validar.
- **Ambiente:** https://sifit.centrion.com.br/configuracoes; Chrome 157.0.8103.78, Windows 11 (x86), janela 1920 × 911.

## Resultado e origem

Entre 0:34 e 0:45, as opções da aba Home são alteradas e o campo de dias recebe 1100; os cartões de resumo mudam em seguida e, após Salvar Configurações (0:45), o menu lateral passa a exibir "Presenças" no lugar de "Check-in" e de "SifitBox". Não há mensagem de confirmação visível.

**Status:** A validar — regra ou contexto pendente.

## Arquivos

| Arquivo | Conteúdo | SHA-256 |
| --- | --- | --- |
| [config_00-33.png](config_00-33.png) | aba Home com os valores iniciais (dias -120). | `4acf1862a599e55b3a549d04ff56ae84f6b5a3bbce520ec8e9ccf4a0465356ea` |
| [config_alterada_00-41.png](config_alterada_00-41.png) | opções alteradas e campo de dias em 11. | `4ea929f1a4636693ad7630ef25cab004fd6b909f697c2f809e2d3fd1cfee99eb` |
| [config_salvar_00-46.png](config_salvar_00-46.png) | valores salvos (dias 1100) e menu lateral alterado. | `61d1eadc24f597d3e857fc0ddc109fa424cadd9050c6577f3ccbaff9c813c88e` |
| [config_avaliacao_00-56.png](config_avaliacao_00-56.png) | aba Avaliação aberta após o salvamento. | `e9b508b7888144781635c4d6716b15f7b940fd71b65bcc731cfd0e90b81b6a2c` |
| [linha_do_tempo.txt](linha_do_tempo.txt) | Cronologia de ações, digitação e rede do Jam. | — |
| [origem.url](origem.url) | Endereço original do Jam. | — |

## Limites

Esta pasta contém documentação da consulta, capturas extraídas da reprodução do Jam e a cronologia; não contém cópia do vídeo, e nenhum hash de vídeo foi gerado. As capturas mostram o botão de reprodução do Jam sobreposto. A mesma gravação é a fonte de vários casos.

Não foram confirmados a mensagem de salvamento, a persistência após recarga, as regras dos campos e o conteúdo das requisições de configuração.

Não houve execução da aplicação, inspeção de código, acesso ao banco ou reteste nesta revisão.
