# JavaScript Coding Best Practices

## 1. Use Consistent Case Style

Choose one naming style and use it everywhere.

Recommended:

```js
camelCase
```

Example:

```js
let userName = "Bruce";
let userAge = 25;

function printDetails() {
}
```

Avoid mixing styles.

Bad:

```js
let userName = "Bruce";
let UserAge = 25;
let user_age = 30;
```

---

## 2. Use Descriptive Variable Names

Variable names should describe the data they hold.

Bad:

```js
const a = [1, 2, 3];
const x = 100;
```

Good:

```js
const numbers = [1, 2, 3];
const totalAmount = 100;
```

---

## 3. Use Descriptive Function Names

Function names should describe what the function does.

Bad:

```js
function calc(n) {
  return n * n;
}
```

Good:

```js
function squareNumber(number) {
  return number * number;
}
```

---

## 4. Use Meaningful Loop Variables

Bad:

```js
for (let i = 0; i < numbers.length; i++) {
}
```

Good:

```js
for (let index = 0; index < numbers.length; index++) {
}
```

---

## 5. Use Meaningful Matrix Loop Variables

Bad:

```js
for (let i = 0; i < matrix.length; i++) {
  for (let j = 0; j < matrix[i].length; j++) {
  }
}
```

Good:

```js
for (let rowIndex = 0; rowIndex < matrix.length; rowIndex++) {
  for (
    let columnIndex = 0;
    columnIndex < matrix[rowIndex].length;
    columnIndex++
  ) {
  }
}
```

---

## 6. Use Proper Indentation

Bad:

```js
function test(){
if(value){
return true;
}
}
```

Good:

```js
function test() {
    if (value) {
        return true;
    }
}
```

VS Code:

```text
Windows/Linux: Ctrl + Shift + I
Mac: Cmd + Shift + I
```

---

## 7. Always Use Curly Braces

Bad:

```js
if (value > 0)
    console.log(value);
```

Good:

```js
if (value > 0) {
    console.log(value);
}
```

---

## 8. Add Spaces Around Operators

Bad:

```js
if(value===10){
}
```

Good:

```js
if (value === 10) {
}
```

---

## 9. Add Spaces After Keywords

Bad:

```js
if(value){
}
```

Good:

```js
if (value) {
}
```

---

## 10. Improve Readability with Blank Lines

Bad:

```js
const fs = require("fs");
const numbers = [1, 2, 3];
const squares = numbers.map((n) => n * n);
console.log(squares);
```

Good:

```js
const fs = require("fs");

const numbers = [1, 2, 3];

const squares = numbers.map((number) => {
    return number * number;
});

console.log(squares);
```

---

## 11. Prefer Explicit Checks

Instead of:

```js
if (!inventory) {
}
```

Prefer:

```js
if (inventory === undefined) {
}
```

When specifically checking for undefined.

---

## 12. Use Strict Equality

Bad:

```js
if (value == 10) {
}
```

Good:

```js
if (value === 10) {
}
```

---

## 13. Format Higher Order Functions Clearly

Bad:

```js
const result = numbers
  .filter(number => number > 5)
  .map(number => number * 2);
```

Preferred style:

```js
const result = numbers
    .filter((number) => {
        return number > 5;
    })
    .map((number) => {
        return number * 2;
    });
```

---

## 14. Use Block Bodies for Callbacks

Bad:

```js
numbers.map((number) => number * 2);
```

Preferred style:

```js
numbers.map((number) => {
    return number * 2;
});
```

---

## 15. Break Long Chains Across Lines

Bad:

```js
const result = arr.filter(...).map(...).reduce(...);
```

Good:

```js
const result = arr
    .filter((item) => {
        return condition;
    })
    .map((item) => {
        return transformedItem;
    })
    .reduce((accumulator, item) => {
        return accumulator + item;
    });
```

---

## 16. Use Explicit Variable Names in Callbacks

Bad:

```js
numbers.map((n) => {
    return n * n;
});
```

Good:

```js
numbers.map((number) => {
    return number * number;
});
```

---

## 17. Keep Consistent Formatting

Bad:

```js
module.exports=problem1;
```

Good:

```js
module.exports = problem1;
```

---

## 18. Separate Declarations and Logic

Good:

```js
const numbers = [1, 2, 3];

const squares = numbers.map((number) => {
    return number * number;
});

console.log(squares);
```

Instead of mixing everything together.

---

## 19. Write Readable Conditions

Bad:

```js
if(!inventory||!id)return[];
```

Good:

```js
if (inventory === undefined || id === undefined) {
    return [];
}
```

---

## 20. Prefer Readability Over Shortness

Bad:

```js
const result = arr.map((n) => n * 2);
```

Preferred LMS style:

```js
const result = arr.map((number) => {
    return number * 2;
});
```

---

## Checklist

- Use consistent naming style
- Use descriptive variable names
- Use descriptive function names
- Use meaningful loop variables
- Indent properly
- Always use `{ }`
- Use spaces around operators
- Use blank lines for readability
- Prefer `===` over `==`
- Prefer explicit checks over ambiguous checks
- Format HOFs across multiple lines
- Use block bodies in callbacks
- Prioritize readability over brevity
- Keep formatting consistent
