![image](https://github.com/user-attachments/assets/f546a3ed-e18d-4930-bd26-d041e0232908)
# Descritivo dos Casos de Uso – Sistema REVISAÍ (Versão Revisada)

---

## 🎯 UC1 – Login  
**Atores Envolvidos:** Usuário  
**Resumo:** Permite que o usuário acesse o sistema mediante inserção e validação de credenciais.  
**Campos Obrigatórios:**  
- E-mail (formato válido)  
- Senha (mínimo 8 caracteres, letras e números)  
**Pré-condições:** Usuário deve possuir conta previamente registrada.  
**Fluxo Principal de Eventos:**  
1. Usuário acessa a tela de login.  
2. Informa e-mail e senha.  
3. Sistema valida credenciais.  
4. Em caso de sucesso, redireciona para o painel conforme perfil (Administrador ou Usuário comum).  
**Fluxos Alternativos:**  
- 3a. Credenciais inválidas: exibir mensagem de erro e permitir nova tentativa.  
- 3b. Campos vazios: solicitar preenchimento obrigatório.  
- 3c. Conta bloqueada após 5 tentativas inválidas consecutivas; exibir mensagem de bloqueio temporário.  
**Pós-condições:** Usuário autenticado e com acesso conforme perfil.

---

## 📝 UC2 – Cadastrar Usuário  
**Atores Envolvidos:** Visitante (não autenticado)  
**Resumo:** Permite que novos usuários se cadastrem no sistema fornecendo informações básicas e documentos.  
**Campos Obrigatórios:**  
- Nome completo  
- E-mail (único e válido)  
- Senha (mínimo 8 caracteres, letras e números)  
- Documento(s) (ex: CPF, RG, conforme regras do sistema)  
**Pré-condições:** Nenhuma.  
**Fluxo Principal de Eventos:**  
1. Usuário acessa tela de cadastro.  
2. Preenche dados obrigatórios.  
3. Sistema valida dados (formato, unicidade do e-mail).  
4. Usuário envia documentação para validação (via UC3).  
5. Sistema registra novo usuário.  
6. Usuário pode realizar login após validação.  
**Fluxos Alternativos:**  
- 3a. E-mail já cadastrado: exibir erro e impedir cadastro duplicado.  
- 3b. Documentação inválida ou incompleta: solicitar reenvio.  
**Pós-condições:** Usuário cadastrado e habilitado para login.

---

## 📄 UC3 – Registrar e Validar Documentação  
**Atores Envolvidos:** Sistema, Usuário  
**Resumo:** Permite armazenar e validar documentos de usuários ou veículos durante seus cadastros.  
**Campos Obrigatórios:** Conforme tipo (usuário ou veículo), por exemplo:  
- Para usuário: CPF, RG, comprovante de endereço  
- Para veículo: CRLV, comprovante de propriedade  
**Pré-condições:** Processo de cadastro em andamento (usuário ou veículo).  
**Fluxo Principal de Eventos:**  
1. Sistema solicita upload dos documentos obrigatórios.  
2. Usuário envia os documentos.  
3. Sistema valida documentos (formato, integridade).  
4. Documentos são associados ao cadastro correspondente.  
**Fluxos Alternativos:**  
- 3a. Documentos inválidos: exibir erro e solicitar novo envio.  
**Pós-condições:** Documentos validados e vinculados ao cadastro.

---

## 🚗 UC4 – Cadastrar Veículo  
**Atores Envolvidos:** Usuário autenticado  
**Resumo:** Permite que usuário registre um ou mais veículos no sistema, associando-os ao seu perfil.  
**Campos Obrigatórios:**  
- Marca  
- Modelo  
- Ano (válido e coerente)  
- Tipo de combustível  
- Quilometragem atual (valor numérico positivo)  
- Placa (validação para formatos Mercosul ou antigo, com regex apropriada)  
- Documentação obrigatória (via UC3)  
**Pré-condições:** Usuário autenticado.  
**Fluxo Principal de Eventos:**  
1. Usuário seleciona opção "Cadastrar Veículo".  
2. Preenche os dados obrigatórios.  
3. Sistema valida dados (formato dos campos e unicidade da placa).  
4. Se mais de um veículo cadastrado, usuário escolhe para qual está cadastrando.  
5. Documentação do veículo é enviada para validação (UC3).  
6. Sistema armazena o veículo e vincula ao usuário.  
**Fluxos Alternativos:**  
- 3a. Placa inválida: exibir mensagem e retornar para preenchimento.  
- 3b. Placa já cadastrada: impedir cadastro duplicado e exibir erro.  
- 5a. Documentação incompleta ou inválida: solicitar novo envio.  
**Pós-condições:** Veículo cadastrado e vinculado ao usuário.

---

## 🤝 UC5 – Compartilhar Veículos  
**Atores Envolvidos:** Proprietário do veículo  
**Resumo:** Permite que proprietário compartilhe o acesso a veículos com outros usuários, definindo permissões.  
**Campos Obrigatórios:**  
- E-mail ou código do usuário convidado  
- Tipo de permissão (visualização, edição)  
**Pré-condições:** Veículo cadastrado e usuário proprietário autenticado.  
**Fluxo Principal de Eventos:**  
1. Proprietário acessa opção de compartilhamento do veículo.  
2. Insere e-mail ou código do usuário convidado.  
3. Define permissões para convidado.  
4. Sistema envia convite e aplica permissões após aceitação.  
**Pós-condições:** Usuário convidado tem acesso conforme permissões.

---

## 🚗 UC5.1 – Associar Motorista ao Veículo  
**Atores Envolvidos:** Proprietário do veículo  
**Resumo:** Permite ao proprietário indicar motoristas autorizados para determinado veículo.  
**Campos Obrigatórios:**  
- Identificação do motorista (usuário já cadastrado)  
**Pré-condições:** Veículo cadastrado e proprietário autenticado.  
**Fluxo Principal de Eventos:**  
1. Proprietário seleciona veículo.  
2. Indica um ou mais motoristas autorizados.  
3. Sistema associa motoristas ao veículo.  
**Pós-condições:** Motoristas vinculados e com permissões definidas.

---

## 🛠 UC6 – Registrar Manutenção  
**Atores Envolvidos:** Usuário autenticado  
**Resumo:** Permite registrar serviços de manutenção realizados em veículos cadastrados.  
**Campos Obrigatórios:**  
- Tipo de serviço  
- Data (não futura)  
- Quilometragem no momento do serviço  
- Oficina  
- Valor (numérico positivo)  
- (Opcional) Anexo de nota fiscal (arquivo válido)  
**Pré-condições:** Veículo cadastrado e selecionado.  
**Fluxo Principal de Eventos:**  
1. Usuário seleciona veículo (caso tenha mais de um).  
2. Preenche dados da manutenção.  
3. (Opcional) Realiza upload da nota fiscal.  
4. Sistema valida dados e armazena registro e arquivo.  
**Fluxos Alternativos:**  
- 3a. Upload da nota fiscal não realizado: sistema registra dados normalmente.  
- 2a. Dados inválidos: exibir mensagem e solicitar correção.  
**Pós-condições:** Registro de manutenção armazenado.

---

## 📊 UC7 – Emitir Relatórios e Histórico  
**Atores Envolvidos:** Usuário autenticado  
**Resumo:** Permite gerar e visualizar relatórios com filtros sobre veículos, manutenções, despesas, e históricos.  
**Campos Obrigatórios:**  
- Critérios de filtro (período, veículo, tipo de registro)  
**Pré-condições:** Dados existentes no sistema.  
**Fluxo Principal de Eventos:**  
1. Usuário seleciona filtros e tipo de relatório.  
2. Sistema gera relatório conforme parâmetros.  
3. Usuário visualiza, baixa ou exporta relatório em PDF.  
**Pós-condições:** Relatório entregue ao usuário.

---

## 📈 UC8 – Atualizar Quilometragem  
**Atores Envolvidos:** Usuário autenticado  
**Resumo:** Permite atualizar a quilometragem atual de veículos cadastrados.  
**Campos Obrigatórios:**  
- Quilometragem nova (maior que a atual)  
**Pré-condições:** Veículo cadastrado e selecionado.  
**Fluxo Principal de Eventos:**  
1. Usuário seleciona veículo.  
2. Informa nova quilometragem.  
3. Sistema valida se quilometragem nova é maior que a anterior.  
4. Atualiza valor e registra no histórico.  
**Fluxos Alternativos:**  
- 3a. Quilometragem inválida (menor ou igual à anterior): exibe erro.  
**Pós-condições:** Quilometragem atualizada.

---

## 💰 UC9 – Registrar Despesas Gerais  
**Atores Envolvidos:** Usuário autenticado  
**Resumo:** Permite registrar despesas relacionadas a veículos.  
**Campos Obrigatórios:**  
- Tipo de despesa  
- Valor (numérico positivo)  
- Data  
- Categoria  
**Pré-condições:** Veículo cadastrado e selecionado.  
**Fluxo Principal de Eventos:**  
1. Usuário seleciona veículo.  
2. Acessa tela de despesas.  
3. Preenche dados obrigatórios.  
4. Sistema valida e armazena informação.  
**Pós-condições:** Despesa registrada no sistema.

---

## 📋 UC10 – Fazer Checklist de Viagem  
**Atores Envolvidos:** Usuário autenticado  
**Resumo:** Gera checklist personalizado antes de viagem, baseado em histórico e tipo de viagem.  
**Campos Obrigatórios:**  
- Tipo de viagem  
**Pré-condições:** Veículo cadastrado e selecionado.  
**Fluxo Principal de Eventos:**  
1. Usuário seleciona veículo e tipo de viagem.  
2. Sistema sugere itens com base em histórico e revisões.  
3. Usuário personaliza checklist.  
4. Checklist pode ser exportado em PDF.  
**Pós-condições:** Checklist disponível para uso.

---

## 🔔 UC11 – Gerar Alertas Inteligentes  
**Atores Envolvidos:** Sistema automatizado  
**Resumo:** Gera alertas automáticos com base em tempo, quilometragem e histórico de manutenção.  
**Pré-condições:** Veículos cadastrados com histórico atualizado.  
**Fluxo Principal de Eventos:**  
1. Sistema verifica periodicamente dados do veículo.  
2. Detecta necessidade de alertas com base em regras de negócio (ex: troca de óleo a cada X km).  
3. Gera alertas e envia notificações para usuários vinculados e motoristas autorizados.  
**Pós-condições:** Alertas gerados e usuários notificados.

---

# Observações Gerais  
- Usuários podem ter múltiplos veículos e devem selecionar qual veículo desejam operar em cada caso de uso.  
- Cadastro de usuário é realizado por visitantes, não por usuários autenticados.  
- Registro de documentação é parte integrada aos cadastros de usuário e veículo (UC3).  
- Associação de motoristas ao veículo é um caso de uso complementar (UC5.1).  
- Validações de formato e regras são essenciais para garantir integridade dos dados (placa, e-mail, datas, valores).  
