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