# Bug Hunt — OrangeHRM Demo

Projeto de testes manuais realizado no ambiente de demonstração público do OrangeHRM, um sistema de gestão de RH open source. O objetivo foi explorar os principais fluxos do sistema, documentar casos de teste e identificar defeitos reais.

---

## Sobre o projeto

| Item | Detalhe |
|---|---|
| App testado | OrangeHRM Demo |
| URL | https://opensource-demo.orangehrmlive.com |
| Tipo de teste | Manual exploratório e funcional |
| Módulos cobertos | Login, PIM, Admin, Recruitment |
| Ambiente | Microsoft Edge · Windows |
| Período | Junho 2026 |
| Casos de teste | 15 (12 Passed, 3 Failed) |

---

## Módulos testados

### Login
Validação do fluxo de autenticação, incluindo cenários positivos (credenciais válidas) e negativos (senha incorreta, campos vazios, credenciais inexistentes).

### PIM — Personal Details
Cadastro, edição e exclusão de funcionários, com foco em campos obrigatórios, validações e componentes de seleção.

### Admin — User Management
Cadastro, edição e exclusão de usuários do sistema, com mesma atenção aos componentes de seleção.

### Recruitment — Vacancies
Cadastro e edição de vagas, confirmando se o comportamento dos campos de seleção se repete fora do módulo PIM.

---

## O que foi encontrado

### BUG-001 — Campos de seleção não filtram opções ao digitar letra inicial

**Severidade:** Medium  
**Módulo:** Global — Admin, PIM e Recruitment  

Ao digitar uma letra nos campos de seleção (ex: Country, Nationality), a lista de opções é exibida mas não filtra de acordo com o caractere digitado. O usuário é obrigado a rolar manualmente por toda a lista para encontrar o item desejado. Comportamento confirmado de forma consistente em três módulos diferentes do sistema.

→ Detalhes completos em [bug-reports.md](./bug-reports.md)

---

## Arquivos do projeto

| Arquivo | Conteúdo |
|---|---|
| [test-cases.md](./test-cases.md) | Casos de teste — estrutura, passos e resultados |
| [bug-reports.md](./bug-reports.md) | Bugs encontrados com evidências |
| [assets/](../assets/) | Screenshots das execuções |

---

## Aprendizados

- Sistemas com listas longas (países, nacionalidades) dependem criticamente de filtros funcionais para boa usabilidade
- Bugs de usabilidade não quebram o sistema mas impactam diretamente a eficiência do usuário
- Testes exploratórios revelam comportamentos inesperados que roteiros fixos podem não cobrir

---

*Projeto desenvolvido como parte do portfólio QA em construção. Veja o repositório principal: [qa-portfolio](../README.md)*
