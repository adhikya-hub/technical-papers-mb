# Closures in JavaScript

A closure is created when a function remembers and can access variables from its outer scope even after the outer function has finished executing.

---

## Example

```js
function outer() {
  const message = "Hello";

  function inner() {
    console.log(message);
  }

  return inner;
}

const greet = outer();

greet();
```

Output:

```js
Hello
```

- `outer()` executes.
- `inner()` is returned.
- Normally, local variables inside `outer()` would disappear after execution.

However:

```js
message
```

is still available when:

```js
greet();
```

is called.

This is because `inner()` forms a closure over the variables it uses from its outer scope.

---

### Private Variables

Closures are commonly used to create private state.

```js
function createCounter() {
  let count = 0;

  return function () {
    count++;
    return count;
  };
}

const counter = createCounter();

console.log(counter());
console.log(counter());
console.log(counter());
```

Output:

```js
1
2
3
```

`count` belongs to the closure.

The returned function keeps a reference to it.

```js
counter()
```

continues to access the same `count` variable.

---

### Closure with Parameters

```js
function multiplyBy(multiplier) {
  return function (number) {
    return number * multiplier;
  };
}

const double = multiplyBy(2);

console.log(double(5));
```

Output:

```js
10
```

The returned function remembers:

```js
multiplier = 2
```

---

### Closures and Callbacks

```js
function greet(name) {
  return function () {
    console.log(`Hello ${name}`);
  };
}

const sayHello = greet("Bob");

sayHello();
```

Output:

```js
Hello Bob
```

The callback remembers `name`.

---
