# Array Methods (Python Collections)

Python primarily uses the following collection data structures:

- Lists
- Dictionaries
- Tuples
- Sets

---

## List Methods

Lists are ordered and mutable collections.

| Method | Description |
| ---------- | ----------- |
| `append()` | Adds an element at the end of the list |
| `clear()` | Removes all the elements from the list |
| `copy()` | Returns a copy of the list |
| `count()` | Returns the number of elements with the specified value |
| `extend()` | Adds the elements of another iterable to the end of the list |
| `index()` | Returns the index of the first matching element |
| `insert()` | Adds an element at the specified position |
| `pop()` | Removes the element at the specified position |
| `remove()` | Removes the first matching element |
| `reverse()` | Reverses the order of the list |
| `sort()` | Sorts the list |

---

## Dictionary Methods

Dictionaries store data in key-value pairs.

| Method | Description |
| ---------- | ----------- |
| `clear()` | Removes all the elements from the dictionary |
| `copy()` | Returns a copy of the dictionary |
| `fromkeys()` | Returns a dictionary with specified keys and values |
| `get()` | Returns the value of the specified key |
| `items()` | Returns key-value pairs as tuples |
| `keys()` | Returns all dictionary keys |
| `pop()` | Removes the element with the specified key |
| `popitem()` | Removes the last inserted key-value pair |
| `setdefault()` | Returns the value of a key or inserts default value |
| `update()` | Updates dictionary with specified key-value pairs |
| `values()` | Returns all dictionary values |

---

## Tuple Methods

Tuples are ordered and immutable collections.

| Method | Description |
| ---------- | ----------- |
| `count()` | Returns the number of times a value occurs |
| `index()` | Returns the index of the specified value |

---

## Set Methods

Sets store unique values.

| Method | Shortcut | Description |
| ---------- | ---------- | ----------- |
| `add()` | — | Adds an element to the set |
| `clear()` | — | Removes all elements from the set |
| `copy()` | — | Returns a copy of the set |
| `difference()` | `-` | Returns difference between sets |
| `discard()` | — | Removes specified item |
| `intersection()` | `&` | Returns common elements |
| `pop()` | — | Removes a random element |
| `remove()` | — | Removes specified element |
| `symmetric_difference()` | `^` | Returns non-common elements |
| `union()` | `\|` | Combines sets |
| `update()` | `\|=` | Updates set with union |

## String Methods

Python has a set of built-in methods that you can use on strings.

All string methods return new values. They do not change the original string.

| Method | Description |
| ---------- | ----------- |
| `lower()` | Converts string into lower case |
| `upper()` | Converts string into upper case |
| `strip()` | Returns a trimmed version of the string |
| `split()` | Splits the string and returns a list |
| `replace()` | Replaces a specified value with another value |
| `join()` | Converts elements of an iterable into a string |
| `startswith()` | Returns `True` if the string starts with specified value |
| `endswith()` | Returns `True` if the string ends with the specified value |
| `find()` | Searches the string for a specified value and returns its position |
| `index()` | Searches the string for a specified value and returns its position |
| `count()` | Returns the number of times a specified value occurs in a string |
| `capitalize()` | Converts the first character to upper case |
| `title()` | Converts first character of each word to upper case |
| `splitlines()` | Splits the string at line breaks |
| `format()` | Formats specified values in a string |
| `rstrip()` | Returns a right-trimmed version of the string |
| `lstrip()` | Returns a left-trimmed version of the string |
| `islower()` | Returns `True` if all characters are lower case |
| `isupper()` | Returns `True` if all characters are upper case |
| `isdigit()` | Returns `True` if all characters are digits |
| `isalpha()` | Returns `True` if all characters are alphabetic |
| `isalnum()` | Returns `True` if all characters are alphanumeric |
| `isspace()` | Returns `True` if all characters are whitespace |
| `swapcase()` | Swaps lower case to upper case and vice versa |
| `center()` | Returns a centered string |
| `ljust()` | Returns a left-justified version of the string |
| `rjust()` | Returns a right-justified version of the string |
| `partition()` | Splits the string into three parts |
| `rpartition()` | Splits the string into three parts from the right |
| `rsplit()` | Splits the string from the right and returns a list |
| `casefold()` | Converts string into lower case |
| `translate()` | Returns a translated string |
| `maketrans()` | Returns a translation table |
| `zfill()` | Fills string with leading zeros |
| `encode()` | Returns an encoded version of the string |
| `expandtabs()` | Sets the tab size of the string |
| `rfind()` | Returns the last occurrence position of a value |
| `rindex()` | Returns the last occurrence position of a value |
| `format_map()` | Formats specified values from a dictionary |
| `istitle()` | Returns `True` if the string follows title case rules |
| `isnumeric()` | Returns `True` if all characters are numeric |
| `isdecimal()` | Returns `True` if all characters are decimal characters |
| `isidentifier()` | Returns `True` if the string is a valid identifier |
| `isprintable()` | Returns `True` if all characters are printable |
| `isascii()` | Returns `True` if all characters are ASCII characters |

