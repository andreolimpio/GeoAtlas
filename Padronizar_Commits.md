# Padrão de Commits para Projetos

## 1. Objetivo

Todo projeto desenvolvido deverá manter um histórico de commits organizado, descritivo e coerente com a evolução real da aplicação.

O commit não deve ser utilizado apenas como mecanismo para salvar arquivos no GitHub. Ele deve representar uma **unidade lógica de alteração realizada no projeto**.

Um bom histórico de commits permite compreender:

* o que foi desenvolvido;
* quando determinada funcionalidade foi implementada;
* quais correções foram realizadas;
* como o projeto evoluiu;
* quais integrantes contribuíram para o desenvolvimento;
* quais alterações ocorreram em cada etapa.

Por esse motivo, a qualidade e a organização dos commits fazem parte dos critérios de avaliação do projeto.

---

# 2. Estrutura padrão

As mensagens deverão seguir preferencialmente a seguinte estrutura:

```text
tipo: descrição objetiva da alteração
```

Exemplo:

```text
feat: adiciona cadastro de países
```

A mensagem possui dois componentes:

```text
feat: adiciona cadastro de países
│     │
│     └── descrição da alteração
│
└── tipo do commit
```

---

# 3. Tipos de commit

Os seguintes tipos deverão ser utilizados como padrão.

## `feat`

Utilizado quando uma nova funcionalidade é adicionada ao projeto.

Exemplos:

```text
feat: adiciona cadastro de países

feat: implementa tela de login

feat: cria endpoint para consulta de cidades

feat: implementa autenticação de usuários
```

---

## `fix`

Utilizado para correção de erros ou comportamentos incorretos.

Exemplos:

```text
fix: corrige validação do formulário de países

fix: corrige relacionamento entre cidades e países

fix: corrige erro na autenticação de usuários
```

---

## `docs`

Utilizado exclusivamente para alterações relacionadas à documentação.

Exemplos:

```text
docs: adiciona instruções de instalação

docs: atualiza documentação do banco de dados

docs: adiciona descrição dos endpoints da API
```

---

## `refactor`

Utilizado quando o código é reorganizado ou melhorado sem alterar sua funcionalidade principal.

Exemplos:

```text
refactor: reorganiza serviço de consulta de países

refactor: separa validações do cadastro de usuários

refactor: reorganiza estrutura das rotas da API
```

---

## `test`

Utilizado para criação ou alteração de testes.

Exemplos:

```text
test: adiciona testes para cadastro de países

test: cria testes de autenticação

test: atualiza testes da API de cidades
```

---

## `style`

Utilizado para alterações visuais ou de formatação que não modificam a lógica da aplicação.

Exemplos:

```text
style: ajusta espaçamento do formulário de login

style: atualiza layout da tela de países

style: padroniza formatação dos arquivos CSS
```

---

## `chore`

Utilizado para tarefas auxiliares de manutenção, configuração ou organização do projeto.

Exemplos:

```text
chore: configura arquivo gitignore

chore: atualiza dependências do projeto

chore: configura ambiente inicial do Node.js
```

---

## `build`

Utilizado para alterações relacionadas ao processo de construção, dependências ou ferramentas de build.

Exemplos:

```text
build: adiciona dependência do express

build: configura projeto React Native

build: atualiza configuração do Gradle
```

---

# 4. Como escrever uma boa mensagem

A descrição deve indicar claramente **o que foi realizado naquele commit**.

Prefira:

```text
feat: adiciona cadastro de continentes
```

em vez de:

```text
feat: alterações
```

Prefira:

```text
fix: corrige validação do campo email
```

em vez de:

```text
fix: correção
```

Prefira:

```text
docs: adiciona documentação do modelo relacional
```

em vez de:

```text
docs: readme
```

A mensagem deve permitir que outra pessoa compreenda a alteração sem precisar abrir imediatamente os arquivos modificados.

---

# 5. Commits devem representar unidades lógicas

Um commit deve representar uma alteração específica e coerente.

Por exemplo, durante a implementação do cadastro de países, poderiam existir:

```text
feat: cria estrutura inicial do cadastro de países

feat: adiciona formulário de cadastro de países

feat: implementa persistência de países

feat: adiciona consulta de países cadastrados

fix: corrige validação do código ISO do país
```

Isso demonstra a evolução natural da funcionalidade.

Não é adequado desenvolver várias partes independentes da aplicação e colocar tudo em um único commit:

```text
feat: adiciona login, países, cidades, usuários e dashboard
```

Esse commit é excessivamente abrangente e dificulta a compreensão do histórico.

---

# 6. Frequência dos commits

Os commits devem acompanhar a evolução real do projeto.

Não existe uma quantidade obrigatória de commits por aula, dia ou semana.

A regra é:

> **Faça um commit quando uma unidade lógica de trabalho estiver concluída e em um estado coerente.**

Portanto, não se deve criar commits artificiais apenas para aumentar sua quantidade.

Da mesma forma, não é adequado desenvolver uma grande parte do projeto durante vários dias e realizar apenas um commit ao final.

O histórico deve refletir naturalmente o processo de desenvolvimento.

