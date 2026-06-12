# What are Web Browser APIs?

Web Browser APIs are functionalities provided by the browser that JavaScript can use.

They are not part of the JavaScript language.

Examples:

```js
setTimeout()
```

```js
fetch()
```

```js
document.querySelector()
```

```js
localStorage
```

```js
addEventListener()
```

These APIs are provided by the browser environment.

---

The browser provides:

```js
DOM API
Fetch API
Timers API
Storage API
Geolocation API
```

JavaScript alone cannot:

- Access the DOM
- Make HTTP requests
- Set timers
- Read browser storage
- Handle user events

The browser exposes APIs for these tasks.

---

## DOM API

Used to interact with HTML.

```js
const button = document.querySelector("button");
```

```js
button.textContent = "Click Me";
```

Examples:

```js
document.getElementById()
```

```js
document.querySelector()
```

```js
document.createElement()
```

---

## Timer APIs

Used to schedule code execution.

```js
setTimeout(() => {
    console.log("Hello");
}, 1000);
```

---

```js
setInterval(() => {
    console.log("Running");
}, 1000);
```

---

## Fetch API

Used to make HTTP requests.

```js
fetch("/users")
    .then((response) => {
        console.log(response);
    });
```

---

## Event API

Used to respond to user actions.

```js
button.addEventListener("click", () => {
    console.log("Clicked");
});
```

Events include:

```js
click
input
submit
keydown
mouseover
```

---

## Storage API

Used to store data in the browser.

```js
localStorage.setItem("name", "Bruce");
```

```js
const name = localStorage.getItem("name");
```

---

## Geolocation API

Used to access location information.

```js
navigator.geolocation.getCurrentPosition(
    (position) => {
        console.log(position);
    }
);
```

---

## Console API

Used for debugging.

```js
console.log("Hello");
```

```js
console.error("Error");
```

```js
console.table(data);
```

---

## How Async Browser APIs Work

Example:

```js
console.log("Start");

setTimeout(() => {
    console.log("Timer");
}, 1000);

console.log("End");
```

Output:

```js
Start
End
Timer
```

1. JavaScript calls `setTimeout()`
2. Browser handles the timer
3. JavaScript continues execution
4. Browser notifies JavaScript when the timer completes
5. Callback executes

This is one of the main reasons JavaScript can perform asynchronous operations.

---

## Common Browser APIs

| API | Purpose |
|-------|---------|
| DOM API | Manipulate HTML |
| Event API | Handle user events |
| Fetch API | HTTP requests |
| Timer API | Delayed execution |
| Storage API | Store data |
| Geolocation API | User location |
| Console API | Debugging |

---

## Node.js APIs

```js
fs
http
path
process
```
