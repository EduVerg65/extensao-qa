# Evidência — CT-RF124: Navegar pelas abas de Configurações com a senha da biometria protegida

- **Fonte:** [Jam — PED-15](https://jam.dev/c/38105352-c89c-492e-bca1-78e2f4017ae2).
- **Autor exibido:** Pedro Figueiredo.
- **Gravação:** 16/11/2026, 21:57:29 BRT, com duração de 25,22 s.
- **Revisão:** 17/11/2026.
- **Caso:** [CT-RF124](../../Cenario_Teste/CT-RF124_Configuracoes_Abas_Biometria_Senha.md).
- **Defeito:** [BUG-046](../../Relatorio-de-Bugs.md#bug-046), em triagem.
- **Ambiente:** https://sifit.centrion.com.br/configuracoes · Chrome 157.0.8103.79 / Windows 10 (x86) · vídeo de 1918 × 998.

## Resultado e origem

As abas percorridas carregaram seus painéis e foi possível retornar a Home. Ao abrir Biometria, o campo Senha exibiu o valor configurado em texto legível, sem ação para revelar a senha.

**Status:** Reprovado nas evidências.

## Arquivos

| Arquivo | Conteúdo | SHA-256 |
| --- | --- | --- |
| [aba_biometria_00-04.jpg](aba_biometria_00-04.jpg) | Cabeçalho da aba Biometria, recortado acima dos dados de integração. | `8074f4f2323a67699c7dc1c476f3eb11376c6548191b27b473bb6aaa6fcc131d` |
| [aba_integracoes_00-17.jpg](aba_integracoes_00-17.jpg) | Cabeçalho da aba Integrações, recortado acima dos dados de conexão. | `3464479cf4d64be80c48469cb1b5081cc6b81717fc7dfc3ab2c91d529cad77d9` |
| [linha_do_tempo.txt](linha_do_tempo.txt) | Cronologia de ações, rede e quadros consultados no Jam. | — |
| [origem.url](origem.url) | Endereço original do Jam. | — |

## Limites

Esta pasta contém a cronologia e os recortes dos quadros consultados. A gravação integral fica no Jam.

O defeito foi observado na interface de uma sessão autenticada. O alcance por perfil, a exposição em respostas de API e a validade do valor exibido não foram testados. As evidências versionadas mostram apenas os cabeçalhos das abas.
