# Repositório do projeto TrybeSmith 

<div align="center">
  <img height="250px" align="right" src="ferreiro.png" />
  <div align="left" style="display: inline_block">
    <h2>Módulo: BACK-END</h2>
    <p>
        Repositório possui projeto desenvolvido no período que estive na <b>Trybe</b>, abordando os conceitos de <b>RESTFul API</b> com CRUD completo utilizando arquitetura Model-Service-Controller (MSC) com TypeScript. 
  </div>
  <br>
</div>
  
## Informações de aprendizados
- Este é um projeto desenvolvido para me ajudar a aprender `TypeScript`;
- Meu primeiro projeto usando `TypeScript`;
- Utilizei o Cliente Rest `Thunder Client`, como extensão, para visualizar o retorno do meu acesso.
## Linguagem usadas

[![JavaScript][JavaScript-logo]][JavaScript-url]
[![NodeJS][NodeJS-logo]][NodeJS-url]
[![Express][Express-logo]][Express-url]
[![MySQL][MySQL-logo]][MySQL-url]
[![Docker][Docker-logo]][Docker-url]
[![Nodemon][Nodemon-logo]][Nodemon-url]
[![JWT][JWT-logo]][JWT-url]
[![ESLint][ESLint-logo]][ESLint-url]
[![TypeScript][TypeScript-logo]][TypeScript-url]
[![ts-node][ts-node-logo]][ts-node-url]
[![.ENV][.ENV-logo]][.ENV-url]
## O que foi desenvolvido
<p> 
 Uma API e um banco de dados, utilizando a arquitetura MSC (model-service-controller), de uma loja de itens medievais, no formato de uma API, utilizando Typescript! <br>
 
 1. Desenvolvi endpoints que estarão conectados ao banco de dados seguindo os princípios do REST;<br>
 2. Para fazer um post é necessário usuário e login, portanto foi trabalhada a relação entre user e post; <br>
 3. Será necessária a utilização de categorias para os posts, trabalhando, assim, a relação de posts para categories e de categories para posts. <br>
</p>

> Arquivo `docker-compose.yml` fornecidos pela Trybe.

## Variáveis de Ambiente

Para rodar esse projeto, atente-se as variáveis de ambiente no seu .env. Existe um arquivo `.env.example` com as informações de configurações.
## Instruções para instalar e rodar

1. Clone o repo:
```
  git clone git@github.com:Ludson96/project-trybesmith.git
```
2. Já existe um arquivo docker-compose.yml (Disponibilizado pela Trybe). Bastando usar o comando docker-compose up para rodar o MySQL e o Node pelo docker. Execute os services do docker: `trybesmith (node)` e `trybesmith_db (banco de dados)` 
```
  docker-compose up -d
```
3. Inicie o container node (renomeado para trybesmith):
```
  docker exec -it trybesmith bash
```
4. Instale as suas dependências:
```
  npm install
```
5. Execute o servidor (ts-node):

```
  npm start
```
Outra forma de executar é utilizando o `nodemom` (permite fazer alteração em tempo real sem precisar derrubar o servidor e iniciá-lo novamente):
```
  npm run dev
```
6. Utilizar alguma Plataforma de API para acessar os endpoints e fazer seus devidos experimentos. Exemplos: Postman e Insomnia. Ou uma extensão no VSCode, recomendo utilizar a thunder client.

