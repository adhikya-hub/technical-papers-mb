# What is Inversion of Control in Callbacks?

Inversion of Control (IoC) occurs when you pass a callback function to another function and hand over control of that callback's execution.

Instead of your code deciding:

- when the callback runs
- how many times it runs
- what arguments it receives

the receiving function decides these things.

---

## Example

```js
function fetchData(callback) {
    // implementation hidden from us

    callback(data);
}

fetchData((data) => {
    console.log(data);
});
```

When you pass:

```js
(data) => {
    console.log(data);
}
```

you no longer control its execution.

The responsibility has been transferred to:

```js
fetchData()
```

When writing:

```js
fetchData(callback);
```

you trust `fetchData()` to:

### Execute the callback

```js
callback();
```

---

### Execute it at the correct time

```js
// after data is available
callback(data);
```

---

### Execute it only once

```js
callback(data);
```

instead of:

```js
callback(data);
callback(data);
callback(data);
```

---

### Pass the correct arguments

```js
callback(userData);
```

instead of:

```js
callback(undefined);
```

---

### Handle errors properly

```js
callback(error, data);
```

---

## "Inversion" of Control

Normally:

```js
step1();
step2();
step3();
```

Your code controls execution.

You decide:

- what runs
- when it runs
- in what order it runs

---

With callbacks:

```js
doSomething(step2);
```

Now:

```js
doSomething()
```

controls when:

```js
step2()
```

runs.

Control has been inverted.

---

### Example

```js
button.addEventListener("click", () => {
    console.log("Clicked");
});
```

You provide the callback:

```js
() => {
    console.log("Clicked");
}
```

The browser decides:

- when a click occurs
- when the callback executes
- how often it executes

---

## How Promises Improve This

With callbacks:

```js
fetchData(callback);
```

`fetchData()` controls callback execution.

---

With Promises:

```js
const promise = fetchData();
```

You receive a Promise object.

Then:

```js
promise.then((data) => {
    console.log(data);
});
```

Promises provide guarantees:

- Resolve only once
- Reject only once
- Preserve execution order
- Cannot be arbitrarily re-triggered by consumer code

Because of these guarantees, Promises reduce the risks associated with callback-based inversion of control.
