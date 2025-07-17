## Diagrama de Estado — Usuário
Estados:

Cadastrado: Usuário concluiu o processo de cadastro, mas ainda não está ativo.

Ativo: Usuário autenticado e utilizando o sistema normalmente.

Inativo: Conta desativada temporariamente.

Bloqueado: Conta impedida de acesso por razões administrativas.

Removido: Conta encerrada permanentemente.
```plantuml
@startuml
[*] --> Cadastrado

Cadastrado --> Ativo : Verificação concluída com sucesso
Ativo --> Inativo : Usuário desativa a conta
Inativo --> Ativo : Reativação da conta
Ativo --> Bloqueado : Violação de termos / Denúncias
Bloqueado --> Ativo : Recurso aceito ou reabilitação manual
Cadastrado --> Bloqueado : Detecção de fraude ou erro grave no cadastro
Bloqueado --> Removido : Conta encerrada definitivamente
Inativo --> Removido : Exclusão definitiva a pedido do usuário
Cadastrado --> Removido : Cadastro incompleto não confirmado após X dias

@enduml
```
