# Error Handling (try...catch) in JavaScript

## What is Error Handling?

Error handling allows your program to deal with runtime errors gracefully instead of crashing.

Without error handling:

```js
const user = JSON.parse("invalid json");

console.log(user);
```

Output:

```js
SyntaxError
```

Program stops executing.

---

# try...catch Syntax

```js
try {
  // code that may throw an error
} catch (error) {
  // handle the error
}
```

Example:

```js
try {
  JSON.parse("invalid json");
} catch (error) {
  console.log("Something went wrong");
}
```

Output:

```js
Something went wrong
```

---

# How It Works

1. JavaScript enters the `try` block.
2. If no error occurs, `catch` is skipped.
3. If an error occurs, execution jumps to `catch`.
4. The error object becomes available inside `catch`.

---

## Accessing Error Details

```js
try {
  JSON.parse("invalid json");
} catch (error) {
  console.log(error);
}
```

Output:

```js
SyntaxError: Unexpected token ...
```

---

## Useful Error Properties

### error.name

```js
try {
  JSON.parse("invalid json");
} catch (error) {
  console.log(error.name);
}
```

Output:

```js
SyntaxError
```

---

### error.message

```js
try {
  JSON.parse("invalid json");
} catch (error) {
  console.log(error.message);
}
```

Output:

```js
Unexpected token ...
```

---

## finally

Runs whether an error occurs or not.

```js
try {
  console.log("Inside try");
} catch (error) {
  console.log("Inside catch");
} finally {
  console.log("Always runs");
}
```

Output:

```js
Inside try
Always runs
```

---

## Common Built-in Error Types

### SyntaxError

Invalid JavaScript syntax.

```js
JSON.parse("invalid");
```

---

### ReferenceError

Using an undefined variable.

```js
console.log(name);
```

---

### TypeError

Performing an invalid operation.

```js
undefined.toUpperCase();
```

---

### RangeError

Value outside allowed range.

```js
new Array(-1);
```

---
