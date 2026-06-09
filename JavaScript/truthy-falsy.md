# Truthy and Falsy Values in JavaScript

In JavaScript, every value can behave like either:

```js
true
```

or

```js
false
```

when used in conditions.

Example:

```js
if ("Hello") {
  console.log("Runs");
}
```

Output:

```js
Runs
```

Even though `"Hello"` is not literally `true`.

JavaScript automatically converts it to a boolean when evaluating the condition.

This process is called:

```text
Boolean Coercion
```

---

JavaScript does not require:

```js
if (userCount > 0)
```

Instead, JavaScript lets us write:

```js
if (userCount)
```

---

## The 8 Falsy Values

JavaScript has only **8 falsy values**.

Everything else is truthy.

---

## 1. false

```js
Boolean(false);
```

Output:

```js
false
```

---

## 2. 0

```js
Boolean(0);
```

Output:

```js
false
```

---

## 3. -0

```js
Boolean(-0);
```

Output:

```js
false
```

---

## 4. 0n (BigInt Zero)

```js
Boolean(0n);
```

Output:

```js
false
```

---

## 5. Empty String

```js
Boolean("");
```

Output:

```js
false
```

Also:

```js
''
``
```

are falsy.

---

## 6. null

```js
Boolean(null);
```

Output:

```js
false
```

---

## 7. undefined

```js
Boolean(undefined);
```

Output:

```js
false
```

---

## 8. NaN

```js
Boolean(NaN);
```

Output:

```js
false
```

---

```text
false
0
-0
0n
""
null
undefined
NaN
```

These are the **only falsy values in JavaScript**.

Everything else is truthy.

---

## Truthy Values

### Non-Empty Strings

```js
Boolean(" ");
```

Output:

```js
true
```

A string containing a space is not empty.

---

Even:

```js
Boolean("0");
```

Output:

```js
true
```

Because it is text, not the number zero.

---

### Arrays

Even empty arrays are truthy.

```js
Boolean([]);
```

Output:

```js
true
```

---

### Objects

Even empty objects are truthy.

```js
Boolean({});
```

Output:

```js
true
```

---

# Functions

```js
Boolean(function () {});
```

Output:

```js
true
```
