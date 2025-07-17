## Diagrama de Atividade: Cadastro de Usuário

- Cadastro com nome completo, e-mail e senha.  
- Login via conta Google.  
- Recuperação de senha por e-mail.  
- Senhas armazenadas com hash seguro.  
- Edição e exclusão de conta.  



```puml
@startuml
start

:Usuário acessa a tela de "Cadastro";

if (Usuário escolhe "Recuperar Senha"?) then (Sim)
  :Sistema solicita o e-mail;
  :Usuário informa o e-mail;

  :Sistema verifica se o e-mail está cadastrado;

  if (E-mail cadastrado?) then (Sim)
    :Sistema envia link de recuperação de senha por e-mail;
    :Usuário segue o link para redefinir a senha;
    stop
  else (Não)
    :Sistema exibe mensagem de erro: "E-mail não encontrado";
    stop
  endif

else (Não)

  :Sistema exibe campos:
  - Nome completo
  - E-mail
  - CPF
  - Senha (mínimo 8 caracteres, validação);

  :Usuário preenche os dados e envia o formulário;

  if (Usuário escolhe "Entrar com Google"?) then (Sim)
    :Sistema redireciona para autenticação via OAuth;
    :Usuário autoriza o acesso;
    :Sistema cria ou acessa conta vinculada ao e-mail do Google;
    :Usuário é redirecionado para a tela inicial logado;
    stop
  else (Não)
    :Sistema verifica se o e-mail já está cadastrado;

    if (E-mail já cadastrado?) then (Sim)
      :Sistema exibe mensagem de erro;
      :Impede o cadastro duplicado;
      stop
    else (Não)
      :Sistema verifica se o CPF já está cadastrado;

      if (CPF já cadastrado?) then (Sim)
        :Sistema exibe mensagem de erro;
        :Impede o cadastro duplicado;
        stop
      else (Não)
        :Sistema armazena os dados com criptografia de senha (hash);
        :Sistema cria o registro de usuário;
        :Usuário é redirecionado para a tela inicial logado;
        stop
      endif
    endif
  endif
endif

@enduml
```
