## Diagrama de Estado - Veículo
Mostra os estados de um veículo no sistema, desde o cadastro até o compartilhamento, transferência ou exclusão.

Estados:

Cadastrado: Veículo registrado no sistema por um usuário.

Compartilhado: Veículo acessível por outros usuários autorizados.

Transferido: Propriedade do veículo alterada para outro usuário.

Excluído: Veículo removido do sistema.

```plantuml
@startuml
title Diagrama de Estados - Veículo

[*] --> Cadastrado

Cadastrado --> Compartilhado : compartilharVeiculo()
Compartilhado --> Cadastrado : removerCompartilhamento()
Cadastrado --> Transferido : transferirPropriedade()
Compartilhado --> Transferido : transferirPropriedade()
Cadastrado --> Excluido : excluirVeiculo()
Compartilhado --> Excluido : excluirVeiculo()

Excluido --> [*]
Transferido --> [*]
@enduml
```
