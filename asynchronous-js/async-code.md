# Ways to Make Code Asynchronous in JavaScript

JavaScript becomes asynchronous when it uses APIs that perform work outside the main call stack and execute code later.

Common ways:

1. Callbacks
2. Timers (`setTimeout`, `setInterval`)
3. Event Listeners
4. Promises
5. Async/Await

---

## 1. Callbacks

A callback is a function passed to another function and executed later.

```js
setTimeout(() => {
    console.log("Done");
}, 1000);
```

Output after 1 second:

```js
Done
```

The callback runs asynchronously.

---

## 2. setTimeout()

Executes a function after a specified delay.

```js
console.log("Start");

setTimeout(() => {
    console.log("Timer");
}, 2000);

console.log("End");
```

Output:

```js
Start
End
Timer
```

---

## 3. setInterval()

Executes a function repeatedly after a specified interval.

```js
setInterval(() => {
    console.log("Running");
}, 1000);
```

Output:

```js
Running
Running
Running
...
```

---

## 4. Event Listeners

The callback executes when the event occurs.

```js
button.addEventListener("click", () => {
    console.log("Clicked");
});
```

The function runs only when the button is clicked.

---

## 5. Promises

A Promise represents a value that will be available in the future.

```js
fetch("/users")
    .then((response) => {
        console.log(response);
    });
```

The callback inside `.then()` executes when the Promise resolves.

---

## 6. Async/Await

A cleaner way to work with Promises.

```js
async function getUsers() {
    const response = await fetch("/users");

    console.log(response);
}
```

`await` pauses only the async function, not the entire JavaScript program.

---

### Example

```js
console.log("Start");

fetch("/users")
    .then(() => {
        console.log("Data Received");
    });

console.log("End");
```

Output:

```js
Start
End
Data Received
```

---

### Common Async Browser APIs

```js
setTimeout()
```

```js
setInterval()
```

```js
fetch()
```

```js
addEventListener()
```

---

### Common Async Node.js APIs

```js
fs.readFile()
```

```js
http.request()
```

```js
database queries
```
