# HabitGo

**Versao**: v2.0

**Membros**
Lorenzo, Felipe, Enzo, João Pedro e Maycon

---

## Sumário

1. [Introdução](#1-introducao)
2. [Requisitos do Sistema](#2-requisitos-do-sistema)
   - 2.1 Requisitos Funcionais
   - 2.2 Requisitos Não Funcionais
3. [Casos de Uso](#3-casos-de-uso)
4. [Diagramas UML](#4-diagramas-uml)
5. [Modelagem do Banco de Dados](#5-modelagem-do-banco-de-dados)
6. [Requisitos Técnicos](#6-requisitos-técnicos)


---

## 1. Introdução

### 1.1 Descrição Geral do Sistema

O HabitGo é um aplicativo multiplataforma (web, desktop e mobile) de gestão e rastreamento de hábitos pessoais. O app tem como proposta central ajudar usuários a criarem, acompanharem e manterem hábitos em seu cotidiano, principalmente pelas notificações/lembretes, combinando simplicidade de uso com recursos de motivação e autoconhecimento, crescendo, assim, na vida de virtudes.

### 1.2 Objetivo do Projeto

Desenvolver um aplicativo multiplataforma funcional que permita ao usuário:

- Criar e organizar hábitos personalizados por categoria e frequência
- Realizar check-ins diários de forma rápida e intuitiva
- Acompanhar o progresso por meio de estatísticas e gráficos
- Manter a disciplina por meio de streaks e notificações
- Registrar o humor diário e correlacionar com a consistência dos hábitos

### 1.3 Público-Alvo

O HabitGo é destinado a pessoas com 15 anos ou mais que desejam organizar melhor sua rotina, desenvolver novos hábitos ou superar hábitos negativos. O app atende perfis variados: estudantes, profissionais, atletas amadores e qualquer pessoa interessada em produtividade e bem-estar pessoal.

### 1.4 Justificativa

A formação de hábitos é a base para uma vida produtiva e ordenada. Entretanto, grande parte das pessoas encontra dificuldade em manter consistência sem ferramentas adequadas de acompanhamento e motivação. O HabitGo surge como solução acessível e completa, unindo rastreamento eficiente com recursos de engajamento que reduzem o abandono ao longo do tempo.

### 1.5 Aviso

O HabitGo não afirma categoricamente que todo usuário irá evoluir apenas por utilizar o aplicativo. Deve ficar claro que o crescimento e o desenvolvimento pessoal dependem exclusivamente do comprometimento e da disciplina de quem usa o sistema.

---

## 2. Requisitos do Sistema

### 2.1 Requisitos Funcionais

| ID    | Funcionalidade       | Descrição |
|-------|----------------------|-----------|
| RF01  | Cadastro de Hábito   | O usuário pode criar hábitos com nome livre, ícone, cor, categoria e frequência (diária, dias específicos ou X vezes por semana). |
| RF02  | Check-in Diário      | Interface para marcar hábitos concluídos no dia, com indicador de progresso (ex: 3 de 5 feitos). |
| RF03  | Streaks              | Contador de dias consecutivos por hábito e registro do melhor recorde. |
| RF04  | Notificações         | Horário personalizado por hábito, notificação ao longo do dia e resumo semanal de desempenho. |
| RF05  | Estatísticas         | Gráfico semanal/mensal, taxa de conclusão e comparativo entre semanas. |
| RF06  | Categorias           | Categorias predefinidas: Saúde, Produtividade, Aprendizado, Relacionamentos, Finanças e Personalizada. |
| RF08  | Registro de Humor    | Registro emocional diário opcional com histórico e correlação entre humor e consistência de hábitos. |
| RF09  | Cadastro de Usuário  | O usuário pode criar uma conta com nome, e-mail e senha, e fazer login no aplicativo. |
| RF10  | Edição e Exclusão    | O usuário pode editar ou excluir hábitos cadastrados a qualquer momento. |

### 2.2 Requisitos Não Funcionais

| ID     | Categoria        | Descrição |
|--------|------------------|-----------|
| RNF01  | Desempenho       | O app deve carregar a tela principal sem muitos atrasos |
| RNF02  | Usabilidade      | A interface deve ser intuitiva, com fluxo de check-in realizável em no máximo 2 toques/cliques. |
| RNF03  | Segurança / LGPD | Dados sensíveis do usuário devem ser armazenados de forma criptografada e transmitidos via HTTPS. Senhas não devem ser salvas em texto plano. O sistema deve garantir ao usuário o direito de acessar, corrigir e excluir seus dados, em conformidade com a LGPD (Lei nº 13.709/2018). |
| RNF04  | Compatibilidade  | O app deve funcionar em Android, iOS, nos principais navegadores modernos (Chrome, Firefox, Safari, Edge) e em computadores de baixo desempenho. |
| RNF05  | Escalabilidade   | A arquitetura deve suportar crescimento de usuários sem degradação significativa de desempenho. |

---

## 3. Casos de Uso

### 3.1 Atores

- **Usuário:** pessoa que utiliza o aplicativo para gerenciar seus hábitos.
- **Sistema:** o próprio aplicativo HabitGo, responsável por processar e exibir dados.

### 3.2 Lista de Casos de Uso

| ID    | Caso de Uso             | Descrição |
|-------|-------------------------|-----------|
| UC01  | Cadastrar usuário       | O usuário cria uma conta informando nome, e-mail e senha. |
| UC02  | Fazer login             | O usuário acessa o app com suas credenciais. |
| UC03  | Criar hábito            | O usuário configura um novo hábito com nome, categoria, frequência, ícone e cor. |
| UC04  | Realizar check-in       | O usuário marca um hábito como concluído no dia. |
| UC05  | Visualizar streak       | O usuário consulta seu contador de dias consecutivos e recorde pessoal. |
| UC06  | Consultar estatísticas  | O usuário acessa gráficos de desempenho por período. |
| UC07  | Registrar humor         | O usuário registra seu estado emocional do dia de forma opcional. |
| UC08  | Receber notificação     | O sistema envia lembretes e alertas conforme configurado. |
| UC09  | Editar/excluir hábito   | O usuário modifica ou remove um hábito existente. |

### 3.3 Descrições Expandidas dos Casos de Uso

#### UC01 — Cadastrar Usuário

| Campo             | Descrição |
|-------------------|-----------|
| Ator principal    | Usuário |
| Pré-condição      | O usuário não possui conta cadastrada no sistema. |
| Fluxo principal   | 1. Usuário acessa a tela de cadastro. 2. Preenche nome, e-mail e senha. 3. Confirma o cadastro. 4. Sistema valida os dados e cria a conta. 5. Usuário é redirecionado para a tela principal. |
| Fluxo alternativo | Se o e-mail já estiver cadastrado, o sistema exibe mensagem de erro e solicita outro e-mail. Se a senha não atender aos requisitos mínimos, o sistema informa as regras e solicita nova senha. |

#### UC02 — Fazer Login

| Campo             | Descrição |
|-------------------|-----------|
| Ator principal    | Usuário |
| Pré-condição      | O usuário possui conta cadastrada no sistema. |
| Fluxo principal   | 1. Usuário acessa a tela de login. 2. Informa e-mail e senha. 3. Sistema valida as credenciais. 4. Usuário é redirecionado para a tela principal. |
| Fluxo alternativo | Se as credenciais estiverem incorretas, o sistema exibe mensagem de erro. Após 5 tentativas falhas, o acesso é temporariamente bloqueado. |

#### UC03 — Criar Hábito

| Campo             | Descrição |
|-------------------|-----------|
| Ator principal    | Usuário |
| Pré-condição      | Usuário autenticado no sistema. |
| Fluxo principal   | 1. Usuário acessa "Novo Hábito". 2. Preenche nome, categoria, ícone e cor. 3. Confirma a criação. 4. Sistema salva e exibe o hábito na tela principal. |
| Fluxo alternativo | Se o usuário não preencher o nome, o sistema exibe mensagem de erro e solicita preenchimento. |

#### UC04 — Realizar Check-in

| Campo             | Descrição |
|-------------------|-----------|
| Ator principal    | Usuário |
| Pré-condição      | Usuário autenticado e com ao menos um hábito cadastrado. |
| Fluxo principal   | 1. Usuário acessa a tela principal. 2. Visualiza a lista de hábitos do dia. 3. Marca um hábito como concluído. 4. Sistema atualiza o indicador de progresso e o streak do hábito. |
| Fluxo alternativo | Se o usuário tentar fazer check-in em um hábito já concluído no dia, o sistema permite desmarcar a conclusão. |

#### UC05 — Visualizar Streak

| Campo             | Descrição |
|-------------------|-----------|
| Ator principal    | Usuário |
| Pré-condição      | Usuário autenticado e com ao menos um check-in registrado. |
| Fluxo principal   | 1. Usuário acessa o hábito desejado. 2. Sistema exibe o contador de dias consecutivos atual e o melhor recorde histórico. 3. Se o streak estiver em risco, o sistema exibe um alerta. |
| Fluxo alternativo | Se o usuário não realizou check-in no dia anterior, o sistema exibe o streak zerado e o recorde anterior como histórico. |

#### UC06 — Consultar Estatísticas

| Campo             | Descrição |
|-------------------|-----------|
| Ator principal    | Usuário |
| Pré-condição      | Usuário autenticado e com ao menos uma semana de check-ins registrados. |
| Fluxo principal   | 1. Usuário acessa a tela de estatísticas. 2. Sistema exibe gráfico semanal/mensal, taxa de conclusão e comparativo entre semanas. 3. Usuário pode filtrar por hábito ou período. |
| Fluxo alternativo | Se não houver dados suficientes, o sistema exibe mensagem orientando o usuário a registrar hábitos por mais dias. |

#### UC07 — Registrar Humor

| Campo             | Descrição |
|-------------------|-----------|
| Ator principal    | Usuário |
| Pré-condição      | Usuário autenticado no sistema. |
| Fluxo principal   | 1. Usuário acessa a tela de registro de humor. 2. Seleciona seu estado emocional na escala de 1 a 5. 3. Opcionalmente, adiciona uma observação escrita. 4. Confirma o registro. 5. Sistema salva e exibe o histórico atualizado. |
| Fluxo alternativo | Se o usuário já registrou o humor no dia, o sistema permite editar o registro existente. |

#### UC08 — Receber Notificação

| Campo             | Descrição |
|-------------------|-----------|
| Ator principal    | Sistema |
| Pré-condição      | Usuário autenticado, com hábitos cadastrados e notificações ativadas. |
| Fluxo principal   | 1. Sistema identifica hábitos com lembrete configurado para o horário atual. 2. Envia notificação ao usuário. 3. Ao fim do dia, envia resumo de desempenho. |
| Fluxo alternativo | Se o usuário estiver com notificações desativadas no dispositivo, o sistema não envia alertas e exibe aviso nas configurações do app. |

#### UC09 — Editar/Excluir Hábito

| Campo             | Descrição |
|-------------------|-----------|
| Ator principal    | Usuário |
| Pré-condição      | Usuário autenticado e com ao menos um hábito cadastrado. |
| Fluxo principal   | 1. Usuário acessa o hábito desejado. 2. Seleciona "Editar" ou "Excluir". 3a. Se editar: altera os dados desejados e confirma. O sistema salva as alterações. 3b. Se excluir: o sistema solicita confirmação. Após confirmação, o hábito é removido. |

---

## 4. Diagramas UML

#### Diagrama de Casos de Uso

Ir para *HabitGo/docs/diagramas_uc*. Usamos arquivos drawio.

#### Diagrama de Classes

- A definir

---

## 5. Modelagem do Banco de Dados

### 5.1 Modelo Entidade-Relacionamento (MER)

- A definir

### 5.2 Dicionário de Dados 

- A definir

---

## 6. Requisitos Técnicos

- A definir