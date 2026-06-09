# What Happens When a Function Does Not Have a Return Statement?

If a function does not have a `return` statement, JavaScript automatically returns `undefined`.

```js
function greet() {
  console.log("Hello");
}

const result = greet();

console.log(result);
```

Output:

```js
Hello
undefined
```

## Explicit vs Implicit

These are same:

```js
function greet() {
}
```

```js
function greet() {
  return undefined;
}
```
