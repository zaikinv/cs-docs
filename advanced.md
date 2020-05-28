## BFS

We add nodes that we have discovered — but not yet visited — to our queue, and come back to them later

- based on Queue
- can be applied to any Binary Tree
- best for deep tree 

<details>
<summary>Example</summary>


![](../assets/bfs.gif)

#### Binary search tree

```js
function bfs(tree) {
  let node = tree.root;
  const result = [];
  const queue = [node];
  // queue = [1]
  // result = []

  while (queue.length) {
    node = queue.shift();
    // queue = []
    // result = [] - not yet fully visited
    if (node.left) queue.push(node.left);
    // queue = [2] - add new target to visit
    // result = [] - not yet fully visited
    if (node.right) queue.push(node.right);
    // queue = [2, 3] - add new target to visit
    // result = [] - not yet fully visited
    result.push(node.value);
    // queue = [2, 3]
    // result = [1] - visited!
  }

  return result;
}
```

#### Graph

![](../assets/20200510103948bfs.png)

```js
function bfs(start) {
  const result = [];
  const visited = {};
  const queue = [start];
  // queue = ["A"]
  let currVertex;

  visited[start] = true;
  // visited = { "A": true }

  while (queue.length) {
    currVertex = queue.shift();
    // queue = []
    // currVertex = "A"
    result.push(currVertex);
    // result = ["A"]

    this.adjList[currVertex].forEach((neighbor) => {
      // neighbor = "B"
      // neighbor = "C"
      if (!visited[neighbor]) {
        visited[neighbor] = true;
        // visited = { "A": true, "B": true, "C": true }
        queue.push(neighbor);
        // queue = ["B", "C"]
      }
    });
  }

  return result;
}
```

</details>

## DFS

We add all left nodes recursively downwards and add new recursive calls to callstack, when bottom reached, javascript will pop last item from the callstack

- based on stack (last in — first out)
- best for wide tree

<details>
<summary>Example</summary>

![](../assets/preorder.gif)

#### Binary search tree

```js
function dfs(tree) {
  const result = [];

  function traverse(node) {
    // stack = [traverse(4)]
    result.push(node.value);
    // result = [4]
    // result = [4, 2]
    // result = [4, 2, 1]
    if (node.left) traverse(node.left);
    // stack = [traverse(4), traverse(2)]
    // stack = [traverse(4), traverse(2), traverse(1)]
    if (node.right) traverse(node.right);
    // stack = [traverse(4), traverse(2)]
  }

  traverse(tree.root);

  return result;
}
```

#### Graph

![](../assets/20200510103948dfs.png)

```js
function dfs(start) {
  const result = [];

  const visited = {};
  const adjList = this.adjList;
  /*
   *     adjList: {
   *       A: ["B", "C"],
   *       B: ["A", "D"],
   *       C: ["A", "E"],
   *       D: ["B", "E", "F"],
   *       E: ["C", "D", "F"],
   *       F: ["D", "E"],
   *     }
   */

  function traverse(vertex) {
    // vertex = "A"
    // vertex = "B"
    // vertex = "D"
    // vertex = "E"
    // vertex = "C"
    if (!vertex) return null;

    visited[vertex] = true;
    // visited = { "A": true }
    // visited = { "A": true, "B": true }
    // visited = { "A": true, "B": true, "D": true }
    // visited = { "A": true, "B": true, "D": true, "E": true }
    // visited = { "A": true, "B": true, "D": true, "E": true, "C": true }
    // visited = { "A": true, "B": true, "D": true, "E": true, "C": true, "F": true }

    result.push(vertex);
    // result = ["A"]
    // result = ["A", "B"]
    // result = ["A", "B", "D"]
    // result = ["A", "B", "D", "E"]
    // result = ["A", "B", "D", "E", "C"]
    // result = ["A", "B", "D", "E", "C", "F"]

    adjList[vertex].forEach((neighbor) => {
      if (!visited[neighbor]) {
        return traverse(neighbor);
        // traverse("B")
        // traverse("D")
        // traverse("E")
        // traverse("C")
      }
    });
  }

  traverse(start);
  // traverse("A")

  return result;
}
```

