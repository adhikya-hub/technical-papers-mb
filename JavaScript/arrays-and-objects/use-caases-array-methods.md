# When to Use forEach, map, filter, and reduce

| Method | Use When |
|----------|----------|
| forEach | Perform an action for every element |
| map | Transform each element into something else |
| filter | Keep only elements that match a condition |
| reduce | Combine all elements into a single value |

---

## 1. forEach()

Use when you want to perform side effects.

Examples:

- Logging
- Updating DOM
- Calling APIs
- Writing to files
- Mutating another variable

```js
const nums = [1, 2, 3];

nums.forEach(num => {
  console.log(num);
});
```

Output:

```js
1
2
3
```

### Returns

```js
undefined
```

---

## 2. map()

Use when you want a new array with transformed values.

```js
const nums = [1, 2, 3];

const doubled = nums.map(num => num * 2);

console.log(doubled);
```

Output:

```js
[2, 4, 6]
```

Examples:

```js
users.map(user => user.name)
```

```js
prices.map(price => price * 1.18)
```

```js
numbers.map(num => num.toString())
```

### Returns

```js
New Array
```

---

## 3. filter()

Use when you want some elements removed.

```js
const nums = [1, 2, 3, 4, 5];

const even = nums.filter(num => num % 2 === 0);

console.log(even);
```

Output:

```js
[2, 4]
```

Examples:

```js
users.filter(user => user.isActive)
```

```js
products.filter(product => product.price < 1000)
```

### Returns

```js
New Array
```

---

## 4. reduce()

Use when you need one final value.

```js
const nums = [1, 2, 3, 4];

const sum = nums.reduce((acc, curr) => {
  return acc + curr;
}, 0);

console.log(sum);
```

Output:

```js
10
```

Examples:

### Sum

```js
nums.reduce((sum, num) => sum + num, 0);
```

### Count

```js
words.reduce((count, word) => count + 1, 0);
```

### Grouping

```js
users.reduce((groups, user) => {
  groups[user.city] = groups[user.city] || [];
  groups[user.city].push(user);

  return groups;
}, {});
```

### Returns

```js
Any value
```

Array, Object, Number, String, etc.

---
