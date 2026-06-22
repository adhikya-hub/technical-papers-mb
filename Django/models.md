# Django Models

A Django model represents a database table.

Example:

```python
from django.db import models

class Book(models.Model):
    title = models.CharField(max_length=100)
    price = models.DecimalField(max_digits=8, decimal_places=2)
```

This creates a table with columns:

```text
Book
├── id
├── title
└── price
```

---

# `on_delete=models.CASCADE`

Used with `ForeignKey` and `OneToOneField` relationships.

Example:

```python
class Author(models.Model):
    name = models.CharField(max_length=100)

class Book(models.Model):
    title = models.CharField(max_length=100)
    author = models.ForeignKey(
        Author,
        on_delete=models.CASCADE
    )
```

## What Does CASCADE Mean?

If the parent record is deleted, all related child records are deleted automatically.

Example:

```text
Author
└── John

Books
├── Django Basics
└── Python Guide
```

Delete:

```text
John
```

Result:

```text
Django Basics
Python Guide
```

are also deleted.

---

# Other `on_delete` Options

## `CASCADE`

Delete related objects.

```python
on_delete=models.CASCADE
```

---

## `PROTECT`

Prevent deletion if related records exist.

```python
on_delete=models.PROTECT
```

Raises:

```text
ProtectedError
```

---

## `SET_NULL`

Set foreign key to `NULL`.

```python
author = models.ForeignKey(
    Author,
    null=True,
    on_delete=models.SET_NULL
)
```

---

## `SET_DEFAULT`

Assign default value.

```python
on_delete=models.SET_DEFAULT
```

---

## `SET()`

Set a custom value.

```python
on_delete=models.SET(get_default_author)
```

---

## `DO_NOTHING`

Django does nothing.

```python
on_delete=models.DO_NOTHING
```

Can cause database integrity errors.

---

# Common Django Fields

## Text Fields

### `CharField`

Short text.

```python
name = models.CharField(max_length=100)
```

Examples:

* Name
* Title
* City

---

### `TextField`

Large text.

```python
description = models.TextField()
```

Examples:

* Blog content
* Comments

---

# Number Fields

### `IntegerField`

```python
age = models.IntegerField()
```

---

### `FloatField`

```python
rating = models.FloatField()
```

---

### `DecimalField`

```python
price = models.DecimalField(
    max_digits=8,
    decimal_places=2
)
```

Preferred for money.

---

# Boolean Field

```python
is_active = models.BooleanField(default=True)
```

Values:

```text
True
False
```

---

# Date & Time Fields

### `DateField`

```python
birth_date = models.DateField()
```

---

### `TimeField`

```python
opening_time = models.TimeField()
```

---

### `DateTimeField`

```python
created_at = models.DateTimeField()
```

---

### Auto Timestamps

```python
created_at = models.DateTimeField(auto_now_add=True)
updated_at = models.DateTimeField(auto_now=True)
```

---

# Relationship Fields

## ForeignKey

Many-to-One

```python
author = models.ForeignKey(
    Author,
    on_delete=models.CASCADE
)
```

Many books → One author

---

## OneToOneField

One-to-One

```python
user = models.OneToOneField(
    User,
    on_delete=models.CASCADE
)
```

One user → One profile

---

## ManyToManyField

Many-to-Many

```python
tags = models.ManyToManyField(Tag)
```

Many posts ↔ Many tags

---

# File Fields

## FileField

```python
document = models.FileField()
```

---

## ImageField

```python
photo = models.ImageField()
```

Requires Pillow:

```bash
pip install pillow
```

---

# Validators

Validators ensure data is valid before saving.

Example:

```python
from django.core.validators import MinValueValidator

age = models.IntegerField(
    validators=[MinValueValidator(18)]
)
```

---

# Common Validators

## MinValueValidator

```python
MinValueValidator(1)
```

Value must be ≥ 1.

---

## MaxValueValidator

```python
MaxValueValidator(100)
```

Value must be ≤ 100.

---

## MinLengthValidator

```python
MinLengthValidator(3)
```

---

## MaxLengthValidator

```python
MaxLengthValidator(50)
```

---

## EmailValidator

```python
EmailValidator()
```

Validates email format.

---

## URLValidator

```python
URLValidator()
```

Validates URLs.

---

## RegexValidator

```python
from django.core.validators import RegexValidator

phone_validator = RegexValidator(
    regex=r"^\d{10}$"
)
```

Validates custom patterns.

---

# Python Module vs Python Class

## Python Module

A module is a Python file containing code.

Example:

```text
utils.py
```

```python
def add(a, b):
    return a + b
```

Import:

```python
import utils

utils.add(1, 2)
```

A module helps organize code.

---

## Python Class

A class is a blueprint for creating objects.

Example:

```python
class Car:
    def __init__(self, brand):
        self.brand = brand
```

Create object:

```python
car = Car("Toyota")
```

A class helps model real-world entities.

---

# Module vs Class

| Module                                 | Class                                |
| -------------------------------------- | ------------------------------------ |
| Python file                            | Blueprint for objects                |
| Contains functions, classes, variables | Contains methods and attributes      |
| Imported using `import`                | Instantiated using `ClassName()`     |
| Used for code organization             | Used for object-oriented programming |

Example:

```text
vehicles.py      ← Module
└── Car          ← Class
```

```python
# vehicles.py

class Car:
    pass
```

```python
from vehicles import Car

car = Car()
```
