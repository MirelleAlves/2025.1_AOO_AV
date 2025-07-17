# Diagrama de Classes: Veículo  
- Cadastro de múltiplos veículos por usuário;  
- Campos obrigatórios: marca, modelo, ano, tipo de combustível, quilometragem atual, placa;  
- Validação de placa nos formatos Mercosul e antigo;  
- Prevenção de duplicidade de placa;  
- Indicação de proprietário e motoristas autorizados;  
- Edição e exclusão de veículos com controle de permissões.

```puml
@startuml
!theme mars

class Veiculo {
    -id: UUID
    -marca: String
    -modelo: String
    -ano: Integer
    -tipoCombustivel: String
    -quilometragemAtual: Long
    -placa: String
    -proprietarioId: UUID
    +cadastrar()
    +editar()
    +excluir()
    +atualizarQuilometragem(novaKm: Long)
}

@enduml
```

# Diagrama de Seguência - Cadastrar veículo

```puml
@startuml
actor Usuario
entity "Sistema" as Sistema
entity "Banco de Dados" as BD

Usuario -> Sistema: Envia dados do veículo (marca, modelo, placa, etc.)
Sistema -> Sistema: Valida formato e duplicidade de placa
alt Placa válida
    Sistema -> BD: Armazena dados do veículo
    Sistema -> Usuario: Exibe mensagem de sucesso
else Placa inválida
    Sistema -> Usuario: Exibe erro de placa inválida
end

== Adiciona motoristas autorizados ==
Usuario -> Sistema: Adiciona motoristas autorizados
Sistema -> BD: Armazena motoristas autorizados
Sistema -> Usuario: Exibe mensagem de sucesso

@enduml
```
