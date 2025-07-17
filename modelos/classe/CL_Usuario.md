# Diagrama de Classes: Usuário  
- Cadastro com nome completo, e-mail e senha;  
- Login via Google;  
- Recuperação de senha por e-mail;  
- Senha armazenada com hash seguro;  
- Edição e exclusão da conta.

```puml
@startuml
!theme mars

class Usuario {
    -id: UUID
    -nomeCompleto: String
    -email: String
    -senhaHash: String
    -tipoLogin: Enum (TRADICIONAL, GOOGLE)
    -permissao: Enum (BASICO, PREMIUM, CORPORATIVO)
    +cadastrar()
    +autenticar()
    +recuperarSenha()
    +editarConta()
    +excluirConta()
}

@enduml
```
