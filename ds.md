## Singly linked list

![](assets/2020-05-02_18h15_59.jpg)

```js
const singlyLinkedList = {
  head: {
    value: 12,
    next: {
      value: 99,
      next: {
        value: 37,
        next: null,
      },
    },
  },
  tail: {
    value: 37,
    next: null,
  },
  length: 3,
};
```

<details>
<summary>Implementation</summary>

```js
class Node {
  constructor(value) {
    this.value = value;
    this.next = null;
  }
}
```

```js
class SinglyLinkedList {
  constructor() {
    this.head = null;
    this.tail = null;
    this.length = 0;
  }
   /*
   * get, set
   * push, pop
   * shift, unshift
   * /
}
```

</details>

<details>
<summary>Usage</summary>

- build Stack and Queue
- undo functionality in programs

</details>

## Doubly linked list

![](assets/2020-05-02_18h17_40.jpg)

```js
const doublyLinkedList = {
  head: {
    value: 12,
    next: {
      value: 99,
      next: {
        value: 37,
        next: null,
        prev: "[Circular]",
      },
      prev: "[Circular]",
    },
    prev: null,
  },
  tail: {
    value: 37,
    next: null,
    prev: {
      value: 99,
      next: "[Circular]",
      prev: {
        value: 12,
        next: "[Circular]",
        prev: null,
      },
    },
  },
  length: 3,
};
```

<details>
<summary>Implementation</summary>

```js
class Node {
  constructor(val) {
    this.val = val;
    this.next = null;
    this.prev = null;
  }
}
```

```js
class DoublyLinkedList {
  constructor() {
    this.head = null;
    this.tail = null;
    this.length = 0;
  }
  /*
   * get, set
   * push, pop
   * shift, unshift
   * /
}
```

</details>

<details>
<summary>Usage</summary>

- browser history
- undo and redo functionality in programs

</details>

## Stack

![](assets/stack.jpg)

```js
const stack = [12, 99, 37];
```

<details>
<summary>Implementation</summary>

- via Array
- via Singly Linked List

  - `push()` via `unshift()`
  - `pop()` via `shift()`

![](assets/unshift-shift.gif)

</details>

<details>
<summary>Usage</summary>

- javascript call stack
- undo/redo in Photoshop
- routing in javascript frameworks

</details>

## Queue

![](assets/queue.jpg)

```js
const queue = [12, 99, 37];
```

<details>
<summary>Implementation</summary>

- via Array
- via Singly Linked List
  - `enqueue()` via `push()`
  - `dequeue()` via `shift()`

![](assets/push-shift.gif)

</details>

<details>
<summary>Usage</summary>

- printing

</details>

## Binary search tree

![](assets/bst.jpg)

```js
const binarySearchTree = {
  root: {
    value: 10,
    left: {
      value: 6,
      left: {
        value: 3,
        left: null,
        right: null,
      },
      right: {
        value: 8,
        left: null,
        right: null,
      },
    },
    right: {
      value: 15,
      left: null,
      right: {
        value: 20,
        left: null,
        right: null,
      },
    },
  },
};
```

<details>
<summary>Implementation</summary>

```js
class Node {
  constructor(val) {
    this.val = val;
    this.left = null;
    this.right = null;
  }
}
```

```js
class BinarySearchTree {
  constructor() {
    this.root = null;
  }
  /*
   * insert, find, contains
   * bfs, dfs
   * preOrder, postOrder, inOrder
   * /
}
```

![](assets/search-create-bst.jpg)

</details>

<details>
<summary>Usage</summary>

- database indexing and search
- Huffman coding algorithm (file compression)
- Array can be converted to BST
- much faster than `Array` at search, insert, and delete (does not store indices unlike `Array`)
  - Array O(n)
  - BST O(log n)
- mcuh slower than `Array` at access
  - Array O(1)
  - BST O(log n)

</details>

## Hash table

![](assets/hash2.jpg)

```js
const hashTable = {
  keyMap: [
    null,
    [['Sue', 'F'], ['Nell', 'F']],
    null,
    [['Joe', 'M'], ['Ally', 'F'], ['Bob', 'M']],
    [['Dan', 'M']]
  ];
}
```

<details>
<summary>Implementation</summary>

![](assets/hash.jpg)

```js
class HashTable {
  constructor(size = 5) {
    this.keyMap = new Array(size);
    // this = { keyMap: [ , , , , ] }
  }

  _hash(key) {
    // return 3
  }

  set(key, value) {
    // [ , , [ 'Joe', 'M' ] , , ]
  }

  get(key) {
    // "M"
  }
}

let ht = new HashTable(5);

ht.set("Joe", "M");
// add more...
```

</details>

<details>
<summary>Usage</summary>

- efficiently lookup without relying on a linear search
- much faster than `Array` at search, insert, and delete
  - Array O(n)
  - Hash Table O(1)
- search in Ski Rent by shoes size
- search citizen passport deatils by ID
  - Array
    - check every ID starting from `1` untill, let's say, `9999`
  - Hash Table
    - convert `Vladimir Putin` to `1002` and directly access it

</details>

## Graph

| Adjacency List                     | Adjacency Matrix                   |
| ---------------------------------- | ---------------------------------- |
| Less space                         | More space                         |
| Fast to iterate over all edges     | Slow to iterate over all edges     |
| Slow to lookup for a specific edge | Fast to lookup for a specific edge |