</details>

## Backtracking

Backtracking is implemented as DFS with pruning of branches based on constraints instead trying all possibilities (no brute-force).

<details>
<summary>Example</summary>

![](assets/backtracking.jpg)

```js
function restoreIpAddresses(originalString) {
  // originalString = 25525511135
  const result = [];
  backtrack(0, []);
  return result;

  function backtrack(start, tempArr) {
    // push results - called 2 times
    if (tempArr.length === 4 && start === originalString.length) {
      result.push(tempArr.join("."));
      return;
    }

    // 4th level reached, don't go deeper
    if (tempArr.length === 4) {
      return;
    }

    // try 1-char, 2-char, 3-char long combinations
    for (let i = 1; i < 4; i++) {
      const segment = originalString.substring(start, start + i);

      if (segment.length > 1 && segment[0] === "0") {
        continue;
      }

      if (parseInt(segment) < 256 && parseInt(segment) >= 0) {
        // add another combination in current segment
        tempArr.push(segment);
        // try the whole IP address e.g.:
        // ["2", "5", "5", "2"]
        // ["2", "5", "5", "25"]
        // ["2", "5", "5", "255"]
        backtrack(start + i, tempArr);
        // remove sibling
        // ["2", "5", "5"]
        // ["2", "5", "5"]
        // ["2", "5", "5"]
        tempArr.pop();

      }
    }
  }
}

restoreIpAddresses("25525511135");
```

Simpler tree:

![](assets/20200528134155.png)

</details>

## Greedy

Make best choice at the moment.

- Break into subproblems
- Find optimal substructure (idea)
- Sort (time/distance/size)
- Solve greedily (iteration/recursion)

<details>
<summary>Example</summary>

- Break into subproblems ➡️ selection of events (select / remove)
- Find optimal substructure (idea) ➡️ every interval must finish as soon as possible to include more events
- Sort (time/distance/size) ➡️ sort by end time
- Solve greedily (iteration/recursion) ➡️ iterate

![](assets/20200525140231.png)

```js
function countOverlapIntervals(intervals) {
  if (intervals.length == 0) return 0;

  intervals.sort((a, b) => a[1] - b[1]);

  let overlapIntervals = 0;
  let lastEventEnd = intervals[0][1];

  for (let i = 1; i < intervals.length; i++) {
    const [currentEventStart, currentEventEnd] = intervals[i];

    if (currentEventStart < lastEventEnd) {
      // overlap, choose the one that finish first (remove biggest blocker)
      lastEventEnd = Math.min(currentEventEnd, lastEventEnd);
      overlapIntervals++;
    } else {
      // no overlap, update current event end
      lastEventEnd = currentEventEnd;
    }
  }

  return overlapIntervals;
}

countOverlapIntervals([
  [1, 2],
  [2, 3],
  [1, 4],
  [4, 5],
]);
```

</details>

## Divide and conquer

Optimizes by breaking down into simpler versions of itself.

## Dynamic programming

Optimizes by caching solutions.

- breaking it down into a collection of simpler subproblems
- solving each of those subproblems just once
- storing their solutions

<details>
<summary>Example</summary>

```js
/*
  Normal
*/
function fib(n) {
  if (n <= 2) return 1;
  return fib(n - 1) + fib(n - 2);
}
```

```js
/*
 *  Memoized
 */
function fib(n, memo = []) {
  if (memo[n] !== undefined) return memo[n];
  if (n <= 2) return 1;
  var res = fib(n - 1, memo) + fib(n - 2, memo);
  memo[n] = res;
  return res;
}
```

```js
/*
 *  Tabulated
 */
function fib(n){
    if(n <= 2) return 1;
    var fibNums = [0,1,1];
    for(var i = 3; i <= n; i++){
        fibNums[i] = fibNums[i-1] + fibNums[i-2];
    }
    return fibNums[n];
}
```

</details>