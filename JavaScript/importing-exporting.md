# Importing and Exporting Modules Using `require` and `module.exports`

A module is simply a JavaScript file.

Modules allow code to be split across multiple files and reused where needed.

---

# Exporting a Value

## math.js

```js
function add(a, b) {
  return a + b;
}

module.exports = add;
```

---

# Importing a Value

## app.js

```js
const add = require("./math");

console.log(add(2, 3));
```

Output:

```js
5
```

---

## Exporting Multiple Values

### math.js

```js
function add(a, b) {
  return a + b;
}

function subtract(a, b) {
  return a - b;
}

module.exports = {
  add,
  subtract
};
```

---

## Importing Multiple Values

### app.js

```js
const math = require("./math");

console.log(math.add(10, 5));
console.log(math.subtract(10, 5));
```

Output:

```js
15
5
```

---

## Object Destructuring

Instead of:

```js
const math = require("./math");

math.add(1, 2);
```

You can write:

```js
const { add, subtract } = require("./math");

console.log(add(1, 2));
console.log(subtract(5, 2));
```

Output:

```js
3
3
```

---

### Node Module

```js
const fs = require("fs");
```

No `./` is needed for built-in or installed packages.

---
