# Important Ways of Declaring Functions in JavaScript

## 1. Function Declaration

```js
function greet() {
  console.log("Hello");
}
```

Usage:

```js
greet();
```

**Fully hoisted** — can be called before its definition.

---

## 2. Function Expression

```js
const greet = function () {
  console.log("Hello");
};
```

Usage:

```js
greet();
```

**Not fully hoisted** — cannot be called before assignment.

---

## 3. Arrow Function

```js
const greet = () => {
  console.log("Hello");
};
```

Usage:

```js
greet();
```

Shorter syntax introduced in ES6.

---

## 4. Arrow Function (Implicit Return)

```js
const add = (a, b) => a + b;
```

Equivalent to:

```js
const add = (a, b) => {
  return a + b;
};
```

---

## 5. Object Method

```js
const user = {
  greet() {
    console.log("Hello");
  }
};
```

Usage:

```js
user.greet();
```

Used when functions belong to objects.