---

# 7. Commits que devem ser evitados

Mensagens genéricas não serão consideradas boas práticas.

Exemplos inadequados:

```text
update

alterações

mudanças

teste

testando

correção

ajustes

projeto

trabalho

atividade

aula

commit

novo

final

versão final

final2

agora vai
```

Também devem ser evitadas mensagens como:

```text
feat: coisas novas

fix: arrumei uns erros

chore: mexendo no projeto
```

Essas mensagens não explicam adequadamente o que foi realizado.

---

# 8. Commits gigantes

Outro comportamento inadequado é realizar praticamente todo o projeto em um único commit.

Exemplo:

```text
Initial commit
```

seguido, dias ou semanas depois, por:

```text
Projeto completo
```

Um histórico desse tipo não demonstra adequadamente a evolução do desenvolvimento.

O Git deve acompanhar o projeto **desde o início**, e não ser utilizado apenas para enviar a versão final ao GitHub.

---

# 9. Commits vazios ou artificiais

Também não é permitido criar commits sem alterações relevantes apenas para aumentar artificialmente o histórico.

Exemplos:

```text
test: commit 1

test: commit 2

test: commit 3

chore: teste github

chore: mais um commit
```

A quantidade de commits isoladamente **não representa qualidade**.

Um projeto com 30 commits coerentes pode apresentar um histórico muito melhor que outro com 150 commits artificiais.

---

# 10. Commits em projetos desenvolvidos em grupo

Nos projetos em grupo, cada integrante deverá realizar commits utilizando sua própria conta GitHub.

O histórico do repositório deverá permitir identificar a participação dos integrantes durante o desenvolvimento.

Não é recomendado que todo o código seja desenvolvido utilizando apenas a conta de um integrante.

A contribuição individual poderá ser analisada considerando:

* autoria dos commits;
* natureza das alterações;
* frequência das contribuições;
* complexidade das implementações;
* participação nas diferentes etapas do projeto.

A quantidade de commits, isoladamente, não determina a contribuição de um integrante.

---

# 11. Segurança

Nunca devem ser enviados ao repositório:

* senhas;
* tokens;
* chaves de API;
* credenciais de banco de dados;
* arquivos contendo informações sensíveis;
* arquivos `.env` com credenciais reais.

Exemplo inadequado:

```text
DB_USER=root
DB_PASSWORD=minhaSenha123
```

Arquivos contendo configurações sensíveis deverão ser incluídos no `.gitignore` quando necessário.

---

# 12. Exemplos de evolução de um projeto

Um histórico organizado poderia apresentar a seguinte sequência:

```text
docs: adiciona documentação inicial do projeto

chore: configura estrutura inicial do repositório

feat: adiciona modelo inicial do banco de dados

feat: cria tabelas de continentes e países

feat: cria tabela de cidades

feat: adiciona relacionamentos entre entidades

feat: adiciona dados iniciais para continentes

feat: implementa estrutura inicial da API

feat: cria endpoint para consulta de países

feat: adiciona cadastro de países

fix: corrige validação do código ISO

feat: adiciona autenticação de usuários

docs: documenta endpoints da API

test: adiciona testes para consulta de países

refactor: reorganiza serviço de países
```

Ao observar esse histórico, é possível compreender como o sistema evoluiu sem precisar analisar inicialmente todo o código-fonte.

---

# 13. Critérios de avaliação

O histórico de commits poderá fazer parte da avaliação dos projetos.

Serão considerados:

### Padronização

Utilização adequada dos tipos:

```text
feat:
fix:
docs:
refactor:
test:
style:
chore:
build:
```

### Clareza

As mensagens descrevem objetivamente as alterações realizadas.

### Coerência

Os commits correspondem às alterações efetivamente realizadas.

### Granularidade

Os commits representam unidades lógicas de desenvolvimento, evitando commits excessivamente grandes ou fragmentados artificialmente.

### Frequência

O histórico acompanha a evolução do projeto ao longo do período de desenvolvimento.

### Participação

Em projetos em grupo, o histórico demonstra a contribuição dos diferentes integrantes.

### Segurança

O repositório não contém credenciais ou outras informações sensíveis.

### Evolução

O histórico permite compreender o desenvolvimento progressivo da aplicação.

---

# 14. O que não será avaliado isoladamente

Não será utilizada apenas a quantidade de commits como indicador de qualidade ou participação.

Portanto:

```text
mais commits ≠ maior nota
```

Da mesma forma:

```text
menos commits ≠ menor nota
```

O que será analisado é a **qualidade do histórico de desenvolvimento**.

---

# 15. Regra geral

Antes de realizar um commit, o desenvolvedor deverá conseguir responder claramente à pergunta:

> **O que este commit adiciona, corrige ou modifica no projeto?**

Se a resposta puder ser expressa de forma objetiva, ela provavelmente poderá ser utilizada como base para a mensagem do commit.

Exemplo:

```text
git add .
git commit -m "feat: adiciona cadastro de países"
```

O objetivo é que o histórico do Git conte, de forma clara e cronológica, **a história do desenvolvimento da aplicação**.
