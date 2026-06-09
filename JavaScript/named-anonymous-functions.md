# Differences Between Named Functions and Anonymous Functions

## Named Function

A named function has an identifier.

```js
function greet() {
  console.log("Hello");
}
```

Function name:

```js
greet
```

---

## Anonymous Function

An anonymous function has no name.

```js
function () {
  console.log("Hello");
}
```

Anonymous functions are usually used as callbacks or assigned to variables.

```js
const greet = function () {
  console.log("Hello");
};
```

The function itself is anonymous even though the variable has a name.

---

# Syntax Comparison

### Named Function

```js
function greet() {
  console.log("Hello");
}
```

### Anonymous Function

```js
const greet = function () {
  console.log("Hello");
};
```

---

## Function Declarations Are Usually Named

```js
function add(a, b) {
  return a + b;
}
```

---

## Anonymous Functions Are Common in Callbacks

```js
setTimeout(function () {
  console.log("Hello");
}, 1000);
```

---

## Function Name Property

### Named Function

```js
function greet() {}

console.log(greet.name);
```

Output:

```js
greet
```

---

### Anonymous Function

```js
const greet = function () {};

console.log(greet.name);
```

Output:

```js
greet
```

Modern JavaScript infers the name from the variable.

---
