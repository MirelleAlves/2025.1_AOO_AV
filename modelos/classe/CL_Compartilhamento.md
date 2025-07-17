# Diagrama de Classes: Compartilhamento de Veículo  
- Compartilhamento por e-mail ou código de convite;  
- Controle de permissões (visualização ou edição);  
- Remoção de acesso a qualquer momento;  
- Notificações de alterações feitas por convidados;  
- Transferência de propriedade.

```puml
@startuml
!theme mars

class Compartilhamento {
    -id: UUID
    -veiculoId: UUID
    -usuarioConvidadoId: UUID
    -permissao: Enum (VISUALIZACAO, EDICAO)
    -codigoConvite: String
    -status: Enum (PENDENTE, ACEITO, REVOGADO)
    +compartilharPorEmail()
    +gerarCodigoConvite()
    +removerAcesso()
    +transferirPropriedade()
}

@enduml
```
