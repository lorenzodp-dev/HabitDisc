# HabitGo

**Projeto Integrador**
Técnico em Desenvolvimento de Sistemas — SENAC — 2025

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
6. [Protótipos de Telas](#6-prototipos-de-telas)
7. [Expansões Futuras](#7-expansoes-futuras)

---

## 1. Introdução

### 1.1 Descrição Geral do Sistema

O HabitGo é um aplicativo multiplataforma (web, desktop e mobile) de gestão e rastreamento de hábitos pessoais, desenvolvido como Projeto Integrador do curso Técnico em Desenvolvimento de Sistemas do SENAC. O app tem como proposta central ajudar usuários a criarem, acompanharem e manterem hábitos em seu cotidiano, combinando simplicidade de uso com recursos de motivação e autoconhecimento, crescendo, assim, na vida de virtudes.

### 1.2 Objetivo do Projeto

Desenvolver um aplicativo multiplataforma funcional que permita ao usuário:

- Criar e organizar hábitos personalizados por categoria e frequência
- Realizar check-ins diários de forma rápida e intuitiva
- Acompanhar o progresso por meio de estatísticas e gráficos
- Manter a motivação por meio de streaks, recompensas e lembretes
- Registrar o humor diário e correlacionar com a consistência dos hábitos

### 1.3 Público-Alvo

O HabitGo é destinado a pessoas com 15 anos ou mais que desejam organizar melhor sua rotina, desenvolver novos hábitos ou superar hábitos negativos. O app atende perfis variados: estudantes, profissionais, atletas amadores e qualquer pessoa interessada em produtividade e bem-estar pessoal.

### 1.4 Justificativa

A formação de hábitos é a base para uma vida digna e respeitável. Entretanto, grande parte das pessoas encontra dificuldade em manter consistência sem ferramentas adequadas de acompanhamento e motivação. O HabitGo surge como solução acessível e completa, unindo rastreamento eficiente com recursos de engajamento que reduzem o abandono ao longo do tempo.

### 1.5 Aviso

O HabitGo não afirma categoricamente que todo usuário irá evoluir apenas por utilizar o aplicativo. Deve ficar claro que o crescimento e o desenvolvimento pessoal dependem exclusivamente do comprometimento e da disciplina de quem usa o sistema.

---

## 2. Requisitos do Sistema

### 2.1 Requisitos Funcionais

| ID    | Funcionalidade       | Descrição |
|-------|----------------------|-----------|
| RF01  | Cadastro de Hábito   | O usuário pode criar hábitos com nome livre, ícone, cor, categoria e frequência (diária, dias específicos ou X vezes por semana). |
| RF02  | Check-in Diário      | Interface para marcar hábitos concluídos no dia, com indicador de progresso (ex: 3 de 5 feitos). |
| RF03  | Streaks              | Contador de dias consecutivos por hábito, alerta de sequência em risco e registro do melhor recorde. |
| RF04  | Lembretes            | Horário personalizado por hábito, notificação motivacional/de lembrete ao longo do dia e resumo semanal de desempenho. |
| RF05  | Estatísticas         | Gráfico semanal/mensal, heatmap de atividade, taxa de conclusão e comparativo entre semanas. |
| RF06  | Categorias           | Categorias predefinidas: Saúde, Produtividade, Aprendizado, Relacionamentos, Finanças e Personalizada. |
| RF07  | Recompensas          | Medalhas por marcos (7, 30, 100 dias), pontos por consistência, desafios temporários e nível de usuário. |
| RF08  | Registro de Humor    | Registro emocional diário opcional com histórico e correlação entre humor e consistência de hábitos. |
| RF09  | Cadastro de Usuário  | O usuário pode criar uma conta com nome, e-mail e senha, e fazer login no aplicativo. |
| RF10  | Edição e Exclusão    | O usuário pode editar ou excluir hábitos cadastrados a qualquer momento. |

### 2.2 Requisitos Não Funcionais

| ID     | Categoria        | Descrição |
|--------|------------------|-----------|
| RNF01  | Desempenho       | O app deve carregar a tela principal em no máximo 2 segundos em conexão 4G. |
| RNF02  | Usabilidade      | A interface deve ser intuitiva, com fluxo de check-in realizável em no máximo 2 toques/cliques. |
| RNF03  | Segurança / LGPD | Dados sensíveis do usuário devem ser armazenados de forma criptografada e transmitidos via HTTPS. Senhas não devem ser salvas em texto plano. O sistema deve garantir ao usuário o direito de acessar, corrigir e excluir seus dados, em conformidade com a LGPD (Lei nº 13.709/2018). |
| RNF04  | Compatibilidade  | O app deve funcionar em Android 8.0+, iOS 13+, nos principais navegadores modernos (Chrome, Firefox, Safari, Edge) e em computadores de baixo desempenho. |
| RNF05  | Disponibilidade  | O sistema deve manter os dados do usuário disponíveis mesmo sem conexão com a internet (modo offline). |
| RNF06  | Escalabilidade   | A arquitetura deve suportar crescimento de usuários sem degradação significativa de desempenho. |

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
| UC06  | Consultar estatísticas  | O usuário acessa gráficos e heatmap de desempenho por período. |
| UC07  | Registrar humor         | O usuário registra seu estado emocional do dia de forma opcional. |
| UC08  | Receber notificação     | O sistema envia lembretes e alertas de streak em risco conforme configurado. |
| UC09  | Ganhar recompensa       | O sistema concede medalhas e pontos automaticamente ao atingir marcos. |
| UC10  | Editar/excluir hábito   | O usuário modifica ou remove um hábito existente. |

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
| Fluxo principal   | 1. Usuário acessa "Novo Hábito". 2. Preenche nome, categoria, frequência, ícone e cor. 3. Confirma a criação. 4. Sistema salva e exibe o hábito na tela principal. |
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
| Fluxo principal   | 1. Usuário acessa a tela de estatísticas. 2. Sistema exibe gráfico semanal/mensal, heatmap de atividade, taxa de conclusão e comparativo entre semanas. 3. Usuário pode filtrar por hábito ou período. |
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
| Fluxo principal   | 1. Sistema identifica hábitos com lembrete configurado para o horário atual. 2. Envia notificação ao usuário. 3. Ao fim do dia, envia resumo de desempenho. 4. Se um streak estiver em risco, envia alerta específico. |
| Fluxo alternativo | Se o usuário estiver com notificações desativadas no dispositivo, o sistema não envia alertas e exibe aviso nas configurações do app. |

#### UC09 — Ganhar Recompensa

| Campo             | Descrição |
|-------------------|-----------|
| Ator principal    | Sistema |
| Pré-condição      | Usuário autenticado e com hábitos em andamento. |
| Fluxo principal   | 1. Sistema detecta que o usuário atingiu um marco (ex: 7, 30 ou 100 dias consecutivos). 2. Concede automaticamente a medalha e os pontos correspondentes. 3. Exibe animação de celebração. 4. Atualiza o nível do usuário se aplicável. |
| Fluxo alternativo | Se o usuário já possuir a recompensa, o sistema não a concede novamente, mas registra o novo recorde. |

#### UC10 — Editar/Excluir Hábito

| Campo             | Descrição |
|-------------------|-----------|
| Ator principal    | Usuário |
| Pré-condição      | Usuário autenticado e com ao menos um hábito cadastrado. |
| Fluxo principal   | 1. Usuário acessa o hábito desejado. 2. Seleciona "Editar" ou "Excluir". 3a. Se editar: altera os dados desejados e confirma. O sistema salva as alterações. 3b. Se excluir: o sistema solicita confirmação. Após confirmação, o hábito e seu histórico são removidos. |
| Fluxo alternativo | Se o usuário cancelar a exclusão na confirmação, o sistema retorna ao hábito sem alterações. |

---

## 4. Diagramas UML

#### Diagrama de Casos de Uso

Ir para *HabitGo/docs/diagramas_uc*. Usamos arquivos .drawio/xxl

#### Diagrama de Classes

- A definir

---

## 5. Modelagem do Banco de Dados

### 5.1 Modelo Entidade-Relacionamento (MER)

- A definir

### 5.2 Dicionário de Dados 

- A definir

---

## 6. Protótipos de Telas

### 6.1 Telas Principais (pode mudar)

| Tela                   | Elementos Obrigatórios |
|------------------------|------------------------|
| Onboarding / Login     | Logotipo HabitGo, campos de e-mail e senha, botão de login e cadastro. |
| Tela Principal (Home)  | Lista de hábitos do dia, indicador de progresso (X de Y feitos), status de streak por hábito, botão de check-in. |
| Criar Hábito           | Campo de nome, seletor de categoria, seletor de frequência, picker de ícone e cor, botão salvar. |
| Estatísticas           | Gráfico de barras semanal, heatmap mensal, taxa de conclusão, comparativo de semanas. |
| Perfil e Recompensas   | Nível do usuário, pontos acumulados, galeria de medalhas conquistadas, histórico de desafios. |
| Registro de Humor      | Escala visual de humor (1-5), campo de observação opcional, histórico em timeline. |

---

## 7. Expansões Futuras

As funcionalidades abaixo estão planejadas para versões futuras do HabitGo, após a entrega do MVP (versão mínima funcional):

| Funcionalidade          | Descrição |
|-------------------------|-----------|
| Modo Desafio            | Desafios com duração fixa e celebração visual ao concluir. |
| Hábitos em Par          | Dois usuários acompanham o mesmo hábito juntos, com progresso compartilhado. |
| Hábitos Negativos       | Monitora comportamentos a eliminar com streak de dias sem recaída. |
| Reflexão Semanal        | Diário de progresso com 3 perguntas reflexivas toda semana. |
| Integração Saúde        | Conexão com Apple Health e Google Fit para check-in automático de hábitos de saúde. |
| Modo Foco               | Timer Pomodoro vinculado a um hábito de produtividade. |
| Widget                  | Marcar hábitos diretamente da tela inicial do celular sem abrir o app. |
| Exportação              | Exportar histórico de hábitos em PDF ou CSV para análise pessoal. |
| Onboarding Inteligente  | Sugestão de hábitos personalizados baseada nos objetivos do usuário no primeiro acesso. |
