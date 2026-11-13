# Evidências — CT-RF04_loginComSucesso

| Item | Registro |
| --- | --- |
| Fonte | [Jam — Login com sucesso](https://jam.dev/c/5e4a28be-4e80-43d3-9587-1b113723cc38). |
| Gravação / consulta | 13/11/2026 / 13/11/2026. |
| Autor / duração | Leonardo Barbosa / aproximadamente 12 segundos. |
| Ambiente | Chrome 157.0.8103.51, Windows 11 (x86), janela 1536 × 742. |
| Página / destino | `https://sifit.centrion.com.br/login` → `https://sifit.centrion.com.br/dashboard`. |
| Material consultado | Metadados e cronologia via `getDetails`; mosaico de seis quadros via `getFrames`, modo `overview`. |
| Resultado | Aprovado conforme a gravação, sem nova execução na aplicação. |

## Resumo da gravação

O usuário informa Login e Senha, clica em **Entrar** e acessa o dashboard. O menu lateral e os cartões do resumo da academia aparecem após o envio. As chamadas de login e verificação da sessão retornam HTTP 200.

## Cronologia observada

| Momento aproximado | Evidência |
| --- | --- |
| 00:01 | Cliques no campo Login; formulário de autenticação visível. |
| 00:03 | Quadro mostra Login preenchido. |
| 00:05 | Quadro mostra senha mascarada; Manter conectado desmarcado. |
| 00:06 | Clique em Entrar; `POST /api/login` e `POST /api/verifica-token-logado` retornam HTTP 200 no backend `backendsifit.centrion.com.br`. |
| 00:06 | Cronologia registra navegação por `/login` e, em seguida, `/dashboard`. |
| 00:07 | Painel aparece; chamadas de dados do dashboard listadas no Jam retornam HTTP 200. |
| 00:09–00:11 | Menu e cartões preenchidos visíveis, incluindo Clientes Ativos, Clientes Ausentes e Sem Matrículas. |
| 00:12 | Fim da gravação. |

## Origem e limites

Os horários são aproximados, transcritos da cronologia e dos rótulos dos quadros. A consulta visual utilizou os quadros em 00:01.019, 00:03.058, 00:05.096, 00:07.134, 00:09.173 e 00:11.211. Não foram exportadas capturas locais; o vídeo permanece na fonte vinculada.

O resultado se apoia no redirecionamento e na apresentação do painel, além dos status HTTP. Não foram inspecionados corpos das requisições/respostas, tokens ou logs do console. Não há conclusão sobre persistência, logout, outros perfis, correspondência do nome do cabeçalho com o cadastro ou correção dos valores do painel. Credenciais foram omitidas.

[Caso completo](../../Cenario_Teste/CT-RF04_loginComSucesso.md) · [Relatório dos testes](../../Relatorio%20dos%20testes.md)
