# How JavaScript Executes Code

When JavaScript runs a program, it executes code in two phases:

1. Memory Creation Phase
2. Execution Phase

This process happens inside an **Execution Context**.

---

## Execution Context

An execution context is the environment in which JavaScript executes code.

JavaScript creates:

- Global Execution Context (GEC)
- Function Execution Context (for each function call)

---

## Phase 1: Memory Creation Phase

Before executing any code, JavaScript scans the entire scope and allocates memory.

Example:

```js
var a = 10;

function greet() {
    console.log("Hello");
}

console.log(a);
```

Memory allocation:

```text
a      → undefined
greet  → function definition
```

No code has executed yet.

Only memory is allocated.

---

## Phase 2: Execution Phase

JavaScript executes code line by line.

```js
var a = 10;
```

Updates:

```text
a → 10
```

---

```js
console.log(a);
```

Output:

```js
10
```

---

## Example

```js
var x = 5;

function square(number) {
    return number * number;
}

var result = square(x);

console.log(result);
```

---

### Memory Creation Phase

```text
x       → undefined
square  → function definition
result  → undefined
```

---

### Execution Phase

```js
x = 5;
```

---

```js
result = square(x);
```

Function is called.

A new Function Execution Context is created.

---

## Function Execution Context

For:

```js
square(5);
```

Memory phase:

```text
number → undefined
```

Execution phase:

```text
number → 5
```

---

```js
return number * number;
```

Returns:

```js
25
```

Function execution context is removed from memory.

---

## Call Stack

JavaScript uses a Call Stack to manage execution contexts.

Example:

```js
function one() {
    two();
}

function two() {
    three();
}

function three() {
    console.log("Hello");
}

one();
```

---

Execution order:

```text
Global
```

↓

```text
one()
```

↓

```text
two()
```

↓

```text
three()
```

↓

```text
console.log()
```

---

Stack:

```text
| console.log |
| three()     |
| two()       |
| one()       |
| Global      |
```

After execution:

```text
| Global |
```

---

## JavaScript is Single Threaded

JavaScript executes one task at a time.

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

The next statement starts only after the current statement finishes.

---

## Execution Context Lifecycle

For every function call:

### 1. Create Execution Context

```text
Memory Phase
```

↓

### 2. Execute Code

```text
Execution Phase
```

↓

### 3. Return Value

↓

### 4. Remove Context From Stack

---

## Global Execution Context

Every JavaScript program starts with a Global Execution Context.

```js
console.log("Hello");
```

Even this simple code runs inside the Global Execution Context.
