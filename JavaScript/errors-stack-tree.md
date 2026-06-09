# Reading Error Messages and Tracing Issues from the Stack Trace

## Purpose

When an error occurs, JavaScript provides:

1. Error Type
2. Error Message
3. Stack Trace

These help identify what failed and where it failed.

---

## Error Structure

Example:

```text
TypeError: Cannot read properties of undefined (reading 'name')
    at greet (app.js:2:20)
    at app.js:5:1
```

---

### Error Type

The first part indicates the category of error.

```text
TypeError
```

Common error types:

| Error Type | Meaning |
|------------|----------|
| ReferenceError | Variable does not exist |
| TypeError | Invalid operation on a value |
| SyntaxError | Invalid syntax |
| RangeError | Value outside allowed range |
| Error | Generic error |

Example:

```js
console.log(userName);
```

Output:

```text
ReferenceError: userName is not defined
```

---

### Error Message

The message describes the reason for the error.

Example:

```text
Cannot read properties of undefined (reading 'name')
```

This indicates that JavaScript attempted to access:

```js
undefined.name
```

Example:

```js
const user = undefined;

console.log(user.name);
```

---

### Stack Trace

The stack trace shows the sequence of function calls that led to the error.

### Example

```js
function greet(user) {
  console.log(user.name);
}

greet();
```

Output:

```text
TypeError: Cannot read properties of undefined (reading 'name')
    at greet (app.js:2:20)
    at app.js:5:1
```


### First Stack Frame

```text
at greet (app.js:2:20)
```

Meaning:

- File: `app.js`
- Line: `2`
- Column: `20`
- Function: `greet`

This is typically the location where the error occurred.

### Second Stack Frame

```text
at app.js:5:1
```

Meaning:

- The call to `greet()` originated from line 5.

---


Example Analysis:

1. Error Type

```text
TypeError
```

2. Error Message

```text
Cannot read properties of undefined
```

3. Error Location

```text
app.js:2
```

Problem:

```js
user.name
```

`user` is undefined because:

```js
greet();
```

was called without an argument.

---

### Example: SyntaxError

```js
JSON.parse("invalid json");
```

Output:

```text
SyntaxError: Unexpected token i in JSON at position 0
```

Analysis:

- Error Type: `SyntaxError`
- Invalid JSON input
- Check the JSON string format

---

### Reading a Stack Trace

Example:

```text
Error: Something failed
    at calculateTotal (app.js:10)
    at checkout (app.js:20)
    at app.js:30
```

Execution flow:

```text
app.js:30
  ↓
checkout()
  ↓
calculateTotal()
  ↓
Error thrown
```

The first stack frame usually identifies the source of the error.

---

### Error Object Properties

Inside a catch block:

```js
try {
  JSON.parse("invalid");
} catch (error) {
  console.log(error.name);
  console.log(error.message);
  console.log(error.stack);
}
```

Example output:

```text
SyntaxError
Unexpected token i in JSON at position 0
<stack trace>
```

---

## Debugging Process

When an error occurs:

### 1. Read the Error Type

```text
TypeError
ReferenceError
SyntaxError
```

### 2. Read the Error Message

```text
Cannot read properties of undefined
```

### 3. Locate the First Stack Frame

```text
at app.js:12:5
```

### 4. Open the File and Line Number

Inspect the code at that location.

### 5. Verify Variable Values

```js
console.log(variable);
```

or

```js
debugger;
```

---
