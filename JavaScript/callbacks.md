# Passing Functions to Other Functions and Invoking Them on Demand

## Functions are First-Class Citizens

In JavaScript, functions can be:

- Stored in variables
- Passed as arguments
- Returned from other functions

This allows one function to be passed to another function and executed later.

---

## Passing a Function as an Argument

```js
function greet() {
  console.log("Hello");
}

function execute(fn) {
  fn();
}

execute(greet);
```

Output:

```js
Hello
```

Pass the function itself:

```js
execute(greet);
```

Not:

```js
execute(greet());
```

---

### Passing the Function

```js
execute(greet);
```

- Function is passed
- Function executes later

---

### Calling the Function Immediately

```js
execute(greet());
```

- `greet()` runs immediately
- Its return value is passed

---

## Invoking on Demand

```js
function greet() {
  console.log("Hello");
}

function runLater(callback) {
  console.log("Before");

  callback();

  console.log("After");
}

runLater(greet);
```

Output:

```js
Before
Hello
After
```

The callback executes only when:

```js
callback();
```

is reached.

---

# Why Use Callbacks?

They allow functions to:

- Execute code later
- Customize behavior
- Reuse logic
- Handle asynchronous operations

---
