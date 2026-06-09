# Spread Operator (...) in JavaScript

## What is the Spread Operator?

The spread operator (`...`) expands an iterable or object into its individual elements or properties.

```js
const numbers = [1, 2, 3];

console.log(...numbers);
```

Output:

```js
1 2 3
```

---

## Syntax

```js
...
```

It can be used with:

- Arrays
- Objects
- Function arguments

---

### Array Copying

```js
const arr1 = [1, 2, 3];

const arr2 = [...arr1];

console.log(arr2);
```

Output:

```js
[1, 2, 3]
```

Creates a shallow copy of the array.

---

### Merging Arrays

```js
const arr1 = [1, 2];
const arr2 = [3, 4];

const result = [...arr1, ...arr2];

console.log(result);
```

Output:

```js
[1, 2, 3, 4]
```

---

### Adding Elements While Copying

```js
const arr = [2, 3];

const result = [1, ...arr, 4];

console.log(result);
```

Output:

```js
[1, 2, 3, 4]
```

---

### Passing Array Elements as Function Arguments

```js
const numbers = [10, 20, 30];

console.log(Math.max(...numbers));
```

Output:

```js
30
```

Without spread:

```js
Math.max(numbers);
```

Output:

```js
NaN
```

---

### Converting Strings to Arrays

```js
const str = "Hello";

console.log([...str]);
```

Output:

```js
["H", "e", "l", "l", "o"]
```

---

### Object Copying

```js
const user = {
  name: "Bob",
  age: 25
};

const copy = {
  ...user
};

console.log(copy);
```

Output:

```js
{
  name: "Bob",
  age: 25
}
```

---

### Merging Objects

```js
const obj1 = {
  name: "Bob"
};

const obj2 = {
  age: 25
};

const result = {
  ...obj1,
  ...obj2
};

console.log(result);
```

Output:

```js
{
  name: "Bob",
  age: 25
}
```

---

### Overriding Properties

```js
const user = {
  name: "Bob",
  age: 25
};

const updatedUser = {
  ...user,
  age: 30
};

console.log(updatedUser);
```

Output:

```js
{
  name: "Bob",
  age: 30
}
```

Later properties overwrite earlier ones.

---

#### Shallow Copy

Spread creates a shallow copy.

```js
const user = {
  name: "Bob",
  address: {
    city: "Hyderabad"
  }
};

const copy = {
  ...user
};

copy.address.city = "Bangalore";

console.log(user.address.city);
```

Output:

```js
Bangalore
```

Nested objects are still shared.

---

## Spread vs Rest Operator

The syntax is the same:

```js
...
```

The meaning depends on usage.

### Spread

Expands values.

```js
const arr = [1, 2, 3];

console.log(...arr);
```

---

### Rest

Collects values.

```js
function sum(...numbers) {
  console.log(numbers);
}
```

Output:

```js
[1, 2, 3]
```

---
