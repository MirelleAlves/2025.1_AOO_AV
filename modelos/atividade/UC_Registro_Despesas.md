## Diagrama de Atividade: Registrar Despesas Gerais

- Registro de despesas como IPVA, seguro, multas, lavagens, etc.  
- Categorização das despesas.  
- Relatórios por mês, categoria e veículo.  



```puml
@startuml
start

:Usuário acessa "Registrar Despesa";

:Sistema exibe campos:
- Tipo de despesa (IPVA, seguro, multa, lavagem etc.)
- Valor
- Data
- Observações;

:Usuário preenche os dados;

:Sistema categoriza a despesa;

:Sistema armazena a despesa no registro do veículo;

:Usuário solicita relatórios;

:Sistema exibe relatórios por:
- Mês
- Categoria
- Veículo;

stop
@enduml
```
