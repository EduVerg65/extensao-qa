# Evidência — CT-RF142: Persistir a opção Ativo da integração de WhatsApp

- **Fonte:** Jam 4 — Persistência da opção Ativo (gravação restrita por conter dados de integração).
- **Autor exibido:** Pedro Figueiredo.
- **Gravação:** 16/11/2026, 23:42:47 BRT, com duração de 29,40 s.
- **Revisão:** 17/11/2026.
- **Caso:** [CT-RF142](../../Cenario_Teste/CT-RF142_Integracoes_WhatsApp_Persistir_Ativo.md).
- **Defeito:** Nenhum no fluxo avaliado.
- **Ambiente:** https://sifit.centrion.com.br/configuracoes · Chrome 157.0.8103.79 / Windows 10 (x86) · vídeo de 1918 × 998.

## Resultado e origem

As tentativas iniciais com a instância vazia não geraram POST. Após recarregar o formulário com a instância preenchida, o salvamento de Ativo enviou `ativo: 1` e a reconsulta devolveu `ativo: true`. Ao desmarcar e salvar, o POST enviou `ativo: 0` e a nova leitura trouxe `ativo: false`. A conexão permaneceu desconectada.

**Status:** Aprovado conforme a gravação.

## Arquivos

| Arquivo | Conteúdo | SHA-256 |
| --- | --- | --- |
| [opcao_ativo_marcada_00-22.jpg](opcao_ativo_marcada_00-22.jpg) | Opção Ativo marcada após a confirmação pela API. | `0ed4cf382bfcb2ae48b7ce23c0b009ee5893758daa53537e20cca97297b2afdc` |
| [opcao_ativo_desmarcada_00-29.jpg](opcao_ativo_desmarcada_00-29.jpg) | Opção Ativo desmarcada após a gravação final. | `92f9488acfd5f7ba584dce03df789d9821df35d1925acda9c72fcb6be30667ff` |
| [linha_do_tempo.txt](linha_do_tempo.txt) | Cronologia de ações, rede e quadros consultados no Jam. | — |
| [origem.url](origem.url) | Página testada. O link da gravação fica restrito. | — |

## Limites

Os recortes e a cronologia omitem valores dos campos de integração, identificadores de conta e dados de autenticação. A gravação integral fica no Jam.

A aprovação é restrita à persistência da opção. A execução de automações e o envio de mensagens não foram exercitados.
