# Template Literals in JavaScript

Template literals are strings enclosed in backticks (`` ` ``) that support:

- String interpolation
- Multi-line strings
- Embedded expressions

```js
const name = "Bob";

console.log(`Hello ${name}`);
```

Output:

```js
Hello Bob
```

---

## Syntax

```js
`text`
```

Example:

```js
const message = `Hello World`;
```

---

## String Interpolation

```js
const name = "Bob";

const message = `Hello ${name}`;

console.log(message);
```

Output:

```js
Hello Bob
```

---

## Embedded Expressions

Anything inside:

```js
${}
```

is evaluated as JavaScript.

```js
const a = 10;
const b = 20;

console.log(`${a + b}`);
```

Output:

```js
30
```

---

### Function Calls

```js
function greet(name) {
  return `Hello ${name}`;
}

console.log(`${greet("Bob")}`);
```

Output:

```js
Hello Bob
```

---

## Multi-line Strings

```js
const text = `
Line 1
Line 2
Line 3
`;

console.log(text);
```

Output:

```text
Line 1
Line 2
Line 3
```

---

### Using Ternary Operators

```js
const age = 20;

console.log(
  `${age >= 18 ? "Adult" : "Minor"}`
);
```

Output:

```js
Adult
```

---

### Creating Dynamic Strings

```js
const user = "Bob";
const score = 95;

const message = `${user} scored ${score}`;

console.log(message);
```

Output:

```js
Bob scored 95
```

---

### HTML Generation

```js
const name = "Bob";

const html = `
<div>
  <h1>${name}</h1>
</div>
`;

console.log(html);
```

Output:

```html
<div>
  <h1>Bob</h1>
</div>
```

---
