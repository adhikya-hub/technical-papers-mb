# Popular Object Utility Methods

**Objects are mutable in JavaScript.**

---

## Object.keys()

Returns an array of keys.

**Immutable**

```js
const user = {
  name: "Bob",
  age: 25
};

console.log(Object.keys(user));
```

Output:

```js
["name", "age"]
```

---

## Object.values()

Returns an array of values.

**Immutable**

```js
const user = {
  name: "Bob",
  age: 25
};

console.log(Object.values(user));
```

Output:

```js
["Bob", 25]
```

---

## Object.entries()

Returns key-value pairs.

**Immutable**

```js
const user = {
  name: "Bob",
  age: 25
};

console.log(Object.entries(user));
```

Output:

```js
[
  ["name", "Bob"],
  ["age", 25]
]
```

---

## Object.fromEntries()

Converts entries back into an object.

**Immutable**

```js
const entries = [
  ["name", "Bob"],
  ["age", 25]
];

console.log(Object.fromEntries(entries));
```

Output:

```js
{
  name: "Bob",
  age: 25
}
```

---

## Object.assign()

Copies properties.

**Mutable** (mutates target object)

```js
const target = {
  a: 1
};

const source = {
  b: 2
};

Object.assign(target, source);

console.log(target);
```

Output:

```js
{
  a: 1,
  b: 2
}
```

---

### Creating a Copy

```js
const user = {
  name: "Bob"
};

const copy = Object.assign({}, user);

console.log(copy);
```

Output:

```js
{
  name: "Bob"
}
```

---

## Spread Operator (...)

Most common way to copy objects.

**Immutable**

```js
const user = {
  name: "Bob"
};

const copy = {
  ...user
};

console.log(copy);
```

Output:

```js
{
  name: "Bob"
}
```

---

## Merging Objects

**Immutable**

```js
const obj1 = {
  a: 1
};

const obj2 = {
  b: 2
};

const merged = {
  ...obj1,
  ...obj2
};

console.log(merged);
```

Output:

```js
{
  a: 1,
  b: 2
}
```

---

## Object.hasOwn()

Checks if a key exists.

**Immutable**

```js
const user = {
  name: "Bob"
};

console.log(Object.hasOwn(user, "name"));
```

Output:

```js
true
```

---

## hasOwnProperty()

Older alternative.

**Immutable**

```js
const user = {
  name: "Bob"
};

console.log(user.hasOwnProperty("name"));
```

Output:

```js
true
```

---

## Object.freeze()

Prevents modifications.

**Mutable** (changes the object's behavior)

```js
const user = {
  name: "Bob"
};

Object.freeze(user);

user.name = "Alice";

console.log(user);
```

Output:

```js
{
  name: "Bob"
}
```

---

## Object.seal()

Allows updating existing properties but prevents adding/removing properties.

**Mutable**

```js
const user = {
  name: "Bob"
};

Object.seal(user);

user.name = "Alice";

console.log(user);
```

Output:

```js
{
  name: "Alice"
}
```

Cannot do:

```js
user.age = 25;
```

---

## Object Destructuring

Extract values into variables.

**Immutable**

```js
const user = {
  name: "Bob",
  age: 25
};

const { name, age } = user;

console.log(name);
console.log(age);
```

Output:

```js
Bob
25
```

---

| Method | Purpose | Mutable |
|----------|----------|----------|
| Object.keys | Get keys | No |
| Object.values | Get values | No |
| Object.entries | Get key-value pairs | No |
| Object.fromEntries | Entries to Object | No |
| Object.assign | Copy/Merge | Yes (target mutated) |
| Spread (...) | Copy/Merge | No |
| Object.hasOwn | Check key exists | No |
| hasOwnProperty | Check key exists | No |
| Object.freeze | Prevent changes | Yes |
| Object.seal | Restrict structure | Yes |
| Destructuring | Extract values | No |

---
