# Object-Oriented Programming (OOP) in Python

---

## 1. Encapsulation

Encapsulation means **bundling data and methods into a single class**, and controlling who can access that data.

**Why it matters:**

- Protects data from accidental changes
- Allows validation before updating values
- Hides internal logic — exposes only what's needed

---

### Access Specifiers

Python uses naming conventions to control access. It does **not** enforce these at the language level.

| Level | Prefix | Accessible From |
| --- | --- | --- |
| Public | *(none)* | Anywhere |
| Protected | `_` | Class and subclasses |
| Private | `__` | Inside the class only |

**Public** — no prefix, accessible from anywhere:

```python
class Employee:
    def __init__(self, name):
        self.name = name        # public

emp = Employee("John")
print(emp.name)                 # Works
```

**Protected** — single underscore, meant for class and subclasses only:

```python
class Employee:
    def __init__(self, age):
        self._age = age         # protected

class SubEmployee(Employee):
    def show_age(self):
        print(self._age)        # Accessible in subclass

emp = SubEmployee(30)
emp.show_age()                  # Works
```

**Private** — double underscore, hidden via **name mangling** (`__salary` becomes `_Employee__salary`):

```python
class Employee:
    def __init__(self, salary):
        self.__salary = salary  # private

    def show_salary(self):
        print(self.__salary)    # Accessible inside class

emp = Employee(60000)
emp.show_salary()               # Works
print(emp.__salary)             # ERROR — AttributeError
```

---

### Protected and Private Methods

The same rules apply to methods:

```python
class BankAccount:
    def __init__(self):
        self.balance = 1000

    def _show_balance(self):            # protected
        print(f"Balance: {self.balance}")

    def __update_balance(self, amount): # private
        self.balance += amount

    def deposit(self, amount):          # public
        if amount > 0:
            self.__update_balance(amount)
            self._show_balance()
        else:
            print("Invalid amount!")

account = BankAccount()
account.deposit(500)
```

**Output:**

```text
Balance: 1500
```

---

### Getter and Setter Methods

Used to **safely read and update private attributes**, with optional validation.

```python
class Employee:
    def __init__(self):
        self.__salary = 50000

    def get_salary(self):           # getter
        return self.__salary

    def set_salary(self, amount):   # setter
        if amount > 0:
            self.__salary = amount
        else:
            print("Invalid salary!")

emp = Employee()
print(emp.get_salary())   # 50000
emp.set_salary(60000)
print(emp.get_salary())   # 60000
```

---

## 2. Abstraction

Abstraction means **hiding implementation details and showing only essential functionality**.

Users interact with only the required methods without knowing the internal logic.

**Why it matters:**

- Hides complex implementation
- Makes code easier to use
- Enforces a common structure
- Improves maintainability

---

### Abstract Base Class (ABC)

Python uses the `abc` module for abstraction.

| Component | Purpose |
| --- | --- |
| `ABC` | Creates an abstract class |
| `@abstractmethod` | Creates an abstract method |

Abstract classes act as blueprints for other classes.

---

### Abstract Method

Abstract methods are methods without implementation.

Child classes must implement them.

```python
from abc import ABC, abstractmethod


class Payment(ABC):

    @abstractmethod
    def pay(self):
        pass


class UPI(Payment):

    def pay(self):
        return "Payment Successful"


upi = UPI()

print(upi.pay())
```

**Output:**

```python
Payment Successful
```

---

### Concrete Methods

Abstract classes can also contain normal methods with implementation.

These are called concrete methods.

```python
from abc import ABC, abstractmethod


class Animal(ABC):

    @abstractmethod
    def sound(self):
        pass

    def move(self):
        print("Animal is moving")


class Dog(Animal):

    def sound(self):
        print("Bark")


dog = Dog()

dog.move()
dog.sound()
```

**Output:**

```python
Animal is moving
Bark
```

---

### Abstract Properties

Abstract properties force subclasses to define specific properties.

```python
from abc import ABC, abstractmethod


class Animal(ABC):

    @property
    @abstractmethod
    def type(self):
        pass


class Dog(Animal):

    @property
    def type(self):
        return "Mammal"


dog = Dog()

print(dog.type)
```

