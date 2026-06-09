# Importance of the catch Block

The `catch` block handles errors that occur inside a `try` block.

```js
try {
  JSON.parse("invalid json");
} catch (error) {
  console.log("Error occurred");
}
```

Output:

```js
Error occurred
```

---

Without a `catch` block, an unhandled error can stop the execution of the current code path.

```js
JSON.parse("invalid json");

console.log("Program continues");
```

Output:

```text
SyntaxError: Unexpected token ...
```

The second statement is not executed.

---

### Preventing Application Crashes

```js
try {
  JSON.parse("invalid json");
} catch (error) {
  console.log("Invalid JSON received");
}

console.log("Program continues");
```

Output:

```js
Invalid JSON received
Program continues
```

The error is handled and execution continues.

---

### Accessing Error Information

The `catch` block receives the thrown error object.

```js
try {
  JSON.parse("invalid json");
} catch (error) {
  console.log(error.name);
  console.log(error.message);
}
```

Output:

```js
SyntaxError
Unexpected token i in JSON at position 0
```

---

### Providing Meaningful Feedback

```js
try {
  JSON.parse(data);
} catch (error) {
  console.log("Invalid data format");
}
```

Instead of showing a technical error message, the application can provide a user-friendly message.

---

### Logging Errors

```js
try {
  riskyOperation();
} catch (error) {
  console.error(error);
}
```

This helps identify and investigate issues.

---

### Handling Custom Errors

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

### catch is Optional

Valid syntax:

```js
try {
  riskyOperation();
} finally {
  cleanup();
}
```

However, if error handling is required, a `catch` block should be used.

---
