![image](https://github.com/user-attachments/assets/f546a3ed-e18d-4930-bd26-d041e0232908)
# 📘 Descritivo dos Casos de Uso – Sistema REVISAÍ

## 🎯 UC1 – Login

- **Atores Envolvidos:** Usuário  
- **Resumo:** Permite que o usuário acesse o sistema informando credenciais válidas.  
- **Pré-condições:** O usuário já deve ter uma conta registrada no sistema.  
- **Fluxo Principal de Eventos:**
  1. O usuário acessa a tela de login.
  2. Informa e-mail e senha.
  3. O sistema valida as credenciais.
  4. Em caso de sucesso, o usuário é redirecionado para o painel principal.
- **Fluxo Alternativo:**
  - 3a. Se as credenciais forem inválidas, o sistema exibe mensagem de erro e permanece na tela de login.
- **Pós-condições:** O usuário tem acesso às funcionalidades permitidas conforme seu perfil.

---

## 📝 UC2 – Cadastrar Usuário

- **Atores Envolvidos:** Usuário  
- **Resumo:** Permite que novos usuários se cadastrem no sistema fornecendo suas informações básicas.  
- **Pré-condições:** Nenhuma.  
- **Fluxo Principal de Eventos:**
  1. O usuário acessa a tela de cadastro.
  2. Preenche os dados solicitados (nome, e-mail, senha etc).
  3. O sistema valida os dados.
  4. Os dados são armazenados.
  5. A documentação é registrada (<<include>> UC3).
- **Pós-condições:** O usuário está cadastrado no sistema e pode realizar login.

---

## 📄 UC3 – Registrar Documentação

- **Atores Envolvidos:** Sistema (chamado via UC2 ou UC4)  
- **Resumo:** Responsável por armazenar e validar os documentos fornecidos por usuários e veículos.  
- **Pré-condições:** O processo de cadastro de usuário ou veículo deve estar em andamento.  
- **Fluxo Principal de Eventos:**
  1. O sistema solicita documentos obrigatórios.
  2. O usuário envia os documentos.
  3. O sistema realiza análise e validação.
  4. Documentos são associados ao cadastro correspondente.
- **Pós-condições:** Documentos armazenados e validados.

---

## 🚗 UC4 – Cadastrar Veículos

- **Atores Envolvidos:** Usuário  
- **Resumo:** Permite que o usuário registre um ou mais veículos no sistema.  
- **Pré-condições:** O usuário deve estar autenticado.  
- **Fluxo Principal de Eventos:**
  1. O usuário acessa a opção "Cadastrar Veículo".
  2. Preenche as informações obrigatórias.
  3. O sistema valida a placa e verifica duplicidade.
  4. Os dados são armazenados.
  5. A documentação do veículo é registrada (<<include>> UC3).
- **Fluxo Alternativo:**
  - 3a. Se a placa estiver em uso, exibe mensagem de erro.
- **Pós-condições:** O veículo está cadastrado e vinculado ao usuário.

---

## 🤝 UC5 – Compartilhar Veículos

- **Atores Envolvidos:** Proprietário  
- **Resumo:** Permite que o proprietário compartilhe o acesso ao veículo com outros usuários.  
- **Pré-condições:** Veículo deve estar cadastrado e o usuário deve ser o proprietário.  
- **Fluxo Principal de Eventos:**
  1. O proprietário acessa a opção de compartilhamento.
  2. Insere o e-mail ou código do convidado.
  3. Define as permissões.
  4. O sistema envia convite ou aplica as permissões.
- **Pós-condições:** O outro usuário tem acesso ao veículo conforme as permissões definidas.

---

## 🛠 UC6 – Registrar Manutenções

- **Atores Envolvidos:** Usuário  
- **Resumo:** Permite o registro de serviços de manutenção executados em veículos cadastrados.  
- **Pré-condições:** Veículo deve estar cadastrado.  
- **Fluxo Principal de Eventos:**
  1. O usuário seleciona o veículo.
  2. Informa os dados da manutenção (tipo, data, quilometragem, valor, etc).
  3. (Opcional) Anexa nota fiscal.
  4. O sistema salva os dados e atualiza histórico.
- **Pós-condições:** A manutenção é registrada e associada ao veículo.

---

## 📊 UC7 – Emitir Históricos e Relatórios

- **Atores Envolvidos:** Usuário  
- **Resumo:** Permite a emissão de relatórios detalhados sobre veículos e manutenções.  
- **Pré-condições:** Deve haver dados registrados no sistema.  
- **Fluxo Principal de Eventos:**
  1. O usuário seleciona filtros e tipo de relatório.
  2. O sistema gera o relatório conforme parâmetros.
  3. O usuário pode visualizar, baixar ou exportar em PDF.
- **Pós-condições:** O relatório é entregue ao usuário conforme solicitado.

---

## 📈 UC8 – Atualizar Quilometragem

- **Atores Envolvidos:** Usuário  
- **Resumo:** Permite atualizar a quilometragem atual do veículo.  
- **Pré-condições:** Veículo deve estar cadastrado.  
- **Fluxo Principal de Eventos:**
  1. O usuário seleciona o veículo.
  2. Informa a nova quilometragem.
  3. O sistema valida a diferença com o valor anterior.
  4. A quilometragem é atualizada e registrada no histórico.
- **Pós-condições:** A quilometragem do veículo é atualizada.

---

## 💰 UC9 – Registrar Despesas Gerais

- **Atores Envolvidos:** Usuário  
- **Resumo:** Permite ao usuário registrar despesas diversas relacionadas ao veículo.  
- **Pré-condições:** Veículo deve estar cadastrado.  
- **Fluxo Principal de Eventos:**
  1. O usuário acessa a tela de despesas.
  2. Informa tipo, valor, data e categoria.
  3. O sistema armazena os dados.
- **Pós-condições:** A despesa é registrada e categorizada no sistema.

---

## 📋 UC10 – Fazer Checklist de Viagem

- **Atores Envolvidos:** Usuário  
- **Resumo:** Permite ao usuário gerar um checklist personalizado antes de realizar uma viagem.  
- **Pré-condições:** Veículo deve estar cadastrado.  
- **Fluxo Principal de Eventos:**
  1. O usuário seleciona o tipo de viagem.
  2. O sistema sugere uma lista baseada em histórico e revisões.
  3. O usuário pode ajustar os itens.
  4. O checklist é gerado e pode ser exportado em PDF.
- **Pós-condições:** O usuário obtém um checklist pronto para uso.

---

## 🔔 UC11 – Alertar

- **Atores Envolvidos:** Robô (Sistema Automatizado)  
- **Resumo:** Gera alertas automáticos com base em tempo ou quilometragem do veículo.  
- **Pré-condições:** Veículo deve ter manutenções e/ou quilometragem atualizadas.  
- **Fluxo Principal de Eventos:**
  1. O robô verifica periodicamente os dados do veículo.
  2. Identifica eventos futuros baseados em padrões (ex: troca de óleo a cada X km).
  3. Gera alerta e envia notificação aos usuários vinculados.
- **Pós-condições:** O alerta é emitido e os usuários notificados.

