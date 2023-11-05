# Template API com JS Vanilla

Este projeto é um Template API utilizando node (v18.17.0) com JavaScript Vanilla, Express e PostgreSQL.

## Recursos

- Node
- Express
- PostgreSQL
- Sequelize
- Jest
- Supertest
- ESLint

## Instalação

1. Faça o clone do repositório: `git clone https://github.com/Elias-Neto/camel`
2. Instale as dependências: `npm i`
3. Configure as variáveis de ambiente (veja a seção "Configuração" abaixo)
4. Inicie o servidor: `npm run dev`

## Configuração

Para que o sistema seja executado, minimamente tem que ser ajustado as seguintes variáveis de ambiente antes de iniciar o servidor:

- `DB_NAME`: Nome do banco de dados.
- `DB_USER`: Nome do usuário para se conectar com o banco de dados.
- `DB_PASSWORD`: Senha para se conectar com o banco de dados.
- `DB_HOST`: Host onde o banco de dados está rodando.
- `DB_DIALECT`: Dialeto que o banco de dados está usando.

---

## Regras de desenvolvimento

### Estrutura de Pastas

#### `/api`

> Cada módulo da API deve possuir um diretório próprio com os recursos internos distribuídos da seguinte forma:

```
api
│   index.ts (declaração de módulos)
|
└───people
│   │   people.router.ts (declaração de recursos do módulo)
│   │   people.router.spec.ts
│   │   people.controller.ts
│   │   people.types.ts
│   │   people.dao.ts
│   │   people.helper.ts
│   │   people.service.ts
│   │   people.middleware.ts
│   │
│   └───addresses
│       │   addresses.router.ts
│       │   addresses.router.spec.ts
│       │   addresses.controller.ts
│       │   addresses.dao.ts
│       │   addresses.types.ts
│       │   addresses.middleware.ts
│       │   addresses.middleware.spec.ts
│       │
│       ...
...
```

#### 1. Router

> /api/module/module.router.ts

**Um Router pode:**

- Prover os endpoints de uma entidade.
- Possuir um ou mais middlewares.
- Possuir o verbo HTTP e a função da controller.

**Um Router não pode:**

- Possuir lógica.

#### 2. Middleware

> /api/module/module.middleware.ts

**Um middleware pode:**

- Validar o corpo e parâmetros das requisições antes que chegarem no controller.
- Validar regras de negócio.

#### 3. Controller

> /api/module/module.controller.ts

**Um controller pode:**

- Prover as funcionalidades para a rota.
- Prover lógicas de negócio.

**Um controller não pode:**

- Ser exposto a qualquer arquivo que não seja uma rota.

#### 4. DAO

> /api/module/module.dao.ts

**Um DAO pode:**

- Realizar as consultas no banco de dados.

**Um DAO não pode:**

- Possuir lógica.

#### 5. Helper

> /api/module/module.helper.ts

**Um helper pode:**

- Definição de funções e constantes compartilhados pelos métodos do controller.

**Um helper não pode:**

- Possuir lógica de negócio.

#### 6. Service

> /api/module/module.service.ts

**Um service pode:**

- Resolver problemas específicos que podem ser compartilhados pelo próprio ou outros módulos.

**Um service não pode:**

- Receber dados http, como o objeto request, response e next, (responsabilidade do controller)

---

```
OBS: Não necessariamente serão criados todos os arquivos descritos
```

---

### /services

**A pasta isolada de services pode :**

- Resolver problemas específicos de maneira genérica.
- Pode ser utilizada em qualquer controller.

---

# Testes

> Se necessário, criar mocks de teste nas tabelas do banco de dados

## Jest/Supertest

> Testes de integração das rotas utilizando o jest com supertest para verificar os cenários de sucesso e `[200, 201, 204]` erro `[400, 401, 404, 409, 500]`

<br />
<br />

<p align="center"> Desenvolvido com ❤ por Elias de Araújo Ferreira Neto 👋 <p>
