# Go Examples

Go (or Golang) is a statically typed, compiled programming language designed by Google. It's known for its simplicity, efficiency, and strong support for concurrency. While Go is primarily procedural and doesn't support some typical object-oriented features like inheritance, it does offer powerful interfaces and is excellent for systems programming. Here's how some of the SICP concepts can be illustrated in Go:

### 1. Abstraction

Go uses interfaces to define behaviors, providing a way to achieve abstraction. This allows for the creation of flexible and interchangeable code components.

```go
package main

import (
    "fmt"
    "math"
)

type Shape interface {
    Area() float64
    Perimeter() float64
}

type Circle struct {
    Radius float64
}

func (c Circle) Area() float64 {
    return math.Pi * c.Radius * c.Radius
}

func (c Circle) Perimeter() float64 {
    return 2 * math.Pi * c.Radius
}

func main() {
    var s Shape = Circle{Radius: 5}
    fmt.Println("Area:", s.Area())
    fmt.Println("Perimeter:", s.Perimeter())
}
```

### 2. Recursive Thinking

Go supports recursion, allowing functions to call themselves. A classic example is computing the factorial of a number.

```go
package main

import "fmt"

func factorial(n int) int {
    if n == 0 {
        return 1
    }
    return n * factorial(n-1)
}

func main() {
    fmt.Println(factorial(5)) // Output: 120
}
```

### 3. Procedural and Data Abstraction

Go's approach to combining data and behavior is through struct types and methods associated with these structs.

```go
package main

import "fmt"

type BankAccount struct {
    Balance float64
}

func (a *BankAccount) Deposit(amount float64) {
    a.Balance += amount
}

func (a *BankAccount) Withdraw(amount float64) {
    a.Balance -= amount
}

func main() {
    account := BankAccount{Balance: 1000}
    account.Deposit(500)
    fmt.Println("Balance:", account.Balance)
}
```

### 4. Functional Programming

Go supports some functional programming concepts such as first-class and higher-order functions, though it does not fully embrace the functional paradigm.

```go
package main

import "fmt"

func square(x int) int {
    return x * x
}

func main() {
    fmt.Println(square(5)) // Output: 25
}
```

### 5. Metalinguistic Abstraction

While Go doesn't naturally lend itself to metalinguistic abstraction, you can still implement basic domain-specific language features using interfaces and types.

```go
package main

import "fmt"

type Expr interface {
    Evaluate() int
}

type Constant int

func (c Constant) Evaluate() int {
    return int(c)
}

func main() {
    var e Expr = Constant(42)
    fmt.Println(e.Evaluate()) // Output: 42
}
```

### 6. Modularity, Objects, and State

Go encourages modularity through packages. The language's approach to objects is through structs and interfaces, and state is managed explicitly.

```go
package main

import "fmt"

type Counter struct {
    count int
}

func (c *Counter) Increment() {
    c.count++
}

func (c *Counter) Count() int {
    return c.count
}

func main() {
    c := Counter{}
    c.Increment()
    fmt.Println(c.Count()) // Output: 1
}
```

### 7. Concurrency and Lazy Evaluation

Go's concurrency model is one of its key features, primarily using goroutines and channels. Lazy evaluation can be implemented using functions and closures.

```go
package main

import (
    "fmt"
    "math/rand"
)

func lazyValue() func() int {
    return func() int {
        return rand.Intn(100)
    }
}

func main() {
    valueGenerator := lazyValue()
    fmt.Println("Value not computed yet")
    value := valueGenerator()
    fmt.Println("Computed value:", value)
}
```

### 8. Symbolic Computing

Go isn't typically used for symbolic computing, but you can manipulate symbols using interfaces and structs.

```go
package main

import "fmt"

type SymbolicExpr interface {
    Simplify() SymbolicExpr
}

type SymbolicConstant struct {
    Value int
}

func (sc SymbolicConstant) Simplify() SymbolicExpr {
    return sc
}

func main() {
    var expr SymbolicExpr = SymbolicConstant{Value: 5}
    fmt.Println(expr.Simplify()) // Output: {5}
}
```

Each example here adapts a concept from SICP to Go, illustrating how Go's features like interfaces, structs, and functions can be used to explore these concepts. While Go is not as naturally suited to some of the more abstract or functional programming concepts as languages like Lisp or Haskell, it still provides a robust and efficient environment for exploring many key computer science ideas.