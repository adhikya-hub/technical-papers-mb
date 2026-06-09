# Variable Number of Arguments Passed to Functions

Sometimes a function should accept any number of arguments.

Examples:

```js
sum(1, 2);
sum(1, 2, 3);
sum(1, 2, 3, 4, 5);
```

---

## Rest Parameters 

The modern way is using the rest operator.

```js
function sum(...numbers) {
  console.log(numbers);
}

sum(1, 2, 3, 4);
```

Output:

```js
[1, 2, 3, 4]
```

All arguments are collected into an array.

---

## Rest Parameter Must Be Last

Valid:

```js
function greet(name, ...messages) {
}
```

Invalid:

```js
function greet(...messages, name) {
}
```

---

## Mixing Normal and Rest Parameters

```js
function greet(name, ...messages) {
  console.log(name);
  console.log(messages);
}

greet("Bruce", "Hi", "Welcome");
```

Output:

```js
Bruce
["Hi", "Welcome"]
```

---

## Older Method: arguments Object

Regular functions have an `arguments` object.

```js
function show() {
  console.log(arguments);
}

show(1, 2, 3);
```

Output:

```js
[Arguments] { 0: 1, 1: 2, 2: 3 }
```
