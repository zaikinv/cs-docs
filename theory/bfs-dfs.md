## BFS

💡 we add nodes that we have discovered — but not yet visited — to our queue, and come back to them later


- based on Queue
- can be applied to any Binary Tree
  - because of `node.left` and `node.right`

![](../assets/bfs.gif)

```js
function bfs(tree) {

  let node = tree.root;  
  const result = [];
  const queue = [node]; 
  // queue = [1]
  // result = []

  while (queue.length) {
    node = queue.shift() 
    // queue = []
    // result = [] - not yet fully visited
    if (node.left) queue.push(node.left)
    // queue = [2] - add new target to visit
    // result = [] - not yet fully visited
    if (node.right) queue.push(node.right)
    // queue = [2, 3] - add new target to visit
    // result = [] - not yet fully visited
    result.push(node.value)
    // queue = [2, 3]
    // result = [1] - visited!
  }

  return result;

}
```

#### Usage

- best for deep tree

## DFS

💡 we add all left nodes recursively downwards and add new recursive calls to callstack, when bottom reached, javascript will pop last item from the callstack

- based on stack (last in — first out)

![](../assets/preorder.gif)

```js
dfs(tree) {

  const result = []

  function traverse(node) {
    // stack = [traverse(4)]
    result.push(node.value) 
    // result = [4]
    // result = [4, 2]
    // result = [4, 2, 1]
    if (node.left) traverse(node.left) 
    // stack = [traverse(4), traverse(2)]
    // stack = [traverse(4), traverse(2), traverse(1)]
    if (node.right) traverse(node.right)
    // stack = [traverse(4), traverse(2)]
  };

  traverse(tree.root)

  return result

}

var tree = new BinarySearchTree()

tree.insert(10)
// insert more...

tree.dfs()
```

#### Usage

- best for wide tree