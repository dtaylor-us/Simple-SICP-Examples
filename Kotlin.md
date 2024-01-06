# Kotlin Examples

Kotlin is a modern programming language that combines object-oriented and functional programming features in a concise and expressive syntax. It is particularly suitable for illustrating SICP concepts because of its support for higher-order functions, immutability, and concise syntax. Below are Kotlin examples for each of the key concepts from SICP, showcasing how these ideas can be implemented in a language that balances functional and object-oriented paradigms.

### 1. Abstraction

In Kotlin, abstraction is achieved through interfaces, abstract classes, and higher-order functions. This allows for the creation of generic, reusable components.

```kotlin
interface Shape {
    fun area(): Double
    fun perimeter(): Double
}

class Circle(private val radius: Double) : Shape {
    override fun area() = Math.PI * radius * radius
    override fun perimeter() = 2 * Math.PI * radius
}
```

### 2. Recursive Thinking

Kotlin supports recursion, and a classic example is the calculation of factorial.

```kotlin
fun factorial(n: Int): Int = if (n == 0) 1 else n * factorial(n - 1)

fun main() {
    println(factorial(5)) // Output: 120
}
```

### 3. Procedural and Data Abstraction

Kotlin encourages a clear separation of data and behavior, which can be seen in its class and function design. Data classes provide a concise way to represent immutable data.

```kotlin
data class BankAccount(val balance: Double)

fun deposit(account: BankAccount, amount: Double) = account.copy(balance = account.balance + amount)
fun withdraw(account: BankAccount, amount: Double) = account.copy(balance = account.balance - amount)
```

### 4. Functional Programming

Kotlin, especially from version 1.3, includes features that support functional programming, such as higher-order functions, lambda expressions, and immutable collections.

```kotlin
fun main() {
    val square = { x: Int -> x * x }
    println(square(5)) // Output: 25
}
```

### 5. Metalinguistic Abstraction

Metalinguistic abstraction in Kotlin can be demonstrated through its ability to create DSLs (Domain-Specific Languages) using higher-order functions and lambdas.

```kotlin
class ExprBuilder {
    var result: Int = 0

    fun add(value: Int) {
        result += value
    }
}

fun expr(init: ExprBuilder.() -> Unit): Int {
    val builder = ExprBuilder()
    builder.init()
    return builder.result
}

fun main() {
    val result = expr {
        add(5)
        add(10)
    }
    println(result) // Output: 15
}
```

### 6. Modularity, Objects, and State

Kotlin's object-oriented features support modularity and encapsulation, while its functional aspects help in managing state in a more predictable manner.

```kotlin
class Counter {
    private var count = 0

    fun increment() {
        count++
    }

    fun getCount() = count
}

fun main() {
    val counter = Counter()
    counter.increment()
    println(counter.getCount()) // Output: 1
}
```

### 7. Concurrency and Lazy Evaluation

Kotlin has native support for concurrency through coroutines. Lazy evaluation is supported using the `lazy` keyword, which delays the computation of a value until it's first accessed.

```kotlin
fun main() {
    val lazyValue: Int by lazy { (1..100).random() }
    println("Value not computed yet")
    println("Computed value: $lazyValue")
}
```

### 8. Symbolic Computing

Symbolic computing isn't a typical use case in Kotlin, but you can represent basic symbolic operations using classes and when expressions.

```kotlin
sealed class SymbolicExpr
class SymbolicConstant(val value: Int) : SymbolicExpr()

fun simplify(expr: SymbolicExpr): Int =
    when (expr) {
        is SymbolicConstant -> expr.value
    }

fun main() {
    val result = simplify(SymbolicConstant(5))
    println(result) // Output: 5
}
```

Each example showcases how Kotlin's features can be used to illustrate concepts from SICP, blending functional programming with object-oriented techniques. This makes Kotlin a practical choice for those looking to apply these concepts in a modern programming environment.