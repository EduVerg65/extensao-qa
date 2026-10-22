## Riscos e Limitações do Ambiente

| ID | Risco | Impacto | Mitigação |
|---|---|---|---|
| R01 | Limite de 500 conexões/hora no banco, compartilhado entre os usuários da turma | Interrupção da verificação de persistência durante a execução | Agrupar consultas em scripts únicos; registrar horário das execuções |
| R02 | Ambiente compartilhado com outros testadores | Dados alterados por terceiros podem invalidar evidências | Prefixar registros próprios; datar todas as evidências |