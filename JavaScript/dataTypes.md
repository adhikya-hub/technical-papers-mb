# Different Data Types in JavaScript

JavaScript has **8 data types**.

## Primitive Data Types

Primitive values store a single value.

1. String
2. Number
3. Boolean
4. Undefined
5. Null
6. BigInt
7. Symbol

## Non-Primitive Data Type

8. Object

---

### String

A String represents text.

```js
let firstName = "Bruce";
let city = 'Hyderabad';
```

Strings can be created using:

```js
"double quotes"
'single quotes'
`backticks`
```

Example:

```js
let name = "JavaScript";
let intro = `I'm ${name}` //template literal
```

Type:

```js
typeof message;
```

Output:

```js
"string"
```

---

### Number

JavaScript has only one numeric data type: `Number`.

Unlike languages such as Java, JavaScript does not have separate types like:

- int
- float
- double

Examples:

```js
let age = 25;
let price = 99.99;
let temperature = -5;
```

Type:

```js
typeof age;
```

Output:

```js
"number"
```

#### Special Number Values

**Infinity**

```js
10 / 0;
```

Output:

```js
Infinity
```

**NaN**

NaN stands for **Not a Number**.

```js
"hello" * 2;
```

Output:

```js
NaN
```

---

### Boolean

A Boolean can have only two values:

```text
true
false
```

Example:

```js
let isLoggedIn = true;
let isAdmin = false;
```

Type:

```js
typeof true;
```

Output:

```js
"boolean"
```

---

### Undefined

A variable that has been declared but not assigned a value has the value `undefined`.

Example:

```js
let name;
```

JavaScript automatically assigns:

```js
undefined
```

Type:

```js
typeof name;
```

Output:

```js
"undefined"
```

---

# Null

`null` represents an intentional absence of a value.

Example:

```js
let user = null;
```

Meaning:

```text
There is currently no user.
```

---

## Null vs Undefined

### Undefined

```js
let user;
```
No value assigned yet

### Null

```js
let user = null;
```
Intentionally set to empty

---

#### note

```js
typeof null;
```

Output:

```js
"object"
```

This is a historical bug in JavaScript.

Although the result is `"object"`, `null` is not actually an object.

---

### BigInt

BigInt is used for very large integers that exceed the range of the Number type.

Example:

```js
90071992547409911234567890n;
```

There is an `n` at the end.

Type:

```js
typeof 123n;
```

Output:

```js
"bigint"
```

#### Why BigInt

- Large IDs
- Financial calculations
- Scientific computations
- Cryptography

---

### Symbol

A Symbol creates a unique value.

Example:

```js
const id1 = Symbol();
const id2 = Symbol();
```

Comparison:

```js
id1 === id2;
```

Output:

```js
false
```

Even though both were created the same way.

Every Symbol is unique.

#### Why Symbol

Used when creating unique object properties without risking naming conflicts.

---

### Object

Objects store collections of related values.

Example:

```js
const person = {
  name: "Bruce",
  age: 36
};
```

Type:

```js
typeof person;
```

Output:

```js
"object"
```

---

### Arrays Are Objects

Example:

```js
const fruits = ["Apple", "Banana"];
```

Type:

```js
typeof fruits;
```

Output:

```js
"object"
```

Proper array check:

```js
Array.isArray(fruits);
```

Output:

```js
true
```

---

### Functions Are Special Objects

Example:

```js
function greet() {
  console.log("Hello");
}
```

Type:

```js
typeof greet;
```

Output:

```js
"function"
```

Internally, functions are special kinds of objects.

---

### Primitive vs Non-Primitive

#### Primitive Data Types

```text
String
Number
Boolean
Undefined
Null
BigInt
Symbol
```

Characteristics:

- Store a single value
- Immutable
- Copied by value

Example:

```js
let a = 10;
let b = a;

b = 20;

console.log(a);
```

Output:

```js
10
```

---

#### Non-Primitive Data Types

```text
Object
Array
Function
Date
Map
Set
```

Characteristics:

- Store collections of values
- Mutable
- Copied by reference

Example:

```js
let obj1 = { name: "Bruce" };
let obj2 = obj1;

obj2.name = "Clark";

console.log(obj1.name);
```

Output:

```js
"Clark"
```

Both variables reference the same object.

---

# Useful typeof Results

```js
typeof "hello";
```

Output:

```js
"string"
```

```js
typeof 10;
```

Output:

```js
"number"
```

```js
typeof true;
```

Output:

```js
"boolean"
```

```js
typeof undefined;
```

Output:

```js
"undefined"
```

```js
typeof null;
```

Output:

```js
"object"
```

```js
typeof 123n;
```

Output:

```js
"bigint"
```

```js
typeof Symbol();
```

Output:

```js
"symbol"
```

```js
typeof {};
```

Output:

```js
"object"
```

```js
typeof [];
```

Output:

```js
"object"
```

```js
typeof function () {};
```

Output:

```js
"function"
```

---