7. Existe um arquivo chamado Trybesmith.sql. Você pode utilizar ele para criar o banco de dados e suas tabelas. Recomendo que uma ferramenta de design de banco de dados visual, como o [MySQL Workbench](https://dev.mysql.com/downloads/workbench/)
## Diagrama

![Diagrama de relacionamentos das tabelas](diagrama.png)

> _Imagem disponibilizada pela Trybe_
## Endpoints

<details>

###  Rota de Produto

####  POST `/products`
- Os produtos enviados são salvos na tabela `products` do banco de dados;
- O corpo deve ter a seguinte estrutura: 
  - `name` e `amount` é obrigatório;
  - `name` e `amount` precisa ser uma string;
  - `name` e `amount` precisa ter mais de 2 caracteres.
- O endpoint deve receber a seguinte estrutura:
```json
  {
    "name": "Espada longa",
    "amount": "30 peças de ouro"
  }
```

> 👉 Para caso os dados sejam enviados corretamente
- O resultado retornado para cadastrar o produto com sucesso deverá ser conforme exibido abaixo, com um _status http_ `201`:
```json
  {
    "id": 6,
    "name": "Espada longa",
    "amount": "30 peças de ouro",
  }
```

---

####  GET `/products`
-  Lista todos os produtos no banco de dados

> 👉 Para caso os dados sejam enviados corretamente
- O resultado retornado para listar produtos com sucesso deverá ser conforme exibido abaixo, com um _status http_ `200`:
```json
[
  {
    "id": 1,
    "name": "Poção de cura",
    "amount": "20 gold",
    "orderId": null
  },
  {
    "id": 2,
    "name": "Escudo do Herói",
    "amount": "100 diamond",
    "orderId": 1
  }
]
```

---

###  Rota de Usuário

####  POST `/users`
- Cadastra um novo usuários;
- As informações de pessoas usuárias cadastradas são salvas na tabela `users` do banco de dados;
- O corpo deve ter a seguinte estrutura: 
  - `username`, `vocation`, `level`, `password` é obrigatório;
  - `username`, `vocation`, `password` precisa ser uma string;
  - `level` precisa ser um number;
  - `username`, `vocation` precisa ter mais de 2 caracteres;
  - `level` precisa ser um número maior que 0;
  - `password` precisa ter 8 ou meias caracteres.
- O endpoint deve receber a seguinte estrutura:
```json
{ 
  "username": "MAX",
  "vocation": "swordsman",
  "level": 10,
  "password": "SavingPeople"
}
```

> 👉 Para caso os dados sejam enviados corretamente
  - Se a pessoa usuária for cadastrada com sucesso, o resultado deverá ser conforme o exibido abaixo, com um _status http_ `201` e retornando um _token_:
  ```json
  {
    "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ.SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c"
  }
  ```

---

###  Rota de Pedidos

####  GET `/orders`
- Lista todos os pedidos e os `id`s dos produtos associados a estes.

> 👉 Para caso os dados sejam enviados corretamente
  - Quando houver mais de um pedido, o resultado retornado para listar pedidos com sucesso deverá ser conforme exibido abaixo, com um _status http_ `200`:
  ```json
    [
      {
        "id": 1,
        "userId": 2,
        "productsIds": [1, 2]
      },
      {
        "id": 2,
        "userId": 1,
        "productsIds": [3, 4]
      }
    ]
  ```

---

### POST `/orders`
- Cadastra um pedido
- Requer autenticação por token `JWT`
- O endpoint deve receber a seguinte estrutura:
```json
  {
    "productsIds": [1, 2]
  }
```

> 👉 Para token
- Se o token não for informado, o resultado retornado deverá ser um _status http_ `401` e
```json
  { "message": "Token not found" }
```

- Se o token informado não for válido, o resultado retornado deverá ser um _status http_ `401` e
```json
  { "message": "Invalid token" }
```

<br>

> 👉 Para products
  - Se o corpo da requisição não possuir o campo "productsIds", o resultado retornado deverá ser um _status http_ `400` e
  ```json
    { "message": "\"productsIds\" is required" }
  ```

  - Se o valor do campo "productsIds" não for um array, o resultado retornado deverá ser um _status http_ `422` e
  ```json
    { "message": "\"productsIds\" must be an array" }
  ```

  - Se o campo "productsIds" possuir um array vazio, o resultado retornado deverá ser um _status http_ `422` e
  ```json
    { "message": "\"productsIds\" must include only numbers" }
  ```

<br>

> 👉 Para caso os dados sejam enviados corretamente
  - O resultado retornado para cadastrar um pedido com sucesso deverá ser conforme exibido abaixo, com um _status http_ `201`:
  ```json
    {
      "userId": 1,
      "productsIds": [1],
    }
  ```

  - O resultado retornado para cadastrar um pedido de vários itens com sucesso deverá ser conforme exibido abaixo, com um _status http_ `201`:
  ```json
    {
      "userId": 1,
      "productsIds": [1, 2]
    }
  ```

---

###  Rota de Login

####  POST `/login`
- Realiza o login.

- O endpoint deve receber a seguinte estrutura:
```json
  {
    "username": "string",
    "password": "string"
  }
```

> 👉 Para caso haja problemas no login
  - Se o _login_ não tiver o campo "username", o resultado retornado deverá ser um _status http_ `400` e
  ```json
    { "message": "\"username\" is required" }
  ```

  - Se o _login_ não tiver o campo "password", o resultado retornado deverá ser um _status http_ `400`
  ```json
    { "message": "\"password\" is required" }
  ```

  - Se o _login_ tiver o username inválido, o resultado retornado deverá ser um _status http_ `401` e
  ```json
    { "message": "Username or password invalid" }
  ```

  - Se o login tiver a senha inválida, o resultado retornado deverá ser um _status http_ `401` e
  ```json
    { "message": "Username or password invalid" }
  ```

<br>

> 👉 Para caso os dados sejam enviados corretamente
  - Se o login foi feito com sucesso, o resultado deverá ser um _status http_ `200` e deverá retornar um _token_:
  ```json
  {
    "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ.SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c"
  }
  ```

</details>

[JavaScript-logo]: https://img.shields.io/badge/javascript-%23323330.svg?style=for-the-badge&logo=javascript&logoColor=%23F7DF1E
[JavaScript-url]: https://www.javascript.com/
[Express-logo]: https://img.shields.io/badge/express.js-%23404d59.svg?style=for-the-badge&logo=express&logoColor=%2361DAFB
[Express-url]: https://expressjs.com
[NodeJS-logo]: https://img.shields.io/badge/node.js-6DA55F?style=for-the-badge&logo=node.js&logoColor=white
[NodeJS-url]: https://nodejs.org/en/
[MySQL-logo]: https://img.shields.io/badge/mysql-%2300f.svg?style=for-the-badge&logo=mysql&logoColor=white
[MySQL-url]: https://www.mysql.com
[Docker-logo]: https://img.shields.io/badge/docker-%230db7ed.svg?style=for-the-badge&logo=docker&logoColor=white
[Docker-url]: https://www.docker.com
[Nodemon-logo]: https://img.shields.io/badge/Nodemon-76D04B?logo=nodemon&logoColor=fff&style=for-the-badge
[Nodemon-url]: https://www.npmjs.com/package/nodemon
[JWT-logo]: https://img.shields.io/badge/JWT-black?style=for-the-badge&logo=JSON%20web%20tokens
[JWT-url]: https://jwt.io/
[ESLint-logo]: https://img.shields.io/badge/ESLint-4B3263?style=for-the-badge&logo=eslint&logoColor=white
[ESLint-url]: https://eslint.org/
[TypeScript-logo]: https://img.shields.io/badge/typescript-%23007ACC.svg?style=for-the-badge&logo=typescript&logoColor=white
[TypeScript-url]: https://www.typescriptlang.org/
[ts-node-logo]: https://img.shields.io/badge/ts--node-3178C6?logo=tsnode&logoColor=fff&style=for-the-badge
[ts-node-url]: https://www.npmjs.com/package/ts-node-dev
[.ENV-logo]: https://img.shields.io/badge/.ENV-ECD53F?logo=dotenv&logoColor=000&style=for-the-badge
[.ENV-url]: https://www.npmjs.com/package/dotenv
