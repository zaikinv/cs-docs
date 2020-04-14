# Theory

## Time complexity (how long takes algorithm to run):

- O(1) - function require 1 step (access, assignment)
- O(n) - function require n steps
- O(n²) - function require n² steps (nested loop)

## Space complexity (how much space in memory does algorithm use):

- O(1) - function allocates static number of variables (independent from input)
- O(n) - function allocates dynamic number of variables (dependent from input)

## Global execution scope

Environment created before any javacript code is executed, consists of:

- global `window` or `global` (Node.js) object
- `this` object (equal to `window` or `global`)
- `arguments` object
- variable environment (all variable declarations)

## Static (lexical) scope

Detrmines variables solely based on their textual position in our code.

- extended by parent lexical scope walking up scope chain until global execution context
- write-time
- only created when you create a new function (`{}`)
- can be accessed by `[[Scopes]]`

## Hoisting

Act of moving of `function` or `var` to the top of the scope.

- because javascript allocates space for them in a memory heap
- during compilation phase
- `var` initialized with `undefined`
- `let` and `const` declarations remain uninitialized

## IIFE

Design pattern to avoid namespace collisions.

- used before modules were introduced
- E means Expression, declaration starts with `function() {}`
- you can pass a param to avoid scope chain lookup

## this

The object that the property or function is property of.

- refers to what is left to the dot `'.'`