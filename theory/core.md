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

## Keyword `this`

- The object that the property or function is property of.

  - refers to what is left to the dot `'.'`

  - the value of `this` can be determined by answering the question _"who called the function?"_

## Keyword `call`

  - can be used for method borrowing, arguments are coma-separated

  ```js
  
  originalObject.method.call(targetObject, argument1, argument2, ...)
  
  ```

## Keyword `apply`

  - can be used for method borrowing, arguments are in `Array`

  ```js
  
  originalObject.method.apply(targetObject, [argument1, argument2, ... ])
  
  ```

## Keyword `bind`

  - returns new function unlinke `call` or `apply`

  - allows to store in function for future use

  ```js
  
  const method = originalObject.method.bind(targetObject, argument1, argument2, ...)
  
  ```
  
  