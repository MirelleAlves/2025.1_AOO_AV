## Diagrama de Atividade: Cadastro de Veículo

- Cadastro de múltiplos veículos por usuário.  
- Campos obrigatórios: marca, modelo, ano, combustível, quilometragem atual, placa.  
- Validação de placa (formatos Mercosul e antigo).  
- Prevenção de placas duplicadas.  




```puml
@startuml
start

:Usuário (proprietário) acessa a tela de "Cadastro de Veículo";
:Sistema identifica o usuário logado;

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
    :Usuário corrige os dados e reenviá-los;
    -> :Usuário preenche os dados e envia o formulário;
  else (Não)
    :Sistema cadastra o veículo;
    :Sistema associa o usuário logado como proprietário ao veículo;

    :Usuário envia documentação do veículo;
    :Sistema valida e armazena a documentação;

    :Sistema confirma cadastro com sucesso;
    stop
  endif

else (Não)
  :Sistema exibe mensagem de erro: "Formato de placa inválido";
  :Usuário corrige os dados e reenviá-los;
  -> :Usuário preenche os dados e envia o formulário;
endif

@enduml

```
