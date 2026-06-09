# Different Types of Loops in JavaScript

## 1. for Loop

Used when you know how many times you want to loop.

```js
for (let i = 0; i < 5; i++) {
  console.log(i);
}
```

Output:

```js
0
1
2
3
4
```

- Access index
- Can use `break` and `continue`

---

## 2. while Loop

Used when the number of iterations is not known beforehand.

```js
let i = 0;

while (i < 5) {
  console.log(i);
  i++;
}
```

Output:

```js
0
1
2
3
4
```

---

## 3. for...of Loop

Used to iterate over iterable values such as:

- Arrays
- Strings
- Sets
- Maps

```js
const fruits = ["Apple", "Banana", "Mango"];

for (const fruit of fruits) {
  console.log(fruit);
}
```

Output:

```js
Apple
Banana
Mango
```

---

## 4. for...in Loop

Used to iterate over object keys.

```js
const user = {
  name: "Bruce",
  age: 25
};

for (const key in user) {
  console.log(key);
}
```

Output:

```js
name
age
```

Getting values:

```js
for (const key in user) {
  console.log(user[key]);
}
```

Output:

```js
Bruce
25
```

---

## 5. forEach()

Array method used to run a callback for every element.

```js
const fruits = ["Apple", "Banana", "Mango"];

fruits.forEach((fruit) => {
  console.log(fruit);
});
```

Output:

```js
Apple
Banana
Mango
```

### Parameters

```js
array.forEach((value, index, array) => {
});
```

Example:

```js
const fruits = ["Apple", "Banana"];

fruits.forEach((fruit, index) => {
  console.log(index, fruit);
});
```

Output:

```js
0 Apple
1 Banana
```

---

- `for` → Use when you need index/control.
- `while` → Use when iterations are unknown.
- `for...of` → Iterate over values.
- `for...in` → Iterate over object keys.
- `forEach()` → Array iteration with callbacks.
