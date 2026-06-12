# Difference Between Synchronous and Asynchronous JavaScript

## Synchronous Execution

In synchronous execution, JavaScript executes one statement at a time in order.

The next statement waits until the current statement finishes.

```js
console.log("A");

console.log("B");

console.log("C");
```

Output:

```js
A
B
C
```

Execution order:

```text
A
↓
B
↓
C
```

---

## Problem with Synchronous Code

If an operation takes a long time, everything after it must wait.

```js
console.log("Start");

// Long-running task

console.log("End");
```

Output:

```js
Start
(wait)
End
```

The program cannot continue until the current task completes.

---

## Asynchronous Execution

In asynchronous execution, JavaScript can start an operation and continue executing other code without waiting for that operation to finish.

```js
console.log("Start");

setTimeout(() => {
    console.log("Timer Finished");
}, 2000);

console.log("End");
```

Output:

```js
Start
End
Timer Finished
```

Execution order:

```text
Start
↓
setTimeout registered
↓
End
↓
Timer Finished
```

---

## Example

```js
console.log("Start");

fetch("/users");

console.log("End");
```

Output:

```js
Start
End
```

The network request continues in the background.

---

Many operations take time:

- API requests
- Database queries
- Reading files
- Timers
- User interactions

If JavaScript waited synchronously for these operations, the application would become unresponsive.

---

## JavaScript is Still Single-Threaded

JavaScript executes code on a single call stack.

Async operations are handled by:

- Browser APIs / Node APIs
- Callback Queue
- Event Loop

This allows JavaScript to continue executing other code while waiting for async operations to complete.

---

### Synchronous Example

```js
function add(a, b) {
    return a + b;
}

const result = add(2, 3);

console.log(result);
```

Output:

```js
5
```

Each line waits for the previous line.

---

### Asynchronous Example

```js
setTimeout(() => {
    console.log("Hello");
}, 1000);

console.log("World");
```

Output:

```js
World
Hello
```

The timer callback executes later.

---

## Common Async APIs

```js
setTimeout()
```

```js
setInterval()
```

```js
fetch()
```

```js
addEventListener()
```

---

## Ways to Handle Async Code

### Callbacks

```js
setTimeout(() => {
    console.log("Done");
}, 1000);
```

---

### Promises

```js
fetch("/users")
    .then((response) => {
        console.log(response);
    });
```

---

### Async/Await

```js
async function getUsers() {
    const response = await fetch("/users");

    console.log(response);
}
```
