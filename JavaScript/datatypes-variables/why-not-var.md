# Why We Must Not Use `var` in JavaScript

Modern JavaScript developers avoid `var` because it can create confusing bugs and unpredictable behavior.

Instead, we use:

```js
const
```

or

```js
let
```

which are safer and easier to understand.

---

Before 2015 (ES6), JavaScript only had:

```js
var
```

In 2015, JavaScript introduced:

```js
let
const
```

to fix many problems caused by `var`.

Most modern codebases avoid `var`.

---

## The Biggest Problem: No Block Scope

Most programmers expect variables inside a block to stay inside that block.

Example:

```js
if (true) {
  var age = 25;
}

console.log(age);
```

Output:

```js
25
```

expected:

```js
ReferenceError
```

But `var` ignores block scope.

---

## This is Dangerous

Imagine an application.

```js
if (userLoggedIn) {
  var token = "abc123";
}
```

Later:

```js
console.log(token);
```

The variable still exists.

A developer may accidentally use or overwrite it.

This can create bugs that are difficult to find.

---

## let Fixes This Problem

```js
if (true) {
  let age = 25;
}

console.log(age);
```

Output:

```js
ReferenceError
```

The variable stays inside the block.

---

# Redeclaration Causes Bugs

`var` allows redeclaration.

Example:

```js
var username = "Bruce";

var username = "Clark";

console.log(username);
```

Output:

```js
Clark
```

No error.

JavaScript silently replaces the old value.

---

## Why Is This Dangerous?

Suppose two developers work on the same file.

Developer 1:

```js
var config = {
  apiUrl: "production"
};
```

Developer 2:

```js
var config = {
  apiUrl: "localhost"
};
```

The second declaration overwrites the first one.

No warning.

No error.

Just unexpected behavior.

---

## let and const Prevent Redeclaration

```js
let username = "Bruce";

let username = "Clark";
```

Output:

```js
SyntaxError
```

JavaScript immediately warns you.

This helps catch bugs early.

---

## Hoisting Creates Confusion

Consider:

```js
console.log(name);

var name = "Bruce";
```

Output:

```js
undefined
```

Many beginners are surprised.

---

## What Actually Happens?

JavaScript internally does something similar to:

```js
var name;

console.log(name);

name = "Bruce";
```

This behavior is called **hoisting**.

---

## Why Is This Confusing?

When reading the code, it looks like:

```js
console.log(name);
```

runs before:

```js
var name = "Bruce";
```

Yet it doesn't throw an error.

This makes code harder to reason about.

---

## let and const Are Safer

```js
console.log(name);

let name = "Bruce";
```

Output:

```js
ReferenceError
```

JavaScript immediately tells you:

> You are trying to use a variable before declaring it.

This catches mistakes early.

---

## Bugs in Loops with Closures

One of the most famous `var` problems.

Example:

```js
for (var i = 0; i < 3; i++) {
  setTimeout(() => {
    console.log(i);
  }, 1000);
}
```

Output:

```js
3
3
3
```

Most people expect:

```js
0
1
2
```

---

## Why Does This Happen?

There is only **one** `i`.

Every callback shares the same variable.

By the time the callbacks run:

```js
i === 3
```

So every callback prints:

```js
3
```

---

## let Fixes It

```js
for (let i = 0; i < 3; i++) {
  setTimeout(() => {
    console.log(i);
  }, 1000);
}
```

Output:

```js
0
1
2
```

Each iteration gets its own variable.

Much more intuitive.

---

## Accidental Global Variables

Old JavaScript code often mixed poorly with `var`.

Example:

```js
function test() {
  score = 100;
}
```

Without proper declarations, variables could accidentally become global.

This caused countless bugs.

Modern JavaScript encourages stricter practices using:

```js
let
const
```

and strict mode.

---

## Function Scope Is Less Intuitive

`var` is function scoped.

Example:

```js
function test() {
  if (true) {
    var age = 25;
  }

  console.log(age);
}
```

Output:

```js
25
```

Many developers expect:

```js
ReferenceError
```

because the variable is inside an `if` block.

---

Most modern projects follow:

```text
const → First choice

let → If value changes

var → Avoid
```
