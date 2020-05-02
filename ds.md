## Singly linked list

![](assets/2020-05-02_18h15_59.jpg)

### Implementation

```js
class Node {
  constructor(val) {
    this.val = val;
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
  // get, setpush, pop, shift, unshift
}
```

### Usage

- build Stack and Queue
- undo functionality in programs

## Doubly linked list

![](assets/2020-05-02_18h17_40.jpg)

### Implementation

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
class SinglyLinkedList {
  constructor() {
    this.head = null;
    this.tail = null;
    this.length = 0;
  }
  // get, set, push, pop, shift, unshift
}
```

### Usage

- browser history
- undo and redo functionality in programs

## Stack

![](assets/stack.jpg)

### Implementation

- via Array
- via Singly Linked List
  - `pop()` via `push()`
  - `push()` via `unshift()`

### Usage

- javascript call stack
- undo/redo in Photoshop
- routing in javascript frameworks

## Queue (FIFO)

![](assets/queue.jpg)

### Implementation

- via Array
- via Singly Linked List
  - `enqueue()` via `push()`
  - `dequeue()` via `shift()`

### Usage

- printing

## Graph

| Adjacency List                     | Adjacency Matrix                   |
| ---------------------------------- | ---------------------------------- |
| Less space                         | More space                         |
| Fast to iterate over all edges     | Slow to iterate over all edges     |
| Slow to lookup for a specific edge | Fast to lookup for a specific edge |
