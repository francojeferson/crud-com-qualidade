# crud-com-qualidade

#### javascript

```js
// [dar bons nomes de variaveis]
var n1 = 10;
var n2 = 20;

console.log(n1 + n2);

// como devs, o que mais fazemos é LER código
// contexto é extremamente importante
const userFirstInputNumber = 10;
const userSecondInputNumber = 20;
// nao ter tipos no js nao precisa ser uma desculpa pra fazer codigo ruim (faz codigo bom usando a propria sintaxe das variaveis)
console.log(userFirstInputNumber + userSecondInputNumber);

// =============================
var inputDoUsuario;

// no browser
// - string
// - elemento do DOM (campo de busca do google)
const inputUsuario = document.querySelector('input').value;
const $inputUsuario = document.querySelector('input'); // $ representa o elemento do DOM

// booleanos
// <input value="" />
document.querySelector('input').hasAttribute('value'); // true | false
// has, is (indica que retorna booleano)
if (hasSomething || isAnything) {
}
if (!hasSomething) {
} // melhor fazer varios if's	do que trabalhar com else

// should
if (shouldOpen) {
} // nao recomendavel
```

#### typescript

```ts
var arr: boolean;
var isArray: boolean;

if (isArray) {
} // contextualizar o booleano na sintaxe
```

## input, processamento e output: a base de tudo

TUDO em tecnologia se resume a `entrada -> processamento -> saida`

### front-end ( web / mobile / android / ios / hibrido: react native / flutter )

- quem da a entrada?
  - usuario
- **quem processa?**
  - navegador/celular
    - dev
      - js (ou alguma linguagem que compila para js)
      - swift
      - java
      - dart
- como é a saida?
  - elemento aparecendo na tela pro usuario
    - alert
    - console.log
    - html + css
  - cookie / localStorage / asyncStorage / qualquer storage disponivel no front

### back-end

- quem da a entrada?
  - usuario
  - json
- **quem processa?**
  - server
    - dev (clojure, js, php)
- como é a saida?
  - json
  - txt
  - html

### cli

request -> response

google: ciencia da computaçao entrada processamento e saida

