# 🧪 Cenário 28: Anexar imagem no campo de vídeo

**Caso de teste:** CT-RF28

**Módulo:** Exercícios / Validação de mídia

**Status:** Reprovado conforme a gravação — o arquivo incompatível não é anexado, mas não há feedback visível.

**Gravação:** 15/11/2026, 16:07 BRT, conforme Info do Jam. **Revisão documental:** 15/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Verificar o tratamento da seleção de um arquivo de imagem no campo destinado exclusivamente a vídeos. |
| Requisito | [RF28](../Analise%20de%20requisitos.md#rf28) — referência de QA; confirmação de produto pendente. |
| Tipo / prioridade | Funcional manual, teste negativo / Média. |
| Defeito | [BUG-015](../Relatorio-de-Bugs.md#bug-015), em triagem. |
| Encaminhamento | Rejeitar o arquivo e informar formatos e limites aceitos no próprio campo. |
| Fonte | [Jam — Imagem no campo de vídeo](https://jam.dev/c/be9437a4-4fe9-4756-a2af-6777d3f43e25) |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/exercicios |
| Navegador / sistema | Edge 157.0.8103.80 / Windows 11 (x86), conforme Info. |
| Tela / duração | 1912 × 960 informados no Jam / aproximadamente 7 s. |
| Rede | Fast · 10+ Mbps, latência de 50 ms, conforme Info. |
| Arquivo | Imagem selecionada no campo Vídeo; nome, formato e tamanho não ficaram legíveis na evidência. |

## Pré-condições

- Sessão autenticada com permissão para cadastrar exercícios.
- Formulário de exercício aberto.
- Arquivo de imagem de teste, sem dados pessoais, disponível localmente.

## Cenário BDD

```gherkin
Cenário: Selecionar uma imagem no campo de vídeo
  Dado que o usuário está no formulário de exercício
  E possui um arquivo de imagem válido como imagem
  Quando selecionar esse arquivo no campo "Vídeo"
  Então o sistema deve rejeitar o arquivo incompatível
  E deve informar os formatos e limites aceitos para vídeos
```

## Passos para execução ou reteste

1. Abrir o formulário de novo exercício.
2. Acionar a seleção de arquivo na seção Vídeo.
3. Selecionar uma imagem conhecida e registrar nome, extensão, MIME e tamanho.
4. Verificar prévia, nome do arquivo, mensagem junto ao campo e notificação geral.
5. Tentar salvar o formulário e confirmar que a imagem não foi associada como vídeo.

## Resultado esperado

A imagem deve ser rejeitada como vídeo e o sistema deve apresentar mensagem clara com os formatos e limites permitidos, preservando o restante do formulário.

## Resultado obtido na gravação

Após a tentativa de selecionar uma imagem na seção Vídeo, não é observada prévia ou associação do arquivo. Também não aparece mensagem explicando a rejeição, os formatos permitidos ou como corrigir a entrada.

**Conclusão:** Reprovado por ausência de feedback visível para arquivo incompatível. A gravação sugere que o arquivo não foi anexado, mas não permite confirmar validação de MIME no servidor.

## Critérios de aceitação para nova execução

1. Arquivos de imagem não são aceitos como vídeo.
2. A mensagem identifica o tipo incompatível e informa formatos e tamanho máximo aceitos.
3. O formulário permanece utilizável e conserva os demais dados.
4. Nenhum upload ou vínculo indevido é persistido.

## Evidências e limites

- [Jam original](https://jam.dev/c/be9437a4-4fe9-4756-a2af-6777d3f43e25).
- A gravação não permite identificar o arquivo, seu MIME ou eventual resposta detalhada da API.
- Não houve nova execução no SIFIT, inspeção de código ou reprodução independente.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)

