# Alertas Inteligentes

- Geração de alertas por tempo e quilometragem.  
- Notificações para todos os motoristas vinculados.  
- Sugestões automáticas com base no histórico de manutenções.  
- Cálculo dinâmico de alertas.



```puml
@startuml
start

:Sistema calcula tempo e quilometragem desde última manutenção;

if (Critérios para alerta atingidos?) then (Sim)
  :Sistema gera alerta;

  :Sistema envia notificação a todos os motoristas vinculados;

  :Sistema sugere manutenção com base no histórico;

else (Não)
  :Nenhuma ação necessária;
endif

:Sistema recalcula alertas dinamicamente;

stop
@enduml
```
