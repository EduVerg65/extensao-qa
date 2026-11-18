# 🧪 Cenário 141: Informar o limite de tamanho ao rejeitar o logo

**Caso de teste:** CT-RF141

**Módulo:** Configurações / Design

**Status:** Reprovado nas evidências.

**Gravação:** 16/11/2026, 23:27:58 BRT. **Revisão documental:** 17/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Verificar se a rejeição de logo por tamanho informa ao usuário o limite retornado pela API. |
| Requisito | [RF141](../Analise%20de%20requisitos.md#rf141) — referência de QA. |
| Tipo / prioridade | Funcional manual / validação e feedback · Baixa, proposta para triagem. |
| Defeito | [BUG-052](../Relatorio-de-Bugs.md#bug-052), em triagem |
| Encaminhamento | Retestar com arquivos de tamanho conhecido no entorno do limite e confirmar a mensagem de validação e a preservação do logo salvo na recusa. |
| Fonte | [Jam 5 — Rejeição de logo pelo limite de tamanho](https://jam.dev/c/7aaeac50-8269-4cd6-b7f6-4c8c3740b0e5) e [evidências locais](../Evidencias/CT-RF149_Configuracoes_Design_Logo_Limite_Tamanho/README.md). |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/configuracoes |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.79 / Windows 10 (x86), conforme os metadados do Jam. |
| Tela / arquivo de vídeo | Tela 1707 × 888 informada no Jam. Vídeo em 1918 × 998. |
| Duração | 18,41 s |
| Localização | Brasil. |
| Versão / zoom / classificação do ambiente | A confirmar antes de nova execução. |
| Dados | Imagem selecionada no cartão Logo. A requisição multipart capturada tinha 10.081.448 bytes no total. |

## Pré-condições

- Sessão autenticada com acesso a Design. Preparar arquivos de teste dos formatos aceitos, com tamanhos medidos abaixo e acima de 6 MB.
- Identificar a versão e registrar os valores iniciais e as permissões no próximo teste.

## Cenário BDD

```gherkin
Cenário: Informar o limite de tamanho ao rejeitar o logo
  Dado que o usuário selecionou um logo acima do limite admitido
  Quando ele tenta salvar as configurações de Design
  Então o arquivo deve ser recusado
  E a tela deve informar o motivo e o limite para orientar a correção
```

## Passos para execução ou reteste

1. Abrir Design e registrar o logo salvo.
2. Selecionar um JPG ou PNG de teste com tamanho medido acima de 6 MB.
3. Acionar Salvar Configurações e comparar o texto da tela com o motivo da API.
4. Selecionar uma imagem abaixo do limite e conferir o salvamento e a consulta após recarregar.

Este procedimento orienta a próxima execução. O resultado abaixo se limita ao trecho registrado no Jam.

## Resultado esperado

Ao rejeitar um logo pelo tamanho, o sistema informa na tela o limite de 6 MB e permite que o usuário substitua o arquivo.

## Resultado obtido na gravação

A imagem selecionada apareceu na prévia. No salvamento, a API retornou HTTP 400 com “O arquivo deve ter no máximo 6 MB.” O diálogo mostrou apenas “Erro ao salvar configurações”. A prévia permaneceu na tela após fechar o diálogo.

| Tempo | Registro |
| --- | --- |
| 0:00–0:08 | Seleciona o logo e a tela mostra a nova prévia. |
| 0:09,38–0:09,40 | Aciona Salvar Configurações. A API recusa o tamanho e a tela mostra o diálogo genérico. |
| 0:15,20 | Fecha o diálogo. A prévia ainda aparece no formulário. |

**Rede:**

- 0:09,40  POST `/api/configuracoes/alterar/1` em multipart, corpo de 10.081.448 bytes conforme o Jam. HTTP 400 com “O arquivo deve ter no máximo 6 MB.”

**Conclusão:** Reprovado nas evidências. O total em bytes corresponde à requisição inteira. O tamanho exato do arquivo e o logo armazenado após recarregar não ficaram demonstrados.

## Critérios de aceitação para nova execução

1. A API recusa o arquivo acima do limite.
2. A interface informa o tamanho máximo permitido na recusa.
3. O usuário consegue substituir o arquivo e tentar salvar novamente.

## Próxima ação e verificações complementares

Retestar com arquivos de tamanho conhecido no entorno do limite e confirmar a mensagem de validação e a preservação do logo salvo na recusa.

## Evidências e limites

- [Jam 5 — Rejeição de logo pelo limite de tamanho](https://jam.dev/c/7aaeac50-8269-4cd6-b7f6-4c8c3740b0e5).
- [Arquivos, origem e limites](../Evidencias/CT-RF149_Configuracoes_Design_Logo_Limite_Tamanho/README.md).
- [Prévia da imagem selecionada no cartão Logo](../Evidencias/CT-RF149_Configuracoes_Design_Logo_Limite_Tamanho/previa_logo_00-08.jpg), [Diálogo genérico após a rejeição pela API](../Evidencias/CT-RF149_Configuracoes_Design_Logo_Limite_Tamanho/erro_generico_ao_salvar_00-12.jpg).
- [Linha do tempo](../Evidencias/CT-RF149_Configuracoes_Design_Logo_Limite_Tamanho/linha_do_tempo.txt).

A revisão documental se baseia nos quadros do vídeo e nos eventos capturados pelo Jam. As verificações complementares ficam para uma nova rodada de testes.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf141) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
