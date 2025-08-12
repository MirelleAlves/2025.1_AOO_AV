## Diagrama de Arquitetura

![Imagem do WhatsApp de 2025-08-08 à(s) 20 03 47_ad0d24ab](https://github.com/user-attachments/assets/67b2eadd-ef99-4b1b-a93e-e6d38b8ce37f)

``` puml
@startuml
skinparam componentStyle rectangle
top to bottom direction
skinparam ArrowColor #333
skinparam Shadowing false

' Cliente
component "Cliente\n(usuário / sistema que consome a API REST)" as Cliente

' Servidor com subcomponentes (agrupados)
package "Servidor de Aplicação (API)" {
  component "Inicialização / Configuração\n(startup, registro de rotas, DI)" as Init
  component "Roteadores / Endpoints\n(recebem requisições HTTP)" as Routes
  component "Validação & Parsing\n(validação inline nos endpoints)" as Validation
  component "Controladores\n(orquestram fluxo por endpoint)" as Controllers
  component "Serviços de Negócio\n(regras e coordenação de operações)" as Services
  component "Repositório / Acesso a Dados\n(queries, transações, persistência)" as Repos
  component "Logs & Monitoramento\n(registro de erros e métricas)" as Logs
  component "Tarefas em Background \n(job scheduling, tarefas assíncronas)" as Background
}

' Banco de dados
database "Armazenamento Persistente\n(Banco relacional)" as DB

' Fluxo principal (vertical)
Cliente --> Routes : Requisição HTTP (JSON)
Routes --> Validation : Parse e validação dos dados
Validation --> Routes : Erro 4xx (validação falhou)
Validation --> Controllers : Dados validados
Controllers --> Services : Chama regras de negócio
Services --> Repos : Operações CRUD / transação
Repos --> DB : Consultas / atualizações (SQL)
Services --> Controllers : Resultado / erros de negócio
Controllers --> Routes : Prepara resposta
Routes --> Cliente : Resposta HTTP (JSON)

' Observability & background
Controllers --> Logs : Eventos / erros
Repos --> Logs : Exceções / queries lentas
Background --> Repos : Operações assíncronas 
Background --> Logs : Registros de execução

' Inicialização
Init --> Routes : Registra endpoints / middlewares
Init --> Background : Inicializa agendadores

' Autenticação/Autorização 
component "Autenticação / Autorização\n(middleware / verificação de tokens)" as Auth
Routes ..> Auth : Verifica credenciais / permissões
Auth ..> Logs : Registra tentativas

' Notas explicativas
note left of Routes
  Endpoints: recebem requisições HTTP e delegam para controllers.
  A validação é feita inline nos endpoints antes de processar.
end note

note right of Services
  Serviços encapsulam regras de negócio e validam
  regras transversais (consistência, fluxos maiores).
end note

note right of Repos
  Repositório: camada responsável por consultas,
  mapeamento e operações transacionais no banco.
end note

note right of DB
  Banco relacional para persistência dos dados.
  Pode ser arquivo local ou servidor remoto.
end note

note bottom of Logs
  Logs & Monitoramento: centraliza alarmes, erros e métricas.
end note
@enduml

``
