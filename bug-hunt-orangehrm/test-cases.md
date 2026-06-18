# Casos de teste — OrangeHRM Demo

| Info | Detalhe |
|---|---|
| **App** | OrangeHRM Demo |
| **URL** | https://opensource-demo.orangehrmlive.com |
| **Testado por** | Jenni |
| **Período** | Junho 2026 |
| **Total de casos** | 15 |

---

## Resumo da execução

| Métrica | Valor |
|---|---|
| ✅ Passed | 12 |
| ❌ Failed | 3 |
| Taxa de sucesso | 80% |

Os 3 casos com falha (TC-008, TC-012, TC-015) estão relacionados ao mesmo defeito — ver [BUG-001](./bug-reports.md) — confirmado de forma consistente nos três módulos testados (PIM, Admin, Recruitment).

---

## Legenda

| Status | Significado |
|---|---|
| ✅ Passed | Comportamento conforme esperado |
| ❌ Failed | Comportamento diferente do esperado |
| ⏳ Not executed | Ainda não executado |

---

## Módulo: Login

### TC-001 — Login com credenciais válidas
| Campo | Detalhe |
|---|---|
| **ID** | TC-001 |
| **Tipo** | Smoke |
| **Prioridade** | Alta |
| **Pré-condição** | Acessar a página de login do OrangeHRM |
| **Dados de teste** | Usuário: Admin / Senha: admin123 |

**Passos:**
1. Acessar https://opensource-demo.orangehrmlive.com
2. Inserir usuário "Admin" no campo Username
3. Inserir "admin123" no campo Password
4. Clicar em "Login"

**Resultado esperado:** Usuário é redirecionado ao dashboard com o nome exibido no canto superior direito.

**Resultado obtido:** ✅ Passed

---

### TC-002 — Login com senha incorreta
| Campo | Detalhe |
|---|---|
| **ID** | TC-002 |
| **Tipo** | Negativo |
| **Prioridade** | Alta |
| **Pré-condição** | Acessar a página de login |
| **Dados de teste** | Usuário: Admin / Senha: senhaerrada |

**Passos:**
1. Inserir usuário "Admin"
2. Inserir senha incorreta "senhaerrada"
3. Clicar em "Login"

**Resultado esperado:** Mensagem de erro é exibida. Usuário permanece na página de login.

**Resultado obtido:** ✅ Passed

---

### TC-003 — Login com campos vazios
| Campo | Detalhe |
|---|---|
| **ID** | TC-003 |
| **Tipo** | Negativo |
| **Prioridade** | Alta |
| **Pré-condição** | Acessar a página de login |
| **Dados de teste** | Campos em branco |

**Passos:**
1. Deixar os campos Username e Password em branco
2. Clicar em "Login"

**Resultado esperado:** Sistema exibe mensagem de campo obrigatório em ambos os campos. Login não é realizado.

**Resultado obtido:** ✅ Passed

---

### TC-004 — Login com usuário inexistente
| Campo | Detalhe |
|---|---|
| **ID** | TC-004 |
| **Tipo** | Negativo |
| **Prioridade** | Média |
| **Pré-condição** | Acessar a página de login |
| **Dados de teste** | Usuário: usuarioinexistente / Senha: qualquer123 |

**Passos:**
1. Inserir um usuário que não existe no sistema
2. Inserir qualquer senha
3. Clicar em "Login"

**Resultado esperado:** Mensagem de erro genérica é exibida sem indicar se o erro é no usuário ou na senha.

**Resultado obtido:** ✅ Passed

---

## Módulo: PIM — Personal Details

### TC-005 — Cadastrar novo funcionário com dados válidos
| Campo | Detalhe |
|---|---|
| **ID** | TC-005 |
| **Tipo** | Funcional positivo |
| **Prioridade** | Alta |
| **Pré-condição** | Usuário logado como Admin |
| **Dados de teste** | Nome, sobrenome e ID do funcionário preenchidos |

**Passos:**
1. Acessar PIM → Add Employee
2. Preencher First Name, Last Name e Employee ID
3. Clicar em "Save"

**Resultado esperado:** Funcionário é cadastrado e sistema redireciona para a página de detalhes do novo funcionário.

**Resultado obtido:** ✅ Passed

---

### TC-006 — Editar dados pessoais de funcionário existente
| Campo | Detalhe |
|---|---|
| **ID** | TC-006 |
| **Tipo** | Funcional positivo |
| **Prioridade** | Alta |
| **Pré-condição** | Funcionário cadastrado no sistema |
| **Dados de teste** | Novo valor para campo de texto (ex: sobrenome) |

**Passos:**
1. Acessar PIM → Employee List
2. Clicar em qualquer funcionário
3. Editar um campo (ex: Last Name)
4. Clicar em "Save"

**Resultado esperado:** Dados são atualizados e mensagem de sucesso é exibida.

**Resultado obtido:** ✅ Passed — *Observação: o sistema confirma o salvamento com mensagem de sucesso, mas não redireciona automaticamente para a Employee List como seria esperado em um fluxo típico de edição.*

---

### TC-007 — Excluir funcionário cadastrado
| Campo | Detalhe |
|---|---|
| **ID** | TC-007 |
| **Tipo** | Funcional positivo |
| **Prioridade** | Média |
| **Pré-condição** | Funcionário cadastrado no sistema |
| **Dados de teste** | — |

**Passos:**
1. Acessar PIM → Employee List
2. Selecionar um funcionário marcando o checkbox
3. Clicar em "Delete Selected"
4. Confirmar a exclusão

**Resultado esperado:** Funcionário é removido da lista. Mensagem de sucesso é exibida.

