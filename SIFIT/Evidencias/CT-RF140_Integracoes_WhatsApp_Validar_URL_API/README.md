# Evidência — CT-RF140: Validar uma URL da API sem formato de endereço

- **Fonte:** Jam 2 — Validação da URL da API (gravação restrita por conter dados de integração).
- **Autor exibido:** Pedro Figueiredo.
- **Gravação:** 16/11/2026, 23:39:06 BRT, com duração de 22,92 s.
- **Revisão:** 17/11/2026.
- **Caso:** [CT-RF140](../../Cenario_Teste/CT-RF140_Integracoes_WhatsApp_Validar_URL_API.md).
- **Defeito:** Sem defeito confirmado.
- **Ambiente:** https://sifit.centrion.com.br/configuracoes · Chrome 157.0.8103.79 / Windows 10 (x86) · vídeo de 1918 × 998.

## Resultado e origem

Foi inserido texto sem formato de URL e acionado Salvar Configuração. O Nome da Instância estava vazio. A captura não registrou POST de configuração ou uma mensagem específica da URL. Após recarregar e voltar a Integrações, o texto digitado já não aparecia no campo.

**Status:** A validar — regra ou contexto pendente.

## Arquivos

| Arquivo | Conteúdo | SHA-256 |
| --- | --- | --- |
| [tentativa_de_salvar_url_00-11.jpg](tentativa_de_salvar_url_00-11.jpg) | Formulário após a tentativa de salvar, com valores de integração ocultos. | `ed26db4e6c0563f29c320852f432eaa261fd66afe3ce764aba81c23e0166b088` |
| [status_ao_reabrir_00-16.jpg](status_ao_reabrir_00-16.jpg) | Status visível após reabrir a aba Integrações. | `cc04088ffc7a4a64c799054b2e7fcca5488988a72715d70bad9ed1426290d0ae` |
| [linha_do_tempo.txt](linha_do_tempo.txt) | Cronologia de ações, rede e quadros consultados no Jam. | — |
| [origem.url](origem.url) | Página testada. O link da gravação fica restrito. | — |

## Limites

Os recortes e a cronologia omitem valores dos campos de integração, identificadores de conta e dados de autenticação. A gravação integral fica no Jam.

O Nome da Instância vazio impede atribuir a ausência de POST à regra de URL. A gravação não demonstra qual validação bloqueou a tentativa.