[entendendo como fazer ajax com a fetchapi](https://medium.com/@omariosouto/entendendo-como-fazer-ajax-com-a-fetchapi-977ff20da3c6)

## tanto faz o nome das pastas, o que importa sao padroes e convencoes

o mundo da programacao tem zilhares de sopa de letrinhas

- mvc
- mvvm
- mvp
- viper
- vip
- flux
- redux
- clean arch
- clean swift
- clean code
- solid
- dry
- kiss
- ???

### processos de softwares no mundo real

- vimos a parte de por tras de um software

### usuario

> twitter

- click num botao "tweet"
- abriu um modal com a caixa para digitar um tweet
- digitei meu tweet, para que o botao de envio fosse liberado
- cliquei para enviar
- aparecer uma mensagem de "publicado com sucesso"

### trabalho das pessoas devs por tras

#### front-end

- programar a tela
  - html, css (visual da tela)
- ter o comportamento de escutar toda vez que o usuario digita um tweet
  - **validar** se tiver mais de 1 caracter, remove o atributo disabled do botao de tweetar
- adicionar um evento que escuta quando o botao de tweetar foi apertado
  - pegar o conteudo do tweet
  - mandar para o servidor

#### back-end

- vamos receber as infos do tweet no body da request
- **validar** se o tweet é um tweet valido
  - se nao for valido, retorna um erro
- salvar o tweet no banco de dados
  - se nao for possivel, retorna um erro
- retornar a mensagem de sucesso

### o que é comum nesses processos?

[view]

- html e css
- respostas do backend

[controller]

- executar funçoes de validaçao, garantir que os dados estao corretos
- enviar para a parte que "salva"

[repository]

- responsavel por PEGAR dados e ENVIAR dados

### código de exemplo [FRONT]

```html
<script>
  const tweetRepository {
    getTweets() {},
    postTweet() {}
  }
  function tweetController() {
    const $input = document.getElementById('input');
    // fail fast validations
    if(!isTweetValid($input.value)) return;
    const tweet = $input;
    // daqui em diante, podemos confiar que TEMOS os dados que precisamos
    tweetRepository.postTweet(tweet);
    alert("Tweet publicado com sucesso!");
  }
</script>
<form>
  <input type="text" id="input" />
  <button type="button" onclick="tweetController()">Tweetar</button>
</form>
```

### [BACK]

[controller] -> recebe o dado do **INPUT**

[repository] -> onde fica a lógica de acesso ao banco de dados

- Responsável por PEGAR dados e por ENVIAR dados

```js
const tweetRepository {
  getTweets() {},
  postTweet() {}
}
function tweetController(request, response) {
  // fail fast validation
  if(!isTweetValid(request.body)) return response.status(400).send('Invalid tweet');
  const tweet = $input;
  // daqui em diante, podemos confiar que TEMOS os dados que precisamos
  tweetRepository.postTweet(tweet);
  return response.status(200).send('Tweet posted');
}
```

> [httpstatusdogs.com](https://httpstatusdogs.com)

## resumo

- isso tudo faz link com `input -> processamento -> output`

- `input (usuario, frontend, serviço) -> processamento (controller, repository) -> output (response, view)`

- CRUDs

- Model
  - representaçao do dado/abstraçao

```js
function Tweet(conteudo, usuario) {
  return {
    content: conteudo,
    user: usuario,
    data: new Date().now,
  };
}
```

## create - memoria vs disco

```js (crud)
console.log('[CRUD]');
```

`$node ./core/crud.js` -> `[CRUD]`

`$npm init -y`

```json (package)
"scripts": {
  "dev": "node ./core/crud.js"
}
```

`$npm install --save-dev nodemon`

```json (package)
"scripts": {
  "start": "node ./core/crud.js",
  "dev": "nodemon ./core/crud.js"
}
```

`$npx gitignore node`

`$npm install typescript`

```json (tsconfig)
"include": ["**/*.ts"],
```

`$npx tsc --init`

`$npm i -D @types/node`

```json (package)
"scripts": {
  "start:crud": "npx ts-node ./core/crud.ts",
  "dev:crud": "nodemon --ext ts,tsx --exec 'npm run start:crud'",
}
```

```ts (crud)
import fs from 'fs'; // ES6
// const fs = require('fs'); - CommonJS
// ...
function create(content: string) {
  // ...
}
```

> [ts-node](https://www.npmjs.com/package/ts-node)

## read - estruturas de dados para guardar informaçoes

```ts (crud)
// [SIMULATION]
create('Primeira TODO');
console.log(read());
```

```ts (crud)
function read() {
  const db = fs.readFileSync(DB_FILE_PATH, 'utf-8');
  return db;
}

// db: Primeira TODO
```

```ts (crud)
function create(content: string) {
  const todo = {
    content: content,
  };
  console.log(todo);

  // salvar o content no sistema
  fs.writeFileSync(DB_FILE_PATH, todo.toString());
  return content;
}

// db: [object Object]
```

```ts (crud)
// salvar o content no sistema
fs.writeFileSync(DB_FILE_PATH, JSON.stringify(todo));
return content;

// db: {"content":"Segunda TODO"}
```

```ts (crud)
const todo = {
  date: new Date().toISOString(),
  content: content,
};

// db: {"date":"2024-02-17T21:30:29.438Z","content":"Segunda TODO"}
```

```ts (crud)
// [SIMULATION]
create('Primeira TODO');
create('Segunda TODO');
console.log(read());

// db: {"date":"2024-02-17T21:32:52.037Z","content":"Segunda TODO"}
```

```ts (crud)
function create(content: string) {
  const todo = {
    date: new Date().toISOString(),
    content: content,
  };

  const todos = [todo];

  // salvar o content no sistema
  fs.writeFileSync(DB_FILE_PATH, JSON.stringify(todos));
  return content;
}

// db: [{"date":"2024-02-17T21:34:52.425Z","content":"Segunda TODO"}]
```

```ts (crud)
// salvar o content no sistema
fs.writeFileSync(DB_FILE_PATH, JSON.stringify({ todos }, null, 2));
return content;

// db:
// {
//   "todos": [
//     {
//       "date": "2024-02-18T11:04:48.623Z",
//       "content": "Segunda TODO"
//     }
//   ]
// }
```

```ts (crud)
// salvar o content no sistema
fs.writeFileSync(DB_FILE_PATH, JSON.stringify({ todos, dogs: [] }, null, 2));
return content;

// db:
// {
//   "todos": [
//     {
//       "date": "2024-02-18T11:09:11.257Z",
//       "content": "Segunda TODO"
//     }
//   ],
//   "dogs": []
// }
```

```ts (crud)
interface Todo {
  date: string;
  content: string;
  done: boolean;
}

function create(content: string) {
  const todo: Todo = {
    date: new Date().toISOString(),
    content: content,
  };
  // ...
}

// Property 'done' is missing in type '{ date: string; content: string; }' but required in type 'Todo'.ts(2741)
```

```ts (crud)
const todo: Todo = {
  date: new Date().toISOString(),
  content: content,
  done: false,
};

// db:
// {
//   "todos": [
//     {
//       "date": "2024-02-18T11:14:10.476Z",
//       "content": "Segunda TODO",
//       "done": false
//     }
//   ],
//   "dogs": []
// }
```

```ts (crud)
function read(): Array<Todo> {
  const db = fs.readFileSync(DB_FILE_PATH, 'utf-8');
  return db;
}

// Type 'string' is not assignable to type 'Todo[]'.ts(2322)
```

```ts (crud)
function read(): Array<Todo> {
  const dbString = fs.readFileSync(DB_FILE_PATH, 'utf-8');
  const db = JSON.parse(dbString);
  return db;
}
```

```ts (crud)
function read(): Array<Todo> {
  const dbString = fs.readFileSync(DB_FILE_PATH, 'utf-8');
  const db = JSON.parse(dbString || '{}');
  return db;
}

// [SIMULATION]
// create('Primeira TODO');
// create('Segunda TODO');
console.log(read());

// db: vazio
```

```ts (crud)
function read(): Array<Todo> {
  const dbString = fs.readFileSync(DB_FILE_PATH, 'utf-8');
  const db = JSON.parse(dbString || '{}');
  // fail fast validation
  if (!db.todos) {
    return [];
  }
  return db.todos;
}

// db: vazio
```

```ts (crud)
const todos: Todo[] = [...read(), todo];
// diamond operator
const todos: Array<Todo> = [...read(), todo];

// db:
// {
//   "todos": [
//     {
//       "date": "2024-02-18T11:26:22.949Z",
//       "content": "Primeira TODO",
//       "done": false
//     },
//     {
//       "date": "2024-02-18T11:27:31.289Z",
//       "content": "Primeira TODO",
//       "done": false
//     }
//   ],
//   "dogs": []
// }
```

```ts (crud)
function CLEAR_DB() {
  fs.writeFileSync(DB_FILE_PATH, '');
}

// [SIMULATION]
CLEAR_DB();
create('Primeira TODO');
create('Segunda TODO');
console.log(read());

// db:
// {
//   "todos": [
//     {
//       "date": "2024-02-18T11:32:08.098Z",
//       "content": "Primeira TODO",
//       "done": false
//     },
//     {
//       "date": "2024-02-18T11:32:08.098Z",
//       "content": "Segunda TODO",
//       "done": false
//     }
//   ],
//   "dogs": []
// }
```
