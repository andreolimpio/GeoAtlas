# 🗄️ Banco de Dados — GeoAtlas

Esta pasta contém os arquivos relacionados ao banco de dados do **GeoAtlas**, incluindo a modelagem, os scripts SQL de criação e manutenção da estrutura e os dados utilizados para inicialização do sistema.

O banco de dados constitui a camada central de persistência do GeoAtlas e será compartilhado pelas diferentes aplicações Web e Mobile desenvolvidas no projeto.

---

## 🎯 Objetivo

O banco de dados do GeoAtlas tem como objetivo armazenar e organizar informações geográficas, administrativas e operacionais utilizadas pelas diferentes versões da aplicação.

Uma das principais características da arquitetura do projeto é a utilização de **uma única estrutura de banco de dados**, independentemente da tecnologia utilizada nas aplicações clientes.

Dessa forma, diferentes implementações poderão consumir e manipular os mesmos dados.

```text
                         GeoAtlas
                            │
                ┌───────────┴───────────┐
                │                       │
               Web                    Mobile
                │                       │
        ┌───────┴───────┐       ┌───────┴────────┐
        │               │       │                │
       PHP           Node.js   React Native    Android
        │               │       │                │
        └─────────────── APIs / Back-end ────────┘
                            │
                            ▼
                         MySQL
                            │
                            ▼
                       bd_geoatlas
```

---

## 🛠️ Tecnologias

O banco de dados do GeoAtlas utiliza as seguintes tecnologias:

* **MySQL** — Sistema Gerenciador de Banco de Dados Relacional.
* **MySQL Workbench** — ferramenta utilizada para modelagem, administração e desenvolvimento do banco.
* **SQL** — linguagem utilizada para definição, manipulação e consulta dos dados.

---

## 🗃️ Banco de Dados

Nome do banco:

```sql
bd_geoatlas
```

O banco foi projetado utilizando o modelo relacional e possui relacionamentos entre suas entidades por meio de **chaves primárias (Primary Keys)** e **chaves estrangeiras (Foreign Keys)**.

---

## 📊 Principais Entidades

A versão inicial do banco de dados é composta pelas seguintes entidades:

### Continentes

Armazena informações relacionadas aos continentes utilizados para organização geográfica dos países.

### Países

Armazena informações dos países cadastrados no GeoAtlas.

Cada país está associado a um continente e poderá possuir diferentes cidades e governantes relacionados.

### Cidades

Armazena informações referentes às cidades.

Cada cidade pertence a um determinado país.

### Governantes

Mantém informações sobre os governantes associados aos países.

A estrutura permite manter o histórico de governantes e seus respectivos períodos de mandato.

### Usuários

Armazena os usuários autorizados a acessar funcionalidades específicas do sistema.

Essa entidade será utilizada posteriormente pelos mecanismos de autenticação e autorização das aplicações.

### Logs

Registra operações realizadas pelos usuários no sistema.

Os registros de log poderão ser utilizados para auditoria, rastreabilidade e análise das operações realizadas nas aplicações.

---

## 🔗 Relacionamentos Principais

A estrutura inicial possui os seguintes relacionamentos:

```text
CONTINENTES
     │
     │ 1:N
     ▼
   PAÍSES
     │
     ├──────────────────┐
     │                  │
     │ 1:N              │ 1:N
     ▼                  ▼
  CIDADES          GOVERNANTES


USUÁRIOS
     │
     │ 1:N
     ▼
    LOGS
```

Principais regras:

* Um continente pode possuir vários países.
* Um país pertence a um continente.
* Um país pode possuir várias cidades.
* Uma cidade pertence a um país.
* Um país pode possuir vários governantes ao longo do tempo.
* Um usuário pode gerar vários registros de log.

---

## 📁 Estrutura da Pasta

