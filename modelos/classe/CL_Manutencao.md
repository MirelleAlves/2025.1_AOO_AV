# Diagrama de Classes: Manutenção  
- Registro detalhado do tipo de serviço, data e quilometragem;  
- Informações da oficina, valor gasto e observações complementares;  
- Upload de nota fiscal com leitura automática via OCR;  
- Edição e exclusão dos registros com rastreamento do autor.

```puml
@startuml
!theme mars

class Manutencao {
    -id: UUID
    -tipoServico: String
    -data: Date
    -quilometragem: Long
    -oficina: String
    -valor: Double
    -observacoes: String
    -notaFiscalUrl: String
    -autorId: UUID
    -veiculoId: UUID
    +registrar()
    +editar()
    +excluir()
    +lerNotaFiscalOCR()
}

@enduml
```
