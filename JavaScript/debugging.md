# Debugging Strategies

Debugging is the process of finding, understanding, and fixing issues in code. Modern browsers provide debugging tools that allow you to inspect variables, pause execution, and trace program flow step-by-step. 

---

## 1. Reading the Error Message 

Read:

1. Error Type
2. Error Message
3. Stack Trace

Example:

```text
TypeError: Cannot read properties of undefined
    at app.js:12:5
```

This tells you:

- What failed
- Why it failed
- Where it failed

---

## 2. Stack Trace

Example:

```text
Error: Something failed
    at calculateTotal (app.js:10)
    at checkout (app.js:20)
    at main (app.js:30)
```

Execution flow:

```text
main()
  ↓
checkout()
  ↓
calculateTotal()
  ↓
Error
```

The first stack frame usually points to the code that caused the error.

---

## 3. Reproduce the Bug

Before fixing anything, make sure the issue happens consistently.

Example:

```text
1. Enter 5
2. Enter 1
3. Click Add
4. Result becomes 51 instead of 6
```

A reproducible bug is easier to investigate and verify after fixing.

---

## 4. console.log()

Inspect values during execution.

```js
console.log(user);
console.log(total);
console.log(typeof value);
```

Verify actual values instead of assuming them.

---

## 5. console.table()

Useful for arrays and objects.

```js
console.table(users);
```

Makes structured data easier to inspect.

---

## 6. The Chrome DevTools Console

Open DevTools:

```text
F12
```

or

```text
Cmd + Option + J (Mac)
```

The Console displays:

- Errors
- Warnings
- Logs
- Executable JavaScript commands

---

## 7. Set Breakpoints

A breakpoint pauses execution at a specific line.

Steps:

1. Open DevTools
2. Go to Sources
3. Click a line number

Execution pauses when that line is reached.

---

## 8. Use the debugger Statement

Instead of manually creating a breakpoint:

```js
function calculateTotal() {
  debugger;

  return 10;
}
```

When DevTools is open, execution pauses on that line.

---

## 9. Inspect Variables While Paused

When execution stops:

- View local variables
- View global variables
- Evaluate expressions
- Check current values

Chrome DevTools provides Scope and Watch panels for this.

---

## 10. Use Watch Expressions

Track values while stepping through code.

Examples:

```js
count
```

```js
user.name
```

```js
cart.length
```

DevTools automatically updates their values as execution proceeds.

---

## 11. Step Through Code

After pausing, use debugger controls.

### Resume

```text
F8
```

Continue execution until the next breakpoint.

### Step Over

```text
F10
```

Execute the current line and move to the next line.

### Step Into

```text
F11
```

Enter the function being called.

### Step Out

Exit the current function and return to the caller.

---

## 12. Inspect the Call Stack

The Call Stack shows how execution reached the current line.

Example:

```text
calculateTotal
checkout
main
```

You can click any frame to inspect its variables and state.

---

## 13. Verify Inputs

Many issues originate from unexpected inputs.

```js
function calculate(price) {
  return price * 2;
}
```

Check:

```js
console.log(price);
```

before investigating the function logic.

---

# 14. Check Data Types

Unexpected types often cause bugs.

```js
console.log(typeof value);
```

Example:

```js
"10" + 5
```

Output:

```js
105
```

because `"10"` is a string.

---

## 15. Test Small Inputs

Instead of:

```js
[1, 2, 3, 4, 5, 6, 7]
```

start with:

```js
[]
```

```js
[1]
```

```js
[1, 2]
```

Smaller inputs make issues easier to locate.

---

## 16. Isolate the Problem

Instead of debugging an entire workflow:

```js
loadData();
processData();
filterData();
renderData();
```

Test each step separately.

```js
loadData();
```

then

```js
processData();
```

and so on.

---

## 17. Verify Assumptions

Instead of assuming:

```js
user exists
```

verify:

```js
console.log(user);
```

Instead of assuming:

```js
array contains items
```

verify:

```js
console.log(array.length);
```

---

## 18. Change One Thing at a Time

Bad approach:

```text
Modify many files and rerun.
```

Good approach:

```text
Make one change.
Run.
Observe.
Repeat.
```

This makes it easier to identify which change fixed the issue.

---

## 19. Check Edge Cases

Test:

```js
[]
```

```js
null
```

```js
undefined
```

```js
0
```

```js
""
```

Many bugs appear only for these values.

---

## Debugging Workflow

```text
1. Reproduce the bug
2. Read the error message
3. Read the stack trace
4. Set a breakpoint
5. Inspect variables
6. Step through execution
7. Find incorrect value or logic
8. Fix
9. Verify the fix
```
