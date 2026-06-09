# Difference Between throw and throw new Error()

```js
throw new Error("Error message here");
```

and

```js
throw "Error message here";
```

Both throw an error, but:

```js
throw new Error(...)
```

is the correct and recommended approach.

---

## throw "Error message here"

Throws a plain string.

```js
try {
  throw "Something went wrong";
} catch (error) {
  console.log(error);
}
```

Output:

```js
Something went wrong
```

Type:

```js
console.log(typeof error);
```

Output:

```js
string
```

---

## throw new Error("Error message here")

Throws an Error object.

```js
try {
  throw new Error("Something went wrong");
} catch (error) {
  console.log(error);
}
```

Output:

```js
Error: Something went wrong
```

Type:

```js
console.log(typeof error);
```

Output:

```js
object
```

---

## Extra Information Available

With `Error` objects:

```js
try {
  throw new Error("Something went wrong");
} catch (error) {
  console.log(error.name);
  console.log(error.message);
}
```

Output:

```js
Error
Something went wrong
```

---

## Stack Trace

```js
try {
  throw new Error("Something went wrong");
} catch (error) {
  console.log(error.stack);
}
```

Output:

```js
Error: Something went wrong
    at ...
    at ...
```

The stack trace shows where the error occurred.

You do not get this with:

```js
throw "Something went wrong";
```

---

## Problem with Throwing Strings

```js
try {
  throw "Something went wrong";
} catch (error) {
  console.log(error.message);
}
```

Output:

```js
undefined
```

Because strings do not have a `message` property.

---
