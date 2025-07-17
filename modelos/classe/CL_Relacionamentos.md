# Diagrama de Classes: Relacionamentos  
- Definição clara das associações entre usuários, veículos e demais entidades do sistema;  
- Um usuário pode possuir vários veículos;  
- Cada veículo pode ter múltiplas manutenções, alertas, despesas, históricos e checklists de viagem;  
- Compartilhamento de veículos permite controle de acessos entre usuários;  
- Histórico pode ser gerado ou editado por usuários vinculados;  
- Estrutura facilita rastreamento, controle de permissões e organização dos dados.

```puml
@startuml
!theme mars

!include Usuario.puml
!include Veiculo.puml
!include Manutencao.puml
!include Alerta.puml
!include Despesa.puml
!include Historico.puml
!include Compartilhamento.puml
!include ChecklistViagem.puml

Usuario "1" -- "0..*" Veiculo : possui
Veiculo "1" -- "0..*" Manutencao : possui
Veiculo "1" -- "0..*" Alerta : possui
Veiculo "1" -- "0..*" Despesa : possui
Veiculo "1" -- "0..*" Historico : possui
Veiculo "1" -- "0..*" ChecklistViagem : possui
Usuario "1" -- "0..*" Compartilhamento : convida
Veiculo "1" -- "0..*" Compartilhamento : é compartilhado
Usuario "1" -- "0..*" Historico : gera/edita

@enduml
```
