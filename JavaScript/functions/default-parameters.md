# Default Parameters in JavaScript

Default parameters allow a function parameter to have a default value when no argument is provided.

```js
function greet(name = "Guest") {
  console.log(`Hello ${name}`);
}

greet();
```

Output:

```js
Hello Guest
```

---

## Providing an Argument

If an argument is passed, the default value is ignored.

```js
function greet(name = "Guest") {
  console.log(name);
}

greet("Bob");
```

Output:

```js
Bob
```

---

## Partial Arguments

```js
function createUser(name = "Guest", age = 18) {
  console.log(name, age);
}

createUser("Bob");//only one argumnet passed
```

Output:

```js
Bob 18
```

---

## Default Parameters with Expressions

```js
function calculate(price, tax = price * 0.18) {
  return price + tax;
}

console.log(calculate(100));
```

Output:

```js
118
```

---

## Using Functions as Defaults

```js
function getDefaultName() {
  return "Guest";
}

function greet(name = getDefaultName()) {
  console.log(name);
}

greet();
```

Output:

```js
Guest
```

---

## undefined Triggers Default Values

```js
function greet(name = "Guest") {
  console.log(name);
}

greet(undefined);
```

Output:

```js
Guest
```

---

## null Does Not Trigger Default Values (or any other falsy value)

```js
function greet(name = "Guest") {
  console.log(name);
}

greet(null);
```

Output:

```js
null
```

Default parameters are only used when the argument is:

```js
undefined
```

---
