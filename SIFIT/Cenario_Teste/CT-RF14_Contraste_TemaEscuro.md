# 🧪 Cenário 14: Baixa legibilidade no tema escuro de Box – Turmas

**Caso de teste:** CT-RF14

**Módulo:** SifitBox / Turmas / Tema

**Status:** Reprovado nas evidências.

**Gravação:** 14/11/2026, 00:37:16 BRT. **Revisão documental:** 14/11/2026.

## Objetivo e rastreabilidade

| Campo | Descrição |
| --- | --- |
| Objetivo | Preservar a legibilidade das tabelas no tema escuro. |
| Requisito | [RF14](../Analise%20de%20requisitos.md#rf14) |
| Tipo / prioridade | Funcional manual, análise de evidências / Média, proposta para triagem. |
| Defeito | [BUG-007](../Relatorio-de-Bugs.md#bug-007) |
| Encaminhamento | Aberto; reteste pendente após correção. |
| Fonte | [Jam — falta de acessibilidade nas cores](https://jam.dev/c/6889db07-bed1-472b-8ec2-00402919cd65) |

## Ambiente e dados de teste

| Item | Registro |
| --- | --- |
| Página gravada | https://sifit.centrion.com.br/sifitbox/turmas |
| Backend de referência | https://backendsifit.centrion.com.br |
| Navegador / sistema | Chrome 157.0.8103.51 / Windows 11 (x86). |
| Tela / arquivo de vídeo | 1920 × 957 informados no Jam; original 1918 × 956 pixels. |
| Duração | 9,38 s |
| Versão / zoom / classificação do ambiente | Não confirmados; registrar antes de nova execução. |
| Dados | Usar dados de teste conhecidos conforme as pré-condições abaixo; valores da gravação são referência histórica, sem copiar credenciais. |

## Pré-condições

- Sessão autenticada com acesso a SifitBox – Turmas.
- Página com modalidades e turmas recorrentes cadastradas.
- Antes de uma nova execução, identificar versão, permissões e dados de referência e preparar a captura de interface e rede.

## Cenário BDD

```gherkin
Cenário: Preservar a legibilidade das tabelas no tema escuro
  Dado que o usuário está em "SifitBox – Turmas" no tema claro
  Quando selecionar o tema "Escuro"
  Então os textos de Modalidades e Turmas recorrentes devem permanecer legíveis
  E as cores de texto e fundo devem ser compatíveis entre si
```

## Passos para execução ou reteste

1. Registrar a apresentação das tabelas no tema Claro.
2. Selecionar Escuro.
3. Conferir títulos, nomes, status e ações sobre os fundos das duas tabelas.

Este procedimento orienta a próxima execução. A evidência atual cobre o trecho gravado e os limites descritos abaixo; passos complementares, como conferir downloads ou recarregar a sessão, não recebem resultado de execução nesta revisão.

## Resultado esperado

Aplicar cores de texto e de fundo que preservem a legibilidade em ambos os temas.

## Resultado obtido na gravação

As áreas de Modalidades e Turmas recorrentes permanecem brancas enquanto diversos textos ficam muito claros, dificultando sua leitura.

**Momentos e registros:** 0:02: seleção de Escuro e POST /api/usuario/tema com HTTP 200. 0:02–0:09: perda de legibilidade nas tabelas.

**Conclusão:** Reprovado nas evidências. O defeito associado descreve a manifestação observada, sem atribuir uma causa técnica não comprovada.

## Critérios de aceitação para nova execução

1. Nomes e demais textos permanecem legíveis ao alternar o tema.
2. Títulos, filtros, status e ações podem ser identificados nas duas tabelas.
3. Uma conclusão formal de acessibilidade depende de medição de contraste e do padrão acordado.

## Próxima ação e verificações complementares

Ajustar as cores e retestar ambos os temas; medir contraste se houver critério formal de acessibilidade definido.

O [BUG-007](../Relatorio-de-Bugs.md#bug-007) permanece aberto. Severidade **Média** e prioridade **Média** são propostas para triagem; encerrar somente após evidências de reteste em uma versão identificada.

## Evidências e limites

- [Jam original — falta de acessibilidade nas cores](https://jam.dev/c/6889db07-bed1-472b-8ec2-00402919cd65).
- [Vídeo original](../Evidencias/CT-RF14_Contraste_TemaEscuro/video.webm).
- [Resumo, origem e integridade](../Evidencias/CT-RF14_Contraste_TemaEscuro/README.md).
- [Cronologia do Jam](../Evidencias/CT-RF14_Contraste_TemaEscuro/linha_do_tempo.txt).

A observação é visual. Não foi medida a razão de contraste nem realizada uma auditoria formal de acessibilidade.

Análise documental das gravações já consultadas em 14/11/2026 (metadados, cronologia e quadros distribuídos pelo vídeo). Esta inclusão não executa novamente o sistema, não corrige a aplicação e não constitui reteste. Versão da aplicação, zoom e classificação do ambiente não foram confirmados.

---

[← Início](../../README.md) · [Requisitos](../Analise%20de%20requisitos.md) · [Plano de testes](../Plano%20de%20testes.md) · [Relatório dos testes](../Relatorio%20dos%20testes.md)
