# Django ORM

## What is ORM?

ORM (Object Relational Mapper) allows Python code to interact with a database without writing SQL directly.

Instead of:

```sql
SELECT * FROM books;
```

you write:

```python
Book.objects.all()
```

Django converts ORM queries into SQL automatically.

---

## Why Use ORM?

Benefits:

* Less SQL to write
* Database-independent code
* Protection against SQL injection
* Easier maintenance
* More readable code

---

## Basic ORM Queries

Assume:

```python
class Book(models.Model):
    title = models.CharField(max_length=100)
    price = models.DecimalField(max_digits=8, decimal_places=2)
```

### Create

```python
Book.objects.create(
    title="Django Basics",
    price=499
)
```

---

### Read

Get all records:

```python
Book.objects.all()
```

Get one record:

```python
Book.objects.get(id=1)
```

---

### Filter

```python
Book.objects.filter(price__gt=500)
```

Equivalent SQL:

```sql
SELECT * FROM book
WHERE price > 500;
```

---

### Update

```python
book = Book.objects.get(id=1)
book.price = 599
book.save()
```

---

### Delete

```python
book.delete()
```

---

# Using ORM in Django Shell

Start shell:

```bash
python manage.py shell
```

Import model:

```python
from books.models import Book
```

---

## Create Data

```python
Book.objects.create(
    title="Python",
    price=399
)
```

---

## Read Data

```python
Book.objects.all()
```

```python
Book.objects.get(id=1)
```

---

## Filtering

```python
Book.objects.filter(price__gt=300)
```

```python
Book.objects.filter(title__icontains="python")
```

---

## Count

```python
Book.objects.count()
```

---

## Ordering

```python
Book.objects.order_by("price")
```

Descending:

```python
Book.objects.order_by("-price")
```

---

# Turning ORM into SQL

Django internally generates SQL.

To inspect it:

```python
queryset = Book.objects.filter(price__gt=500)

print(queryset.query)
```

Output:

```sql
SELECT *
FROM books_book
WHERE price > 500;
```

Useful for:

* Learning SQL
* Debugging
* Query optimization

---

# Aggregations

## What are Aggregations?

Aggregations calculate a single summary value from multiple rows.

Examples:

* Count
* Sum
* Average
* Minimum
* Maximum

---

## Count

```python
from django.db.models import Count

Book.objects.aggregate(
    total=Count("id")
)
```

Result:

```python
{
    "total": 50
}
```

---

## Sum

```python
from django.db.models import Sum

Book.objects.aggregate(
    total_price=Sum("price")
)
```

---

## Average

```python
from django.db.models import Avg

Book.objects.aggregate(
    average_price=Avg("price")
)
```

---

## Maximum

```python
from django.db.models import Max

Book.objects.aggregate(
    highest_price=Max("price")
)
```

---

## Minimum

```python
from django.db.models import Min

Book.objects.aggregate(
    lowest_price=Min("price")
)
```

---

## Aggregate vs Normal Query

Normal query:

```python
Book.objects.all()
```

Returns multiple rows.

Aggregation:

```python
Book.objects.aggregate(
    Avg("price")
)
```

Returns a summary value.

---

# Annotations

## What are Annotations?

Annotations add calculated values to each row.

Aggregation:

```text
Many rows → One result
```

Annotation:

```text
Many rows → Many rows with extra columns
```

---

## Example Models

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

---

## Count Books per Author

```python
from django.db.models import Count

Author.objects.annotate(
    book_count=Count("book")
)
```

Result:

```text
John    5
Alice   2
Bob     8
```

Each author receives an extra field:

```python
author.book_count
```

---

## Example SQL

```sql
SELECT
    author.id,
    COUNT(book.id)
FROM author
LEFT JOIN book
GROUP BY author.id;
```

---

# Aggregate vs Annotate

| Aggregate                  | Annotate         |
| -------------------------- | ---------------- |
| Returns one summary result | Returns queryset |
| Entire table               | Per row          |
| `aggregate()`              | `annotate()`     |

Example:

```python
Book.objects.aggregate(
    Avg("price")
)
```

One value.

---

```python
Author.objects.annotate(
    Count("book")
)
```

One value per author.

---

# Migration Files

## What is a Migration?

A migration is a Python file that describes changes to the database schema.

Example:

```python
class Book(models.Model):
    title = models.CharField(max_length=100)
```

Add:

```python
published_year = models.IntegerField()
```

Django detects the change.

---

## Generate Migration

```bash
python manage.py makemigrations
```

Example:

```text
books/migrations/
0002_add_published_year.py
```

---

## Apply Migration

```bash
python manage.py migrate
```

Database updated automatically.

---

Without migrations:

* Django model changes
* Database schema stays unchanged

This causes inconsistencies.

Migrations keep:

```text
Models
     ↓
Migration Files
     ↓
Database Schema
```

synchronized.

---

## Benefits

* Version controlled
* Team collaboration
* Safe schema evolution
* Rollback support

---

## Rollback Example

```bash
python manage.py migrate books 0001
```

Moves database back to migration 0001.

---

# SQL Transactions

## What is a Transaction?

A transaction is a group of database operations treated as one unit of work.

Example:

Transfer ₹1000.

Step 1:

```sql
UPDATE account
SET balance = balance - 1000
WHERE id = 1;
```

Step 2:

```sql
UPDATE account
SET balance = balance + 1000
WHERE id = 2;
```

Both operations must succeed together.

---

## Problem Without Transactions

Imagine:

```text
Money deducted
Server crashes
Money not credited
```

Data becomes inconsistent.

---

## Transaction Solution

```sql
BEGIN;

UPDATE ...;

UPDATE ...;

COMMIT;
```

If anything fails:

```sql
ROLLBACK;
```

Database returns to original state.

---

# ACID Properties

Every transaction should satisfy:

## Atomicity

All or nothing.

## Consistency

Database remains valid.

## Isolation

Concurrent transactions don't interfere.

## Durability

Committed data survives crashes.

---

# Atomic Transactions in Django

## What is an Atomic Transaction?

Atomic means:

```text
Everything succeeds
OR
Everything fails
```

No partial updates.

---

## Example

Without atomic transaction:

```python
account1.balance -= 1000
account1.save()

raise Exception()

account2.balance += 1000
account2.save()
```

Money deducted but not credited.

---

## Using `transaction.atomic`

```python
from django.db import transaction

with transaction.atomic():
    account1.balance -= 1000
    account1.save()

    account2.balance += 1000
    account2.save()
```

---

## If Error Occurs

```python
from django.db import transaction

with transaction.atomic():
    account1.save()

    raise Exception()

    account2.save()
```

Result:

```text
ROLLBACK
```

Nothing is saved.

---

## Atomic Decorator

```python
from django.db import transaction

@transaction.atomic
def transfer_money():
    ...
```

Entire function becomes one transaction.
