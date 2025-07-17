## Diagrama de Atividade: Compartilhar Veículo

- Compartilhamento via e-mail ou código de convite.  
- Controle de permissões (visualização ou edição).  
- Remoção de acesso a qualquer momento.  
- Notificações de alterações feitas por convidados.  
- Transferência de propriedade do veículo.



```puml
@startuml
start

:Usuário acessa a opção "Compartilhar Veículo";

:Sistema exibe opções:
- Compartilhar via e-mail
- Compartilhar via código de convite;

:Usuário escolhe a forma de compartilhamento;

if (Via e-mail?) then (Sim)
  :Usuário informa o e-mail do convidado;
  :Sistema envia convite com link de acesso;
else (Via código)
  :Sistema gera código de convite;
  :Usuário compartilha o código com o convidado;
endif

:Usuário define permissão:
- Visualização
- Edição;

:Sistema associa permissão ao convidado;

:Convidado aceita o convite;

:Sistema concede o acesso conforme permissão;

:Sistema ativa notificações de alterações ao proprietário;

:Usuário deseja transferir a propriedade?;

if (Sim)
  :Usuário seleciona novo proprietário;
  :Sistema transfere a propriedade;
  :Novo proprietário recebe notificação;
else (Não)
  :Sistema mantém a propriedade original;
endif

:Usuário pode remover acesso de qualquer convidado a qualquer momento;

stop
@enduml
```
