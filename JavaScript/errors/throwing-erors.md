# Throwing Errors in JavaScript

## What is `throw`?

The `throw` keyword is used to create and raise an error manually.

```js
throw new Error("Something went wrong");
```

When JavaScript encounters `throw`, execution stops immediately and looks for a matching `catch` block.

---

## Basic Syntax

```js
throw value;
```

```js
throw new Error("Something went wrong");
```

---

## Throwing a Custom Error

```js
const age = 15;

if (age < 18) {
  throw new Error("Age must be at least 18");
}
```

Output:

```js
Error: Age must be at least 18
```

---

## Catching Error

```js
try {
  const age = 15;

  if (age < 18) {
    throw new Error("Age must be at least 18");
  }
} catch (error) {
  console.log(error.message);
}
```

Output:

```js
Age must be at least 18
```

---

## Error Object

```js
throw new Error("Invalid input");
```

Creates an Error object.

Properties:

```js
error.name
```

```js
error.message
```

Example:

```js
try {
  throw new Error("Invalid input");
} catch (error) {
  console.log(error.name);
  console.log(error.message);
}
```

Output:

```js
Error
Invalid input
```

---

## Throwing Different Error Types

```js
throw new TypeError("Expected a string");
```

```js
throw new RangeError("Age must be positive");
```

```js
throw new ReferenceError("Variable not found");
```

```js
throw new SyntaxError("Invalid syntax");
```
