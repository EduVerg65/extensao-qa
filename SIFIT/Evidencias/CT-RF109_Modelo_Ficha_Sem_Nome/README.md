# Evidência — CT-RF109: Bloquear cadastro de modelo de ficha sem nome

- **Fonte:** [Jam original](https://jam.dev/c/fb5673c9-3cd1-46c4-88f4-d5fb32574a8e).
- **Autor exibido:** Pedro Figueiredo.
- **Gravação:** 16/11/2026, 22:19:51 BRT, com duração de 18,91 s.
- **Revisão:** 17/11/2026.
- **Caso:** [CT-RF109](../../Cenario_Teste/CT-RF109_Modelo_Ficha_Sem_Nome.md).
- **Defeito:** nenhum no fluxo avaliado.
- **Ambiente:** https://sifit.centrion.com.br/fichas-treino-modelo · Chrome 157.0.8103.79, Windows 10 (x86), vídeo de 1918 × 998.

## Resultado e origem

Após o clique em Criar Modelo, a tela exibiu o aviso “Informe o nome do modelo.” Ao clicar em Entendi, o formulário permaneceu aberto com o personal selecionado. A captura não registrou requisições de rede durante a tentativa.

**Status:** Aprovado conforme a gravação.

## Arquivos

| Arquivo | Conteúdo | SHA-256 |
| --- | --- | --- |
| [aviso_nome_obrigatorio_00-13.jpg](aviso_nome_obrigatorio_00-13.jpg) | Aviso exibido após tentar criar sem nome. | `3e40722a8398303f4c939a6d579171d1046243235462a27c6de794c5c7eb37a4` |
| [formulario_apos_aviso_00-17.jpg](formulario_apos_aviso_00-17.jpg) | Formulário disponível após fechar o aviso. | `90a7f2c76f5deb470ebfc52b50452b4c7956a0a377d04d76340876360a81e4fe` |
| [linha_do_tempo.txt](linha_do_tempo.txt) | Cronologia de ações, rede e quadros consultados no Jam. | — |
| [origem.url](origem.url) | Endereço do Jam original. | — |

## Limites

Esta pasta contém a cronologia, a origem e os recortes dos quadros consultados. O vídeo permanece no Jam.

A gravação cobre o nome vazio com um personal selecionado. Entrada composta apenas por espaços, envio com todos os campos vazios e validação no servidor exigem verificação própria.

A revisão se limita ao material gravado. A execução do sistema para as verificações complementares está prevista no caso de teste.
