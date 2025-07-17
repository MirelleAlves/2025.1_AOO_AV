## Diagrama de Atividade: Emitir Relatório/Histórico

- Histórico completo por veículo.  
- Filtros por motorista, serviço, oficina e datas.  
- Relatórios promocionais e exportação em PDF.  
- Geração de relatório de entrega de veículo.



```puml
@startuml
start

:Usuário acessa "Histórico e Relatórios";

:Sistema exibe filtros:
- Motorista
- Serviço
- Oficina
- Datas;

:Usuário aplica filtros;

:Sistema exibe histórico completo do veículo;

:Usuário solicita geração de relatório;

if (Tipo de relatório: promocional ou entrega?) then (Entrega)
  :Sistema gera relatório de entrega de veículo em PDF;
else (Promocional)
  :Sistema gera relatório promocional em PDF;
endif

:Usuário faz download do PDF;

stop
@enduml
```
