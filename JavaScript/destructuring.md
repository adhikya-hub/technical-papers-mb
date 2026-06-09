# Destructuring in JavaScript

Destructuring is a syntax that allows values to be extracted from arrays or properties from objects into separate variables.

---

## Array Destructuring

```js
const colors = ["red", "green", "blue"];

const [first, second] = colors;

console.log(first);
console.log(second);
```

Output:

```js
red
green
```

---

### Extracting Multiple Values

```js
const numbers = [10, 20, 30];

const [a, b, c] = numbers;

console.log(a, b, c);
```

Output:

```js
10 20 30
```

---

### Skipping Values

```js
const numbers = [10, 20, 30];

const [first, , third] = numbers;

console.log(first);
console.log(third);
```

Output:

```js
10
30
```

---

### Default Values

```js
const numbers = [10];

const [a, b = 20] = numbers;

console.log(a);
console.log(b);
```

Output:

```js
10
20
```

---

### Rest Operator with Arrays

```js
const numbers = [1, 2, 3, 4, 5];

const [first, ...rest] = numbers;

console.log(first);
console.log(rest);
```

Output:

```js
1
[2, 3, 4, 5]
```

---

### Swapping Variables

Without destructuring:

```js
let a = 10;
let b = 20;

let temp = a;
a = b;
b = temp;
```

With destructuring:

```js
let a = 10;
let b = 20;

[a, b] = [b, a];

console.log(a, b);
```

Output:

```js
20 10
```

---

## Object Destructuring

```js
const user = {
  name: "Bob",
  age: 25
};

const { name, age } = user;

console.log(name);
console.log(age);
```

Output:

```js
Bob
25
```

---

### Variable Names Must Match Property Names

```js
const user = {
  name: "Bob",
  age: 25
};

const { name } = user;
```

Works because the property is named `name`.

---

### Renaming Variables

```js
const user = {
  name: "Bob"
};

const { name: userName } = user;

console.log(userName);
```

Output:

```js
Bob
```

---

### Default Values

```js
const user = {
  name: "Bob"
};

const { age = 18 } = user;

console.log(age);
```

Output:

```js
18
```

---

### Rest Operator with Objects

```js
const user = {
  name: "Bob",
  age: 25,
  city: "Hyderabad"
};

const { name, ...rest } = user;

console.log(name);
console.log(rest);
```

Output:

```js
Bob

{
  age: 25,
  city: "Hyderabad"
}
```

---

### Nested Object Destructuring

```js
const user = {
  name: "Bob",
  address: {
    city: "Hyderabad"
  }
};

const {
  address: { city }
} = user;

console.log(city);
```

Output:

```js
Hyderabad
```

---

### Destructuring Function Parameters

Without destructuring:

```js
function greet({ name }) {
  console.log(name);
}
```

Usage:

```js
greet({
  name: "Bob"
});
```

Output:

```js
Bob
```

---

### Array Destructuring in Loops

```js
const entries = [
  ["name", "Bob"],
  ["age", 25]
];

for (const [key, value] of entries) {
  console.log(key, value);
}
```

Output:

```js
name Bob
age 25
```

---