**Resultado obtido:** ✅ Passed

---

### TC-008 — Campo de seleção não filtra por letra inicial (PIM)
| Campo | Detalhe |
|---|---|
| **ID** | TC-008 |
| **Tipo** | Negativo / Usabilidade |
| **Prioridade** | Média |
| **Pré-condição** | Usuário em PIM → Personal Details de qualquer funcionário |
| **Dados de teste** | Letra "B" digitada no campo Nationality |

**Passos:**
1. Acessar PIM → Employee List → clicar em qualquer funcionário
2. Ir até Personal Details
3. Clicar no campo "Nationality"
4. Digitar a letra "B"
5. Observar a lista exibida

**Resultado esperado:** Lista filtra e exibe apenas nacionalidades que começam com "B".

**Resultado obtido:** ❌ Failed — *Ver BUG-001*

---

## Módulo: Admin

### TC-009 — Cadastrar novo usuário com dados válidos
| Campo | Detalhe |
|---|---|
| **ID** | TC-009 |
| **Tipo** | Funcional positivo |
| **Prioridade** | Alta |
| **Pré-condição** | Usuário logado como Admin |
| **Dados de teste** | Username único, role, status e funcionário vinculado |

**Passos:**
1. Acessar Admin → User Management → Users
2. Clicar em "Add"
3. Preencher todos os campos obrigatórios
4. Clicar em "Save"

**Resultado esperado:** Novo usuário é criado e aparece na lista de usuários.

**Resultado obtido:** ✅ Passed

---

### TC-010 — Editar dados de usuário existente
| Campo | Detalhe |
|---|---|
| **ID** | TC-010 |
| **Tipo** | Funcional positivo |
| **Prioridade** | Alta |
| **Pré-condição** | Usuário cadastrado no sistema |
| **Dados de teste** | Novo valor para campo editável |

**Passos:**
1. Acessar Admin → User Management → Users
2. Clicar no ícone de edição de qualquer usuário
3. Alterar um campo (ex: User Role)
4. Clicar em "Save"

**Resultado esperado:** Dados atualizados com sucesso. Mensagem de confirmação exibida.

**Resultado obtido:** ✅ Passed

---

### TC-011 — Excluir usuário cadastrado
| Campo | Detalhe |
|---|---|
| **ID** | TC-011 |
| **Tipo** | Funcional positivo |
| **Prioridade** | Média |
| **Pré-condição** | Usuário cadastrado no sistema (diferente do Admin principal) |
| **Dados de teste** | — |

**Passos:**
1. Acessar Admin → User Management → Users
2. Selecionar um usuário pelo checkbox
3. Clicar em "Delete Selected"
4. Confirmar a exclusão

**Resultado esperado:** Usuário removido da lista. Mensagem de sucesso exibida.

**Resultado obtido:** ✅ Passed

---

### TC-012 — Campo de seleção não filtra por letra inicial (Admin)
| Campo | Detalhe |
|---|---|
| **ID** | TC-012 |
| **Tipo** | Negativo / Usabilidade |
| **Prioridade** | Média |
| **Pré-condição** | Usuário em Admin → formulário de criação ou edição |
| **Dados de teste** | Letra digitada em campo de seleção |

**Passos:**
1. Acessar Admin → User Management → Users → Add
2. Clicar em um campo de seleção do formulário
3. Digitar uma letra
4. Observar a lista exibida

**Resultado esperado:** Lista filtra de acordo com a letra digitada.

**Resultado obtido:** ❌ Failed — *Ver BUG-001*

---

## Módulo: Recruitment

### TC-013 — Cadastrar nova vaga com dados válidos
| Campo | Detalhe |
|---|---|
| **ID** | TC-013 |
| **Tipo** | Funcional positivo |
| **Prioridade** | Alta |
| **Pré-condição** | Usuário logado como Admin |
| **Dados de teste** | Nome da vaga, número de posições e gerente responsável |

**Passos:**
1. Acessar Recruitment → Vacancies → Add
2. Preencher os campos obrigatórios
3. Clicar em "Save"

**Resultado esperado:** Vaga criada com sucesso e exibida na lista de vagas.

**Resultado obtido:** ✅ Passed

---

### TC-014 — Editar vaga existente
| Campo | Detalhe |
|---|---|
| **ID** | TC-014 |
| **Tipo** | Funcional positivo |
| **Prioridade** | Média |
| **Pré-condição** | Vaga cadastrada no sistema |
| **Dados de teste** | Novo valor para campo editável |

**Passos:**
1. Acessar Recruitment → Vacancies
2. Clicar no ícone de edição de uma vaga
3. Alterar um campo (ex: número de posições)
4. Clicar em "Save"

**Resultado esperado:** Dados da vaga atualizados. Mensagem de confirmação exibida.

**Resultado obtido:** ✅ Passed

---

### TC-015 — Campo de seleção não filtra por letra inicial (Recruitment)
| Campo | Detalhe |
|---|---|
| **ID** | TC-015 |
| **Tipo** | Negativo / Usabilidade |
| **Prioridade** | Média |
| **Pré-condição** | Usuário em Recruitment → formulário de vaga |
| **Dados de teste** | Letra digitada em campo de seleção |

**Passos:**
1. Acessar Recruitment → Vacancies → Add
2. Clicar em um campo de seleção do formulário
3. Digitar uma letra
4. Observar a lista exibida

**Resultado esperado:** Lista filtra de acordo com a letra digitada.

**Resultado obtido:** ❌ Failed — *Ver BUG-001*

---

*Voltar para o projeto: [README.md](./README.md)*
