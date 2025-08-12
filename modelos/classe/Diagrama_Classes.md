## Descrição do Diagrama de Classes Geral

Este diagrama apresenta uma visão integrada das principais classes do sistema, detalhando seus atributos, métodos e relacionamentos.

- **Usuário**: representa o usuário do sistema, com dados pessoais, tipo de login e permissões. Inclui métodos para cadastro, autenticação, recuperação e gestão da conta.  
- **Veículo**: contém as informações essenciais do veículo, vinculado a um usuário proprietário, e métodos para gerenciar seus dados e quilometragem.  
- **Manutenção**: registra serviços realizados no veículo, incluindo detalhes como tipo de serviço, quilometragem, oficina, valor e documentação digital (nota fiscal).  
- **Alerta**: gerencia notificações relacionadas ao veículo, como alertas baseados em tempo ou quilometragem, com métodos para controlar o ciclo do alerta.  
- **Despesa**: registra despesas associadas ao veículo, com informações detalhadas e comprovantes digitais.  
- **Histórico**: mantém um registro das ações e eventos do veículo, categorizados por tipo, com suporte a consultas e geração de relatórios.  
- **Checklist de Viagem**: lista de itens a serem verificados antes de viagens, com funcionalidades para personalização e registro de conclusão.  
- **Compartilhamento**: gerencia o compartilhamento do veículo entre usuários, definindo permissões e status dos convites.

As relações entre as classes são cuidadosamente definidas para representar a posse e associações necessárias, como a ligação entre usuário e veículos, veículos e suas manutenções, alertas, despesas, histórico e checklists, bem como o compartilhamento entre usuários.


```puml
@startuml
!theme mars

class Usuario {
    -id: UUID
    -nomeCompleto: String
    -email: String
    -senhaHash: String
    -tipoLogin: Enum (TRADICIONAL, GOOGLE)
    -permissao: Enum (BASICO, PREMIUM, CORPORATIVO)
    +cadastrar()
    +autenticar()
    +recuperarSenha()
    +editarConta()
    +excluirConta()
}

class Veiculo {
    -id: UUID
    -marca: String
    -modelo: String
    -ano: Integer
    -tipoCombustivel: String
    -quilometragemAtual: Long
    -placa: String
    -proprietarioId: UUID
    +cadastrar()
    +editar()
    +excluir()
    +atualizarQuilometragem(novaKm: Long)
}

class Manutencao {
    -id: UUID
    -tipoServico: String
    -data: Date
    -quilometragem: Long
    -oficina: String
    -valor: Double
    -observacoes: String
    -notaFiscalUrl: String
    -autorId: UUID
    -veiculoId: UUID
    +registrar()
    +editar()
    +excluir()
    +lerNotaFiscalOCR()
}

class Alerta {
    -id: UUID
    -tipo: Enum (TEMPO, QUILOMETRAGEM, COMBINADO)
    -dataAlvo: Date
    -quilometragemAlvo: Long
    -descricao: String
    -status: Enum (ATIVO, CONCLUIDO, ADIADO, CANCELADO)
    -veiculoId: UUID
    -autorId: UUID
    +gerar()
    +notificar()
    +confirmar()
    +ajustarParametros()
    +marcarComoConcluido()
    +adiar()
    +cancelar()
}

class Despesa {
    -id: UUID
    -tipo: String
    -data: Date
    -valor: Double
    -descricao: String
    -categoria: String
    -comprovanteUrl: String
    -veiculoId: UUID
    -autorId: UUID
    +registrar()
    +editar()
    +excluir()
}

class Historico {
    -id: UUID
    -dataRegistro: Date
    -tipoRegistro: Enum (MANUTENCAO, DESPESA, ATUALIZACAO_KM, CHECKLIST)
    -detalhes: String
    -veiculoId: UUID
    -autorId: UUID
    +consultar()
    +filtrar()
    +gerarRelatorioPDF()
}

class ChecklistViagem {
    -id: UUID
    -tipoViagem: String
    -dataGeracao: Date
    -itens: List<String>
    -status: Enum (PENDENTE, CONCLUIDO)
    -veiculoId: UUID
    -autorId: UUID
    +gerarSugestao()
    +personalizar()
    +exportarPDF()
    +marcarItemVerificado()
    +registrarConclusao()
}

class Compartilhamento {
    -id: UUID
    -veiculoId: UUID
    -usuarioConvidadoId: UUID
    -permissao: Enum (VISUALIZACAO, EDICAO)
    -codigoConvite: String
    -status: Enum (PENDENTE, ACEITO, REVOGADO)
    +compartilharPorEmail()
    +gerarCodigoConvite()
    +removerAcesso()
    +transferirPropriedade()
}

' Relacionamentos

Usuario "1" -- "0..*" Veiculo : possui
Veiculo "1" -- "0..*" Manutencao : possui
Veiculo "1" -- "0..*" Alerta : possui
Veiculo "1" -- "0..*" Despesa : possui
Veiculo "1" -- "0..*" Historico : possui
Veiculo "1" -- "0..*" ChecklistViagem : possui
Usuario "1" -- "0..*" Compartilhamento : convida
Veiculo "1" -- "0..*" Compartilhamento : é compartilhado
Usuario "1" -- "0..*" Historico : gera/edita

@enduml
``
