# Function Hoisting in JavaScript

Function hoisting is JavaScript's behavior of making function declarations available before they appear in the code.

Example:

```js
greet();

function greet() {
  console.log("Hello");
}
```

Output:

```js
Hello
```

Even though the function is called before it is defined.

---

Before executing your code, JavaScript performs a phase called **Creation Phase**.

During this phase, JavaScript scans the code and stores function declarations in memory.


```js
function greet() {
  console.log("Hello");
}

greet();
```

and

```js
greet();

function greet() {
  console.log("Hello");
}
```

behave the same.

---

## Function Declarations Are Fully Hoisted

Example:

```js
sayHi();

function sayHi() {
  console.log("Hi");
}
```

Output:

```js
Hi
```

JavaScript hoists the entire function.

Not just the name.

---

For a function declaration:

```js
function greet() {
  console.log("Hello");
}
```

JavaScript stores:

```js
greet → function object
```

before execution starts.

Therefore the function can be called anywhere in its scope.

---

## Function Expressions Are Different

Example:

```js
sayHi();

const sayHi = function () {
  console.log("Hi");
};
```

Output:

```js
ReferenceError
```

Here:

```js
const sayHi = function () {
  console.log("Hi");
};
```

JavaScript hoists only the variable declaration.

The function value is assigned later during execution.

At the time:

```js
sayHi();
```

runs, the variable hasn't received the function yet.

---

## Using var with Function Expressions

Example:

```js
sayHi();

var sayHi = function () {
  console.log("Hi");
};
```

Output:

```js
TypeError: sayHi is not a function
```

---

# Why TypeError Instead of ReferenceError?

During hoisting:

```js
var sayHi;
```

is created.

So JavaScript sees:

```js
sayHi();
```

as:

```js
undefined();
```

Trying to call `undefined` as a function causes:

```js
TypeError
```

---

# Function Declaration vs Function Expression

## Function Declaration

```js
function greet() {
  console.log("Hello");
}
```

Can be called before definition.

```js
greet();

function greet() {
  console.log("Hello");
}
```

Works.

---

## Function Expression

```js
const greet = function () {
  console.log("Hello");
};
```

Cannot be called before assignment.

```js
greet();

const greet = function () {
  console.log("Hello");
};
```

Throws an error.

---

# Arrow Functions

Arrow functions behave like function expressions.

Example:

```js
sayHi();

const sayHi = () => {
  console.log("Hi");
};
```

Output:

```js
ReferenceError
```

Because arrow functions are assigned to variables.

They are not function declarations.

---

# Summary Table

| Type | Can Be Called Before Definition? |
|--------|--------|
| Function Declaration | Yes |
| Function Expression + var | TypeError |
| Function Expression + let | ReferenceError |
| Function Expression + const | ReferenceError |
| Arrow Function + let/const | ReferenceError |

---
