# Popular Array Utility Methods

## Mutable vs Immutable Methods

### Mutable

These modify the original array.

```js
push()
pop()
splice()
sort()
```

### Immutable

These return a new value/array without modifying the original array.

```js
concat()
slice()
join()
flat()
find()
findIndex()
includes()
indexOf()
filter()
map()
reduce()
```

---

## Basics

### Array.push()

Adds element(s) to the end.

**Mutable**

```js
const arr = [1, 2];

arr.push(3);

console.log(arr);
```

Output:

```js
[1, 2, 3]
```

Returns:

```js
New length of array
```

---

### Array.pop()

Removes the last element.

**Mutable**

```js
const arr = [1, 2, 3];

const removed = arr.pop();

console.log(arr);
console.log(removed);
```

Output:

```js
[1, 2]
3
```

---

### Array.concat()

Combines arrays.

**Immutable**

```js
const arr1 = [1, 2];
const arr2 = [3, 4];

const result = arr1.concat(arr2);

console.log(result);
```

Output:

```js
[1, 2, 3, 4]
```

---

### Array.slice()

Extracts a portion of an array.

**Immutable**

```js
const arr = [10, 20, 30, 40];

const result = arr.slice(1, 3);

console.log(result);
```

Output:

```js
[20, 30]
```

---

### Array.splice()

Add, remove, or replace elements.

**Mutable**

#### Remove

```js
const arr = [1, 2, 3, 4];

arr.splice(1, 2);

console.log(arr);
```

Output:

```js
[1, 4]
```

#### Add

```js
const arr = [1, 4];

arr.splice(1, 0, 2, 3);

console.log(arr);
```

Output:

```js
[1, 2, 3, 4]
```

---

### Array.join()

Converts array into string.

**Immutable**

```js
const arr = ["A", "B", "C"];

console.log(arr.join("-"));
```

Output:

```js
A-B-C
```

---

### Array.flat()

Flattens nested arrays.

**Immutable**

```js
const arr = [1, [2, 3], [4, 5]];

console.log(arr.flat());
```

Output:

```js
[1, 2, 3, 4, 5]
```

---

## Finding Methods

### Array.find()

Returns first matching element.

**Immutable**

```js
const nums = [5, 10, 15];

const result = nums.find(num => num > 8);

console.log(result);
```

Output:

```js
10
```

---

### Array.indexOf()

Returns index of first occurrence.

**Immutable**

```js
const arr = ["A", "B", "C"];

console.log(arr.indexOf("B"));
```

Output:

```js
1
```

Not found:

```js
-1
```

---

### Array.includes()

Checks existence.

**Immutable**

```js
const arr = ["A", "B", "C"];

console.log(arr.includes("B"));
```

Output:

```js
true
```

---

### Array.findIndex()

Returns index of first matching element.

**Immutable**

```js
const nums = [5, 10, 15];

const index = nums.findIndex(num => num > 8);

console.log(index);
```

Output:

```js
1
```

---

## Higher Order Functions

## Array.forEach()

Runs callback for every element.

**Immutable** (unless you manually modify something)

```js
const nums = [1, 2, 3];

nums.forEach(num => {
  console.log(num);
});
```

Output:

```js
1
2
3
```

Returns:

```js
undefined
```

---

### Array.filter()

Returns matching elements.

**Immutable**

```js
const nums = [1, 2, 3, 4];

const even = nums.filter(num => num % 2 === 0);

console.log(even);
```

Output:

```js
[2, 4]
```

---

### Array.map()

Transforms each element.

**Immutable**

```js
const nums = [1, 2, 3];

const doubled = nums.map(num => num * 2);

console.log(doubled);
```

Output:

```js
[2, 4, 6]
```

---

### Array.reduce()

Reduces array to a single value.

**Immutable**

```js
const nums = [1, 2, 3, 4];

const sum = nums.reduce((acc, curr) => {
  return acc + curr;
}, 0);

console.log(sum);
```

Output:

```js
10
```

---

### Array.sort()

Sorts array.

**Mutable**

```js
const nums = [3, 1, 2];

nums.sort();

console.log(nums);
```

Output:

```js
[1, 2, 3]
```

### Important

```js
[10, 2, 100].sort();
```

Output:

```js
[10, 100, 2]
```

Because sorting is alphabetical by default.

Correct numeric sort:

```js
const nums = [10, 2, 100];

nums.sort((a, b) => a - b);

console.log(nums);
```

Output:

```js
[2, 10, 100]
```

```js
function compareFn(a, b) {
  if (a is less than b by some ordering criterion) {
    return -1;
  } else if (a is greater than b by the ordering criterion) {
    return 1;
  }
  // a must be equal to b
  return 0;
}
```

---

## Advanced: Method Chaining

Combining multiple array methods together.

```js
const nums = [1, 2, 3, 4, 5];

const result = nums
  .filter(num => num % 2 === 0)
  .map(num => num * 10);

console.log(result);
```

Output:

```js
[20, 40]
```

---

# Quick Revision Table

| Method | Purpose | Mutable |
|----------|----------|----------|
| push | Add at end | Yes |
| pop | Remove last | Yes |
| concat | Merge arrays | No |
| slice | Extract portion | No |
| splice | Add/remove/replace | Yes |
| join | Array → String | No |
| flat | Flatten nested arrays | No |
| find | First matching value | No |
| indexOf | Find index | No |
| includes | Check existence | No |
| findIndex | First matching index | No |
| forEach | Iterate | No |
| filter | Select elements | No |
| map | Transform elements | No |
| reduce | Single value | No |
| sort | Sort array | Yes |

---
