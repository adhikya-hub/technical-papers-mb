# Difference Between `null` and `undefined`

Both `null` and `undefined` represent the absence of a value, but they are used in different situations.

---

## `undefined`

`undefined` means a value has not been assigned.

```js
let name;

console.log(name);
```

Output:

```js
undefined
```

---

## Function Without Return

```js
function greet() {}

console.log(greet());
```

Output:

```js
undefined
```

---

## Missing Object Property

```js
const user = {
  name: "Bruce"
};

console.log(user.age);
```

Output:

```js
undefined
```

---

## Missing Function Argument

```js
function greet(name) {
  console.log(name);
}

greet();
```

Output:

```js
undefined
```

---

## `null`

`null` is an intentional assignment that represents "no value".

```js
const user = null;

console.log(user);
```

Output:

```js
null
```

---

## Example

```js
let selectedUser = null;
```

This means:

```text
A value is expected here later,
but currently there is no value.
```

---

## Type Comparison

```js
console.log(typeof undefined);
```

Output:

```js
"undefined"
```

---

```js
console.log(typeof null);
```

Output:

```js
"object"
```

This is a historical JavaScript bug that remains for compatibility.

---

## Equality Comparison

```js
console.log(null == undefined);
```

Output:

```js
true
```

Loose equality treats them as equal.

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

## undefined

Usually produced automatically by JavaScript.

```js
let value;
```

```js
obj.missingProperty;
```

```js
function test() {}
```

---

## null

Usually assigned explicitly by developers.

```js
let user = null;
```

```js
let selectedFile = null;
```

---
