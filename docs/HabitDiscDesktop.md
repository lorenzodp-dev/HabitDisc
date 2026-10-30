# HabitDisc — Versão Desktop

**Versão**: v5.0 (Desktop)

**Membros**
Lorenzo, Felipe, Enzo, João Pedro e Maycon

> Esta documentação cobre **somente a versão desktop** (C# / Windows Forms). As versões web e mobile terão documentação própria, a ser escrita separadamente.

---

## Sumário

1. [Introdução](#1-introdução)
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

O HabitDisc Desktop é um aplicativo para Windows, desenvolvido em C# com Windows Forms, de gestão e rastreamento de hábitos pessoais. O app tem como proposta central ajudar o usuário a criar, acompanhar e manter hábitos em seu cotidiano, principalmente pelos lembretes, combinando simplicidade de uso com recursos de motivação e autoconhecimento.

### 1.2 Objetivo do Projeto

Desenvolver um aplicativo desktop funcional que permita ao usuário:

- Criar e organizar hábitos personalizados por categoria
- Realizar check-ins diários de forma rápida e intuitiva
- Acompanhar o progresso por meio de estatísticas e gráficos
- Manter a disciplina por meio de streaks e lembretes
- Registrar o humor diário com histórico pessoal

### 1.3 Público-Alvo

O HabitDisc é destinado a pessoas com 15 anos ou mais que desejam organizar melhor sua rotina, desenvolver novos hábitos ou superar hábitos negativos. O app atende perfis variados: estudantes, profissionais, atletas amadores e qualquer pessoa interessada em produtividade e bem-estar pessoal.

### 1.4 Justificativa

A formação de hábitos é a base para uma vida produtiva e ordenada. Entretanto, grande parte das pessoas encontra dificuldade em manter consistência sem ferramentas adequadas de acompanhamento e motivação. O HabitDisc surge como solução acessível e completa, unindo rastreamento eficiente com recursos de engajamento que reduzem o abandono ao longo do tempo.

### 1.5 Limitações do Sistema

O HabitDisc não afirma categoricamente que todo usuário irá evoluir apenas por utilizar o aplicativo. O crescimento e o desenvolvimento pessoal dependem do comprometimento e da disciplina de quem usa o sistema.

### 1.6 Escopo desta Versão

- Uso individual: **um único usuário por instalação**, sem cadastro, login ou conta.
- Sem sincronização entre dispositivos: os dados ficam no banco MySQL configurado para a instalação.
- Plataforma exclusiva: Windows.

---

## 2. Requisitos do Sistema

### 2.1 Requisitos Funcionais

| ID   | Funcionalidade        | Descrição |
|------|-----------------------|-----------|
| RF01 | Cadastro de Hábito    | O usuário pode criar hábitos com nome livre, ícone, cor e categoria. |
| RF02 | Check-in Diário       | Interface para marcar hábitos concluídos no dia, com indicador de progresso (ex: 3 de 5 feitos) e exibição do streak atual calculado a partir do histórico de check-ins. |
| RF03 | Lembretes             | Horário personalizado por hábito, com notificação do Windows no horário configurado enquanto o aplicativo estiver em execução, e resumo semanal de desempenho exibido dentro do aplicativo. |
| RF04 | Estatísticas          | Gráfico semanal/mensal, taxa de conclusão e comparativo entre semanas. |
| RF05 | Categorias            | Categorias predefinidas (Saúde, Produtividade, Aprendizado, Relacionamentos, Finanças), com possibilidade de criação de categorias personalizadas. |
| RF06 | Registro de Humor     | Registro emocional diário opcional com histórico. |
| RF07 | Edição e Exclusão     | O usuário pode editar ou excluir hábitos cadastrados a qualquer momento. |
| RF08 | Log de Banco de Dados | O sistema deve registrar automaticamente um histórico de operações críticas (como criação, alteração e exclusão de hábitos, categorias personalizadas e registros de check-in) para fins de auditoria e recuperação de dados. |

### 2.2 Requisitos Não Funcionais

| ID    | Categoria              | Descrição |
|-------|------------------------|-----------|
| RNF01 | Desempenho             | O app deve abrir a tela inicial e alternar entre as telas sem atrasos perceptíveis. |
| RNF02 | Usabilidade            | A interface deve ser intuitiva, com fluxo de check-in realizável em no máximo 2 cliques. |
| RNF03 | Segurança e Privacidade | O app não coleta dados de identificação pessoal (nome, e-mail etc.) e não envia dados a terceiros. Os dados ficam no banco MySQL configurado, com criptografia em repouso habilitada no servidor do banco. A string de conexão não deve ficar fixa no código-fonte. O usuário pode excluir seus hábitos e registros a qualquer momento (RF07), em alinhamento com a LGPD (Lei nº 13.709/2018). |
| RNF04 | Compatibilidade        | O app deve funcionar em Windows 10 ou superior, inclusive em computadores de baixo desempenho. |
| RNF05 | Volume de Dados        | O histórico de check-ins e humores pode crescer por anos sem degradação perceptível de desempenho (uso de índices nas colunas consultadas com mais frequência, como `id_habito` e `data`). |

---

## 3. Casos de Uso

### 3.1 Atores

- **Usuário:** pessoa que utiliza o aplicativo para gerenciar seus hábitos.
- **Sistema:** o próprio aplicativo HabitDisc, responsável por processar e exibir dados.

### 3.2 Lista de Casos de Uso

| ID   | Caso de Uso              | Descrição |
|------|--------------------------|-----------|
| UC01 | Criar hábito             | O usuário configura um novo hábito com nome, categoria, ícone e cor. |
| UC02 | Realizar check-in        | O usuário marca um hábito como concluído no dia. |
| UC03 | Visualizar streak        | O usuário consulta o streak calculado a partir do histórico de check-ins. |
| UC04 | Consultar estatísticas   | O usuário acessa gráficos de desempenho por período. |
| UC05 | Registrar humor          | O usuário registra seu estado emocional do dia de forma opcional. |
| UC06 | Receber notificação      | O sistema exibe lembretes conforme configurado. |
| UC07 | Editar/excluir hábito    | O usuário modifica ou remove um hábito existente. |
| UC08 | Visualizar hábito        | O usuário acessa os detalhes de um hábito específico. |
| UC09 | Gerenciar categorias     | O usuário cria, edita ou exclui categorias personalizadas. |

### 3.3 Descrições Expandidas dos Casos de Uso

#### UC01 — Criar Hábito

| Campo             | Descrição |
|-------------------|-----------|
| Ator principal    | Usuário |
| Pré-condição      | Aplicativo em execução. |
| Fluxo principal   | 1. Usuário acessa "Novo Hábito". 2. Preenche nome, categoria, ícone e cor. 3. Confirma a criação. 4. Sistema salva e exibe o hábito na lista de hábitos. |
| Fluxo alternativo | Se o usuário não preencher o nome, o sistema exibe mensagem de erro e solicita preenchimento. |

#### UC02 — Realizar Check-in

| Campo             | Descrição |
|-------------------|-----------|
| Ator principal    | Usuário |
| Pré-condição      | Ao menos um hábito cadastrado. |
| Fluxo principal   | 1. Usuário acessa a tela inicial. 2. Visualiza a lista de hábitos do dia. 3. Marca um hábito como concluído. 4. Sistema registra o check-in e atualiza o indicador de progresso. |
| Fluxo alternativo | Se o usuário tentar fazer check-in em um hábito já concluído no dia, o sistema permite desmarcar a conclusão. |

#### UC03 — Visualizar Streak

| Campo             | Descrição |
|-------------------|-----------|
| Ator principal    | Usuário |
| Pré-condição      | Ao menos um check-in registrado. |
| Fluxo principal   | 1. Usuário acessa o hábito desejado. 2. Sistema calcula o streak a partir do histórico de check-ins e exibe o contador de dias consecutivos atual e o melhor recorde histórico. |
| Fluxo alternativo | Se o usuário não realizou check-in no dia anterior, o sistema exibe o streak zerado e o recorde anterior como histórico. |

#### UC04 — Consultar Estatísticas

| Campo             | Descrição |
|-------------------|-----------|
| Ator principal    | Usuário |
| Pré-condição      | Ao menos uma semana de check-ins registrados. |
| Fluxo principal   | 1. Usuário acessa a tela de estatísticas. 2. Sistema exibe gráfico semanal/mensal, taxa de conclusão e comparativo entre semanas. 3. Usuário pode filtrar por hábito ou período. |
| Fluxo alternativo | Se não houver dados suficientes, o sistema exibe mensagem orientando o usuário a registrar hábitos por mais dias. |

#### UC05 — Registrar Humor

| Campo             | Descrição |
|-------------------|-----------|
| Ator principal    | Usuário |
| Pré-condição      | Aplicativo em execução. |
| Fluxo principal   | 1. Usuário acessa a tela de registro de humor. 2. Seleciona seu estado emocional na escala de 1 a 5. 3. Opcionalmente, adiciona uma observação escrita. 4. Confirma o registro. 5. Sistema salva e exibe o histórico atualizado. |
| Fluxo alternativo | Se o usuário já registrou o humor no dia, o sistema permite editar o registro existente. |

#### UC06 — Receber Notificação

| Campo             | Descrição |
|-------------------|-----------|
| Ator principal    | Sistema |
| Pré-condição      | Aplicativo em execução, com hábitos cadastrados e ao menos um lembrete ativo. |
| Fluxo principal   | 1. Sistema identifica hábitos com lembrete configurado para o horário atual. 2. Exibe a notificação do Windows ao usuário. 3. O resumo semanal de desempenho fica disponível dentro do aplicativo. |
| Fluxo alternativo | Se as notificações do Windows estiverem desativadas, o sistema não consegue exibir o alerta e mostra um aviso dentro do aplicativo. |

#### UC07 — Editar/Excluir Hábito

| Campo             | Descrição |
|-------------------|-----------|
| Ator principal    | Usuário |
| Pré-condição      | Ao menos um hábito cadastrado. |
| Fluxo principal   | 1. Usuário acessa o hábito desejado. 2. Seleciona "Editar" ou "Excluir". 3a. Se editar: altera os dados desejados e confirma. O sistema salva as alterações. 3b. Se excluir: o sistema solicita confirmação. Após confirmação, o hábito e seus dados associados (check-ins e lembretes) são removidos. |
| Fluxo alternativo | Se o usuário cancelar a exclusão na confirmação, o sistema retorna ao hábito sem alterações. |

#### UC08 — Visualizar Hábito

| Campo             | Descrição |
|-------------------|-----------|
| Ator principal    | Usuário |
| Pré-condição      | Ao menos um hábito cadastrado. |
| Fluxo principal   | 1. Usuário seleciona um hábito na lista. 2. Sistema exibe os detalhes do hábito: nome, ícone, cor e categoria. 3. Sistema calcula e exibe o streak atual, melhor recorde e histórico recente de check-ins. |
| Fluxo alternativo | Se o hábito não possuir nenhum check-in registrado, o sistema exibe os detalhes do hábito com streak zerado e histórico vazio. |

#### UC09 — Gerenciar Categorias

| Campo             | Descrição |
|-------------------|-----------|
| Ator principal    | Usuário |
| Pré-condição      | Aplicativo em execução. |
| Fluxo principal   | 1. Usuário acessa a tela de categorias. 2. Visualiza as categorias predefinidas e as suas próprias. 2a. Para criar: preenche nome, ícone e cor e confirma. 3a. Sistema salva e exibe a nova categoria. 2b. Para editar: seleciona uma categoria personalizada, altera os dados e confirma. 3b. Sistema salva as alterações. 2c. Para excluir: seleciona uma categoria personalizada e confirma a exclusão. 3c. Sistema remove a categoria. |
| Fluxo alternativo | Se a categoria excluída estiver vinculada a hábitos existentes, o sistema exibe erro e sinaliza que categorias com hábitos vinculados não podem ser apagadas. Categorias predefinidas não podem ser editadas nem excluídas. |

---

## 4. Diagramas UML

### Diagrama de Casos de Uso

Ir para *HabitDisc/docs/diagramas_uc*. Usamos arquivos drawio.

> **Atenção:** os diagramas existentes foram feitos para a versão anterior. É necessário removê-los dos casos de uso de cadastro, login, edição de perfil e exclusão de conta, e atualizar a numeração (UC01 a UC09) conforme a seção 3.

### Diagrama de Classes

- A definir

---

## 5. Modelagem do Banco de Dados

### 5.1 Modelo Entidade-Relacionamento (MER)

| Entidade | Atributos | Relacionamentos |
| :--- | :--- | :--- |
| categorias | id, nome, icone, cor, predefinida | 1 categoria possui N hábitos |
| habitos | id, nome, icone, cor, id_categoria, criado_em | 1 hábito pertence a 1 categoria; 1 hábito possui N check-ins; 1 hábito possui N lembretes |
| checkins | id, id_habito, data, concluido | N check-ins pertencem a 1 hábito |
| humores | id, data, valor (1-5), observacao | Sem relacionamentos (um registro por dia) |
| lembretes | id, id_habito, horario, ativo | N lembretes pertencem a 1 hábito |

> **Nota técnica:** Por ser uma versão de usuário único, não existem as tabelas de usuário, vínculo usuário-categoria e dispositivo da versão multiplataforma. Todos os registros pertencem implicitamente ao único usuário da instalação.

> **Nota técnica:** As categorias predefinidas (`predefinida = true`) são inseridas pelo script do banco de dados. As categorias criadas pelo usuário são gravadas com `predefinida = false`. A exclusão de uma categoria com hábitos vinculados deve ser bloqueada (chave estrangeira com `ON DELETE RESTRICT`).

> **Nota técnica:** O streak não é armazenado como tabela própria. Ele é calculado dinamicamente a partir do histórico de check-ins sempre que necessário, evitando inconsistências entre dados primários e derivados.

### 5.2 Dicionário de Dados

#### 5.2.1. Tabela: `categorias`
Armazena as categorias predefinidas pelo sistema e as personalizadas pelo usuário.

| Campo | Tipo de Dado | Restrições | Descrição |
| :--- | :--- | :--- | :--- |
| `id` | INT | PK, AUTO_INCREMENT | Identificador único da categoria. |
| `nome` | VARCHAR(50) | NOT NULL | Nome da categoria (ex: Saúde, Finanças). |
| `icone` | VARCHAR(50) | NOT NULL | String identificadora do ícone (ex: 'heart', 'book'). |
| `cor` | VARCHAR(7) | NOT NULL | Código hexadecimal da cor associada (ex: '#FF5733'). |
| `predefinida` | BOOLEAN | DEFAULT FALSE | Indica se a categoria é predefinida (`true`) ou personalizada (`false`). |

#### 5.2.2. Tabela: `habitos`
Registra as configurações e detalhes dos hábitos criados pelo usuário.

| Campo | Tipo de Dado | Restrições | Descrição |
| :--- | :--- | :--- | :--- |
| `id` | BIGINT | PK, AUTO_INCREMENT | Identificador único do hábito. |
| `nome` | VARCHAR(100) | NOT NULL | Nome descritivo do hábito (ex: 'Beber 2L de água'). |
| `icone` | VARCHAR(50) | NOT NULL | Nome do ícone para estilização do hábito na interface. |
| `cor` | VARCHAR(7) | NOT NULL | Código hexadecimal da cor escolhida pelo usuário para o hábito. |
| `id_categoria` | INT | FK (`categorias.id`), NOT NULL | Categoria à qual este hábito pertence. |
| `criado_em` | TIMESTAMP | DEFAULT NOW() | Data e hora de criação do hábito. |

#### 5.2.3. Tabela: `checkins`
Armazena o histórico diário de conclusões de cada hábito para o cálculo de métricas e streaks.

| Campo | Tipo de Dado | Restrições | Descrição |
| :--- | :--- | :--- | :--- |
| `id` | BIGINT | PK, AUTO_INCREMENT | Identificador único do check-in. |
| `id_habito` | BIGINT | FK (`habitos.id`), NOT NULL | Hábito que foi marcado como concluído. |
| `data` | DATE | NOT NULL | Data em que o hábito foi realizado. Combinação (`id_habito`, `data`) única: um registro por hábito por dia. |
| `concluido` | BOOLEAN | DEFAULT TRUE | Status da conclusão (permite marcar e desmarcar a atividade). |

#### 5.2.4. Tabela: `humores`
Registra o estado emocional diário opcional inserido pelo usuário.

| Campo | Tipo de Dado | Restrições | Descrição |
| :--- | :--- | :--- | :--- |
| `id` | BIGINT | PK, AUTO_INCREMENT | Identificador único do registro de humor. |
| `data` | DATE | NOT NULL, UNIQUE | Data do registro do humor (apenas um por dia). |
| `valor` | INT | NOT NULL (CHECK 1-5) | Avaliação do humor na escala de 1 (Muito Ruim) a 5 (Excelente). |
| `observacao` | TEXT | NULL | Notas, diário ou comentários opcionais sobre o dia. |

#### 5.2.5. Tabela: `lembretes`
Guarda os horários de disparo de notificações configurados pelo usuário para cada hábito.

| Campo | Tipo de Dado | Restrições | Descrição |
| :--- | :--- | :--- | :--- |
| `id` | BIGINT | PK, AUTO_INCREMENT | Identificador único do lembrete. |
| `id_habito` | BIGINT | FK (`habitos.id`), NOT NULL | Hábito associado ao lembrete. |
| `horario` | TIME | NOT NULL | Horário programado para disparar a notificação (HH:MM:SS). |
| `ativo` | BOOLEAN | DEFAULT TRUE | Define se o lembrete específico está ligado ou desligado. |

#### 5.2.6. Log de operações (RF08)
- A definir: estrutura da tabela de auditoria e das triggers que a alimentam, junto ao script do banco de dados.

---

## 6. Requisitos Técnicos

### 6.1 Plataforma

| Item | Definição |
| :--- | :--- |
| Linguagem | C# |
| Interface | Windows Forms |
| Runtime | .NET 10 (LTS), alvo `net10.0-windows` (confirmar a versão instalada no ambiente de desenvolvimento) |
| Sistema operacional | Windows 10 ou superior |

### 6.2 Banco de Dados e ORM

- **Banco:** MySQL 8.x, acessível pelo computador onde o aplicativo é executado.
- **ORM:** Entity Framework Core, com o provedor Pomelo para MySQL.
- **Abordagem de mapeamento:** a definir (Database First com Data Annotations ou Code First).

**Compatibilidade de versões (verificada em outubro de 2026).** O provedor Pomelo ainda não possui versão para o EF Core 10: a última versão publicada é a 9.0.0, que aceita apenas o EF Core 9.x. Misturar o Pomelo 9 com pacotes EF Core 10 gera erro de restauração (NU1107) ou aviso (NU1608) e falha em tempo de execução (`MissingMethodException`). Opções:

| Opção | Pacote de banco | Pacotes EF Core | Observação |
| :--- | :--- | :--- | :--- |
| A (recomendada) | `Pomelo.EntityFrameworkCore.MySql` 9.0.0 | Todos em 9.0.x (`Microsoft.EntityFrameworkCore`, `.Design`, `.Tools`) | Funciona em projetos `net10.0`. O suporte do EF Core 9 (STS) termina em 10/11/2026, então serve como ponte até o Pomelo lançar a versão 10. |
| B | `Microting.EntityFrameworkCore.MySql` 10.x | Todos em 10.0.x | Fork comunitário do Pomelo, com namespaces renomeados (`Microting.*`). |
| C | `MySql.EntityFrameworkCore` 10.x (Oracle) | Todos em 10.0.x | Provedor diferente, com API e tradução de consultas diferentes (`UseMySQL`). |

Regras para qualquer opção:
- Manter **todos** os pacotes `Microsoft.EntityFrameworkCore.*` na mesma versão major do provedor.
- Não suprimir o aviso NU1608 (`NoWarn`): o projeto compila e falha ao iniciar.
- Manter a ferramenta `dotnet-ef` na mesma major dos pacotes do projeto.
- Verificar a compatibilidade novamente antes de atualizar qualquer pacote.

### 6.3 Arquitetura da Interface (Navegação)

Decisões tomadas para a versão desktop:

1. Navegação por **Panel + UserControl**, no lugar do MdiContainer.
2. O `MainForm` é uma "casca" fixa: painel de navegação à esquerda e painel de conteúdo ocupando o restante.
3. A tela **Home** é carregada ao iniciar.
4. A lógica de troca de tela fica em métodos do próprio `MainForm`, que é o dono do painel de conteúdo. Não são usadas `IUserControl` nem classes `...Services` para isso.
5. Os parâmetros desses métodos são do tipo `UserControl`, para aceitar qualquer tela (polimorfismo).
6. As telas são criadas e **reaproveitadas**, em vez de uma instância nova a cada clique.

Telas do menu lateral:

| Tela | Casos de uso atendidos |
| :--- | :--- |
| Home | UC02 (check-in do dia e progresso) |
| Hábitos | UC01, UC03, UC07, UC08 |
| Estatísticas | UC04 |
| Humor | UC05 |
| Categorias | UC09 |

O UC06 (notificação) é executado pelo sistema e não possui tela própria.

Pendente: definir como cada tela atualiza seus dados ao ser exibida novamente.

### 6.4 Estrutura de Camadas

- A definir

### 6.5 Gráficos

- A definir (biblioteca de gráficos para a tela de Estatísticas)

<!--
ATENÇÃO GRUPO: Decisão sobre Criptografia do Nome do Hábito

Por que NÃO criptografamos o nome do hábito diretamente no banco de dados (via código)?
 - Destruição do Desempenho (RNF01): O banco de dados perderia a capacidade de usar índices de texto. Consultas simples como `WHERE nome LIKE '%agua%'` deixariam de funcionar.
 - Complexidade Inútil: Para ordenar os hábitos por ordem alfabética, o aplicativo teria que carregar todos os registros do banco, descriptografar um por um na memória e só então ordenar. Isso inviabilizaria o app com histórico grande.

Como garantimos a privacidade e conformidade com a LGPD (RNF03) sem perder desempenho?
 1. Criptografia em Repouso (Encryption at Rest): Ativada diretamente no servidor do banco de dados (MySQL). Se alguém roubar o HD, os dados estarão ilegíveis.
 2. Conexão protegida: Se o MySQL estiver em outra máquina, usar conexão com SSL/TLS. Se estiver na própria máquina, não há tráfego de rede a proteger.
 3. Sem dados de identificação: A versão desktop não guarda nome nem e-mail, então os hábitos não ficam associados a uma pessoa identificável.

Comentario gerado com IA. Estava discutindo sobre a privacidade do usuario quanto aos nomes de um habito (as vezes, um usuario pode nao querer mostrar o que ele precisa melhorar)
-- Lorenzo
(Adaptado para a versão desktop.)
-->
