# Pass by Value and Pass by Reference in JavaScript

JavaScript is technically **pass-by-value**.

However:

- Primitive values behave like **pass-by-value**
- Objects behave like **pass-by-reference** (the reference is passed by value)

```text
Primitives → Pass by Value
Objects → Pass by Reference
```

---

## Pass by Value

When a value is copied, the new variable gets its own independent copy.

Changing one variable does not affect the other.

```js
let a = 10;
let b = a;

b = 20;

console.log(a);
console.log(b);
```

Output:

```js
10
20
```

`a` and `b` are completely independent.

---

## Pass by Value in Function Calls

```js
function increase(num) {
  num = num + 1;
}

let score = 10;

increase(score);

console.log(score);
```

Output:

```js
10
```

The function receives a copy of the value.

Modifying the parameter does not affect the original variable.

---

## Pass by Reference

Objects are stored in memory and variables hold references to them.

When assigning one object to another variable, both variables point to the same object.

```js
const person1 = {
  name: "Bob"
};

const person2 = person1;

person2.name = "Alice";

console.log(person1.name);
console.log(person2.name);
```

Output:

```js
Alice
Alice
```

Both variables refer to the same object.

---

## Arrays

```js
const arr1 = [1, 2, 3];
const arr2 = arr1;

arr2.push(4);

console.log(arr1);
console.log(arr2);
```

Output:

```js
[1, 2, 3, 4]
[1, 2, 3, 4]
```

Both variables point to the same array.

---

## Objects in Function Calls

```js
function changeName(person) {
  person.name = "Alice";
}

const user = {
  name: "Bob"
};

changeName(user);

console.log(user.name);
```

Output:

```js
Alice
```

The function modifies the same object.

---

## Reassigning Is Different

```js
function changePerson(person) {
  person = {
    name: "Alice"
  };
}

const user = {
  name: "Bob"
};

changePerson(user);

console.log(user.name);
```

Output:

```js
Bob
```

Because the function parameter received a copy of the reference.

Reassigning the parameter does not change the original variable.

---

## Array Copy

```js
const arr1 = [1, 2, 3];
const arr2 = [...arr1];

arr2.push(4);

console.log(arr1);
console.log(arr2);
```

Output:

```js
[1, 2, 3]
[1, 2, 3, 4]
```

---

## Object Copy

```js
const user1 = {
  name: "Bob"
};

const user2 = {
  ...user1
};

user2.name = "Alice";

console.log(user1.name);
console.log(user2.name);
```

Output:

```js
Bob
Alice
```

---

## Comparison

| Feature | Pass by Value | Pass by Reference |
|----------|----------|----------|
| Used By | Primitives | Objects, Arrays, Functions |
| Copy Created | Yes | No |
| Changes Affect Original | No | Yes |
| Independent Variables | Yes | No |

---