**Output:**

```python
Mammal
```

---

### Abstract Class Instantiation

Abstract classes cannot be instantiated directly.

```python
from abc import ABC, abstractmethod


class Animal(ABC):

    @abstractmethod
    def sound(self):
        pass


animal = Animal()
```

**Output:**

```python
TypeError
```

---

### Key Points

- Abstraction hides internal implementation
- Abstract classes work as blueprints
- Abstract methods must be implemented in child classes
- Concrete methods already contain implementation
- Abstract classes cannot create objects directly
- Python uses the `abc` module for abstraction

## 3. Inheritance

Inheritance allows a class to **reuse attributes and methods** from another class.

- Parent class → base class
- Child class → derived class

**Why it matters:**

- Reduces code duplication
- Improves code reusability
- Creates logical relationships between classes
- Makes code easier to maintain

---

### Basic Inheritance

```python
class Animal:

    def __init__(self, name):
        self.name = name

    def info(self):
        print("Animal:", self.name)


class Dog(Animal):

    def sound(self):
        print(self.name, "barks")


dog = Dog("Buddy")

dog.info()
dog.sound()
```

**Output:**

```python
Animal: Buddy
Buddy barks
```

---

### `super()` Function

`super()` is used to call methods from the parent class.

Mostly used inside constructors.

```python
class Animal:

    def __init__(self, name):
        self.name = name


class Dog(Animal):

    def __init__(self, name, breed):
        super().__init__(name)
        self.breed = breed

    def details(self):
        print(self.name, "-", self.breed)


dog = Dog("Buddy", "Golden Retriever")

dog.details()
```

**Output:**

```python
Buddy - Golden Retriever
```

---

## Types of Inheritance

---

### 1. Single Inheritance

One child class inherits from one parent class.

```python
class Parent:

    def show(self):
        print("Parent class")


class Child(Parent):

    def display(self):
        print("Child class")


obj = Child()

obj.show()
obj.display()
```

**Output:**

```python
Parent class
Child class
```

---

### 2. Multiple Inheritance

One child class inherits from multiple parent classes.

```python
class Father:

    def father_skill(self):
        print("Driving")


class Mother:

    def mother_skill(self):
        print("Cooking")


class Child(Father, Mother):
    pass


obj = Child()

obj.father_skill()
obj.mother_skill()
```

**Output:**

```python
Driving
Cooking
```

---

### 3. Multilevel Inheritance

A child class inherits from another child class.

```python
class Grandparent:

    def house(self):
        print("Grandparent's house")


class Parent(Grandparent):

    def car(self):
        print("Parent's car")


class Child(Parent):

    def bike(self):
        print("Child's bike")


obj = Child()

obj.house()
obj.car()
obj.bike()
```

**Output:**

```python
Grandparent's house
Parent's car
Child's bike
```

---

### 4. Hierarchical Inheritance

Multiple child classes inherit from one parent class.

```python
class Parent:

    def home(self):
        print("Parent home")


class Child1(Parent):

    def room(self):
        print("Child1 room")


class Child2(Parent):

    def shop(self):
        print("Child2 shop")


obj1 = Child1()
obj2 = Child2()

obj1.home()
obj2.home()
```

**Output:**

```python
Parent home
Parent home
```

---

### 5. Hybrid Inheritance

Combination of multiple inheritance types.

```python
class A:

    def method_a(self):
        print("Class A")


class B(A):

    def method_b(self):
        print("Class B")


class C(A):

    def method_c(self):
        print("Class C")


class D(B, C):

    def method_d(self):
        print("Class D")


obj = D()

obj.method_a()
obj.method_b()
obj.method_c()
obj.method_d()
```

**Output:**

```python
Class A
Class B
Class C
Class D
```

---

Key Points

- Inheritance allows code reuse
- Child classes inherit parent methods and attributes
- `super()` calls parent class methods
- Python supports multiple types of inheritance
- Inheritance improves scalability and maintainability
