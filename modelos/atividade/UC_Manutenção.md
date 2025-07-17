## Diagrama de Atividade: Manutenções do veículo

- Registro de tipo de serviço, data, quilometragem, oficina, valor e observações.  
- Upload de nota fiscal com leitura automática (OCR).  
- Edição e exclusão com rastreamento do autor. 



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

:Usuário faz upload da nota fiscal;

:Sistema processa nota com OCR (leitura automática);

:Sistema armazena os dados e arquivo da nota;

:Usuário pode editar ou excluir registro;

:Sistema rastreia e armazena autor das alterações;

stop
@enduml
```
