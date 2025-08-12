# Diagrama de Casos de Uso - Visão Geral do Sistema REVISAÍ

Este diagrama apresenta a visão geral dos casos de uso do sistema REVISAÍ, mostrando os atores principais, os casos de uso e as interações entre eles.

Ele complementa os documentos individuais de cada caso de uso, que detalham os fluxos, regras de negócio e validações específicas.

<img width="480" height="1014" alt="casodeuso" src="https://github.com/user-attachments/assets/c19dc214-f57c-4274-b76a-78abea25e88c" />


```puml
@startuml
left to right direction
skinparam packageStyle rectangle

actor "Visitante" as Visitante
actor "Usuário" as Usuario
actor "Proprietário" as Proprietario
actor "Sistema" as Sistema

rectangle "Sistema REVISAÍ" {

  usecase "Cadastrar Usuário" as UC2
  usecase "Login" as UC1
  usecase "Cadastrar Veículo" as UC4
  usecase "Registrar Documentação" as UC3
  usecase "Compartilhar Veículo" as UC5
  usecase "Associar Motorista ao Veículo" as UC5_1
  usecase "Registrar Manutenção" as UC6
  usecase "Emitir Relatórios e Histórico" as UC7
  usecase "Atualizar Quilometragem" as UC8
  usecase "Registrar Despesas" as UC9
  usecase "Fazer Checklist de Viagem" as UC10
  usecase "Gerar Alertas Inteligentes" as UC11

  Visitante --> UC2
  Visitante --> UC1

  Usuario --> UC1
  Usuario --> UC4
  Usuario --> UC5
  Usuario --> UC6
  Usuario --> UC7
  Usuario --> UC8
  Usuario --> UC9
  Usuario --> UC10

  Proprietario --> UC5_1
  Proprietario --> UC5

  Sistema --> UC11

  UC2 .> UC3 : <<include>>
  UC4 .> UC3 : <<include>>

  UC6 .> UC4 : <<include>> : "Selecionar veículo"
  UC7 .> UC4 : <<include>> : "Selecionar veículo"
  UC8 .> UC4 : <<include>> : "Selecionar veículo"
  UC9 .> UC4 : <<include>> : "Selecionar veículo"
  UC10 .> UC4 : <<include>> : "Selecionar veículo"

  UC5_1 .> UC4 : <<include>> : "Selecionar veículo"

  UC5_1 .> UC5 : <<extend>>

}

@enduml
``
