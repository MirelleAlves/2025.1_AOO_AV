## Diagrama de Estado — Histórico de Manutenção
Estados:

Criado: Registro inicial criado automaticamente ou por usuário.

AguardandoConfirmação: Pendência de validação.

Confirmado: Registro validado.

Editado: Sofreu alguma edição.

Arquivado: Não mais ativo, mas fechado como histórico.

Removido: Apagado do sistema.
```plantuml
@startuml
[*] --> Criado

Criado --> AguardandoConfirmacao : Dados aguardando validação do usuário ou sistema
AguardandoConfirmacao --> Confirmado : Validação concluída com sucesso
Confirmado --> Editado : Modificação feita manualmente
Editado --> Confirmado : Nova validação concluída
Confirmado --> Arquivado : Veículo vendido ou item não mais relevante
Criado --> Removido : Remoção antes da confirmação
AguardandoConfirmacao --> Removido : Dados inválidos ou inconsistentes

@enduml
```
