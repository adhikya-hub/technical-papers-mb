# Difference Between Arrow Functions and Regular Functions

## Syntax

### Regular Function

```js
function greet(name) {
  return `Hello ${name}`;
}
```

### Arrow Function

```js
const greet = (name) => {
  return `Hello ${name}`;
};
```

---

## Short Syntax

Arrow functions support implicit return.

```js
const add = (a, b) => a + b;
```

Equivalent to:

```js
function add(a, b) {
  return a + b;
}
```

---

## `this` Binding

This is the most important difference.

### Regular Function

`this` depends on how the function is called.

```js
const user = {
  name: "Bruce",

  greet: function () {
    console.log(this.name);
  }
};

user.greet();
```

Output:

```js
Bruce
```

---

### Arrow Function

Arrow functions do not create their own `this`.

They use the `this` value from the surrounding scope.

```js
const user = {
  name: "Bruce",

  greet: () => {
    console.log(this.name);
  }
};

user.greet();
```

Output:

```js
undefined
```

The arrow function does not use `user` as `this`.

---

## arguments Object

## Regular Function

Has access to the `arguments` object.

```js
function show() {
  console.log(arguments);
}

show(1, 2, 3);
```

Output:

```js
[Arguments] { '0': 1, '1': 2, '2': 3 }
```

---

## Arrow Function

Does not have its own `arguments` object.

```js
const show = () => {
  console.log(arguments);
};

show(1, 2, 3);
```

Output:

```js
ReferenceError
```

Use rest parameters instead:

```js
const show = (...args) => {
  console.log(args);
};
```

---

## Hoisting

## Function Declaration

```js
greet();

function greet() {
  console.log("Hello");
}
```

Output:

```js
Hello
```

---

## Arrow Function

```js
greet();

const greet = () => {
  console.log("Hello");
};
```

Output:

```js
ReferenceError
```

---

## Callbacks

Arrow functions are commonly used for callbacks.

```js
const numbers = [1, 2, 3];

const doubled = numbers.map(num => num * 2);
```

Output:

```js
[2, 4, 6]
```

---

## Use Regular Functions

- Object methods
- Constructor functions
- When `this` should depend on the caller
- When `arguments` is needed

## Use Arrow Functions

- Callbacks
- Array methods
- Short utility functions
- When lexical `this` is desired
