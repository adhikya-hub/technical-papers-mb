# Difference Between `==` and `===` in JavaScript

JavaScript provides two equality operators:

```js
==
```

Loose Equality

and

```js
===
```

Strict Equality

---

# `===` (Strict Equality)

Checks:

1. Value
2. Data Type

Both must match.

```js
console.log(5 === 5);
```

Output:

```js
true
```

---

```js
console.log(5 === "5");
```

Output:

```js
false
```

Because:

```js
5      // Number
"5"    // String
```

have different types.

---

# `==` (Loose Equality)

Checks values after performing type conversion if necessary.

```js
console.log(5 == "5");
```

Output:

```js
true
```

JavaScript converts:

```js
"5"
```

to:

```js
5
```

before comparison.

---

## null and undefined

```js
console.log(null == undefined);
```

Output:

```js
true
```

---

```js
console.log(null === undefined);
```

Output:

```js
false
```

Different types.

---

# Objects

```js
const obj1 = {};
const obj2 = {};

console.log(obj1 === obj2);
```

Output:

```js
false
```

Each object has a different reference.

---

```js
const obj1 = {};
const obj2 = obj1;

console.log(obj1 === obj2);
```

Output:

```js
true
```

Both variables reference the same object.

---
