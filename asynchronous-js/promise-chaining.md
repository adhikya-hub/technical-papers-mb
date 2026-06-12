# Promise Chaining

Promise chaining is the process of connecting multiple asynchronous operations using `.then()`.

The value returned from one `.then()` becomes the input to the next `.then()`.

---

## Example

```js
Promise.resolve(5)
    .then((value) => {
        return value * 2;
    })
    .then((value) => {
        return value + 10;
    })
    .then((value) => {
        console.log(value);
    });
```

Output:

```js
20
```

---

## Error Handling with .catch()

A `.catch()` handles any rejection or error that occurs earlier in the chain.

```js
Promise.reject("Something went wrong")
    .catch((error) => {
        console.log(error);
    });
```

Output:

```js
Something went wrong
```

---

## Error Thrown Inside .then()

```js
Promise.resolve()
    .then(() => {
        throw new Error("Failed");
    })
    .catch((error) => {
        console.log(error.message);
    });
```

Output:

```js
Failed
```

When an error is thrown inside `.then()`, the Promise becomes rejected and control moves to the nearest `.catch()`.

---

## Error Thrown Without .catch()

```js
Promise.resolve()
    .then(() => {
        throw new Error("Failed");
    });
```

Output:

```text
Unhandled Promise Rejection
```

The rejection remains unhandled.

---

## finally()

`finally()` executes whether the Promise succeeds or fails.

```js
Promise.resolve("Success")
    .finally(() => {
        console.log("Cleanup");
    });
```

Output:

```js
Cleanup
```

---

```js
Promise.reject("Error")
    .finally(() => {
        console.log("Cleanup");
    });
```

Output:

```js
Cleanup
```

Common use:

```js
hideLoader();
closeConnection();
clearTimer();
```

---

## Why Should .catch() Be Near the End?

```js
fetchData()
    .then(step1)
    .then(step2)
    .then(step3)
    .catch(handleError);
```

This single `.catch()` can handle:

- Promise rejections
- Errors in `step1`
- Errors in `step2`
- Errors in `step3`

If `.catch()` is placed too early:

```js
fetchData()
    .catch(handleError)
    .then(step1)
    .then(step2);
```

Errors occurring later may not be handled.

---

## Consuming Multiple Promises by Chaining

Sequential execution.

```js
getUser()
    .then((user) => {
        return getOrders(user.id);
    })
    .then((orders) => {
        return getPayment(orders[0].id);
    })
    .then((payment) => {
        console.log(payment);
    });
```

Each Promise starts after the previous one completes.

---

## Consuming Multiple Promises with Promise.all()

Parallel execution.

```js
Promise.all([
    fetchUsers(),
    fetchProducts(),
    fetchOrders()
])
.then((results) => {
    console.log(results);
});
```

All Promises start immediately.

---

## Error Handling with Promises

Use `.catch()`.

```js
fetchData()
    .then(processData)
    .catch((error) => {
        console.error(error);
    });
```

---

## Why Is Error Handling Important?

Without error handling:

```js
Promise.reject("Failed");
```

Output:

```text
Unhandled Promise Rejection
```

Problems:

- Application failures
- Unexpected behavior
- Difficult debugging

Every Promise chain should have error handling.

---

## Promisifying Callback-Based Functions

## Example: setTimeout

Callback version:

```js
setTimeout(() => {
    console.log("Done");
}, 1000);
```

Promisified:

```js
function delay(ms) {
    return new Promise((resolve) => {
        setTimeout(resolve, ms);
    });
}
```

Usage:

```js
delay(1000).then(() => {
    console.log("Done");
});
```

---

## Example: fs.readFile

Callback version:

```js
fs.readFile("file.txt", (error, data) => {
});
```

Promisified:

```js
function readFile(fileName) {
    return new Promise((resolve, reject) => {
        fs.readFile(fileName, (error, data) => {
            if (error) {
                reject(error);
            } else {
                resolve(data);
            }
        });
    });
}
```

---

## Promise.resolve()

Creates an already fulfilled Promise.

```js
Promise.resolve("Hello")
    .then((value) => {
        console.log(value);
    });
```

Output:

```js
Hello
```

---

## Promise.reject()

Creates an already rejected Promise.

```js
Promise.reject("Failed")
    .catch((error) => {
        console.log(error);
    });
```

Output:

```js
Failed
```

---

## Promise.all()

Waits for all Promises to fulfill.

```js
Promise.all([
    Promise.resolve(1),
    Promise.resolve(2),
    Promise.resolve(3)
])
.then((values) => {
    console.log(values);
});
```

Output:

```js
[1, 2, 3]
```

If any Promise rejects:

```js
Promise.all()
```

rejects immediately.

---

## Promise.allSettled()

Waits for all Promises to settle.

```js
Promise.allSettled([
    Promise.resolve("Success"),
    Promise.reject("Error")
])
.then((results) => {
    console.log(results);
});
```

Output:

```js
[
  { status: "fulfilled", value: "Success" },
  { status: "rejected", reason: "Error" }
]
```

---

## Promise.any()

Returns the first fulfilled Promise.

```js
Promise.any([
    Promise.reject("A"),
    Promise.resolve("B"),
    Promise.resolve("C")
])
.then((value) => {
    console.log(value);
});
```

Output:

```js
B
```

Rejects only if all Promises reject.

---

## Promise.race()

Returns the first settled Promise.

```js
Promise.race([
    Promise.resolve("Success"),
    Promise.reject("Error")
])
.then((value) => {
    console.log(value);
});
```

Output depends on which Promise settles first.

Could be:

```js
Success
```

or rejection.

---

| Method | Returns |
|----------|----------|
| Promise.resolve | Fulfilled Promise |
| Promise.reject | Rejected Promise |
| Promise.all | All fulfilled results |
| Promise.allSettled | All results with status |
| Promise.any | First fulfilled result |
| Promise.race | First settled result |

---
