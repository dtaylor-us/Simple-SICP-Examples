# Scala Examples

Scala is a powerful language that seamlessly integrates the features of object-oriented and functional programming. It is particularly well-suited for expressing concepts from SICP due to its support for higher-order functions, pattern matching, case classes, and a strong type system. Below are Scala examples for each of the SICP concepts, showcasing the language's capabilities to implement these ideas.

### 1. Abstraction

Scala uses traits and abstract classes to achieve abstraction, allowing for the definition of general contracts for a set of functionalities.

```scala
trait Shape {
  def area: Double
  def perimeter: Double
}

class Circle(radius: Double) extends Shape {
  override def area: Double = Math.PI * radius * radius
  override def perimeter: Double = 2 * Math.PI * radius
}

// Usage
val circle = new Circle(5)
println(circle.area)
println(circle.perimeter)
```

### 2. Recursive Thinking

Scala supports recursive methods and is particularly adept at handling tail-recursive functions, which are optimized by the compiler.

```scala
def factorial(n: Int): Int = {
  @annotation.tailrec
  def loop(acc: Int, n: Int): Int = {
    if (n == 0) acc
    else loop(acc * n, n - 1)
  }
  loop(1, n)
}

// Usage
println(factorial(5)) // Output: 120
```

### 3. Procedural and Data Abstraction

Scala uses case classes to encapsulate data, and methods can be defined to operate on this data. This promotes a clear separation of concerns.

```scala
case class BankAccount(balance: Double) {
  def deposit(amount: Double): BankAccount = this.copy(balance = this.balance + amount)
  def withdraw(amount: Double): BankAccount = this.copy(balance = this.balance - amount)
}

// Usage
val account = BankAccount(1000)
val updatedAccount = account.deposit(500)
println(updatedAccount.balance)
```

### 4. Functional Programming

Scala's functional programming aspects include immutable data structures, higher-order functions, and lambda expressions.

```scala
val square: Int => Int = x => x * x

// Usage
println(square(5)) // Output: 25
```

### 5. Metalinguistic Abstraction

Scala allows for metalinguistic abstraction, especially with its powerful pattern matching and case class features, enabling the construction of interpreters and DSLs.

```scala
sealed trait Expr
case class Constant(value: Int) extends Expr
case class Add(left: Expr, right: Expr) extends Expr

def evaluate(expr: Expr): Int = expr match {
  case Constant(value) => value
  case Add(left, right) => evaluate(left) + evaluate(right)
}

// Usage
val expr = Add(Constant(10), Constant(32))
println(evaluate(expr)) // Output: 42
```

### 6. Modularity, Objects, and State

Scala's object-oriented features naturally support modularity and encapsulation. Scala also offers traits as a way to compose behavior.

```scala
class Counter {
  private var count = 0
  def increment(): Unit = { count += 1 }
  def getCount: Int = count
}

// Usage
val counter = new Counter()
counter.increment()
println(counter.getCount) // Output: 1
```

### 7. Concurrency and Lazy Evaluation

Scala has strong support for concurrency, particularly through Futures and Akka framework. Lazy evaluation is achieved using `lazy val`.

```scala
lazy val lazyValue: Int = {
  println("Computed")
  scala.util.Random.nextInt(100)
}

// Usage
println("Value not computed yet")
println(s"Computed value: $lazyValue")
```

### 8. Symbolic Computing

Symbolic computing can be expressed in Scala, although it's not a common use case. Case classes can be used to represent symbolic expressions and operations.

```scala
sealed trait SymbolicExpr
case class SymbolicConstant(value: Int) extends SymbolicExpr

def simplify(expr: SymbolicExpr): SymbolicExpr = expr match {
  case constant: SymbolicConstant => constant
}

// Usage
val expr = SymbolicConstant(5)
println(simplify(expr)) // Output: SymbolicConstant(5)
```

These Scala examples demonstrate how Scala's unique blend of functional and object-oriented programming features makes it a robust language for illustrating and implementing a wide range of programming concepts, including those found in SICP.