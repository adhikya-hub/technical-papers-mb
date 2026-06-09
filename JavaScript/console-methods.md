# Common Console Methods in JavaScript

The `console` object provides methods for logging information, debugging, and inspecting code.

---

## console.log()

General-purpose logging.

```js
console.log("Hello");
```

Output:

```js
Hello
```

---

## console.error()

Logs errors.

```js
console.error("Something went wrong");
```

Output:

```text
Something went wrong
```

Usually displayed in red in browser developer tools.

---

## console.warn()

Logs warnings.

```js
console.warn("This feature is deprecated");
```

Output:

```text
This feature is deprecated
```

Usually displayed with a warning icon.

---

## console.info()

Logs informational messages.

```js
console.info("Application started");
```

Output:

```text
Application started
```

Similar to `console.log()` in most environments.

---

## console.table()

Displays arrays or objects in table format.

```js
const users = [
  { name: "Bruce", age: 25 },
  { name: "Clark", age: 30 }
];

console.table(users);
```

Output:

```text
┌─────────┬─────────┬─────┐
│ (index) │  name   │ age │
├─────────┼─────────┼─────┤
│    0    │ Bruce   │ 25  │
│    1    │ Clark   │ 30  │
└─────────┴─────────┴─────┘
```

---

## console.clear()

Clears the console.

```js
console.clear();
```

---

## console.count()

Counts how many times a label has been logged.

```js
console.count("click");
console.count("click");
console.count("click");
```

Output:

```text
click: 1
click: 2
click: 3
```

---

## console.time()

Starts a timer.

```js
console.time("loop");
```

---

## console.timeEnd()

Stops the timer and prints the duration.

```js
console.time("loop");

for (let i = 0; i < 1000000; i++) {}

console.timeEnd("loop");
```

Output:

```text
loop: 3.4ms
```

---

## console.assert()

Logs a message only if the condition is false.

```js
console.assert(2 > 5, "Condition failed");
```

Output:

```text
Assertion failed: Condition failed
```

---

## console.trace()

Prints the current call stack.

```js
function a() {
  b();
}

function b() {
  console.trace();
}

a();
```

Output:

```text
Trace
  at b
  at a
```

Useful for tracing function calls.

---

| Method | Purpose |
|----------|----------|
| console.log() | General logging |
| console.error() | Errors |
| console.warn() | Warnings |
| console.info() | Information |
| console.table() | Display tabular data |
| console.dir() | Inspect objects |
| console.clear() | Clear console |
| console.count() | Count executions |
| console.time() | Start timer |
| console.timeEnd() | Stop timer |
| console.assert() | Assert condition |
| console.group() | Start group |
| console.groupEnd() | End group |
| console.trace() | Print call stack |

---
