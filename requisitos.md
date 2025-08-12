# 📃 Requisitos do Sistema — Versão Ajustada

## 🧑‍💼 Regras de Negócio (RN)

1. O sistema deve aceitar placas nos formatos **ABC-1234** (antigo) e **AAA1A11** (Mercosul), com máscara e validação automática para garantir o formato correto.  
2. Prevenir o cadastro de placas duplicadas, impedindo que mais de um veículo use a mesma placa.  
3. Deve oferecer controle de manutenção para evitar prejuízos e prolongar a vida útil dos veículos.  
4. Existirão versões diferenciadas: gratuita (funções básicas) e premium (recursos avançados).  
5. Possibilidade de parcerias com oficinas, seguradoras e autopeças para ampliar o suporte ao usuário.  
6. Indicadores de desempenho (KPIs) do sistema, tais como:  
   - Número de usuários ativos;  
   - Taxa de engajamento com alertas;  
   - Manutenções preventivas registradas por mês;  
   - Retenção de usuários após 30 dias.  
7. Atualizações do sistema serão trimestrais, incluindo suporte via e-mail e formulário.  
8. Plano corporativo para gestão de frotas de pequenas e médias empresas.  
9. Sistema de recompensas baseado no uso contínuo e nas boas práticas de manutenção.  
10. Futuramente, integração com loja de serviços para agendamento, catálogo e promoções.  
11. Avaliação e aprovação de escritórios de manutenção pela comunidade.  
12. Disponibilização de API pública para integração com sistemas externos.

---

## ✅ Requisitos Funcionais (RF)

### 1. Cadastro e Autenticação

- Usuário pode cadastrar conta com: nome completo, e-mail e senha.  
- Suporte a login via conta Google (OAuth).  
- Recuperação de senha por e-mail.  
- Senhas armazenadas com hash seguro.  
- Usuário pode editar e excluir sua conta.  
- Sistema valida campos obrigatórios no cadastro (nome, e-mail, senha).  
- Limita tentativas de login, bloqueando conta temporariamente após 5 tentativas inválidas consecutivas.

### 2. Cadastro de Veículos

- Usuário pode cadastrar **múltiplos veículos**, podendo escolher qual veículo gerenciar.  
- Campos obrigatórios: marca, modelo, ano, tipo de combustível, quilometragem atual, placa.  
- Sistema valida a placa com máscara conforme formatos Mercosul e antigo.  
- Placa duplicada não pode ser cadastrada (mensagem de erro exibida).  
- O usuário indica o proprietário do veículo e pode adicionar motoristas autorizados.  
- É obrigatório o cadastro da documentação do veículo (ex.: CRLV), vinculada ao veículo.  
- Usuário pode editar e excluir veículos, respeitando permissões.  

### 3. Compartilhamento de Veículos

- Proprietário pode compartilhar o acesso ao veículo com outros usuários por e-mail ou código de convite.  
- Permissões configuráveis: visualização ou edição.  
- Acesso compartilhado pode ser removido a qualquer momento pelo proprietário.  
- Sistema notifica usuários sobre alterações feitas por convidados.  
- É possível transferir a propriedade do veículo.

### 4. Registro de Manutenções

- Usuário registra manutenções indicando: tipo de serviço, data, quilometragem, oficina, valor e observações.  
- Upload opcional de nota fiscal, que pode ser processada via OCR para extração de dados.  
- Manutenções podem ser editadas ou excluídas, com registro do autor da alteração.

### 5. Alertas Inteligentes

- Sistema gera alertas automáticos baseados em tempo e quilometragem desde última manutenção.  
- Todos os motoristas vinculados recebem notificações dos alertas.  
- Sugestões de manutenção são geradas com base no histórico do veículo.  
- Cálculo e atualização dos alertas são dinâmicos, considerando atualizações recentes.

### 6. Histórico e Relatórios

- Histórico detalhado de eventos por veículo, incluindo manutenções, despesas e atualizações.  
- Filtros para motoristas, tipo de serviço, oficinas e intervalos de datas.  
- Geração de relatórios visuais e exportação em PDF.  
- Relatório específico para entrega do veículo ao final de uma viagem ou uso.

### 7. Atualização de Quilometragem

- Usuário atualiza manualmente a quilometragem atual do veículo.  
- Histórico de alterações com identificação do usuário que fez a atualização.

### 8. Módulo de Despesas Gerais

- Registro de despesas associadas ao veículo, como IPVA, seguro, multas, lavagens e outras.  
- Despesas categorizadas para melhor controle financeiro.  
- Geração de relatórios por categoria, período e veículo.

### 9. Checklist de Viagem

- Geração de checklist personalizado baseado no tipo de viagem e revisões anteriores.  
- Usuário pode ajustar os itens sugeridos.  
- Checklist pode ser exportado em PDF para uso offline.

---

## ✅ Requisitos Não Funcionais (RNF)

### 1. Segurança e Permissões

- Controle de permissões de acesso por usuário e perfil.  
- Criptografia de dados sensíveis.  
- Autenticação via JWT.  
- Confirmações para ações críticas (exclusão, compartilhamento).  

### 2. Compatibilidade e Acessibilidade

- Aplicação compatível com Android 8.0 ou superior.  
- Suporte a modo escuro e interface responsiva.  
- Atenção a padrões de acessibilidade.

### 3. Desempenho e Escalabilidade

- Tela inicial deve carregar em até 2 segundos.  
- Backend desacoplado e escalável (Node.js + PostgreSQL).  

### 4. Funcionalidade Offline

- Permitir salvamento local e notificações offline.  
- Sincronização automática e segura quando estiver online.

### 5. Backup e Confiabilidade

- Backups diários criptografados.  
- Sistema de logs detalhado para auditoria e análise.

### 6. Suporte Multilíngue e Integração

- Interface inicialmente em português, com planos para multilíngue.  
- Integração com o calendário do celular para lembretes e alertas.
