## Cadastro de Motoristas Autorizados


```puml
@startuml
start

:Usuário acessa a tela de "Gerenciar Motoristas Autorizados";
:Sistema lista motoristas disponíveis (usuários cadastrados);

:Usuário seleciona motoristas autorizados;
:Sistema valida se motoristas selecionados não estão já vinculados ao veículo;

if (Motorista já autorizado?) then (Sim)
  :Sistema exibe mensagem de erro: "Motorista já vinculado";
  stop
else (Não)
  :Sistema associa motoristas ao veículo;
  :Sistema confirma vinculação com sucesso;
  stop
endif

@enduml
``
