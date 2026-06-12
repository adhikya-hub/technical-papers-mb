# What is Callback Hell?

Callback Hell occurs when multiple asynchronous operations are nested inside each other, resulting in deeply indented and difficult-to-read code.

---

## Example

```js
getUser(userId, (user) => {
    getOrders(user.id, (orders) => {
        getPayment(orders[0].id, (payment) => {
            getInvoice(payment.id, (invoice) => {
                console.log(invoice);
            });
        });
    });
});
```

---

## Problems

- Difficult to read
- Difficult to debug
- Difficult to maintain
- Error handling becomes complicated
- Excessive nesting

---

## Why It Happens

Each asynchronous operation depends on the result of the previous operation.

```text
Get User
  ↓
Get Orders
  ↓
Get Payment
  ↓
Get Invoice
```

---

## Solution

Use:

### Promises

```js
getUser(userId)
    .then((user) => getOrders(user.id))
    .then((orders) => getPayment(orders[0].id))
    .then((payment) => getInvoice(payment.id))
    .then((invoice) => {
        console.log(invoice);
    });
```

---

### Async/Await

```js
const user = await getUser(userId);
const orders = await getOrders(user.id);
const payment = await getPayment(orders[0].id);
const invoice = await getInvoice(payment.id);

console.log(invoice);
```

---
