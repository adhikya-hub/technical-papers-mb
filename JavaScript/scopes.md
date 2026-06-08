# Scopes in JavaScript

## What is Scope?

**Scope determines where a variable can be accessed in our code.**

In simple words:

Scope is the **access level** of a variable.

If a variable is inside a scope, it can be used there.

If it's outside that scope, JavaScript cannot find it and throws an error.

---

## Why Do We Need Scope?

If every variable in a program is accessible everywhere, variables will start colliding with each other.

Scope helps:

- Organize code
- Prevent naming conflicts
- Improve readability
- Protect data from accidental modification

---

## Types of Scope in JavaScript

There are mainly three scopes:

1. Global Scope
2. Function Scope
3. Block Scope

---

## Global Scope

A variable declared outside all functions and blocks belongs to the global scope.

Example:

```js
const company = "Mountblue";

function greet() {
  console.log(company);
}

console.log(company);
greet();
```

Output:

```js
Mountblue
Mountblue
```

The variable can be accessed from anywhere.

---

## Global Variables Are Dangerous

Any function can modify it. As applications grow, global variables become difficult to manage.

Avoid creating unnecessary global variables.

---

## Function Scope

Variables declared inside a function are only accessible inside that function.

Example:

```js
function greet() {
  let message = "Hello";
  console.log(message);
}

greet();
```

Output:

```js
Hello
```

But:

```js
console.log(message);
```

Output:

```js
ReferenceError
```

Because `message` exists only inside the function.

---

## Block Scope

A block is anything enclosed by curly braces `{}`.

Examples:

```js
if (true) {
}
```

```js
for (...) {
}
```

```js
while (...) {
}
```

```js
{
}
```

Variables declared using:

```js
let
const
```

are block scoped.

Example:

```js
if (true) {
  let age = 25;
  console.log(age);
}
```

Output:

```js
25
```

Outside the block:

```js
console.log(age);
```

Output:

```js
ReferenceError
```

---

### let and const Respect Block Scope

Example:

```js
{
  let a = 10;
  const b = 20;
}

console.log(a);
console.log(b);
```

Output:

```js
ReferenceError
ReferenceError
```

Both variables are confined to the block.

---

### var Does NOT Respect Block Scope

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

Even though `age` was declared inside the block.

This is one reason to avoid `var`.

---

### var is Function Scoped

Example:

```js
function test() {
  var score = 100;
}

console.log(score);
```

Output:

```js
ReferenceError
```

Because `var` respects function scope.

But:

```js
if (true) {
  var score = 100;
}

console.log(score);
```

Output:

```js
100
```

Because `var` ignores block scope.

---

## Scope Chain

When JavaScript needs a variable, it searches in layers.

Example:

```js
const company = "Mountblue";

function greet() {
  const name = "Bob";

  console.log(company);
}
```

When JavaScript encounters:

```js
console.log(company);
```

it searches:

```text
Current Scope
      ↓
Parent Scope
      ↓
Global Scope
```

Until it finds the variable.

This searching process is called the **Scope Chain**.

---

## Child Scope Can Access Parent Scope

Example:

```js
const company = "Mountblue";

function greet() {
  console.log(company);
}

greet();
```

Output:

```js
Mountblue
```

Children can access parent variables.

---

## Parent Scope Cannot Access Child Scope

Example:

```js
function greet() {
  const name = "Bob";
}

console.log(name);
```

Output:

```js
ReferenceError
```

Parent scopes cannot access child variables.

---


## Nested Scopes

Functions can be nested inside other functions.

Example:

```js
function outer() {
  let outerVar = "outer";

  function inner() {
    let innerVar = "inner";

    console.log(outerVar);
  }

  inner();
}

outer();
```

Output:

```js
outer
```

---

## Shadowing

A variable in an inner scope can hide a variable with the same name from an outer scope.

Example:

```js
let name = "Bob";

function greet() {
  let name = "Alice";

  console.log(name);
}

greet();
```

Output:

```js
Alice
```

The inner variable shadows the outer variable.

---

## Lexical Scope

JavaScript uses lexical scope.

This means:

> Scope is determined by where variables are written in the code.

Example:

```js
const a = 10;

function test() {
  console.log(a);
}

test();
```

Output:

```js
10
```

The function remembers where it was created.

Not where it was called.

---

### var is Function Scoped

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

Many beginners expect an error.

---

### Accidentally Creating Globals

```js
function test() {
  score = 100;
}
```

Without `let`, `const`, or `var`, JavaScript may create a global variable.

Always declare variables properly.
