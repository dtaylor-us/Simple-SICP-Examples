## Java Examples
Java is not inherently a functional programming language like Clojure, but modern Java (especially Java 8 and later) includes features that support functional programming concepts.

### 1. Abstraction

Abstraction in Java can be achieved through interfaces and abstract classes. This allows you to define a general form or protocol for a set of functionalities.

```java
interface Shape {
    double area();
    double perimeter();
}

class Circle implements Shape {
    private double radius;

    Circle(double radius) {
        this.radius = radius;
    }

    @Override
    public double area() {
        return Math.PI * radius * radius;
    }

    @Override
    public double perimeter() {
        return 2 * Math.PI * radius;
    }
}
```

### 2. Recursive Thinking

Java supports recursive methods. A classic example is the calculation of the factorial of a number.

```java
public class Main {
    static int factorial(int n) {
        if (n == 0) return 1;
        return n * factorial(n - 1);
    }

    public static void main(String[] args) {
        System.out.println(factorial(5)); // Output: 120
    }
}
```

### 3. Procedural and Data Abstraction

Java encapsulates data and procedures using classes and methods. You can design classes to represent data and include methods that operate on this data.

```java
class BankAccount {
    private double balance;

    BankAccount(double balance) {
        this.balance = balance;
    }

    void deposit(double amount) {
        balance += amount;
    }

    void withdraw(double amount) {
        balance -= amount;
    }

    double getBalance() {
        return balance;
    }
}
```

### 4. Functional Programming

Java 8 introduced lambda expressions and functional interfaces, enabling a functional programming style.

```java
import java.util.function.Function;

public class Main {
    public static void main(String[] args) {
        Function<Integer, Integer> square = x -> x * x;
        System.out.println(square.apply(5)); // Output: 25
    }
}
```

### 5. Metalinguistic Abstraction

This concept involves creating new languages or interpreters. In Java, this can be illustrated by implementing a simple expression evaluator.

```java
interface Expr {
    int evaluate();
}

class Constant implements Expr {
    private int value;

    Constant(int value) {
        this.value = value;
    }

    @Override
    public int evaluate() {
        return value;
    }
}

class Addition implements Expr {
    private Expr left, right;

    Addition(Expr left, Expr right) {
        this.left = left;
        this.right = right;
    }

    @Override
    public int evaluate() {
        return left.evaluate() + right.evaluate();
    }
}
```

### 6. Modularity, Objects, and State

Object-oriented features in Java naturally support modularity. Encapsulation is achieved using access modifiers and class design.

```java
class Counter {
    private int count = 0;

    public void increment() {
        count++;
    }

    public int getCount() {
        return count;
    }
}
```

### 7. Concurrency and Lazy Evaluation

Java supports concurrency through threads and lazy evaluation can be implemented using suppliers.

```java
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;
import java.util.function.Supplier;

public class Main {
    public static void main(String[] args) {
        // Concurrency
        ExecutorService executor = Executors.newFixedThreadPool(2);
        executor.submit(() -> System.out.println("Running in a separate thread"));
        executor.shutdown();

        // Lazy Evaluation
        Supplier<Double> lazyValue = () -> Math.random();
        System.out.println("Value not computed yet");
        System.out.println("Computed value: " + lazyValue.get());
    }
}
```

### 8. Symbolic Computing

Symbolic computing isn't a typical use case in Java, but you can implement basic symbolic operations like expression trees.

```java
abstract class SymbolicExpr {
    abstract SymbolicExpr simplify();
}

class SymbolicConstant extends SymbolicExpr {
    private double value;

    SymbolicConstant(double value) {
        this.value = value;
    }

    @Override
    SymbolicExpr simplify() {
        return this;
    }
}
```

Each of these examples illustrates a concept from SICP adapted to Java. However, remember that some of the concepts, like metalinguistic abstraction and symbolic computing, are more naturally suited to languages like Scheme and Lisp. Java examples provide a basic idea but may not capture the full depth of the concepts as presented in SICP.