# Popular String Utility Methods

**Strings are immutable in JavaScript.**

Once a string is created, it cannot be changed.

```js
let str = "hello";

str[0] = "H";

console.log(str);
```

Output:

```js
hello
```

The string remains unchanged.

---

## Important Note

All string methods return a **new string**.

They do **not** modify the original string.

---

## Searching

### String.includes()

Checks if a string contains another string.

```js
const str = "JavaScript";

console.log(str.includes("Script"));
```

Output:

```js
true
```

---

### String.indexOf()

Returns the position of the first occurrence.

```js
const str = "JavaScript";

console.log(str.indexOf("Script"));
```

Output:

```js
4
```

Not found:

```js
-1
```

---

### String.startsWith()

Checks beginning of string.

```js
const str = "JavaScript";

console.log(str.startsWith("Java"));
```

Output:

```js
true
```

---

### String.endsWith()

Checks end of string.

```js
const str = "JavaScript";

console.log(str.endsWith("Script"));
```

Output:

```js
true
```

---

## Extracting

### String.slice()

Extracts part of a string.

```js
const str = "JavaScript";

console.log(str.slice(0, 4));
```

Output:

```js
Java
```

---

### String.substring()

Similar to slice.

```js
const str = "JavaScript";

console.log(str.substring(0, 4));
```

Output:

```js
Java
```

---

## Transforming

### String.toUpperCase()

Converts to uppercase.

```js
const str = "hello";

console.log(str.toUpperCase());
```

Output:

```js
HELLO
```

---

### String.toLowerCase()

Converts to lowercase.

```js
const str = "HELLO";

console.log(str.toLowerCase());
```

Output:

```js
hello
```

---

### String.trim()

Removes spaces from both ends.

```js
const str = "   hello   ";

console.log(str.trim());
```

Output:

```js
hello
```

---

### String.trimStart()

Removes leading spaces.

```js
const str = "   hello";

console.log(str.trimStart());
```

Output:

```js
hello
```

---

### String.trimEnd()

Removes trailing spaces.


```js
const str = "hello   ";

console.log(str.trimEnd());
```

Output:

```js
hello
```

---

## Replacing

### String.replace()

Replaces first match.

```js
const str = "I like Java";

console.log(str.replace("Java", "JavaScript"));
```

Output:

```js
I like JavaScript
```

---

### String.replaceAll()

Replaces all matches.

```js
const str = "cat cat cat";

console.log(str.replaceAll("cat", "dog"));
```

Output:

```js
dog dog dog
```

---

## Splitting and Joining

### String.split()

Converts string into array.

```js
const str = "A,B,C";

console.log(str.split(","));
```

Output:

```js
["A", "B", "C"]
```

---

### Array.join()

Often used with split.

```js
const str = "A-B-C";

const result = str.split("-").join(" ");

console.log(result);
```

Output:

```js
A B C
```

---

## Character Access

### String.charAt()

Returns character at index.

```js
const str = "Java";

console.log(str.charAt(1));
```

Output:

```js
a
```

---

### Bracket Notation

```js
const str = "Java";

console.log(str[1]);
```

Output:

```js
a
```

---

## Repeating

### String.repeat()

Repeats a string.

```js
console.log("Hi ".repeat(3));
```

Output:

```js
Hi Hi Hi
```

---

## Method Chaining

```js
const str = "  hello world  ";

const result = str
  .trim()
  .toUpperCase()
  .replace("WORLD", "JS");

console.log(result);
```

Output:

```js
HELLO JS
```

---

| Method | Purpose | Mutable |
|----------|----------|----------|
| includes | Check existence | No |
| indexOf | Find position | No |
| startsWith | Check beginning | No |
| endsWith | Check ending | No |
| slice | Extract portion | No |
| substring | Extract portion | No |
| toUpperCase | Uppercase | No |
| toLowerCase | Lowercase | No |
| trim | Remove spaces | No |
| trimStart | Remove leading spaces | No |
| trimEnd | Remove trailing spaces | No |
| replace | Replace first match | No |
| replaceAll | Replace all matches | No |
| split | String to Array | No |
| charAt | Character access | No |
| repeat | Repeat string | No |
| padStart | Add at beginning | No |
| padEnd | Add at end | No |

---
