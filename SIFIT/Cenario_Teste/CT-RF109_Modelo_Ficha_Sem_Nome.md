# 🧪 Cenário 109: Bloquear cadastro de modelo de ficha sem nome

**Caso de teste:** CT-RF109

**Módulo:** Treinamento / Modelos de Ficha / Cadastro

**Status:** Aprovado conforme a gravação.

**Gravação:** 16/11/2026, 22:19:51 BRT. **Revisão documental:** 17/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Impedir a criação de um modelo quando o campo Nome do Modelo estiver vazio e informar como corrigir o preenchimento. |
| Requisito | [RF109](../Analise%20de%20requisitos.md#rf109) — referência de QA. Confirmação de produto pendente. |
| Tipo / prioridade | Funcional manual / teste negativo · Média, proposta para triagem. |
| Defeito | Nenhum no fluxo avaliado |
| Encaminhamento | Usar como regressão e verificar nome composto apenas por espaços e submissão com todos os campos vazios. |
| Fonte | [Jam — Modelos de Ficha (PED-25)](https://jam.dev/c/fb5673c9-3cd1-46c4-88f4-d5fb32574a8e) e [evidências locais](../Evidencias/CT-RF109_Modelo_Ficha_Sem_Nome/README.md). |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/fichas-treino-modelo |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.79 / Windows 10 (x86), conforme os metadados do Jam. |
| Tela / arquivo de vídeo | 1536 × 799 informados no Jam. Vídeo em 1918 × 998. |
| Duração | 18,91 s |
| Localização | Brasil. |
| Versão / zoom / classificação do ambiente | A confirmar antes de nova execução. |
| Dados | Nome do Modelo vazio e um personal selecionado. |

## Pré-condições

- Sessão autenticada com permissão de cadastro e pelo menos um personal disponível.
- Identificar a versão e preparar a captura da listagem, do formulário ou dos filtros e dos eventos de rede pertinentes.

## Cenário BDD

```gherkin
Cenário: Bloquear cadastro de modelo de ficha sem nome
  Dado que o formulário Novo Modelo de Ficha está aberto com um personal selecionado
  Quando o usuário acionar Criar Modelo com o Nome do Modelo em branco
  Então o sistema deve bloquear o cadastro e informar que o nome precisa ser preenchido
  E o formulário deve permanecer disponível para correção
```

## Passos para execução ou reteste

1. Abrir Modelos de Ficha e clicar no botão de adição.
2. Selecionar um personal e deixar Nome do Modelo em branco.
3. Clicar em Criar Modelo e registrar o aviso, a listagem e os eventos de rede.
4. Fechar o aviso com Entendi e verificar se é possível corrigir o nome.

Este procedimento orienta a próxima execução. O resultado abaixo se limita ao trecho registrado no Jam.

## Resultado esperado

O sistema exibe um aviso de nome obrigatório, mantém o formulário disponível para correção e não cria um modelo.

## Resultado obtido na gravação

Após o clique em Criar Modelo, a tela exibiu o aviso “Informe o nome do modelo.” Ao clicar em Entendi, o formulário permaneceu aberto com o personal selecionado. A captura não registrou requisições de rede durante a tentativa.

| Tempo | Registro |
| --- | --- |
| 0:03–0:11 | Abre Novo Modelo de Ficha e seleciona um personal enquanto mantém o nome vazio. |
| 0:12–0:13 | Aciona Criar Modelo e recebe o aviso de nome obrigatório. |
| 0:15–0:18 | Fecha o aviso com Entendi. O formulário permanece aberto. |

**Rede:** Nenhuma requisição de rede capturada durante o trecho, incluindo o clique em Criar Modelo.

**Conclusão:** Aprovado conforme a gravação. A gravação cobre o nome vazio com um personal selecionado. Entrada composta apenas por espaços, envio com todos os campos vazios e validação no servidor exigem verificação própria.

## Critérios de aceitação para nova execução

1. O aviso identifica que o Nome do Modelo precisa ser preenchido.
2. Nenhum modelo é criado com nome vazio.
3. Após fechar o aviso, o formulário está disponível para corrigir o preenchimento.

## Próxima ação e verificações complementares

Usar como regressão e verificar nome composto apenas por espaços e submissão com todos os campos vazios.

## Evidências e limites

- [Jam original — PED-25](https://jam.dev/c/fb5673c9-3cd1-46c4-88f4-d5fb32574a8e).
- [Arquivos, origem e limites](../Evidencias/CT-RF109_Modelo_Ficha_Sem_Nome/README.md).
- [Aviso de nome obrigatório em 0:13](../Evidencias/CT-RF109_Modelo_Ficha_Sem_Nome/aviso_nome_obrigatorio_00-13.jpg), [Formulário após fechar o aviso em 0:17](../Evidencias/CT-RF109_Modelo_Ficha_Sem_Nome/formulario_apos_aviso_00-17.jpg).
- [Linha do tempo](../Evidencias/CT-RF109_Modelo_Ficha_Sem_Nome/linha_do_tempo.txt).

Foram consultados os metadados, os eventos de rede e de interação e os quadros do vídeo. Os recortes estão na pasta de evidências. O vídeo permanece no Jam.

A revisão documental de 17/11/2026 registra a execução gravada. As verificações complementares ficam para uma nova rodada de testes.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md#rf109) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
