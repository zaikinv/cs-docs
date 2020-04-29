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