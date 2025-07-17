# Diagrama de Classes: Despesa
- Registro de despesas com abastecimento, manutenção, pedágios e mais;  
- Classificação por categoria para controle financeiro;  
- Inclusão de comprovantes em imagem ou PDF;  
- Edição ou exclusão de lançamentos a qualquer momento;  
- Associação de cada despesa a um veículo específico.

```puml
@startuml
!theme mars

class Despesa {
    -id: UUID
    -tipo: String
    -data: Date
    -valor: Double
    -descricao: String
    -categoria: String
    -comprovanteUrl: String
    -veiculoId: UUID
    -autorId: UUID
    +registrar()
    +editar()
    +excluir()
}

@enduml
```
