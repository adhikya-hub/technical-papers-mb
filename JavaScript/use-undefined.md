# Why `value === undefined` is Better Than `!value` (When Checking for Undefined)

## Problem with `!value`

The expression:

```js
!value
```

does not check only for `undefined`.

It checks whether a value is **falsy**.

Example:

```js
const value = 0;

console.log(!value);
```

Output:

```js
true
```

But:

```js
0
```

is a valid value, not `undefined`.

---

### Falsy Values

The following values make:

```js
!value
```

evaluate to `true`.

```js
false
0
-0
0n
""
null
undefined
NaN
```

Example:

```js
console.log(!0);
console.log(!"");
console.log(!false);
console.log(!undefined);
```

Output:

```js
true
true
true
true
```

---

## Using `=== undefined`

If the goal is specifically to check for `undefined`:

```js
value === undefined
```

is more precise.

Example:

```js
const value = 0;

console.log(value === undefined);
```

Output:

```js
false
```

Correctly identifies that the value exists.

---

## Example

```js
function printCount(count) {
  if (!count) {
    console.log("Count not provided");
    return;
  }

  console.log(count);
}

printCount(0);
```

Output:

```js
Count not provided
```

This is incorrect because:

```js
0
```

was provided.

---

Using:

```js
function printCount(count) {
  if (count === undefined) {
    console.log("Count not provided");
    return;
  }

  console.log(count);
}

printCount(0);
```

Output:

```js
0
```

---

## When `!value` Is Appropriate

Use:

```js
!value
```

when any falsy value should be treated as "missing" or "invalid".

Example:

```js
if (!username) {
  console.log("Username required");
}
```

This catches:

```js
""
null
undefined
```

which may be desirable.

---

## When `=== undefined` Is Appropriate

Use:

```js
value === undefined
```

when only `undefined` should be matched.

Example:

```js
if (value === undefined) {
}
```

This does not affect:

```js
0
false
""
null
```

---
