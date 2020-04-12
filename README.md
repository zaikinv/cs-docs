# Bubble Sort

> starting from first element compare couples and swap if necessary: every outer loop (going from end to start) will get one sorted item at the end.

## `swap(arr, i, j)`

```js
const swap = (arr, i, j) => {
  [arr[i], arr[j]] = [arr[j], arr[i]];
};
```

## `bubbleSort(arr)`

```js
const bubbleSort = arr => {
  for (let i = arr.length - 1; i > 0; i--) {
    let noSwaps = true;

    for (let j = 0; j < i; j++) {
      if (arr[j] > arr[j + 1]) {
        swap(arr, j, j + 1);
        noSwaps = false;
      }
    }

    if (noSwaps) break;
  }

  return arr;
};
```

# Selection Sort

> starting from first element (current, smallest) compare with the rest of array and found less than smallest, update smallest. At the end of inner loop swap current and smallest.

## `swap(arr, i, j)`

```js
const swap = (arr, i, j) => {
  [arr[i], arr[j]] = [arr[j], arr[i]];
};
```

## `selectionSort(arr)`

```js
const selectionSort = arr => {
  for (let i = 0; i < arr.length; i++) {
    let smallest = i;
    for (let j = i + 1; j < arr.length; j++) {
      if (arr[smallest] > arr[j]) {
        smallest = j;
      }
    }
    if (i !== smallest) swap(arr, i, smallest);
  }
  return arr;
};
```

# Insertion Sort

> starting from second element (current), increase subarray (considered as fully sorted) loop backwards in the inner loop copying bigger values forward. At the end of the inner loop, replace first duplicate by current

## `insertionSort(arr)`

```js
const insertionSort = arr => {
  for (let i = 1; i < arr.length; i++) {
    let curr = arr[i];

    for (var j = i - 1; j >= 0 && arr[j] > curr; j--) arr[j + 1] = arr[j];

    arr[j + 1] = curr;
  }

  return arr;
};
```

# Merge Sort

> description

## `merge(arr1, arr2)`

```js
const merge = (arr1, arr2) => {
  let ret = [];
  let i = 0;
  let j = 0;

  while (i < arr1.length && j < arr2.length) {
    if (arr1[i] < arr2[j]) ret.push(arr1[i++]);
    else ret.push(arr2[j++]);
  }

  while (i < arr1.length) ret.push(arr1[i++]);
  while (j < arr2.length) ret.push(arr2[j++]);

  return ret;
};
```

## `mergeSort(arr)`

```js
const mergeSort = arr => {
  if (arr.length <= 1) return arr;

  let mid = Math.floor(arr.length / 2);
  let left = mergeSort(arr.slice(0, mid));
  let right = mergeSort(arr.slice(mid));

  return merge(left, right);
};
```

# Quick Sort

> PARTITION: scan array starting after pivot element (swapIdx = 0) and compare every item with pivot element, for every smaller element found: first increase swapIdx and then swap it with element at swapIdx. After loop, finally swap pivot with element at swap index.

> SORT: recursively apply to parts before and after pivot element checking if start < end

## `pivot(arr, left = 0, right = arr.length - 1)`

```js
const pivot = (arr, left, right) => {
  const swap = (arr, i, j) => {
    [arr[i], arr[j]] = [arr[j], arr[i]];
  };

  let pivot = arr[left];
  let swapIndex = left;

  for (let i = left + 1; i <= right; i++)
    if (pivot > arr[i]) swap(arr, ++swapIndex, i);
  swap(arr, left, swapIndex);

  return swapIndex;
};
```

## `quickSort(arr)`

```js
const quickSort = (arr, left = 0, right = arr.length - 1) => {
  if (left < right) {
    let pivotIndex = pivot(arr, left, right);
    quickSort(arr, left, pivotIndex - 1);
    quickSort(arr, pivotIndex + 1, right);
  }

  return arr;
};
```
