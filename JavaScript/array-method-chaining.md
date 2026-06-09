# Array Method Chaining

## What is Method Chaining?

Method chaining is the practice of calling multiple array methods one after another.

Each method returns a new array, which becomes the input for the next method.

---

## Example

```js
const numbers = [1, 2, 3, 4, 5];

const result = numbers
  .filter(num => num % 2 === 0)
  .map(num => num * 10);

console.log(result);
```

Output:

```js
[20, 40]
```

---