## Objects and Object Oriented Programming (OOP)

Object Oriented Programming (OOP) helps organize code using **classes** and **objects**.  
It makes programs more reusable, modular, and easier to maintain.

---

### What is a Class?

A **class** is a blueprint for creating objects.

```python
class Dog:
    sound = "bark"
```

---

### What is an Object?

An **object** is an instance of a class.

```python
class Dog:
    sound = "bark"

dog1 = Dog()

print(dog1.sound)
```

Output

```python
bark
```

---

### Constructor `__init__()`

`__init__()` runs automatically when an object is created.

```python
class Dog:
    species = "Canine"

    def __init__(self, name, age):
        self.name = name
        self.age = age

dog1 = Dog("Buddy", 3)

print(dog1.name)
print(dog1.species)
```

Output

```python
Buddy
Canine
```

- `self` refers to current object
- `name` and `age` are instance variables

---

## `__str__()` Method

Used to display objects in a readable format.

```python
class Dog:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def __str__(self):
        return f"{self.name} is {self.age} years old"

dog1 = Dog("Buddy", 3)

print(dog1)
```

### Output

```python
Buddy is 3 years old
```

---

## Class Variables vs Instance Variables

### Class Variable

Shared by all objects.

```python
class Student:
    school = "ABC School"
```

### Instance Variable

Unique for each object.

```python
class Student:
    def __init__(self, name):
        self.name = name
```

---

## Example

```python
class CSStudent:
    stream = "CSE"

    def __init__(self, name):
        self.name = name

a = CSStudent("Rose")
b = CSStudent("Nat")

print(a.stream)
print(b.stream)

print(a.name)
print(b.name)
```

Output

```python
CSE
CSE
Rose
Nat
```

---

## Modifying Class Variables

### Using Object (Not Recommended)

```python
a.stream = "ECE"
```

Creates a new instance variable only for `a`.

### Using Class Name (Recommended)

```python
CSStudent.stream = "MECH"
```

Updates the class variable for all objects.

---

## Four Pillars of OOP

### 1. Inheritance

Allows one class to use properties and methods of another class.

```python
class Animal:
    pass

class Dog(Animal):
    pass
```

---

### 2. Polymorphism

Same method name behaves differently.

```python
class Dog:
    def sound(self):
        print("Bark")

class Cat:
    def sound(self):
        print("Meow")
```

---

### 3. Encapsulation

Bundles data and methods together.

```python
class Student:
    def __init__(self, name):
        self.name = name
```

---

### 4. Abstraction

Hides implementation details and shows only necessary functionality.

---

## Access Modifiers

### Public

Accessible from anywhere.

```python
class Geek:
    def __init__(self):
        self.name = "R2J"
```

---

### Protected

Starts with `_`

```python
class Geek:
    def __init__(self):
        self._name = "R2J"
```

> Convention: should not be accessed outside class

---

### Private

Starts with `__`

```python
class Geek:
    def __init__(self):
        self.__name = "R2J"
```

Access using name mangling:

```python
obj._Geek__name
```

---

## Benefits of OOP

- Better code organization
- Reusable code
- Easier maintenance
- Improved scalability
- Real-world modeling

---

## Quick Summary

