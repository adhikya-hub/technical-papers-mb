# What is the Event Loop?

The Event Loop is the mechanism that allows JavaScript to handle asynchronous operations while remaining single-threaded.

It continuously checks:

1. Is the Call Stack empty?
2. Are there callbacks waiting in a queue?

If the stack is empty, it moves waiting callbacks to the Call Stack for execution.

JavaScript has only one Call Stack.

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

Only one piece of code can execute at a time.

To support:

- Timers
- API requests
- User events

JavaScript relies on Browser APIs and the Event Loop.

---

## Example

```js
console.log("Start");

setTimeout(() => {
    console.log("Timer");
}, 0);

console.log("End");
```

Output:

```js
Start
End
Timer
```

---

### Step 1

```js
console.log("Start");
```

Output:

```js
Start
```

Call Stack:

```text
console.log()
```

↓

```text
empty
```

---

### Step 2

```js
setTimeout(...)
```

The browser registers the timer.

The callback does **not** enter the Call Stack.

It is handled by the Timer API.

---

### Step 3

```js
console.log("End");
```

Output:

```js
End
```

---

### Step 4

Timer completes.

The callback is placed into the Callback Queue.

```text
Callback Queue

[ callback ]
```

---

### Step 5

The Event Loop checks:

```text
Is the Call Stack empty?
```

Yes.

The callback is moved to the Call Stack.

```js
console.log("Timer");
```

Output:

```js
Timer
```

---

### Call Stack

Executes JavaScript code.

```text
LIFO Stack
```

---

### Web Browser APIs

Handle asynchronous operations.

Examples:

```js
setTimeout()
```

```js
fetch()
```

```js
addEventListener()
```

---

### Callback Queue

Stores completed callback functions waiting to execute.

```text
[
  timerCallback,
  clickCallback
]
```

---

### Event Loop

Continuously checks:

```text
Call Stack Empty?
```

If yes:

```text
Move callback from queue to stack
```

---

### Example

```js
button.addEventListener("click", () => {
    console.log("Clicked");
});
```

What happens:

1. Browser listens for clicks.
2. User clicks button.
3. Callback enters Callback Queue.
4. Event Loop waits for an empty stack.
5. Callback executes.

---

### Event Loop Rule

A callback can execute only when:

```text
Call Stack is empty
```

Even if a timer has finished.

---

### Example

```js
setTimeout(() => {
    console.log("Timer");
}, 0);

for (let i = 0; i < 1000000000; i++) {
}
```

Output:

```js
Timer
```

appears only after the loop finishes.

Reason:

```text
Call Stack not empty
```

The Event Loop must wait.

---

## Macrotasks vs Microtasks

### Microtasks

Higher-priority asynchronous tasks.

Examples:

```js
Promise.then()
Promise.catch()
Promise.finally()
queueMicrotask()
```

---

### Macrotasks

Regular asynchronous tasks.

Examples:

```js
setTimeout()
setInterval()
addEventListener()
```

---

### Execution Order

After synchronous code finishes:

```text
1. Execute all microtasks
2. Execute one macrotask
3. Repeat
```

---

### Example

```js
setTimeout(() => {
    console.log("Timer");
}, 0);

Promise.resolve().then(() => {
    console.log("Promise");
});
```

Output:

```js
Promise
Timer
```

Because:

```text
Microtasks run before macrotasks.
```

---