```text
database/
│
├── model/
│   └── geoatlas.mwb
│
├── scripts/
│   ├── 01_create_database.sql
│   ├── 02_create_tables.sql
│   ├── 03_constraints.sql
│   └── 04_initial_data.sql
│
├── seeds/
│
└── README.md
```

### `model/`

Contém os arquivos relacionados à modelagem do banco de dados.

O arquivo principal será:

```text
geoatlas.mwb
```

Ele contém o modelo desenvolvido utilizando o **MySQL Workbench**.

### `scripts/`

Contém os scripts SQL necessários para criação e configuração do banco de dados.

Os scripts são numerados para indicar a ordem recomendada de execução.

#### `01_create_database.sql`

Responsável pela criação do banco:

```text
bd_geoatlas
```

#### `02_create_tables.sql`

Responsável pela criação das tabelas e definição inicial de seus atributos.

#### `03_constraints.sql`

Responsável pelas regras de integridade e relacionamentos adicionais do banco de dados.

#### `04_initial_data.sql`

Contém os registros iniciais necessários para utilização e testes do banco.

### `seeds/`

Contém conjuntos de dados utilizados para popular o banco durante o desenvolvimento, testes e demonstrações do GeoAtlas.

---

## ▶️ Criação do Banco

Para construir o banco de dados a partir dos scripts disponíveis neste repositório, execute os arquivos SQL respeitando sua ordem numérica:

```text
01_create_database.sql
        ↓
02_create_tables.sql
        ↓
03_constraints.sql
        ↓
04_initial_data.sql
```

Os scripts podem ser executados utilizando o **MySQL Workbench** ou outra ferramenta compatível com MySQL.

---

## 🔐 Segurança

Informações sensíveis utilizadas para conexão com o banco de dados **não devem ser armazenadas neste repositório**.

Isso inclui:

* senhas;
* usuários administrativos;
* tokens;
* chaves de API;
* strings de conexão contendo credenciais;
* arquivos `.env` contendo dados reais.

As aplicações deverão utilizar mecanismos apropriados para armazenamento das configurações de ambiente.

---

## 🌐 Utilização pelas Aplicações

O mesmo banco `bd_geoatlas` será utilizado pelas diferentes implementações do projeto.

Entre elas:

### Web

**Versão 1**

```text
HTML + CSS + JavaScript
          ↓
         PHP
          ↓
        MySQL
```

**Versão 2**

```text
HTML + CSS + JavaScript + TypeScript
                  ↓
             API / Node.js
                  ↓
                MySQL
```

### Mobile — React Native

```text
React Native + Expo + TypeScript
                  ↓
             API Node.js
                  ↓
                MySQL
```

### Mobile — Android

```text
Android
Kotlin / Java
     ↓
    API
     ↓
   MySQL
```

Essa abordagem permite demonstrar como diferentes tecnologias podem acessar e manipular informações provenientes de uma **mesma camada de persistência**.

---

## 📚 Finalidade Educacional

Além de integrar as diferentes aplicações do GeoAtlas, o banco de dados será utilizado para estudo e aplicação prática de conceitos de bancos de dados relacionais.

Durante a evolução do projeto poderão ser explorados conceitos como:

* modelagem conceitual;
* modelagem lógica;
* modelagem física;
* entidades e atributos;
* chaves primárias e estrangeiras;
* relacionamentos;
* cardinalidade;
* integridade referencial;
* normalização;
* comandos DDL;
* comandos DML;
* consultas SQL;
* `JOIN`;
* subconsultas;
* índices;
* views;
* procedures;
* functions;
* triggers;
* transactions;
* controle de usuários;
* auditoria e logs.

---

## 🚧 Status

**Em desenvolvimento.**

A estrutura do banco de dados será atualizada e documentada conforme a evolução do projeto GeoAtlas.

---

## 👨‍💻 Autor

**André Olímpio**

Projeto desenvolvido para fins educacionais e para demonstração prática do desenvolvimento completo de aplicações Web e Mobile.