| Concept | Meaning |
| -------- | ------- |
| `__init__()` | Constructor |
| `self` | Current object |
| Class Variable | Shared by all objects |
| Instance Variable | Unique to each object |
| Inheritance | Reuse code |
| Polymorphism | Same method, different behavior |
| Encapsulation | Group data and methods |
| Abstraction | Hide implementation details |

---

## Decorators

Decorators add extra functionality to functions without changing original code. :contentReference[oaicite:0]{index=0}

---

## Simple Decorator Example

```python
def decorator(func):
    def wrapper():
        print("Before function")
        func()
        print("After function")
    return wrapper

@decorator
def greet():
    print("Hello")

greet()
```

Output

```python
Before function
Hello
After function
```

---

## Decorator with Arguments

```python
def decorator(func):
    def wrapper(*args, **kwargs):
        print("Running function")
        return func(*args, **kwargs)
    return wrapper

@decorator
def add(a, b):
    return a + b

print(add(2, 3))
```

Output

```python
Running function
5
```

---

## Functions as First-Class Objects

Functions can:

- Be stored in variables
- Be passed as arguments
- Be returned from functions

```python
def greet(name):
    return f"Hello {name}"

say_hi = greet

print(say_hi("Alex"))
```

---

## Higher-Order Functions

Functions that take another function as input.

```python
def apply(func, value):
    return func(value)

def square(x):
    return x * x

print(apply(square, 5))
```

Output

```python
25
```

---

## Types of Decorators

### Function Decorator

```python
def simple(func):
    def wrapper():
        print("Start")
        func()
        print("End")
    return wrapper
```

---

### Method Decorator

Used inside classes.

```python
def method_decorator(func):
    def wrapper(self):
        print("Before")
        func(self)
        print("After")
    return wrapper
```

---

### Class Decorator

Used to modify classes.

```python
def add_name(cls):
    cls.type = "Person"
    return cls

@add_name
class User:
    pass

print(User.type)
```

---

## Built-in Decorators

### `@staticmethod`

No `self` needed.

```python
class Math:
    @staticmethod
    def add(a, b):
        return a + b

print(Math.add(2, 3))
```

---

### `@classmethod`

Uses `cls`.

```python
class Employee:
    company = "Google"

    @classmethod
    def change_company(cls, name):
        cls.company = name
```

---

### `@property`

Access method like variable.

```python
class Circle:
    def __init__(self, radius):
        self._radius = radius

    @property
    def area(self):
        return 3.14 * self._radius * self._radius

c = Circle(5)

print(c.area)
```

---

## Chaining Decorators

Using multiple decorators together.

```python
def decor1(func):
    def wrapper():
        return func() * 2
    return wrapper

def decor2(func):
    def wrapper():
        return func() + 5
    return wrapper

@decor1
@decor2
def num():
    return 10

print(num())
```

Output

```python
30
```

---

## Real-World Uses of Decorators

- Logging
- Authentication
- Caching
- API rate limiting
- Retry failed requests

---

## Python Virtual Environment

A virtual environment is an isolated space for a Python project.  
It keeps project packages separate from other projects. :contentReference[oaicite:0]{index=0}

---

## Why Use Virtual Environment?

- Avoid package conflicts
- Keep projects separate
- Install different package versions
- Keep system Python clean

---

## Create Virtual Environment

```bash
python -m venv myproject
```

This creates a folder named `myproject`.

---

## Activate Virtual Environment

### Windows

```bash
myproject\Scripts\activate
```

### macOS/Linux

```bash
source myproject/bin/activate
```

After activation:

```bash
(myproject)
```

---

## Install Package

Example using `pylint`.

```bash
pip install pylint
```

---

## Check Installed Package

```bash
pylint --version
```

---

## Create Python File

```python
# app.py

name = "Alex"

print("Hello", name)
```

---

## Run Pylint

```bash
pylint app.py
```

Example Output:

```bash
Your code has been rated at 10.00/10
```

---

## Deactivate Virtual Environment

```bash
deactivate
```

---

## Delete Virtual Environment

```bash
rm -rf myproject
```

---

## Benefits

- Cleaner projects
- Easier dependency management
- Better testing
- Reproducible environments

---

| Command | Purpose |
| --- | --- |
| `python -m venv myproject` | Create virtual environment |
| `activate` | Start virtual environment |
| `pip install pylint` | Install package |
| `pylint app.py` | Run pylint |
| `deactivate` | Exit virtual environment |

