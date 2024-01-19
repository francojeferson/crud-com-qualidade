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
