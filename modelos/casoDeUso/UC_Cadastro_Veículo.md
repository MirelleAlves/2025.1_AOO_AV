## Diagrama de Atividade: Cadastro de Veículo

- Cadastro de múltiplos veículos por usuário.  
- Campos obrigatórios: marca, modelo, ano, combustível, quilometragem atual, placa.  
- Validação de placa (formatos Mercosul e antigo).  
- Prevenção de placas duplicadas.  
- Indicação de proprietário e motoristas autorizados.  
- Edição e exclusão com controle de permissões.  



```puml
@startuml
start

:Usuário acessa a tela de "Cadastro de Veículo";

:Sistema exibe campos obrigatórios:
- Marca
- Modelo
- Ano
- Combustível
- Quilometragem atual
- Placa;

:Usuário preenche os dados e envia o formulário;

:Sistema valida formato da placa (Mercosul ou antigo);

if (Placa válida?) then (Sim)
  :Sistema verifica duplicidade da placa;

  if (Placa já cadastrada?) then (Sim)
    :Sistema exibe mensagem de erro: "Placa duplicada";
    stop
  else (Não)
    :Sistema cadastra o veículo;
    :Sistema associa o proprietário ao veículo;

    :Usuário escolhe adicionar motoristas autorizados?;

    if (Sim)
      :Usuário seleciona motoristas autorizados;
      :Sistema associa motoristas autorizados ao veículo;
    else (Não)
      note right
      Apenas o proprietário terá acesso inicialmente.
      end note
    endif

    :Sistema confirma cadastro com sucesso;
    stop
  endif

else (Não)
  :Sistema exibe mensagem de erro: "Formato de placa inválido";
  stop
endif

@enduml
```