## pip Package Manager

`pip` is Python’s package manager.  
It is used to install and manage Python packages.

A package is a collection of ready-made Python code.

Example:

- `pylint` → checks code quality
- `requests` → works with APIs
- `numpy` → math operations

---

## Check pip Version

```bash
pip --version
```

---

## Install a Package

Example: install `pylint`

```bash
pip install pylint
```

---

## Use Installed Package

Create a file:

```python
# hello.py

name = "Sam"

print("Hello", name)
```

Run pylint:

```bash
pylint hello.py
```

Example Output:

```bash
Your code has been rated at 10.00/10
```

---

## View Installed Packages

```bash
pip list
```

---

## Show Package Information

```bash
pip show pylint
```

---

## Upgrade a Package

```bash
pip install --upgrade pylint
```

---

## Uninstall a Package

```bash
pip uninstall pylint
```

---

## Install Specific Version

```bash
pip install pylint==3.2.0
```

---

## Install Packages from requirements.txt

```bash
pip install -r requirements.txt
```

Example `requirements.txt`

```txt
pylint
requests
numpy
```

---

## Create requirements.txt

```bash
pip freeze > requirements.txt
```

---

## Why Use pip?

- Easy package installation
- Saves development time
- Manage project dependencies
- Install useful libraries quickly

---

| Command | Purpose |
| --- | --- |
| `pip install pylint` | Install package |
| `pip list` | Show installed packages |
| `pip show pylint` | Show package details |
| `pip uninstall pylint` | Remove package |
| `pip freeze` | Show installed packages |
| `pip install -r requirements.txt` | Install from file |

## PEP 8 – Python Style Guide (Quick Reference)

> Code is read more often than it is written. Readability counts.

---

### Indentation

- Use **4 spaces** per level (no tabs)
- Align continuation lines with the opening delimiter or use a hanging indent

```python
# Good
foo = long_function_name(var_one, var_two,
                         var_three, var_four)
# Also good
foo = long_function_name(
    var_one, var_two,
    var_three, var_four)
```

---

### Line Length

- Max **79 characters** for code
- Max **72 characters** for comments and docstrings
- Use parentheses for line wrapping (avoid backslashes)

---

### Blank Lines

- **2 blank lines** around top-level functions and classes
- **1 blank line** between methods inside a class

---

### Imports

- One import per line
- Order: standard library → third-party → local
- Put a blank line between each group
- Avoid wildcard imports (`from module import *`)

```python
# Good
import os
import sys

import requests

from myapp import utils
```

---

### Whitespace

- No spaces inside brackets: `spam(ham[1], {eggs: 2})`
- No space before a colon or comma: `if x == 4: print(x, y)`
- One space around `=`, `+=`, `==`, etc.
- No spaces around `=` for keyword args: `func(key=value)`

---

### Comments

- Keep comments up to date with the code
- Write in complete sentences, starting with a capital letter
- Write in English

---

### Naming Conventions

| Type | Style | Example |
| --- | --- | --- |
| Variable / Function | `snake_case` | `my_variable` |
| Class | `CapWords` | `MyClass` |
| Constant | `UPPER_CASE` | `MAX_SIZE` |
| Module / Package | `lowercase` | `mymodule` |
| "Private" | `_leading_underscore` | `_internal` |

- Avoid `l`, `O`, `I` as single-character names (they look like `1` and `0`)

---

### String Quotes

- Single and double quotes are both fine — just **be consistent**
- Use double quotes for docstrings (`"""like this"""`)

---

### Programming Tips

- Compare to `None` with `is` / `is not`, not `==`
- Use `isinstance()` instead of `type()`
- Use `startswith()` / `endswith()` instead of slicing
- Use `with` statements for file/resource handling
- Catch specific exceptions, not bare `except:`
- Don't compare booleans with `== True` — just use `if greeting:`

---

### Type Annotations

```python
# Good
def greet(name: str) -> str:
    return f"Hello, {name}"

# Variable annotation
count: int = 0
```

- Space after colon, space around `->`, space around `=` when annotated

---

*[peps.python.org/pep-0008](https://peps.python.org/pep-0008/)*
