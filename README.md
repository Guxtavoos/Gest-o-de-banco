# Sistema de Gestão de Relacionamento com o Cliente (CRM)

## Descrição do Projeto
Este projeto implementa as estruturas e dados de um banco de dados para um sistema de gestão de relacionamento com o cliente (CRM). O banco de dados foi projetado para armazenar informações sobre clientes, campanhas de marketing e interações realizadas com os clientes.

## Estrutura do Banco de Dados
O banco de dados é composto por três tabelas principais:

### 1. CLIENTES
Tabela que armazena as informações básicas dos clientes.
- **CLIENTE_ID** (NUMBER NOT NULL): Identificador único do cliente (chave primária).
- **NOME** (VARCHAR2(100) NOT NULL): Nome do cliente.
- **EMAIL** (VARCHAR2(100)): Endereço de e-mail do cliente (opcional).
- **TELEFONE** (VARCHAR2(15)): Telefone do cliente.
- **DATA_CADASTRO** (DATE): Data de cadastro do cliente no sistema.

### 2. CAMPANHAS
Tabela que armazena informações sobre campanhas de marketing.
- **CAMPANHA_ID** (NUMBER NOT NULL): Identificador único da campanha (chave primária).
- **NOME** (VARCHAR2(100) NOT NULL): Nome da campanha.
- **DATA_INICIO** (DATE): Data de início da campanha.
- **DATA_FIM** (DATE): Data de término da campanha.
- **ORCAMENTO** (NUMBER(10, 2)): Orçamento alocado para a campanha.

### 3. INTERACOES
Tabela que registra as interações realizadas com os clientes no contexto de campanhas.
- **INTERACAO_ID** (NUMBER NOT NULL): Identificador único da interação (chave primária).
- **CLIENTE_ID** (NUMBER NOT NULL): Identificador do cliente (chave estrangeira para `CLIENTES.CLIENTE_ID`).
- **CAMPANHA_ID** (NUMBER NOT NULL): Identificador da campanha (chave estrangeira para `CAMPANHAS.CAMPANHA_ID`).
- **DATA_INTERACAO** (DATE): Data da interação.
- **TIPO** (VARCHAR2(50)): Tipo da interação (ex.: E-mail, Telefone, SMS).
- **METRICA** (VARCHAR2(100)): Métrica avaliada (ex.: Taxa de Abertura, Conversão).
- **VALOR** (NUMBER): Valor associado à métrica.

## Como Executar os Scripts
### Pré-requisitos
- Oracle Database instalado.
- Ferramenta de gerenciamento (SQL*Plus, SQL Developer, ou equivalente).
- Permissões adequadas para criar usuários, tabelas e inserir dados.

### Passos
1. Faça o download dos scripts `estrutura.sql` e `dados.sql` do repositório.
2. No Oracle, execute os comandos para criar o usuário e o esquema:
   ```sql
   CREATE USER USR_CRM IDENTIFIED BY senha_default;
   GRANT CONNECT, RESOURCE TO USR_CRM;
   ALTER SESSION SET CURRENT_SCHEMA = USR_CRM;

