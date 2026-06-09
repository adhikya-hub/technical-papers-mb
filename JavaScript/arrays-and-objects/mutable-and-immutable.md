# Mutable and Immutable Methods in JavaScript

## Mutable

A method is **mutable** if it changes the original array or object.

```js
const arr = [1, 2, 3];

arr.push(4);

console.log(arr);
```

Output:

```js
[1, 2, 3, 4]
```

The original array was modified.

---

## Immutable

A method is **immutable** if it returns a new value and leaves the original unchanged.

```js
const arr = [1, 2, 3];

const result = arr.concat([4]);

console.log(arr);
console.log(result);
```

Output:

```js
[1, 2, 3]
[1, 2, 3, 4]
```

The original array remains unchanged.

---

| Mutable | Immutable |
|----------|----------|
| push | concat |
| pop | slice |
| shift | map |
| unshift | filter |
| splice | reduce |
| sort | find |
| reverse | findIndex |
| Object.assign(target, source) | includes |
| Object.freeze | indexOf |
| Object.seal | join |
|  | flat |
|  | Object.keys |
|  | Object.values |
|  | Object.entries |

---
