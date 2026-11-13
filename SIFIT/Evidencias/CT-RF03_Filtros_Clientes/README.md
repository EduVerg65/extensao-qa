# 📸 Evidências — CT-RF03: Filtros da página Clientes

**Sistema:** SIFIT

**Caso:** [CT-RF03](../../Cenario_Teste/CT-RF03_FILTRO_TelaClientes.md)

**Defeito:** [BUG-003](../../Relatorio-de-Bugs.md#bug-003--filtros-combinados-da-página-clientes-não-restringem-a-listagem)

**Organização documental:** 13/11/2026, a partir dos registros da revisão de 12/11/2026.

## 📁 Arquivos e origem

| Evidência | Origem registrada | Informação disponível |
| --- | --- | --- |
| [Captura 1](filtros-clientes-01.png) | Captura fornecida e descrita na documentação existente. | Filtros selecionados, listagem e uma entrada XHR HTTP 200; painel com 26,9 kB transferidos e 185 kB de recursos. Não mostra payload ou URL completa. |
| [Captura 2](filtros-clientes-02.png) | Captura fornecida e descrita na documentação existente. | Filtros selecionados, listagem semelhante e painel Network sem requisições listadas naquele instante. |
| [Jam — gravação fornecida](https://jam.dev/c/657627ec-e7e2-455d-a505-9b2a26f44bf1) | Link informado pelo solicitante. | Conteúdo sem consulta direta na revisão registrada; detalhes de rede transcritos do relato. |

Os arquivos de imagem foram mantidos sem alterações nesta padronização. A descrição acima reproduz as observações já documentadas nos cenários e relatórios.

---

## 🌐 Cronologia de rede informada

O relato atribui à gravação três chamadas a `POST https://backendsifit.centrion.com.br/api/clientesPorNome/1`:

| Momento aproximado | Status informado | Volume de resposta informado |
| --- | --- | --- |
| 00:05 | HTTP 200 | 180,9 KB |
| 00:20 | HTTP 200 | 180,9 KB |
| 00:28 | HTTP 200 | 180,9 KB |

Esses dados têm origem no relato e não foram extraídos diretamente do Jam nesta atualização. Não foi estabelecida a correspondência exata entre cada chamada e a situação financeira selecionada.

### Corpo simplificado informado

Transcrição sem autenticação; não representa uma exportação HAR nem o corpo integral capturado:

```json
{
  "empresa_id": 1,
  "nome": ""
}
```

Status, Situação Financeira, Plano e Personal não aparecem nesse corpo simplificado. É necessário verificar o código e o contrato da API para determinar como os critérios devem ser aplicados.

## 🔎 Limites das evidências

- Os textos dos filtros aparecem truncados nas capturas, e os vínculos individuais dos clientes não estão visíveis; as imagens não comprovam isoladamente a incompatibilidade de cada registro.
- O painel sem requisições na captura 2 não comprova ausência de chamadas durante toda a execução.
- As métricas visíveis na captura 1 não foram tratadas como equivalentes ao volume atribuído às chamadas do Jam.
- HTTP 200 não demonstra aplicação correta dos filtros; volumes semelhantes não comprovam respostas idênticas.
- Não foram fornecidos HAR, respostas integrais ou cadastros de referência. URL do frontend, data da gravação e versão da aplicação permanecem não confirmadas.
- A causa técnica e os IDs das opções não estão confirmados. A matriz de reteste permanece pendente; esta organização não acrescenta nova execução.

---

[← Caso de teste](../../Cenario_Teste/CT-RF03_FILTRO_TelaClientes.md) · [Relatório dos testes](../../Relatorio%20dos%20testes.md) · [Início](../../../README.md)
