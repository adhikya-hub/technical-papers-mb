# SOLID Principles in Python

SOLID is a set of five design principles used to write clean, maintainable, and scalable object-oriented code.

| Principle | Full Form |
| ---------- | ------------------------------------ |
| S | Single Responsibility Principle |
| O | Open Closed Principle |
| L | Liskov Substitution Principle |
| I | Interface Segregation Principle |
| D | Dependency Inversion Principle |

---

## 1. Single Responsibility Principle (SRP)

A class should have only one responsibility.

A class should have only one reason to change.

### Bad Example

One class handles both file operations and ZIP operations.

```python
from zipfile import ZipFile


class FileManager:
    def read(self):
        print("Reading file")

    def write(self):
        print("Writing file")

    def compress(self):
        print("Compressing file")
```

This class has multiple responsibilities.

---

### Good Example

Split responsibilities into separate classes.

```python
class FileManager:
    def read(self):
        print("Reading file")

    def write(self):
        print("Writing file")


class ZipManager:
    def compress(self):
        print("Compressing file")
```

### Benefits of SRP

- Easier to maintain
- Easier to test
- Cleaner design

---

## 2. Open Closed Principle (OCP)

Classes should be:

- Open for extension
- Closed for modification

Add new behavior without changing existing code.

Bad Example

```python
class Shape:
    def area(self, shape_type):
        if shape_type == "circle":
            return "Circle Area"

        if shape_type == "rectangle":
            return "Rectangle Area"

        return "Unknown Shape"
```

Adding a new shape requires modifying the class.

---

Good Example

```python
from abc import ABC, abstractmethod


class Shape(ABC):
    @abstractmethod
    def area(self):
        """Calculate area."""


class Circle(Shape):
    def area(self):
        return "Circle Area"


class Rectangle(Shape):
    def area(self):
        return "Rectangle Area"
```

### Benefits of OCP

- Easy to extend
- Less risk of breaking old code
- Better scalability

---

## 3. Liskov Substitution Principle (LSP)

Child classes should properly replace parent classes without breaking behavior.

Good Example

```python
class Bird:
    def move(self):
        print("Bird moves")


class Sparrow(Bird):
    def move(self):
        print("Sparrow flies")


def movement(bird):
    bird.move()


movement(Bird())
movement(Sparrow())
```

**Output:**

```python
Bird moves
Sparrow flies
```

### Benefits of LSP

- Predictable behavior
- Better polymorphism
- Safer inheritance

---

## 4. Interface Segregation Principle (ISP)

Classes should not be forced to use methods they do not need.

Bad Example

```python
from abc import ABC, abstractmethod


class Machine(ABC):
    @abstractmethod
    def print(self):
        """Print document."""

    @abstractmethod
    def scan(self):
        """Scan document."""


class OldPrinter(Machine):
    def print(self):
        print("Printing")

    def scan(self):
        raise NotImplementedError
```

OldPrinter does not support scanning.

---

Good Example

```python
from abc import ABC, abstractmethod


class Printer(ABC):
    @abstractmethod
    def print(self):
        """Print document."""


class Scanner(ABC):
    @abstractmethod
    def scan(self):
        """Scan document."""


class OldPrinter(Printer):
    def print(self):
        print("Printing")
```

### Benefits of ISP

- Smaller interfaces
- Cleaner design
- Avoids unnecessary methods

---

## 5. Dependency Inversion Principle (DIP)

Classes should depend on abstractions, not concrete classes.

Bad Example

```python
class MySQLDatabase:
    def connect(self):
        return "Connected to MySQL"


class App:
    def __init__(self):
        self.db = MySQLDatabase()
```

`App` is tightly coupled to MySQL.

---

Good Example

```python
from abc import ABC, abstractmethod


class Database(ABC):
    @abstractmethod
    def connect(self):
        """Connect to database."""


class MySQLDatabase(Database):
    def connect(self):
        return "Connected to MySQL"


class PostgreSQLDatabase(Database):
    def connect(self):
        return "Connected to PostgreSQL"


class App:
    def __init__(self, database):
        self.db = database

    def start(self):
        print(self.db.connect())


app = App(MySQLDatabase())

app.start()
```

**Output:**

```python
Connected to MySQL
```

### Benefits of DIP

- Loose coupling
- Easier testing
- Flexible code

---

## Conclusion

SOLID principles help write:

- Cleaner code
- Reusable code
- Scalable applications
- Maintainable systems

Using SOLID improves object-oriented design and makes projects easier to manage.
