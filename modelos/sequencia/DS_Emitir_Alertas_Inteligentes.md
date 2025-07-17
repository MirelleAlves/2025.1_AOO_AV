# Diagrama de Sequência - Emitir Alertas Inteligentes

```puml
@startuml
actor Sistema
actor Usuario
entity "Banco de Dados" as BD

Sistema -> BD: Recupera dados do veículo (última quilometragem, manutenções)
Sistema -> Sistema: Aplica regras para gerar alertas (tempo, quilometragem)
Sistema -> Usuario: Envia notificação de alerta

alt Usuário confirma alerta
    Usuario -> Sistema: Confirma alerta
    Sistema -> BD: Armazena alerta
else Usuário ajusta alerta
    Usuario -> Sistema: Ajusta parâmetros (km, data, tipo de serviço)
    Sistema -> BD: Atualiza alerta
end
@enduml
```puml
