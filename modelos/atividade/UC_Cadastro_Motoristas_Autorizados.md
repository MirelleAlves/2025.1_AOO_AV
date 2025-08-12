## Diagrama de Atividade: Cadastro de Motoristas Autorizados

- Permite ao usuário logado associar motoristas previamente cadastrados ao seu veículo.  
- Exibe lista de motoristas disponíveis para seleção.  
- Valida se o motorista selecionado já está vinculado ao veículo, prevenindo duplicidades.  
- Em caso de motorista já autorizado, exibe mensagem de erro e encerra o processo.  
- Se validado, associa o(s) motorista(s) ao veículo e confirma a operação com sucesso.


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
