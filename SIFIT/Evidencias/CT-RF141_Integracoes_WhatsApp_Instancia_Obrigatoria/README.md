# Evidência — CT-RF141: Bloquear o salvamento com Nome da Instância vazio

- **Fonte:** Jam 3 — Obrigatoriedade do Nome da Instância (gravação restrita por conter dados de integração).
- **Autor exibido:** Pedro Figueiredo.
- **Gravação:** 16/11/2026, 23:41:03 BRT, com duração de 28,69 s.
- **Revisão:** 17/11/2026.
- **Caso:** [CT-RF141](../../Cenario_Teste/CT-RF141_Integracoes_WhatsApp_Instancia_Obrigatoria.md).
- **Defeito:** Nenhum no fluxo avaliado.
- **Ambiente:** https://sifit.centrion.com.br/configuracoes · Chrome 157.0.8103.79 / Windows 10 (x86) · vídeo de 1918 × 998.

## Resultado e origem

Com a instância preenchida, o POST retornou sucesso e o GET trouxe o valor salvo. Ao limpar o campo, as tentativas seguintes não produziram POST na captura. Após recarregar e reabrir Integrações, o nome salvo voltou a aparecer. Uma nova tentativa com o nome vazio também não registrou envio.

**Status:** Aprovado conforme a gravação.

## Arquivos

| Arquivo | Conteúdo | SHA-256 |
| --- | --- | --- |
| [instancia_vazia_00-14.jpg](instancia_vazia_00-14.jpg) | Campo Nome da Instância vazio e ação Salvar Configuração. | `3c42939749c4405a1dee6b4e275847f16012a39dfc9fa256d9786d2ebc5488cf` |
| [instancia_apos_reabrir_00-24.jpg](instancia_apos_reabrir_00-24.jpg) | Nome da Instância preenchido novamente pelo valor salvo. | `182be12f671ead122a2e5d70e179c6989e38b96c328adbd644d753085f4317aa` |
| [linha_do_tempo.txt](linha_do_tempo.txt) | Cronologia de ações, rede e quadros consultados no Jam. | — |
| [origem.url](origem.url) | Página testada. O link da gravação fica restrito. | — |

## Limites

Os recortes e a cronologia omitem valores dos campos de integração, identificadores de conta e dados de autenticação. A gravação integral fica no Jam.

A evidência confirma o bloqueio e a persistência do valor anterior. A regra para espaços e o texto da orientação de validação ficam para reteste.
