# Promises in JavaScript

A Promise is an object that represents the eventual result of an asynchronous operation.

The result may be:

- Available successfully
- Failed with an error
- Not available yet

Examples:

```js
fetch("/users");
```

```js
readFile("data.txt");
```

These operations take time, so they return a Promise.

Without Promises, asynchronous code often relies on nested callbacks.

Promises provide:

- Better readability
- Better error handling
- Easier chaining of async operations

---

## Creating a New Promise

A Promise is created using the `Promise` constructor.

```js
const promise = new Promise((resolve, reject) => {
    // async work
});
```

The executor function receives:

```js
resolve
```

and

```js
reject
```

---

### Resolving a Promise

```js
const promise = new Promise((resolve, reject) => {
    resolve("Success");
});
```

---

### Rejecting a Promise

```js
const promise = new Promise((resolve, reject) => {
    reject("Something went wrong");
});
```

---

### Promise States

Every Promise is always in one of three states.

---

#### 1. Pending

Initial state.

The operation has not completed yet.

```js
const promise = new Promise(() => {
});
```

State:

```text
Pending
```

---

### 2. Fulfilled

The operation completed successfully.

```js
const promise = new Promise((resolve) => {
    resolve("Success");
});
```

State:

```text
Fulfilled
```

Value:

```text
Success
```

---

#### 3. Rejected

The operation failed.

```js
const promise = new Promise((resolve, reject) => {
    reject("Error");
});
```

State:

```text
Rejected
```

Reason:

```text
Error
```

---

#### State Transitions

```text
           Pending
          /       \
         /         \
 Fulfilled      Rejected
```

A Promise can settle only once.

Valid:

```text
Pending → Fulfilled
```

or

```text
Pending → Rejected
```

Invalid:

```text
Fulfilled → Rejected
```

```text
Rejected → Fulfilled
```

---

## Consuming a Promise

To use the result of a Promise, use:

```js
.then()
```

and

```js
.catch()
```

---

### Using .then()

```js
const promise = Promise.resolve("Success");

promise.then((value) => {
    console.log(value);
});
```

Output:

```js
Success
```

---

### Using .catch()

```js
const promise = Promise.reject("Error");

promise.catch((error) => {
    console.log(error);
});
```

Output:

```js
Error
```

---

### Example

```js
const promise = new Promise((resolve, reject) => {
    const success = true;

    if (success) {
        resolve("Data received");
    } else {
        reject("Request failed");
    }
});

promise
    .then((result) => {
        console.log(result);
    })
    .catch((error) => {
        console.log(error);
    });
```

Output:

```js
Data received
```

---

## Promise.resolve()

Creates an already-fulfilled Promise.

```js
const promise = Promise.resolve("Hello");
```

Equivalent to:

```js
const promise = new Promise((resolve) => {
    resolve("Hello");
});
```

---

## Promise.reject()

Creates an already-rejected Promise.

```js
const promise = Promise.reject("Error");
```

Equivalent to:

```js
const promise = new Promise((resolve, reject) => {
    reject("Error");
});
```

---

```js
fetch("/users")
    .then((response) => {
        return response.json();
    })
    .then((data) => {
        console.log(data);
    })
    .catch((error) => {
        console.log(error);
    });
```
