# let, var, const in JavaScript

`let`, `var`, and `const` are keywords used to **declare variables** in JavaScript.

A variable is simply a container that stores data.

```js
let name = "Bob";
var age = 25;
const country = "India";
```

All three create variables, but they behave differently.

---

# Comparison

| Feature | var | let | const |
|----------|------|------|--------|
| Can Reassign | Yes | Yes | No |
| Can Redeclare | Yes | No | No |
| Block Scoped | No | Yes | Yes |
| Function Scoped | Yes | No | No |
| Hoisted | Yes | Yes | Yes |
| Temporal Dead Zone | No | Yes | Yes |
| Modern Usage | Rarely | Common | Most Common |

---

## var

`var` was the only way to declare variables before ES6 (2015).

Example:

```js
var name = "Bob";
```

---

### Reassignment

Allowed.

```js
var age = 25;

age = 30;

console.log(age);
```

Output:

```js
30
```

---

### Redeclaration

Also allowed.

```js
var age = 25;
var age = 30;

console.log(age);
```

Output:

```js
30
```

This can cause bugs.

---

### Function Scope

`var` is function scoped.

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

The variable exists only inside the function.

---

### var Ignores Block Scope

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

`var` escapes the block.

---

### Problem with var

Consider:

```js
for (var i = 0; i < 3; i++) {
}

console.log(i);
```

Output:

```js
3
```

The loop variable is available outside the loop.

---

## let

`let` was introduced in ES6.

It solves many problems caused by `var`.

Example:

```js
let name = "Bob";
```

---

### Reassignment

Allowed.

```js
let age = 25;

age = 30;

console.log(age);
```

Output:

```js
30
```

---

### Redeclaration

Not allowed.

```js
let age = 25;
let age = 30;
```

Output:

```js
SyntaxError
```

This helps prevent accidental mistakes.

---

# Block Scope

`let` respects block scope.

Example:

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

The variable exists only inside the block.

---

### Loop Example

```js
for (let i = 0; i < 3; i++) {
}

console.log(i);
```

Output:

```js
ReferenceError
```

The loop variable stays inside the loop.

---

## const

`const` was also introduced in ES6.

A `const` variable cannot be reassigned.

Example:

```js
const country = "India";
```

---

### Reassignment

Not allowed.

```js
const country = "India";

country = "USA";
```

Output:

```js
TypeError
```

---

### Declaration and Initialization

`const` must be given a value immediately.

Wrong:

```js
const age;
```

Output:

```js
SyntaxError
```

Correct:

```js
const age = 25;
```

---

### Block Scope

`const` is block scoped.

Example:

```js
if (true) {
  const age = 25;
}

console.log(age);
```

Output:

```js
ReferenceError
```

---

# const doesn't make Objects Immutable

This is a common misconception.

Consider:

```js
const person = {
  name: "Bob"
};
```

This is allowed:

```js
person.name = "Alice";
```

Output:

```js
{ name: "Alice" }
```

Because the object itself is still the same object.

Only the reference is constant.

---

```js
const person = {
  name: "Bob"
};

person = {};
```

Output:

```js
TypeError
```

The variable cannot point to a new object.

---

## Hoisting

All three declarations are hoisted.

---

### var Hoisting

Example:

```js
console.log(name);

var name = "Bob";
```

JavaScript treats it like:

```js
var name;

console.log(name);

name = "Bob";
```

Output:

```js
undefined
```

---

### let Hoisting

Example:

```js
console.log(name);

let name = "Bob";
```

Output:

```js
ReferenceError
```

The variable exists but cannot be accessed yet.

---

### const Hoisting

Example:

```js
console.log(name);

const name = "Bob";
```

Output:

```js
ReferenceError
```

Same behavior as `let`.

---

#### Temporal Dead Zone (TDZ)

The period between start of scope and Variable declaration is called the **Temporal Dead Zone**.

Example:

```js
{
  console.log(age);

  let age = 25;
}
```

Output:

```js
ReferenceError
```

The variable exists but is inaccessible until its declaration line.

---

## When to Use What?

### Use const by Default

```js
const company = "Wayne Enterprises";
```

If the value should not change.

---

### Use let When Value Changes

```js
let score = 0;

score++;
```

For counters, loops, user input, etc.

---

### Avoid var

```js
var score = 0;
```

Modern JavaScript rarely uses `var`.

Most style guides recommend avoiding it.
