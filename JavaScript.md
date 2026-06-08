# JavaScript

1. [different datatypes in JavaScript](#different-datatypes-in-javascript)
2. [scopes in javaScript](#scopes-in-javascript)
3. [let, var, const](#let-var-const)
4. [why we must not use var](#why-we-must-not-use-var)
5. [why using global variables is bad](#why-using-global-variables-is-bad)
6. [truthy and falsy values](#truthy-and-falsy-values)
7. [function hoisting](#function-hoisting)
8. [what happens when a function does not have a return statement](#what-happens-when-a-function-does-not-have-a-return-statement)
9. [different ways of declaring a function](#different-ways-of-declaring-a-function)
10. [pass by reference and pass by value - add codeblocks](#pass-by-reference-and-pass-by-value---add-codeblocks)
11. [different types of for loops - for with numbers, for..in, for..of, forEach, while](#different-types-of-for-loops---for-with-numbers-forin-forof-foreach-while)
12. [searching mdn (mozilla developer network)](#searching-mdn-mozilla-developer-network)

13. [popular array utility methods - add codeblocks and mention mutable/immutable](#popular-array-utility-methods---add-codeblocks-and-mention-mutableimmutable)
   - [13.1 Basics:](#basics)
   - [13.2 Array.pop](#arraypop)
   - [13.3 Array.push](#arraypush)
   - [13.4 Array.concat](#arrayconcat)
   - [13.5 Array.slice](#arrayslice)
   - [13.6 Array.splice](#arraysplice)
   - [13.7 Array.join](#arrayjoin)
   - [13.8 Array.flat](#arrayflat)
   - [13.9 Finding:](#finding)
   - [13.10 Array.find](#arrayfind)
   - [13.11 Array.indexOf](#arrayindexof)
   - [13.12 Array.includes](#arrayincludes)
   - [13.13 Array.findIndex](#arrayfindindex)
   - [13.14 Higher Order Functions:](#higher-order-functions)
   - [13.15 Array.forEach](#arrayforeach)
   - [13.16 Array.filter](#arrayfilter)
   - [13.17 Array.map](#arraymap)
   - [13.18 Array.reduce](#arrayreduce)
   - [13.19 Array.sort](#arraysort)
   - [13.20 Advanced:](#advanced)
   - [13.21 Array methods chaining](#array-methods-chaining)

14. [popular string utility methods - add codeblocks and mention mutable/immutable](#popular-string-utility-methods---add-codeblocks-and-mention-mutableimmutable)

15. [popular object utility methods - add codeblocks and mention mutable/immutable](#popular-object-utility-methods---add-codeblocks-and-mention-mutableimmutable)

16. [when to use forEach, when to use array utility methods like map, filter, reduce](#when-to-use-foreach-when-to-use-array-utility-methods-like-map-filter-reduce)

17. [immutable and mutable methods](#immutable-and-mutable-methods)

18. [error handling (try catch)](#error-handling-try-catch)

19. [throwing errors](#throwing-errors)

20. [difference between throw new Error("Error message here") and throw "Error message here](#difference-between-throw-new-errorerror-message-here-and-throw-error-message-here)

21. [reading error messages and tracing issues from the stack trace when errors happen - practice this daily for 2 weeks with different examples. this is very important](#reading-error-messages-and-tracing-issues-from-the-stack-trace-when-errors-happen---practice-this-daily-for-2-weeks-with-different-examples-this-is-very-important)

22. [importance of catch block](#importance-of-catch-block)

23. [spread operator](#spread-operator)

24. [template literals](#template-literals)

25. [default parameters](#default-parameters)

26. [destructuring](#destructuring)

27. [closures](#closures)

28. [difference between arrow functions and regular functions](#difference-between-arrow-functions-and-regular-functions)

29. [difference between === and ==](#difference-between--and-)

30. [why using value === undefined is better than using !value](#why-using-value--undefined-is-better-than-using-value)

31. [array utility methods chaining](#array-utility-methods-chaining)

32. [difference between null and undefined](#difference-between-null-and-undefined)

33. [importing and exporting modules using require and module.exports](#importing-and-exporting-modules-using-require-and-moduleexports)

34. [the different methods of console such as console.log, console.error, console.info and so on](#the-different-methods-of-console-such-as-consolelog-consoleerror-consoleinfo-and-so-on)

35. [all the best practices mentioned on the LMS - indendation, variable naming, loop variable naming and all the others](#all-the-best-practices-mentioned-on-the-lms---indendation-variable-naming-loop-variable-naming-and-all-the-others)

36. [passing functions to other functions and invoking them on demand](#passing-functions-to-other-functions-and-invoking-them-on-demand)

37. [differences between named functions and anonymous functions](#differences-between-named-functions-and-anonymous-functions)

38. [variable number of arguments passed to functions](#variable-number-of-arguments-passed-to-functions)

39. [debugging strategies](#debugging-strategies)

## Different Data Types in JavaScript

JavaScript has **8 data types**.

### Primitive Data Types

Primitive values store a single value.

1. String
2. Number
3. Boolean
4. Undefined
5. Null
6. BigInt
7. Symbol

### Non-Primitive Data Type

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
