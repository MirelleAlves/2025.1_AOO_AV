## Diagrama de Atividade: Manutenções do veículo

- Registro de tipo de serviço, data, quilometragem, oficina, valor e observações.  
- Opção de upload de nota fiscal durante o registro.  
- Armazenamento dos dados e arquivo da nota fiscal, se enviado.  
- Registro do usuário logado responsável pelo cadastro.


```puml
@startuml
start

:Usuário acessa "Registrar Manutenção";

:Sistema exibe campos:
- Tipo de serviço
- Data
- Quilometragem
- Oficina
- Valor
- Observações;

:Usuário preenche dados;

:Usuário faz upload da nota fiscal?;

if (Nota fiscal enviada?) then (Sim)
  :Sistema armazena dados e arquivo da nota;
else (Não)
  :Sistema armazena dados sem nota fiscal;
endif

:Sistema registra usuário logado responsável;

stop
@enduml

```
