# Theory

## Time complexity:

- how long takes algorithm to run

  - O(1) - function require 1 step (access, assignment)

  - O(n) - function require n steps

  - O(n²) - function require n² steps (nested loop)

## Space complexity:

- how much space in memory does algorithm use

  - O(1) - function allocates static number of variables (independent from input)

  - O(n) - function allocates dynamic number of variables (dependent from input)

## Global execution scope

- Environment created before any javacript code is executed, consists of:

  - global `window` or `global` (Node.js) object

  - `this` object (equal to `window` or `global`)

  - `arguments` object

  - variable environment (all variable declarations)

## Static (lexical) scope

- write-time (detrmines variables solely based on their textual position in our code)

- based on nesting of scope

- the scope that can be determined statically at a write time

- only created when you create a new function (`{}`)

- extended by parent lexical scope walking up scope chain until global execution context

- can be accessed by `[[Scopes]]`

## Dynamic scope

- run-time

- based on callstack

- the scope that can be determined dynamicaly at a runtime

## Hoisting

- Act of moving of `function` or `var` to the top of the scope.

  - because javascript allocates space for them in a memory heap

  - during compilation phase

  - `var` initialized with `undefined`

  - `let` and `const` declarations remain uninitialized

## IIFE

- Design pattern to avoid namespace collisions.

  - used before modules were introduced

  - E means Expression, declaration starts with `function() {}`

  - you can pass a param to avoid scope chain lookup

## `this`

- The object that the property or function is property of.

  - refers to what is left to the dot `'.'`

  - the value of `this` can be determined by answering the question _"who called the function?"_

## `call`, `bind`, `apply`

- `call`

  - can be used for method borrowing, arguments are coma-separated

  - `originalObject.method.call(targetObject, argument1, argument2, ...)`

- `apply`

  - can be used for method borrowing, arguments are in `Array`

  - `originalObject.method.call(targetObject, [argument1, argument2, ... ])`

- `bind`

  - returns new function unlinke `call` or `apply`

  - allows to store in function for future use

  - `const method = originalObject.method.bind(targetObject, argument1, argument2, ...);`

## Currying

- function with N params → function with 1 params

- transforms a function that accepts multiple arguments “all at once” into a series of function calls

```js
const normal = (a, b, c, d) => a + b + c + d

const curried = (a) => (b) => (c) => (d) => a + b + c + d
``` 

- useful for FP to have less params for better composition and reuse

  - you can pass more arguments to `const sum = (a, b) => a + b` and they will be ignored `sum(a, b, 'ignored')`, but how can you pass less?

## Partial application

- function with N params → function with M params

- derive new function, with specific behavior, from general function

```js
const normal = (a, b, c, d) => a + b + c + d

const partial = normal.bind(null, 1, 2, 3)
```   

## Memoization

- caching result of function execution in function itself (more precisely, in closure)

- closure with cache

- params are cache's keys

- improves performance  

```js
const normal = (n) => n * 2; 
// normal(10);
```   

```js
const memoized = (n) => {
  let cache = {};
  return function(n) {
    if (n in cache) {
      return cache[n];
    } else {
      const answer = n * 2;
      cache[n] = answer;
      return answer;
    }
  }
}
// memoized()(10);
```

## First class citizens

- simply means “being able to do what everyone else can do”

  - can assign as variable

  - pass as an argument

  - return

- basis for functional programming

## Higher order function

- function that not only accept data, but what to do (function)

## Closure

- function with reference to its lexical scope

- in "normal" function when it is returned, variables declared inside it are garbage collected, in closures they are not

- concept of closures is similar to classes with private methods

- uses for data privacy, keep "secret" data inside a function and only allow reading it via access methods

```js

function a() {
  let grandpa = 'grandpa'
  return function b() {
    let father = 'father'
    let random = 4327493274233379 // garbage collected!
    return function c() {
      let son = 'son'
      return `${grandpa} > ${father} > ${son}`
    }
  }
}
```

## Prototypal inheritance

- programming paradigm when objects directly inherit from another objects (unlike OOP where classes inherit from classes)

- everything instantiated via `new` keyword gets `__proto__` pointing to `prototype` that contains parent methods

- top of the protypal chain is base `object` (not an `Object`)

- advantages

  - memory efficience (reuse methods instead of copying it)

- create object from prototype (2 ways)

  - `Object.create( <Object> .prototype)`

```js
const elfFunctions = attack() {
  return 'attack'
}

const newElf = Object.create(elfFunctions)

newElf.name = 'Alex'
newElf.weapon = 'Hammer'
```

  - `new <Object>` ("constructor function")

```js
function Elf(name, weapon) {
  this.name = name;
  this.weapon = weapon;
}

Elf.prototype.attack = () => {
  return 'attack'
}

const alex = new Elf('Alex', 'Hammer')
```

## `new`

- suppose we have a constructor function

  - `function Animal(name) { this.name = name; }`

- `var cat = new Animal('Dora')` creates instance:

  - creates blank plain `object`

    - `var obj = {};`

  - sets `__proto__` to `prototype` of given object

    - `obj.__proto__ = Animal.prototype`

  - if arguments are provided they are assigned to `this`

    - `this.name = "Dora"`

  - returns `obj`

## JavaScript types

- `string`

- `number`

- `boolean`

- `null`

- `undefined`

## Class

- syntactic sugar on top of prototypal inheritance

- `constructor`

  - we are not including instance methods into constructor not to overload memory (when calling with `new Animal()` )

- `extends`

  - adds parent's class `__proto__` to current class `__proto__`

  ![](assets/20200421124051.png)

## Functional programming

- keep data and operations separately

- Keep functions small, pure and composable

## Pure function

- no side effects

- same input prduces same output

- advantages:

  - easy to test

  - easy to compose

  - avoid bugs

 ## Inheritance (Object Oriented Programming)

- implemented via `Class` and `extend`

- stateful

  - functions live together with state in one class

- Problems

  - taxonomy should be perfectly designed in the beginning, otherwise hard to make changes to hierarchy

  - can lead to "gorilla-banana problem"

  - tight coupling

## Composition (Functional Programming)

- implemented via `function`

- stateless

  - functions exist independently and can be reused everywhere    
