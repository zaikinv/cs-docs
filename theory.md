> Global execution scope 

Environment created before any javacript code is executed, consists of:

- global `window` or `global` (Node.js) object
- `this` object (equal to `window` or `global`)
- `arguments` object
- variable environment (all variable declarations)

> Static (lexical) scope

Detrmines variables solely based on their textual position in our code.

- extended by parent lexical scope walking up scope chain until global execution context
- write-time
- only created when you create a new function (`{}`)
- can be accessed by `[[Scopes]]`

> Hoisting

Act of moving of `function` or `var` to the top of the scope.

- because javascript allocates space for them in a memory heap
- during compilation phase
- `var` initialized with `undefined`
-  `let` and `const` declarations remain uninitialized

> `arguments`

Avoid using because it is "array-like", if you really need use `...args` instead (converts to array)

> `'use strict'`

Allows to avoid using undeclared variables e.g. just writing `height = 50`




