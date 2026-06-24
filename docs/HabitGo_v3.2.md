# HabitGo

**Versão**: v3.2

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
6. [Requisitos Técnicos](#6-requisitos-tecnicos)

---

## 1. Introdução

### 1.1 Descrição Geral do Sistema

O HabitGo é um aplicativo multiplataforma (web, desktop e mobile) de gestão e rastreamento de hábitos pessoais. O app tem como proposta central ajudar usuários a criarem, acompanharem e manterem hábitos em seu cotidiano, principalmente pelas notificações/lembretes, combinando simplicidade de uso com recursos de motivação e autoconhecimento.

### 1.2 Objetivo do Projeto

Desenvolver um aplicativo multiplataforma funcional que permita ao usuário:

- Criar e organizar hábitos personalizados por categoria
- Realizar check-ins diários de forma rápida e intuitiva
- Acompanhar o progresso por meio de estatísticas e gráficos
- Manter a disciplina por meio de streaks e notificações
- Registrar o humor diário com histórico pessoal

### 1.3 Público-Alvo

O HabitGo é destinado a pessoas com 15 anos ou mais que desejam organizar melhor sua rotina, desenvolver novos hábitos ou superar hábitos negativos. O app atende perfis variados: estudantes, profissionais, atletas amadores e qualquer pessoa interessada em produtividade e bem-estar pessoal.

### 1.4 Justificativa

A formação de hábitos é a base para uma vida produtiva e ordenada. Entretanto, grande parte das pessoas encontra dificuldade em manter consistência sem ferramentas adequadas de acompanhamento e motivação. O HabitGo surge como solução acessível e completa, unindo rastreamento eficiente com recursos de engajamento que reduzem o abandono ao longo do tempo.

### 1.5 Limitações do Sistema

O HabitGo não afirma categoricamente que todo usuário irá evoluir apenas por utilizar o aplicativo. O crescimento e o desenvolvimento pessoal dependem do comprometimento e da disciplina de quem usa o sistema.

---

## 2. Requisitos do Sistema

### 2.1 Requisitos Funcionais

| ID   | Funcionalidade        | Descrição |
|------|-----------------------|-----------|
| RF01 | Cadastro de Hábito    | O usuário pode criar hábitos com nome livre, ícone, cor e categoria. |
| RF02 | Check-in Diário       | Interface para marcar hábitos concluídos no dia, com indicador de progresso (ex: 3 de 5 feitos) e exibição do streak atual calculado a partir do histórico de check-ins. |
| RF03 | Notificações          | Horário personalizado por hábito, notificação de lembrete ao longo do dia e resumo semanal de desempenho. |
| RF04 | Estatísticas          | Gráfico semanal/mensal, taxa de conclusão e comparativo entre semanas. |
| RF05 | Categorias            | Categorias predefinidas (Saúde, Produtividade, Aprendizado, Relacionamentos, Finanças) disponíveis a todos os usuários, com possibilidade de criação de categorias personalizadas. |
| RF06 | Registro de Humor     | Registro emocional diário opcional com histórico. |
| RF07 | Cadastro de Usuário   | O usuário pode criar uma conta com nome, e-mail e senha, editar seu perfil e excluir sua conta. |
| RF08 | Edição e Exclusão     | O usuário pode editar ou excluir hábitos cadastrados a qualquer momento. |
| RF09 | Log de Banco de Dados | O sistema deve registrar automaticamente um histórico de operações críticas (como criação, alteração e exclusão de usuários, hábitos e registros de check-in) para fins de auditoria, segurança e recuperação de dados. |

### 2.2 Requisitos Não Funcionais

| ID    | Categoria        | Descrição |
|-------|------------------|-----------|
| RNF01 | Desempenho       | O app deve carregar a tela principal sem atrasos perceptíveis. |
| RNF02 | Usabilidade      | A interface deve ser intuitiva, com fluxo de check-in realizável em no máximo 2 toques/cliques. |
| RNF03 | Segurança / LGPD | Dados sensíveis do usuário devem ser armazenados de forma criptografada e transmitidos via HTTPS. Senhas não devem ser salvas em texto plano. O sistema deve garantir ao usuário o direito de acessar, corrigir e excluir seus dados, em conformidade com a LGPD (Lei nº 13.709/2018). |
| RNF04 | Compatibilidade  | O app deve funcionar em Android, iOS, nos principais navegadores modernos (Chrome, Firefox, Safari, Edge) e em computadores de baixo desempenho. |
| RNF05 | Escalabilidade   | A arquitetura deve suportar crescimento de usuários sem degradação significativa de desempenho. |

---

## 3. Casos de Uso

### 3.1 Atores

- **Usuário:** pessoa que utiliza o aplicativo para gerenciar seus hábitos.
- **Sistema:** o próprio aplicativo HabitGo, responsável por processar e exibir dados.

### 3.2 Lista de Casos de Uso

| ID   | Caso de Uso              | Descrição |
|------|--------------------------|-----------|
| UC01 | Cadastrar usuário        | O usuário cria uma conta informando nome, e-mail e senha. |
| UC02 | Fazer login              | O usuário acessa o app com suas credenciais. |
| UC03 | Criar hábito             | O usuário configura um novo hábito com nome, categoria, ícone e cor. |
| UC04 | Realizar check-in        | O usuário marca um hábito como concluído no dia. |
| UC05 | Visualizar streak        | O usuário consulta o streak calculado a partir do histórico de check-ins. |
| UC06 | Consultar estatísticas   | O usuário acessa gráficos de desempenho por período. |
| UC07 | Registrar humor          | O usuário registra seu estado emocional do dia de forma opcional. |
| UC08 | Receber notificação      | O sistema envia lembretes conforme configurado. |
| UC09 | Editar/excluir hábito    | O usuário modifica ou remove um hábito existente. |
| UC10 | Visualizar hábito        | O usuário acessa os detalhes de um hábito específico. |
| UC11 | Editar perfil            | O usuário altera seus dados cadastrais. |
| UC12 | Excluir conta            | O usuário remove permanentemente sua conta e dados. |
| UC13 | Gerenciar categorias     | O usuário cria, edita ou exclui categorias personalizadas. |

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
| Fluxo principal   | 1. Usuário acessa a tela principal. 2. Visualiza a lista de hábitos do dia. 3. Marca um hábito como concluído. 4. Sistema registra o check-in e atualiza o indicador de progresso. |
| Fluxo alternativo | Se o usuário tentar fazer check-in em um hábito já concluído no dia, o sistema permite desmarcar a conclusão. |

#### UC05 — Visualizar Streak

| Campo             | Descrição |
|-------------------|-----------|
| Ator principal    | Usuário |
| Pré-condição      | Usuário autenticado e com ao menos um check-in registrado. |
| Fluxo principal   | 1. Usuário acessa o hábito desejado. 2. Sistema calcula o streak a partir do histórico de check-ins e exibe o contador de dias consecutivos atual e o melhor recorde histórico. |
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
| Fluxo principal   | 1. Usuário acessa o hábito desejado. 2. Seleciona "Editar" ou "Excluir". 3a. Se editar: altera os dados desejados e confirma. O sistema salva as alterações. 3b. Se excluir: o sistema solicita confirmação. Após confirmação, o hábito e seu histórico de check-ins são removidos. |
| Fluxo alternativo | Se o usuário cancelar a exclusão na confirmação, o sistema retorna ao hábito sem alterações. |

#### UC10 — Visualizar Hábito

| Campo             | Descrição |
|-------------------|-----------|
| Ator principal    | Usuário |
| Pré-condição      | Usuário autenticado e com ao menos um hábito cadastrado. |
| Fluxo principal   | 1. Usuário seleciona um hábito na tela principal. 2. Sistema exibe os detalhes do hábito: nome, ícone, cor e categoria. 3. Sistema calcula e exibe o streak atual, melhor recorde e histórico recente de check-ins. |
| Fluxo alternativo | Se o hábito não possuir nenhum check-in registrado, o sistema exibe os detalhes do hábito com streak zerado e histórico vazio. |

#### UC11 — Editar Perfil

| Campo             | Descrição |
|-------------------|-----------|
| Ator principal    | Usuário |
| Pré-condição      | Usuário autenticado no sistema. |
| Fluxo principal   | 1. Usuário acessa as configurações do perfil. 2. Altera nome, e-mail ou senha. 3. Confirma as alterações. 4. Sistema valida os dados e salva as mudanças. |
| Fluxo alternativo | Se o novo e-mail já estiver em uso por outro usuário, o sistema exibe mensagem de erro. Se a nova senha não atender aos requisitos mínimos, o sistema informa as regras e solicita nova senha. |

#### UC12 — Excluir Conta

| Campo             | Descrição |
|-------------------|-----------|
| Ator principal    | Usuário |
| Pré-condição      | Usuário autenticado no sistema. |
| Fluxo principal   | 1. Usuário acessa as configurações do perfil. 2. Seleciona "Excluir conta". 3. Sistema solicita confirmação e exige a senha atual. 4. Usuário confirma. 5. Sistema remove todos os dados do usuário e redireciona para a tela de cadastro. |
| Fluxo alternativo | Se a senha informada estiver incorreta, o sistema exibe mensagem de erro e cancela a operação. |

#### UC13 — Gerenciar Categorias

| Campo             | Descrição |
|-------------------|-----------|
| Ator principal    | Usuário |
| Pré-condição      | Usuário autenticado no sistema. |
| Fluxo principal   | 1. Usuário acessa a tela de configuração de hábitos. 2. Usuário acessa configuração de categorias. 3. Visualiza as categorias predefinidas e as suas próprias. 3a. Para criar: preenche nome, ícone e cor e confirma. 4a. Sistema salva e exibe a nova categoria. 3b. Para editar: seleciona uma categoria personalizada, altera os dados e confirma. 4b. Sistema salva as alterações. 3c. Para excluir: seleciona uma categoria personalizada e confirma a exclusão. 4c. Sistema remove a categoria. |
| Fluxo alternativo | Se a categoria excluída estiver vinculada a hábitos existentes, sistema exibe erro e sinaliza que categorias com hábitos vinculados não podem ser apagadas. |

---

## 4. Diagramas UML

### Diagrama de Casos de Uso

Ir para *HabitGo/docs/diagramas_uc*. Usamos arquivos drawio.

### Diagrama de Classes

- A definir

---

## 5. Modelagem do Banco de Dados

### 5.1 Modelo Entidade-Relacionamento (MER)

| Entidade | Atributos | Relacionamentos |
| :--- | :--- | :--- |
| usuario | id, nome, email, senha_hash, criado_em | 1 usuário possui N hábitos; 1 usuário possui N registros de humor; 1 usuário possui N dispositivos; 1 usuário está vinculado a N categorias através de `usuario_categoria` |
| categoria | id, nome, icone, cor, predefinida | 1 categoria possui N hábitos; 1 categoria está vinculada a N usuários através de `usuario_categoria` |
| usuario_categoria | id_usuario, id_categoria, criado_em | Tabela Associativa (N:N): Vincula os usuários às categorias que eles utilizam (tanto as globais quanto as personalizadas) |
| habito | id, nome, icone, cor, id_categoria, id_usuario, criado_em | 1 hábito pertence a 1 usuário; 1 hábito pertence a 1 categoria; 1 hábito possui N check-ins; 1 hábito possui N lembretes |
| checkin | id, id_habito, data, concluido | N check-ins pertencem a 1 hábito |
| humor | id, id_usuario, data, valor (1-5), observacao | N humores pertencem a 1 usuário |
| lembrete | id, id_habito, horario, ativo | N lembretes pertencem a 1 hábito |
| dispositivo | id, id_usuario, token_push, plataforma, criado_em | N dispositivos pertencem a 1 usuário |

> **Nota técnica:** A tabela associativa `usuario_categoria` implementa o relacionamento Muitos-para-Muitos (N:N) entre as tabelas `usuario` e `categoria`. Isso elimina a necessidade de chaves estrangeiras nulas (`null`) na tabela de categorias. Quando um novo usuário se cadastra, o sistema gera automaticamente os vínculos dele com as categorias globais (`predefinida = true`). Se o usuário criar uma categoria customizada, o sistema insere o registro em `categoria` (`predefinida = false`) e cria o vínculo exclusivo para este usuário.

> **Nota técnica:** A tabela `dispositivo` armazena os tokens push gerados pelo Firebase (Android), APNs (iOS) ou Web Push API (navegadores) no momento em que o usuário ativa as notificações. Cada token identifica um dispositivo específico, permitindo que o servidor entregue notificações ao usuário em todos os seus dispositivos.

> **Nota técnica:** O streak não é armazenado como tabela própria. Ele é calculado dinamicamente a partir do histórico de check-ins sempre que necessário, evitando inconsistências entre dados primários e derivados.

### 5.2 Dicionário de Dados

#### 5.2.1. Tabela: `usuarios`
Armazena as informações cadastrais e credenciais dos usuários do sistema.

| Campo | Tipo de Dado | Restrições | Descrição |
| :--- | :--- | :--- | :--- |
| `id` | BIGINT | PK, AUTO_INCREMENT | Identificador único do usuário. |
| `nome` | VARCHAR(100) | NOT NULL | Nome completo ou de exibição do usuário. |
| `email` | VARCHAR(150) | UNIQUE, NOT NULL | E-mail do usuário (usado para login e comunicação). |
| `senha_hash` | VARCHAR(255) | NOT NULL | Hash seguro da senha do usuário (nunca armazenada em texto plano). |
| `criado_em` | TIMESTAMP | DEFAULT NOW() | Data e hora em que a conta foi criada. |

#### 5.2.2. Tabela: `categorias`
Armazena tanto as categorias globais predefinidas pelo sistema quanto as customizadas pelos usuários.

| Campo | Tipo de Dado | Restrições | Descrição |
| :--- | :--- | :--- | :--- |
| `id` | INT | PK, AUTO_INCREMENT | Identificador único da categoria. |
| `nome` | VARCHAR(50) | NOT NULL | Nome da categoria (ex: Saúde, Finanças). |
| `icone` | VARCHAR(50) | NOT NULL | String identificadora do ícone (ex: 'heart', 'book'). |
| `cor` | VARCHAR(7) | NOT NULL | Código hexadecimal da cor associada (ex: '#FF5733'). |
| `predefinida` | BOOLEAN | DEFAULT FALSE | Indica se a categoria é global (`true`) ou personalizada (`false`). |

#### 5.2.3. Tabela: `usuario_categoria`
Gerencia o relacionamento Muitos para Muitos (N:N) entre usuários e as categorias às quais eles têm acesso ou que criaram de forma personalizada.

| Campo | Tipo de Dado | Restrições | Descrição |
| :--- | :--- | :--- | :--- |
| `id_usuario` | BIGINT | PK, FK (`usuario.id`) | Identificador do usuário relacionado. |
| `id_categoria` | INT | PK, FK (`categoria.id`) | Identificador da categoria relacionada. |
| `criado_em` | TIMESTAMP | DEFAULT NOW() | Data e hora em que o vínculo foi criado. |

#### 5.2.4. Tabela: `habitos`
Registra as configurações e detalhes dos hábitos criados pelos usuários.

| Campo | Tipo de Dado | Restrições | Descrição |
| :--- | :--- | :--- | :--- |
| `id` | BIGINT | PK, AUTO_INCREMENT | Identificador único do hábito. |
| `nome` | VARCHAR(100) | NOT NULL | Nome descritivo do hábito (ex: 'Beber 2L de água'). |
| `icone` | VARCHAR(50) | NOT NULL | Nome do ícone para estilização do hábito na interface. |
| `cor` | VARCHAR(7) | NOT NULL | Código hexadecimal da cor escolhida pelo usuário para o hábito. |
| `id_categoria` | INT | FK (`categoria.id`), NOT NULL | Categoria à qual este hábito pertence. |
| `id_usuario` | BIGINT | FK (`usuario.id`), NOT NULL | Usuário proprietário deste hábito. |
| `criado_em` | TIMESTAMP | DEFAULT NOW() | Data e hora de criação do hábito. |

#### 5.2.5. Tabela: `checkins`
Armazena o histórico diário de conclusões de cada hábito para o cálculo de métricas e streaks.

| Campo | Tipo de Dado | Restrições | Descrição |
| :--- | :--- | :--- | :--- |
| `id` | BIGINT | PK, AUTO_INCREMENT | Identificador único do check-in. |
| `id_habito` | BIGINT | FK (`habito.id`), NOT NULL | Hábito que foi marcado como concluído. |
| `data` | DATE | NOT NULL | Data em que o hábito foi realizado. |
| `concluido` | BOOLEAN | DEFAULT TRUE | Status da conclusão (permite marcar e desmarcar a atividade). |

#### 5.2.6. Tabela: `humores`
Registra o estado emocional diário opcional inserido pelo usuário.

| Campo | Tipo de Dado | Restrições | Descrição |
| :--- | :--- | :--- | :--- |
| `id` | BIGINT | PK, AUTO_INCREMENT | Identificador único do registro de humor. |
| `id_usuario` | BIGINT | FK (`usuario.id`), NOT NULL | Usuário que realizou o registro emocional. |
| `data` | DATE | NOT NULL | Data do registro do humor (restrito a apenas um por dia por usuário). |
| `valor` | INT | NOT NULL (CHECK 1-5) | Avaliação do humor na escala de 1 (Muito Ruim) a 5 (Excelente). |
| `observacao` | TEXT | NULL | Notas, diário ou comentários opcionais sobre o dia do usuário. |

#### 5.2.7. Tabela: `lembretes`
Guarda os horários de disparos de notificações configurados pelo usuário para cada hábito.

| Campo | Tipo de Dado | Restrições | Descrição |
| :--- | :--- | :--- | :--- |
| `id` | BIGINT | PK, AUTO_INCREMENT | Identificador único do lembrete. |
| `id_habito` | BIGINT | FK (`habito.id`), NOT NULL | Hábito associado ao lembrete de notificação. |
| `horario` | TIME | NOT NULL | Horário programado para disparar o alarme (HH:MM:SS). |
| `ativo` | BOOLEAN | DEFAULT TRUE | Define se o lembrete específico está ligado ou desligado. |

#### 5.2.8. Tabela: `dispositivos`
Armazena tokens de push notification para vincular múltiplos aparelhos a uma única conta de usuário.

| Campo | Tipo de Dado | Restrições | Descrição |
| :--- | :--- | :--- | :--- |
| `id` | BIGINT | PK, AUTO_INCREMENT | Identificador único do dispositivo. |
| `id_usuario` | BIGINT | FK (`usuario.id`), NOT NULL | Usuário proprietário do dispositivo. |
| `token_push` | VARCHAR(255) | NOT NULL, UNIQUE | Token único gerado pelo Firebase (FCM), APNs ou Web Push. |
| `plataforma` | VARCHAR(20) | NOT NULL | Identifica o SO do dispositivo (ex: 'android', 'ios', 'web'). |
| `criado_em` | TIMESTAMP | DEFAULT NOW() | Data de registro/vinculação do dispositivo ao sistema. |

---

## 6. Requisitos Técnicos

- A definir





<!--
ATENÇÃO GRUPO: Decisão sobre Criptografia do Nome do Hábito

Por que NÃO criptografamos o nome do hábito diretamente no banco de dados (via código)?
 - Destruição do Desempenho (RNF01): O banco de dados perderia a capacidade de usar índices de texto. Consultas simples como `WHERE nome LIKE '%agua%'` deixariam de funcionar.
 - Complexidade Inútil: Para ordenar os hábitos por ordem alfabética, o backend teria que baixar todos os registros do banco, descriptografar um por um na memória do servidor e só então ordenar. Isso inviabilizaria o app em escala.

Como garantimos a privacidade e conformidade com a LGPD (RNF03) sem perder desempenho?
 1. Criptografia em Repouso (Encryption at Rest): Ativada diretamente no servidor do banco de dados (PostgreSQL/MySQL). Se alguém invadir o servidor e roubar o HD, os dados estarão ilegíveis.
 2. Criptografia em Trânsito: Uso obrigatório de HTTPS para impedir interceptação de dados na rede.
 3. Isolamento Rígido de Rotas: A API valida estritamente o token do usuário. O Usuário X nunca tem permissão de ler ou alterar dados do Usuário Y.


Comentario gerado com IA. Estava discutindo sobre a privacidade do usuario quanto aos nomes de um habito (as vezes, um usuario pode nao querer mostrar o que ele precisa melhorar)
-- Lorenzo
-->