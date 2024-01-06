# Python Examples

Python is a versatile, high-level programming language known for its readability and support for multiple programming paradigms, including object-oriented and functional programming. Its simplicity and expressiveness make it a great choice for illustrating SICP concepts. Below are Python examples for each key concept, highlighting Python's capabilities in both functional and OOP styles.

### 1. Abstraction

Python achieves abstraction through functions, classes, and interfaces (abstract base classes). This allows for defining generic forms of operations and data structures.

```python
from abc import ABC, abstractmethod
import math

class Shape(ABC):
    @abstractmethod
    def area(self):
        pass

    @abstractmethod
    def perimeter(self):
        pass

class Circle(Shape):
    def __init__(self, radius):
        self.radius = radius

    def area(self):
        return math.pi * self.radius ** 2

    def perimeter(self):
        return 2 * math.pi * self.radius

# Usage
circle = Circle(5)
print(circle.area())
print(circle.perimeter())
```

### 2. Recursive Thinking

Python naturally supports recursion, allowing functions to call themselves. A classic example is calculating the factorial of a number.

```python
def factorial(n):
    if n == 0:
        return 1
    return n * factorial(n - 1)

# Usage
print(factorial(5))  # Output: 120
```

### 3. Procedural and Data Abstraction

Python supports the encapsulation of data and procedures through classes, combining data attributes with methods that operate on that data.

```python
class BankAccount:
    def __init__(self, balance):
        self.balance = balance

    def deposit(self, amount):
        self.balance += amount

    def withdraw(self, amount):
        self.balance -= amount

    def get_balance(self):
        return self.balance

# Usage
account = BankAccount(1000)
account.deposit(500)
print(account.get_balance())
```

### 4. Functional Programming

Python includes features that support functional programming, such as higher-order functions, lambda expressions, and immutability in certain data types.

```python
square = lambda x: x * x

# Usage
print(square(5))  # Output: 25
```

### 5. Metalinguistic Abstraction

Python can be used for metalinguistic abstraction, particularly through its dynamic typing and first-class functions, enabling the creation of interpreters or domain-specific languages.

```python
class Expr:
    pass

class Constant(Expr):
    def __init__(self, value):
        self.value = value

    def evaluate(self):
        return self.value

# Usage
expr = Constant(42)
print(expr.evaluate())  # Output: 42
```

### 6. Modularity, Objects, and State

Python promotes modularity through its package and module system. State and behavior are encapsulated within objects, aligning with OOP principles.

```python
class Counter:
    def __init__(self):
        self.count = 0

    def increment(self):
        self.count += 1

    def get_count(self):
        return self.count

# Usage
counter = Counter()
counter.increment()
print(counter.get_count())  # Output: 1
```

### 7. Concurrency and Lazy Evaluation

Python supports concurrency through various mechanisms like threading and asyncio. Lazy evaluation can be achieved through generators and iterators.

```python
def lazy_value():
    import random
    return random.randint(1, 100)

# Usage
print("Value not computed yet")
value = lazy_value()
print(f"Computed value: {value}")
```

### 8. Symbolic Computing

While not a typical use case for Python, symbolic computing can be implemented using classes to represent symbols and operations.

```python
class SymbolicExpr:
    pass

class SymbolicConstant(SymbolicExpr):
    def __init__(self, value):
        self.value = value

    def simplify(self):
        return self

# Usage
expr = SymbolicConstant(5)
print(expr.simplify())  # Output: <__main__.SymbolicConstant object at 0x...>
```

These Python examples showcase the flexibility of the language in illustrating concepts from SICP, blending functional and object-oriented approaches effectively. Python's readable syntax and powerful features make it an ideal language for both learning and applying these fundamental programming concepts.