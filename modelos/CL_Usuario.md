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

# Diagrama de Sequência - Cadastrar usuário

```puml
@startuml
actor Usuario
entity "Sistema" as Sistema
entity "Banco de Dados" as BD
entity "Autenticação Google" as Google

Usuario -> Sistema: Envia dados (nome, e-mail, senha)
Sistema -> BD: Verifica duplicidade de e-mail
alt E-mail não cadastrado
    Sistema -> BD: Criptografa senha e armazena dados
    Sistema -> Usuario: Redireciona para tela inicial
else E-mail já cadastrado
    Sistema -> Usuario: Exibe erro de duplicidade
end

== Cadastro via Google ==
Usuario -> Sistema: Escolhe "Entrar com Google"
Sistema -> Google: Solicita autenticação OAuth
Google -> Sistema: Autenticação confirmada
Sistema -> BD: Cria ou acessa conta Google
Sistema -> Usuario: Redireciona para tela inicial

@endum
```
