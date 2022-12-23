# :construction: README em construção ! :construction:

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
- Este é um projeto desenvolvido para me ajudar a aprender `TypeScript`.
- Meu primeiro projeto usando `TypeScript`.

---

### Linguagem usadas

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

---

## O que foi desenvolvido
<p> 
 Uma API e um banco de dados, utilizando a arquitetura MSC (model-service-controller), para a produção de conteúdo para um blog! <br>
 
 1. Desenvolvi endpoints que estarão conectados ao banco de dados seguindo os princípios do REST;<br>
 2. Para fazer um post é necessário usuário e login, portanto foi trabalhada a relação entre user e post; <br>
 3. Será necessária a utilização de categorias para os posts, trabalhando, assim, a relação de posts para categories e de categories para posts. <br>
</p>

---

## Variáveis de Ambiente

Para rodar esse projeto, atente-se as variáveis de ambiente no seu .env

---

### Instruções para instalar e rodar

1. Clone o repo:
```
  git clone git@github.com:Ludson96/project-trybesmith.git
```
2. Já existe um arquivo docker-compose.yml (Disponibilizado pela Trybe). Bastando usar o comando docker-compose up para rodar o MySQL e o Node pelo docker. Execute os services do docker: `node` e `db` 
```
  docker-compose up -d
```
3. Inicie o container node (renomeado para blogs_api):
```
  docker exec -it blogs_api bash
```
4. Instale as suas dependencias:
```
  npm install
```
5. Execute o servidor:

```
  npm start
```
Outra forma de executar é utilizando o `nodemom` (permite fazer alteração em tempo real sem precisar derrubar o servidor e iniciá-lo novamente):
```
  npm run debug
```
6. Utilizar alguma Plataforma de API para acessar os endpoints e fazer seus devidos experimentos. Exemplos: Postman e Insomnia. Ou uma extensão no VSCode, recomendo utlizar a thunder client.

7. Uso

- utiline o comando `npm run prestart`, ele criará o banco de dados e as tabelas de acordo com o que está em `/migrations` e `/seeders` .

- Todas as rotas (exceto `post /login` e `post /user` ) requerem autenticação

---

## Diagrama

![Diagrama de relacionamentos das tabelas](diagrama.png)

<i> Imagem disponibilizada pela Trybe </i>

---

## Endpoints

<details>



</details>

> `docker-compose.yml`, `config.js` e `/seeders` arquivos providos pela Trybe.

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
