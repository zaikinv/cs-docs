## Composition

- implemented via `function`

- stateless

  - functions exist independently and can be reused everywhere

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

## First class citizens

- simply means “being able to do what everyone else can do”

  - can assign as variable

  - pass as an argument

  - return

- basis for functional programming

## Higher order function

- function that not only accept data, but what to do (function)

## Currying

- function with N params → function with 1 params

- transforms a function that accepts multiple arguments “all at once” into a series of function calls

```js
const normal = (a, b, c, d) => a + b + c + d;

const curried = (a) => (b) => (c) => (d) => a + b + c + d;
```

- useful for FP to have less params for better composition and reuse

  - you can pass more arguments to `const sum = (a, b) => a + b` and they will be ignored `sum(a, b, 'ignored')`, but how can you pass less?

- example: `log`

```js
const normal = (date, message) => alert(`${date} ${message}`);

const curried = (date) => (message) => alert(`${date} ${message}`);

const logNow = curried("now");

logNow("message");
```

## Partial application

- function with N params → function with M params

- derive new function, with specific behavior, from general function

```js
const normal = (a, b, c, d) => a + b + c + d;

const partial = normal.bind(null, 1, 2, 3);
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
  return function (n) {
    if (n in cache) {
      return cache[n];
    } else {
      const answer = n * 2;
      cache[n] = answer;
      return answer;
    }
  };
};
// memoized()(10);
```

## Compose

- FP technique to progressively process data by multiple functions ("conveyor")

  ```js
  const compose = (f1, f2) => (data) => f1(f2(data));

  compose(
    (param) => param + 10,
    (param) => param * 10
  )(10); // 100
  ```

## Pipe

- same as compose, just in different order

  ```js
  const pipe = (f1, f2) => (data) => f2(f1(data));

  pipe(
    (param) => param + 10,
    (param) => param * 10
  )(10); // 200
  ```

## Dynamic programming

solving a complex problem by 
- breaking it down into a collection of simpler subproblems
- solving each of those subproblems just once
- storing their solutions

```js
/*
  Normal
*/
function fib(n) {
  if (n <= 2) return 1;
  return fib(n - 1) + fib(n - 2);
}
```

#### Memoization

Storing the results of and returning the cached result when the same inputs occur again

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

#### Tabulation

Storing the result of a previous result in a "table" (usually an array)

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